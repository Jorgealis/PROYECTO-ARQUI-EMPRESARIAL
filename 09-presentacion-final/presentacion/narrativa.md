# Narrativa de la presentación — Biblioteca Municipal "Rubiel Valencia Cossio"

**Equipo:** ARQUITECH · **Estado:** Punto 1 aprobado (30/10/2026)
**Formato:** 4 actos + cierre, 10 minutos. Lenguaje de negocio; el detalle técnico queda como apoyo.

## Acto 1. Problema (2 min)
> "La Biblioteca de Cogua tiene entre 7.000 y 8.000 libros, pero hoy solo unos 1.100 a 1.200 están en Koha, el sistema que ve el público. Al empezar el semestre eran 600 o 700. Los estudiantes de servicio social ayudan mucho, pero no alcanza: la bibliotecaria, además de atender la biblioteca, debe digitar libro por libro, y su condición de salud le impide hacer tareas repetitivas por periodos largos. La meta es llegar a unos 3.000 libros en noviembre."

**Urgencia (cuenta de ritmo, a confirmar con la cliente):** el conteo empezó a mediados de agosto; en ~2,5 meses se pasó de 600-700 a 1.100-1.200 (≈ 200 libros/mes). Para llegar a 3.000 en noviembre faltan ≈ 1.850, es decir, cerca de 9 veces el ritmo actual.

**Fuentes:** Ficha de Caracterización (Taller 0), BPMN (Taller 1), datos actualizados aportados por el equipo (oct. 2026). Nota: los Talleres 6, 7 y 8 citan "más de 8.000" y "cerca del 10 %"; se usan las cifras actualizadas.

## Acto 2. Análisis (2 min)
> "Al revisar cómo funciona hoy, vimos que la plataforma para consultar el catálogo ya existe; lo que falta es contenido. El cuello de botella es la carga manual. Además encontramos un riesgo: las cuentas de Koha se comparten con los estudiantes, con permisos de edición y acceso a datos de menores, y nadie puede saber quién hizo qué."

**Hallazgo principal:** el catálogo existe, falta cargarlo (Talleres 3, 4 y 6). **Hallazgo secundario:** cuentas compartidas con acceso a datos de menores (Talleres 5 y 6).

## Acto 3. Solución (2 min)
> "Proponemos repartir el trabajo con cuentas individuales para los estudiantes y permisos solo de catalogación. Así avanza el catálogo y se protegen los datos de los menores. Como ayudas rápidas, un lector de códigos de barras y copias de seguridad de los archivos. Más adelante, una app propia para cargar libros por lotes. Esa fase necesita una vía autorizada para escribir en Koha: lo preferible es una credencial de servicio con permiso mínimo sobre la API de Koha, que Biteca debe habilitar; si no, que IDECUT autorice usar las cookies de sesión de la plataforma."

**Fuente:** Taller 7 (matriz ponderada: distribuida 4,20; asistida 3,45; lotes 3,25). Taller 8 (tablero integrado, carpeta `08-integracion-vistas` del proyecto): confirma las cifras de la matriz y la Fase 2 condicionada, y propone una credencial de servicio con permiso mínimo para la app.
**Pesos:** validados por la bibliotecaria el 05/11/2026 sin cambios (Taller 7).
**Pendiente:** autorización de Biteca/IDECUT para conectar la app al Koha real.

## Acto 4. Plan de implementación (2 min) — provisional hasta el Punto 4
> "Primero lo que se puede hacer ya y a bajo costo (respaldo y lector de códigos). Después, la catalogación distribuida con los estudiantes. Al final, la app de lotes, cuando haya autorización."

## Cierre (2 min)
Resumen en una frase y paso a preguntas del panel.

## Notas para otros puntos
- Punto 3 (matriz de riesgos): incluir el riesgo de usar cookies de sesión en una app propia (equivale a actuar con la identidad de un usuario; Taller 5, suplantación) y la dependencia de autorización de Biteca/IDECUT.

## Evidencia clave por acto (Punto 2 aprobado, 30/10/2026)

| Acto | Elemento elegido | Origen | Qué resaltar |
|---|---|---|---|
| 1. Problema | Proceso de catalogación (BPMN) | Taller 1 · `01-bpmn/BPMN.drawio.svg` | El paso manual de buscar, digitar, corregir campos y guardar, hecho por una sola persona |
| 2. Análisis | C2 de contenedores | Taller 3 · `03-arquitectura-c4/c2-contenedores-final.drawio` | OPAC y app Nextbit ya existen (el canal está; falta contenido), el Excel con la colección no catalogada y la "cuenta compartida" del personal |
| 3. Solución | Proceso TO-BE de catalogación | Taller 7 · `07-opportunities-solutions/mejora-arquitectura.md` (sección 3.1) | Estudiantes con cuenta individual catalogan; la bibliotecaria revisa una muestra |
| 4. Plan | Roadmap por fases | Punto 4 de este taller | Por definir |

**Decisión (06/11):** en la presentación se usará un recorte del hilo «Catalogar» del tablero del Taller 8 como evidencia del Acto 3; el proceso TO-BE del Taller 7 queda como respaldo.
**Nota de diseño:** el C2 es denso; en la diapositiva conviene mostrar un recorte o resaltar solo los elementos del Acto 2.

## Estructura final: 5 diapositivas (actualizada 31/10/2026)
Por indicación del profesor en la sesión del 31/10, la presentación se organiza en 5 láminas, una por tema. Los 4 actos de arriba siguen siendo la base del contenido. La matriz de riesgos completa va como lámina de anexo para preguntas, fuera de las 5.

| # | Diapositiva | Tiempo | Presenta | Contenido |
|---|---|---|---|---|
| 1 | Conocer la organización | 1,5 min | Jorge Alarcón | La biblioteca, su equipo (una empleada y estudiantes de servicio social) y su colección de 7.000 a 8.000 libros |
| 2 | El problema (AS-IS) | 2 min | Jorge Alarcón | BPMN actual con el paso manual resaltado; ~200 libros al mes frente a ~1.850 faltantes (~9 meses); una sola persona con limitación de salud |
| 3 | La propuesta (TO-BE) | 2,5 min | Julián Aguirre | Proceso TO-BE: catalogación distribuida con cuentas individuales, lector de ISBN, respaldo 3-2-1 y la app de catalogación |
| 4 | Normativa | 1,5 min | Brayan Presiga | Ley 1581 y datos de menores (R5), cuentas compartidas (R4), terceros (R11, R12) y cookies de sesión (R10) |
| 5 | Plan de implementación | 2,5 min | Brayan Presiga | Roadmap con fechas y cortes de etapa (`entrega/roadmap-implementacion.svg`) |
| + | Demo del prototipo (si sobra tiempo) | ~1 min | Brayan Presiga | Recorrido corto por la app contra el Koha de pruebas |

**Tiempo total:** 10 min, más la demo si hay tiempo. **Estilo:** sobrio e institucional, sin los colores de la Universidad.
