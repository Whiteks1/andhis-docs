# Andhis – IA Conversacional (Producto / MVP)

Este directorio contiene las **decisiones de producto y UX** relacionadas con la
IA conversacional del MVP de Andhis.

Aquí vive lo que el usuario ve y experimenta:
- onboarding guiado,
- selección de avatar,
- comportamiento esperado de cada agente.

No contiene implementación técnica.

---

## Alcance del MVP

- Red social de texto tipo X (posts).
- Onboarding guiado al primer login.
- Avatar guía neutro para explicar la app.
- Selección de avatar principal por estilo (1–5).
- Preparación para chat con IA (fase siguiente).

---

## Archivos y responsabilidades

### `agents.yaml`
Catálogo de **avatares del MVP**.

Incluye:
- `slug` del agente
- nombre visible
- descripción
- si es seleccionable
- `style_code` (1–5)
- `default_workflow_id`
- `settings` (ej. temperature)

 **Fuente de verdad** para los agentes del producto.

---

### `agents_mapping.yaml`
Mapea:
- estilo elegido en onboarding (1–5)
→ `slug` del agente real.

Usado por backend durante el onboarding.

---

### `agents_mvp.md`
Explicación humana de cada avatar:
- tono
- promesa al usuario
- límites
- cuándo usarlo

Referencia para prompts, UX y tests.

---

### `onboarding_flow.md`
Describe el **flujo paso a paso** del onboarding:
- condición de entrada
- pasos
- condición de salida

 Describe **qué pasa**, no cómo se implementa.

---

### `onboarding_contract.md`
Contrato Frontend ↔ Backend del onboarding.

Incluye:
- endpoint
- estructura de requests
- estructura de responses
- redirecciones

 **Fuente de verdad para implementación**.

---

### `workflows.md`
Lista los workflows relacionados con el producto:
- activos
- planned
- legacy

 Referencia funcional, no técnica.

---

## Relación con otros directorios

- Los workflows YAML reales viven en: `docs/ai/workflows/`
- Las políticas globales viven en: `docs/ai/base/`
- Los tests viven en: `docs/ai/tests/`

---

## Estado actual

- Onboarding diseñado y documentado.
- Avatares definidos a nivel producto.
- Chat con IA: **planned**.

Diseño conversacional:
- Whiteks L.P.R
