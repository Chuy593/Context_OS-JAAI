# Optimus Steel — Data Warehouse — State

Estado operativo actual del diseño del Data Warehouse Financiero y Operativo de Optimus Steel. El histórico vive en archive.md de esta carpeta — aquí solo lo necesario para operar hoy.

Last updated: 2026-08-25 (documentado el estado AS-IS del proceso actual, en sesión de Cowork)

## State

**AS-IS (proceso actual):**

SAP S/4HANA (FI/GL, CO, Cost Centers, Internal Orders, Materials, Vendors, Producción, Manufacturing costs) → extracción a Excel por períodos cerrados (Ledger 2025 P1-P9, Ledger 2025 P10-P12, Ledger 2026 P1-P6 ~1.29M registros) → Power Query "Ledger_2" (núcleo de la lógica de negocio: clasificación de Familia, Tipo de Orden, CECO, Área, Account, Nivel 1/2/3, Tipo de costo, usando tablas auxiliares de Accounts/Cost Centers/Materials/Families/Cost classification/Areas/Orders) → Power BI (Actual Cost, Budget, Variance, Cost per Ton, Production, Manufacturing Cost, dashboards de Monthly Cost Review) + Excel (pivots, ad-hoc).

Intento paralelo de repositorio intermedio en Access para consolidar el histórico (Append de los Excel): ya ~2GB, falla al intentar agregar los ~1.29M registros de 2026 P1-P6 (límite de tamaño/operación).

**Diagnóstico:** el problema no es solo volumen/performance — es que la lógica de negocio está demasiado acoplada al proceso de transformación (Power Query). Cada consumidor corre el riesgo de reimplementar/duplicar reglas → inconsistencia entre reportes.

**TO-BE (visión, aún no diseñado en detalle):** SAP/Excel → Data Layer → Business Rules → Consolidated Data → Power BI + Excel (mismo consumo, sin reconstruir lógica). Preguntas abiertas: arquitectura (fact tables/dimensiones/master data/reglas de negocio separados), ETL estructurado, almacenamiento histórico multi-año sin reproceso mensual completo, performance a escala de millones de registros, governance (linaje, trazabilidad, reconciliación contra SAP).

**Carpeta conectada:** "Data Warehouse" (OneDrive - Turia) — vacía a la fecha (2026-08-25). Aún no se han subido los archivos de Ledger, Access, ni el M code del Power Query actual para revisión directa.

## Open threads

- [ ] Subir a la carpeta conectada: archivos Ledger históricos, base Access actual, código M de Power Query "Ledger_2", tablas auxiliares (Accounts, Cost Centers, Materials, Families, Cost classification, Areas, Orders).
- [ ] Diseñar la arquitectura TO-BE en detalle (capas, modelo de datos, motor de almacenamiento/consulta).
- [ ] Definir estrategia de migración que preserve el conocimiento de negocio de Ledger_2 sin reconstruirlo desde cero.
- [ ] Resolver el límite de Access como repositorio intermedio (ya no escala a 2026 P1-P6).

## References

- Reglas y rol del asistente en este proyecto → CLAUDE.md de esta carpeta.
- KPIs y áreas productivas de Optimus Steel (compartido) → 02_wiki/optimus-steel/.
- Instrucciones completas del proyecto "Data Warehouse" en Claude Cowork (propósito, rol, principio "build once use everywhere") — ya distribuidas entre este archivo y CLAUDE.md, no se duplican aquí.
