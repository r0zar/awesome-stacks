# ⚡ Awesome Stacks [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of awesome resources, tools, and projects for building on Stacks - Bitcoin's leading Layer 2 for smart contracts, apps, and DeFi.

Stacks enables decentralized apps and predictable smart contracts using the Clarity language, secured by Bitcoin through Proof of Transfer (PoX).

## Contents

- [Getting Started](#getting-started)
  - [API Access Setup](#api-access-setup)
- [Official Documentation](#official-documentation)
- [Development Tools](#development-tools)
- [Smart Contracts & Clarity](#smart-contracts--clarity)
- [Frontend Development](#frontend-development)
- [Backend & Infrastructure](#backend--infrastructure)
- [DeFi Development](#defi-development)
- [NFTs & Digital Assets](#nfts--digital-assets)
- [Bitcoin Integration](#bitcoin-integration)
- [Tutorials & Guides](#tutorials--guides)
- [Sample Projects](#sample-projects)
- [Developer Programs](#developer-programs)
- [Community](#community)
- [Contributing](#contributing)

## Getting Started

### Quick Start Resources
- [Developer Quickstart](https://docs.stacks.co/guides-and-tutorials/hello-stacks-quickstart-tutorial) - Complete app in about an hour
- [Stacks Primer](https://www.stacks.co/primer) - 5-day email course from basics to first contract
- [Start Building on Bitcoin](https://www.stacks.co/build/get-started) - Official getting started guide

### Learning Platforms
- [LearnWeb3 Stacks Developer Degree](https://learnweb3.io/) - Full-stack applications with Clarity and Stacks.js
- [Clarity Universe](https://clarity-lang.org/universe) - Start-to-finish Clarity guide with self-paced and cohort options
- [The Clarity Book](https://book.clarity-lang.org/) - Comprehensive Clarity development resource

### Development Environment Setup
- [Clarinet Installation](https://github.com/hirosystems/clarinet) - Local development and testing environment
- [Hiro Platform Setup](https://platform.hiro.so/) - Cloud development environment
- [VS Code Clarity Extension](https://marketplace.visualstudio.com/items?itemName=HiroSystems.clarity-lsp) - IDE support for Clarity

### API Access Setup
- [Hiro API Key Setup](https://docs.hiro.so/resources/guides/api-keys) - **Essential**: Get your free API key for blockchain data access
- [API Key Management](https://platform.hiro.so/projects) - Manage API keys, monitor usage, and upgrade limits
- [Rate Limits & Pricing](https://docs.hiro.so/resources/guides/rate-limits) - Understanding API rate limits and paid tiers

> **⚠️ Important**: A Hiro API key is required for almost all read-only API calls including balance queries, transaction history, on-chain analytics, and blockchain data access. Without an API key, you'll be limited to basic testing only.

## Official Documentation

### Core Documentation
- [Stacks Documentation](https://docs.stacks.co/) - Official comprehensive documentation
- [Clarity Language Reference](https://docs.stacks.co/docs/clarity) - Complete Clarity language documentation
- [Stacks.js Documentation](https://stacks.js.org/) - Frontend library documentation
- [API Reference](https://docs.hiro.so/api) - Stacks blockchain API documentation

### Technical Specifications
- [Stacks Improvement Proposals (SIPs)](https://github.com/stacksgov/sips) - Protocol specifications and improvements
- [Clarity Language Specification](https://github.com/clarity-lang/reference) - Language specification and semantics

## Development Tools

### CLI Tools
- [Clarinet](https://github.com/hirosystems/clarinet) - Clarity runtime packaged as CLI, testing and deployment
- [@stacks/cli](https://www.npmjs.com/package/@stacks/cli) - Command-line interface for Stacks blockchain for humans+AI

### IDE & Editors
- [Clarity LSP](https://github.com/hirosystems/clarity-lsp) - Language server protocol for Clarity
- [Clarity VS Code Extension](https://marketplace.visualstudio.com/items?itemName=HiroSystems.clarity-lsp) - Syntax highlighting and debugging

### Testing & Debugging
- [Clarinet Console](https://docs.hiro.so/clarinet/guides/clarinet-console) - Interactive Clarity REPL
- [Stacks Devnet](https://docs.stacks.co/understand-stacks/local-development) - Local development network
- [Clarity WASM](https://github.com/hirosystems/clarity-wasm) - WebAssembly implementation for testing

### Deployment & CI/CD
- [Hiro Platform](https://platform.hiro.so/) - Hosted deployment and management
- [Clarinet Deployments](https://docs.hiro.so/clarinet/guides/deploy-contracts) - Contract deployment workflows
- [GitHub Actions for Stacks](https://github.com/marketplace/actions/clarinet) - CI/CD integration

### Contract Launchpads
- [Charisma Launchpad](https://launchpad.charisma.rocks/) - No-code contract deployment and token launch platform
- [Charisma Metadata Hosting](https://metadata.charisma.rocks/) - Hosted metadata creation and storage service for tokens and NFTs

## Smart Contracts & Clarity

### Language Resources
- [Clarity by Example](https://clarity-lang.org/tutorial) - Interactive examples and tutorials
- [Clarity Standard Library](https://docs.stacks.co/references/language-clarity) - Built-in functions and traits
- [Clarity Keywords Reference](https://docs.stacks.co/references/language-keywords) - Complete keyword documentation

### Best Practices & Patterns
- [Clarity Security Guidelines](https://docs.stacks.co/write-smart-contracts/security) - Security best practices
- [Design Patterns in Clarity](https://docs.stacks.co/write-smart-contracts/clarity-primer) - Common patterns and idioms
- [Testing Strategies](https://docs.hiro.so/clarinet/guides/test-contract-with-clarinet) - Unit testing and integration testing

### Contract Libraries & Standards
- [SIP-009 NFT Standard](https://github.com/stacksgov/sips/blob/main/sips/sip-009/sip-009-nft-standard.md) - Non-fungible token standard
- [SIP-010 Fungible Token Standard](https://github.com/stacksgov/sips/blob/main/sips/sip-010/sip-010-fungible-token-standard.md) - Fungible token standard
- [Clarity Universe Contracts](https://github.com/clarity-lang/clarity-universe) - Community contract library

## Frontend Development

### Core Libraries
- [Stacks.js](https://stacks.js.org/) - Official JavaScript library for Stacks integration
- [@stacks/connect](https://github.com/hirosystems/connect) - Wallet connection library

### Starters & Templates
- [Stacks.js Starters](https://github.com/hirosystems/stacks.js-starters) - Official starter templates
- [Next.js Stacks Template](https://github.com/hirosystems/stacks-nextjs-template) - Next.js application template
- [Create Stacks App](https://github.com/fungible-systems/create-stacks-app) - CLI for creating Stacks apps

## Backend & Infrastructure

### Chain Explorers
- [Stacks Explorer by Hiro](https://explorer.hiro.so/?chain=mainnet) - Block explorer functionality by Hiro
- [Charisma Lakehouse](https://lakehouse.charisma.rocks/) - Real-time financial activity explorer with advanced analytics
- [STX Tools](https://stxtools.io/) - Comprehensive Stacks blockchain explorer and tools

### Indexing & Analytics
- [Hiro API Documentation](https://hirosystems.github.io/stacks-blockchain-api/) - REST API and WebSocket for Stacks
- [Hiro Token Metadata API](https://docs.hiro.so/apis/token-metadata-api) - Official NFT and token metadata service
- [Charisma Token Metadata API](https://tokens.charisma.rocks/) - Community-driven token metadata service
- [On-Chain Realtime Events Hook](https://github.com/hirosystems/chainhook) - Trigger workflows based on on-chain events

### Node & Infrastructure
- [Stacks Core](https://github.com/stacks-network/stacks-core) - Reference implementation in Rust
- [Hiro API Source Code](https://github.com/hirosystems/stacks-blockchain-api) - Hiro blockchain API source code
- [Stacks Node Docker](https://docs.stacks.co/understand-stacks/running-mainnet-node) - Containerized node setup
- [QuickNode Stacks](https://www.quicknode.com/chains/stacks) - RPC endpoints and infrastructure

## DeFi Development

### DEX & AMM Protocols
- [ALEX](https://alexgo.io/) - DeFi infrastructure and AMM on Stacks
- [Velar](https://app.velar.com/swap) - Modern DEX with advanced trading features
- [Charisma](https://swap.charisma.rocks/) - Community-driven decentralized exchange
- [BitFlow](https://www.bitflow.finance/) - High-performance DEX on Stacks

### Lending & Borrowing
- [Zest Protocol](https://zestprotocol.com/) - Bitcoin lending on Stacks
- [Granite](https://www.granite.world/) - Bitcoin lending protocol on Stacks

## NFTs & Digital Assets

### NFT Standards & Libraries
- [SIP-009 Implementation](https://github.com/stacksgov/sips/blob/main/sips/sip-009/sip-009-nft-standard.md) - NFT standard reference
- [Stacks NFT Library](https://github.com/hirosystems/stacks-nft) - NFT development tools

### NFT Marketplaces
- [Gamma.io](https://gamma.io/) - NFT marketplace for Stacks & Bitcoin NFTs

### Creation Tools
- [NFT Minting Tools](https://docs.stacks.co/build-apps/guides/mint-nfts) - Guide to minting NFTs
- [Collection Creator](https://gamma.io/create) - No-code NFT collection creation
- [NFT Metadata Standards](https://docs.hiro.so/apis/token-metadata-api) - NFT metadata best practices and standards

## Bitcoin Integration

### Bitcoin Capabilities
- [sBTC](https://sbtc.tech/) - Programmable Bitcoin on Stacks
- [Bitcoin Block Headers](https://docs.stacks.co/docs/clarity/bitcoin-integration) - Reading Bitcoin state in Clarity
- [UTXO Verification](https://docs.stacks.co/write-smart-contracts/bitcoin-integration) - Bitcoin transaction verification
- [Bitcoin RPC Integration](https://docs.hiro.so/api#tag/Bitcoin) - Bitcoin data through Stacks API

### Proof of Transfer (PoX)
- [PoX Contract](https://github.com/stacks-network/stacks-core/tree/master/stackslib/src/chainstate/stacks/boot) - Core PoX implementation
- [Stacking Guide](https://docs.stacks.co/understand-stacks/stacking) - How to participate in Stacking
- [Delegation Pools](https://pool.stacks.co/) - Stacking pool implementations

## Tutorials & Guides

### Beginner Tutorials
- [Hello Stacks Tutorial](https://docs.stacks.co/guides-and-tutorials/hello-stacks-quickstart-tutorial) - First Stacks application
- [Counter Tutorial](https://docs.stacks.co/guides-and-tutorials/building-counter) - Simple smart contract example
- [NFT Tutorial](https://docs.stacks.co/build-apps/guides/mint-nfts) - Creating and minting NFTs

### Advanced Guides
- [DeFi Protocol Building](https://docs.stacks.co/guides-and-tutorials/build-a-borrowing-and-lending-protocol) - Complex DeFi application development

### Video Tutorials
- WIP...

## Sample Projects

### Starter Projects
- [Hello Stacks](https://github.com/hirosystems/hello-stacks) - Basic Stacks application
- [STX Transfer](https://github.com/hirosystems/stx-transfer) - Simple token transfer app
- [Clarity Counter](https://github.com/hirosystems/clarity-counter) - Smart contract example

### WIP...

## Developer Programs

### Grants & Funding
- [Stacks Foundation Grants](https://grants.stacks.org/) - Official grant program
- [Bitcoin Frontier Fund](https://bitcoinfrontierfund.org/) - Early-stage funding
- [Stacks Ventures](https://stacks.vc/) - Investment and acceleration

### Accelerators & Incubators
- [Bitcoin Startup Lab](https://bitcoinstartuplab.com/) - Bitcoin-focused accelerator
- [Stacks Accelerator](https://stacks.org/accelerator) - Official accelerator program
- [Trust Machines Incubator](https://trustmachines.co/) - Bitcoin application incubator

### Bounty Programs
- [Code for STX](https://www.stacks.co/code-for-stx) - Monthly STX rewards for builders
- [Bug Bounty Program](https://github.com/stacks-network/stacks-core/security) - Security vulnerability rewards
- [Community Challenges](https://github.com/stacksgov/community-challenges) - Community-driven bounties

### Developer Communities
- [Clarity Collective](https://clarity.community/) - Exclusive community for proven builders
- [Stacks Discord](https://discord.gg/stacks) - Active developer community
- [Developer Office Hours](https://www.stacks.co/office-hours) - Weekly developer support

## Community

### Official Channels
- [Stacks Website](https://www.stacks.co/) - Official project website
- [Stacks Blog](https://blog.stacks.co/) - Official announcements and updates
- [Stacks Twitter](https://twitter.com/stacks) - Latest news and community updates

### Developer Communities
- [Stacks Discord](https://discord.gg/stacks) - Active developer discussions
- [Reddit r/stacks](https://reddit.com/r/stacks) - Community discussions
- [Stacks Forum](https://forum.stacks.org/) - In-depth technical discussions

### Regional Communities
- [Stacks Japan](https://stacks.jp/) - Japanese Stacks community
- [Stacks India](https://twitter.com/stacksindia) - Indian developer community
- [Stacks Africa](https://twitter.com/stacksafrica) - African Stacks builders

### Events & Meetups
- [Developer Workshops](https://www.stacks.co/events) - Technical workshops and hackathons

## Contributing

We welcome contributions to this awesome list! Please read our [contributing guidelines](CONTRIBUTING.md) before submitting.

### How to Contribute
1. Fork this repository
2. Add your awesome resource to the appropriate section
3. Ensure the resource is relevant to Stacks development
4. Submit a pull request with a clear description

### Contribution Guidelines
- Resources should be actively maintained and documented
- Include a brief description explaining why the resource is awesome
- Check that the resource isn't already listed
- Maintain alphabetical ordering within sections
- Follow the existing format and style

### Quality Standards
- Resources must be directly relevant to Stacks blockchain development
- Links should be active and pointing to quality content
- Prefer official documentation and actively maintained projects
- Community resources should have proven value to developers

---

## License

[![CC0](https://mirrors.creativecommons.org/presskit/buttons/88x31/svg/cc-zero.svg)](https://creativecommons.org/publicdomain/zero/1.0/)

This work is licensed under a [Creative Commons CC0 1.0 Universal License](https://creativecommons.org/publicdomain/zero/1.0/).