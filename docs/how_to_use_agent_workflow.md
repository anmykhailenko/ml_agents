# How To Use The ML Agent Workflow

This guide explains how to use the ML Agent Framework in practice without treating every project as a full production audit.

## What This Framework Is

The framework is a library of ML review and delivery agents organized by lifecycle phase.

It is designed to help you:
- choose the right audit or planning agent for the current project stage
- avoid skipping critical ML checks such as target definition, leakage review, and data contracts
- scale from lightweight prototype review to full production release gating

The lifecycle is intentionally chronological:
1. `01_intake_and_scope`
2. `02_repository_runtime_foundation`
3. `03_exploratory_analysis_and_metric_definition`
4. `04_data_foundation_and_contracts`
5. `05_dataset_feature_target_integrity`
6. `06_training_evaluation_and_registry`
7. `07_inference_outputs_and_decisioning`
8. `08_monitoring_operational_resilience`
9. `09_final_integration_and_release_gates`

Files are not numbered individually. Recommended ordering lives in `agent_framework/agent_registry.yaml` through `phase_order` and `agent_order`.

## When To Use It

Use this framework when:
- you are starting a new ML project and want a default review sequence
- you inherited an existing or messy ML repository
- you need targeted audits before training, inference, or release
- you want structured written outputs under `reports/agent_reviews/`
- you are preparing an MVP, prototype, production release, or take-home assignment

## When Not To Use All Agents

Do not run every agent by default.

Avoid using all agents when:
- the task is a small take-home or time-boxed interview assignment
- you only need one narrow review, such as leakage, evaluation thresholds, or offline/online consistency
- the project is an MVP and does not yet have production infrastructure
- the repo is too immature for late-stage monitoring or release gates

Default rule:
- start with the smallest useful set
- add specialists only when a risk, dependency, or project stage justifies them

## Recommended Workflow For A New ML Project

For a new project, use the lifecycle in order.

1. Start with `task_triage_router`.
   Use it to classify the problem, scope the work, and identify hidden requirements.
2. Run `multi_agent_orchestrator`.
   Use it to map the project into the right lifecycle phases and avoid unnecessary work.
3. Stabilize the repo foundation.
   Typical agents: `ml_repository_architect`, `environment_and_runtime_auditor`, `dependency_package_auditor`.
4. Define analytical framing.
   Typical agents: `eda_auditor`, `analytical_metrics_auditor`.
5. Lock down data contracts before heavy feature work.
   Typical agents: `warehouse_metadata_extractor`, `data_source_contract_auditor`, `schema_mapping`, `sql_generator`.
6. Validate target and feature integrity before training.
   Typical agents: `label_target_definition_agent`, `temporal_leakage_auditor`, `feature_engineering_auditor`.
7. Audit training and evaluation.
   Typical agents: `training_pipeline_auditor`, `model_evaluation_threshold_auditor`, `mlflow_registry_auditor`.
8. Audit inference and operational paths if deployment exists.
   Typical agents: `inference_pipeline_auditor`, `output_artifacts_auditor`, `model_monitoring_auditor`.
9. Use final gates only when the project is ready for closure or release.

## Recommended Workflow For An Existing Messy Project

For a messy inherited project, do not begin with training.

Recommended sequence:
1. `task_triage_router`
2. `multi_agent_orchestrator`
3. `ml_repository_architect`
4. `environment_and_runtime_auditor`
5. `data_source_contract_auditor`
6. `label_target_definition_agent`
7. `temporal_leakage_auditor`
8. `training_pipeline_auditor`

Add these based on what you find:
- `git_hygiene_auditor` if the repo is cluttered or unsafe
- `documentation_runbook_auditor` if nobody can reproduce the workflow
- `join_integrity` if source joins are unclear
- `business_logic_auditor` if score meaning or downstream use is ambiguous
- `offline_to_online_consistency_auditor` if a deployed scoring path already exists

The goal for a messy project is to restore trust in structure, contracts, target logic, and training validity before optimizing anything else.

## Minimal Workflow For MVP Or Prototype

For an MVP, use a narrow path.

Recommended default:
1. `task_triage_router`
2. `overengineering_control`
3. `data_source_contract_auditor`
4. `label_target_definition_agent`
5. `temporal_leakage_auditor`
6. `training_pipeline_auditor`
7. `model_evaluation_threshold_auditor`

Optional adds:
- `feature_engineering_auditor` if feature complexity is growing
- `output_artifacts_auditor` if you are handing predictions to another team

Usually skip:
- most monitoring agents
- most release-gate agents
- deep specialist audits unless a concrete risk appears

## Full Workflow For Production ML Release

For a production release, use the full lifecycle selectively but completely enough to cover delivery risk.

Recommended path:
1. Intake and scope: `task_triage_router`, `multi_agent_orchestrator`
2. Foundation: `ml_repository_architect`, `environment_and_runtime_auditor`, `dependency_package_auditor`, `security_auditor`, `documentation_runbook_auditor`
3. Analytical framing: `eda_auditor`, `analytical_metrics_auditor`
4. Data contracts: `warehouse_metadata_extractor`, `data_source_contract_auditor`, `schema_mapping`, `sql_generator`, `contract_compiler_validator`
5. Dataset integrity: `label_target_definition_agent`, `label_quality_and_ground_truth_auditor`, `temporal_leakage_auditor`, `feature_availability_at_time_auditor`, `feature_engineering_auditor`
6. Training and registry: `training_pipeline_auditor`, `model_evaluation_threshold_auditor`, `mlflow_registry_auditor`
7. Inference and outputs: `inference_pipeline_auditor`, `offline_to_online_consistency_auditor`, `output_artifacts_auditor`, `promotion_release_gate_agent`
8. Monitoring and resilience: `model_monitoring_auditor`, `testing_and_validation_auditor`, `preflight_execution_guard`, `incident_rollback_readiness_agent`
9. Final gates in strict order: `integration_consistency`, `production_readiness_auditor`, `end_to_end_ml_auditor`, `acceptance_criteria_verifier`

## Workflow For Take-Home / Interview Assignment

For a take-home, optimize for correctness and scope control, not full production governance.

Recommended path:
1. `task_triage_router`
2. `overengineering_control`
3. `label_target_definition_agent`
4. `temporal_leakage_auditor`
5. `training_pipeline_auditor`
6. `model_evaluation_threshold_auditor`
7. `acceptance_criteria_verifier`

Useful optional agents:
- `business_insight_quality_auditor` if the assignment expects interpretation
- `documentation_runbook_auditor` if submission clarity matters

Usually skip:
- registry and deployment agents
- monitoring agents
- most specialists unless the assignment explicitly requires them

## How To Choose Agents By Lifecycle Phase

Use phases as the default filter.

- `01_intake_and_scope`
  Use for routing, scoping, sequencing, and deciding how much rigor is warranted.
- `02_repository_runtime_foundation`
  Use when repo structure, runtime setup, packages, documentation, or security may block reliable work.
- `03_exploratory_analysis_and_metric_definition`
  Use when KPI definitions, cohorts, EDA, or business insight quality need review.
- `04_data_foundation_and_contracts`
  Use before dataset building, SQL generation, or schema-heavy work.
- `05_dataset_feature_target_integrity`
  Use before training whenever target definition, label quality, feature timing, or leakage risk matters.
- `06_training_evaluation_and_registry`
  Use for train/validation/test policy, evaluation rigor, thresholding, and model registration.
- `07_inference_outputs_and_decisioning`
  Use when the model produces deployable outputs or downstream decisions.
- `08_monitoring_operational_resilience`
  Use when the system has operational execution, monitoring, retry, rollback, or orchestration concerns.
- `09_final_integration_and_release_gates`
  Use only near project closure, release, or formal acceptance.

## How To Run One Agent

Use a direct prompt naming the agent and the review target.

Example:

```text
Use agent: temporal_leakage_auditor

Review this training dataset and feature pipeline for temporal leakage.
Focus on:
- point-in-time correctness
- label window alignment
- feature availability at scoring time

Project context:
- binary churn model
- daily prediction cadence
- training data built from warehouse SQL

Write the output to reports/agent_reviews/temporal_leakage_auditor_round1.md
```

Good single-agent prompts include:
- the exact agent name
- the artifact to inspect
- the business or model context
- the desired output file

## How To Store Outputs Under `reports/agent_reviews/`

Store each review as a separate Markdown file under `reports/agent_reviews/`.

Recommended naming:
- `reports/agent_reviews/<agent_name>_round1.md`
- `reports/agent_reviews/<agent_name>_round2.md`
- `reports/agent_reviews/<project_stage>_<agent_name>.md`

Suggested structure inside each review:
- scope reviewed
- findings
- required fixes
- optional improvements
- open questions
- next recommended agent

If the directory does not exist yet, create it before writing outputs.

## How To Re-Run After Fixes

After applying fixes:
1. re-run the same agent that raised the issue
2. confirm the original finding is closed
3. run the immediate downstream agent if the fix changes dependent artifacts

Examples:
- after fixing target definition, re-run `label_target_definition_agent` and then `temporal_leakage_auditor`
- after fixing dataset SQL, re-run `data_source_contract_auditor`, `schema_mapping`, or `join_integrity` as needed
- after fixing training logic, re-run `training_pipeline_auditor` before any release gating

Do not jump to final gates immediately after a major fix in an upstream phase.

## How To Use Final Gate Agents

Final gate agents are not general-purpose auditors. They are closure gates.

Run them only after upstream work is materially complete.

Use them in this strict order:
1. `integration_consistency`
2. `production_readiness_auditor`
3. `end_to_end_ml_auditor`
4. `acceptance_criteria_verifier`

Interpretation:
- `integration_consistency` checks cross-component alignment
- `production_readiness_auditor` checks operational safety and readiness
- `end_to_end_ml_auditor` checks whole-system readiness
- `acceptance_criteria_verifier` checks whether the delivered work satisfies the original ask

If one gate fails, fix the issue and re-run that gate before moving forward.

## Example Codex Prompt Template

Use this template:

```text
Use agent: <agent_name>

Task:
<what you want reviewed or produced>

Context:
- project type: <new project | messy project | MVP | production | take-home>
- model type: <classification | regression | ranking | uplift | forecasting>
- current lifecycle phase: <phase name>
- relevant files or folders: <paths>

Focus on:
- <focus area 1>
- <focus area 2>
- <focus area 3>

Constraints:
- do not rewrite unrelated code
- keep recommendations proportional to project maturity

Output:
Write the review to reports/agent_reviews/<output_name>.md
```

## Common Mistakes

- running all agents at once
  This produces noisy outputs and ignores lifecycle dependencies.
- mixing roles
  Do not use specialist agents as your default top-level path when a primary agent should route first.
- skipping data contracts
  Training on weakly defined datasets makes later evaluation and inference reviews unreliable.
- training before target or leakage checks
  This is one of the fastest ways to create false confidence in model quality.
- treating specialist agents as default
  Specialists should be called because a risk, domain need, or dependency justifies them.

## Recommended Build → Audit → Fix → Re-Audit → Gate Loop

Use this loop for almost every serious ML project:

1. Build the current stage artifact.
   Examples: contract, dataset, features, training pipeline, inference pipeline.
2. Audit that artifact with the right agent for the current lifecycle phase.
3. Fix the issues found.
4. Re-audit the same stage to confirm closure.
5. Move to the next lifecycle phase.
6. Use final gate agents only when the upstream chain is stable.

In short:
- do not build everything first and audit at the end
- audit at each stage boundary
- gate only after re-audit passes
