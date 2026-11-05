# TrustFlow SDK — Wave Program Sprint Plan

## Overview
The Wave Program accelerates TrustFlow SDK development through scoped, well-defined issues that external contributors complete during time-boxed sprint cycles. Maintainers break down the protocol roadmap into independent tasks with explicit acceptance criteria, designated source files, and test expectations.

---

## Planned Issue Types & Scoped Work

### 1. Bug Fixes (Low to Medium Complexity)
Targeting edge cases, error propagation, and state synchronization:
- **Contract & Invocation**: Correct resource fee safety margins in `invokeContract` and handle transient Soroban RPC timeouts cleanly.
- **Multisig Escrow**: Validate signer arrays and signature sets during `importState` deserialization.
- **React Hooks**: Ensure `useBalance` and `useEscrow` reset cached data and errors upon account disconnect or wallet change.
- **Data & Storage**: Sanitize CIDv1 base58btc multihash inputs and prevent malformed milestone claim parameters.

### 2. New Features (Medium to Large Complexity)
Extending core SDK capabilities on Stellar and Soroban:
- **Resource Footprint Estimation**: Provide utilities to calculate CPU instruction count and RAM footprint prior to transaction submission.
- **Pluggable Wallet Adapters**: Expand wallet connectors beyond Freighter to include WalletConnect v2 and Lobstr.
- **Batch Contract Operations**: Support bundled milestone funding and atomic claims through Soroban transaction pipelines.
- **Real-Time Event Streams**: Add WebSocket-based contract event subscriptions with automatic reconnect logic.

### 3. Testing & QA (Low to Medium Complexity)
Strengthening test coverage and protocol invariants:
- **Soroban Mock RPC**: Expand mock harnesses in `src/testing/` to simulate ledger latency, sequence mismatches, and contract rollbacks.
- **Escrow State Fuzzing**: Introduce property-based tests for escrow transitions (Funded → Milestone Review → Dispute → Juror Resolution).
- **Testnet E2E Suite**: Add automated end-to-end integration flows targeting Stellar Testnet.

### 4. Documentation & Developer Experience (Low Complexity)
Lowering friction for developers building on TrustFlow:
- **Integration Guides**: Build interactive guides for escrow lifecycle management and React frontend integration.
- **TypeDoc & API Reference**: Ensure comprehensive JSDoc coverage across public client methods and types.
- **Error Remediation Catalog**: Document all `TrustFlowError` codes alongside probable causes and recommended fixes.

### 5. Performance & Refactoring (Medium Complexity)
Maintaining modularity, security, and a minimal footprint:
- **Bundle Optimization**: Audit sub-path exports (`/escrow`, `/react`, `/wallet`) against `.size-limit.json` to prevent tree-shaking regressions.
- **Schema Harmonization**: Align Zod validation schemas strictly with generated Soroban contract types.

---

## Sprint Workflow & Issue Structure
Every posted Wave issue follows a structured format:
- **Context & Pointers**: Contextual background with direct file/line references.
- **Acceptance Criteria**: Clear, testable checklist for PR review.
- **Verification**: Required unit and coverage tests (`npm run test:coverage`, `npm run typecheck`).
- **T-Shirt Sizing**: Labeled with difficulty (`wave:beginner`, `wave:intermediate`, `wave:advanced`).
