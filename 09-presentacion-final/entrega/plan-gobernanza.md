# Plan de Gobernanza de la Implementación

## Cliente
Biblioteca Pública Municipal de Cogua "Rubiel Valencia Cossio". Bibliotecaria: Ana Cecilia Pastrana Rodríguez.

## Integrantes del equipo (ARQUITECH)
- Jorge Alarcón
- Julián Aguirre
- Brayan Presiga

## Propósito de este documento

Este documento define con qué reglas se toman las decisiones sobre la solución de la biblioteca y quién vigila que el plan de implementación se cumpla: los principios, los estándares tecnológicos, el comité de gobierno, cada cuánto se reúne, cuándo se da por terminada una etapa, qué pasa cuando algo se sale de lo planeado y con qué métricas se sabe si todo esto funciona.

El gobierno no es un trámite. Sin reglas comunes, cada decisión aislada, aunque sea razonable por separado, termina desordenando la solución: catálogos en paralelo, cuentas prestadas, herramientas que nadie controla. Las reglas limitan esas variaciones y por eso permiten decidir rápido. El objetivo es que, cuando el equipo ARQUITECH ya no esté, la biblioteca siga tomando decisiones coherentes y sepa por qué se tomaron las anteriores.

## Principios Arquitectónicos

> **Supuesto (por verificar):** se asume que el documento de visión del Taller 0 (`00-preliminary-vision/vision.md` del repositorio del proyecto) no incluyó un borrador de principios. Por eso los cuatro principios siguientes son nuevos y se derivan de la evidencia de los Talleres 1 a 7. No hay principios confirmados, reescritos ni retirados. Si la verificación encuentra un borrador, esta tabla se actualiza marcando cada principio como confirmado, reescrito o retirado.

| Principio | Declaración | Implicación (qué descarta) | Justificación en el proyecto (evidencia de los talleres) | Estado frente al Taller 0 |
|---|---|---|---|---|
| **P1. Koha como fuente única del catálogo** | El registro oficial de cada ejemplar de la colección es el que está en Koha. Ninguna otra herramienta mantiene una versión válida del catálogo. | Las hojas de cálculo, los cuadernos o los formularios solo se usan como apoyo temporal de captura y no reemplazan el registro en Koha. Cualquier herramienta nueva, como la app de catalogación, debe escribir directamente en Koha o terminar en él. Se descarta catalogar en paralelo para "subir después". | El avance hacia la meta de ~3.000 títulos (hoy de 1.100 a 1.200, de una colección de 7.000 a 8.000) solo se puede medir y consultar si todo el catálogo está en un mismo lugar. El proceso AS-IS del Taller 1 mostró que los registros dispersos duplican el trabajo y hacen que el avance no se pueda verificar. | Nuevo |
| **P2. Primero, reducir la carga de la bibliotecaria** | Entre dos opciones que cumplen el objetivo, se elige la que exige menos esfuerzo directo a la bibliotecaria. | Una solución que le sume tareas a Ana Cecilia Pastrana se descarta o se rediseña, aunque sea técnicamente superior. El trabajo operativo se traslada a los estudiantes de servicio social o a herramientas de apoyo, y la bibliotecaria queda en el rol de validación y supervisión. | El proceso depende de una sola persona con limitaciones de salud. La carga de trabajo es su principal molestia y, por eso, el criterio de mayor peso en la matriz de decisión del Taller 7. | Nuevo |
| **P3. Cuenta propia y acceso mínimo** | Cada persona que trabaja en Koha usa una cuenta personal, con los permisos estrictamente necesarios para su tarea. | Se prohíben las cuentas compartidas, incluso para agilizar la incorporación de estudiantes. Los estudiantes de servicio social tienen un perfil de catalogador sin acceso a circulación ni a datos de usuarios, y su cuenta se desactiva al terminar el servicio. | Las cuentas compartidas de Koha (R4) son uno de los dos riesgos de mayor nivel de la matriz (nivel 9). Impiden saber quién modificó cada registro y exponen los datos de los usuarios a personas que no los necesitan. | Nuevo |
| **P4. Protección de datos desde el diseño** | Todo cambio que toque datos personales debe cumplir la Ley 1581 de 2012 antes de ponerse en operación, no después. | No se integra ningún tercero, herramienta ni formulario que no demuestre cifrado y un tratamiento adecuado de los datos. Los datos de menores de edad reciben protección reforzada. Se descartan los formularios con cuentas no institucionales y el uso de cookies de sesión sin autorización formal. | La biblioteca atiende población infantil y juvenil. La matriz de riesgos identificó los datos de menores (R5), las cookies de sesión (R10) y los terceros sin evidencia de cifrado (R12) como riesgos de nivel 6, además de las brechas del Taller 5 (WP5: G4 y G6). | Nuevo |

Principios del borrador del Taller 0 que se retiran, y por qué:

| Principio retirado | Qué evidencia lo contradijo |
|---|---|
| Ninguno | Supuesto: el Taller 0 no incluyó borrador de principios (pendiente de verificar). |

## Estándares Tecnológicos

Cualquier excepción a estos estándares se registra y se aprueba mediante una ADR en `procedimiento-cambios.md`.

| Categoría | Estándar definido | Por qué |
|---|---|---|
| Lenguaje / framework | **Kotlin**, para la app móvil Android de catalogación por lotes. | Es el lenguaje oficial de Android. Permite usar la cámara del teléfono como lector de códigos de barras, así que los estudiantes de servicio social catalogan desde su propio celular sin equipos adicionales. Esto quita carga operativa a la bibliotecaria (P2). |
| Tipo de comunicación | **API REST oficial de Koha**, con autenticación por cuenta personal. El uso de cookies de sesión queda como excepción y solo procede con autorización escrita de IDECUT. | Es la vía soportada por Koha. Cada registro queda en Koha a nombre de quien lo creó (P1, P3). Las cookies de sesión son un riesgo identificado (R10) y no ofrecen garantías de seguridad (P4). |
| Infraestructura | **Koha alojado por Biteca**, y la app y sus datos de apoyo en la **nube institucional**. El prototipo se prueba únicamente contra el Koha de pruebas del repositorio oficial. | La biblioteca no tiene personal técnico para mantener servidores propios (P2). Ningún dato real de usuarios, incluidos menores, entra al entorno de pruebas (P4). |

## Mecanismo de gobierno

El comité de gobierno lo forman **la bibliotecaria y los 2 estudiantes de servicio social**. Revisa el avance del plan de implementación, los errores encontrados en la revisión semanal de la bibliotecaria y las dudas o problemas de la semana. También decide las solicitudes de cambio y las excepciones a los estándares, y las registra como ADR en `procedimiento-cambios.md`.

Lo que no depende de la biblioteca no lo decide el comité: las compras las aprueba la Alcaldía de Cogua y la conexión de la app al Koha real la autorizan los proveedores de Koha (Biteca e IDECUT). En esos casos el comité prepara y envía la solicitud.

## Cadencia de seguimiento

Una **reunión semanal de una hora**, mientras dure el plan de implementación. La hora de reunión es aparte de las 5 horas semanales de catalogación de cada estudiante, para no reducir el ritmo de registro. En cada reunión se revisan las métricas M1 y M2 de este documento.

## Criterio de conformidad

Una etapa del plan de implementación se da por terminada solo si cumple **las dos condiciones**:

1. **El resultado visible se comprobó.** La bibliotecaria (o la Alcaldía, cuando corresponde) comprobó el resultado visible de esa etapa, según la tabla "Resultado visible por fase" del plan de implementación.
2. **Se respetan los principios y los estándares de este documento.** Por ejemplo: ningún libro se catalogó en una hoja de cálculo para "subir después" (P1), nadie usa la cuenta de otra persona (P3), ningún dato real de usuarios entró al entorno de pruebas (P4) y la app se conecta a Koha por la vía autorizada (estándar de comunicación).

Si una etapa rompe un principio o un estándar sin una ADR que lo autorice, no se da por terminada: el comité define en la reunión siguiente qué se corrige.

## Escalamiento

Hay tres casos en los que algo se sale de lo planeado:

| Caso | Quién decide | Cómo |
|---|---|---|
| Hace falta comprar algo (disco, lector, nube) | Alcaldía de Cogua | El comité prepara una solicitud de una página con el costo y el resultado esperado. |
| Hace falta un permiso sobre Koha (credencial para la app, perfil de catalogador) | Proveedores de Koha (Biteca e IDECUT) | El comité envía una solicitud formal. Mientras no haya respuesta, se sigue con el plan B del plan de implementación. |
| Alguien necesita salirse de un estándar o cambiar algo del diseño aprobado | Comité de gobierno | Nadie lo hace por su cuenta. Se propone en la reunión semanal y, si se aprueba, se registra como ADR en `procedimiento-cambios.md`. La ADR es la "puerta" de los estándares: permite excepciones justificadas para que nadie tenga que buscar soluciones a escondidas. |

## Métricas de gobierno

| Métrica | Qué mide (principio) | Fórmula | Fuente que ya existe | Línea base | Umbral |
|---|---|---|---|---|---|
| **M1 · Libros registrados al mes** | Si se cumple **P1** (Koha como fuente única del catálogo): el catálogo oficial crece al ritmo que exige la meta. | Registros bibliográficos nuevos en Koha en el mes. Como dato de apoyo: libros en Koha ÷ libros de la colección × 100. | Conteo de registros de Koha, que saca la bibliotecaria (el perfil de estudiante no tiene acceso a reportes), y el inventario de la colección en Excel. | ~200 libros al mes; ~1.100 a 1.200 libros en Koha de 7.000 a 8.000 (≈ 15 %). | Un mes por debajo de la meta mensual del plan de implementación: el comité revisa la causa en la reunión siguiente. Dos meses seguidos: el comité ajusta la meta o activa el plan B. |
| **M2 · Porcentaje de libros con errores** | Si se cumple **P1** con calidad: el registro oficial sigue siendo confiable ahora que catalogan más personas (la consecuencia negativa aceptada en ADR-001). | Libros con errores o duplicados en la muestra semanal ÷ libros revisados en la muestra × 100. | Revisión semanal de una muestra y el informe de errores y duplicados que ya hace la bibliotecaria. | El informe más reciente señaló unos 80 libros con errores y al menos uno duplicado, pero no registró cuántos libros se revisaron. El porcentaje se calcula por primera vez en la revisión de diciembre de 2026. | Más de 10 % en una semana: el comité refuerza la capacitación del estudiante y la guía de catalogación en la reunión siguiente. |
| **M3 · Tiempo de decisión del comité** (mide al comité) | Si el **gobierno** estorba: el comité decide antes de que la gente resuelva por su cuenta (por ejemplo, prestándose una cuenta). | Días hábiles entre la propuesta de una ADR, solicitud de cambio o excepción y la decisión del comité. | Registro de ADR de `procedimiento-cambios.md` (fechas de propuesta y de dictamen). | Antes de que existiera el comité, ADR-001 tardó casi 4 semanas (10/10/2026 → 05/11/2026, mientras se esperaba la validación de pesos de la bibliotecaria). ADR-002 tardó una semana (31/10/2026 → 07/11/2026). | Más de 5 días hábiles, es decir, una reunión semanal sin decidir. Las solicitudes a la Alcaldía o a los proveedores de Koha no cuentan, porque no las decide el comité. |

**Principio sin métrica.** P2 (reducir la carga de la bibliotecaria) no tiene métrica todavía. La medida natural serían las horas que ella dedica a catalogar frente a las que dedica a revisar, pero hoy nadie las registra, así que no hay fuente ni línea base. Se deja escrito en lugar de inventar un valor.
