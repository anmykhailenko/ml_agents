# Execution Modes

This document defines execution modes for the ML Agent Framework so teams can choose a rigor level first and then expand only when justified.

The goal is to use the framework as a modular rigor-escalation operating system rather than a flat 56-agent governance library.

## 1. Minimal Core Flow

Expected rigor level:
- low to moderate

Expected project type:
- early ML spike
- narrow internal analysis-to-model workflow
- small project where correctness matters more than production depth

Required agents:
- `task_triage_router`
- `overengineering_control`
- `label_target_definition_agent`
- `temporal_leakage_auditor`
- `training_pipeline_auditor`
- `model_evaluation_threshold_auditor`

Optional agents:
- `data_source_contract_auditor`
- `feature_engineering_auditor`
- `business_insight_quality_auditor`
- `acceptance_criteria_verifier`

Recommended stopping point:
- stop after evaluation logic is credible and the training path is reproducible enough for the current scope
- do not proceed into inference, monitoring, or release-gate phases unless deployment becomes part of the task

## 2. Prototype/MVP Flow

Expected rigor level:
- moderate

Expected project type:
- MVP
- proof-of-concept intended to influence product direction
- early internal deployment candidate

Required agents:
- `task_triage_router`
- `overengineering_control`
- `multi_agent_orchestrator`
- `data_source_contract_auditor`
- `label_target_definition_agent`
- `temporal_leakage_auditor`
- `feature_engineering_auditor`
- `training_pipeline_auditor`
- `model_evaluation_threshold_auditor`

Optional agents:
- `environment_and_runtime_auditor`
- `analytical_metrics_auditor`
- `output_artifacts_auditor`
- `business_logic_auditor`
- `testing_and_validation_auditor`
- `documentation_runbook_auditor`
- `acceptance_criteria_verifier`

Recommended stopping point:
- stop once the dataset, target logic, training path, and evaluation outputs are trustworthy enough to support an MVP decision or handoff
- if predictions will be consumed by another system or team, extend to `output_artifacts_auditor`

## 3. Production ML Flow

Expected rigor level:
- high

Expected project type:
- production batch scoring
- production retraining pipeline
- decision-support or customer-impacting ML system

Required agents:
- `task_triage_router`
- `multi_agent_orchestrator`
- `ml_repository_architect`
- `environment_and_runtime_auditor`
- `dependency_package_auditor`
- `security_auditor`
- `documentation_runbook_auditor`
- `warehouse_metadata_extractor`
- `data_source_contract_auditor`
- `schema_mapping`
- `contract_compiler_validator`
- `label_target_definition_agent`
- `label_quality_and_ground_truth_auditor`
- `temporal_leakage_auditor`
- `feature_availability_at_time_auditor`
- `feature_engineering_auditor`
- `training_pipeline_auditor`
- `model_evaluation_threshold_auditor`
- `mlflow_registry_auditor`
- `inference_pipeline_auditor`
- `offline_to_online_consistency_auditor`
- `output_artifacts_auditor`
- `promotion_release_gate_agent`
- `testing_and_validation_auditor`
- `config_governance_auditor`
- `deployment_and_orchestration_auditor`
- `preflight_execution_guard`
- `model_monitoring_auditor`
- `data_drift_auditor`
- `incident_rollback_readiness_agent`
- `integration_consistency`
- `production_readiness_auditor`
- `end_to_end_ml_auditor`
- `acceptance_criteria_verifier`

Optional agents:
- `overengineering_control`
- `join_integrity`
- `sql_partition_pruning`
- `business_logic_auditor`
- `pipeline_idempotency_auditor`
- `silent_fallback_auditor`
- `unit_test_coverage_auditor`
- `model_comparison_auditor`
- `memory_and_performance_auditor`

Recommended stopping point:
- stop only after final gate completion and explicit operational readiness
- if this is an internal production hardening step rather than a release event, stopping after `production_readiness_auditor` can be acceptable before final business closure

## 4. High-Rigor Research Flow

Expected rigor level:
- high analytical rigor
- moderate production rigor unless deployment is also in scope

Expected project type:
- experimentation-heavy ML
- uplift/causal modeling
- research workflow that may influence product or policy decisions

Required agents:
- `task_triage_router`
- `multi_agent_orchestrator`
- `eda_auditor`
- `analytical_metrics_auditor`
- `statistical_validity_auditor`
- `experimental_design_and_causal_inference_auditor`
- `sampling_and_representativeness_auditor`
- `data_source_contract_auditor`
- `label_target_definition_agent`
- `temporal_leakage_auditor`
- `training_pipeline_auditor`
- `model_evaluation_threshold_auditor`
- `business_insight_quality_auditor`

Optional agents:
- `cohort_logic_auditor`
- `wau_mau_dau_consistency_auditor`
- `segment_naming_stability_auditor`
- `feature_engineering_auditor`
- `model_comparison_auditor`
- `mlflow_registry_auditor`
- `acceptance_criteria_verifier`

Recommended stopping point:
- stop after the analytical claim, experimental validity, and model evaluation story are defensible
- extend into registry, inference, monitoring, and release only if the research output is being converted into an operational system

## 5. Messy Legacy System Recovery Flow

Expected rigor level:
- moderate to high

Expected project type:
- inherited ML repo
- brittle production-adjacent system
- undocumented pipeline with low trust

Required agents:
- `task_triage_router`
- `multi_agent_orchestrator`
- `ml_repository_architect`
- `environment_and_runtime_auditor`
- `documentation_runbook_auditor`
- `data_source_contract_auditor`
- `label_target_definition_agent`
- `temporal_leakage_auditor`
- `training_pipeline_auditor`
- `integration_consistency`

Optional agents:
- `git_hygiene_auditor`
- `dependency_package_auditor`
- `join_integrity`
- `feature_engineering_auditor`
- `offline_to_online_consistency_auditor`
- `testing_and_validation_auditor`
- `config_governance_auditor`
- `deployment_and_orchestration_auditor`
- `production_readiness_auditor`
- `model_monitoring_auditor`
- `sampling_and_representativeness_auditor`
- `statistical_validity_auditor`

Recommended stopping point:
- stop once structural trust is restored in data contracts, target logic, training validity, and cross-stage consistency
- only continue into full production gating if the legacy system is actually being prepared for continued production ownership or release

## 6. Take-Home Assignment Flow

Expected rigor level:
- low, with strict proportionality

Expected project type:
- take-home assignment
- interview project
- time-boxed demonstration of ML judgment

Required agents:
- `task_triage_router`
- `overengineering_control`
- `label_target_definition_agent`
- `temporal_leakage_auditor`
- `training_pipeline_auditor`
- `model_evaluation_threshold_auditor`
- `acceptance_criteria_verifier`

Optional agents:
- `business_insight_quality_auditor`
- `documentation_runbook_auditor`
- `statistical_validity_auditor`
- `feature_engineering_auditor`

Recommended stopping point:
- stop after the submission is correct, scoped appropriately, and clearly evidenced against the ask
- do not escalate into registry, monitoring, rollback, or production release agents unless the assignment explicitly requires them

## Operating Rule

Use execution modes as the default top-level entrypoint:

1. Choose the smallest mode that matches the real project.
2. Run the required agents for that mode.
3. Add optional agents only when a real dependency, risk, or downstream use justifies more rigor.
4. Escalate to the next mode when project maturity increases, not when more framework surface area is available.
