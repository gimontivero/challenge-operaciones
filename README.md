# Dashboard de soporte - Challenge Operaciones

Dashboard HTML para el challenge de Analista de Operaciones. La vista esta pensada para que un lider de Operaciones pueda revisar el flujo de soporte, detectar foco operativo y simular una alerta accionable.

## Archivos

- `index.html`: dashboard final.
- `logo.svg`: logo usado en el header.
- `README.md`: descripcion del entregable.
- `proceso-ia.pdf`: documento breve sobre proceso, herramientas, correcciones y supuestos.

## Que muestra el dashboard

- KPIs operativos: tiempo promedio de resolucion, porcentaje de escalados, tickets abiertos criticos y satisfaccion promedio.
- Prioridad de atencion inmediata: tickets abiertos ordenados por criticidad, escalamiento, cliente, tipo de bug y dias abiertos.
- Principal alerta operativa: bug con mayor incidencia, tickets totales, abiertos, escalados y clientes afectados.
- Estado de tickets: tickets por estado agrupados por mes.
- Evolucion semanal: tickets creados vs tickets cerrados.
- Patrones de incidencia: bugs que concentran volumen, clientes afectados, backlog y escalaciones.
- Clientes afectados: ranking operativo por demora, criticidad e insatisfaccion.
- Acciones recomendadas: acciones priorizadas para reducir backlog, insatisfaccion y reincidencia.

## Fuente de datos

El dashboard lee como fuente principal el Google Sheet de tickets:

`https://docs.google.com/spreadsheets/d/1UM-ukK-6l8NJtXShLErb3E4H4Gx6_v0AuIo9DMssdgU/edit?usp=sharing`

El HTML usa el endpoint GViz/JSONP de Google Sheets para poder funcionar como dashboard estatico. Si el Sheet no responde, conserva un CSV embebido como respaldo para que el dashboard siga abriendo.

La unidad de analisis es una fila por ticket. Los tickets abiertos no tienen fecha de cierre ni tiempo de resolucion final, por eso se usan para backlog, aging y prioridad, pero no para calculos de resolucion cerrada.

## Simulacion de alertas

El boton `Crear alerta` permite simular una alerta operativa estilo Slack sin depender de acceso real a Slack.

Flujo:

1. Elegir `Cliente en riesgo`, `Bug con volumen alto de tickets` o ambas.
2. Crear la alerta.
3. Revisar la vista previa del mensaje.
4. Guardar la alerta y cerrar el modal.

La simulacion usa los filtros aplicados en el dashboard y calcula automaticamente el cliente o bug con mayor riesgo operativo.

