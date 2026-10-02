# 📄 Informe Técnico del Taller

## 🔖 Nombre del Taller
_Taller 3 - Arquitectura Actual del Sistema con el Modelo C4_

## 👥 Integrantes del equipo
- Jorge Alarcón
- Julián Aguirre
- Brayan Presiga

_(Equipo ARQUITECH)_

## 🧠 Descripción general del trabajo
El objetivo de este taller es representar la arquitectura **actual (AS-IS)** de la Biblioteca Pública Municipal Rubiel Valencia Cossio usando las vistas **C1 (Contexto)** y **C2 (Contenedores)** del modelo C4. Este trabajo corresponde a la Parte 2 del taller — la aplicación al cliente real — y se construye sobre el diagnóstico AS-IS y el levantamiento de información que el equipo ya había realizado con la bibliotecaria Ana Cecilia Pastrana Rodríguez.

## 🔧 Proceso de desarrollo
Seguimos la metodología de 4 pasos de la guía del taller, una vista a la vez:

1. **C1 — Identificación de actores y límites del sistema.** A partir de la ficha de caracterización y el diagnóstico AS-IS ya elaborados, identificamos dos actores humanos (la bibliotecaria y el usuario/afiliado) y definimos el **sistema en alcance** como el conjunto de herramientas que la biblioteca opera directamente. Los sistemas de terceros que no están bajo control del equipo ni del cliente (Llave del Saber y la red de catalogación compartida vía Z39.50) se marcaron como externos.
2. **C2 — Descomposición en contenedores.** Investigamos la arquitectura técnica real de Koha (documentada públicamente) para descomponer el sistema en alcance de forma fiel: Koha como aplicación web, su base de datos relacional y su motor de indexación, además de las herramientas paralelas que hoy sostienen procesos que Koha todavía no cubre (Excel y el registro físico en papel).
3. **Validación cruzada con el diagnóstico previo.** Contrastamos ambos diagramas contra los hallazgos ya documentados en el AS-IS (duplicidad de sistemas, dependencia de infraestructura externa, ausencia de canal digital para usuarios) para asegurarnos de que el modelo C4 no contradijera, sino que reforzara con notación formal, lo que ya se había diagnosticado de forma más narrativa.
4. **Herramienta:** ambos diagramas se construyeron en draw.io, siguiendo la leyenda de notación de la guía (persona = óvalo azul, sistema en alcance = rectángulo azul oscuro, sistema externo = rectángulo gris de doble borde, contenedor = rectángulo azul claro, infraestructura = cilindro/rectángulo gris).

## 🧩 Análisis del modelo propuesto

**Cómo se estructura el modelo:**
- El **C1** muestra 2 actores, 1 sistema en alcance y 2 sistemas externos, con las 4 relaciones correspondientes etiquetadas.
- El **C2** abre el sistema en alcance en 3 contenedores (Koha, Excel, Registro Físico) y 2 piezas de infraestructura (base de datos de Koha y su motor de indexación), manteniendo visibles los mismos actores y sistemas externos del C1, tal como exige la metodología.

**Cómo representa las necesidades del cliente:**
- El diagrama C2 hace explícita, con una arista propia, la **duplicidad de sistemas** que la ficha de caracterización señala como el problema #2: la bibliotecaria alimenta Koha *y* Llave del Saber por separado — la relación entre la Bibliotecaria y Llave del Saber sale directamente de ella, no del sistema Koha, precisamente porque hoy no existe integración entre ambos.
- La relación entre el Usuario/Afiliado y Koha se etiquetó explícitamente como "sin canal digital directo, mediado presencialmente por la bibliotecaria" — esto refleja el problema #3 de la ficha (falta de una plataforma digital para que los usuarios consulten el inventario) en vez de forzar una relación digital que hoy no existe.
- Incluir el "Registro Físico (Carpeta)" como contenedor, aunque no sea software, mantiene la fidelidad del AS-IS: es una pieza real del proceso actual y va a ser insumo directo de cualquier propuesta TO-BE de migración de datos.

**Supuestos tomados:**
1. Se modeló "Sistema de Gestión Biblioteca Rubiel Valencia Cossio" como una única caja en el C1, aunque en la realidad no es un sistema unificado sino tres herramientas fragmentadas — esa fragmentación se revela intencionalmente al bajar al nivel C2, que es justamente el propósito de cada nivel de abstracción en C4.
2. Se asumió que Koha corre sobre MySQL/MariaDB con un motor de indexación tipo Zebra (u opcionalmente Elasticsearch), siguiendo la arquitectura estándar documentada del proyecto Koha — esto no fue confirmado directamente con el proveedor de hosting real usado por la RNBP para esta biblioteca en particular.
3. Se asumió que la relación entre la bibliotecaria y Llave del Saber es completamente independiente de Koha (sin sincronización automática), con base en el problema #2 documentado en la ficha de caracterización del cliente.
4. No se incluyó el proceso de préstamos ni de gestión de eventos en el C2 (aunque sí aparecen como procesos de negocio en el diagnóstico AS-IS previo), porque el foco de modelado acordado con la bibliotecaria para esta primera fase es el registro de material bibliográfico.

## 📈 Diagrama final entregado
- [`c1-contexto-final.drawio`](c1-contexto-final.drawio) — Vista de Contexto (C1)
- [`c2-contenedores-final.drawio`](c2-contenedores-final.drawio) — Vista de Contenedores (C2)

## 📋 Tabla de actores, entidades o componentes

| Nombre del elemento | Tipo | Descripción | Responsable |
|---|---|---|---|
| Bibliotecaria (Ana Cecilia Pastrana) | Actor | Única empleada de la biblioteca; ejecuta manualmente el registro, préstamo y reporte de información | Cliente |
| Usuario / Afiliado | Actor | Visitante que consulta o solicita préstamo de material; hoy sin canal digital propio | Cliente |
| Sistema de Gestión Biblioteca Rubiel Valencia Cossio | Sistema en alcance | Conjunto de herramientas operadas directamente por la biblioteca (Koha + Excel + registro físico) | Equipo ARQUITECH (modelado) |
| Koha | Contenedor | ILS de código abierto; cataloga material bibliográfico con estándar MARC21 | RNBP / Biblioteca |
| Hoja de Cálculo Excel | Contenedor | Registro y consulta manual de visitantes | Bibliotecaria |
| Registro Físico (Carpeta) | Contenedor manual | Registro en papel de datos de usuarios | Bibliotecaria |
| Base de Datos Koha | Infraestructura | Persistencia de registros bibliográficos y de usuarios (MySQL/MariaDB) | RNBP (hosting externo) |
| Motor de Indexación | Infraestructura | Búsqueda de catálogo y protocolo Z39.50 (Zebra / Elasticsearch) | RNBP (hosting externo) |
| Llave del Saber | Sistema externo | Plataforma nacional de estadísticas, usuarios y servicios bibliotecarios (RNBP) | Ministerio de las Culturas / Fundación Carvajal |
| Red de Catalogación Compartida | Sistema externo | Bibliotecas conectadas vía Z39.50 para copiar registros bibliográficos existentes | Terceros (otras bibliotecas y redes) |

## 🔍 Investigación complementaria

### Tema investigado
Arquitectura técnica real de Koha (ILS de código abierto) y del Sistema Nacional de Información Llave del Saber, como sustento para decidir qué piezas del ecosistema de la biblioteca son "sistema en alcance" y cuáles son "sistemas externos" en el modelo C4.

### Resumen
La arquitectura de Koha está documentada públicamente por su propia comunidad: el sistema se construye sobre una base de código en Perl y JavaScript, persiste su información transaccional en una base de datos relacional (MySQL o MariaDB) y almacena los registros bibliográficos en formato MARC21. Para la búsqueda y recuperación de catálogo, Koha se apoya históricamente en el motor de indexación Zebra —que además implementa el protocolo Z39.50, usado tanto para copiar registros de catálogos externos como para exponer el propio catálogo a otras bibliotecas—, aunque Elasticsearch se ha ido consolidando como alternativa más moderna. Esta separación entre "datos transaccionales" y "búsqueda/interoperabilidad bibliográfica" es exactamente la que representamos en el C2 como dos piezas de infraestructura distintas.

Llave del Saber, en cambio, no es un ILS de propósito general sino una plataforma de estadísticas y gestión construida específicamente para la Red Nacional de Bibliotecas Públicas: la desarrolla desde 2013 el Ministerio de las Culturas en alianza con la Fundación Carvajal, centraliza la identificación de usuarios y el reporte de servicios de cerca de 1.400 bibliotecas públicas del país, es de acceso totalmente web (no requiere instalación local) y las credenciales de acceso las asigna directamente la RNBP a cada biblioteca. Esto confirma que Llave del Saber está genuinamente fuera del control técnico del cliente, lo que sustenta su clasificación como sistema externo en el C1 y el C2.

Comparar ambas arquitecturas ayudó a justificar la frontera del sistema en alcance: Koha, aunque también depende de infraestructura de hosting gestionada por un tercero, es el sistema que la bibliotecaria opera y personaliza directamente día a día (cataloga, corrige metadatos, crea ítems), por lo que se modela como parte del sistema en alcance; Llave del Saber es una herramienta cerrada y administrada centralmente en la que la biblioteca únicamente alimenta datos, sin ninguna capacidad de configuración arquitectónica, por lo que corresponde clasificarla como sistema externo según la metodología C4.

## 📚 Referencias
Ver [`referencias.md`](referencias.md).

---

_Este documento hace parte de la entrega del Taller 3 del curso AREM (Arquitectura Empresarial) - Universidad de La Sabana._
