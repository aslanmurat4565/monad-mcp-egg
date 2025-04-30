# EggManager: MCP Madness Submission

## Project Purpose
This project, **EggManager**, was created for the **MCP Madness** competition hosted by Monad Devs (@monad_dev) on April 17, 2025. The goal was to build an MCP (Model Context Protocol) server that interacts with the Monad Testnet using AI tools. My idea was to create a gamified quiz system where users can:
- Answer questions of varying difficulty (easy, medium, hard) to earn points.
- Upon reaching a progress threshold (3 points), receive a **Soulbound Token (EggSBT)** and a corresponding amount of **GameToken** as a reward.
- Interact with the system through an MCP server that communicates with smart contracts deployed on the Monad Testnet.

The project aims to demonstrate how gamification can be integrated into blockchain applications, rewarding users with non-transferable tokens (SBTs) for their achievements while using Monad's high-performance Testnet.

## Challenges Faced
During the development process, we encountered several significant challenges:
- **Private Key Issue**: The private key provided for the Monad Testnet was 65 characters long (excluding `0x`), while tools like Hardhat and Foundry expected a 64-character key (32 bytes). This caused errors like *"Invalid account: #0 for network: monadTestnet - private key too short, expected 32 bytes"*. We suspect this mismatch may be due to Monad Testnet using a non-standard key format, possibly related to a custom virtual machine (e.g., SEVM-like).
- **Monad Testnet Compatibility**: Initially, we tried using Hardhat and Foundry to deploy the smart contracts, but both tools failed due to potential incompatibilities with Monad Testnet. Although Monad is described as "EVM-compatible," it may not fully align with standard EVM tools, leading us to explore alternatives like Truffle and Ethers.js.
- **Time Constraints**: The competition deadline was April 30, 2025, at 10:00 AM +03, and we faced these technical issues in the final minutes. This prevented us from successfully deploying the contracts and running the MCP server on the Monad Testnet in time.

Despite these challenges, the smart contracts and MCP server are fully implemented and ready to be deployed with the right tools.

## Technical Overview
- **Smart Contracts** (`contracts/EggManager.sol`):
  - `EggSBT`: A non-transferable ERC721 Soulbound Token representing user achievements.
  - `GameToken`: An ERC20 token used as a reward for earning EggSBTs.
  - `EggManager`: Manages the quiz logic, tracks user progress, and distributes rewards.
- **MCP Server** (`src/index.ts`):
  - Built using the `@modelcontextprotocol/sdk` library.
  - Provides tools for starting a quiz, answering questions, checking progress, and viewing earned tokens.
  - Designed to interact with the `EggManager` contract on the Monad Testnet.

## Notice
Due to the technical challenges mentioned above, we were unable to deploy the smart contracts and run the MCP server on the Monad Testnet before the competition deadline (April 30, 2025, 10:00 AM +03). However, the project is fully implemented and documented here for review. I have shared the GitHub repository link on the Monad Devs Discord channel and requested consideration for a late submission, as the core idea and implementation are complete.

## Setup Instructions
1. **Clone the Repository**:
   ```bash
   git clone https://github.com/<your-username>/monad-mcp-egg.git
   cd monad-mcp-egg
