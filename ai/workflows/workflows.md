# Workflows – Andhis

Este documento lista los workflows conversacionales del sistema Andhis
desde el punto de vista de producto y experiencia de usuario.

No contiene lógica técnica ni definición de estados.
Los workflows reales se definen en YAML dentro de `docs/ai/workflows/`.

---

## Workflows activos

### onboarding_basic
- **Estado:** activo (MVP)
- **Propósito:** Dar la bienvenida al usuario, recoger información básica y preparar el sistema.
- **Entrada:** Primer login con `onboarding_completed = false`
- **Salida:** Usuario preparado para usar la app
- **YAML:** `docs/ai/workflows/onboarding_basic.yaml`

---

## Workflows planificados

### chat_first_contact
- **Estado:** planned
- **Propósito:** Primer contacto del usuario con su avatar tras el onboarding.
- **Entrada:** Usuario accede al chat por primera vez
- **Salida:** Usuario entiende cómo interactuar con su avatar
- **YAML:** (pendiente)

---

## Workflows legacy
_Ninguno por el momento._
