# 📄 Informe Técnico del Taller

## 🔖 Nombre del Taller
_Taller 7 - Opportunities & Solutions (Parte 2: aplicación al cliente real)_

## 👥 Integrantes del equipo
- Jorge Alarcón (Jorgealis)
- Julián Aguirre (JulianAguirreUnisabana)
- Brayan Presiga (Brayan-137)

_(Equipo ARQUITECH)_

## 🧠 Descripción general del trabajo
El objetivo del taller es proponer la arquitectura objetivo (TO-BE) de Aplicaciones y de Tecnología de la Biblioteca Pública Municipal de Cogua - Rubiel Valencia Cossio. Para ello se identifican las brechas frente al estado actual (AS-IS) documentado en los Talleres 1 a 6, incluidas la seguridad y el cumplimiento normativo, y se priorizan las soluciones que las cierran. En la Parte 1, trabajada en clase, se aplicó la metodología al caso base de RedExpress. Este informe documenta la **Parte 2**: el TO-BE del cliente real, que se entrega en `mejora-arquitectura.md` junto con sus anexos.

## 🔧 Proceso de desarrollo

#### Herramientas
- Draw.io: diagramas TO-BE, construidos extendiendo los `.drawio` finales de los Talleres 3 y 4.
- Excel: matriz de brechas y cálculo de la matriz de decisión con fórmulas (`matriz-brechas.xlsx`).
- Editor Markdown, Git y GitHub: documentación y trabajo colaborativo.
- Claude: asistente de IA para proponer opciones, borradores de puntajes y análisis de sensibilidad, y para buscar fuentes [16]. Todos los datos del cliente los aportó el equipo; lo propuesto por la IA se registra en la matriz de decisión.

#### Proceso
1. **Lectura de la guía y las plantillas.** Se siguió la metodología en 4 partes (diagnóstico, propuesta de mejoras, visualización TO-BE, beneficios y riesgos) y la rúbrica del taller [1].
2. **Consolidación del diagnóstico.** Se reunieron los hallazgos del BPMN (Taller 1), el C2 (Taller 3), el mapa de infraestructura (Taller 4), la tabla STRIDE (Taller 5) y el checklist normativo (Taller 6) en 8 brechas, cada una trazada a su taller de origen. No se agregaron hallazgos nuevos.
3. **Elección de la brecha raíz.** El equipo decidió que la brecha más importante es la catalogación manual del BPMN. El mapa del Taller 4 y el checklist del Taller 6 mostraron que el catálogo público ya existe pero solo contiene cerca del 10 % de la colección, así que el problema es la carga del catálogo y no la falta de una plataforma.
4. **Lluvia de ideas y priorización.** Se listaron 9 ideas (proceso, tecnología, seguridad, cumplimiento y gobierno) y se priorizaron 3 por esfuerzo e impacto, distinguiendo quick wins de mejoras de mayor plazo.
5. **Matriz de decisión ponderada.** Para G1 se compararon tres opciones con 4 criterios. Se incorporaron dos datos del equipo: Koha no ofrece carga por lotes, así que esa opción exige una app propia, y sí se pueden crear más cuentas en Koha. Los totales y la sensibilidad se recalcularon con fórmulas.
6. **Visualización TO-BE.** Se copiaron los `.drawio` del Taller 3 y 4 y se agregaron los componentes nuevos (en verde) con los mismos nombres de los componentes existentes. Los elementos de Fase 2 van con borde punteado.
7. **Controles de seguridad.** Se tomaron las mitigaciones del Taller 5 y las recomendaciones del Taller 6, y se trazó cada control al componente que lo implementa.
8. **Beneficios, riesgos, capacidades y paquetes de trabajo.** Se contrastó cada solución con sus dependencias reales y se agruparon las brechas por capacidad de negocio en 5 paquetes.
9. **Investigación complementaria.** Se consultó la documentación de Koha (API, permisos, catalogación por copia) y el principio de mínimo privilegio.

## 🧩 Análisis del modelo propuesto

### Estructura del modelo
- **Aplicaciones:** extiende el C2 del Taller 3 con el actor *Estudiante catalogador*, los dos perfiles de Koha (bibliotecaria-admin y catalogador), el *Formulario de inscripción* en cuenta institucional y, en Fase 2, la *App de carga por lotes*.
- **Tecnología:** extiende el mapa del Taller 4 con una zona de herramientas de catalogación (lector de códigos, portal del estudiante, app de Fase 2) y el respaldo 3-2-1 del PC (disco externo y nube institucional). Las zonas de Biteca, Llave del Saber y Z39.50 no cambian, porque la biblioteca no las controla.
- **Priorización:** 3 soluciones priorizadas (catalogación distribuida, catalogación asistida y respaldo 3-2-1) y una Fase 2 condicionada (carga por lotes).

### Cómo representa las necesidades del cliente
- Disminuye la carga de la bibliotecaria sin pedirle más horas: el trabajo repetitivo pasa a los dos estudiantes de servicio social y ella pasa a revisar una muestra.
- Responde a la restricción de recursos limitados: las dos primeras mejoras son de bajo costo (servicio social existente y un lector de códigos).
- Cierra al mismo tiempo brechas de seguridad y cumplimiento que ya estaban diagnosticadas: cuentas individuales y perfil restringido frente al acceso compartido a datos de menores (Taller 5, T3 y T4; Taller 6, ítems 9, 11, 13 y 14).
- Atiende el riesgo de mayor severidad del Taller 4 (pérdida permanente de archivos) con una medida que la biblioteca ejecuta sola.
- Respeta la restricción legal de la ficha: ninguna solución migra metadatos desde Llave del Saber hacia Koha.

### Supuestos tomados
- Los dos estudiantes dedican unas 15 horas semanales cada uno. Es un supuesto del equipo, sin confirmar con la bibliotecaria.
- El perfil de solo catalogación se puede configurar en la instancia de Koha de Cogua. El equipo confirmó que se pueden crear cuentas, y la documentación indica que los permisos se asignan por módulo [5][6], pero el perfil restringido aún no se ha probado.
- La API REST de Koha no está confirmada en la versión de Biteca. Por eso la carga por lotes es una Fase 2 condicionada [3][4].
- Los costos (lector de códigos, nube) son supuestos por cotizar. La nube sería una cuenta institucional de la Alcaldía.
- Los pesos de la matriz de decisión son una propuesta del equipo con apoyo de IA y están pendientes de validar con la bibliotecaria.
- La fecha de noviembre de la ficha no se usó en esta iteración, por lo que el "último momento responsable" queda pendiente.

### Limitaciones
No se tuvo acceso administrativo a Koha ni a Llave del Saber, y Biteca no puede responder algunas preguntas por restricciones contractuales (Taller 4). Por eso las soluciones que dependen de configuración de Koha se presentan con su dependencia explícita y se marcan para validar antes de implementarse.

## 📈 Diagrama final entregado
<img width="1608" height="927" alt="to-be-aplicaciones-final drawio" src="https://github.com/user-attachments/assets/b89f9777-a607-4d0b-a977-738378ca061d" />

- [`to-be-aplicaciones-final.drawio`](to-be-aplicaciones-final.drawio): TO-BE de Aplicaciones (extiende el C2 del Taller 3).

<img width="1402" height="1082" alt="to-be-tecnologia-final drawio" src="https://github.com/user-attachments/assets/4023dba7-811a-432b-9adb-6c0467778786" />

- [`to-be-tecnologia-final.drawio`](to-be-tecnologia-final.drawio): TO-BE de Tecnología (extiende el mapa del Taller 4).
- [`matriz-brechas.xlsx`](matriz-brechas.xlsx): matriz de brechas, decisión ponderada de G1 y capacidades.

En ambos diagramas, el verde indica un componente nuevo y el borde punteado indica un elemento de Fase 2 por confirmar con Biteca.

## 📋 Tabla de actores, entidades o componentes

| Nombre del elemento | Tipo | Descripción | Responsable |
|---|---|---|---|
| Estudiante catalogador | Actor (nuevo) | Estudiante de servicio social con cuenta individual y perfil de solo catalogación en Koha | Biblioteca (supervisa la bibliotecaria) |
| Bibliotecaria | Actor (existente) | Pasa de digitar a revisar una muestra de registros; administra cuentas y reportes de Koha | Alcaldía de Cogua |
| Koha (perfiles admin y catalogador) | Contenedor (modificado) | Sistema de gestión bibliotecaria con cuentas individuales y permisos por módulo | IDECUT / Biteca (instancia); la biblioteca administra las cuentas |
| Formulario de inscripción | Contenedor (nuevo en el C2) | Microsoft Forms en cuenta institucional; recoge la autorización del usuario y sus datos | Biblioteca / Alcaldía |
| Lector de códigos de barras / ISBN | Periférico (nuevo) | Se conecta al PC y escribe el ISBN donde esté el cursor [8] | Biblioteca |
| Portal Web (Koha) - Estudiante catalogador | Cliente (nuevo) | Acceso del estudiante con cuenta individual y perfil restringido | Biblioteca |
| App de carga por lotes (Fase 2) | Contenedor (nuevo, condicionado) | Lee ISBN, consulta Z39.50/SRU y carga registros a Koha por la API con una cuenta de servicio | Equipo ARQUITECH / por definir |
| Almacenamiento local - PC bibliotecaria | Almacenamiento (modificado) | Pasa de copia única a copia 1 de 3 | Biblioteca |
| Disco externo | Almacenamiento (nuevo) | Copia 2, en otro tipo de medio | Biblioteca |
| Almacenamiento en la nube institucional | Almacenamiento (nuevo) | Copia 3, fuera del sitio | Alcaldía / Biblioteca |

## 🔍 Investigación complementaria

### Tema 1: Catalogación por copia, lector de códigos y por qué la carga por lotes exige una app aparte

Al estudiar la brecha de catalogación quisimos entender qué partes del proceso del BPMN ya se pueden acelerar con las herramientas de Koha. La documentación describe que los registros se agregan por catalogación original o por copia, y que el botón de importación desde Z39.50/SRU abre el registro encontrado en el editor de catalogación para modificarlo y guardarlo [7]. También se recomienda buscar por ISBN, porque da el registro exacto [9]. Un manual de catalogación de otra biblioteca indica que, si se usa un lector de códigos de barras, basta ubicar el cursor en el campo ISBN y escanear [8]. Con esto, la idea del lector de códigos se apoya en una práctica real de uso, y no hace falta cambiar el sistema.

La carga por lotes es distinta. Como Koha no la ofrece en esta instalación, habría que construir una app que haga el trabajo hacia Koha. Koha tiene dos caminos de integración. El primero es una API antigua (`/svc/`) con rutas para crear y actualizar registros con archivos MARCXML [2]. El segundo es la API REST moderna, con una ruta POST para crear registros bibliográficos aceptando formatos MARC, cuyo desarrollo se discutió en el bug 31800 [3][4]. Según las instrucciones de prueba de ese parche, para usarla hay que activar la preferencia de autenticación básica (RESTBasicAuth) e indicar el marco de catalogación en una cabecera [3]. Esto nos llevó a dos decisiones: modelar la carga por lotes como Fase 2 condicionada, porque la versión de Koha de Biteca es desconocida, y asumir que la app necesita una credencial propia que Biteca tendría que autorizar, lo que aparece como dependencia en la matriz.

### Tema 2: Mínimo privilegio y permisos por módulo en Koha

El Taller 6 mostró que las cuentas de edición de Koha se comparten entre la bibliotecaria y los estudiantes, y que eso contradice la política de la Alcaldía. Para diseñar una alternativa investigamos cómo gestiona Koha los permisos. El personal accede a la interfaz de gestión con el permiso mínimo `catalogue`, que permite ver el catálogo, y los demás permisos se suman por módulo: edición de catálogo, usuarios (`borrowers`), parámetros, entre otros [5]. Solo quien tenga el permiso para modificar permisos de otro personal (o el de superbibliotecario) puede asignarlos desde la ficha del usuario, con la opción "Establecer permisos" [5][6]. Esto es lo que hace viable el perfil catalogador: un estudiante con permisos de catalogación y sin permiso sobre usuarios no vería datos personales de menores.

Esto coincide con el principio de mínimo privilegio, que el control AC-6 de NIST SP 800-53 formula como permitir solo los accesos necesarios para las tareas asignadas, y que aplica también a procesos que actúan en nombre de usuarios [10]. De ahí sacamos una segunda aplicación: la cuenta de servicio de la app de Fase 2 debe tener permiso solo para crear registros bibliográficos, y no la clave institucional de Llave del Saber ni una cuenta de administración. Así, el mismo principio justifica tanto el perfil de los estudiantes como la credencial de la app.

## 📚 Referencias
Ver [`referencias.md`](referencias.md).

---

_Este documento hace parte de la entrega del Taller 7 (Opportunities & Solutions) del curso AREM (Arquitectura Empresarial) - Universidad de La Sabana._
