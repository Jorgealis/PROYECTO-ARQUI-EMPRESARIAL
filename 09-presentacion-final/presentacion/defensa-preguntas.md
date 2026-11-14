# Preparación de la defensa — Preguntas del panel

**Equipo:** ARQUITECH · **Estado:** borrador del Punto 5 (30/10/2026). Respuestas basadas en la evidencia del proyecto, no en opinión.

## 1. La meta es ~3.000 libros en noviembre y el plan dura 6 meses. ¿Cómo cumplen?
**Evidencia:** cuenta de capacidad (plan de implementación) y R2 de la matriz de riesgos.
**Respuesta:** "Con el ritmo actual, de unos 200 libros al mes, no se llega a 3.000 en noviembre: faltan unos 1.850 libros, y al ritmo actual tomaría unos 9 meses. Por eso el plan fija una meta nueva: al menos 6.000 libros en Koha el 31 de mayo de 2027, con una meta mensual. Con 2 estudiantes de 5 horas semanales, a mano se llega a unos 300 libros al mes; la meta se alcanza porque desde marzo la app permite entre 1.150 y 1.350 libros al mes, unos 30 libros por hora por estudiante. El piloto de noviembre mide la velocidad real de la app y el comité revisa el avance cada semana."

## 2. Si la app de lotes es la que más reduce la carga, ¿por qué no empiezan por ella?
**Evidencia:** matriz de decisión del Taller 7 (distribuida 4,20; asistida 3,45; lotes 3,25); R9 y R10.
**Respuesta:** "La app depende de una autorización de Biteca o IDECUT que todavía no tenemos, y usar cookies de sesión sin ella sería actuar con la identidad de otro usuario. La catalogación distribuida no depende de nadie y cierra además las cuentas compartidas. No son excluyentes: el plan hace una primero y la otra después. Con los pesos que la bibliotecaria validó el 05/11 gana la distribuida, y aunque ella le diera mucho más peso a la eficiencia, la distribuida seguiría primera."

## 3. ¿Qué pasa si Biteca o IDECUT no autorizan conectar la app?
**Evidencia:** R9, R10, R13 y dependencias del plan.
**Respuesta:** "La app no se conecta al Koha real y el resto del plan sigue igual: respaldo, lector, cuentas individuales y catalogación distribuida no dependen de esa autorización. El prototipo, construido contra una instancia de pruebas, sirve de demostración para solicitarla. Lo que cambia es la meta, y el plan B ya lo dice con números: si la app llega en abril, en mayo habrá unos 4.950 libros y los 6.000 se alcanzan en junio; si nunca llega, se sigue a mano, unos 300 libros al mes, con unos 3.100 libros en mayo. La vía preferida es una credencial de servicio con permiso mínimo sobre la API de Koha; las cookies de sesión son solo la alternativa y exigen autorización escrita."

## 4. Con estudiantes rotativos, ¿cómo evitan errores y duplicados?
**Evidencia:** R6; un informe reciente señaló ~80 libros con errores y al menos un duplicado.
**Respuesta:** "El problema ya existe hoy: esta semana llegó un informe con unos 80 libros con errores, y al menos uno estaba duplicado. El plan lo atiende con el lector de ISBN (menos errores de digitación), el formato corto con campos obligatorios, la búsqueda del título antes de crear un registro, una guía de catalogación y la revisión semanal de una muestra por la bibliotecaria, con un informe de errores."

## 5. ¿Cómo protegen los datos de menores si los estudiantes catalogan?
**Evidencia:** R4 y R5; Taller 5 (STRIDE) y Taller 6 (ítems 9, 11, 13 y 14); Ley 1581.
**Respuesta:** "Hoy los estudiantes usan cuentas compartidas con permisos de edición y acceso a datos de menores. El plan crea cuentas individuales con un perfil de catalogador sin acceso a usuarios ni reportes, un compromiso de confidencialidad, inducción y baja de la cuenta al terminar el servicio social. Es la fase de Corto plazo, y la elegimos pronto porque R4 es prioridad 1 y su esfuerzo es bajo."

## 6. ¿Por qué aceptan el doble registro de usuarios?
**Evidencia:** R7 (Aceptar).
**Respuesta:** "La gobernación exige usar Koha y Llave del Saber, y la migración entre ambos sistemas está fuera de alcance, por lo que el equipo no puede eliminar la causa. Aceptarlo es una decisión registrada: se monitorea con un cruce periódico por número de documento."

## 7. ¿Los pesos de la matriz están validados? ¿El perfil restringido de Koha funciona?
**Evidencia:** supuestos del Taller 7.
**Evidencia adicional:** validación de pesos del 05/11/2026 (Taller 7, matriz de decisión).
**Respuesta:** "Los pesos sí: la bibliotecaria los validó el 05/11 sin cambios, y a petición suya el primer criterio se llama ahora eficiencia del proceso de catalogación. El perfil restringido todavía no está probado y lo decimos como supuesto. El perfil de catalogador se prueba en enero de 2027 con una cuenta de prueba; la documentación de Koha indica que los permisos se asignan por módulo."

## 8. ¿Cuánto cuesta?
**Evidencia:** supuestos del Taller 7 (costos por cotizar).
**Respuesta:** "El diseño prioriza el bajo costo: un lector de códigos de barras (compra pequeña), un disco externo y la nube institucional de la Alcaldía; el trabajo lo hace el servicio social existente. Los valores se cotizarán antes de ejecutar."

## 9. El Taller 8 dice que solo el 10 % de la colección está en el catálogo. ¿Por qué ustedes usan otra cifra?
**Evidencia:** datos actualizados de octubre de 2026 aportados por el equipo; Talleres 6, 7 y 8.
**Respuesta:** "Esa cifra era de cuando se hizo el Taller 6 y los talleres posteriores la repiten. Hoy hay unos 1.100 a 1.200 libros en Koha de una colección de 7.000 a 8.000, cerca del 15 %; al empezar el semestre eran 600 o 700. Usamos la cifra actualizada porque mide el avance real."

## Pendientes
- ~~Validar los pesos de la matriz de decisión con la bibliotecaria el jueves 05/11.~~ Hecho: validados sin cambios (Taller 7); respuestas 2 y 7 actualizadas.
- Verificar en `00-preliminary-vision/vision.md` del repositorio del proyecto si el Taller 0 tenía borrador de principios (hoy es un supuesto en el plan de gobernanza).
- Preguntar al profesor (31/10) si el avance ya realizado en la app cuenta para la evaluación.
- Probar el perfil de catalogador en la instancia de Koha de pruebas antes del 14/11 (refuerza la respuesta 7).
- Cotizar el lector de códigos de barras y la nube institucional.
