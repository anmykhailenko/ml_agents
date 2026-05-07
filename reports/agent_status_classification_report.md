# Agent Status Classification Report

## Summary

- active: 44
- experimental: 9
- deprecated: 0
- archived: 0

## Classification Rules Applied

- Primary core lifecycle agents were kept as `active`.
- Broad, production-relevant specialist auditors were kept as `active`.
- Narrower or optional specialist agents were marked `experimental` when they are useful but not default for most framework runs.
- No agents were marked `deprecated` because no remaining prompt is currently superseded by a better replacement.
- No agents were marked `archived` per the requested policy.

## Active Agents

- `contract_compiler_validator`: production-ready and reusable as a default framework capability
- `data_source_contract_auditor`: production-ready and reusable as a default framework capability
- `join_integrity`: production-ready and reusable as a default framework capability
- `schema_mapping`: production-ready and reusable as a default framework capability
- `sql_generator`: production-ready and reusable as a default framework capability
- `sql_partition_pruning`: production-ready and reusable as a default framework capability
- `warehouse_metadata_extractor`: production-ready and reusable as a default framework capability
- `business_logic_auditor`: production-ready and reusable as a default framework capability
- `feature_availability_at_time_auditor`: production-ready and reusable as a default framework capability
- `feature_engineering_auditor`: production-ready and reusable as a default framework capability
- `label_quality_and_ground_truth_auditor`: production-ready and reusable as a default framework capability
- `label_target_definition_agent`: production-ready and reusable as a default framework capability
- `temporal_leakage_auditor`: production-ready and reusable as a default framework capability
- `analytical_metrics_auditor`: production-ready and reusable as a default framework capability
- `business_insight_quality_auditor`: production-ready and reusable as a default framework capability
- `eda_auditor`: production-ready and reusable as a default framework capability
- `acceptance_criteria_verifier`: production-ready and reusable as a default framework capability
- `end_to_end_ml_auditor`: production-ready and reusable as a default framework capability
- `integration_consistency`: production-ready and reusable as a default framework capability
- `production_readiness_auditor`: production-ready and reusable as a default framework capability
- `inference_pipeline_auditor`: production-ready and reusable as a default framework capability
- `offline_to_online_consistency_auditor`: production-ready and reusable as a default framework capability
- `output_artifacts_auditor`: production-ready and reusable as a default framework capability
- `promotion_release_gate_agent`: production-ready and reusable as a default framework capability
- `multi_agent_orchestrator`: production-ready and reusable as a default framework capability
- `task_triage_router`: production-ready and reusable as a default framework capability
- `config_governance_auditor`: production-ready and reusable as a default framework capability
- `data_drift_auditor`: production-ready and reusable as a default framework capability
- `deployment_and_orchestration_auditor`: production-ready and reusable as a default framework capability
- `incident_rollback_readiness_agent`: production-ready and reusable as a default framework capability
- `model_monitoring_auditor`: production-ready and reusable as a default framework capability
- `pipeline_idempotency_auditor`: production-ready and reusable as a default framework capability
- `preflight_execution_guard`: production-ready and reusable as a default framework capability
- `silent_fallback_auditor`: production-ready and reusable as a default framework capability
- `testing_and_validation_auditor`: production-ready and reusable as a default framework capability
- `dependency_package_auditor`: production-ready and reusable as a default framework capability
- `documentation_runbook_auditor`: production-ready and reusable as a default framework capability
- `environment_and_runtime_auditor`: production-ready and reusable as a default framework capability
- `git_hygiene_auditor`: production-ready and reusable as a default framework capability
- `ml_repository_architect`: production-ready and reusable as a default framework capability
- `security_auditor`: production-ready and reusable as a default framework capability
- `mlflow_registry_auditor`: production-ready and reusable as a default framework capability
- `model_evaluation_threshold_auditor`: production-ready and reusable as a default framework capability
- `training_pipeline_auditor`: production-ready and reusable as a default framework capability

## Experimental Agents

- `feature_engineering_relevance_auditor`: useful but narrower, more optional, or not a default entrypoint for most projects
- `cohort_logic_auditor`: useful but narrower, more optional, or not a default entrypoint for most projects
- `segment_naming_stability_auditor`: useful but narrower, more optional, or not a default entrypoint for most projects
- `wau_mau_dau_consistency_auditor`: useful but narrower, more optional, or not a default entrypoint for most projects
- `overengineering_control`: useful but narrower, more optional, or not a default entrypoint for most projects
- `unit_test_coverage_auditor`: useful but narrower, more optional, or not a default entrypoint for most projects
- `code_patch_reviewer`: useful but narrower, more optional, or not a default entrypoint for most projects
- `memory_and_performance_auditor`: useful but narrower, more optional, or not a default entrypoint for most projects
- `model_comparison_auditor`: useful but narrower, more optional, or not a default entrypoint for most projects

## Deprecated Agents

- None.

## Archived Agents

- None.

## Notes

- `experimental` does not mean low quality. It means narrower default applicability or optional use in a standard lifecycle run.
- Child-role agents remained in `primary/` or `specialist/` folders based on current usage pattern; relationship type was not used as a filesystem rule.
- Registry, prompt front matter, and lifecycle map were updated consistently from the same status source of truth.
