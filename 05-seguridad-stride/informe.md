# 📄 Informe Técnico del Taller

## 🔖 Nombre del Taller
_Taller 5 - Evaluación de Seguridad con STRIDE_

## 👥 Integrantes del equipo
- Jorge Alarcón
- Julián Aguirre
- Brayan Presiga

_(Equipo ARQUITECH)_

## 🧠 Descripción general del trabajo
El objetivo de este taller es aplicar el marco STRIDE (Spoofing, Tampering, Repudiation, Information Disclosure, Denial of Service, Elevation of Privilege) sobre un flujo crítico de la Biblioteca Pública Municipal Rubiel Valencia Cossio, para identificar amenazas de seguridad concretas y proponer mitigaciones priorizadas por riesgo. Se eligió como flujo crítico el **registro y gestión de datos personales de usuarios/afiliados (formulario de inscripción, Koha y Llave del Saber)**, porque es el punto donde confluyen los hallazgos más sensibles de los talleres anteriores: duplicidad de sistemas (Taller 3), ausencia de redundancia y credencial única (Taller 4), y el hecho de que ese flujo maneja datos personales de menores de edad. Esta versión corrige el análisis con lo confirmado después en los Talleres 4 y 6: Biteca opera Koha, el catálogo público (OPAC) y la app Nextbit ya existen, la inscripción se hace en un formulario de Microsoft Forms y los estudiantes de servicio social catalogan con cuentas compartidas.

## 🔧 Proceso de desarrollo
Seguimos la metodología de 5 pasos de la guía del taller:

1. **Elegir el flujo y dibujar su DFD** — se representó el flujo de registro de datos personales como un diagrama de flujo de datos, marcando los límites de confianza: la biblioteca de Cogua es la única zona bajo control directo del cliente; Microsoft 365 (formulario, en una cuenta creada por un estudiante), el centro de datos de Biteca (Koha, OPAC, Nextbit) y Llave del Saber (RNBP) son zonas externas, cada una con su proveedor.
2. **Identificar los elementos a analizar** — se listaron los procesos (formulario de inscripción, interfaz de registro en Koha, formulario web de Llave del Saber, OPAC y app Nextbit), los almacenes de datos (respuestas del formulario, BD Koha, BD Llave del Saber) y los flujos entre el usuario/afiliado, la bibliotecaria, los estudiantes de servicio social y los sistemas.
3. **Aplicar las 6 categorías STRIDE** — se formuló al menos una amenaza concreta por categoría sobre un elemento específico del DFD y, tras contrastar con los hallazgos del Taller 6, se añadieron tres amenazas (T7, T8 y T9).
4. **Reconocimiento pasivo autorizado** — en lugar de asumir qué controles existen hoy en Llave del Saber, se buscó evidencia pública real: el manual oficial de usuario del sistema (publicado por la propia RNBP) confirma textualmente que **"cada biblioteca tendrá un único usuario de acceso para todas las personas que trabajan en la biblioteca"** y que esa contraseña **"será el mismo para todos los sistemas de información nacionales"** de la RNBP. Esta evidencia, obtenida por observación pasiva de documentación pública (sin ninguna prueba activa contra el sistema), cambió por completo el nivel de detalle y la severidad de las amenazas T1 y T3 frente a lo que hubiéramos escrito por simple suposición. En la revisión posterior, T3 se recalculó con el Taller 6 (ítem 9): las cuentas compartidas de Koha ya existen, así que el riesgo es actual y no futuro.
5. **Evaluar impacto y priorizar por riesgo** — se completaron impacto, probabilidad y nivel de riesgo para cada amenaza, y se ordenó la tabla de mayor a menor riesgo (7 amenazas de riesgo Alto y 2 de riesgo Medio).

En la Parte 1 (trabajo en clase), aplicamos primero la misma metodología completa sobre el caso base de EdukIT siguiendo el ejemplo ya resuelto en la guía, y adicionalmente completamos el reto práctico #1 de OWASP Juice Shop (login bypass) en una instancia local, registrando el hallazgo como una fila adicional (T7) en `tabla-stride-clase.xlsx` — sin repetir esa técnica activa contra ningún sistema real, tal como exige la guía.

## 🧩 Análisis del modelo propuesto

**Cómo se estructura el modelo:**
El DFD tiene 3 actores (Usuario/Afiliado, Bibliotecaria y Estudiante de servicio social, modelados como roles), 4 procesos (P1 interfaz de Koha, P2 formulario de Llave del Saber, P3 formulario de Microsoft Forms, P4 OPAC y app Nextbit) y 3 almacenes de datos (D1 BD Koha, D2 BD Llave del Saber, D3 respuestas del formulario), repartidos en 4 zonas: Biblioteca de Cogua (bajo control del cliente), Microsoft 365, centro de datos de Biteca y Llave del Saber (las tres externas, cada una con su proveedor). Sobre estos 10 elementos se identificaron 9 amenazas, cubriendo las 6 categorías STRIDE, en `tabla-stride-cliente.xlsx`.

**Cómo representa las necesidades del cliente:**
Dos de las seis amenazas (T1 y T3) giran alrededor del mismo hallazgo real: **la credencial de acceso institucional es única por biblioteca y se reutiliza en todos los sistemas nacionales**. Esto no es una suposición — es una cita textual del manual oficial de Llave del Saber — y tiene una implicación directa sobre la ficha de caracterización del cliente: los estudiantes de servicio social ya trabajan junto a la bibliotecaria con dos cuentas de Koha con permisos de edición compartidas (Taller 6, ítem 9), y en Llave del Saber la credencial sigue siendo única, por lo que **varias personas entran con la misma cuenta**, sin ninguna forma de auditar quién hizo qué. La amenaza T4 (exposición de datos de menores) conecta directamente con que la plataforma maneja categorías de usuario como "Niños (6 a 12 años)" y "Primera Infancia (0 a 5 años)", lo cual activa protecciones reforzadas bajo la Ley 1581 de 2012. Las amenazas nuevas salen de los hallazgos del Taller 6: T7 (el formulario de Microsoft Forms vive en la cuenta personal de un estudiante, ítems 8 y 11), T8 (reportes y exportaciones de Koha desde cuentas compartidas, ítem 11) y T9 (permisos de edición compartidos con estudiantes, ítem 9). La amenaza T6 se recalculó porque el OPAC y la app Nextbit ya exponen Koha a internet. La amenaza T5 retoma textualmente el hallazgo ya diagnosticado en el Taller 4 (conexión a internet sin respaldo), y se refuerza con un dato adicional encontrado en el propio manual de Llave del Saber: el sistema ya contempla que el internet puede fallar, porque permite registrar actividades con fecha retroactiva "cuando el servicio de internet no está disponible" — es decir, el proveedor asume como normal una condición que nosotros ya habíamos señalado como un riesgo.

**Qué supuestos se tomaron:**
1. No se tuvo acceso a ningún sistema real del cliente (ni Koha ni Llave del Saber) con credenciales — todo el reconocimiento fue pasivo, sobre documentación pública oficial. La columna "Controles de Seguridad Existentes" para T2, T3, T6, T7, T8 y T9 combina esa evidencia pública con los hallazgos ya diagnosticados en los Talleres 3 y 4, no con observación directa del sistema en producción.
2. La infraestructura de Koha la opera Biteca S.A.S. (contratada por IDECUT) en un centro de datos de Bogotá, y no fue auditada por el equipo (T4) — es una limitación explícita del alcance de este taller, no un hallazgo confirmado de vulnerabilidad real. No existe evidencia de un acuerdo de transmisión de datos entre la Alcaldía e IDECUT/Biteca (Taller 6, ítem 8).
3. La amenaza T6 (elevación de privilegios) se modeló como riesgo **actual**, porque el OPAC (cogua.bibliotecasidecut.com) y la app Nextbit ya existen y exponen la instancia de Koha a internet (confirmado en el Taller 4). Su nivel (probabilidad media, riesgo alto) es un juicio del equipo, sin pruebas activas. Se asumió además que la bibliotecaria transcribe las respuestas del formulario a Koha y a Llave del Saber; ese flujo no fue confirmado.
4. No se realizó ninguna prueba activa (inyección, manipulación de solicitudes, fuerza bruta) contra Koha ni contra Llave del Saber, conforme a la restricción estricta del taller.

## 📈 Diagrama final entregado
- [`tabla-stride-cliente.xlsx`](tabla-stride-cliente.xlsx) — Tabla STRIDE completa aplicada al flujo de registro de datos personales de la biblioteca

**Diagrama de flujo de datos (DFD) del flujo analizado:**

```mermaid
flowchart LR
    usuario(["🧑 Usuario / Afiliado"])

    subgraph cogua["Biblioteca de Cogua (única zona bajo control del cliente)"]
        bib(["🧑 Bibliotecaria"])
        est(["🧑 Estudiante de servicio social"])
    end

    subgraph ms["Microsoft 365 - cuenta creada por un estudiante (externo)"]
        p3["P3: Formulario de inscripción (Microsoft Forms)"]
        d3[("D3: Respuestas del formulario")]
    end

    subgraph biteca["Centro de datos Biteca - Bogotá (externo)"]
        p1["P1: Interfaz de Registro Koha"]
        d1[("D1: BD Koha")]
        p4["P4: OPAC y app Nextbit"]
    end

    subgraph lds["Llave del Saber - MinCultura / RNBP (externo)"]
        p2["P2: Formulario Web Llave del Saber"]
        d2[("D2: BD Llave del Saber")]
    end

    usuario -->|"F1: datos personales, de menores y sensibles (HTTPS)"| p3
    p3 -->|"F1b: persiste"| d3
    bib -->|"F1c: consulta las respuestas"| d3
    bib -->|"F2: transcribe, consulta y edita (cuenta compartida)"| p1
    est -->|"F2b: cataloga, edita y exporta reportes (cuenta compartida)"| p1
    p1 -->|"F3: persiste"| d1
    bib -->|"F4: ingresa los mismos datos (credencial única)"| p2
    p2 -->|"F5: persiste"| d2
    usuario -->|"F7: consulta el catálogo (HTTPS)"| p4
    p4 -->|"F8: lee el catálogo"| d1
```

![DFD](./dfd-cliente-final.drawio.svg)

## 📋 Tabla de actores, entidades o componentes

| Nombre del elemento | Tipo | Descripción | Responsable |
|---|---|---|---|
| Usuario / Afiliado | Actor externo | Persona que entrega sus datos personales (incluidos menores) para afiliarse o consulta el catálogo | Cliente |
| Bibliotecaria | Actor interno (rol) | Opera Koha, Llave del Saber y consulta las respuestas del formulario; comparte cuentas de Koha con los estudiantes | Cliente |
| Estudiante de servicio social | Actor interno (rol) | Cataloga, edita y exporta reportes en Koha con las cuentas compartidas | Cliente |
| Formulario de inscripción (P3) | Proceso | Formulario de Microsoft Forms donde el usuario se inscribe | Biblioteca / Alcaldía (cuenta de un estudiante) |
| Interfaz de Registro Koha (P1) | Proceso | Aplicación web del personal donde se cataloga y se registra usuarios | Biteca (instancia) / Biblioteca (uso) |
| Formulario Web Llave del Saber (P2) | Proceso | Formulario nacional donde se afilian usuarios y se reportan estadísticas | RNBP |
| OPAC y app Nextbit (P4) | Proceso | Catálogo público web y app móvil que consultan Koha | Biteca |
| Respuestas del formulario (D3) | Almacén de datos | Persiste las respuestas de inscripción en Microsoft 365 | Cuenta personal de un estudiante |
| BD Koha (D1) | Almacén de datos | Persiste los datos personales y bibliográficos de Koha | Biteca S.A.S. / IDECUT |
| BD Llave del Saber (D2) | Almacén de datos | Persiste los datos personales y de servicios a nivel nacional | Ministerio de las Culturas / Fundación Carvajal |

## 🔍 Investigación complementaria

### Tema investigado
Protección de datos personales de menores de edad en Colombia (Ley 1581 de 2012) y su aplicación al sector bibliotecario público, dado que la biblioteca registra usuarios en categorías como "Niños (6 a 12 años)" y "Primera Infancia (0 a 5 años)".

### Resumen
La Ley 1581 de 2012 establece en su artículo 7° que el tratamiento de datos personales de niños, niñas y adolescentes está en principio **prohibido**, salvo que se trate de datos de naturaleza pública y que dicho tratamiento respete el interés superior del menor y sus derechos fundamentales; en esos casos, la autorización debe darla el representante legal, no el menor. La Superintendencia de Industria y Comercio —autoridad de control de esta ley— confirma que los datos de menores tienen una protección reforzada frente a los de un adulto, lo que implica exigencias adicionales de cuidado para cualquier entidad, pública o privada, que los recolecte.

Esto tiene una implicación directa para la biblioteca: al registrar usuarios en categorías etarias que incluyen desde primera infancia, tanto Koha como Llave del Saber están tratando datos personales de menores, lo que activa formalmente el régimen reforzado de la Ley 1581 y su Decreto reglamentario 1377 de 2013. La biblioteca, sin embargo, no gestiona directamente la política de tratamiento de datos de ninguna de las dos plataformas —esa responsabilidad recae en la RNBP, en IDECUT y en su proveedor Biteca (Koha), y en la Alcaldía como Responsable del tratamiento—, por lo que la mitigación realista para el equipo no es "cifrar la base de datos" (fuera de su alcance técnico), sino exigir documentación formal de cumplimiento a quien sí controla esa infraestructura (y formalizar el acuerdo de transmisión con Biteca), y limitar internamente qué datos de menores se capturan y para qué se usan.

Finalmente, esta investigación reforzó una decisión concreta de la tabla STRIDE: la amenaza T4 (Information Disclosure) se calificó como **riesgo alto** no solo por el impacto técnico de una posible filtración, sino porque, al tratarse de datos de menores, cualquier filtración tendría además una consecuencia legal reforzada bajo la normativa colombiana vigente (al ser la Alcaldía una entidad pública, las infracciones se tramitan ante la Procuraduría y no con multa de la SIC) — un matiz que no habría aparecido sin conectar el hallazgo técnico con el marco legal del sector.

## 📚 Referencias
Ver [`referencias.md`](referencias.md).

---

_Este documento hace parte de la entrega del Taller 5 del curso AREM (Arquitectura Empresarial) - Universidad de La Sabana._
