# Agents Repository

This repository is organized by ML project lifecycle phase.

Prompt files are stored as Markdown prompts with YAML front matter:
- `agents/<lifecycle_phase>/primary/<agent_name>.md`
- `agents/<lifecycle_phase>/specialist/<agent_name>.md`

`child` role types are stored under `primary/` and remain distinguishable in prompt metadata and the registry.

## Layout

- `agents/`
  Lifecycle-organized prompt corpus.
- `agent_framework/`
  Governance layer for lifecycle definitions, orchestration, shared standards, and registry metadata.
- `docs/`
  Practical usage guides for applying the framework.
- `reports/`
  Meta-review and framework implementation reports.

## Scientific Rigor Specialist Layer

The framework includes an optional Scientific Rigor specialist layer for cases where conclusions depend on:
- statistical validity
- causal or experimental validity
- sampling and representativeness validity

These are specialist gates, not default primary agents. Use them when ML, analytics, experimentation, uplift, response modeling, or business decisioning claims need deeper rigor before downstream sign-off.

## Choose Agents By Phase

### 1. Intake and scope

Use:
- `agents/01_intake_and_scope/primary/task_triage_router.md`
- `agents/01_intake_and_scope/primary/multi_agent_orchestrator.md`
- `agents/01_intake_and_scope/specialist/overengineering_control.md`

Use this phase when you are defining scope, assigning ownership, or deciding how much production rigor is actually required.

### 2. Repository runtime foundation

Use:
- `agents/02_repository_runtime_foundation/`

Use this phase when environment assumptions, repository layout, dependencies, security, documentation, or patch review need to be stabilized before deeper ML work.

### 3. Exploratory analysis and metric definition

Use:
- `agents/03_exploratory_analysis_and_metric_definition/`

Use this phase when KPI definitions, cohort logic, active-user logic, segment naming, EDA quality, business insight quality, or scientific rigor around statistics, causal claims, and sampling validity need to be established.

### 4. Data foundation and contracts

Use:
- `agents/04_data_foundation_and_contracts/`

Use this phase before SQL generation, schema mapping, dataset contract formalization, or join and partition safety review.

### 5. Dataset feature target integrity

Use:
- `agents/05_dataset_feature_target_integrity/`

Use this phase when target policy, label quality, feature governance, feature availability, business-facing score meaning, or temporal leakage must be made explicit.

### 6. Training evaluation and registry

Use:
- `agents/06_training_evaluation_and_registry/`

Use this phase when validating split policy, reproducibility, evaluation, thresholding, comparison fairness, or model registry governance.

### 7. Inference outputs and decisioning

Use:
- `agents/07_inference_outputs_and_decisioning/`

Use this phase when validating inference determinism, offline-online parity, output schemas, or release gating for inference-capable artifacts.

### 8. Monitoring operational resilience

Use:
- `agents/08_monitoring_operational_resilience/`

Use this phase when focusing on monitoring, drift, test coverage, orchestration safety, preflight checks, rerun safety, silent failures, or rollback readiness.

### 9. Final integration and release gates

Use:
- `agents/09_final_integration_and_release_gates/`

Run these in strict order:
1. `integration_consistency`
2. `production_readiness_auditor`
3. `end_to_end_ml_auditor`
4. `acceptance_criteria_verifier`

Use this phase only after upstream lifecycle outputs and contracts are available.

## Recommended Execution Order

Lifecycle folders are numbered to reflect the default ML project execution sequence from intake through release.

Prompt files themselves are not numbered because the recommended ordering lives in framework metadata rather than filenames.

Use `phase_order` and `agent_order` in [agent_framework/agent_registry.yaml](/Users/anastasiia.m/Documents/My%20projects/Agents/agent_framework/agent_registry.yaml) when you need deterministic automation or programmatic routing.

## Governance References

- [docs/how_to_use_agent_workflow.md](/Users/anastasiia.m/Documents/My%20projects/Agents/docs/how_to_use_agent_workflow.md)
- [agent_framework/README.md](/Users/anastasiia.m/Documents/My%20projects/Agents/agent_framework/README.md)
- [agent_framework/lifecycle_groups.md](/Users/anastasiia.m/Documents/My%20projects/Agents/agent_framework/lifecycle_groups.md)
- [agent_framework/orchestration_graph.md](/Users/anastasiia.m/Documents/My%20projects/Agents/agent_framework/orchestration_graph.md)
- [agent_framework/agent_registry.yaml](/Users/anastasiia.m/Documents/My%20projects/Agents/agent_framework/agent_registry.yaml)
- [agent_framework/agent_dependencies.yaml](/Users/anastasiia.m/Documents/My%20projects/Agents/agent_framework/agent_dependencies.yaml)
- [agent_framework/agent_lifecycle_map.yaml](/Users/anastasiia.m/Documents/My%20projects/Agents/agent_framework/agent_lifecycle_map.yaml)
