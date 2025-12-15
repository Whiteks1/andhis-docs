# Onboarding – Contrato Frontend ↔ Backend (MVP)

Este documento define el contrato de comunicación entre frontend y backend
para el proceso de onboarding inicial del usuario.

No describe implementación interna ni la lógica de negocio.
Define exclusivamente qué se envía y qué se recibe.

---

## Contexto general

- El onboarding se muestra únicamente si:
  - onboarding_completed = false
- El onboarding **no es chat libre**.
- Es un flujo guiado por UI (mensajes + botones).
- El **backend controla la lógica y el estado**.
- El **frontend solo renderiza lo que el backend devuelve**.

---

## Endpoint principal

**POST /api/onboarding/action**

### Headers requeridos

```
Authorization: Bearer <JWT>
Content-Type: application/json
```

---

## Estructura general del request

```json
{
  "action": "string",
  "value": "string",
  "context": {}
}
```

Campos:

- action: tipo de acción del usuario (evento en la UI).
- value: valor seleccionado por el usuario.
- context (opcional): datos adicionales que mantienen la continuidad del flujo.

---

## Estructura general de la response

```json
{
  "progress": {
    "step": "string"
  },
  "ui": {
    "type": "message | choices",
    "text": "string",
    "action": "string",
    "choices": []
  },
  "result": {},
  "next_route": "string"
}
```

Campos:

- progress.step: paso actual del onboarding.
- ui: instrucción que define qué debe mostrar el frontend.
- result: datos finales cuando el onboarding ha concluido.
- next_route: ruta a la que debe redirigir el frontend (solo al finalizar).

---

# EVENTO 1  
## Elegir uso principal

Acción: **choose_main_use**

### Request

```json
{
  "action": "choose_main_use",
  "value": "B"
}
```

Valores posibles:

- "A" → Hablar con un avatar IA  
- "B" → Publicar y leer posts  
- "C" → Ambas  

### Response

```json
{
  "progress": {
    "step": "choose_avatar_style",
    "main_use": "B"
  },
  "ui": {
    "type": "choices",
    "text": "Elige el estilo de avatar que prefieres:",
    "action": "choose_avatar_style",
    "choices": [
      { "value": "1", "label": "Calmado y empático" },
      { "value": "2", "label": "Directo y práctico" },
      { "value": "3", "label": "Motivador / coach" },
      { "value": "4", "label": "Divertido y ligero" },
      { "value": "5", "label": "Informativo / neutral" }
    ]
  }
}
```

---

# EVENTO 2  
## Elegir estilo de avatar

Acción: **choose_avatar_style**

### Request

```json
{
  "action": "choose_avatar_style",
  "value": "3",
  "context": {
    "main_use": "B"
  }
}
```

Valores posibles:

- "1" → Calmado y empático  
- "2" → Directo y práctico  
- "3" → Motivador / coach  
- "4" → Divertido y ligero  
- "5" → Informativo / neutral  

### Response (onboarding completado)

```json
{
  "progress": {
    "step": "completed",
    "main_use": "B",
    "preferred_style": "3"
  },
  "result": {
    "selected_agent_id": "uuid-del-avatar-asignado",
    "onboarding_completed": true
  },
  "ui": {
    "type": "message",
    "text": "Listo. Tu avatar principal está configurado. Puedes cambiarlo cuando quieras en Ajustes."
  },
  "next_route": "/chat/uuid-del-avatar-asignado"
}
```

---

## Comportamiento esperado del backend

- Validar `action`, `value` y `context`.
- Resolver el avatar según el estilo seleccionado.
- Guardar en el usuario:
  - selected_agent_id
  - onboarding_completed = true
  - onboarding_completed_at
- Definir `next_route` según `main_use`.

---

## Comportamiento esperado del frontend

- Renderizar **solo** lo que indique `ui`.
- Redirigir únicamente si existe `next_route`.
- No volver a mostrar onboarding si `onboarding_completed = true`.

---

## Notas finales

- Este contrato define el MVP del onboarding.
- Puede ampliarse sin romper compatibilidad hacia adelante.
- El onboarding es independiente del chat con IA.

Estado:
- Funcionalmente aprobado  
- Pendiente de implementación  
