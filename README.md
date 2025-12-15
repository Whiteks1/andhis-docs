# Andhis – IA Conversacional (Docs)

Este directorio agrupa toda la documentación relacionada con la capa de IA:
agentes (avatares), workflows conversacionales, contratos y pruebas.

Objetivo:
- Mantener un “source of truth” claro.
- Separar lo estable (base) de lo específico del producto (product).
- Facilitar implementación, revisión y mantenimiento.

---

## Estructura de carpetas

### `base/`
Documentación “fundacional” y transversal del sistema.

Contiene:
- `policies.md` → políticas globales de IA (seguridad, límites, temas sensibles).
- `api_contracts.md` → contratos generales de API/IA (si aplica).
- `agent_system_default.yaml` → especificación del asistente por defecto (tono, goals, safety).

Uso:
- Referencia para comportamiento global del sistema y criterios de seguridad.

---

### `product/`
Decisiones específicas del MVP (UX + comportamiento) para Andhis.

Contiene:
- `README.md` → resumen del MVP y decisiones principales.
- `agents.yaml` → catálogo de avatares del MVP (seleccionables y sistema).
- `agents_mapping.yaml` → mapeo estilo (1–5) → slug/avatar.
- `agents_mvp.md` → explicación humana de cada avatar (tono, límites, promesa).
- `onboarding_flow.md` → flujo paso a paso del onboarding.
- `onboarding_contract.md` → contrato Frontend ↔ Backend del onboarding.
- `workflows.md` → lista/estado de workflows aplicables al producto.

Uso:
- Guía para implementación del onboarding, selector de avatares y comportamiento esperado.

---

### `workflows/`
Workflows conversacionales en formato YAML (fuente para el motor de workflows).

Contiene:
- `<workflow_id>.yaml` → definición de estados, transiciones y acciones.

Convención:
- El nombre del archivo coincide con `workflow_id`.
- Ejemplo: `onboarding_guide_ui.yaml`

---

### `tests/`
Casos de prueba y criterios de aceptación (manuales o automatizables).

Contiene:
- `onboarding_basic.md` (ejemplo)
- futuros: `onboarding_guide_ui.md`, `chat_companion_v1.md`, etc.

---

## Workflows activos (MVP)

- `onboarding_guide_ui` → onboarding con avatar guía + selección por botones.

Workflows “planned” (aún no implementados):
- `chat_companion_v1`
- `chat_info_v1`

---

## Convenciones (importante)

- Los ejemplos JSON de request/response van dentro de archivos `.md` (documentación).
- Los `.yaml` en `workflows/` son definiciones que el motor puede cargar.
- “Base” define reglas globales; “Product” define la experiencia del MVP.

---

## Estado actual

- Documentación: en progreso y versionada.
- Implementación: pendiente en backend/frontend según contratos de `product/`.

Diseño conversacional:
- Whiteks L.P.R

Responsable de implementación:
- Dev (Go/React)
