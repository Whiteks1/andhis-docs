# HANDOFF – Agentes IA (Andhis)

Este documento describe el estado actual de la definición de agentes de IA
y cómo deben ser utilizados durante la implementación técnica.

Su objetivo es evitar ambigüedades entre diseño conversacional y backend.

---

## Estado actual

- Los agentes de IA están **definidos a nivel de producto y diseño**.
- Existe un registro técnico unificado (`agents_registry.yaml`) **preparado**, 
  pero **no consumido aún por el backend**.
- El onboarding y los workflows están diseñados, pero el chat IA completo
  está en fase *planned*.

---

## Fuente de verdad (importante)

| Área | Fuente de verdad |
|----|----|
| Catálogo técnico de agentes | `docs/ai/agents/agents_registry.yaml` (draft) |
| Documentación humana / UX | `docs/ai/agents/agents_mvp.md` |
| Políticas globales IA | `docs/ai/base/policies.md` |
| Mapeo onboarding | `docs/ai/agents/agents_mapping.yaml` |
| Workflows | `docs/ai/workflows/` |

> ⚠️ Hasta nuevo aviso, **el backend NO debe consumir**
> `agents_registry.yaml` directamente.

---

## Qué puede implementar el backend ahora

- Onboarding guiado según `onboarding_contract.md`.
- Asignación de avatar usando `agents_mapping.yaml`.
- Persistencia de `selected_agent_id`.
- Preparación del endpoint `/api/chat` sin lógica de agentes dinámica.

---

## Qué NO debe implementar todavía

- Carga dinámica de agentes desde `agents_registry.yaml`.
- Lógica condicional basada en `tone_tags` o `limits`.
- Selección automática de workflow por agente en runtime.

Estas partes están diseñadas, pero aún no están activas.

---

## Cuándo activar el registro de agentes

El `agents_registry.yaml` pasará a ser **fuente de verdad activa** cuando:

- Se implemente el motor de chat IA real.
- El backend necesite resolver:
  - qué agente responde,
  - con qué workflow,
  - y con qué configuración.
- Se acuerde explícitamente entre diseño y backend.

Ese momento requiere una revisión conjunta.

---

## Regla de cambios

Mientras este estado se mantenga:

- Cambios de **estructura** → deben revisarse con backend.
- Cambios de **copy / tono** → pueden hacerse libremente.
- Cambios de **IDs / slugs** → no se hacen sin coordinación.

---

## Contacto / responsable

- Diseño conversacional y definición de agentes: Whiteks
- Implementación backend: Dev team

---

## Nota final

Este documento no bloquea la implementación.
Sirve para que diseño y backend avancen **sin pisarse**.
