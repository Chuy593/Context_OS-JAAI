# Musica JAAI — Rules

Composicion, arreglos musicales y produccion musical con IA (Suno) usando el JAAI Music Framework: direccion artistica, ingenieria emocional y performance vocal para canciones concretas de Chuy.

Este archivo contiene solo reglas. El estado vive en memory.md de esta carpeta.

## Scope

Entra aqui: canciones y proyectos musicales concretos que Chuy esta componiendo o produciendo (letras, prompts de estilo para Suno, decisiones de produccion de un track especifico, iteraciones de un mismo tema), correos o notas relacionadas a un lanzamiento o EP concreto.

No entra aqui (y va a otro lado): el JAAI Music Framework en si — metodologia, vocabulario de corchetes, voice casting, estructura de prompts, tecnicas de composicion de letras — vive en 02_wiki/musica-jaai/ y este proyecto solo lo referencia.

Test: "¿esto sigue siendo util si cambio de cancion/proyecto musical?" No (es especifico de una cancion o release concreto) → aqui. Si (es una tecnica o definicion reutilizable del framework) → wiki.

## Estructura

memory.md — cancion(es) o proyecto musical en curso: estado, prompts probados, decisiones de estilo/persona, next step.
archive.md — historico de canciones/proyectos ya cerrados (se crea la primera vez que se reemplaza un estado en memory.md).

## Reglas heredadas de la raiz

Propagacion macro: esta conversacion puede escribir directo en el memory.md raiz cuando cambia el status del proyecto o su next step.
Memoria → Archivo: cuando una cancion/proyecto queda cerrado y se reemplaza el estado en memory.md, el estado anterior se mueve primero a archive.md de esta carpeta antes de sobrescribirlo.
Single source of truth: el framework JAAI (estructura de prompts, vocabulario de corchetes, voice identity, tecnicas de composicion) NO se repite aqui — esta en 02_wiki/musica-jaai/. Este archivo solo apunta a el.

## Referencias

Framework completo (principios, fundamentos, performance prompting, Suno advanced workflow, voice identity engineering, composicion de letras, direccion vocal por corchetes) → 02_wiki/musica-jaai/ (ver index_musica-jaai.md).

Migrado desde el Project "Musica JAAI" de claude.ai el 2026-08-25: las instrucciones del proyecto (el framework JAAI) se movieron a 02_wiki/musica-jaai/ como conocimiento reutilizable, y este archivo se quedo solo con el estado/reglas del trabajo de composicion en curso, en vez de vivir todo junto en un solo bloque de instrucciones del Project.
