---
name: actualizacion-inventario-vsm
description: Sincroniza a demanda el Inventario Maestro de Procesos del proyecto VSM Planeación Financiera en Smartsheet contra los archivos Excel individuales del equipo (carpeta VSM local del usuario). Usar cuando el usuario pide "ejecuta la actualización del inventario", "actualiza el inventario VSM" o equivalente.
---

# Actualización del Inventario Maestro de Procesos VSM — Procedure (a demanda)

v1.0 — 2026-08-25: migrado desde el Project "VSM Planeación Financiera Optimus Steel" de claude.ai, sin cambios operativos.

Sincroniza el Inventario Maestro de Procesos en Smartsheet contra los archivos Excel individuales de cada persona del equipo VSM.

Goal de la procedure: mantener Smartsheet como fuente única y actualizada del inventario, sin duplicar captura entre los Excel individuales y la hoja maestra.

Dispara con: el usuario (Jesús "Chuy" Almaguer) escribe algo como "ejecuta la actualización del inventario" o "actualiza el inventario VSM". Ejecutar de inmediato, sin pedir confirmación de cada paso, los criterios de decisión ya están definidos abajo, salvo el gate explícito del Paso 7 (más de 15 procesos nuevos).

Prerequisitos:

- Conexión al dispositivo del usuario vía puente de dispositivo (requiere que la app de escritorio esté abierta). Carpeta: C:\Users\jesus.almagner\OneDrive - Turia\VSM.
- Directorio de equipo actualizado, ver directorio-equipo-vsm.
- Hoja maestra en Smartsheet: "Inventario Maestro de Procesos", workspace "VSM - Planeación Financiera", sheet_id 2701948162625412.

## Pasos

### 1. Contexto

Leer memory.md de 10_projects/vsm-planeacion-financiera/ para el estado vigente (no es fuente de verdad operativa, solo contexto).

### 2. Conectar y listar

Conectar al dispositivo del usuario (device_list_dir / device_request_folder_access si hace falta) y listar la carpeta VSM. Si no hay conexión al escritorio, avisar y no tocar Smartsheet.

### 3. Leer archivos individuales

Para cada archivo "Inventario_Procesos_VSM - *.xlsx": stagear y leer con Python/openpyxl, hoja "Inventario". Ignorar la fila de ejemplo si existe, ID "EJ-01" o "EJEMPLO" en Comentarios. Ojo: no todos los archivos usan la misma plantilla exacta, verificar en cada uno si la primera fila de datos es un ejemplo antes de asumirlo.

### 4. Calcular IDs vigentes

Por archivo, calcular CURRENT_IDS = valores "PF-###" que aparecen actualmente en la columna "Proceso maestro asignado" (procesos vigentes de esa persona).

### 5. Detectar procesos nuevos

Filas con "Proceso o actividad" pero sin "Proceso maestro asignado" = procesos nuevos a cargar.

### 6. Mapear y cargar procesos nuevos

Leer Smartsheet completo, determinar el siguiente consecutivo PF-### disponible. Cargar (add_rows) mapeando:

- ID Proceso: siguiente PF-###.
- Nombre del Proceso: texto EXACTO del Excel, "Proceso o actividad". El match posterior para escribir el ID de vuelta se hace por nombre exacto, no modificar aunque sea corto o genérico.
- Área/Subárea: inferir entre Planeación Financiera, Presupuesto, Costos, Tesorería, Contabilidad, Control de Gestión. Si no es claro, usar "Planeación Financiera" y anotar "REVISAR" en Observaciones.
- Tipo de Proceso: inferir entre Estratégico, Operativo, Soporte, Control, default "Operativo". "Estratégico" cuando el output va directo a CEO/CFO/Junta Directiva o es anual/board-facing. "Soporte" cuando la persona es colaboradora de un proyecto liderado por alguien más.
- Frecuencia: mapear a Diaria, Semanal, Quincenal, Mensual, Trimestral, Anual, A Demanda / Eventual. Si el valor original no encaja en ninguna, dejar en blanco y anotar REVISAR con el valor original.
- Responsable del Proceso: usar directorio-equipo-vsm si el nombre/apodo del archivo coincide. Si es persona nueva, preguntar al usuario nombre completo y correo, no inventar ni asumir dominio de correo de otras personas, y agregarla al directorio una vez confirmada.
- Estatus VSM: "Por mapear".
- Prioridad de Mejora: dejar en blanco siempre, se llena en bloque al final, ver Things to Know.
- Observaciones: resumen de Descripción breve + Disparador + Sistemas + Output + Tiempo + Comentarios/Backup relevantes + notas REVISAR.

Si hay más de 15 procesos nuevos en una sola corrida: pausar, mostrar la lista completa al usuario (tabla por archivo) y pedir confirmación antes de cargar masivamente.

### 7. Detectar borrados

Para cada persona/archivo leído con éxito, buscar filas de Smartsheet que le pertenezcan (por correo o por nombre en Observaciones "Responsable: Nombre"). Cualquier ID de Smartsheet que ya no esté en CURRENT_IDS de esa persona fue borrado del Excel, eliminar de Smartsheet con delete_rows. Ser conservador con el match, ante duda no borrar.

### 8. Escribir de vuelta

Escribir el ID asignado en el Excel (columna "Proceso maestro asignado" = PF-###, "Estatus de mapeo" = "Inventariado en Smartsheet"), por coincidencia exacta del texto de "Proceso o actividad". Verificar después de guardar que no quedó ninguna fila nueva sin ID por mismatch de texto, corregir y re-guardar si falta alguna. Guardar y subir de vuelta a la misma ruta (SendUserFile + device_commit_files).

### 9. Resumen

Dar resumen al usuario: procesos nuevos agregados, procesos eliminados, archivos sin cambios, archivos no leídos, cualquier "REVISAR".

## Things to Know

- Prioridad de Mejora se llena al final, en bloque, cuando estén todos los archivos, no incremental.
- Borrados en Excel → borrado automático e incondicional en Smartsheet (irreversible, aceptado explícitamente por el usuario).
- Automatización 100% en la nube no es viable, no hay acceso a carpetas locales desde un cron remoto, esa vía quedó desactivada. Alternativa compartida al usuario: tarea LOCAL en la app de escritorio (Routines → Local). Hasta confirmar que quedó configurada, el modo vigente es "a demanda".
- Con más de 15 procesos nuevos: mostrar lista y esperar confirmación antes de cargar, no solo reportar sin cargar.

## History Log

- 2026-08-18: primera carga inicial, se eliminaron 7 filas mockup (PF-001 a PF-007) y se cargaron PF-008 y PF-009 desde el archivo de Daniel Agudelo.
- 2026-08-18 (corrida posterior): sin cambios, todo sincronizado.
- 2026-08-18 (corrida a demanda): 21 procesos nuevos, 7 de Daniel Agudelo y 14 de David Berrio Zapata. Se confirmó identidad de David Berrio Zapata. Usuario aprobó cargar los 21 de una vez. PF-010 a PF-030 cargados, IDs escritos de vuelta en ambos Excel. Sin borrados.
- 2026-08-19 (corrida a demanda): 3 archivos nuevos vacíos aparecidos (Felipe, Lao, Mauricio), sin procesos, sin cambios en Smartsheet.
- 2026-08-19 (corrida posterior): archivo "Lao" con 9 procesos capturados. Identidad confirmada: Laura Cristina Castro Salazar. PF-031 a PF-039 cargados. Sin borrados. Felipe.xlsx y Mauricio.xlsx seguían vacíos.
- 2026-08-19 (corrida posterior, tarde): archivo nuevo vacío "Benjamin.xlsx" aparecido. Daniel Agudelo agregó 1 proceso nuevo (Refacturación equipos IT y Líneas de Google). Archivo "Felipe" con 7 procesos. Identidad confirmada: Felipe Castrillón Cuartas. PF-040 a PF-047 cargados. Sin borrados. Se detectó que Smartsheet ya tiene la opción "A Demanda / Eventual" en el picklist de Frecuencia, agregada externamente, usarla desde entonces.
- 2026-08-21 (corrida a demanda): archivo "Benjamin" con 9 procesos. Identidad confirmada: Benjamin Carrillo, dominio de correo distinto. PF-048 a PF-056 cargados. Daniel Agudelo y Felipe sin cambios. Mauricio.xlsx seguía vacío.
