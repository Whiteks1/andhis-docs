# Andhis – AI Documentation

This repository contains the **authoritative documentation**
for the conversational AI system of Andhis.

The `ai/` directory is the **root of truth** for:
- AI behavior
- conversational workflows
- onboarding logic
- and API contracts related to AI interactions

This repository is intentionally **decoupled from application code**.

---

## Source of Truth (TL;DR)
ocumentación de diseño y contratos de la capa de IA.
A continuación se indica **qué archivo es la fuente de verdad** para cada parte del sistema.

### Agentes
- **Implementación (YAML – fuente de verdad técnica):**  
  `ai/agents/agents_registry.yaml`
- **Producto / UX (documentación humana):**  
  `ai/product/agents_mvp.md`

### Onboarding
- **Contrato API (backend ↔ frontend):**  
  `ai/api/CONTRACT_onboarding_action.md`
- **Workflow ejecutable:**  
  `ai/workflows/onboarding_basic.yaml`
- **Casos de prueba / criterios de aceptación:**  
  `ai/tests/onboarding_basic.md`

### Notas importantes
- El backend **solo debe consumir** los YAML marcados como fuente de verdad técnica.
- Los documentos en `product/` describen **intención, UX y decisiones de negocio**, no lógica ejecutable.
- Cualquier cambio en workflows o contratos debe reflejarse también en sus tests asociados.


## Why `ai/` is the root directory

This repository focuses exclusively on the AI domain.
For this reason, the `ai/` folder is the semantic root, not a subfolder of `docs/`.

The application codebase may reference or mirror this structure,
but this repository remains the **source of truth** for design and contracts.

---

## Scope

- AI agents (product definition and technical registry)
- Conversational workflows (YAML state machines)
- Frontend ↔ Backend API contracts
- Functional workflow tests
- Global AI policies and limits

---

## Non-Goals

- Backend implementation
- Frontend implementation
- Prompt runtime configuration

---

## Directory structure

ai/
├─ base/
├─ product/
├─ workflows/
├─ api/
└─ tests/


---

## Status

Active – under iterative design.

# AI Domain

This directory contains the complete definition of Andhis AI behavior.

Everything here is considered **design- and contract-level truth**.
Implementation must conform to these documents.
