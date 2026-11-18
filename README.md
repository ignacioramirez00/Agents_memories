# AI Investment Research Assistant

## Introducción

AI Investment Research Assistant es una aplicación basada en inteligencia artificial diseñada para asistir en el análisis de inversiones y el seguimiento de información financiera y económica.

El sistema permite investigar empresas, analizar fundamentos financieros, evaluar riesgos y construir tesis de inversión mediante una interfaz conversacional.

A diferencia de un chatbot tradicional, la aplicación mantiene el contexto de las investigaciones y almacena información reutilizable entre distintas conversaciones. Esto permite retomar análisis anteriores, actualizar conclusiones y mantener criterios de evaluación consistentes a lo largo del tiempo.

## Objetivo del proyecto

El objetivo principal es desarrollar un asistente financiero que permita realizar investigaciones de inversión de manera iterativa, aplicando conceptos de memoria, persistencia y gestión de estado mediante LangGraph.

El proyecto busca explorar cómo construir workflows inteligentes capaces de recuperar información previa, interpretar nuevas solicitudes y actualizar únicamente los análisis que hayan sido afectados.

## Funcionalidades principales

### 1. Company Research

Permite investigar empresas y analizar diferentes aspectos de su situación financiera:

- Ingresos y crecimiento.
- Márgenes y rentabilidad.
- Flujo de caja.
- Endeudamiento.
- Ratios financieros.
- Valuación.
- Riesgos y oportunidades.
- Competidores y sector.

### 2. Investment Thesis

Permite construir y mantener una tesis de inversión para cada empresa analizada.

- Registrar los fundamentos de una inversión.
- Identificar oportunidades y riesgos.
- Definir hipótesis y criterios de evaluación.
- Actualizar conclusiones ante nueva información.
- Comparar la tesis actual con análisis anteriores.

### 3. Portfolio Analysis

Permite analizar una cartera de inversiones y comprender su composición.

- Registrar activos y posiciones.
- Analizar distribución y exposición.
- Identificar concentración de riesgos.
- Evaluar rendimiento.
- Relacionar los activos con el contexto económico.

### 4. Macro Research

Permite analizar variables económicas que pueden afectar las decisiones de inversión.

- Inflación.
- Tasas de interés.
- Tipo de cambio.
- Actividad económica.
- Indicadores financieros.
- Contexto económico nacional e internacional.

## Memoria y persistencia con LangGraph

Uno de los objetivos centrales del proyecto es implementar dos mecanismos de memoria con responsabilidades diferentes.

### Checkpointer — Short-term Memory

Permite guardar y recuperar el estado de una investigación asociada a un `thread_id`.

Por ejemplo, una investigación sobre Apple puede mantener su historial, análisis fundamental, valuación y tesis de inversión a través de múltiples interacciones.

El Checkpointer permite retomar una investigación sin comenzar desde cero.

### Store — Long-term Memory

Permite almacenar información reutilizable entre diferentes investigaciones y conversaciones.

Por ejemplo:

- Preferencias y criterios de inversión del usuario.
- Horizonte de inversión.
- Métricas financieras de interés.
- Metodología de evaluación de empresas.
- Información relevante que pueda compartirse entre investigaciones.

De esta manera, el sistema puede recuperar las preferencias del usuario al analizar distintas compañías, independientemente del `thread_id` utilizado.

## Arquitectura conceptual

El flujo general del sistema contempla:

1. El usuario realiza una consulta desde la interfaz conversacional.
2. LangGraph recupera el estado de la investigación mediante el Checkpointer.
3. El sistema consulta el Store para recuperar información compartida relevante.
4. Un nodo de clasificación identifica el tipo de solicitud.
5. Se ejecuta el workflow correspondiente.
6. Se actualiza el estado con los resultados obtenidos.
7. El Checkpointer persiste el nuevo estado.
8. El usuario recibe el análisis actualizado.

## Tecnologías

- **Python:** lenguaje principal.
- **LangGraph:** orquestación de workflows, gestión del estado y memoria.
- **LangChain:** integración con modelos de lenguaje.
- **OpenAI:** proveedor de modelos de lenguaje.
- **Pydantic:** validación y estructuración de datos.
- **Streamlit:** interfaz de usuario.
- **PostgreSQL:** persistencia de checkpoints y memoria a largo plazo.

## Conceptos técnicos a desarrollar

Este proyecto está orientado al aprendizaje y aplicación de los siguientes conceptos:

| Concepto | Aplicación |
|---|---|
| State | Estado compartido durante una investigación. |
| Checkpointer | Persistencia y recuperación del estado por thread. |
| Thread ID | Identificación de cada investigación conversacional. |
| Store | Memoria compartida entre diferentes investigaciones. |
| Namespace | Organización de la información almacenada en el Store. |
| Memory | Recuperación de información relevante para nuevas interacciones. |
| Conditional Edges | Selección dinámica de workflows según la solicitud. |
| Pydantic | Modelado y validación de resultados estructurados. |
| State Management | Actualización selectiva de la información del proyecto. |

## Alcance inicial

La primera versión se enfocará en el análisis fundamental de empresas y la gestión de tesis de inversión.

Inicialmente, la información financiera podrá ingresarse manualmente o mediante archivos. En etapas posteriores se incorporarán APIs externas para obtener cotizaciones, balances e indicadores económicos actualizados.

El foco principal no será construir una plataforma financiera completa, sino comprender cómo diseñar un asistente inteligente con memoria persistente, estado compartido y workflows condicionales.

## Consideraciones

Los análisis generados por inteligencia artificial son herramientas de investigación y apoyo a la toma de decisiones. No constituyen recomendaciones financieras personalizadas ni garantizan resultados de inversión.

La información financiera deberá diferenciar datos observados, estimaciones y conclusiones generadas por el modelo, incluyendo fuentes y fechas cuando corresponda.

---

**AI Investment Research Assistant — Stateful Financial Research with LangGraph**