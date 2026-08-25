# VSM Planeación Financiera — Estado

Estado operativo actual del proyecto VSM Planeación Financiera Optimus Steel. El histórico vive en archive.md de esta carpeta, aquí solo lo necesario para operar hoy.

Last updated: 2026-08-25 (migración inicial desde el Project de claude.ai, sin cambios operativos nuevos)

## State

- Inventario maestro en Smartsheet ("Inventario Maestro de Procesos", workspace "VSM - Planeación Financiera", sheet_id 2701948162625412): 56 procesos cargados (PF-008 a PF-056), todos con estatus "Por mapear".
- Personas con archivo individual confirmado y sincronizado hasta la fecha: Daniel Agudelo, David Berrio Zapata, Laura Cristina Castro Salazar, Felipe Castrillón Cuartas, Benjamin Carrillo. Directorio completo, correos y nombres de archivo en 02_wiki/vsm-planeacion-financiera/directorio-equipo-vsm.md.
- Archivo de Mauricio Mojica existe en la carpeta compartida pero seguía vacío, sin procesos capturados, al 21-ago-2026.
- Mecanismo de sincronización a demanda operando desde el 18-ago-2026: cada corrida detecta procesos nuevos y borrados en los Excel individuales, actualiza Smartsheet y escribe de vuelta el ID PF-### asignado en el archivo de cada persona. Ninguna corrida ha detectado borrados hasta la fecha.
- Único proceso mapeado con detalle completo (disparador, pasos, sistemas, tiempos, desperdicios) hasta ahora: Interfaces y Revisión de Costos/Gastos G&A, ambos de Daniel Agudelo, entrevista del 18-ago-2026.
- Campo "Prioridad de Mejora" se deja en blanco en todas las corridas, se llenará en bloque cuando estén todos los archivos completos.

## Open threads

- Agendar y ejecutar entrevistas de mapeo detallado con Daniela Benjumea, Diana Muñeton y Jesús Almaguer para los procesos de prioridad "Alta" identificados en la reunión del 13-ago.
- Confirmar si Mauricio Mojica ya capturó procesos en su archivo.
- Definir responsables de backup para Interfaces y Revisión SG&A, ninguno de los dos cuenta con uno documentado hoy.
- Validar si los 16 procesos de la reunión del 13-ago corresponden a los puntos 2.1.2, 2.1.3 y 2.1.9 de un documento de referencia externo del usuario, no disponible en este repo.
- Detallar el proceso "manejo de órdenes internas", responsable y pasos aún sin definir.
- Confirmar si el usuario logró configurar la tarea local de actualización automática del inventario en su equipo, la vía 100% en la nube quedó descartada por falta de acceso a carpetas locales.
- Iniciar la priorización y el mapeo VSM detallado, proceso por proceso, de los 56 ya cargados en Smartsheet.
- Llenar en bloque el campo "Prioridad de Mejora" una vez que los archivos restantes, Mauricio y posibles personas nuevas, estén completos.

## References

- Procedimiento operativo y reglas completas del proyecto: ver "Referencias" en CLAUDE.md de esta carpeta.
- Docs originales del Project de claude.ai (inventario borrador, entrevistas, resúmenes semanales), contenido ya distribuido entre este archivo, la wiki, el skill de actualización y 01_raw/_processed/, no se duplica aquí.
