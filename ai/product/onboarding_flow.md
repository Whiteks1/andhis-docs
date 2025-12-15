# Onboarding – Flujo paso a paso (MVP)

Este documento describe QUÉ PASA, no cómo se implementa.

## Condición de entrada
- El usuario inicia sesión.
- `onboarding_completed = false`.

## Flujo

1. El sistema muestra un avatar guía neutro.
2. El guía explica brevemente qué es la app.
3. El usuario elige su uso principal:
   - Publicar y leer posts
   - Hablar con un avatar IA
   - Ambas
4. El usuario elige el estilo de avatar (1–5).
5. El sistema asigna un avatar principal.
6. El sistema marca onboarding como completado.
7. El usuario es redirigido al feed o al chat.

## Condición de salida
- `onboarding_completed = true`
- `selected_agent_id` asignado
