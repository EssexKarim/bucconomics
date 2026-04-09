# Welcome to BUCCONOMICS! 

We're thrilled that you'd like to help build BUCCONOMICS — an open-source infrastructure to empower local communities with decentralized financial tools.

This document outlines our collaboration standards, development approach, and contribution process, rooted in Agile, Test-Driven Development (TDD), Behavior-Driven Development (BDD), and Agile Product Management.

## 🚦 Code of Conduct

We’re committed to creating a respectful, inclusive, and safe environment for everyone.

* **Be kind and constructive.**
* **Assume positive intent.**
* **Debate ideas, not people.**
* **Avoid discriminatory or offensive behavior.**

*(See our full Code of Conduct for more details).*

## 📂 Repository Structure (Monorepo)

BUCCONOMICS is structured as a **Monorepo** using **npm workspaces** and **Turborepo**. This allows us to keep our core open-source logic in one place.

* `/contracts`: Our smart contract development environment (powered by **Foundry**).
* `/apps/web`: Our frontend user interfaces (powered by **Next.js**).
* `/apps/api`: Our backend services and adapters (powered by **Node.js**).

## 🚀 How to Contribute

### 1. Propose Ideas or Report Issues
Open a GitHub Issue with a clear problem statement, feature request, or improvement idea. Use the labels `bug`, `enhancement`, or `help wanted` appropriately.

### 2. Discuss or Refine via Discussions
Use GitHub Discussions to collaborate on design, product feedback, or strategic suggestions before coding begins.

### 3. Fork & Create a Feature Branch (GitFlow)
We strictly follow the **GitFlow** branching strategy. Always branch off `develop` (not `main`).

```bash
# Clone your fork locally
$ git clone https://github.com/YOUR_USERNAME/bucconomics.git

# Checkout the develop branch
$ git checkout develop

# Create your feature branch
$ git checkout -b feature/your-feature-name
```

### 4. Write Behavior Specs (BDD)
Use Gherkin syntax to define the behavior before coding:

```gherkin
Feature: Token staking
  Scenario: User stakes BUCC tokens
    Given the user has BUCC tokens
    When the user stakes tokens into a pool
    Then the dashboard shows yield projection
```

### 5. Write Tests (TDD)
Begin with failing unit/integration tests. Commit tests before implementation. Then make them pass.

### 6. Submit a Pull Request
* Push your branch to GitHub and open a Pull Request.
* Reference the related issue in your PR description (e.g., `Closes #21`).
* Ensure tests pass and follow our coding guidelines (below).
* A team member will review your submission and may request changes before merging.

## ✨ Pull Request Template

**What this PR does?**
[Brief description of the changes]

**What issue(s) does this close?** Closes #[Issue Number]

**How to test this PR?**
[Step-by-step instructions]

**Screenshots / Output (if applicable):**
[Images or logs]

**Checklist:**
- [ ] Code runs locally
- [ ] Tests are written or updated
- [ ] README/documentation updated

## 🐛 Bug Report / 💡 Feature Request Template

**Describe your idea or issue:**
[Description]

**Steps to reproduce (if bug):**
1. 
2. 

**Expected behavior:**
[What should happen]

**Proposed solution (if any):**
[Your ideas on how to fix/build it]

**Additional context / screenshots:**
[Anything else we should know]

## 💻 Coding Guidelines

* **Use meaningful names and clear logic.**
* **Prefer composition over inheritance.**
* **Adhere to formatting rules:** Prettier and ESLint are strictly enforced via pre-commit hooks for all JS/TS files.
* **Smart Contracts:** We allow a floating pragma (e.g., `pragma solidity ^0.8.0;`) to ensure compatibility with audited forks. Inherit from the latest OpenZeppelin libraries.
* **Write readable, well-commented code.** Use JSdoc or NatSpec as needed.
* *If you're not sure about style, check other files in the repo or ask in a discussion!*

## ✅ Testing & Validation

Follow TDD: write failing tests before implementing features. Aim for high coverage of critical paths (e.g., lending, governance logic). We welcome tests for edge cases, smart contract security, and regression prevention.

Because we use a monorepo, testing is handled through specific frameworks:
* **Smart Contracts:** Use **Foundry**. Tests are written in Solidity.
* **Web & API:** Use **Jest** or **Vitest**.

### Running Tests Locally

To install dependencies across all workspaces and the Foundry environment:
```bash
npm install
forge install
```

To run all tests globally across the entire monorepo (via Turborepo):
```bash
npm run test
```

To test only the smart contracts:
```bash
cd contracts
forge test
```

## 🔄 Agile & Iterative Delivery

We work in short iterations. If your contribution is part of a larger feature:
* Break it down into smaller, testable parts.
* Submit MVPs or working slices.
* Add your work to the `/projects` Kanban board if relevant.

## 🙌 Thank You

Whether you're fixing a typo, designing governance flows, or writing Solidity — your contribution matters. We're building this for everyone, with everyone.

**Rayyan & The BUCCONOMICS OS Squad** ✊
