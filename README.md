# Arquitectura Empresarial — Biblioteca Municipal "Rubiel Valencia Cossio"
 
**Equipo:** ARQUITECH · Jorge Alarcon, Julian Aguirre, Brayan Presiga
**Curso:** Arquitectura Empresarial 2026-II — Universidad de La Sabana
 
---
 
## 📌 En una frase
 
Proponemos que la Biblioteca Municipal de Cogua termine de registrar su colección en el catálogo en línea repartiendo el trabajo entre su equipo, mientras protege sus archivos y los datos de sus usuarios.
 
## 🩺 El problema
 
La biblioteca debe registrar más de 8.000 libros y otros materiales en su nuevo sistema de catálogo. Hoy el catálogo en línea y la aplicación para usuarios ya existen, pero solo muestran cerca del 10 % de la colección; el resto se consulta en una hoja de cálculo. El registro se hace título por título y depende de una sola persona, la bibliotecaria, que además atiende el resto de la operación con el apoyo de dos estudiantes de servicio social.
 
A esto se suman otras dificultades:
 
- Cada usuario nuevo se inscribe dos veces, en dos sistemas distintos que no se comunican entre sí.
- Los archivos de eventos, talleres y recursos de la biblioteca existen en una sola copia, en el computador de la bibliotecaria.
- Las cuentas del sistema de catálogo se comparten entre la bibliotecaria y los estudiantes, así que no se sabe quién hizo cada cambio y todos tienen acceso a los datos personales de los usuarios, incluidos menores de edad.
## 💡 Lo que proponemos
 
- **Repartir el registro de la colección:** los estudiantes de servicio social se encargan de registrar el material, cada uno con su propia cuenta y acceso solo a lo que necesita; la bibliotecaria pasa de digitar a revisar una muestra.
- **Registrar más rápido y con menos errores:** leer el código del libro en lugar de digitar sus datos, para que cada título tome menos tiempo.
- **Proteger los archivos de la biblioteca:** mantener tres copias de los archivos de trabajo, una de ellas fuera de la biblioteca, para que un daño o un robo del computador no signifique perderlos.
- **Cuidar los datos de los usuarios:** que cada persona tenga su propia cuenta, que se sepa quién hace cada cambio y que solo la bibliotecaria vea la información personal de los usuarios.
- **Una segunda fase, si el proveedor la habilita:** cargar el material por lotes para cerrar el catálogo mucho más rápido.
## 🗺️ Cómo se implementa
 
La implementación avanza de lo más urgente y económico a lo que depende de terceros:
 
1. **Primero, acciones rápidas y de bajo costo:** las copias de seguridad de los archivos y la lectura del código de los libros. La biblioteca puede hacerlas por su cuenta.
2. **Luego, el registro compartido de la colección:** crear las cuentas individuales de los estudiantes, darles una inducción y un compromiso de confidencialidad, y empezar a catalogar.
3. **Después, la carga por lotes:** solo si el proveedor del sistema de catálogo habilita el acceso necesario.
4. **En paralelo, los pendientes con entidades externas:** el formulario de inscripción, el doble registro de usuarios y la continuidad cuando falla internet, que dependen del proveedor y de la red nacional de bibliotecas.


Ver el **[Resumen Ejecutivo](resumen-ejecutivo.md)** — ahí está el detalle de beneficios esperados, fases de implementación y tiempos, en un solo documento pensado para el negocio, no para el equipo técnico.
 
## 📂 Si quiere ver el detalle técnico completo

Todo el análisis que sustenta esta propuesta está documentado carpeta por carpeta, siguiendo el método usado durante el proyecto:

| Carpeta | Qué contiene |
|---|---|
| `00-preliminary-vision/` | Contexto del cliente y visión de la solución |
| `01-bpmn/` | Cómo funciona hoy el proceso de negocio analizado |
| `02-modelo-informacion/` | Qué información maneja el negocio y cómo fluye |
| `03-arquitectura-c4/` | Los sistemas actuales y cómo están construidos |
| `04-infraestructura/` | Dónde corre todo hoy y qué riesgos técnicos tiene |
| `05-seguridad-stride/` | Análisis de seguridad de la información |
| `06-normatividad/` | Cumplimiento legal y normativo |
| `07-opportunities-solutions/` | La solución propuesta y qué brechas cierra |
| `08-integracion-vistas/` | Cómo se conecta todo lo anterior en una sola arquitectura |
| `09-presentacion-final/` | Presentación ejecutiva, plan de implementación y gobernanza |

## 👥 Contacto

Ana Cecilia Pastrana Rodriguez - bibliotecarubielvalencia@gmail.com
