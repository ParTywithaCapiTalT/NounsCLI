Getting Started: Establishing the Pipeline

This repository serves as a verifiable, fiduciary-first deployment pipeline. We prioritize transparent, reproducible builds to ensure that every DAO initialized by the Launch-CLI matches the pre-audited security specifications.1. Prerequisites

Ensure you are using an environment that supports deterministic build patterns:
Node.js: v18.x (LTS) or higher.
Package Manager: pnpm (recommended for strict dependency locking).
2. Installation & Build

Clone the repository and initialize the secure environment:
# Clone the repository
git clone https://github.com/your-org/nouns-builder-launch-cli
cd nouns-builder-launch-cli

# Install dependencies and build the artifact
pnpm install
pnpm run build
3. Secure Configuration

For security, this CLI utilizes an environment-based configuration to prevent hardcoded credentials. Copy the configuration template:
cp .env.example .env
Required Environment Variables:
RPC_URL: Secure endpoint for deployment execution.
DEPLOYER_PK: The deployer account (kept private and local).
FACTORY_ADDRESS: The verified NounsBuilderV2 Factory address.
4. Verifiable Dry-Run

To provide the "proof" requested by reviewers, you can execute a dry run. This simulates the CREATE2 deployment and permission handoff without broadcasting to the chain, allowing for architecture verification:
# Simulate the Fiduciary-First Handoff
pnpm start deploy --dry-run
This command verifies that your local environment is configured to properly transfer administrative roles to the DAO Treasury immediately upon initialization
