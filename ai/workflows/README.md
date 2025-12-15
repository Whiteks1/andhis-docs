# Andhis – Workflows Conversacionales

Este directorio contiene los **workflows conversacionales en formato YAML**.

Los workflows describen:
- estados
- transiciones
- acciones
- comportamiento esperado del sistema

Son la base para el motor de workflows del backend.

---

## Convenciones

- Cada archivo corresponde a un `workflow_id`.
- El nombre del archivo debe coincidir con el `workflow_id`.
- Ejemplo:
  - `onboarding_guide_ui.yaml` → `workflow_id: onboarding_guide_ui`

---

## Workflows activos (MVP)

### `onboarding_guide_ui.yaml`
- Onboarding guiado con avatar neutro.
- Interacción por botones (no chat libre).
- Permite:
  - explicar la app
  - elegir uso principal
  - elegir estilo de avatar

👉 Usado en producción (MVP).

---

## Workflows base / legacy

### `onboarding_basic.yaml`
- Workflow genérico de onboarding.
- Usado como referencia técnica o legacy.
- No representa la UX final del producto.

👉 No se usa directamente en el MVP.

---

## Workflows planned (no implementados aún)

Estos workflows están referenciados en `product/agents.yaml`,
pero aún no existen como YAML ejecutables:

- `chat_companion_v1`
- `chat_info_v1`

👉 Se implementarán en la siguiente fase (chat con IA).

---

## Relación con otros documentos

- Diseño funcional del onboarding:
  - `docs/ai/product/onboarding_flow.md`
- Contrato frontend ↔ backend:
  - `docs/ai/product/onboarding_contract.md`
- Tests:
  - `docs/ai/tests/`

---

## Estado

- Directorio preparado para crecimiento.
- Nuevos workflows deben añadirse aquí siguiendo la convención.

Responsable Diseño de workflows:
- Whiteks L.P.R
