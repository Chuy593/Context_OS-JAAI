# Hábitos y Salud — State

> Estado operativo actual del proyecto de salud, bienestar y hábitos de Jesús (Chuy). El histórico completo de mediciones vive en `biometrics-log.csv` de esta carpeta — aquí solo el resumen para operar hoy.

**Last updated:** 2026-08-25 (migración desde el Project "Salud, Bienestar y Hábitos" de claude.ai; última medición registrada: 2026-08-19)

## Última medición (2026-08-19, 09:10h)

| Métrica | Valor |
|---|---|
| Peso | 99.95 kg |
| BMI | 34.6 |
| Grasa corporal | 33.3% (33.3 kg) |
| Masa muscular esquelética | 34.3% |
| Cintura / Cadera / Pecho | 109 / 114.5 / 107 cm |
| Presión arterial | 117/78 mmHg |
| Frecuencia cardiaca | 64 bpm |
| Horas de sueño (reportadas) | 7 h |
| Metabolismo basal | 1,939 kcal/día |

## Tendencia

- Peso: pico en 2026-02-16 (102.15 kg) → 99.95 kg al 2026-08-19 (-2.2 kg desde el pico, prácticamente en línea con el punto de partida de 2025-11-25, 99.5 kg).
- % de grasa corporal se mantiene en rango 33–34% desde noviembre 2025, sin cambio estructural claro — la pérdida de peso reciente aún no se refleja en composición corporal.
- Presión arterial y frecuencia cardiaca dentro de rango normal en la última medición (117/78, 64 bpm), con variabilidad entre tomas.
- `biometrics-log.csv` solo trae composición corporal y signos vitales (báscula + presión arterial); todavía no hay serie longitudinal de glucosa, HbA1c, perfil lipídico ni hormonal — se agregan aquí en cuanto haya un panel de laboratorio.

## Goals

*(heredados del objetivo general del proyecto — ver el skill para el detalle de cómo se abordan)*

1. Reducir grasa corporal preservando masa muscular.
2. Mejorar sensibilidad a la insulina, disminuir inflamación y mejorar colesterol/triglicéridos.
3. Aumentar testosterona de forma natural, mejorar energía diaria, optimizar sueño y disminuir estrés.
4. Mejorar rendimiento cognitivo, prevenir enfermedad cardiovascular y aumentar healthspan.

## Open threads

- [ ] Definir plan concreto de alimentación + actividad física (heredado del next step registrado en el `memory.md` raíz).
- [ ] Registrar panel de laboratorios (glucosa, HbA1c, perfil lipídico, perfil hormonal, función hepática/renal) — aún no hay serie en `biometrics-log.csv`.
- [ ] Agregar cada nueva medición a `biometrics-log.csv` y actualizar esta tabla y la sección de tendencia.

## References

- Metodología y formato de análisis: ver "Referencias" en [CLAUDE.md](CLAUDE.md) de este proyecto.
- Histórico completo de mediciones: [biometrics-log.csv](biometrics-log.csv)
- La hoja `metabolic data.xlsx` vivía como file upload en el Project de claude.ai; `biometrics-log.csv` es la versión consolidada y editable en texto plano.
