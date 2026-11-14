# Procedimiento de Actualización y Revisión de la Arquitectura

## Cliente
Biblioteca Pública Municipal de Cogua "Rubiel Valencia Cossio". Bibliotecaria: Ana Cecilia Pastrana Rodríguez.

## Integrantes del equipo (ARQUITECH)
- Jorge Alarcón
- Julián Aguirre
- Brayan Presiga

## Propósito de este documento

A diferencia del Plan de Implementación (que ejecuta un cambio ya decidido) y del Plan de Gobernanza (que supervisa esa ejecución), este documento cubre qué pasa **después**: cómo se mantiene la arquitectura actualizada cuando surge una necesidad de cambio nueva, una vez terminado el roadmap del curso.

## Disparadores de cambio

Cuando ocurre alguno de estos eventos, el comité de gobierno revisa la solución en la reunión semanal siguiente, sin esperar la revisión periódica.

| Disparador | Ejemplo concreto para este cliente |
|---|---|
| Nueva regulación | Un cambio en la Ley 1581 de 2012 o en sus decretos, sobre todo en lo que toca a los datos de menores de edad, que atiende la biblioteca. |
| Cambio de proveedor tecnológico | La biblioteca deja Koha, Biteca deja de alojarlo o IDECUT cambia las condiciones de la Red de Bibliotecas. |
| Incidente de seguridad | Alguien usa la cuenta de otra persona, un estudiante ve datos de usuarios que no debería ver, o se pierden archivos de la biblioteca. |
| Crecimiento inesperado de demanda | Llega una donación grande de libros que cambia el tamaño de la colección y la meta de catalogación. |
| Otro: cambia el número de estudiantes | Llegan más o menos de 2 estudiantes de servicio social. El ritmo de catalogación depende directamente de ellos, así que hay que recalcular la meta mensual. |
| Otro: herramientas por fuera del sistema | Alguien empieza a catalogar en una hoja de cálculo, un formulario o una herramienta con inteligencia artificial en lugar de Koha. Va en contra de P1 (Koha como fuente única del catálogo). |
| Otro: la app queda sin quien la mantenga | La persona que desarrolló la app ya no puede seguir manteniéndola (riesgo R13 de la matriz). |

## Proceso de cambio

No todo cambio necesita el mismo trámite. Documentar todo equivale a no documentar nada, así que se separan dos tipos:

| Tipo de cambio | Ejemplos | Cómo se decide |
|---|---|---|
| **Pequeño** (fácil de deshacer) | Ajustar la guía de catalogación, cambiar el tamaño de la muestra semanal de revisión, mover el día de la reunión. | Se decide en la reunión semanal y queda anotado en el acta. No necesita ADR. |
| **Grande** (difícil o costoso de deshacer) | Cambiar de sistema de catálogo, dar más permisos a los estudiantes, conectar una herramienta nueva a Koha, salirse de un estándar. | Necesita una ADR. Sin ADR no se aprueba. |

Pasos para un cambio grande:

1. **Proponer.** Cualquier integrante del comité (la bibliotecaria o un estudiante) describe el problema en términos de su efecto en la biblioteca, no como una solución ya escogida. Se registra una ADR en estado **Propuesta**.
2. **Evaluar.** En la reunión semanal siguiente, el comité compara al menos dos alternativas contra los principios P1 a P4, los estándares del plan de gobernanza y la meta de libros en Koha.
3. **Decidir.** El comité decide en máximo **5 días hábiles** desde la propuesta, es decir, en una reunión (métrica M3 del plan de gobernanza). La ADR pasa a **Aceptada** y se completa con sus cuatro partes: contexto, alternativas descartadas con su razón, decisión y consecuencias buenas y malas. Si la decisión depende de la Alcaldía o de los proveedores de Koha, se sigue el escalamiento del plan de gobernanza.
4. **Fijar cuándo se revisa.** Toda ADR aceptada lleva la fecha o el evento en que se vuelve a mirar (ver "Revisión periódica completa").

**Reglas de las ADR.** Las ADR se manejan por estados: Propuesta → Aceptada → Reemplazada por ADR-00X. Nunca se borran ni se editan para cambiarles el sentido. Si una decisión se corrige, se escribe una ADR nueva que reemplaza a la anterior; el error también es parte de la historia de la biblioteca.

## Registro de decisiones (ADR)

> **Sobre las fechas.** Las fechas de propuesta y de dictamen se reconstruyeron con el calendario del curso y el historial de los repositorios de los talleres, porque las decisiones se tomaron antes de que existiera este registro. Desde ahora, cada ADR se fecha el mismo día en que se propone y en que se decide.

| Campo | ADR-001 |
|---|---|
| Título | Catalogación distribuida entre estudiantes de servicio social, primero manual y luego con la app de lotes |
| Estado | Aceptada |
| Fecha de propuesta | 10/10/2026 (sesión del Taller 7, Opportunities & Solutions) |
| Fecha de dictamen | 05/11/2026 (la bibliotecaria valida los pesos de la matriz de decisión y se entrega el Taller 7) |
| Fecha de revisión | Cuando la app se conecte a Koha (marzo de 2027) y el 31/05/2027 |
| Contexto | La colección tiene de 7.000 a 8.000 libros y en Koha hay de 1.100 a 1.200. Al ritmo actual (~200 libros al mes) faltan unos 9 meses para la meta de ~3.000 de noviembre. El proceso depende de una bibliotecaria con limitación de salud, apoyada por estudiantes de servicio social que dedican en promedio 5 horas semanales y catalogan de 4 a 7 libros por hora. |
| Problema | ¿Qué modelo de catalogación aumenta el ritmo sin cargar más a la bibliotecaria? |
| Decisión | Se adopta la **catalogación distribuida**: cada estudiante cataloga con su propia cuenta y la bibliotecaria valida. Se implementa en dos momentos: primero de forma manual en Koha y después con la app móvil de catalogación, cuando la integración esté habilitada. La matriz ponderada del Taller 7 le dio 4,20 con pesos 35/25/20/20. |
| Alternativas consideradas | **Catalogación asistida (3,45):** se descartó porque mantiene a la bibliotecaria en el centro del proceso y no reduce su carga en la misma medida. **Catalogación por lotes como modelo único (3,25):** se descartó como modelo principal porque depende de una integración que hoy no está habilitada. Se conserva como herramienta de la segunda etapa. |
| Consecuencias | (+) El ritmo crece con el número de estudiantes y no con las horas de la bibliotecaria, que pasa a validar y supervisar. La fase manual empieza de inmediato, sin esperar la app. (−) Con varias personas catalogando, la calidad de los registros es menos uniforme, lo que exige capacitación y revisión. La etapa con la app sigue condicionada. **Trade-off aceptado:** se sacrifica la uniformidad de un solo catalogador a cambio de velocidad. **Nota:** la bibliotecaria validó los pesos el 05/11/2026 sin cambios; a petición suya, el criterio de carga se renombró "Eficiencia del proceso de catalogación" (Taller 7, matriz de decisión). Análisis de sensibilidad: si el peso de ese criterio superara el 66,7 %, la opción por lotes superaría a la asistida, pero la distribuida seguiría primera. |

| Campo | ADR-002 |
|---|---|
| Título | Cuentas personales en Koha con perfil de acceso mínimo |
| Estado | Aceptada |
| Fecha de propuesta | 31/10/2026 (sesión del Taller 9, al construir la matriz de riesgos) |
| Fecha de dictamen | 07/11/2026 (cierre del Corte 3 y ensayo, al aprobar la matriz) |
| Fecha de revisión | 31/01/2027 (cierre de la etapa de cuentas) y en cada revisión semestral |
| Contexto | Hoy las personas que trabajan en Koha comparten cuentas. La matriz de riesgos lo registró como R4, con nivel 9, uno de los dos más altos. La ADR-001 suma más personas catalogando, así que el problema crece. |
| Problema | ¿Cómo dar acceso a Koha a varios estudiantes manteniendo trazabilidad y protegiendo los datos de los usuarios? |
| Decisión | Cada persona tiene una **cuenta personal** con un **perfil de catalogador** sin acceso a circulación ni a datos de usuarios. La cuenta se desactiva al terminar el servicio social. Con esto R4 se **elimina**. |
| Alternativas consideradas | **Mantener la cuenta compartida:** se descartó porque no permite saber quién modificó cada registro y expone los datos de los usuarios, incluidos menores (Ley 1581). **Una cuenta por turno o por grupo:** se descartó porque reduce el riesgo pero no lo elimina, ya que dentro del grupo tampoco se sabe quién hizo cada cambio. |
| Consecuencias | (+) Cada registro queda a nombre de quien lo creó, lo que permite revisar la calidad por persona (apoya la ADR-001). El acceso a datos personales queda limitado. (−) Crear y desactivar cuentas es una tarea nueva de administración. **Trade-off aceptado:** se sacrifica algo de agilidad y se agrega una tarea pequeña a la bibliotecaria (en tensión con P2), porque prevalecen la seguridad y la trazabilidad (P3, P4). Para mitigarlo, se usa un perfil plantilla para crear las cuentas en pocos minutos. |

## Revisión periódica completa

Además de los disparadores, el comité revisa toda la solución **una vez por semestre**, cuando cambia el grupo de estudiantes de servicio social. La primera revisión es en junio de 2027, al terminar el corto plazo del plan de implementación. En esa reunión se hacen tres cosas:

1. **Revisar cada ADR en su fecha de revisión** y decidir si sigue vigente o si hay que reemplazarla:

   | ADR | Cuándo se revisa | Qué se pregunta |
   |---|---|---|
   | ADR-001 · Catalogación distribuida | Cuando la app se conecte a Koha (marzo de 2027) y al 31 de mayo de 2027 | ¿Se alcanzó la meta mensual? ¿La catalogación con la app debe pasar a ser el modelo principal? |
   | ADR-002 · Cuentas personales | Al cierre de la etapa de cuentas (31 de enero de 2027) y en cada revisión semestral | ¿Todas las personas usan su propia cuenta? ¿Se desactivaron las cuentas de los estudiantes que terminaron? |

2. **Actualizar los diagramas que cambian despacio** (el proceso de catalogación y los diagramas de la arquitectura) para que sigan mostrando cómo funciona la biblioteca de verdad. Si nadie los actualiza, con el tiempo dejan de parecerse a la realidad y pierden su utilidad.

3. **Confirmar dónde quedan guardados los documentos.** Las ADR, los diagramas y este procedimiento se guardan en el repositorio compartido del proyecto, junto al código de la app (el mismo que el plan de implementación prevé para el riesgo R13), y no en una carpeta que nadie abre. Así sobreviven a la rotación de los estudiantes y del equipo.

---

_Este documento hace parte de la entrega final del Taller 9 del curso AREM (Arquitectura Empresarial) - Universidad de La Sabana._
