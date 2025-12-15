# API Contract – /api/chat (v1)

This document defines the technical contract for the chat endpoint.
It is the **single source of truth** for backend ↔ frontend interaction.

---

## Endpoint

POST /api/chat

---

## Required Headers

````
```http
Authorization: Bearer <JWT>
Content-Type: application/json
````

## General Principles

This endpoint handles **free chat** (not onboarding).

* The backend:

    - validates authentication,

    - validates agent existence,

    - applies global AI policies.

* The frontend:

    - sends user messages,

    - renders responses exactly as received.

* No UI logic is implemented in the backend beyond basic hints.

## Request Schema 

````
````json
{
  "agent_id": "string",
  "message": "string",
  "conversation_id": "string | null",
  "context": {}
}
````

## Field rules
agent_id`

    - Required

    - Must exist in *agents_registry.yaml*

`message`

    - Required

    - Plain user input

`conversation_id`

    - Optional

    - Used to continue an existing conversation

`context`

    - Optional

    - Reserved for future extensions

## Response Schema
````
```json
{
  "messages": [
    {
      "role": "assistant",
      "content": "string"
    }
  ],
  "conversation_id": "string",
  "agent_id": "string"
}
````

## Error Responses
**401– Unauthorized**

User is not authenticated.

**400 – Invalid agent**

The provided agent_id does not exist.

**400 – Invalid message**

Empty or malformed input.

## Relation to Agents

- The backend does not interpret personality manually.

- Agent behavior is defined exclusively in:

    - `ai/agents/agents_registry.yaml`

## Relation to Workflows

* Current state:

 - Free chat without complex workflows.

* Planned:

  - Agent-specific workflows (future).

This contract does *not* require a workflow engine to be implemented yet.



