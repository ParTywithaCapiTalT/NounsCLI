CONTRIBUTING.md

This document outlines the guidelines for contributing to the Nouns Builder Launch-CLI. By prioritizing the Fiduciary-First philosophy, we ensure that all code contributions maintain the integrity and security of the DAOs initialized through our pipeline.
1. Contribution Philosophy

We are building a modular, developer-first tool. All contributions must adhere to our security-first mandate:
Security-First: Every PR involving contract interaction or permission handling requires a comprehensive test suite.
Modular Extensibility: We encourage the creation of new treasury, governor, or metadata modules. Keep code modular and decoupled to ensure auditability.
Deterministic Integrity: New features must not break the CREATE2 deterministic deployment flow.

2. Development Setup

To contribute to the CLI, ensure your environment matches our production specifications:
Fork and Clone: Fork the repository and clone your branch locally.
Dependencies: Run pnpm install to set up the environment.
Testing: Execute the full test suite using pnpm test before submitting changes.

3. Submitting New Modules


We welcome contributions that expand the utility of the Launch-CLI. To submit a new treasury or governor module:
Structure: Place all new logic within the src/modules/ directory.
Verification: Ensure your module follows the standard Module interface defined in src/types/.
Integration: Include a module_test.ts file demonstrating the permission handoff logic for your specific module.
Documentation: Update the README.md to reflect new parameters or configuration requirements introduced by your module.

4. Pull Request Workflow

Issue Tracking: Open an issue to discuss your proposed module or improvement before writing code.
Branching: Use descriptive branch names (e.g., feat/new-treasury-module or fix/security-handoff).
Code Review: All PRs are subject to a security review focusing on:
Prevention of unauthorized admin role retention.
Correct usage of Viem for transaction batching.
Gas optimization.
Testing: PRs will not be merged without passing all CI/CD integration tests, including the dry-run simulations.

5. Code Standards

Language: TypeScript (Strict mode enabled).
Framework: Viem (required for all chain interactions).
Style: Follow the existing project structure and linting configuration (.eslintrc).
