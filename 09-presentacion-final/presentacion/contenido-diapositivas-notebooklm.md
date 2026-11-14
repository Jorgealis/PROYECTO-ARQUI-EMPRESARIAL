# Contenido de las diapositivas: Comité de Arquitectura, Biblioteca de Cogua

## Instrucciones de diseño (para NotebookLM)
- 5 diapositivas en español, de apoyo a una exposición oral de 10 minutos. **Poco texto**: máximo unas 20 palabras visibles por diapositiva, sin contar las etiquetas de los diagramas.
- Cada diapositiva gira en torno a **un diagrama simple** que cuenta una sola idea. No usar diagramas técnicos completos.
- Estilo: **tema claro, profesional y minimalista**. Fondo blanco o marfil, texto gris carbón y **un solo color de acento** (verde pizarra oscuro) para lo nuevo o lo positivo. Un rojo apagado solo para marcar problemas o riesgos. Sin colores institucionales de universidades, sin degradados, sin imágenes de stock y sin íconos decorativos de relleno.
- Tipografía sobria (una serif para títulos y una sans-serif para el texto) y mucho espacio en blanco.
- La historia: **una biblioteca con una sola bibliotecaria → un catálogo que no avanza → repartir el trabajo de forma segura → hacerlo cumpliendo la ley → un plan con fechas.**

---

## Diapositiva 1. Conocer la organización
**Título:** Biblioteca Pública Municipal de Cogua "Rubiel Valencia Cossio"
**Mensaje clave:** Una biblioteca pública que sostiene una sola persona.

**Diagrama: "mapa de la organización".** Un círculo central con "Biblioteca de Cogua" y tres bloques alrededor:
- **Personas:** 1 bibliotecaria (Ana Cecilia Pastrana) y estudiantes de servicio social (de 2 a 8 h por semana).
- **Colección:** de 7.000 a 8.000 libros.
- **Herramientas:** Koha (catálogo, operado por Biteca para IDECUT), Llave del Saber (Red Nacional de Bibliotecas) y Excel.

Debajo, una franja con la **meta del cliente**: "~3.000 libros en Koha en noviembre".

**Texto visible:** "1 bibliotecaria · 7.000–8.000 libros · 3 herramientas"

---

## Diapositiva 2. El problema (AS-IS)
**Título:** El catálogo existe, pero está casi vacío
**Mensaje clave:** Catalogar depende de una sola persona y, a este ritmo, la meta tarda 9 meses.

**Diagrama izquierdo: el proceso actual simplificado** (resume el BPMN del Taller 1). Un flujo horizontal de 4 pasos, todos sobre una sola figura de persona con la etiqueta "Bibliotecaria":
1. Llega un libro
2. Busca el registro en servidores externos
3. Importa o digita los datos
4. Corrige campos y guarda

Una flecha de regreso del paso 4 al 1 con la etiqueta "libro por libro". Los pasos 2 a 4 se marcan con el rojo apagado como el cuello de botella.

**Diagrama derecho: barra de avance.** Una barra horizontal que representa la colección (7.000–8.000):
- Tramo lleno: **~1.150 en Koha**, alrededor del 15 %.
- Marca vertical: **meta de 3.000**.
- Debajo: "Ritmo actual: ~200 libros/mes → ~9 meses para la meta".

**Franja inferior** (resume el C2 del Taller 3): "El canal para el público ya existe (catálogo web y app Nextbit). Lo que falta es contenido."

**Texto visible:** "Una persona · libro por libro · ~200 libros al mes"

---

## Diapositiva 3. La propuesta (TO-BE)
**Título:** Repartir el trabajo, con seguridad
**Mensaje clave:** Los estudiantes catalogan con su propia cuenta, la bibliotecaria supervisa y la tecnología acelera.

**Diagrama central: antes y después de quién hace qué** (resume el TO-BE de aplicaciones del Taller 7). Dos columnas:
- **Antes:** la bibliotecaria y los estudiantes entran a Koha con una **cuenta compartida**. La bibliotecaria digita todo.
- **Después:**
  - Estudiantes → **cuenta individual con perfil de catalogador** → Koha.
  - Herramientas de apoyo: **lector de ISBN** y **app móvil de catalogación por lotes** (la app está marcada con borde punteado: "conexión al Koha real, sujeta a autorización").
  - Bibliotecaria → **perfil administradora** → revisa una muestra cada semana.
  - Al lado, un ícono pequeño: **respaldo 3-2-1** (PC, disco externo y nube institucional).

**Gráfico pequeño (esquina):** "¿Por qué esta opción?". Barras horizontales de la matriz ponderada:
- Distribuida **4,20** (resaltada en verde)
- Asistida 3,45
- Por lotes 3,25

**Texto visible:** "Estudiantes catalogan · la bibliotecaria valida · el lector y la app aceleran"

---

## Diapositiva 4. Normativa
**Título:** Cumplir la ley mientras se acelera
**Mensaje clave:** La biblioteca maneja datos de menores y datos sensibles; cada cambio debe protegerlos.

**Diagrama: de riesgo a control.** Cuatro filas, cada una con un riesgo a la izquierda (en rojo apagado), una flecha y su control a la derecha (en verde):

| Riesgo | Control |
|---|---|
| Cuentas compartidas en Koha | Una cuenta por persona, con permisos mínimos |
| Estudiantes con acceso a datos de menores | Perfil de catalogador sin acceso a usuarios + compromiso de confidencialidad |
| Formulario en cuenta no institucional | Formulario en cuenta institucional |
| Terceros sin evidencia de cifrado ni respaldos | Solicitud formal a Biteca e IDECUT |

**Franja superior:** el marco legal, en tres etiquetas: **Ley 1581 de 2012** (datos personales, menores y datos sensibles), **Ley 1379 de 2010** (catálogo público) y "Responsable: entidad pública → riesgo disciplinario (Procuraduría)".

**Un sello de "ya logrado":** "Aviso de privacidad implementado en el formulario, 1 oct. 2026".

**Texto visible:** "Ley 1581 · Ley 1379 · cuatro riesgos, cuatro controles"

---

## Diapositiva 5. Plan de implementación
**Título:** Un plan con fechas
**Mensaje clave:** Lo urgente y barato primero; en junio de 2027 la solución completa está funcionando.

**Diagrama: línea de tiempo simplificada** (resume el roadmap del plan). Eje horizontal de septiembre de 2026 a junio de 2027, con **dos líneas verticales punteadas**: "Fin quick wins · 1 ene 2027" y "Fin corto plazo · 1 jun 2027". Cuatro bloques:
1. **Sep–nov 2026 · En curso:** app de catalogación, prototipo y piloto (en gris, "ya avanzado").
2. **Dic 2026 · Quick wins:** respaldo 3-2-1, lector de ISBN y solicitudes a Biteca e IDECUT.
3. **Ene 2027:** cuentas individuales y perfil de catalogador.
4. **Feb–may 2027:** catalogación distribuida + conexión de la app al Koha real (con borde punteado: "si hay autorización").

**Pie:** "Mediano y largo plazo: sin actividades pendientes."

**Texto visible:** "Dic: quick wins · Ene: cuentas · Feb–May: catalogación distribuida"

---

## (Opcional) Cierre y demo
Si sobra tiempo, una lámina con el título "Prototipo de la app de catalogación", el texto "demostración contra un Koha de pruebas" y espacio para cambiar a la demo en vivo.
