# Andhis – AI Documentation

This repository contains the **authoritative documentation**
for the conversational AI domain of Andhis.

The `ai/` directory is the **single source of truth (SSOT)** for:
- AI behavior and limits
- conversational workflows
- onboarding logic
- API contracts related to AI interactions

This repository is intentionally **decoupled from application code**.
Its purpose is to define design, contracts, and behavior — not implementation.

---

## Source of Truth (TL;DR)

Design documentation and contracts for the AI layer.
Below is a concise map of **which file is authoritative** for each part of the system.

### Agents
- **Implementation (YAML – technical source of truth):**  
  `ai/agents/agents_registry.yaml`
- **Product / UX (human documentation):**  
  `ai/product/agents_mvp.md`

### Onboarding
- **API Contract (backend ↔ frontend):**  
  `ai/api/CONTRACT_onboarding_action.md`
- **Executable workflow:**  
  `ai/workflows/onboarding_basic.yaml`
- **Tests / acceptance criteria:**  
  `ai/tests/onboarding_basic.md`

### Important notes
- Backend **must only consume** YAML files explicitly marked as technical sources of truth.
- Documents in `product/` describe **intent, UX, and business decisions**, not executable logic.
- Any change to workflows or contracts must be reflected in their corresponding tests.

---

## Why `ai/` is the root directory

This repository focuses exclusively on the AI domain.

For this reason, the `ai/` folder is the semantic root of the project,
not a subfolder of `docs/`.

The application codebase may reference or mirror this structure,
but this repository remains the **design and contract authority**
for the AI system.

---

## Scope

This repository covers:

- AI agents (product definition and technical registry)
- Conversational workflows (YAML state machines)
- Frontend ↔ Backend API contracts related to AI
- Functional workflow tests and acceptance criteria
- Global AI policies, limits, and safety rules

---

## Non-Goals

This repository does **not** include:

- Backend implementation
- Frontend implementation
- Runtime prompt configuration
- Infrastructure or deployment concerns

---

## Directory Structure

ai/
├─ agents/ # Agent registry, mappings, and agent-related documentation
├─ base/ # Global AI policies and defaults
├─ product/ # Product and UX documentation
├─ workflows/ # Executable conversational workflows (YAML)
├─ api/ # AI-related API contracts
└─ tests/ # Workflow tests and acceptance criteria



---

## AI Domain & Status

This directory contains the complete definition of Andhis AI behavior.

Everything in `ai/` is considered **design- and contract-level truth**.
All implementations must conform to these documents.

**Status:** Active – under iterative design.
