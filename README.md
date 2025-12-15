Andhis – AI Documentation

Este repositorio contiene la documentación de diseño conversacional e IA del proyecto Andhis.

Aquí se define qué hace la IA, cómo se comporta y cómo debe integrarse, antes de cualquier implementación técnica.

Alcance del repositorio

Este repositorio cubre exclusivamente:

Definición de agentes (avatares) de IA

Diseño de workflows conversacionales (YAML)

Contratos de API relacionados con IA (onboarding, chat)

Políticas globales y límites de comportamiento

Tests funcionales de workflows

Qué es este repositorio

Fuente de verdad del diseño conversacional

Referencia compartida entre producto, UX y backend

Documentación versionada y revisable

Base para implementación determinista de IA

Qué NO es este repositorio

No contiene código backend

No contiene código frontend

No define lógica de infraestructura ni runtime

No ejecuta workflows

Nota sobre la estructura del repositorio

Este repositorio está dedicado exclusivamente a la documentación de IA de Andhis.

Por ese motivo, la estructura comienza directamente en ai/, en lugar de docs/ai/ como ocurre en el repositorio principal de la aplicación.

Conceptualmente, ai/ en este repositorio equivale a docs/ai/ en el monorepo principal.
La documentación y su organización son las mismas; únicamente cambia el punto de entrada.

Estructura de carpetas

ai/
├─ base/ — Políticas globales de IA (límites, estilo, seguridad)
├─ product/ — Decisiones de producto y UX relacionadas con IA
├─ agents/ — Definición de agentes (técnica y documentación humana)
├─ workflows/ — Workflows conversacionales en YAML
├─ tests/ — Tests funcionales de workflows
└─ api/ — Contratos de API relacionados con IA

Fuentes de verdad (importante)

Cada tipo de información tiene una única fuente de verdad:

Comportamiento global de la IA → ai/base/

Agentes (definición técnica) → ai/agents/agents_registry.yaml

Agentes (producto y UX) → ai/agents/agents_mvp.md

Mapeo onboarding → ai/agents/agents_mapping.yaml

Workflows conversacionales → ai/workflows/

Tests de comportamiento → ai/tests/

Contratos de API → ai/api/

No se deben duplicar decisiones entre archivos.

Estado del proyecto

Onboarding: diseñado y documentado

Agentes IA: definidos a nivel de producto

Motor de workflows: pendiente de implementación

Chat IA completo: planned

La documentación está en iteración activa.

Reglas de edición

Cambios estructurales deben revisarse antes de implementarse.

Cambios de copy o tono pueden iterarse libremente.

IDs, slugs y nombres técnicos no se cambian sin coordinación.

Todo cambio debe preservar coherencia entre:

workflows

contratos

tests

Rol y responsabilidad

Diseño conversacional y documentación IA: Whiteks

Implementación técnica: equipo de desarrollo

Este repositorio existe para que diseño y backend avancen alineados y sin ambigüedades.
