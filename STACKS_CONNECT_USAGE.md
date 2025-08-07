# @stacks/connect Usage Patterns

A comprehensive guide to using `@stacks/connect` for Stacks wallet integration in web applications.

## Overview

`@stacks/connect` is the official library for integrating Stacks wallets into web applications. It provides a standardized interface for wallet connection, transaction signing, and message authentication across different wallet providers.

## Core Functions & Usage Patterns

### 1. Wallet Connection & Management

#### Basic Wallet Connection
```typescript
import { connect } from "@stacks/connect";
import type { AddressEntry } from "@stacks/connect/dist/types/methods";

const connectWallet = async () => {
  try {
    const result = await connect();
    console.log("Connected addresses:", result.addresses);
    
    // Store addresses for persistence
    localStorage.setItem("stacks-addresses", JSON.stringify(result.addresses));
    return result.addresses;
  } catch (error) {
    console.error("Connection failed:", error);
    throw error;
  }
};
```

#### Multi-Network Address Management
```typescript
const connectWithNetworkSupport = async () => {
  const result = await connect();
  
  // Store addresses for both networks
  localStorage.setItem("addresses-mainnet", JSON.stringify(result.addresses));
  localStorage.setItem("addresses-testnet", JSON.stringify(result.addresses));
  
  // Get current network addresses
  const currentAddresses = getCurrentNetworkAddresses(result.addresses);
  return currentAddresses;
};

const getCurrentNetworkAddresses = (addresses: AddressEntry[]) => {
  const network = detectNetwork(); // Custom network detection
  return addresses.filter(addr => 
    network === 'mainnet' ? addr.address.startsWith('SP') : addr.address.startsWith('ST')
  );
};
```

#### React Context Pattern for Wallet State
```typescript
import React, { createContext, useContext, useState, useEffect } from 'react';
import { connect } from "@stacks/connect";
import type { AddressEntry } from "@stacks/connect/dist/types/methods";

interface WalletContextType {
  addresses: AddressEntry[] | null;
  isConnected: boolean;
  connect: () => Promise<void>;
  disconnect: () => void;
  currentAddress: string | null;
}

const WalletContext = createContext<WalletContextType | null>(null);

export const WalletProvider: React.FC<{ children: React.ReactNode }> = ({ children }) => {
  const [addresses, setAddresses] = useState<AddressEntry[] | null>(null);
  const [isConnected, setIsConnected] = useState(false);

  const connectWallet = async () => {
    try {
      const result = await connect();
      setAddresses(result.addresses);
      setIsConnected(true);
      
      // Persist connection
      localStorage.setItem("wallet-connected", "true");
      localStorage.setItem("wallet-addresses", JSON.stringify(result.addresses));
    } catch (error) {
      console.error("Connection failed:", error);
    }
  };

  const disconnect = () => {
    setAddresses(null);
    setIsConnected(false);
    localStorage.removeItem("wallet-connected");
    localStorage.removeItem("wallet-addresses");
  };

  // Restore connection on page load
  useEffect(() => {
    const wasConnected = localStorage.getItem("wallet-connected");
    const storedAddresses = localStorage.getItem("wallet-addresses");
    
    if (wasConnected && storedAddresses) {
      try {
        const addresses = JSON.parse(storedAddresses);
        setAddresses(addresses);
        setIsConnected(true);
      } catch (error) {
        console.error("Failed to restore wallet connection:", error);
      }
    }
  }, []);

  const currentAddress = addresses?.[0]?.address || null;

  return (
    <WalletContext.Provider value={{
      addresses,
      isConnected,
      connect: connectWallet,
      disconnect,
      currentAddress
    }}>
      {children}
    </WalletContext.Provider>
  );
};

export const useWallet = () => {
  const context = useContext(WalletContext);
  if (!context) {
    throw new Error('useWallet must be used within WalletProvider');
  }
  return context;
};
```

### 2. Transaction Requests

#### Basic Contract Call Request
```typescript
import { request } from '@stacks/connect';
import type { TransactionResult } from '@stacks/connect/dist/types/methods';

const makeContractCall = async (
  contractAddress: string,
  contractName: string,
  functionName: string,
  functionArgs: any[],
  senderAddress: string
) => {
  try {
    const result = await request('stx_callContract', {
      contractAddress,
      contractName,
      functionName,
      functionArgs,
      senderAddress,
      network: 'mainnet', // or 'testnet'
    });
    
    if (result?.txid) {
      console.log("Transaction submitted:", result.txid);
      return result.txid;
    }
    
    throw new Error("No transaction ID returned");
  } catch (error) {
    handleTransactionError(error);
    throw error;
  }
};
```

#### Advanced Contract Call with Post-Conditions
```typescript
import { request } from '@stacks/connect';
import type { PostCondition } from '@stacks/connect/dist/types/methods';

const makeContractCallWithPostConditions = async ({
  contractAddress,
  contractName,
  functionName,
  functionArgs,
  senderAddress,
  postConditions,
  fee = 200000
}: {
  contractAddress: string;
  contractName: string;
  functionName: string;
  functionArgs: any[];
  senderAddress: string;
  postConditions?: PostCondition[];
  fee?: number;
}) => {
  const params = {
    contractAddress,
    contractName,
    functionName,
    functionArgs,
    senderAddress,
    network: 'mainnet',
    fee,
    ...(postConditions && { postConditions })
  };

  try {
    const result = await request('stx_callContract', params);
    return result;
  } catch (error) {
    console.error("Contract call failed:", error);
    throw error;
  }
};
```

#### Transaction Error Handling
```typescript
const handleTransactionError = (error: any) => {
  if (error.code === 4001) {
    // User rejected the transaction
    console.log("Transaction cancelled by user");
    return { cancelled: true };
  } else if (error.code === -32603) {
    // Internal error
    console.error("Wallet internal error:", error.message);
    return { error: "Wallet error occurred" };
  } else if (error.message?.includes('insufficient funds')) {
    console.error("Insufficient funds");
    return { error: "Insufficient funds for transaction" };
  } else {
    console.error("Unknown transaction error:", error);
    return { error: "Transaction failed" };
  }
};
```

### 3. Message & Structured Data Signing

#### Basic Message Signing for Authentication
```typescript
import { request } from '@stacks/connect';

const signMessageForAuth = async (message: string) => {
  try {
    const result = await request('stx_signMessage', {
      message: message
    });
    
    return {
      signature: result.signature,
      publicKey: result.publicKey
    };
  } catch (error) {
    console.error("Message signing failed:", error);
    throw error;
  }
};

// Usage example for timestamped authentication
const authenticateUser = async (userAddress: string) => {
  const timestamp = Date.now();
  const message = `Authenticate ${userAddress} at ${timestamp}`;
  
  try {
    const authData = await signMessageForAuth(message);
    return {
      ...authData,
      timestamp,
      message
    };
  } catch (error) {
    throw new Error("Authentication failed");
  }
};
```

#### Structured Data Signing
```typescript
import { request, SignatureData } from '@stacks/connect';

const signStructuredData = async (domain: any, message: any) => {
  try {
    const result: SignatureData = await request('stx_signStructuredMessage', {
      domain,
      message
    });
    
    return result;
  } catch (error) {
    console.error("Structured data signing failed:", error);
    throw error;
  }
};

// Example: Intent-based transaction signing
const signIntent = async ({
  contractAddress,
  functionName,
  amount,
  recipient,
  uuid
}: {
  contractAddress: string;
  functionName: string;
  amount: number;
  recipient: string;
  uuid: string;
}) => {
  const domain = {
    name: "MyApp",
    version: "1.0.0",
    chainId: 1
  };
  
  const message = {
    contract: contractAddress,
    function: functionName,
    amount: amount.toString(),
    recipient,
    uuid,
    timestamp: Date.now()
  };
  
  return await signStructuredData(domain, message);
};
```

### 4. Component Integration Patterns

#### Transaction Button Component
```typescript
import React, { useState } from 'react';
import { request } from '@stacks/connect';
import { useWallet } from './WalletContext';

interface TransactionButtonProps {
  contractAddress: string;
  contractName: string;
  functionName: string;
  functionArgs: any[];
  onSuccess?: (txid: string) => void;
  onError?: (error: any) => void;
  disabled?: boolean;
  children: React.ReactNode;
}

const TransactionButton: React.FC<TransactionButtonProps> = ({
  contractAddress,
  contractName,
  functionName,
  functionArgs,
  onSuccess,
  onError,
  disabled,
  children
}) => {
  const { currentAddress, isConnected } = useWallet();
  const [isLoading, setIsLoading] = useState(false);

  const handleClick = async () => {
    if (!isConnected || !currentAddress) {
      alert("Please connect your wallet first");
      return;
    }

    setIsLoading(true);
    try {
      const result = await request('stx_callContract', {
        contractAddress,
        contractName,
        functionName,
        functionArgs,
        senderAddress: currentAddress,
        network: 'mainnet'
      });

      if (result?.txid) {
        onSuccess?.(result.txid);
      }
    } catch (error) {
      console.error("Transaction failed:", error);
      onError?.(error);
    } finally {
      setIsLoading(false);
    }
  };

  return (
    <button 
      onClick={handleClick}
      disabled={disabled || !isConnected || isLoading}
      className={isLoading ? "loading" : ""}
    >
      {isLoading ? "Processing..." : children}
    </button>
  );
};
```

#### Wallet Connection Modal Component
```typescript
import React, { useState } from 'react';
import { connect } from '@stacks/connect';

const WalletModal: React.FC<{ 
  isOpen: boolean; 
  onClose: () => void;
  onConnect: (addresses: any[]) => void;
}> = ({ isOpen, onClose, onConnect }) => {
  const [isConnecting, setIsConnecting] = useState(false);
  const [error, setError] = useState<string | null>(null);

  const handleConnect = async () => {
    setIsConnecting(true);
    setError(null);
    
    try {
      const result = await connect();
      onConnect(result.addresses);
      onClose();
    } catch (error: any) {
      setError(error.message || "Connection failed");
    } finally {
      setIsConnecting(false);
    }
  };

  if (!isOpen) return null;

  return (
    <div className="modal-overlay">
      <div className="modal-content">
        <h2>Connect Wallet</h2>
        <p>Connect your Stacks wallet to interact with the application.</p>
        
        {error && (
          <div className="error-message">{error}</div>
        )}
        
        <div className="modal-actions">
          <button 
            onClick={handleConnect}
            disabled={isConnecting}
            className="primary-button"
          >
            {isConnecting ? "Connecting..." : "Connect Wallet"}
          </button>
          <button onClick={onClose} className="secondary-button">
            Cancel
          </button>
        </div>
      </div>
    </div>
  );
};
```

This documentation covers the basic patterns for integrating `@stacks/connect` into modern web applications, providing both basic functionality and advanced patterns for complex use cases.