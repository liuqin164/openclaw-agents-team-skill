---
name: devteam
description: Artifact-driven virtual dev team workflow with PM-led governance and staged delivery.
---

# OpenClaw Dev Team (devteam)

Use this skill when the user wants an end-to-end product development workflow that is driven by artifacts and stage gates (PRD → Design → Implementation → QA). The system controller should enforce the registry workflow and only advance stages when the required artifacts are completed.

## Governance Mode (Project Control)

At requirement collection, the PM must output a GovernanceState artifact and select one mode:

- **human-in-loop**: after each stage, report progress and wait for the user to explicitly confirm “continue”.
- **autopilot**: after each stage, report progress and proceed automatically until QA completes.

## Execution Semantics

When interpreting command results, use the ExecResult artifact and its `interpretation` field. For commands like `ps`/`grep`/`rg`, exit code `1` can mean “no match” rather than failure.

## Key Files

- `registry.yaml`: workflow stages, triggers, and transitions
- `artifacts.yaml`: artifact schema and status flow
- `system_prompt.md`: system controller rules
