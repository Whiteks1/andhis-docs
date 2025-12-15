
# Contrato API – /api/onboarding/action (FINAL)

Este documento define el contrato técnico del endpoint de onboarding.
Es la **fuente de verdad para la implementación backend** y debe cumplirse
exactamente para garantizar coherencia entre backend, frontend y tests.

---

## Endpoint

POST /api/onboarding/action

---

## Headers requeridos

```http
Authorization: Bearer <JWT>
Content-Type: application/json
````

---

## Principios generales

* El onboarding **no es chat libre**.
* El backend controla:

  * estado,
  * transiciones,
  * validaciones,
  * persistencia.
* El frontend:

  * envía acciones,
  * renderiza **exactamente** la respuesta recibida,
  * no implementa lógica de decisión.

---

## Estructura general del request

```json
{
  "action": "START | SUBMIT_TEXT | SELECT_OPTION",
  "value": "string | null",
  "context": {}
}
```

### Campos

* `action`: acción explícita enviada por el frontend.
* `value`: valor asociado a la acción (texto libre u opción seleccionada).
* `context`: contexto adicional enviado por el frontend (normalmente vacío).

---

## Estructura general del response

```json
{
  "state": "string",
  "messages": [
    {
      "role": "system | assistant",
      "content": "string"
    }
  ],
  "ui": {
    "type": "buttons | input | none",
    "options": []
  },
  "context": {
    "onboarding_completed": false
  }
}
```

### Reglas del response

* `state` refleja **el estado actual del workflow**.
* `messages` contiene únicamente mensajes a renderizar.
* `ui` define el tipo de interacción esperada:

  * `buttons`: selección cerrada,
  * `input`: texto libre,
  * `none`: sin interacción.
* `context` contiene datos persistentes relevantes para el flujo.

---

## Acciones soportadas

### 1️⃣ START

Inicia o reanuda el onboarding.

#### Request

```json
{
  "action": "START",
  "value": null,
  "context": {}
}
```

#### Comportamiento esperado

* Mensaje de bienvenida.
* Transición automática al estado `ask_name`.

---

### 2️⃣ SUBMIT_TEXT

Usada para inputs de texto libre (nombre, objetivo).

#### Ejemplo – responder nombre

```json
{
  "action": "SUBMIT_TEXT",
  "value": "Me llamo Marta",
  "context": {}
}
```

#### Reglas

* El backend valida `input_not_empty`.
* Si el input es válido → transición al siguiente estado.
* Si es inválido → se repite el estado actual.

---

### 3️⃣ SELECT_OPTION

Usada para selección mediante botones (uso principal, estilo, etc.).

#### Ejemplo – elegir estilo

```json
{
  "action": "SELECT_OPTION",
  "value": "3",
  "context": {}
}
```

#### Reglas

* El backend valida la opción seleccionada.
* Resuelve el significado de la opción.
* Asigna el agente correspondiente usando `agents_mapping.yaml`.

---

## Estados principales del workflow

| Estado     | Tipo     | Acción esperada |
| ---------- | -------- | --------------- |
| `start`    | system   | Mensaje inicial |
| `ask_name` | prompt   | SUBMIT_TEXT     |
| `ask_goal` | prompt   | SUBMIT_TEXT     |
| `summary`  | llm      | Generar resumen |
| `end`      | terminal | Cierre          |

---

## Reglas estrictas (obligatorias)

### Estado `summary`

* Usar el nombre del usuario.
* Resumir el objetivo indicado.
* Proponer **2 o 3 pasos concretos y accionables**.
* **No hacer preguntas**.
* No introducir lógica de chat libre.

### Estado `end`

* Mensaje corto de cierre.
* Confirmación implícita de finalización.
* **No hacer preguntas**.

---

## Manejo de errores

* Acción inválida:

  * error controlado,
  * no rompe el estado.
* Input vacío:

  * se repite el estado actual.
* Estado inexistente:

  * reiniciar onboarding con `START`.

---

## Persistencia al finalizar

Al completar el onboarding, el backend debe persistir:

```json
{
  "onboarding_completed": true,
  "selected_agent_id": "calm_companion"
}
```

Estos valores serán utilizados posteriormente por `/api/chat`.

---

## Nota final

Este contrato debe cumplirse **exactamente** para que:

* los tests pasen,
* el frontend funcione sin lógica adicional,
* el onboarding sea determinista, estable y predecible.

Este documento es **material de implementación**
