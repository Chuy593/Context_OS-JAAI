# Listado de Tareas, Procesos y Actividades Mencionadas — Reunión SAP CO (13-ago-2026)

Fuente: transcripción "NEXUS Optimus Exploración CO" con Jeanpiero Linares (724). Listado simple, no documentación completa, para apoyar el llenado de las tareas del WBS 2.1.2 (Daniel), 2.1.3 (Daniela) y 2.1.9 (Jesús) en la plantilla oficial. Migrado desde el Project "VSM Planeación Financiera Optimus Steel" de claude.ai el 2026-08-25. Destilado y consolidado en la tabla de inventario: 02_wiki/vsm-planeacion-financiera/inventario-maestro-procesos-borrador.md.

## Daniela Andrea Muñeton Higuita (WBS 2.1.3)

- Cascadeo de costos / armado de la "ficha de costos" mensual (Scrap Yard, Melt Shop, Rolling Mill) a partir de la base de causación.
- Organización manual en Excel de la causación bajada de SAP en grupos/categorías (scrap y sus componentes, plan de presupuesto vs. ejecución real).
- Actualización de recetas (BOM) de consumo real / ideales, en conjunto con Calidad y Producción.
- Intentos de cálculo de costo estándar en SAP para materiales puntuales (pruebas de validación, con apoyo de Daniel).
- Ciclos de subreparto (assessment cycles), parte del cierre mensual.
- Cierre y liquidación de órdenes de producción.
- Ejecución/corrida de Material Ledger (cálculo de costo real), una vez al mes; genera documentos, libera precio, calcula variación precio vs. variación consumo.
- Revisión del balance de masas del cierre.
- Búsqueda y corrección de errores durante la corrida del cierre (ciclos de subreparto, etc.), resolución manual de problemas.
- Carga de presupuesto a nivel de cuenta CO (clase de costo, cuenta de gasto, centro de costo).
- Activación/gestión del control de presupuesto (flag, excepciones de cuentas como depreciación, seguros, payroll; alertas al 80%).

## Daniel Agudelo Giraldo (WBS 2.1.2)

- Apoyo en los intentos de cálculo de costo estándar en SAP (pruebas con Daniela).
- Revisión y ajuste manual de consumos cuando hay diferencias entre lo reportado por CUMOS y lo esperado (ej. diferencias en toneladas: se revisan las órdenes involucradas y se corrige).
- Manejo/detalle técnico de la interfaz CUMOS–SAP.

## Jesus Carlos Almaguer Valles (WBS 2.1.9)

- Extracción de la base de datos maestra de causación desde SAP vía transacción Z ("Costos, Gastos"), la transacción oficial para la bajada mensual.
- Clasificación de la causación extraída mediante queries propios en Excel: reasigna cuentas GL a su elemento de costo real (ej. ítems de "Supplies and Tools" que en realidad son "Rolls and Guides" o mantenimiento).
- Alimentación de reportes/KPIs en Power BI a partir de la misma base de Costos-Gastos ya clasificada.
- Identificación y gestión del riesgo de continuidad de la transacción Z ante el upgrade de SAP (versión 2025): validar qué tablas usa, confirmar disponibilidad post-upgrade, marcarla como crítica para el cierre mensual.
- Solicitud/evaluación de mejora futura de la transacción Z (conectarla al módulo de órdenes de compra para traer más detalle).
- Evaluación de una segunda extracción de datos separada para movimientos de inventario (clase de movimiento, cuenta contable, pedido, materiales), para no sobrecargar una sola extracción.

## Diana Patricia Benjumea Muñoz (WBS 2.1.1, referencia, no solicitado por ahora)

- Definición y explicación de la estructura de costeo estándar fuera de SAP (dueña del archivo maestro de cascadeo).
- Envío del valor de inventario calculado en Excel a Contabilidad para su ajuste contable en SAP.
- Revisión conceptual de la coherencia entre recetas/tarifas y el costo real.
- Definición de categorías de producto (prime, byproduct, subproducto, reproceso, materia prima producida vs. comprada), pendiente de mapear en el sistema.

## Actividades/procesos mencionados sin responsable claro (a confirmar)

- Manejo de órdenes internas (confirmado que existe el proceso, sin detalle).
- Trazabilidad de producción vía CUMOS y Chip Up (interfase de inventario y facturación/despachos), no se especificó responsable directo del equipo de Planeación Financiera.
