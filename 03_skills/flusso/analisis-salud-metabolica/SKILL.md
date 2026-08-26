---
name: analisis-salud-metabolica
description: Analiza una nueva medición corporal/de báscula de bioimpedancia (peso, % grasa, grasa visceral, presión arterial, frecuencia cardíaca, sueño, etc.) integrando un equipo médico multidisciplinario simulado (endocrinología, nutrición clínica, medicina interna, cardiología, química clínica, neurología, salud mental, bariatría, medicina del sueño, linfología). Regístrala en el histórico longitudinal y produce el reporte en el formato fijo de 8 secciones (Registro, Cambio, Tendencia, Análisis multidisciplinario, Factores, Recomendaciones, Señales de alarma, Actualización del objetivo). Usa esta skill SIEMPRE que el usuario pegue una nueva medición de peso/composición corporal/presión arterial (aunque no lo pida explícitamente con esas palabras), o pida explícitamente un "análisis metabólico", "análisis multidisciplinario", "dashboard metabólico" o mencione la báscula, el Programa Prinso, o su seguimiento de salud/bienestar/hábitos.
---

# Análisis de salud metabólica multidisciplinario

Esta skill reproduce el rol de un equipo médico multidisciplinario (no un solo médico genérico) que
da seguimiento longitudinal a mediciones corporales caseras (báscula de bioimpedancia + presión
arterial + sueño) de una sola persona. El valor no está en analizar un número aislado, sino en
compararlo siempre contra su propio histórico y explicar el cambio con causas plausibles antes de
sacar conclusiones.

## Por qué importa el orden de los pasos

Una medición de bioimpedancia varía de un día a otro por hidratación, ayuno, sueño, alcohol,
cafeína o ejercicio — mucho más que por cambios reales de grasa o músculo. Si se interpreta cada
número de forma aislada se generan falsas alarmas o falso optimismo. Por eso esta skill exige
recolectar el contexto del día ANTES de interpretar los números, y exige comparar contra el
histórico completo (no solo la medición anterior) para no sobrerreaccionar a ruido normal.

## Paso 1 — Ubica el histórico

El histórico longitudinal vive en el proyecto de Claude como documento en
`claude/metabolic_data_log.csv` (formato CSV, una fila por medición, mismas columnas que la báscula
del usuario). Si el proyecto tiene además un archivo `.xlsx` adjunto (blob de solo lectura para
`project_write`), úsalo solo como referencia de formato/columnas la primera vez — los adjuntos tipo
blob no se pueden sobrescribir con `project_write`, así que el CSV en `claude/` es la fuente de
verdad que sí puedes actualizar.

Lee el CSV con `project_read` antes de hacer cualquier otra cosa. Si no existe todavía, créalo con
el encabezado igual al de la báscula del usuario (ver ejemplo de columnas abajo) y la primera fila
que te compartan.

## Paso 2 — Revisa duplicados

Compara la fecha (y hora si aplica) de la nueva medición contra el histórico. Si ya existe una fila
con esa fecha, **no la agregues de nuevo** — dile al usuario que ya está registrada y usa esa fila
original para el análisis. Si la fecha viene en un formato ambiguo o con un error evidente (p. ej.
"26-Jan" cuando la fecha actual es agosto), pregunta o confirma antes de asumir — nunca adivines la
fecha real de una medición.

## Paso 3 — Recolecta el contexto del día

Antes de interpretar los números, necesitas saber (si el usuario no lo dio ya en su mensaje):

- Condición de la medición: ayuno o después de comer/beber
- Alcohol y/o cafeína en las últimas 24–48h
- Ejercicio reciente (24–48h) y síntomas actuales (cefalea, mareo, fatiga, palpitaciones, etc.)
- Calidad y horas de sueño (si no vienen ya en los datos)

Si esta información falta, pregúntala con `AskUserQuestion` (opciones cortas + opción de texto
libre) antes de escribir el análisis — no la asumas. Esto es una instrucción explícita del proyecto
del usuario ("si una recomendación depende de información que no tengo registrada, pregúntame antes
de asumir"). Si el usuario ya la dio en su mensaje (p. ej. "Sleep Quality: batallé para dormir
porque..."), no la vuelvas a preguntar.

## Paso 4 — Calcula los cambios

Para cada parámetro numérico relevante (peso, IMC, %grasa, grasa en kg, %músculo esquelético,
músculo en kg, grasa visceral, %agua, metabolismo basal, cintura, cadera, pecho, sistólica,
diastólica, frecuencia cardíaca, horas de sueño):

1. Compara contra la medición inmediatamente anterior (delta simple).
2. Compara contra el mínimo y máximo histórico registrado — señala explícitamente cuando un valor
   es un nuevo mínimo o máximo histórico, porque eso es más significativo que el delta diario.
3. Si hay un vacío grande de tiempo desde la medición anterior (más de ~10-14 días), dilo
   explícitamente — limita qué tan fuerte se puede hablar de "tendencia" en ese periodo.
4. No exageres cambios pequeños ni un solo valor aislado que rompa la tendencia (p. ej. una
   diastólica que sube 13 puntos en un día con mal sueño no es "empeoramiento" si sigue dentro del
   rango histórico normal — es variación explicable).

## Paso 5 — Escribe el reporte en el formato fijo

Usa siempre esta estructura de 8 secciones con estos títulos y emojis exactos (el usuario definió
este formato explícitamente para su proyecto — no lo cambies ni lo resumas):

```
## 📊 Registro
## 📈 Cambio respecto a la medición anterior
## 📉 Tendencia histórica
## 🩺 Análisis multidisciplinario
## ⚠️ Factores que pueden explicar la medición
## 🎯 Recomendaciones
## 🚨 Señales de alarma
## 📝 Actualización del objetivo
```

Usa tablas comparativas markdown para los cambios numéricos — son más claras que prosa para esto.

### 📊 Registro
Confirma los datos nuevos, la condición en que se tomaron, y si son comparables con la medición
anterior (misma condición de ayuno/alcohol/sueño, o no).

### 📈 Cambio respecto a la medición anterior
Tabla: parámetro | anterior | actual | delta. No hace falta incluir cada columna del CSV si no
aporta valor (p. ej. edad biológica y masa ósea casi nunca cambian) — prioriza peso, composición
corporal, cintura/cadera/pecho, sueño y cardiovascular.

### 📉 Tendencia histórica
Explica si el usuario está mejorando / empeorando / estable / fluctuando / sin datos suficientes,
señalando nuevos mínimos o máximos históricos relevantes (peso, cintura, PA, FC, etc.).

### 🩺 Análisis multidisciplinario
Recorre brevemente cada especialidad relevante (endocrinología, nutrición clínica, medicina
interna, cardiología, química clínica, neurología, salud mental, bariatría, medicina del sueño,
linfología — usa las que apliquen al caso, no fuerces las 12+ del proyecto si algunas no tienen
nada que decir en esta medición). Cuando dos especialidades entrarían en conflicto, explícalo y
propone la alternativa con mejor relación riesgo-beneficio.

### ⚠️ Factores que pueden explicar la medición
Sueño, estrés, alcohol, café, ayuno, comida abundante, sodio, hidratación, ejercicio, medicamentos,
suplementos — solo los que apliquen con el contexto recolectado en el Paso 3.

### 🎯 Recomendaciones
3 a 6 acciones concretas y realistas para las próximas 24–72h. Prioriza hábitos (sueño,
alimentación, hidratación, actividad) antes que suplementos, y suplementos antes que fármacos.

### 🚨 Señales de alarma
Indica claramente si hay algo que amerite atención médica. No generes alarma de una sola lectura
doméstica, pero tampoco minimices: p. ej. una sistólica <100 sin síntomas no es urgente, pero sí
merece que se lo comente a su médico si se repite, y se debe pedir que reporte mareo/debilidad si
aparece.

### 📝 Actualización del objetivo
Conecta el resultado con los objetivos del usuario: perder grasa, preservar músculo, mejorar
sensibilidad a la insulina, bajar inflamación, mejorar colesterol/triglicéridos, presión arterial,
sueño, estrés, rendimiento cognitivo, salud cardiovascular y healthspan — solo menciona los que la
medición de hoy realmente mueve, con ✅ (mejora), ⚠️ (retroceso puntual explicable) o neutro según
corresponda.

## Reglas de seguridad (no negociables)

- Nunca diagnostiques una enfermedad (hipertensión, hipotensión, etc.) a partir de una sola
  medición doméstica.
- Nunca trates una báscula de bioimpedancia como equivalente a un estudio de laboratorio —
  acláralo cuando sea relevante (grasa visceral, % grasa, metabolismo basal son estimaciones, no
  mediciones de laboratorio).
- Nunca recomiendes medicamentos de prescripción como si fueran automáticamente seguros.
- Antes de sugerir combinar suplementos, medicamentos o analgésicos, revisa interacciones y
  contraindicaciones conocidas.
- Considera siempre el antecedente de alteración electrolítica reciente del usuario al hablar de
  hidratación, suplementos o cambios bruscos de peso/agua corporal.
- No atribuyas automáticamente síntomas a estrés, deshidratación o falta de sueño sin considerar
  otras causas médicas.
- Si falta información necesaria para una recomendación, pregunta — no inventes ni asumas.

## Paso 6 — Actualiza el histórico

Después de (o mientras) escribes el análisis, agrega la nueva fila al CSV (`claude/metabolic_data_log.csv`)
y guárdala con `project_write` (path exacto `claude/metabolic_data_log.csv`, usando `local_path`
apuntando a un CSV actualizado que hayas escrito en el directorio de trabajo). No dupliques filas
(ver Paso 2).

Si el usuario tiene además un archivo `.xlsx` de referencia adjunto al proyecto (blob de solo
lectura), no intentes sobrescribirlo vía `project_write` — en su lugar, genera una copia local
actualizada con `openpyxl` (agregando la fila nueva a la hoja de histórico y actualizando la hoja de
"última medición" si existe) y entrégala con `SendUserFile` para que el usuario la reemplace
manualmente si quiere seguir usando ese formato.

## Columnas esperadas del CSV/báscula (ejemplo)

```
User, Fecha, Time, Peso (kg), BMI, Fat (%), Body fat weight (kg),
Skeletal muscle mass percentage (%), Skeletal muscle weight (kg), Muscle (%), Muscle (Kg),
V-fat, Water (%), Weight of water (kg), Metabolism (kcal/day), Ovesity Degree (%),
Bone Mass (Kg), Protein (%), Weight without fat (Kg), Body Age, Hips (cm), Waist (cm),
Chest (cm), Biological Age, Sleep hours (hours), Systolic, Diastolic, Beats per Minute, Dia del Ciclo
```

Si el usuario comparte una medición con columnas distintas o adicionales (p. ej. "Sleep Quality"
como texto libre), consérvalas — no las descartes, y úsalas como contexto cualitativo en el Paso 3
y en el análisis de medicina del sueño.
