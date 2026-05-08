# Agent Framework Validation Report

## Summary

- registry agents validated: 53
- missing prompt paths: 0
- supported status lifecycle: active, experimental, deprecated, archived
- lifecycle folders validated: 9 numbered phases in chronological order

## Path Validation

- PASS: all registry `prompt_path` values resolve to existing files.
- PASS: no legacy unnumbered lifecycle paths remain in framework metadata, reports, or prompt front matter.

## Role Bucket Rules

- `primary` prompts include registry `role_type` values `primary` and `child`.
- `specialist` prompts include registry `role_type` value `specialist`.

## Metadata Header Validation

- PASS: every prompt was rewritten with a YAML front matter header containing agent_name, version, status, role_type, lifecycle_phase, tags, upstream_dependencies, and downstream_dependencies.

## Generated Governance Artifacts

- `agent_framework/agent_dependencies.yaml`
- `agent_framework/agent_lifecycle_map.yaml`
- `agent_framework/agent_registry.yaml` updated with explicit `prompt_path`, `role_type`, `phase_order`, and `agent_order` metadata.

## Open Notes

- No core prompt bodies were rewritten during lifecycle renaming; changes were limited to metadata front matter and path updates.
