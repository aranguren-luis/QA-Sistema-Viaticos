**Plan de Pruebas: ExpenseFlow **

| Versión del Documento | 1.0 |
| --- | --- |
| Fecha | 2026-03-20 |
| Autor | Luis Aranguren (Analista QA) |
| Proyecto | ExpenseFlow |

**1. Introducción**

Este documento describe el plan de pruebas para las nuevas funcionalidades implementadas en ExpenseFlow. El objetivo es garantizar que todas las nuevas características funcionen según lo esperado, sean confiables y brinden una experiencia de usuario positiva.

El sistema ah agregado funcionalidades nuevas para la gestión de beneficios de hoteles, un sistema de notificaciones, un módulo de feedback de hoteles, un panel de gestión de departamentos, notificaciones push, bases para un sistema de presupuestos, importación masiva de hoteles, solución de zona horaria y diversas optimizaciones visuales y de filtros.

**2. Alcance**

**Dentro del alcance:**

**Características documentadas por el equipo de producto:**

Nuevos campos de beneficios para hoteles (desayuno, almuerzo, cena, estacionamiento, etc.).

Sistema de notificaciones por correo electrónico para aprobación de viáticos.

Sistema de feedback de hoteles (calificación por estrellas y observaciones).

Nuevo sistema de departamentos (incluyendo integración con la base de datos de Profit).

Sistema de notificaciones push (a través de la página de Filament).

Sistema de presupuestos (bases iniciales).

**Características documentadas por el equipo de producto (continuación):**

Importación masiva de hoteles (asistente con archivo Excel).

Solución de zona horaria (hora de Venezuela).

Mejoras visuales (nombre de quien aprueba , nombre del hotel en la tabla).

Optimización de filtros (múltiples supervisores, múltiples departamentos, búsqueda por Local/Foráneo, inclusión del día de hoy en rangos de fecha).

**Fuera del alcance:**

Pruebas de seguridad 

**3. Objetivos de las Pruebas**

**Funcionalidad:** Verificar que todas las nuevas características operan según las especificaciones.

**Integración:** Asegurar que el nuevo sistema de departamentos sincroniza correctamente con la base de datos externa de Profit.

**Usabilidad:** Confirmar que los nuevos elementos visuales (botones, tablas) son intuitivos y que los nuevos filtros son fáciles de usar.

**Confiabilidad:** Validar que las notificaciones (correo y push) se activan y entregan de manera consistente.

**Integridad de datos:** Garantizar que los datos importados (masivamente) y los ingresados manualmente se guardan correctamente en la base de datos.

**4. Estrategia de Pruebas**

**Pruebas positivas:** Verificar que las funcionalidades trabajan con datos válidos.

**Pruebas negativas:** Intentar romper las funcionalidades con datos inválidos o inesperados (ej. importar un archivo Excel corrupto, enviar un feedback sin calificación).

**Pruebas de integración:** Probar la conexión entre el nuevo panel de departamentos y la base de datos externa de Profit.

**Pruebas de regresión:** Asegurar que las nuevas funcionalidades no afecten negativamente las características existentes del sistema.

**5. Entorno de Pruebas**

**Aplicación:** ExpenseFlow (basado en web).

**Navegador:** Google Chrome (última versión) 

**Sistema operativo:** Windows 10/11.

**Base de datos:** Base de datos local 

**Servicio de correo:** Un servidor de correo de prueba para capturar y verificar los correos sin enviar a destinatarios reales.

**6. Casos de ****Prueba**** :**** 24 en total **

**7. Criterios de Entrada y Salida**

**Criterios de entrada:**

Todas las funcionalidades de las Fases 1 y 2 han sido desplegadas en el entorno de pruebas.

El entorno de pruebas es estable y accesible.

Los datos de prueba necesarios (ej. archivos Excel, cuentas de usuario) han sido preparados.

**Criterios de salida:**

Se ha ejecutado el 100% de los casos de prueba planificados.

Todos los defectos de severidad **Crítica** y **Alta** han sido corregidos y verificados.

El informe de pruebas ha sido revisado y aprobado por el Líder de QA.

**8. Entregables**

Este documento de Plan de Pruebas.

Casos de prueba ejecutados (aprobados/fallidos) con reportes de defectos detallados.

Un informe resumen de pruebas con métricas de defectos y una evaluación general de la calidad.

**9****. ****Cuenta de Prueba ****
****
****
**** ExpenseFlow#2026*******
