# AI Project Architect

## Introducción

AI Project Architect es una aplicación basada en inteligencia artificial que permite crear, modificar y mantener la documentación técnica de proyectos de software mediante una interfaz conversacional.

A diferencia de un generador de documentación tradicional, el sistema conserva el contexto de cada proyecto y permite realizar cambios de manera iterativa. El usuario puede solicitar modificaciones sobre la arquitectura, los requerimientos o las tecnologías utilizadas, sin tener que proporcionar nuevamente toda la información del proyecto.

Por ejemplo, después de generar la arquitectura inicial de una aplicación con FastAPI y PostgreSQL, el usuario puede solicitar cambiar el backend a NestJS y agregar notificaciones por WhatsApp. El sistema recupera el contexto anterior, identifica los componentes afectados y actualiza la documentación correspondiente.

## Objetivo

El objetivo principal es implementar un flujo conversacional con memoria persistente utilizando LangGraph, permitiendo que cada proyecto mantenga su propio contexto entre distintas interacciones.

## Funcionalidades principales

- Crear proyectos a partir de una descripción inicial.
- Generar requerimientos funcionales y no funcionales.
- Diseñar la arquitectura técnica del proyecto.
- Generar documentación técnica en Markdown.
- Mantener el contexto de cada proyecto entre conversaciones.
- Interpretar solicitudes de modificación sobre proyectos existentes.
- Actualizar únicamente los componentes afectados cuando sea posible.
- Recuperar el estado de un proyecto después de cerrar y volver a abrir la aplicación.
- Mantener conversaciones y proyectos independientes.

## Tecnologías

- **Python:** lenguaje principal.
- **LangGraph:** orquestación de flujos y gestión del estado.
- **LangChain:** integración con modelos de lenguaje.
- **Pydantic:** validación y estructuración de respuestas.
- **OpenAI:** proveedor de modelos de lenguaje.
- **Streamlit:** interfaz de usuario.
- **PostgreSQL:** persistencia de checkpoints y estado conversacional.

## Conceptos principales

Este proyecto permite trabajar con algunos conceptos fundamentales de LangGraph:

- **State:** información compartida entre los nodos del grafo.
- **Checkpointer:** mecanismo que permite guardar y recuperar el estado de una ejecución.
- **Thread ID:** identificador que permite mantener el contexto de una conversación o proyecto.
- **Memory:** capacidad de recuperar información previa para continuar una interacción.
- **Conditional Edges:** permiten decidir qué parte del flujo debe ejecutarse según la solicitud del usuario.

## Funcionamiento general

1. El usuario crea un proyecto y proporciona una descripción inicial.
2. LangGraph procesa la información y genera los primeros documentos.
3. El estado del proyecto se guarda mediante un checkpointer.
4. El usuario puede solicitar modificaciones desde la interfaz conversacional.
5. El sistema recupera el estado anterior e identifica qué información necesita actualizar.
6. Se ejecutan los nodos correspondientes y se actualiza la documentación.
7. Los cambios quedan guardados para futuras interacciones.

## Alcance del proyecto

El foco de este ejercicio está puesto en la memoria conversacional, la persistencia del estado y la ejecución de flujos dinámicos con LangGraph.

No se busca implementar un sistema multiagente complejo ni incorporar RAG o bases de datos vectoriales. La prioridad es comprender cómo gestionar el contexto y mantener workflows consistentes a través de múltiples interacciones.

---

**AI Project Architect — Conversational Memory & Stateful Workflows**