# HANDOFF – Onboarding (Andhis)

Este documento define el estado actual del onboarding de Andhis y establece
cómo debe ser implementado por el backend sin ambigüedades.

Su objetivo es servir como **documento de traspaso** entre:
- diseño conversacional / producto
- implementación backend

---

## Estado actual

- El onboarding está **completamente diseñado y documentado**.
- Existe:
  - flujo funcional,
  - contrato frontend ↔ backend,
  - workflow YAML,
  - tests funcionales.
- El onboarding **sí puede implementarse ahora**.
- El sistema de chat IA completo está aún en fase *planned*.

---

## Propósito del onboarding

El onboarding tiene como objetivo:

1. Dar la bienvenida al usuario.
2. Explicar brevemente la app.
3. Detectar el uso principal del usuario.
4. Permitir elegir un estilo de avatar (1–5).
5. Asignar un agente principal.
6. Marcar el onboarding como completado.
7. Redirigir al usuario a la app.

No es chat libre.  
Es un flujo guiado por UI.

---

## Fuentes de verdad (obligatorio respetar)

| Área | Documento |
|----|----|
| Flujo funcional | `docs/ai/onboarding_flow.md` |
| Contrato FE ↔ BE | `docs/ai/onboarding_contract.md` |
| Workflow técnico | `docs/ai/workflows/onboarding_basic.yaml` |
| Tests funcionales | `docs/ai/tests/onboarding_basic.md` |
| Mapeo estilo → agente | `docs/ai/agents/agents_mapping.yaml` |
| Registro de agentes (draft) | `docs/ai/agents/agents_registry.yaml` |
| Políticas globales IA | `docs/ai/base/policies.md` |

> ⚠️ El backend **NO debe interpretar** ni inventar pasos.
> Todo el comportamiento esperado está documentado.

---

## Qué debe implementar el backend ahora

✔️ Endpoint:
- `POST /api/onboarding/action`

✔️ Lógica:
- El backend controla:
  - estado actual del onboarding,
  - transiciones,
  - validación de inputs.
- El frontend **solo renderiza** lo que el backend devuelve.

✔️ Persistencia mínima:
- `onboarding_completed: boolean`
- `selected_agent_id: string`
- `main_use: string | null`
- `preferred_style: string | null`

✔️ Asignación de agente:
- El usuario **elige estilo**, no agente.
- El backend usa `agents_mapping.yaml` para resolver:
  `style_code → agent_id`.

---

## Qué NO debe implementarse todavía

❌ Carga dinámica de agentes desde `agents_registry.yaml`  
❌ Lógica avanzada de tono (`tone_tags`)  
❌ Selección dinámica de workflow por agente  
❌ Chat IA libre

Estas partes están diseñadas, pero **no activas**.

---

## Reglas críticas del onboarding

- El onboarding:
  - **no es chat**
  - **no hace preguntas abiertas fuera de las definidas**
- En los estados finales (`summary`, `end`):
  - **NO se hacen preguntas nuevas**
  - **NO se alarga la conversación**
- El resumen debe:
  - mencionar nombre y objetivo del usuario,
  - proponer **exactamente 2 o 3 pasos** (no más).

---

## Regla de cambios

Mientras este onboarding esté activo:

- Cambios de flujo → requieren revisión conjunta.
- Cambios de copy → permitidos si no rompen el contrato.
- Cambios de IDs / estilos → **no se hacen sin coordinación**.

---

## Responsables

- Diseño conversacional / producto: Whiteks
- Implementación backend: Dev team

---

## Nota final

Este handoff permite implementar el onboarding **sin depender**
del sistema de chat IA completo.

Cualquier desviación debe discutirse antes de programar.
