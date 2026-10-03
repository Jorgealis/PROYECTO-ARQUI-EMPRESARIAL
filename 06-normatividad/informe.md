# 📄 Informe Técnico del Taller

## 🔖 Checklist de Cumplimiento Normativo
_Taller 6 - Checklist de cumplimiento normativo_

## 👥 Integrantes del equipo
- Brayan Presiga (brayanprse@unisabana.edu.co)
- Julian Aguirre (julianagla@unisabana.edu.co)
- Jorge Alarcon (jorgealis@unisabana.edu.co)

## 🧠 Descripción general del trabajo
Se realizó este taller con el propósito de verificar los aspectos legales, normativos y de cumplimiento que aplican a los procesos de nuestro cliente, la Biblioteca Pública Municipal Rubiel Valencia Cossio de Cogua. Aunque en los talleres anteriores el alcance se concentró en la catalogación, para este ejercicio lo ampliamos a los tres procesos que manejan información de la biblioteca: catalogación y gestión de material bibliográfico, registro y gestión de usuarios, y préstamo y circulación. Para construir la lista de control partimos de los marcos de la guía del taller (Habeas Data, ISO/IEC 27001, prevención de fugas y control de accesos) y la adaptamos a la normativa colombiana que realmente le aplica a una biblioteca pública municipal: la Ley 1581 de 2012 y su reglamentación [1][2], la Ley 1379 de 2010 de la Red Nacional de Bibliotecas Públicas [3], la Ley General de Archivos [4] y el Modelo de Seguridad y Privacidad de la Información de MinTIC [5].

El resultado es una checklist de 16 ítems organizados en siete categorías, evaluados con evidencia obtenida directamente del cliente: entrevistas con la bibliotecaria, el formulario de inscripción de usuarios y la política de tratamiento de datos de la Alcaldía de Cogua [6]. A partir de la evaluación se identificaron 12 brechas, cada una con su riesgo, una recomendación correctiva y un nivel de prioridad.

## 🔧 Proceso de desarrollo
#### Herramientas

- Excel: Diligenciar la plantilla oficial del taller (`checklist-cliente.xlsx`) con las hojas Checklist General y Brechas Identificadas.
- Editor markdown: Escribir la documentación y una versión espejo de la checklist (`checklist.md`).
- Git y github: Colaborar entre los miembros del equipo.
- Claude: Asistente de IA usado para analizar la guía del taller, investigar y verificar la normativa en fuentes oficiales, y estructurar la evaluación. Toda la información sobre la biblioteca la aportamos nosotros a partir del trabajo con el cliente.
- Microsoft Forms: Plataforma donde se construyó el nuevo formulario de inscripción de usuarios con el aviso de privacidad.

#### Proceso

1. **Análisis de la guía y la plantilla**: Revisamos la guía paso a paso del taller [12] y la plantilla oficial para entender qué produce cada paso. Identificamos que la entrega final son dos hojas (Checklist General y Brechas Identificadas) y que las tablas de los pasos 1, 2 y 4 son de trabajo.
2. **Definición del alcance**: Decidimos no limitar la checklist a la catalogación, porque el proceso donde se concentran los datos personales es el registro de usuarios y el préstamo. Por eso trabajamos con los tres procesos.
3. **Identificación de datos y procesos sensibles**: Listamos todos los datos que la biblioteca recolecta y clasificamos cada uno. Encontramos datos personales comunes (identificación, contacto), datos sensibles (discapacidad y grupo étnico), datos de menores de edad, datos de terceros (acudiente o contacto de emergencia) y datos que no son personales (el catálogo).
4. **Investigación normativa**: Consultamos los textos oficiales de cada norma y separamos lo que es obligación legal de lo que es estándar técnico o buena práctica. Por ejemplo, ISO/IEC 27001 es un estándar voluntario, mientras que la Resolución 500 de 2021 de MinTIC sí es exigible a las entidades territoriales [5].
5. **Recolección de evidencia con el cliente**: Hicimos preguntas concretas a la bibliotecaria sobre las plataformas, los accesos, los documentos existentes y el manejo de los registros físicos. Además encontramos la política de tratamiento de datos de la Alcaldía [6], que confirmó que el Responsable del Tratamiento es el municipio y no la biblioteca.
6. **Construcción de la checklist**: Agrupamos 16 ítems en las categorías de la guía y agregamos una categoría propia, *Catalogación y Colecciones*, porque la Ley 1379 de 2010 impone obligaciones verificables sobre el catálogo, el inventario y la conservación [3].
7. **Evaluación del cumplimiento**: Evaluamos cada ítem como Cumple o Parcial, siempre con evidencia concreta. La evaluación refleja el estado actual (AS-IS): no marcamos como cumplido nada que no estuviera implementado.
8. **Riesgo y priorización**: Definimos un criterio explícito de riesgo (Alto, Medio, Bajo) y otro de prioridad, y ordenamos las brechas según ellos.
9. **Ajuste del formulario y reevaluación**: Con base en los hallazgos redactamos un nuevo aviso de privacidad, que el cliente implementó en el formulario de inscripción. Con esa evidencia reevaluamos la checklist: tres ítems pasaron de Parcial a Cumple y una brecha bajó de riesgo Alto a Medio.
10. **Revisión de consistencia**: Verificamos que cada ítem Parcial tuviera su brecha, que cada criterio citara su fuente y que las recomendaciones corrigieran directamente la brecha encontrada.

## 🧩 Análisis del modelo propuesto

### Estructura del modelo
La checklist sigue la estructura de la plantilla oficial en dos hojas:

- **Checklist General**: 16 ítems en siete categorías (Consentimiento, Protección de Datos, Seguridad, Prevención de Fugas, Retención, Roles y Responsabilidades, y Catalogación y Colecciones). Como la plantilla no tiene una columna de fuente, la norma que sustenta cada ítem se cita entre paréntesis al final del *Criterio de Cumplimiento*.
- **Brechas Identificadas**: una fila por cada ítem en Parcial (12 en total). La columna *Riesgo* incluye el nivel seguido de una frase que explica la consecuencia, para cumplir con el requisito de la guía de que cada brecha tenga su riesgo explicado.

Para asignar el riesgo usamos este criterio:

- **Alto**: la brecha involucra datos sensibles o de menores, o permite el acceso no autorizado o la pérdida de control sobre los datos.
- **Medio**: la brecha incumple una obligación legal sin exponer directamente los datos, o afecta la prestación del servicio.
- **Bajo**: la brecha es una deficiencia formal o el incumplimiento de una política interna o buena práctica.

La prioridad sigue al riesgo (Alto → Alta, Medio → Media). La única excepción es la formación del personal, que tiene riesgo Bajo pero prioridad Media porque se ejecuta junto con el compromiso de confidencialidad de los estudiantes.

### Cómo representa las necesidades del cliente
La checklist muestra que la biblioteca cumple con 4 de los 16 ítems: la autorización expresa del usuario, el contenido del aviso de privacidad, la existencia de una política de tratamiento y el procedimiento de consultas y reclamos. Tres de esos cuatro se lograron durante el taller, gracias al nuevo formulario de inscripción.

Las 5 brechas de prioridad Alta se concentran en el control de acceso a los datos:

- dos cuentas de Koha con permisos de edición compartidas entre la bibliotecaria y los estudiantes de servicio social;
- el formulario de inscripción alojado en una cuenta creada por un estudiante;
- exportaciones de datos sin control;
- la pregunta de discapacidad, obligatoria y sin opción de no responder;
- la falta de un procedimiento evidenciado para validar las inscripciones de menores.

Estas brechas reflejan una biblioteca que está en plena implementación tecnológica (el catálogo en Koha tiene apenas cerca del 10 % de la colección) y que depende del apoyo de estudiantes para operar. Por eso las recomendaciones priorizan medidas de bajo costo y aplicación inmediata, como crear cuentas individuales y migrar el formulario a una cuenta institucional.

Un punto importante para el cliente es el tipo de consecuencia. Como la biblioteca es una dependencia de una autoridad pública, el incumplimiento de la Ley 1581 no genera multas de la Superintendencia de Industria y Comercio, sino que se remite a la Procuraduría General de la Nación [1]. El riesgo legal es disciplinario para los servidores responsables.

### Supuestos tomados
- La biblioteca es una dependencia de la Alcaldía de Cogua. Lo sustentamos con que la bibliotecaria aparece en el directorio de la Alcaldía como servidora pública, pero no revisamos el acto de creación de la biblioteca. De este supuesto depende que le apliquen la Resolución 500 de 2021 y la obligación de tablas de retención documental.
- El formulario de Microsoft Forms es el canal vigente de inscripción para Koha y la Llave del Saber, diligenciado por el propio usuario.
- Biteca S.A.S. actúa como Encargado del Tratamiento por su contrato con IDECUT [9]; no tuvimos acceso a ese contrato.
- Tratar el historial de préstamos como un dato que puede revelar información sensible (por los títulos leídos) es una interpretación nuestra, no una clasificación de la ley.
- El estrato socioeconómico, que exige la Llave del Saber [8], no es un dato sensible según la Ley 1581; lo tratamos como dato socioeconómico [10].

## 📋 Tabla de actores, entidades o componentes (si aplica)

| Nombre del elemento | Tipo | Descripción | Responsable |
|---------------------|------|-------------|-------------|
| Alcaldía Municipal de Cogua | Actor (Responsable del Tratamiento) | Decide sobre las bases de datos y responde legalmente por el tratamiento. Publicó la política de tratamiento de datos en abril de 2025 [6]. | Municipio de Cogua |
| Biblioteca Pública Municipal Rubiel Valencia Cossio | Unidad organizacional | Dependencia de la Alcaldía que recolecta los datos de los usuarios y gestiona el catálogo y los préstamos. | Alcaldía de Cogua |
| Bibliotecaria | Actor (rol humano) | Servidora pública que inscribe usuarios, cataloga material, gestiona préstamos y custodia los registros físicos. | Alcaldía de Cogua |
| Estudiantes de servicio social | Actor (rol humano) | Apoyan la catalogación y el registro de usuarios con acceso a Koha mediante cuentas compartidas. | Biblioteca (bajo supervisión de la bibliotecaria) |
| Usuario de la biblioteca | Actor (Titular de los datos) | Persona cuyos datos se registran; puede ejercer los derechos del art. 8 de la Ley 1581 [1]. | - |
| Acudiente o contacto de emergencia | Actor (Titular tercero) | Adulto cuyos datos se registran para localizarlo en una emergencia o, en el caso de menores, como responsable. | - |
| IDECUT | Actor externo | Instituto Departamental de Cultura y Turismo; contrató la implementación de Koha para la Red Departamental [9]. | Gobernación de Cundinamarca |
| Biteca S.A.S. | Actor externo (Encargado del Tratamiento, supuesto) | Empresa que implementa y da soporte a Koha en las bibliotecas de la Red Departamental [9]. | IDECUT |
| Superintendencia de Industria y Comercio | Autoridad | Vigila el cumplimiento de la Ley 1581; ante una autoridad pública, remite la actuación a la Procuraduría [1]. | Gobierno Nacional |
| Procuraduría General de la Nación | Autoridad | Ejerce el control disciplinario sobre los servidores públicos responsables. | Ministerio Público |
| Koha | Componente de aplicación | Sistema de gestión bibliotecaria para catálogo, usuarios y préstamos; catálogo público en cogua.bibliotecasidecut.com. | IDECUT / Biteca S.A.S. |
| Llave del Saber | Componente de aplicación | Sistema Nacional de Información de la Red Nacional de Bibliotecas Públicas para identificar usuarios y reportar el uso de los servicios [7]. | Ministerio de las Culturas / Biblioteca Nacional |
| Formulario de inscripción (Microsoft Forms) | Componente de aplicación | Canal único de inscripción con el aviso de privacidad y las autorizaciones. | Biblioteca (cuenta por migrar a una institucional) |

## 🔍 Investigación complementaria

### Tema 1: Datos sensibles y el carácter facultativo de la autorización

Al clasificar los datos que recolecta la biblioteca encontramos que dos de ellos, la discapacidad y el grupo étnico, son datos sensibles. Quisimos entender por qué esto cambia tanto la evaluación, ya que fue la base de una de las brechas de prioridad Alta.

La Ley 1581 define como sensibles los datos que afectan la intimidad del titular o cuyo uso indebido puede generar su discriminación, y menciona expresamente el origen racial o étnico y los datos relativos a la salud [1]. Para estos datos la regla general es la prohibición: solo pueden tratarse con autorización explícita del titular, salvo excepciones puntuales [1]. Además, cuando se pide la autorización, el responsable debe informar que responder las preguntas sobre datos sensibles es facultativo [1]. Esto explica por qué una pregunta de discapacidad obligatoria, cuya única salida es "Ninguna", no cumple: aunque la persona no tenga discapacidad, se le obliga a declarar algo sobre su salud. También explica por qué condicionar la inscripción a autorizar el tratamiento de datos sensibles es un problema, ya que convierte en obligatorio algo que la ley exige que sea voluntario.

Un hallazgo interesante fue el contraste con el estrato socioeconómico, que exige la Llave del Saber. Este dato no aparece en la lista de datos sensibles de la ley, y en la práctica de las entidades públicas se trata como dato socioeconómico [10]. Aun así, el propio manual de la Llave del Saber ofrece la opción "No responde" cuando el usuario no conoce la información [8], lo que muestra que la plataforma ya contempla una salida voluntaria que el formulario de la biblioteca todavía no ofrece para la discapacidad.

### Tema 2: Por qué el riesgo de la biblioteca es disciplinario y no una multa

Al documentar el riesgo de cada brecha, nuestro primer impulso fue escribir "sanción de la SIC", como en el ejemplo de GobData de la guía. Al revisar el régimen sancionatorio de la Ley 1581 encontramos que esto no es exacto para nuestro cliente.

La ley establece que las sanciones de la Superintendencia de Industria y Comercio, incluidas las multas, solo aplican a personas de naturaleza privada [1]. Cuando la SIC advierte un presunto incumplimiento de una autoridad pública, remite la actuación a la Procuraduría General de la Nación para que adelante la investigación respectiva [1]. Como la biblioteca es una dependencia de la Alcaldía, el riesgo legal real es disciplinario para los servidores públicos que tienen a cargo el tratamiento de los datos, no una multa para la entidad. Por eso en la columna de Riesgo hablamos de "posible investigación disciplinaria" y no de sanciones económicas.

Esto también nos ayudó a entender por qué la política de la Alcaldía es tan importante como evidencia. Esa política compromete a la entidad con controles concretos, como credenciales únicas por usuario, acuerdos de confidencialidad y archivadores con cerradura [6]. Así, varias brechas no solo incumplen la ley: también incumplen la política que la propia Alcaldía publicó, lo que hace más difícil justificarlas ante un control disciplinario.

## 📚 Referencias

**Normativa:**
- [1] Congreso de la República de Colombia. *Ley 1581 de 2012, por la cual se dictan disposiciones generales para la protección de datos personales*. 2012. http://www.secretariasenado.gov.co/senado/basedoc/ley_1581_2012.html
- [2] Presidencia de la República de Colombia. *Decreto 1377 de 2013, por el cual se reglamenta parcialmente la Ley 1581 de 2012* (compilado en el Decreto 1074 de 2015). 2013. https://www.funcionpublica.gov.co/eva/gestornormativo/norma.php?i=53646
- [3] Congreso de la República de Colombia. *Ley 1379 de 2010, por la cual se organiza la Red Nacional de Bibliotecas Públicas y se dictan otras disposiciones*. 2010. http://www.secretariasenado.gov.co/senado/basedoc/ley_1379_2010.html
- [4] Congreso de la República de Colombia. *Ley 594 de 2000, Ley General de Archivos*. 2000. http://www.secretariasenado.gov.co/senado/basedoc/ley_0594_2000.html
- [5] Ministerio de Tecnologías de la Información y las Comunicaciones. *Resolución 500 de 2021, por la cual se establecen los lineamientos y estándares para la estrategia de seguridad digital y se adopta el modelo de seguridad y privacidad como habilitador de la política de Gobierno Digital*. 2021. https://www.suin-juriscol.gov.co/viewDocument.asp?id=30044822

**Documentos del cliente y plataformas:**
- [6] Alcaldía Municipal de Cogua. *Política de Tratamiento de Datos Personales*. 2025. https://www.cogua-cundinamarca.gov.co/transparencia/politica-de-tratamiento-de-datos
- [7] Biblioteca Nacional de Colombia. *La Llave del Saber se actualiza y se renueva*. 2021. https://www.bibliotecanacional.gov.co/es-co/actividades/noticias/en-la-rnbp/llave-del-saber-se-actualiza
- [8] Llave del Saber. *Manual de usuario: Registro de usuarios*. https://llavedelsaberrnbp.gov.co/manual_usuario/reg_usu/registro_usuarios.php
- [9] Biteca S.A.S. *Koha como herramienta de acceso al conocimiento*. 2024. https://www.biteca.com/koha_acceso_conocimiento/

**Clasificación de datos personales:**
- [10] Superintendencia de Sociedades. *Manual de Tratamiento de Datos Personales (GC-M-003)*. https://www.supersociedades.gov.co/documents/107391/3463418/GC-M-003_ManualTratamientoDatosPersonales.pdf
- [11] Superintendencia de Industria y Comercio. *Sobre la protección de datos personales*. https://www.sic.gov.co/content/sobre-la-protecci%C3%B3n-de-datos-personales

**Material del curso y apoyo:**
- [12] Universidad de La Sabana, curso AREM. *Guía Paso a Paso: Checklist de Cumplimiento Normativo* (`paso_a_paso_normatividad.md`), Taller 6.
- [13] Fuente asistida por IA: Claude (Anthropic), septiembre-octubre 2026.

---

_Este documento hace parte de la entrega del taller 6 del curso AREM (Arquitectura Empresarial) - Universidad de La Sabana._
