# Shared Prompt Template

Use this template for new agents and for major rewrites of weak prompts. Strong existing prompts do not need to be forced into this exact wording unless they are being materially changed.

## Template

### 1. Role

State the role and exact system domain.

Example:
- `You are a Principal <Domain> Agent/Auditor for ML systems.`

### 2. Only Task

Define the boundary in one sentence.

Example:
- `Your only task is to audit <scope>.`

### 3. Non-Goals

List what the agent must not do.

Rules:
- include adjacent responsibilities that belong to other agents
- forbid silent assumption-making where production risk exists
- forbid scope expansion beyond the stated responsibility

### 4. Focus

List the narrow dimensions the agent is responsible for.

Rules:
- use capability language, not generic quality language
- make edge-case areas explicit where relevant

### 5. Required Inputs

State what the agent should inspect or require before proceeding.

Preferred fields:
- source artifacts
- contract artifacts
- upstream reports
- configs
- schemas
- runtime context

### 6. Mission

Use numbered steps.

Recommended structure:
1. Identify scope-specific entrypoints or artifacts.
2. Document the current state with explicit fields.
3. Audit correctness and compatibility.
4. Detect risks and edge cases.
5. Produce machine-readable contract or manifest if this agent owns one.
6. Produce a human-readable report.
7. Add validation recommendations or checks.

### 7. Deliverables

List exact output paths.

Rules:
- use deterministic paths
- separate machine-readable artifacts from narrative reports
- avoid inventing multiple overlapping artifacts unless necessary

### 8. Upstream Prerequisites

State what must exist before the agent should run.

Examples:
- metadata inventory
- target definition
- feature contract
- evaluation outputs
- registry state

### 9. Downstream Handoff

State which agents consume this output and what they rely on.

Rules:
- make dependencies explicit
- include both machine and human artifacts where relevant

### 10. Validation Rules

State specific checks the agent recommends or implements.

Rules:
- prefer executable validations over vague review language
- include fail-fast checks where production safety matters

### 11. Stop Conditions

State when the agent must stop and escalate.

Examples:
- ambiguous schema semantics
- missing target maturity rules
- unresolved upstream contract conflicts
- missing required artifacts for release

### 12. Final Validation

State what must be true before the agent can complete.

### 13. Final Response Must Include

Use a stable output summary shape:
- major issues found
- artifacts created or updated
- validation checks added or recommended
- unresolved assumptions

## Shared Conventions

- Every agent should name upstream prerequisites and downstream handoff explicitly.
- Every contract-producing agent should conform to the shared contract envelope.
- Every final report should separate blockers from warnings where applicable.
- Every prompt should preserve production edge cases around grain, partitions, target maturity, reruns, and rollback where relevant.
