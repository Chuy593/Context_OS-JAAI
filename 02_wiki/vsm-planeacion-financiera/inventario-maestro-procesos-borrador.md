# Inventario Maestro de Procesos — borrador inicial

Fuente: transcripción reunión "NEXUS Optimus Exploración CO" con asesor SAP (Jeanpiero Linares), 13-ago-2026. Participantes internos: Diana Patricia Benjumea Muñoz, Daniela Andrea Muñeton Higuita, Jesus Carlos Almaguer Valles, Daniel Agudelo Giraldo.

Este es el primer borrador del inventario, extraído directamente de la transcripción. Fue el punto de partida del proceso de levantamiento; el inventario vigente y consolidado, con 56 procesos de todo el equipo, vive en Smartsheet, ver memory.md del proyecto. Varios de los procesos de abajo requieren profundizar, tiempos de ciclo exactos, triggers, esperas, entregables puntuales, en sesiones de mapeo dedicadas.

Nota sin confirmar: el usuario indicó que buena parte de este contenido podría corresponder a los puntos 2.1.2, 2.1.3 y 2.1.9 de un documento externo de referencia, no disponible en este repo. Ver open thread en memory.md del proyecto.

| # | Proceso | Responsable(s) mencionado(s) | Sistemas usados | Frecuencia | Descripción breve | Prioridad |
|---|---------|------------------------------|------------------|------------|--------------------|-----------|
| 1 | Extracción de base de datos maestra de causación (transacción Z "Costos, Gastos") | Daniela, Jesús | SAP (transacción Z), Excel | Mensual (parte del cierre) | Se baja de SAP el 100% de la causación contable del mes vía una transacción Z; es la base de datos oficial para todo el cascadeo de costos. | Alta |
| 2 | Clasificación/categorización de la causación por query en Excel (catálogos propios) | Jesús | Excel (queries), SAP como fuente | Mensual | Sobre la base extraída, un query propio en Excel reclasifica las cuentas GL en los elementos de costo reales, corrigiendo lo que SAP no distingue por falta de categorías de valoración. | Alta |
| 3 | Cascadeo de costos / "ficha de costos" mensual por área (Scrap Yard, Melt Shop, Rolling Mill) | Diana (dueña del archivo), equipo de costos | Excel (archivo maestro vinculado a otros archivos) | Mensual | A partir de la base clasificada, se arma la ficha de costos de cada proceso: toneladas, costos y valores unitarios, balance de masas de scrap, inventario de billets, costo unitario de producto terminado. Define el valor de inventario reportado. | Alta |
| 4 | Ajuste manual de inventario en contabilidad | Contabilidad (fuera del equipo de costos) | Excel → SAP (ajuste manual) | Mensual | Contabilidad recibe el valor de inventario calculado en el Excel de costos y ajusta el saldo en SAP contra una cuenta de ajuste genérica, no por material. | Alta (riesgo de control) |
| 5 | Actualización de recetas / listas de materiales (BOM) ideales | Daniela, con Calidad y Producción | SAP (o vía CUMOS) | En curso / reciente | Carga de recetas "ideales" de consumo real (mezcla de chatarra, aleaciones, consumibles) para que el sistema calcule variación consumo vs. variación precio. | Alta |
| 6 | Intento de cálculo de costo estándar en SAP (prueba/validación) | Daniela, con Daniel | SAP (CK11N / variantes de cálculo) | Ad hoc | Corridas de prueba de costo estándar para 2-3 materiales, comparando el valor esperado vs. el resultado de SAP; los resultados no han cuadrado (doble/triple del valor esperado). | Media-Alta |
| 7 | Validación y ajuste manual de consumos por diferencias de interfaz CUMOS–SAP | Daniel | CUMOS (piso de planta), SAP (vía interfaz con PP) | Mensual / cuando hay diferencias | Cuando las toneladas reportadas por CUMOS no cuadran con lo esperado, se revisan manualmente las órdenes involucradas y se hacen ajustes. | Media-Alta |
| 8 | Ciclos de subreparto (assessment cycles) | Daniela | SAP (CO) | Mensual (parte del cierre) | Distribución de costos entre centros de costo como parte del proceso de cierre. | Alta |
| 9 | Cierre y liquidación de órdenes de producción | Daniela | SAP (CO/PP) | Mensual | Liquidación de las órdenes de producción del mes como parte del cierre de costos. | Alta |
| 10 | Corrida de Material Ledger (cálculo de costo real) | Daniela | SAP (CKMLSP / material ledger) | Mensual | Ejecución del cálculo de costo real vía material ledger; genera documentos de valoración. Incluye liberación de precio y variación precio vs. variación consumo. | Alta |
| 11 | Revisión de balance de masas (status de calidad y disposición de producción) | Diana / equipo de costos | SAP + CUMOS + Chip Up | Mensual | Verificación de que la producción que se está costeando corresponde correctamente según estatus de calidad y disposición. | Media |
| 12 | Alimentación de reportes Power BI desde el reporte Z de Costos | Jesús | Reporte Z (SAP) → Power BI | Mensual | La misma base extraída y clasificada en Excel alimenta reportes/KPIs en Power BI, hoy no existe un reporte BI nativo desde el módulo de costos en SAP. | Media |
| 13 | Planificación y presupuesto (carga de presupuesto a nivel de cuenta) | Daniela | SAP (CO) | Anual / periódico | Carga de presupuesto a nivel de cuenta CO (clase de costo, cuenta de gasto, centro de costo). No se maneja planificación de ingresos en SAP. | Media |
| 14 | Control de presupuesto (budget control / bloqueo de gasto) | Daniela | SAP (control de presupuesto / FM) | Configuración anual, monitoreo continuo | Flag de control de presupuesto con excepciones (depreciación, seguros, payroll excluidos). Genera alertas al 80% de consumo y puede bloquear compras que excedan el presupuesto. | Media |
| 15 | Continuidad de la transacción Z crítica ante upgrade de SAP (versión 2025) | Jesús (identifica el riesgo) | SAP | Ad hoc (proyecto de upgrade) | Validar qué tablas usa la transacción Z de costos, confirmar disponibilidad post-upgrade, marcarla como crítica para el cierre mensual. | Alta (riesgo de proyecto) |
| 16 | Manejo de órdenes internas | Sin responsable directo confirmado | SAP | No especificada | Proceso confirmado como existente; sin detalle de pasos, triggers ni responsable específico. | Por definir |

## Temas transversales / dolores identificados

- Falta de categorías de valoración suficientemente detalladas en datos maestros de materiales, todo cae en "bolsas" contables muy generales, obligando a reclasificar manualmente fuera de SAP.
- Estructura de centros de costo/elementos de costo demasiado básica, solo centro de costo + cuenta contable, sin agrupación por elemento de costo.
- Falta de tarifas definidas en órdenes de producción (energía, depreciación, mano de obra), lo que impide un costeo real robusto.
- Módulo de activos fijos no conectado a las órdenes de trabajo de mantenimiento, impidiendo asociar costos de mantenimiento a un activo/equipo específico.
- Dependencia estructural de un Excel maestro para la valoración de inventario y el cierre, sin trazabilidad completa dentro de SAP.
- Falta de definición formal de subcategorías de producto (prime, byproduct, subproducto, reproceso, materia prima producida vs. comprada).

Fuente completa de la transcripción, con el desglose por persona (Daniela, Daniel, Jesús, Diana): 01_raw/_processed/vsm-reunion-sap-co-2026-08-13.md.
