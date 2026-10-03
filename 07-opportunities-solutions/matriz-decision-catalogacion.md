# Matriz de Decisión Ponderada — Brecha G1: catalogación manual del material en Koha

Una matriz por cada brecha con más de una solución posible. Guía y ejemplo completo: sección 2.1 de la [guía paso a paso](../clase/guia_paso_a_paso_opportunities_solutions.md). Los totales se recalculan con fórmulas en la hoja "Decisión G1" de `matriz-brechas.xlsx`.

---

## Brecha que se decide

**G1 · Catalogación manual título por título, a cargo de una sola persona.** La evidencia está en el BPMN del Taller 1, en el C2 del Taller 3 y en el ítem 15 del checklist del Taller 6 (cerca del 10 % de la colección cargada en Koha).

---

## Paso 1 — Problema en términos de impacto

Cada título que llega exige que una sola persona busque, corrija y valide sus datos a mano. Con más de 8.000 ejemplares por registrar y cerca del 10 % hecho, el catálogo público muestra solo una fracción de la colección, y la carga recae en una persona que no puede sostener tareas repetitivas durante periodos largos.

---

## Paso 2 — Último momento responsable para decidir

| Dato | Valor |
|---|---|
| Fecha en que el problema empieza a doler | Pendiente: el cliente aún no fija la fecha; la meta de la ficha (50 % en Koha en noviembre) no se usa en esta iteración |
| Tiempo que necesita la opción más probable (implementación + pruebas) | Pendiente |
| **Último momento responsable** | Pendiente de calcular cuando se fije la fecha |
| Fecha de hoy y días que quedan | — |

---

## Paso 3 — Criterios, pesos y escala

Los pesos los propuso el equipo con apoyo de IA y **están pendientes de validar con la bibliotecaria**, porque la guía exige que los defina o valide el negocio. En la escala 1-5, 5 es siempre lo más favorable.

| Criterio | Peso (%) | Qué significa 5 | Qué significa 1 |
|---|---|---|---|
| Reducción de la carga de la bibliotecaria | 35 | El trabajo deja de depender de una sola persona o se reduce a revisar excepciones | El esfuerzo por título no cambia |
| Dependencia de terceros | 25 | La biblioteca lo hace sola | Requiere que Biteca o IDECUT habiliten algo sin garantía |
| Costo adicional | 20 | Sin costo adicional (4 = compra única pequeña; 3 = compra mediana u horas de desarrollo; 2 = costo recurrente) | Contratación o costo recurrente alto |
| Calidad de datos y seguridad | 20 | Mejora a la vez la calidad de los datos y la trazabilidad de quién hace qué | Aumenta errores, duplicados o acceso no controlado |
| **Total** | **100** | | |

_Por qué esos pesos:_ la carga pesa más porque es la expectativa central de la ficha ("disminuir la carga de trabajo"). La dependencia pesa 25 % porque Biteca solo pudo responder parte de las preguntas por restricciones contractuales (Taller 4). El costo pesa 20 % por los recursos limitados del cliente. La calidad y seguridad pesan 20 % por las brechas de los Talleres 5 y 6.

_Criterio eliminatorio:_ toda opción con Reducción de carga menor a 3 se descarta.

---

## Paso 4 — Opciones

| Opción | Descripción |
|---|---|
| A · Catalogación asistida | Lector de código de barras / ISBN y formato de catalogación más corto en Koha. La bibliotecaria sigue haciendo todo el proceso del BPMN, pero con menos digitación. |
| B · Catalogación distribuida | Los 2 estudiantes de servicio social ejecutan el carril "Bibliotecaria" del BPMN con cuentas individuales de solo catalogación. La bibliotecaria revisa una muestra. |
| C · Carga por lotes con app propia | Koha no ofrece carga por lotes en esta instalación. Se construiría una app que lee ISBN en bloque, consulta Z39.50/SRU y carga los registros a Koha por su API. Es la opción radicalmente distinta (lote en vez de título por título). |

Las tres no son excluyentes: la matriz decide cuál va primero.

---

## Paso 5 — Consejo consultado

| A quién | Qué aportó | Qué opción afecta |
|---|---|---|
| Equipo (conoce la instancia de Koha de la biblioteca) | Se pueden crear más cuentas en Koha; Koha no ofrece carga por lotes, por lo que habría que construir una app aparte | B y C |
| Bibliotecaria / estudiantes | Hay 2 estudiantes de servicio social; las 15 horas semanales son un supuesto del equipo, por confirmar | B |
| Biteca / IDECUT | **Pendiente:** ¿está habilitada la API REST de Koha y qué versión tiene la instancia? ¿Hay formato de catalogación corto disponible? | A y C |

---

## Paso 6 — Puntajes con justificación

| Opción | Carga (35 %) | Dependencia (25 %) | Costo (20 %) | Calidad y seguridad (20 %) |
|---|---|---|---|---|
| A | **3** — acelera cada título, pero la bibliotecaria sigue haciendo todos | **4** — el lector funciona sin Biteca; solo el formato corto podría requerir permiso | **4** — compra única de un lector (supuesto, por cotizar) | **3** — el ISBN reduce errores de digitación, pero no resuelve las cuentas compartidas |
| B | **4** — reparte el trabajo repetitivo entre 2 estudiantes; queda la revisión por muestreo | **4** — el equipo confirmó que se pueden crear cuentas y quien tenga permiso de administración asigna permisos por módulo [5][6]; falta probar el perfil restringido en su instancia | **5** — el servicio social ya existe, sin costo adicional | **4** — cuentas individuales dan trazabilidad (T5-T3, T6-ítem 9); la calidad depende de estudiantes rotativos |
| C | **5** — pasa de título por título a lote; el estudiante solo atiende excepciones | **2** — requiere API REST de Koha habilitada por Biteca (versión por confirmar) [3][4] y alguien que construya y mantenga la app | **3** — lector más horas de desarrollo y pruebas; sin costo recurrente si corre en el PC (supuesto) | **2** — nueva superficie (credencial de API) y riesgo de duplicados o registros de calidad variable cargados en masa |

**Totales ponderados:**

| Opción | Cálculo | Total |
|---|---|---|
| A | 3×0,35 + 4×0,25 + 4×0,20 + 3×0,20 = 1,05 + 1,00 + 0,80 + 0,60 | **3,45** |
| B | 4×0,35 + 4×0,25 + 5×0,20 + 4×0,20 = 1,40 + 1,00 + 1,00 + 0,80 | **4,20** |
| C | 5×0,35 + 2×0,25 + 3×0,20 + 2×0,20 = 1,75 + 0,50 + 0,60 + 0,40 | **3,25** |

**Sensibilidad:**

| Escenario de pesos (carga / dependencia / costo / calidad) | Total A | Total B | Total C | ¿Gana la misma opción? |
|---|---|---|---|---|
| Pesos base: 35 / 25 / 20 / 20 | 3,45 | 4,20 | 3,25 | B |
| Costo y facilidad: 20 / 30 / 30 / 20 | 3,60 | 4,30 | 2,90 | Sí (B) |
| Carga alta: 50 / 15 / 15 / 20 | 3,30 | 4,15 | 3,65 | Sí (B) |

C solo superaría a B si la reducción de carga pesara más del 66,7 % (repartiendo el resto en partes iguales): en ese punto ambas empatan en 4,11. Entre A (3,45) y C (3,25) hay 0,20 puntos, así que se tratan como empate técnico, y las dos pasan el criterio eliminatorio.

---

## Paso 7 — Decisión

- **Decisión:** implementar la catalogación distribuida (B) como solución principal, con la catalogación asistida (A) como quick win complementario y la carga por lotes (C) como Fase 2.
- **Trade-off aceptado:** se sacrifica el control directo sobre la calidad de la catalogación, que quedará en manos de personas rotativas (se mitiga con guía de una página, revisión por muestreo, inducción y compromiso de confidencialidad), a cambio de repartir la carga y cerrar las brechas de cuentas compartidas y acceso a datos de menores.
- **Alternativas descartadas y su razón:**
  - A como solución única: no redistribuye el trabajo, la bibliotecaria seguiría haciendo todos los títulos. Se conserva como complemento barato.
  - C como primera opción: depende de que Biteca habilite la API de Koha y de construir y mantener una app. Se conserva como Fase 2.

---

## Paso 8 — Reevaluación

- Si Biteca confirma la API REST de Koha, reconsiderar C como siguiente paquete (WP4).
- Después del primer mes con estudiantes, medir los títulos catalogados por semana. Si la capacidad real (horas de los estudiantes por títulos por hora) queda muy por debajo de la esperada, reconsiderar A + C.
- Si el perfil restringido no se puede configurar en la instancia de Cogua, bajar la Dependencia de B a 2 y recalcular.

---

## Registro de uso de IA

La IA propone; el equipo justifica y decide ([guía, sección 2.2](../clase/guia_paso_a_paso_opportunities_solutions.md)).

| Paso | Qué se le pidió a la IA | Qué propuso | Dato verificado o recalculado | Qué cambió el equipo |
|---|---|---|---|---|
| 3 | Pesos y escalas de los criterios | 35 / 25 / 20 / 20, con razón por criterio | Totales y escenarios recalculados con fórmulas en `matriz-brechas.xlsx` | Pendiente: el equipo debe validarlos con la bibliotecaria |
| 4 | Opciones, incluida una radicalmente distinta | A, B y C | Se verificó en la documentación de Koha que existe una ruta de API para crear registros bibliográficos [3][4] | El equipo aportó que Koha no tiene carga por lotes y que C exige una app aparte |
| 6 | Borrador de puntajes con su razón | Puntajes de A, B y C | El equipo confirmó que se pueden crear más cuentas en Koha, y la dependencia de B subió de 3 a 4; C se recalibró | El equipo debe validar cada celda con la escala del Paso 3 |
| 7 | Atacar la decisión | Umbral de sensibilidad | Recalculado: C supera a B solo si la carga pesa más del 66,7 % | — |

- [ ] Puntué por mi cuenta antes de comparar con la IA (evita el anclaje). _Por completar por el equipo._
- [ ] Verifiqué o recalculé toda cifra y afirmación de la IA que entró a la matriz. _Totales y sensibilidad recalculados en la hoja de cálculo; supuestos de costo y horas por confirmar._
- [ ] Los pesos los fijó o validó el negocio, no la IA. _Pendiente de validar con la bibliotecaria._

---

_Esta decisión es el borrador de una ADR: en el Taller 9 se formaliza su registro (Contexto, Problema, Decisión, Alternativas, Consecuencias)._
