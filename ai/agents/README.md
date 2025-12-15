# Andhis – AI Agents

This directory contains the complete definition and documentation
of the AI agents (avatars) used in the Andhis system.

It clearly separates:
- **technical configuration** consumed by the system,
- **product / UX documentation**,
- and **functional mappings** used during onboarding.

---

## Single Source of Truth

### `agents_registry.yaml`
**Status:** PREPARED (draft, not consumed by code yet)

This file is the **single source of truth (SSOT)** for AI agent definitions.

- Defines which agents exist.
- Specifies their type (`system` / `selectable`).
- Declares default workflows and technical settings.
- Intended to be consumed by backend and frontend when implemented.

> ⚠️ Currently, this file is **not yet consumed by backend code**.

No other YAML file defines implementable agents.

---

## Product / UX Documentation

### `agents_mvp.md`

Human-readable product and UX documentation.

- Describes tone, promise, and limits of each avatar.
- Used as reference for design, tests, and prompt engineering.
- **Not consumed by the system.**

---

## Onboarding Mapping

### `agents_mapping.yaml`

Functional mapping used during onboarding.

- Maps the user-selected `style_code` (1–5)
  to the actual agent (`id` / `slug`).
- Used by backend logic during onboarding.

---

## Relation to Other Directories

- Global AI policies: `ai/base/policies.md`
- Conversational workflows: `ai/workflows/`
- Workflow tests: `ai/tests/`

---

## Editing Rules (Important)

While `agents_registry.yaml` is in *draft* status:

- **Technical agent changes** → `agents_registry.yaml`
- **Product / UX changes** → `agents_mvp.md`
- **Onboarding selection logic** → `agents_mapping.yaml`
- **Global safety and limits** → `policies.md`

---

## Final Note

This design is prepared to scale:
- new agents,
- multiple styles,
- dynamic backend consumption,
- future chat-based workflows.

Any structural change must be discussed before implementation.
