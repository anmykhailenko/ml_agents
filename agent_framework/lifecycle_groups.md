# Lifecycle Groups

All prompt files now live under `agents/<lifecycle_phase>/<primary|specialist>/`, with `agent_framework/` reserved for governance artifacts and `reports/` reserved for review outputs. Agents with registry `role_type: child` are stored under `primary/`.

## 1. Intake And Scope

Primary agents:
- `task_triage_router`
- `multi_agent_orchestrator`

Child and specialist agents:
- `overengineering_control`

Purpose:
- classify the incoming problem
- define the minimal correct scope
- decide prototype vs production rigor
- assign owners and sequencing

## 2. Repository Runtime Foundation

Primary agents:
- `ml_repository_architect`
- `environment_and_runtime_auditor`
- `dependency_package_auditor`

Specialist agents:
- `security_auditor`
- `git_hygiene_auditor`
- `documentation_runbook_auditor`
- `code_patch_reviewer`

Purpose:
- establish repository boundaries
- verify environment and runtime assumptions
- validate dependency hygiene
- protect secrets and operational setup

## 3. Exploratory Analysis And Metric Definition

Primary agents:
- `eda_auditor`
- `analytical_metrics_auditor`
- `business_insight_quality_auditor`

Specialist agents:
- `wau_mau_dau_consistency_auditor`
- `cohort_logic_auditor`
- `segment_naming_stability_auditor`

Purpose:
- validate analytical framing before pipeline hardening
- make KPI definitions explicit
- protect cohort, active-user, and segmentation correctness

## 4. Data Foundation And Contracts

Primary agents:
- `warehouse_metadata_extractor`
- `data_source_contract_auditor`
- `schema_mapping`
- `sql_generator`

Child and specialist agents:
- `join_integrity`
- `sql_partition_pruning`
- `contract_compiler_validator`

Purpose:
- discover source metadata
- formalize dataset contracts
- map schema lineage and compatibility
- produce production-safe SQL and enforce contract compilation

## 5. Dataset Feature Target Integrity

Primary agents:
- `label_target_definition_agent`
- `label_quality_and_ground_truth_auditor`
- `feature_engineering_auditor`

Specialist agents:
- `temporal_leakage_auditor`
- `feature_availability_at_time_auditor`
- `feature_engineering_relevance_auditor`
- `business_logic_auditor`

Purpose:
- define the target policy
- protect target maturity and supervision correctness
- validate feature reproducibility, availability, and relevance

## 6. Training Evaluation And Registry

Primary agents:
- `training_pipeline_auditor`
- `model_evaluation_threshold_auditor`
- `mlflow_registry_auditor`

Specialist agents:
- `model_comparison_auditor`
- `memory_and_performance_auditor`

Purpose:
- validate split logic and training reproducibility
- verify evaluation and threshold governance
- enforce registry traceability and promotion prerequisites

## 7. Inference Outputs And Decisioning

Primary agents:
- `inference_pipeline_auditor`
- `offline_to_online_consistency_auditor`
- `output_artifacts_auditor`

Child and specialist agents:
- `promotion_release_gate_agent`

Purpose:
- protect inference determinism and feature parity
- ensure outputs are metadata-complete
- gate release of inference-capable artifacts into production decisioning

## 8. Monitoring Operational Resilience

Primary agents:
- `model_monitoring_auditor`
- `data_drift_auditor`
- `testing_and_validation_auditor`

Specialist agents:
- `pipeline_idempotency_auditor`
- `silent_fallback_auditor`
- `config_governance_auditor`
- `deployment_and_orchestration_auditor`
- `preflight_execution_guard`
- `incident_rollback_readiness_agent`
- `unit_test_coverage_auditor`

Purpose:
- validate runtime checks, monitoring, and drift detection
- harden retries, reruns, execution guards, and rollback readiness
- ensure orchestration and configuration are safe under failure

## 9. Final Integration And Release Gates

Primary agents:
- `integration_consistency`
- `production_readiness_auditor`
- `end_to_end_ml_auditor`
- `acceptance_criteria_verifier`

Purpose:
- consolidate prior audit outputs
- verify contract alignment and execution readiness
- make the final go-live and task-closure decision in strict order
