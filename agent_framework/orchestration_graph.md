# Orchestration Graph

```text
task_triage_router
  -> overengineering_control
  -> multi_agent_orchestrator

multi_agent_orchestrator
  -> ml_repository_architect
  -> environment_and_runtime_auditor
  -> dependency_package_auditor
  -> security_auditor
  -> git_hygiene_auditor

eda_auditor
  -> analytical_metrics_auditor
  -> business_insight_quality_auditor
  -> cohort_logic_auditor
  -> wau_mau_dau_consistency_auditor
  -> segment_naming_stability_auditor

warehouse_metadata_extractor
  -> data_source_contract_auditor
  -> schema_mapping
  -> sql_generator
  -> join_integrity
  -> sql_partition_pruning

data_source_contract_auditor
  -> contract_compiler_validator
  -> label_target_definition_agent
  -> feature_engineering_auditor

label_target_definition_agent
  -> label_quality_and_ground_truth_auditor
  -> temporal_leakage_auditor
  -> model_evaluation_threshold_auditor
  -> model_monitoring_auditor

feature_engineering_auditor
  -> feature_availability_at_time_auditor
  -> feature_engineering_relevance_auditor
  -> training_pipeline_auditor
  -> inference_pipeline_auditor

training_pipeline_auditor
  -> model_evaluation_threshold_auditor
  -> model_comparison_auditor
  -> mlflow_registry_auditor
  -> memory_and_performance_auditor

mlflow_registry_auditor
  -> promotion_release_gate_agent
  -> inference_pipeline_auditor

inference_pipeline_auditor
  -> offline_to_online_consistency_auditor
  -> output_artifacts_auditor
  -> business_logic_auditor
  -> model_monitoring_auditor

testing_and_validation_auditor
  -> preflight_execution_guard
  -> pipeline_idempotency_auditor
  -> incident_rollback_readiness_agent
  -> unit_test_coverage_auditor

deployment_and_orchestration_auditor
  -> config_governance_auditor
  -> documentation_runbook_auditor
  -> preflight_execution_guard
  -> pipeline_idempotency_auditor
  -> incident_rollback_readiness_agent

Strict final gate order:
integration_consistency
  -> production_readiness_auditor
  -> end_to_end_ml_auditor
  -> acceptance_criteria_verifier
```

## Ordering Notes

- `contract_compiler_validator` should run after the first wave of contract-producing agents and again before final integration if contracts were updated.
- `label_target_definition_agent` must run before label auditing, evaluation compatibility review, and monitoring target checks.
- `promotion_release_gate_agent` must run after evaluation and registry evidence exist, and before final production release.
- `preflight_execution_guard` belongs immediately before any concrete execution step such as training, inference, monitoring, or backfill.
- `incident_rollback_readiness_agent` should run before final production approval, not after release.
