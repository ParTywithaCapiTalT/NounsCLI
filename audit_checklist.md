Fiduciary-First Security Audit Checklist

Before submitting a Pull Request, please ensure your changes satisfy the following security and integrity requirements. This checklist is mandatory for all modules impacting DAO treasury or governance.1. Permission Handoff Verification
Atomic Revocation: Does the module ensure that administrative roles (e.g., DEFAULT_ADMIN_ROLE) are revoked from the deployer address immediately upon initialization?
No "Backdoor" Access: Verify that no hardcoded addresses or specific deployer logic persists after the initialization sequence.
Immutable Governance: Ensure that ownership of the Treasury or Governor contract cannot be re-claimed by the deployer account once handed off to the DAO.
2. Deterministic Deployment (CREATE2)
Salt Uniqueness: If introducing new factory logic, does the salt generation include unique, user-defined parameters to prevent deployment collisions?
Bytecode Integrity: Does the module maintain bytecode consistency across chains? Any deviations must be explicitly audited and documented in the PR.
3. Transaction Integrity (Viem)
Batch Safety: If utilizing Viem's batching or multicall functions, ensure that an error in one transaction triggers a full revert of the initialization sequence to prevent "partial deployments."
Gas Estimation: Have you simulated the gas costs? The initialization sequence must be performant and not exceed standard block gas limits for the targeted chains.
4. Testing & Simulations
Dry-Run Validated: Did you execute pnpm start deploy --dry-run with your new module, and did it pass the automated security audit check?
Negative Testing: Have you included a test case where the deployment is intentionally "broken" (e.g., providing invalid config) to ensure the system fails securely without creating orphaned contracts?
