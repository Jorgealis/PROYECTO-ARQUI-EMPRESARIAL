<!--
Esta es la puerta de entrada de su repositorio. Complétela pensando en que la primera
persona que la abra puede ser alguien del área de negocio del cliente, no un técnico.
Evite jerga (TOGAF, ArchiMate, STRIDE, etc.) en esta parte — eso queda para las carpetas
técnicas de abajo.
-->

# Arquitectura Empresarial — Biblioteca Municipal "Rubiel Valencia Cossio"

**Equipo:** ARQUITECH · Jorge Alarcon, Julian Aguirre, Brayan Presiga
**Curso:** Arquitectura Empresarial 2026-II— Universidad de La Sabana

---

## 📌 En una frase

Proponemos una solucion para optimizar las tareas de la Biblioteca Municipal "Rubiel Valencia Cossio", facilitando conexion de plataformas, pagina web y experiencia de usuario.

## 🩺 El problema


Se tiene que alimentar un nuevo software de gestión (Koha) con más de 8000 ejemplares de libros y otros recursos, Se tiene tambien dos software de gestión de inventario que tienen que ser usados en paralelo para registrar a los nuevos afiliados y ser alimentados con los nuevos materiales de la biblioteca, junto con Falta de una plataforma digital para consultar información de la biblioteca, sus eventos e inventario de los recursos disponibles (actualmente excel).

## 💡 Lo que proponemos

[3-5 líneas o viñetas, en lenguaje de negocio, sin nombrar herramientas ni marcos técnicos. Ej:
- Integrar los tres sistemas para que la información del paciente se actualice en tiempo real en todos lados.
- Reforzar la protección de los datos clínicos según la normativa vigente.
- Un plan de implementación en fases, empezando por lo más urgente y de menor costo.]

## 🗺️ Cómo se implementa

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
