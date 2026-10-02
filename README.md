<div align="center">

# QA · ExpenseFlow — Sistema de Gestión de Viáticos

**Documentación de QA manual: plan de pruebas, diseño de casos de prueba y ejecución de smoke test sobre un sistema web de gestión de viáticos corporativos**

![Manual Testing](https://img.shields.io/badge/Testing-Manual-3b82f6)
![Test Case Design](https://img.shields.io/badge/Test%20Case%20Design-CP--XX-0f2044)
![Markdown](https://img.shields.io/badge/Docs-Markdown-000000?logo=markdown&logoColor=white)
![License: MIT](https://img.shields.io/badge/License-MIT-green)

</div>

## Features

- Plan de pruebas formal: introducción, alcance, objetivos, estrategia y criterios de entrada/salida
- 30 casos de prueba detallados (`CP-01` a `CP-30`) con precondiciones, datos de prueba, pasos, resultado esperado/obtenido y observaciones
- Ejecución de smoke test documentada sobre 32 casos, con triage de severidad y hallazgo crítico (`504 Gateway Timeout`)
- Portal estático en GitHub Pages para navegar los 3 documentos sin salir del navegador

## Metodología QA

Este repositorio es una muestra de portafolio de **QA manual / documentación de pruebas** — no contiene código ni automatización. Demuestra el proceso completo de diseño y ejecución de pruebas sobre un sistema real:

| Etapa | Qué incluye |
| --- | --- |
| Planificación | Plan de pruebas con alcance (10 funcionalidades nuevas), objetivos (funcionalidad, integración, usabilidad, confiabilidad, integridad de datos) y estrategia (pruebas positivas, negativas, de integración y de regresión) |
| Diseño de casos | 30 casos de prueba en formato `CP-XX`, cada uno con plataforma, precondiciones, datos de prueba, pasos numerados y resultado esperado explícito |
| Ejecución (smoke test) | Corrida de 32 casos sobre el ambiente de pruebas, clasificados en Correcto / Fallido / Bloqueado, con evidencia y observaciones por caso |
| Triage de defectos | Clasificación de hallazgos por severidad (ej. error crítico de `504 Gateway Timeout` que bloquea la creación de solicitudes; inconsistencias de idioma inglés/español en la interfaz) |

## Project Structure

```
QA-Sistema-Viaticos/
├── docs/                                  # GitHub Pages (rama main, carpeta /docs)
│   ├── index.html                         # Landing page con las 3 tarjetas de navegación
│   ├── plan-de-pruebas.html                # Plan de pruebas renderizado
│   ├── casos-de-prueba.html                # Casos de prueba renderizados
│   └── reporte-smoke-test.html             # Reporte de smoke test renderizado
├── reports/                                # Fuente en Markdown (contenido original)
│   ├── plan-de-pruebas-expenseflow.md
│   ├── casos-de-prueba-expenseflow.md
│   └── reporte-smoke-test-expenseflow.md
└── LICENSE
```

## Cobertura de Pruebas

| Documento | Métrica | Valor |
| --- | --- | --- |
| Plan de Pruebas | Funcionalidades nuevas en alcance | 10 (beneficios de hoteles, notificaciones por correo, feedback de hoteles, departamentos con integración a Profit, notificaciones push, presupuestos, importación masiva de hoteles, zona horaria, mejoras visuales, optimización de filtros) |
| Plan de Pruebas | Casos de prueba planificados | 24 |
| Casos de Prueba | Casos de prueba diseñados | 30 (`CP-01` a `CP-30`) |
| Casos de Prueba | Resultado (regresión) | 22 Correctos / 6 Fallidos / 2 Bloqueados |
| Reporte Smoke Test | Casos ejecutados | 32 |
| Reporte Smoke Test | Resultado | 11 Correcto / 6 Fallido / 14 Bloqueado |

> El número de casos creció entre la planificación (24) y el diseño detallado (30), y la corrida de smoke test cubrió casos adicionales (32) sumados durante la ejecución — reflejo normal de cómo evoluciona el alcance real de pruebas frente al plan inicial.

## Cómo Navegar este Portafolio

Este repositorio no tiene código para ejecutar: es documentación de QA manual en Markdown, publicada como HTML estático vía GitHub Pages.

```bash
git clone https://github.com/aranguren-luis/QA-Sistema-Viaticos.git
cd QA-Sistema-Viaticos
```

- Los documentos fuente están en [`reports/`](reports/) en formato Markdown.
- La versión navegable está publicada en GitHub Pages — ver tabla de [Documentación](#documentación) abajo.

## Using with Claude Code

Este repositorio es documentación pura (sin código fuente), por lo que no incluye un `CLAUDE.md` de contexto de desarrollo — los 3 reportes en `reports/` son autoexplicativos y pueden leerse directamente.

## Documentación

| Documento | Enlace |
| --- | --- |
| Portal (índice) | https://aranguren-luis.github.io/QA-Sistema-Viaticos/ |
| Plan de Pruebas | https://aranguren-luis.github.io/QA-Sistema-Viaticos/plan-de-pruebas.html |
| Casos de Prueba | https://aranguren-luis.github.io/QA-Sistema-Viaticos/casos-de-prueba.html |
| Reporte Smoke Test | https://aranguren-luis.github.io/QA-Sistema-Viaticos/reporte-smoke-test.html |

## Notas Técnicas

- El hallazgo más severo de la corrida de smoke test fue un `504 Gateway Timeout` al crear una solicitud de viáticos, que bloqueó en cascada la ejecución de varios casos dependientes (cálculo de logística, flujo de aprobación, zona horaria).
- Se documentaron inconsistencias de idioma (textos y alertas mezclando inglés y español) como hallazgo transversal a múltiples módulos, no acotado a una sola pantalla.
- Varios casos quedaron en estado "Bloqueado" por dependencias no disponibles en el ambiente de pruebas (ej. envío real de correos vía integración con Profit, plantilla de Excel para importación masiva de usuarios).
- Las observaciones de cada caso incluyen sugerencias de mejora de UX incluso cuando el resultado fue "Correcto" (ej. agregar buscador de usuarios, validar duplicados en tipos de trámite), siguiendo una práctica de QA que va más allá del binario pasa/falla.

---

<div align="center">

QA Engineering · Manual Testing · Test Case Design · Bug Triage

</div>
