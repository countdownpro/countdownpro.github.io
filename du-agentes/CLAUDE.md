# du. Comunicación: sistema de agentes

Este archivo lo lee Claude Code en cada sesión. Es la constitución del sistema.

## Quién habla
Gastón y Salva (du.). Respuestas en español rioplatense, tono profesional y directo.
Prohibido el guion largo en cualquier documento que vea un cliente.

## Agentes
| Agente | Archivo | Modelo | Hace |
|---|---|---|---|
| Gestor | .claude/agents/gestor.md | opus | Lee el pedido, decide trayectoria, reparte, controla calidad |
| Estratega | .claude/agents/estratega.md | opus | Biblia de persona, preguntas, estrategia, biblia de contenido |
| Editor | .claude/agents/editor.md | sonnet | Marcos de edición, storyboard, edición Edits/Adobe |
| Métricas | .claude/agents/metricas.md | sonnet | Reporte mensual por cliente, piezas estrella, PPT |

## Ruteo de modelos (lo aplica el Gestor)
- **Opus**: estrategia, criterio, síntesis de biblias, decisiones de trayectoria.
- **Sonnet**: ejecución con criterio (guiones, storyboards, análisis de métricas, PPT).
- **Haiku**: tareas mecánicas (renombrar, ordenar carpetas, extraer datos, formatear tablas).
- **Fable**: SOLO con autorización explícita de Gastón en el chat. El Gestor pregunta
  "¿Autorizás Fable para X? Motivo: Y. Alternativa sin Fable: Z." y espera respuesta.

## Estructura
- `biblioteca/`: libros y marcos (Golden Circle de Sinek, etc.). Solo lectura.
- `du/biblia-du.md`: cómo piensa du. (se escribe una vez, se revisa por versión).
- `clientes/<cliente>/`: una carpeta por cliente, copiada de `clientes/_plantilla/`.
- `clientes/<cliente>/estado.md`: fase actual, pendientes y aprobaciones. Fuente de verdad.
- `_cola/`: pedidos sueltos que el Gestor todavía no asignó.

## Reglas de traspaso
1. Ningún agente avanza de fase sin que `estado.md` diga `APROBADO por: <nombre>`.
2. Cada entrega termina con un bloque `## Para el siguiente agente` (qué usar, qué no tocar).
3. Si falta un insumo, el agente lo pide en una línea y frena. No inventa.
4. Gastón explica lo mínimo: el Gestor infiere desde `estado.md`, las biblias y el historial.

## Fuentes y conectores
- Google Drive, Docs, Slides: lectura de bibliografía y entregables.
- Granola: transcripciones de reuniones con clientes.
- Supermetrics: métricas de redes.
- Adobe for creativity: edición profunda de video.
- Skills existentes a reutilizar: `du-estudio:*`, `guionista-du`, `edicion-macro-gns`, `critica`.
