---
name: correo-jesus
description: Redacta un correo en el estilo real de Jesús Almaguer — directo, profesional, sin relleno, con los cierres que usa siempre. Usar para "ayúdame con este correo", "redacta un email para...", "responde este correo", "help me with this email".
---

# Correo — Estilo Jesús

*v1.0*

Atómico: una entrada (contexto/solicitud del correo), una salida (el correo redactado). No decide de qué trata el correo — eso lo trae quien lo llama.

## Idioma

Español o inglés según el idioma del correo original o del hilo al que responde. Nunca mezclar dentro del mismo correo.

## Estructura

1. Saludo breve ("Good afternoon," / "Buenas tardes," / directo al grano si el hilo ya está iniciado).
2. Contexto, solo si hace falta — una o dos líneas, no un preámbulo.
3. Solicitud o respuesta — el cuerpo real del mensaje.
4. Datos importantes (cifras, fechas, adjuntos referenciados) integrados al cuerpo, no como posdata.
5. Cierre.

## Cierres permitidos (no usar otros)

- Español: `Saludos!!`
- Inglés: `Thanks!!` o `Best regards,\nJesus`

## Reglas de tono

- Profesional, natural, directo, cordial. Sin frases de relleno ("espero que este correo te encuentre bien", "sin más por el momento").
- Nunca debe leerse como redactado por IA: frases cortas, concretas, sin adjetivos innecesarios.
- Si hay urgencia, se indica de forma natural dentro del texto, no con mayúsculas ni exceso de signos: "Urge tu apoyo…", "We need this today…".
- Cuando el correo reporta cifras de costo/producción de Optimus Steel (ej. envío de un cost review), seguir el formato numérico y la estructura de `03_skills/flusso/cost-review-mensual/SKILL.md` en el cuerpo, y aplicar este skill solo al saludo/cierre/tono general.

## Ejemplos reales de referencia

Los 4 correos de Executive Summary (`01_raw/_processed/cost-meeting-{jan,feb,mar,may}-2026-email-example.md`, texto extraído de los PDF originales) son la fuente real de estilo: abren con "Good afternoon,", cuerpo técnico denso en bullets, cierran con "Regards, Jesus" o "Jesus Almaguer" + cargo ("Cost & Finance" / "Finance & Cost").

---
*Fuente: Project "Optimus Steel" de claude.ai (sección "Correos"), migrado a Context OS el 2026-08-25. Reutilizable fuera de Optimus Steel — no depende del proyecto.*
