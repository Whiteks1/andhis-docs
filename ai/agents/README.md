# Andhis – Agentes IA

Este directorio contiene la definición y documentación de los agentes
(avatars) de IA del sistema Andhis.

Aquí se separan claramente:
- la **configuración técnica** consumible por el sistema,
- la **documentación de producto / UX**,
- y los **mapeos funcionales** usados durante el onboarding.

---

## Archivos principales

### `agents_registry.yaml`
**Estado:** PREPARADO (draft, no consumido por código)

Registro técnico unificado de todos los agentes del sistema.

- Define qué agentes existen.
- Establece su tipo (system / selectable).
- Indica el workflow por defecto y ajustes técnicos.
- Está pensado para ser la **fuente de verdad técnica** cuando se implemente.

> ⚠️ Actualmente este archivo **NO es leído por el backend**.

---

### `agents_mvp.md`
Documento humano de producto y UX.

- Describe el tono, promesa y límites de cada avatar.
- Sirve como referencia para diseño, tests y prompts.
- No es consumido por el sistema.

---

### `agents_mapping.yaml`
Mapa funcional usado durante el onboarding.

- Relaciona el `style_code` elegido por el usuario (1–5)
  con el agente real (`id` / `slug`).
- Usado por backend durante el onboarding.

---

## Relación con otros directorios

- Políticas globales de IA: `docs/ai/base/policies.md`
- Workflows YAML: `docs/ai/workflows/`
- Tests de workflows: `docs/ai/tests/`

---

## Reglas de edición (importante)

Mientras `agents_registry.yaml` esté en estado *draft*:

- Cambios **técnicos** → `agents_registry.yaml`
- Cambios de **producto / UX** → `agents_mvp.md`
- Cambios de **onboarding** → `agents_mapping.yaml`
- Cambios de **seguridad y límites globales** → `policies.md`

---

## Nota final

Este diseño está preparado para escalar:
- nuevos agentes,
- variantes por estilo,
- consumo dinámico desde backend,
- evolución del chat con IA.

Cualquier cambio estructural debe discutirse antes de implementarse.
