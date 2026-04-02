# BUCCONOMICS: Code Standards and Defaults

## 1. Repository & Version Control

* **Architecture:** The open-source protocol will be structured as a **Monorepo** using **npm workspaces** and **Turborepo**. This allows the frontend components, backend services, and smart contracts to exist in a single repository with shared dependencies and lightning-fast, cached build times.
* **Submodule Integration:** This open-source monorepo will be imported as a Git Submodule within the private, proprietary repository, allowing developers to build proprietary features on top of the public protocol.
* **Branching Strategy:** The repository will strictly adhere to the **GitFlow** workflow:
  * `main`: The immutable representation of production-ready code. Commits here represent formal releases.
  * `develop`: The active integration branch where all tested features are combined.
  * `feature/*`: Short-lived branches created from `develop` for individual tasks.
  * `release/*`: Branches cut from `develop` to stabilize, test, and finalize a deployment before merging to `main`.
  * `hotfix/*`: Urgent production fixes cut directly from `main` and merged back into both `main` and `develop`.

## 2. Tooling & Package Management

* **Package Manager:** **npm** will be the exclusive package manager.
* **Task Orchestration:** **Turborepo** will manage scripts (`npm run build`, `npm run test`) across all workspaces simultaneously.
* **Formatting & Linting:**
  * **Prettier:** Configured globally and enforced via Git pre-commit hooks to ensure uniform code style.
  * **ESLint:** Strictly configured for all TypeScript/JavaScript environments to catch syntax and architectural errors before they reach pull requests.


  ## 3. Smart Contract Standards

* **Development Framework:** **Foundry** will be the primary toolchain for compiling, deploying, and testing smart contracts. Its Rust-based architecture ensures rapid build times, and writing tests in Solidity provides better alignment with the core logic.
* **Solidity Versioning:** A **floating pragma** (e.g., `pragma solidity ^0.8.0;`) is permitted and encouraged to ensure seamless integration and compilation with forked, pre-audited protocols (such as the Goldfinch tranche logic).
* **Security & Dependencies:**
  * **OpenZeppelin:** All standard token implementations (ERC-20, ERC-721/SBT) and access control mechanisms must inherit from the latest secure OpenZeppelin library releases.
  * **Testing:** All pull requests involving smart contracts must include Foundry test coverage (`forge test`) covering positive, negative, and edge-case scenarios. 
* **Deployment:** Deployment scripts will be managed via Foundry's `forge script`, with clear separation between local, testnet (Base Sepolia), and mainnet (Base) configurations.

## 4. Application Standards (Frontend & Backend)

* **Language:** **Strict TypeScript** will be used across all web application codebases. The monorepo structure will be utilized to share standard interfaces (e.g., agnostic provider models) between the frontend and backend.
* **Frontend Framework:** **Next.js (React)** will be used for the web application (Unified Dashboard, KYC widgets, Forum UI). It offers robust performance, built-in API routes if needed, and excellent ecosystem support for Web3 libraries.
* **Backend Framework:** **Node.js** will power the API services (Community API, DAO Bridge, Webhook listeners). 
* **API Design:** All backend services will follow standard RESTful principles, returning predictable JSON payloads.
* **State Management & Web3 Hooks:** The frontend will utilize standard React hooks, abstracting Web3 interactions behind the provider-agnostic adapter patterns defined in the architecture.