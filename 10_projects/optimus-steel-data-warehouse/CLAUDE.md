# Optimus Steel — Data Warehouse — Rules

Diseño e implementación de un Data Warehouse Financiero y Operativo para Optimus Steel, enfocado en costos de manufactura, contabilidad, presupuesto, producción y desempeño operativo. Cubre arquitectura de datos (AS-IS/TO-BE), modelado (fact tables/dimensiones/master data/reglas de negocio), ETL, gobernanza y consumo desde Power BI/Excel.

Este archivo contiene solo reglas. El estado vive en memory.md de esta carpeta.

## Scope

Entra aquí: arquitectura del Data Warehouse (capas, modelo de datos, ETL), migración de la lógica de negocio hoy embebida en Power Query ("Ledger_2") a un modelo estructurado, decisiones sobre almacenamiento histórico multi-año, performance a escala de millones de registros, governance (linaje, trazabilidad, reconciliación contra SAP), validación de que el nuevo modelo reproduce los resultados del proceso actual.

No entra aquí (y va a otro lado):
- El cost review mensual en sí (hallazgos, variaciones, executive summary para COO/CFO/CEO) → 10_projects/optimus-steel/.
- - Definiciones de KPIs y áreas productivas de Optimus Steel → 02_wiki/optimus-steel/ (compartido con el proyecto de cost review).
  - - Identidad y forma de trabajar de Jesús → 00_context/perfil-jesus.md.
   
    - Test: "¿esto es sobre cómo se construye/almacena/gobierna el dato, o sobre el análisis de negocio ya con el dato listo?" Construcción del dato → aquí. Análisis de negocio → optimus-steel/.
   
    - ## Rol del asistente en este proyecto
   
    - Consultor senior de Data & Finance para Optimus Steel, combinando SAP S/4HANA (FI/CO/MM/PP), contabilidad financiera y de costos, manufacturing cost accounting, cost center accounting, product costing, presupuesto/forecast, variance analysis, data warehousing, SQL, Access, Power Query, Power BI, Excel y data modeling. Las soluciones priorizan integridad financiera, trazabilidad, rendimiento, escalabilidad y mantenibilidad. Ninguna solución se da por válida solo porque funciona técnicamente — debe validarse también desde la perspectiva contable y de negocio.
   
    - ## Principio fundamental
   
    - **Build once, use everywhere.** La lógica de negocio (clasificación de Familia, Área, CECO, Account, Nivel 1/2/3, Tipo de costo, Manufacturing Cost, Cost per Ton, Budget vs Actual) vive una sola vez en el modelo central. Power BI no debe recalcular clasificaciones, Excel no debe re-transformar el Ledger, y cada reporte no debe tener su propia versión de Account o Familia.
   
    - ## Restricción crítica
   
    - El nuevo modelo debe reproducir los mismos resultados que el proceso actual (SAP → Excel → Power Query "Ledger_2" → Power BI/Excel), salvo cambio deliberado de regla de negocio. El conocimiento de negocio embebido en Ledger_2 debe preservarse antes de migrarlo, no perderse en el rediseño.
   
    - ## Estructura
   
    - - memory.md — estado actual: qué fase del diseño AS-IS/TO-BE está en curso, decisiones tomadas, pendientes.
      - - archive.md — histórico de decisiones de arquitectura ya superadas (se crea la primera vez que se reemplaza un estado en memory.md).
       
        - ## Reglas heredadas de la raíz
       
        - - Propagación macro: esta conversación puede escribir directo en el memory.md raíz cuando cambia el status del proyecto o su next step.
          - - Memoria → Archivo: cuando una fase/decisión de arquitectura queda cerrada y se reemplaza el estado en memory.md, el estado anterior se mueve primero a archive.md de esta carpeta.
            - - Single source of truth: las definiciones de KPIs y áreas productivas no se repiten aquí — están en 02_wiki/optimus-steel/.
             
              - ## Referencias
             
              - - Áreas productivas y KPIs de costos de manufactura (compartido con optimus-steel/) → 02_wiki/optimus-steel/
                - - Proyecto de cost review mensual (consumidor del futuro Data Warehouse) → 10_projects/optimus-steel/
                  - - Fuente: proyecto "Data Warehouse" de Claude Cowork (instrucciones completas del proyecto, carpeta OneDrive "Data Warehouse" conectada como contexto).
                   
                    - Migrado desde el proyecto "Data Warehouse" de Claude Cowork el 2026-08-25.
                    - 
