# ML Multi-Agent Framework

This directory defines the framework layer around the lifecycle-organized prompt corpus under `agents/`. It standardizes lifecycle placement, registry metadata, orchestration order, prompt structure, and contract shape without flattening the domain-specific rigor already present in the specialized agents.

## Repository Structure

The prompt corpus now lives under:

- `agents/<lifecycle_phase>/primary/<agent_name>.md`
- `agents/<lifecycle_phase>/specialist/<agent_name>.md`

Agents with registry `role_type: child` are stored under `primary/` while keeping their explicit role type in metadata and the registry.

High-level layout:

- `agents/`
- `agent_framework/`
- `reports/`
- `README.md`

## Canonical Lifecycle

1. `intake_and_scope`
2. `repository_runtime_foundation`
3. `exploratory_analysis_and_metric_definition`
4. `data_foundation_and_contracts`
5. `dataset_feature_target_integrity`
6. `training_evaluation_and_registry`
7. `inference_outputs_and_decisioning`
8. `monitoring_operational_resilience`
9. `final_integration_and_release_gates`

## Strict Final Gate Order

The final gate order is fixed and should not be reordered:

1. `integration_consistency`
2. `production_readiness_auditor`
3. `end_to_end_ml_auditor`
4. `acceptance_criteria_verifier`

Each gate has a narrower closure role than the next:

- `integration_consistency` verifies contract compatibility and cross-component alignment.
- `production_readiness_auditor` verifies production execution safety, observability, and handover readiness.
- `end_to_end_ml_auditor` issues the final full-system readiness judgment.
- `acceptance_criteria_verifier` checks closure against the original requested scope and evidence.

## Framework Artifacts

- [lifecycle_groups.md](/Users/anastasiia.m/Documents/My%20projects/Agents/agent_framework/lifecycle_groups.md)
- [orchestration_graph.md](/Users/anastasiia.m/Documents/My%20projects/Agents/agent_framework/orchestration_graph.md)
- [shared_prompt_template.md](/Users/anastasiia.m/Documents/My%20projects/Agents/agent_framework/shared_prompt_template.md)
- [shared_contract_envelope.yaml](/Users/anastasiia.m/Documents/My%20projects/Agents/agent_framework/shared_contract_envelope.yaml)
- [agent_registry.yaml](/Users/anastasiia.m/Documents/My%20projects/Agents/agent_framework/agent_registry.yaml)
- [agent_dependencies.yaml](/Users/anastasiia.m/Documents/My%20projects/Agents/agent_framework/agent_dependencies.yaml)
- [agent_lifecycle_map.yaml](/Users/anastasiia.m/Documents/My%20projects/Agents/agent_framework/agent_lifecycle_map.yaml)

## Canonical Naming

- `datasource_conractor` -> `data_source_contract_auditor`
- `leackage_audit` -> `temporal_leakage_auditor`
- `model_evaluation_treshold_auditor` -> `model_evaluation_threshold_auditor`
- `prod_readiness_auditor` -> `production_readiness_auditor`
- `end-to-end-ml_auditor` -> `end_to_end_ml_auditor`
- `multi-agent-orchestrator` -> `multi_agent_orchestrator`

## Structural Changes Applied

- `pipeline_idempotency_auditor` was rewritten to cover actual rerun, retry, duplicate-write, and backfill safety.
- Five missing agents were added:
  - `contract_compiler_validator`
  - `label_target_definition_agent`
  - `promotion_release_gate_agent`
  - `preflight_execution_guard`
  - `incident_rollback_readiness_agent`

## Design Principles

- Preserve specialized depth where the existing prompt is already production-useful.
- Make parent vs specialist relationships explicit instead of flattening all prompts into peer defaults.
- Treat contracts, validation, and handoff artifacts as first-class orchestration dependencies.
- Preserve edge-case handling around temporal safety, grain, monitoring maturity, rerun safety, and release gating.
