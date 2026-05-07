# Agent Framework Meta-Implementation

## What Was Created

- `agent_framework/README.md`
- `agent_framework/lifecycle_groups.md`
- `agent_framework/orchestration_graph.md`
- `agent_framework/shared_prompt_template.md`
- `agent_framework/shared_contract_envelope.yaml`
- `agent_framework/agent_registry.yaml`
- five new agent prompts:
  - `contract_compiler_validator`
  - `label_target_definition_agent`
  - `promotion_release_gate_agent`
  - `preflight_execution_guard`
  - `incident_rollback_readiness_agent`

## What Was Renamed

- `datasource_conractor` -> `data_source_contract_auditor`
- `leackage_audit` -> `temporal_leakage_auditor`
- `model_evaluation_treshold_auditor` -> `model_evaluation_threshold_auditor`

## What Was Rewritten

- `pipeline_idempotency_auditor`

The prompt now audits:
- duplicate-write risk
- retry safety
- backfill safety
- append vs overwrite behavior
- rerun semantics
- artifact and promotion idempotency

It no longer duplicates offline-online consistency.

## Final Gate Order Implemented

The framework now defines a strict final gate chain:

1. `integration_consistency`
2. `production_readiness_auditor`
3. `end_to_end_ml_auditor`
4. `acceptance_criteria_verifier`

This order is documented in:
- `agent_framework/README.md`
- `agent_framework/orchestration_graph.md`
- `agent_framework/agent_registry.yaml`

## Shared Standards Implemented

### Shared prompt structure

Defined in `agent_framework/shared_prompt_template.md` with standard sections for:
- role
- only task
- non-goals
- focus
- required inputs
- mission
- deliverables
- upstream prerequisites
- downstream handoff
- validation rules
- stop conditions
- final validation
- final response shape

### Shared contract envelope

Defined in `agent_framework/shared_contract_envelope.yaml` with canonical fields for:
- ownership
- lifecycle phase
- upstream dependencies
- downstream consumers
- grain and partition semantics
- validation rules
- assumptions
- open questions
- domain payload

## Strong Prompts Left Unchanged

The following prompts were intentionally left unchanged because the meta-review classified them as strong:

- `task_triage_router`
- `warehouse_metadata_extractor`
- `schema_mapping`
- `sql_generator`
- `join_integrity`
- `temporal_leakage_auditor`
- `training_pipeline_auditor`
- `inference_pipeline_auditor`
- `mlflow_registry_auditor`
- `model_monitoring_auditor`
- `business_logic_auditor`

## Registry Design Choices

- Primary agents own the default lifecycle responsibility for a phase or major stage.
- Specialist agents are narrower controls that should usually be routed by a primary agent or orchestrator.
- Child agents are framework-supporting agents added to fill missing lifecycle mechanics such as contract compilation, preflight gating, release gating, and rollback readiness.

## Open Questions

1. Whether prompt files should remain extensionless or later move to an explicit `.md` or `.prompt` convention.
2. Whether older prompts should be incrementally migrated to the shared template as they are next edited, rather than mass-rewritten now.
3. Whether contract-producing prompts should later be updated to write into a unified `contracts/` directory instead of mixed legacy paths under `configs/` and `data/`.
