# Contrato técnico – Motor de workflows y API de conversación

Este documento especifica cómo debe comportarse el motor de workflows
que interpreta los YAML de Andhis y cómo se integra con la API de chat.


## 1. Conceptos básicos

### 1.1. Workflow

Un workflow es un documento YAML con al menos:

- `id`: identificador único del flujo (`onboarding_basic`).
- `name`: nombre descriptivo.
- `description`: propósito del flujo.
- `states`: lista ordenada de estados.

Ejemplo mínimo:

```yaml
id: "onboarding_basic"
name: "Onboarding básico"
description: "Flujo de bienvenida para entender quién es el usuario y qué quiere conseguir."
states:
  - id: "start"
    ...
