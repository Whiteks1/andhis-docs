# Andhis – Conversational Workflows

This directory contains the **conversational workflows in YAML format**.

Workflows define:
- states
- transitions
- allowed actions
- expected system behavior

They are the foundation of the backend workflow engine.

---

## Conventions

- Each file represents a single `workflow_id`.
- The filename **must match** the `workflow_id`.
- Example:
  - `onboarding_guide_ui.yaml` → `workflow_id: onboarding_guide_ui`

---

## Active Workflows (MVP)

### `onboarding_guide_ui.yaml`

- Guided onboarding using a neutral system avatar.
- Button-based interaction (not free chat).
- Allows the system to:
  - explain the app,
  - determine main user intent,
  - select avatar style.

👉 **Used in MVP onboarding.**

---

## Base / Legacy Workflows

### `onboarding_basic.yaml`

- Generic onboarding workflow.
- Kept as technical reference or legacy flow.
- Does **not** represent final product UX.

👉 Not used directly in the MVP UI.

---

## Planned Workflows (Not Implemented Yet)

The following workflows are referenced by agents
but do not yet exist as executable YAML:

- `chat_companion_v1`
- `chat_info_v1`

👉 Planned for the next phase (free chat with AI).

---

## Relation to Other Documents

- Onboarding functional design:
  - `ai/product/onboarding_flow.md`
- Frontend ↔ Backend contract:
  - `ai/product/onboarding_contract.md`
- Tests and acceptance criteria:
  - `ai/tests/`

---

## Status

- Directory ready for growth.
- New workflows must follow the established conventions.

Workflow design owner:
- Whiteks L.P.R
