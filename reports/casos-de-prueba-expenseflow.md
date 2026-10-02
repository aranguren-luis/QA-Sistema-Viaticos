# Casos de Prueba — ExpenseFlow (Test de Regresión)

**Resumen de Casos de Prueba — Test de Regresión**

| Estado | Cantidad |
| --- | --- |
| Correctos | 22 |
| Fallidos | 6 |
| Bloqueo | 2 |
| Total de Casos | 30 |

| Implementación nueva | Test case | Status |
| --- | --- | --- |
| Nuevos campos de beneficios para hoteles (desayuno, almuerzo, cena, estacionamiento, etc.) | CP-23: Visualización de tabla de hoteles<br>CP-24: Creación de lista de hoteles (con toggles de beneficios)<br>CP-26: Edición de hotel: activar/desactivar beneficios | Correcto |
| Sistema de notificaciones por correo electrónico para aprobación de viáticos | CP-27: Envío de correo electrónico al crear solicitud de viático | Bloqueado |
| Sistema de feedback de hoteles (calificación por estrellas y observaciones) | CP-29: Acceso al formulario de valoración de hotel desde solicitud aprobada | Correcto (con observaciones) |
| Nuevo sistema de departamentos (incluyendo integración con Profit) | CP-11: Visualización de tabla de departamentos<br>CP-12: Creación de un nuevo departamento | Correcto |
| Sistema de notificaciones push | CP-28: Envío y recepción de notificación push | Fallido |
| Sistema de presupuestos (budget) | CP-13: Asignación de presupuesto (Budget) a un departamento desde edición | Fallido |
| Importación masiva de hoteles (asistente con archivo Excel) | CP-25: Carga masiva de hoteles desde archivo Excel | Fallido |
| Solución de zona horaria (hora de Venezuela) | — | Correcto |
| Mejoras visuales (nombre de quien aprueba, nombre del hotel en la tabla) | — | Correcto |
| Optimización de filtros (múltiples supervisores, múltiples departamentos, búsqueda por Local/Foráneo, inclusión del día de hoy en rangos de fecha) | CP-09: Reportes | Correcto (con observaciones) |

---

## Cuentas de Prueba

- ANALIST1
- qa.tester@example.com (cuenta de prueba creada)
- Solicitante@example.com
- supervisor@example.com — Contraseña: ExpenseFlow#2026

---

## Matriz Detallada de Casos de Prueba

| ID | Descripción | Resultado Esperado | Resultado Obtenido | Estado |
| --- | --- | --- | --- | --- |
| CP-01 | Verificar que un usuario registrado pueda iniciar sesión correctamente utilizando credenciales válidas. | El sistema permite el acceso y redirige al usuario al Dashboard mostrando el contenido correspondiente al perfil autenticado. | Carga correctamente al Dashboard. | Correcto |
| CP-02 | Verificar que al acceder al Dashboard se muestren los indicadores KPI "Aprobados", "Por aprobar" y "Rechazados" y los datos del usuario correctamente. | Se visualizan los tres KPI con sus respectivos valores. | El KPI "Aprobados" no filtra correctamente al redirigir y las siglas del usuario son incorrectas. | Fallido |
| CP-03 | Validar que el Dashboard muestre una gráfica histórica de viáticos por día. | Se muestra una gráfica con información histórica de viáticos clasificada. | Gráfica con información histórica de viáticos clasificada. | Correcto |
| CP-04 | Verificar que el botón "Actualizar contraseña" despliegue el formulario para cambiar la contraseña del usuario. | Se muestra el formulario para actualizar la contraseña. | Se muestra el formulario para actualizar la contraseña. | Correcto |
| CP-05 | Verificar que el botón "Salir" (Logout) cierre la sesión actual y redirija al usuario a la pantalla de inicio de sesión. | El usuario es desconectado y llevado a la pantalla de login. | El usuario es desconectado y llevado a la pantalla de login. | Correcto |
| CP-06 | Verificar que la tabla de "Aprobación de Viáticos" muestre correctamente las opciones de estado y permita exportar los datos a Excel. | La tabla muestra correctamente los estados: "Rechazados", "Cancelados", "Por aprobar analista", "Aprobado por sup. y analista". | La tabla muestra correctamente los estados indicados. | Correcto |
| CP-07 | Validar que al seleccionar un viático de la tabla se muestren correctamente los detalles y las observaciones de la solicitud. | Se despliegan los detalles y observaciones específicos del viático seleccionado. | Se despliegan los detalles y observaciones específicos del viático seleccionado. | Correcto |
| CP-08 | Verificar que el usuario puede crear correctamente una solicitud de viáticos llenando todos los campos requeridos. | La solicitud es creada exitosamente; se muestra un mensaje de confirmación y la solicitud aparece en la lista. | La solicitud es creada exitosamente; se muestra un mensaje de confirmación y la solicitud aparece en la lista. | Correcto |
| CP-09 | Verificar que el módulo de Reportes muestre la tabla de solicitudes de viáticos clasificadas por estado. | La tabla muestra, de manera diferenciada, las solicitudes en estado "sin aprobar", "aprobados" y "rechazados". | La tabla muestra los tres estados correctamente, pero el filtro de selectores presenta fallas. | Correcto (requiere ajuste en selectores) |
| CP-10 | Verificar que "Histórico de actualización de viáticos" muestre la tabla con las columnas correspondientes. | La tabla se despliega correctamente con las columnas especificadas. | Se observa toda la información de los viáticos realizados y se aplican las opciones de filtro. | Correcto |
| CP-11 | Verificar que "Ajustes Departamentos" muestre una tabla con las columnas correspondientes. | La tabla muestra correctamente las columnas: código, departamento, supervisor y presupuesto total. | La tabla muestra correctamente las columnas indicadas. | Correcto |
| CP-12 | Verificar que el usuario puede crear un nuevo departamento llenando todos los campos requeridos. | El departamento es registrado y aparece en la tabla. | Se crea correctamente el departamento nuevo. | Correcto |
| CP-13 | Verificar la funcionalidad de asignación de "Budget" o presupuesto específico a un departamento. | El presupuesto es asignado exitosamente al departamento. | Fallo al crear Budget. | Fallido |
| CP-14 | Verificar que "Tipo de trámites" visualice una tabla con las columnas correspondientes. | La tabla muestra correctamente columnas para "Tipo de trámite" y "Fecha de creación". | Se puede crear correctamente el trámite. | Correcto |
| CP-15 | Verificar que "Usuarios" muestre una tabla con las columnas correspondientes. | La tabla muestra correctamente los campos cédula, nombre, apellido, empresa, departamento y rol. | La tabla muestra correctamente los campos solicitados. | Correcto |
| CP-16 | Verificar que, al editar un usuario, se despliega un formulario donde se puede modificar rol e información. | Se actualiza la información del usuario y se refleja en la tabla. | Se actualiza la información del usuario y se refleja en la tabla. | Correcto |
| CP-17 | Verificar que el formulario de creación de usuario permite ingresar todos los campos requeridos. | El usuario se agrega y aparece en la tabla. | El usuario se agrega y aparece en la tabla. | Correcto |
| CP-18 | Validar que un usuario con rol "admin" pueda crear un nuevo rol y guardar exitosamente. | Se guarda el nuevo rol correctamente y se muestra un mensaje de éxito. | Alerta de error; la aplicación se rompe. | Fallido |
| CP-19 | Verificar que la importación de usuarios vía Excel permite cargar, revisar y editar antes de confirmar. | Recepción de correo tras la importación. | No implementado. | Bloqueado |
| CP-20 | Validar que el usuario puede crear un nuevo tipo de trámite. | El nuevo tipo de trámite se guarda correctamente y es visible en la tabla. | El nuevo tipo de trámite se guarda correctamente y es visible en la tabla. | Correcto |
| CP-21 | Verificar que "Zonas" muestre una tabla con las columnas correspondientes. | La tabla muestra correctamente las columnas "Zona" y "Fecha de creación". | La tabla muestra correctamente las columnas solicitadas. | Correcto |
| CP-22 | Validar la creación de una nueva zona mediante el formulario correspondiente. | La zona es creada correctamente y aparece en la tabla de zonas. | La zona es creada correctamente y aparece en la tabla de zonas. | Correcto |
| CP-23 | Verificar que "Hoteles" despliegue una tabla con las columnas correspondientes. | La tabla muestra correctamente los campos de zona, hotel, dirección y beneficios. | La tabla muestra correctamente los campos solicitados. | Correcto |
| CP-24 | Validar la creación de lista de hoteles con todos los campos requeridos. | El hotel se registra correctamente y aparece en la tabla general. | El hotel se registra correctamente y aparece en la tabla general. | Correcto |
| CP-25 | Validar el flujo de carga masiva de hoteles desde archivo Excel. | Los hoteles del archivo aparecen en la tabla tras la carga masiva. | Fallo al adjuntar archivo. | Fallido |
| CP-26 | Verificar que se puedan activar y desactivar beneficios de un hotel existente. | Los cambios se guardan correctamente y se reflejan en la tabla. | Edición de beneficios correcta. | Correcto |
| CP-27 | Verificar que al crear una solicitud de viático se envíen correos de notificación al analista y al supervisor. | El analista y el supervisor reciben el correo de notificación. | No es posible verificar la recepción del correo en el ambiente de prueba. | Bloqueado |
| CP-28 | Verificar que se puedan enviar y recibir notificaciones push. | La notificación push aparece en la interfaz del usuario destinatario. | No se observó envío ni recepción de notificaciones push. | Fallido |
| CP-29 | Verificar que el botón para valorar un hotel esté visible y accesible desde una solicitud aprobada. | Se abre un modal o formulario que permite calificar el hotel. | Función activa, pero accesible también en solicitudes no aprobadas o sin hotel registrado. | Correcto (con observaciones) |
| CP-30 | Verificar que al crear un usuario con correo ya registrado se muestre una alerta clara y no se permita la creación. | Mensaje de error claro; no se crea el usuario. | Sin alerta; la aplicación se rompe y sale del formulario. | Fallido |

---

## Detalle de Casos de Prueba

#### CP-01 — Inicio de sesión exitoso en la plataforma de viáticos

| Campo | Detalle |
| --- | --- |
| **Plataforma** | Web |
| **Precondiciones** | El usuario debe estar previamente registrado y su cuenta debe estar activa. |
| **Datos de Prueba** | Correo electrónico: Solicitante@example.com<br>Contraseña: ExpenseFlow#2026 |
| **Pasos** | 1. Acceder a la URL https://expenseflow.example.com/admin/login.<br>2. Introducir el correo electrónico.<br>3. Introducir la contraseña.<br>4. Hacer clic en el botón Entrar. |
| **Resultado Esperado** | El sistema permite el acceso y redirige al usuario al Dashboard mostrando el contenido correspondiente al perfil autenticado. |
| **Resultado Obtenido** | Carga correctamente al Dashboard. |
| **Estado** | Correcto |
| **Observaciones** | Ver BUG-001 (la persistencia de sesión no depende de la opción "Recuérdame"). |

#### CP-02 — Visualización correcta de los KPIs en el Dashboard / Datos Usuario

| Campo | Detalle |
| --- | --- |
| **Plataforma** | Web |
| **Precondiciones** | Usuario autenticado en la plataforma y en la sección Dashboard. |
| **Datos de Prueba** | Sesión iniciada con un usuario válido. |
| **Pasos** | 1. Observar el área de indicadores KPI. |
| **Resultado Esperado** | Se visualizan los tres KPI: "Aprobados", "Por aprobar" y "Rechazados" con sus respectivos valores. |
| **Resultado Obtenido** | Al hacer clic en los KPI "Rechazados" y "Por aprobar" redirige correctamente a la tabla filtrada por esos valores; esto no ocurre para "Aprobados" (redirige a `https://expenseflow.example.com/admin/aprobacion-viaticos?activeTab=Todos` en vez de filtrar por el estado correspondiente). Además, las siglas del usuario mostradas son incorrectas: en lugar de tomar la primera letra del nombre y del apellido, toma las dos primeras letras del nombre. |
| **Estado** | Fallido |
| **Observaciones** | Ver BUG-002 (filtro del KPI "Aprobados") y BUG-003 (siglas de usuario incorrectas). |

#### CP-03 — Visualización de gráfica histórica de viáticos por día

| Campo | Detalle |
| --- | --- |
| **Plataforma** | Web |
| **Precondiciones** | Usuario autenticado y ubicado en el Dashboard. |
| **Datos de Prueba** | Sesión iniciada con historial de viáticos registrado. |
| **Pasos** | 1. Ingresar al Dashboard.<br>2. Buscar la sección "Histórico" y visualizar la gráfica de viáticos por día. |
| **Resultado Esperado** | Se muestra una gráfica con información histórica de viáticos clasificada. |
| **Resultado Obtenido** | Gráfica con información histórica de viáticos clasificada. |
| **Estado** | Correcto |
| **Observaciones** | NA |

#### CP-04 — Funcionamiento del botón "Actualizar contraseña" en el Dashboard

| Campo | Detalle |
| --- | --- |
| **Plataforma** | Web |
| **Precondiciones** | Usuario autenticado y ubicado en el Dashboard. |
| **Datos de Prueba** | Usuario con perfil editable. |
| **Pasos** | 1. Ingresar al Dashboard.<br>2. Hacer clic en el botón "Actualizar contraseña". |
| **Resultado Esperado** | Se muestra el formulario para actualizar la contraseña. |
| **Resultado Obtenido** | Se muestra el formulario para actualizar la contraseña. |
| **Estado** | Correcto |
| **Observaciones** | NA |

#### CP-05 — Funcionamiento del botón "Salir" (Logout) en el Dashboard

| Campo | Detalle |
| --- | --- |
| **Plataforma** | Web |
| **Precondiciones** | Usuario autenticado y ubicado en el Dashboard. |
| **Datos de Prueba** | Sesión iniciada. |
| **Pasos** | 1. Ingresar al Dashboard.<br>2. Hacer clic en el botón "Salir". |
| **Resultado Esperado** | El usuario es desconectado y llevado a la pantalla de login. |
| **Resultado Obtenido** | El usuario es desconectado y llevado a la pantalla de login. |
| **Estado** | Correcto |
| **Observaciones** | Pendiente verificar que la sesión se cierre correctamente y que no se pueda volver al Dashboard con el botón de atrás del navegador. |

#### CP-06 — Visualización de opciones de estado en la tabla de Aprobación de Viáticos

| Campo | Detalle |
| --- | --- |
| **Plataforma** | Web |
| **Precondiciones** | Usuario autenticado con permisos para acceder al módulo de aprobación de viáticos. |
| **Datos de Prueba** | Viáticos registrados previamente en diferentes estados. |
| **Pasos** | 1. Hacer clic en la sección "Aprobación de viáticos" desde el menú principal.<br>2. Observar la tabla y sus opciones de filtro o visualización. |
| **Resultado Esperado** | La tabla muestra correctamente los estados: "Rechazados", "Cancelados", "Por aprobar analista", "Aprobado por sup. y analista". |
| **Resultado Obtenido** | La tabla muestra correctamente los estados: "Rechazados", "Cancelados", "Por aprobar analista", "Aprobado por sup. y analista". |
| **Estado** | Correcto |
| **Observaciones** | NA |

#### CP-07 — Revisión de detalles y observaciones de una solicitud de viático

| Campo | Detalle |
| --- | --- |
| **Plataforma** | Web |
| **Precondiciones** | Usuario autenticado. Viáticos cargados en la tabla. |
| **Datos de Prueba** | Un viático seleccionable con detalles y observaciones registrados. |
| **Pasos** | 1. En la pantalla de tabla de aprobación de viáticos, hacer clic en algún registro de viático.<br>2. Observar los detalles y el campo de observaciones de la solicitud. |
| **Resultado Esperado** | Se despliegan los detalles y observaciones específicos del viático seleccionado. |
| **Resultado Obtenido** | Se despliegan los detalles y observaciones específicos del viático seleccionado. |
| **Estado** | Correcto |
| **Observaciones** | NA |

#### CP-08 — Creación exitosa de una solicitud de viáticos con todos los campos y opciones

| Campo | Detalle |
| --- | --- |
| **Plataforma** | Web |
| **Precondiciones** | Usuario autenticado en la plataforma. Permisos para crear solicitudes de viático. |
| **Datos de Prueba** | Solicitante: "Equipo Thomas"<br>Tipo de trámite<br>Fecha de salida<br>Fecha de retorno<br>Acompañante<br>Incluirme: Toggle en "Sí"<br>Observaciones/resumen<br>Desea agregar más información: Toggle en "Sí" |
| **Pasos** | 1. Hacer clic en la sección "Solicitud de viáticos" desde el menú principal.<br>2. Hacer clic en el botón "Crear solicitud de viáticos".<br>3. Llenar el formulario con la información indicada en los Datos de Prueba.<br>4. Usar el toggle "Incluirme" y establecerlo en "Sí".<br>5. Ingresar el resumen en observaciones, verificando que no exceda los 50 caracteres.<br>6. Usar el toggle "Desea agregar más información" y establecerlo en "No".<br>7. Guardar o enviar la solicitud. |
| **Resultado Esperado** | La solicitud es creada exitosamente; se muestra un mensaje de confirmación y la solicitud aparece en la lista de solicitudes. |
| **Resultado Obtenido** | La solicitud es creada exitosamente; se muestra un mensaje de confirmación y la solicitud aparece en la lista de solicitudes. |
| **Estado** | Correcto |
| **Observaciones** | Ver BUG-004 (el campo "Tasa BCV" no se repuebla al borrarlo) y BUG-005 (el selector de hotel queda vacío para la zona/ciudad seleccionada). |

#### CP-09 — Visualización de solicitudes de viáticos en el módulo de Reportes

| Campo | Detalle |
| --- | --- |
| **Plataforma** | Web |
| **Precondiciones** | Usuario autenticado en la plataforma. Existencia de solicitudes de viáticos en los estados "sin aprobar", "aprobados" y "rechazados". |
| **Datos de Prueba** | Solicitudes de viáticos previamente registradas en distintos estados. |
| **Pasos** | 1. Hacer clic en la sección "Reportes" desde el menú principal.<br>2. Observar la tabla principal que contiene las solicitudes de viáticos. |
| **Resultado Esperado** | La tabla muestra, de manera diferenciada, las solicitudes de viáticos en estado "sin aprobar", "aprobados" y "rechazados", permitiendo visualizarlos correctamente. |
| **Resultado Obtenido** | La tabla muestra, de manera diferenciada, las solicitudes en los tres estados solicitados; sin embargo, el selector de filtro permite seleccionar 2 o 3 opciones a la vez, el filtro de "Tipo de trámite" no contempla todos los tipos existentes, y el filtro de Departamento no se refleja en la tabla. |
| **Estado** | Correcto (requiere ajuste en selectores) |
| **Observaciones** | Ver BUG-006 (selector múltiple selecciona 2-3 opciones a la vez), BUG-007 (filtro "Tipo de trámite" no incluye Jornada especial/Otros) y BUG-008 (filtro de Departamento no se aplica en la tabla). [enlace de grabación interno omitido] |

#### CP-10 — Visualización correcta del histórico de actualización de viáticos

| Campo | Detalle |
| --- | --- |
| **Plataforma** | Web |
| **Precondiciones** | Usuario autenticado en la plataforma. Existen registros de actualizaciones sobre solicitudes de viáticos en el sistema. |
| **Datos de Prueba** | Actualizaciones de solicitudes de viáticos previamente realizadas por diferentes usuarios y con diferentes fechas/estados. |
| **Pasos** | 1. Hacer clic en la sección "Histórico de actualización de viáticos" desde el menú principal.<br>2. Visualizar la tabla que muestra el histórico de actualizaciones. |
| **Resultado Esperado** | La tabla se despliega correctamente y contiene las columnas: autorizado por, modificación de status, fecha de actualización, fecha de salida, fecha de retorno y observaciones. |
| **Resultado Obtenido** | Se observa toda la información de los viáticos realizados y se aplican las opciones de filtro. |
| **Estado** | Correcto |
| **Observaciones** | NA |

#### CP-11 — Visualización de la tabla de departamentos en Ajustes

| Campo | Detalle |
| --- | --- |
| **Plataforma** | Web |
| **Precondiciones** | Usuario autenticado con permisos de administración. Departamentos registrados previamente en el sistema. |
| **Datos de Prueba** | Múltiples departamentos cargados con código, nombre, supervisor asignado y presupuesto total. |
| **Pasos** | 1. Hacer clic en la sección "Ajustes Departamentos" desde el menú.<br>2. Visualizar la tabla principal de departamentos. |
| **Resultado Esperado** | La tabla muestra correctamente las columnas: código, departamento, supervisor, y presupuesto total para cada registro. |
| **Resultado Obtenido** | La tabla muestra correctamente las columnas: código, departamento, supervisor, y presupuesto total para cada registro. |
| **Estado** | Correcto |
| **Observaciones** | NA |

#### CP-12 — Creación de un nuevo departamento

| Campo | Detalle |
| --- | --- |
| **Plataforma** | Web |
| **Precondiciones** | Usuario autenticado con permisos de creación. |
| **Datos de Prueba** | Código Profit Interno: "DPTO-PRUEBA-01"<br>Nombre del departamento<br>Supervisor |
| **Pasos** | 1. Hacer clic en "Ajustes Departamentos".<br>2. Hacer clic en el botón "Crear Departamento".<br>3. Llenar los campos: Código Profit Interno y Nombre del departamento.<br>4. Asignar supervisor de sede/área en el correspondiente campo.<br>5. Elegir una de las opciones de guardar: "Crear", "Crear y crear otro" o cancelar la operación. |
| **Resultado Esperado** | Si se elige "Crear" o "Crear y crear otro", el departamento es registrado y aparece en la tabla; si se cancela, no se registra ningún dato. |
| **Resultado Obtenido** | Se crea correctamente el departamento nuevo. |
| **Estado** | Correcto |
| **Observaciones** | NA |

#### CP-13 — Asignación de presupuesto (Budget) a un departamento desde edición

| Campo | Detalle |
| --- | --- |
| **Plataforma** | Web |
| **Precondiciones** | Usuario autenticado con permiso de edición sobre departamentos. Departamento previamente creado y visible en la tabla. |
| **Datos de Prueba** | Monto a asignar: 500,000 |
| **Pasos** | 1. En la tabla de departamentos, hacer clic en el botón "Crear Budget" para un departamento.<br>2. Se despliega el campo "amount".<br>3. Ingresar el monto deseado y confirmar con el botón "Crear". |
| **Resultado Esperado** | El presupuesto es asignado exitosamente al departamento; se actualiza la información y muestra mensaje de éxito. |
| **Resultado Obtenido** | Fallo al crear Budget. |
| **Estado** | Fallido |
| **Observaciones** | Ver BUG-009. Se recomienda además que el campo "amount" no acepte valores no numéricos o negativos. |

#### CP-14 — Visualización de la tabla de tipo de trámites – Creación

| Campo | Detalle |
| --- | --- |
| **Plataforma** | Web |
| **Precondiciones** | Usuario autenticado con acceso a la sección correspondiente. Existe al menos un tipo de trámite previamente registrado en el sistema. |
| **Datos de Prueba** | Tipos de trámite de ejemplo: "Comisión", "Capacitación" (con sus fechas de creación). |
| **Pasos** | 1. Hacer clic en la opción "Tipo de trámites" en el menú.<br>2. Observar la tabla que se presenta en pantalla. |
| **Resultado Esperado** | La tabla muestra correctamente columnas para "Tipo de trámite" y "Fecha de creación" con datos válidos. |
| **Resultado Obtenido** | Se puede crear correctamente el trámite. |
| **Estado** | Correcto |
| **Observaciones** | Ver BUG-010 (ausencia de validación para evitar tipos de trámite duplicados). |

#### CP-15 — Visualización de la tabla de usuarios

| Campo | Detalle |
| --- | --- |
| **Plataforma** | Web |
| **Precondiciones** | Usuario autenticado con permisos para ver usuarios. Usuarios registrados previamente en el sistema. |
| **Datos de Prueba** | NA |
| **Pasos** | 1. Hacer clic en "Usuarios" en el menú principal.<br>2. Observar la tabla presentada en pantalla. |
| **Resultado Esperado** | La tabla muestra correctamente los campos cédula, nombre, apellido, empresa, departamento y rol para cada usuario registrado. |
| **Resultado Obtenido** | La tabla muestra correctamente los campos cédula, nombre, apellido, empresa, departamento y rol para cada usuario registrado. |
| **Estado** | Correcto |
| **Observaciones** | Se propone agregar un buscador para los usuarios (mejora sugerida, no bloqueante). |

#### CP-16 — Edición de usuario

| Campo | Detalle |
| --- | --- |
| **Plataforma** | Web |
| **Precondiciones** | Usuario autenticado con permisos administrador. Usuario existente en el sistema. |
| **Datos de Prueba** | NA |
| **Pasos** | 1. En la lista de usuarios, hacer clic en el botón de editar correspondiente.<br>2. Guardar los cambios. |
| **Resultado Esperado** | Se actualiza la información del usuario y se refleja en la tabla. |
| **Resultado Obtenido** | Se actualiza la información del usuario y se refleja en la tabla. |
| **Estado** | Correcto |
| **Observaciones** | NA |

#### CP-17 — Creación de un usuario nuevo

| Campo | Detalle |
| --- | --- |
| **Plataforma** | Web |
| **Precondiciones** | Usuario autenticado con permiso para crear usuarios. |
| **Datos de Prueba** | Nombre: "Luis"<br>Apellido: "Gómez"<br>Cédula: "45678901"<br>Rol: "Operador"<br>Empresa: "BetaCorp"<br>Departamento: "Logística"<br>Email: "luis.gomez@betacorp.com"<br>Contraseña: "LuisGomez2026*" |
| **Pasos** | 1. Hacer clic en "Usuarios".<br>2. Hacer clic en el botón "Crear usuario".<br>3. Completar todos los campos del formulario según los datos de prueba.<br>4. Probar las siguientes opciones: a) Clic en "Crear". b) Clic en "Crear y crear otro". c) Clic en "Cancelar". |
| **Resultado Esperado** | El usuario se agrega y aparece en la tabla. |
| **Resultado Obtenido** | El usuario se agrega y aparece en la tabla. |
| **Estado** | Correcto |
| **Observaciones** | NA |

#### CP-18 — Creación de nuevo rol específico por parte de un Usuario admin

| Campo | Detalle |
| --- | --- |
| **Plataforma** | Web |
| **Precondiciones** | Usuario con rol "Super Usuario" ha iniciado sesión en el sistema. |
| **Pasos** | 1. En el menú lateral, ir a Ajustes > Usuarios.<br>2. Hacer clic en el botón "+ Agregar Nuevo" (o "Crear").<br>3. Hacer clic en el botón "Crear" (o "Crear y crear otro" según se requiera).<br>4. Observar el mensaje de éxito y verificar el nuevo rol en el listado. |
| **Resultado Esperado** | Al hacer clic en "Crear", se guarda el nuevo rol correctamente y se muestra un mensaje de éxito. |
| **Resultado Obtenido** | Alerta de error; la aplicación se rompe. |
| **Estado** | Fallido |
| **Observaciones** | Ver BUG-011. La aplicación se rompe sin mostrar una alerta de error clara al usuario. |

#### CP-19 — Importación masiva de usuarios desde archivo Excel

| Campo | Detalle |
| --- | --- |
| **Plataforma** | Web |
| **Precondiciones** | Usuario autenticado con permisos para importación. Archivo Excel válido con datos de usuarios estructurados correctamente. |
| **Datos de Prueba** | Plantilla Excel con campos para la creación de usuario |
| **Pasos** | 1. Hacer clic en "Usuarios".<br>2. Hacer clic en el botón "Import".<br>3. Seleccionar el archivo "usuarios_import.xlsx".<br>4. Hacer clic en "Siguiente".<br>5. Revisar la previsualización; editar registros si es posible.<br>6. Confirmar la importación. |
| **Resultado Esperado** | Recepción de correo tras la importación. |
| **Resultado Obtenido** | NA |
| **Estado** | Bloqueado |
| **Observaciones** | Ver BUG-012 (limitación: funcionalidad no implementada, no se cuenta con una plantilla de Excel específica). |

#### CP-20 — Creación de un nuevo tipo de trámite

| Campo | Detalle |
| --- | --- |
| **Plataforma** | Web |
| **Precondiciones** | Usuario autenticado con permisos. |
| **Datos de Prueba** | Tipo de trámite: "Prueba" |
| **Pasos** | 1. Hacer clic en "Tipo de trámites" en el menú.<br>2. Hacer clic en el botón "Crear tipo de trámite".<br>3. Llenar el campo Tipo de trámite, seleccionar Traslado Foráneo o Local.<br>4. Guardar la información. |
| **Resultado Esperado** | El nuevo tipo de trámite se guarda correctamente y es visible en la tabla junto con la fecha de creación. |
| **Resultado Obtenido** | El nuevo tipo de trámite se guarda correctamente y es visible en la tabla junto con la fecha de creación. |
| **Estado** | Correcto |
| **Observaciones** | NA |

#### CP-21 — Visualización de la tabla de zonas

| Campo | Detalle |
| --- | --- |
| **Plataforma** | Web |
| **Precondiciones** | Usuario autenticado con acceso a la sección. Al menos una zona registrada previamente en el sistema. |
| **Datos de Prueba** | NA |
| **Pasos** | 1. Hacer clic en el menú "Zonas".<br>2. Observar la tabla presentada. |
| **Resultado Esperado** | La tabla muestra correctamente las columnas "Zona" y "Fecha de creación" con datos válidos y correctamente alineados. |
| **Resultado Obtenido** | La tabla muestra correctamente las columnas "Zona" y "Fecha de creación" con datos válidos y correctamente alineados. |
| **Estado** | Correcto |
| **Observaciones** | NA |

#### CP-22 — Creación de una nueva zona

| Campo | Detalle |
| --- | --- |
| **Plataforma** | Web |
| **Precondiciones** | Usuario autenticado con permisos de creación para esta sección. |
| **Datos de Prueba** | Zona: "Prueba"<br>Descripción: "Prueba" |
| **Pasos** | 1. Hacer clic en "Zonas".<br>2. Hacer clic en el botón "Crear Zona".<br>3. Completar los campos: Zona y Descripción.<br>4. Hacer clic en "Crear". |
| **Resultado Esperado** | La zona es creada correctamente y aparece en la tabla de zonas. |
| **Resultado Obtenido** | La zona es creada correctamente y aparece en la tabla de zonas. |
| **Estado** | Correcto |
| **Observaciones** | Pendiente verificar la validación de campos obligatorios, mensajes de éxito y el correcto refresco de la tabla. |

#### CP-23 — Visualización de la tabla de hoteles

| Campo | Detalle |
| --- | --- |
| **Plataforma** | Web |
| **Precondiciones** | Usuario autenticado. Al menos un hotel registrado en el sistema. |
| **Datos de Prueba** | NA |
| **Pasos** | 1. Hacer clic en "Hoteles" en el menú principal.<br>2. Observar la tabla desplegada. |
| **Resultado Esperado** | La tabla muestra correctamente los campos de zona, hotel, dirección y beneficios para cada registro disponible. |
| **Resultado Obtenido** | La tabla muestra correctamente los campos de zona, hotel, dirección y beneficios para cada registro disponible. |
| **Estado** | Correcto |
| **Observaciones** | NA |

#### CP-24 — Creación de lista de hoteles

| Campo | Detalle |
| --- | --- |
| **Plataforma** | Web |
| **Precondiciones** | Usuario autenticado con permiso. Zonas previamente registradas para selección. |
| **Datos de Prueba** | Zona<br>Nombre hotel<br>Razón social<br>Dirección<br>Número de teléfono<br>Número local<br>Datos bancarios<br>Beneficios<br>Tarifas |
| **Pasos** | 1. Hacer clic en "Hoteles".<br>2. Hacer clic en "Crear lista de hoteles".<br>3. Desplegar y completar todos los campos del formulario.<br>4. Hacer clic en el botón "Crear". |
| **Resultado Esperado** | El hotel se registra correctamente y aparece en la tabla general, mostrando todos los campos, incluidas las tarifas y beneficios seleccionados. |
| **Resultado Obtenido** | El hotel se registra correctamente y aparece en la tabla general, mostrando todos los campos, incluidas las tarifas y beneficios seleccionados. |
| **Estado** | Correcto |
| **Observaciones** | Ver BUG-013 (alerta de validación requerida no traducida al español). |

#### CP-25 — Carga masiva de hoteles desde archivo Excel

| Campo | Detalle |
| --- | --- |
| **Plataforma** | Web |
| **Precondiciones** | Usuario autenticado. Archivo Excel con estructura válida y al menos 2 hoteles de ejemplo. |
| **Datos de Prueba** | Archivo Excel |
| **Pasos** | 1. Ir a "Hoteles".<br>2. Hacer clic en el botón "Carga Masiva".<br>3. Seleccionar el archivo "hoteles_ejemplo.xlsx" en el campo correspondiente.<br>4. Hacer clic en "Siguiente".<br>5. Confirmar la carga. |
| **Resultado Esperado** | Los hoteles en el archivo aparecen en la tabla tras la carga masiva, con la información correctamente distribuida en cada campo. |
| **Resultado Obtenido** | Fallo al adjuntar archivo. |
| **Estado** | Fallido |
| **Observaciones** | Ver BUG-014. |

#### CP-26 — Edición de hotel: activar y desactivar beneficios existentes

| Campo | Detalle |
| --- | --- |
| **Plataforma** | Web |
| **Precondiciones** | Existir un hotel con beneficios ya asignados. El usuario debe tener permisos de edición. |
| **Datos de Prueba** | Hotel con beneficios preexistentes (ej. "wifi" activado, "gimnasio" desactivado). |
| **Pasos** | 1. En el listado de hoteles, seleccionar un hotel que ya tenga algunos beneficios asignados.<br>2. Hacer clic en "Editar".<br>3. Activar un beneficio que antes no tenía.<br>4. Desactivar un beneficio que sí tenía.<br>5. Guardar los cambios.<br>6. Volver a la tabla de hoteles y verificar los beneficios mostrados. |
| **Resultado Esperado** | Los cambios se guardan correctamente. En la tabla, el hotel refleja el nuevo estado: el beneficio activado aparece, el desactivado desaparece. |
| **Resultado Obtenido** | Edición de beneficios correcta. |
| **Estado** | Correcto |
| **Observaciones** | Ver BUG-015. Para el filtrado de columnas mostrar/ocultar, solo se observan como opciones "Comentario estacionamiento" y "Personal"; se sugiere agregar el resto de opciones al filtrado. |

#### CP-27 — Envío de correo electrónico al crear solicitud de viático

| Campo | Detalle |
| --- | --- |
| **Plataforma** | Web |
| **Precondiciones** | Empleado con sesión activa cuyo departamento tenga un supervisor asignado. Tener un analista de viáticos configurado en el sistema. |
| **Datos de Prueba** | Usuario solicitante, supervisor asignado, analista de viáticos. |
| **Pasos** | 1. Iniciar sesión.<br>2. Crear una nueva solicitud de viático (completar todos los datos requeridos).<br>3. Guardar la solicitud.<br>4. Revisar la bandeja de entrada del analista de viáticos y del supervisor del departamento. |
| **Resultado Esperado** | El analista de viáticos y el supervisor reciben un correo electrónico con la información de la solicitud: nombre del solicitante, datos de las personas que viajan, y un botón que redirige a la página de revisión de viáticos. |
| **Resultado Obtenido** | No es posible verificar la recepción de correo ya que el sistema extrae la información de Profit y envía los correos directamente; ese flujo no está disponible en el ambiente de prueba. |
| **Estado** | Bloqueado |
| **Observaciones** | Ver BUG-016 (limitación de ambiente, no defecto funcional confirmado). |

#### CP-28 — Envío y recepción de notificación push

| Campo | Detalle |
| --- | --- |
| **Plataforma** | Web |
| **Precondiciones** | Usuarios con sesión activa. |
| **Datos de Prueba** | Usuario administrador, usuario destinatario (solicitante y supervisor). |
| **Pasos** | 1. Crear solicitud de viáticos.<br>2. Verificar notificación push por cada rol. |
| **Resultado Esperado** | La notificación push aparece en la interfaz del usuario destinatario. |
| **Resultado Obtenido** | Se crearon viáticos de prueba para las cuentas solicitante@example.com y supervisor@example.com. No se observó envío ni recepción de notificaciones push. |
| **Estado** | Fallido |
| **Observaciones** | Ver BUG-017. Se observó adicionalmente un error de notificación al rechazar una solicitud de viático (detalle no ampliado en la fuente original). |

#### CP-29 — Acceso al formulario de valoración de hotel desde solicitud aprobada

| Campo | Detalle |
| --- | --- |
| **Plataforma** | Web |
| **Precondiciones** | Existir una solicitud de viático en estado "Aprobada" que esté asociada a un hotel. |
| **Datos de Prueba** | Solicitud de viático aprobada con hotel registrado. |
| **Pasos** | 1. Como usuario, ingresar al módulo de solicitudes de viático.<br>2. Buscar una solicitud que ya esté aprobada.<br>3. Localizar el botón amarillo "Valorar Hotel".<br>4. Hacer clic en el botón. |
| **Resultado Esperado** | Se abre un modal o formulario que permite calificar el hotel. |
| **Resultado Obtenido** | Función de valoración activa; se puede registrar la valoración de hotel incluso en solicitudes aún sin aprobar o sin hotel registrado. |
| **Estado** | Correcto (con observaciones) |
| **Observaciones** | Ver BUG-018. Actualmente es posible valorar solicitudes que no cuentan con hotel registrado o que están canceladas; se sugiere restringir la valoración únicamente a solicitudes aprobadas con hotel registrado. |

#### CP-30 — Validación de correo duplicado en creación de usuario

| Campo | Detalle |
| --- | --- |
| **Plataforma** | Web |
| **Precondiciones** | Usuario con permisos de administración. |
| **Pasos** | 1. Navegar a Ajustes > Usuarios y hacer clic en "Crear usuario".<br>2. Completar todos los campos obligatorios: nombre, apellido, cédula, rol, empresa, departamento, correo electrónico, contraseña.<br>3. En el campo "Correo electrónico", ingresar "admin@admin.com".<br>4. Hacer clic en el botón Crear.<br>5. Observar el mensaje mostrado en pantalla. |
| **Resultado Esperado** | El sistema debe mostrar un mensaje de error indicando que el correo electrónico ya está registrado (ej. "El correo electrónico ya existe"). No debe permitirse la creación del usuario y el formulario debe permanecer en pantalla sin recargarse completamente (o con los datos ingresados). |
| **Resultado Obtenido** | Sin mensaje de alerta; la aplicación se rompe y sale del formulario. |
| **Estado** | Fallido |
| **Observaciones** | Ver BUG-019. |

---

## Registro de Hallazgos

19 hallazgos identificados en la corrida de regresión.

### BUG-001 — Persistencia de sesión no respeta la opción "Recuérdame"

| Campo | Detalle |
| --- | --- |
| **ID** | BUG-001 (caso CP-01) |
| **Descripción** | La sesión se mantiene al cerrar inesperadamente la página, independientemente de si la opción "Recuérdame" está marcada o no, lo que genera confusión sobre el comportamiento esperado de inicio de sesión. |
| **Severidad** | Media |
| **Pasos para Reproducir** | 1. Iniciar sesión sin marcar "Recuérdame".<br>2. Cerrar la página inesperadamente.<br>3. Volver a abrir la URL de la plataforma.<br>4. Observar que la sesión se mantiene activa igualmente. |
| **Estado** | Pendiente |

### BUG-002 — El KPI "Aprobados" no filtra correctamente al redirigir

| Campo | Detalle |
| --- | --- |
| **ID** | BUG-002 (caso CP-02) |
| **Descripción** | Al hacer clic en el KPI "Aprobados" del Dashboard, el sistema redirige a `aprobacion-viaticos?activeTab=Todos` en vez de filtrar la tabla por el estado "Aprobados", a diferencia de los KPI "Rechazados" y "Por aprobar" que sí filtran correctamente. |
| **Severidad** | Media |
| **Pasos para Reproducir** | 1. Iniciar sesión y acceder al Dashboard.<br>2. Hacer clic en el KPI "Aprobados".<br>3. Observar que la tabla resultante muestra la pestaña "Todos" en vez de filtrar por aprobados. |
| **Estado** | Pendiente |

### BUG-003 — Siglas del usuario incorrectas en el Dashboard

| Campo | Detalle |
| --- | --- |
| **ID** | BUG-003 (caso CP-02) |
| **Descripción** | Las siglas mostradas para el usuario toman las dos primeras letras del nombre, en vez de la primera letra del nombre y la primera letra del apellido. |
| **Severidad** | Baja |
| **Pasos para Reproducir** | 1. Iniciar sesión con un usuario que tenga nombre y apellido.<br>2. Observar el avatar/siglas del usuario en el Dashboard. |
| **Estado** | Pendiente |

### BUG-004 — El campo "Tasa BCV" no se repuebla tras borrarlo

| Campo | Detalle |
| --- | --- |
| **ID** | BUG-004 (caso CP-08) |
| **Descripción** | Al borrar el campo "Tasa BCV" en el formulario de creación de solicitud, el valor debería visualizarse nuevamente (recalcularse), pero actualmente queda vacío o en 0. |
| **Severidad** | Media |
| **Pasos para Reproducir** | 1. Iniciar creación de una solicitud de viáticos.<br>2. Ubicar el campo "Tasa BCV".<br>3. Borrar su contenido.<br>4. Observar que el campo queda vacío o en 0 en lugar de recalcularse. |
| **Estado** | Pendiente |

### BUG-005 — Selector de hotel vacío para la zona/ciudad seleccionada

| Campo | Detalle |
| --- | --- |
| **ID** | BUG-005 (caso CP-08) |
| **Descripción** | En el selector de zona con opciones correspondientes a ciudades, la opción de hotel se muestra vacía o como opcional, en vez de listar los hoteles disponibles para esa zona/ciudad. |
| **Severidad** | Media |
| **Pasos para Reproducir** | 1. Iniciar creación de una solicitud de viáticos.<br>2. Seleccionar una zona/ciudad en el formulario.<br>3. Observar el selector de hotel asociado. |
| **Estado** | Pendiente |

### BUG-006 — Selector de filtros múltiples en Reportes selecciona varias opciones a la vez

| Campo | Detalle |
| --- | --- |
| **ID** | BUG-006 (caso CP-09) |
| **Descripción** | El selector de filtros del módulo de Reportes selecciona 2 o 3 opciones a la vez en lugar de respetar la selección individual del usuario. |
| **Severidad** | Media |
| **Pasos para Reproducir** | 1. Acceder al módulo de Reportes.<br>2. Abrir cualquier selector de filtro de selección múltiple.<br>3. Seleccionar una sola opción.<br>4. Observar que el sistema marca 2 o 3 opciones simultáneamente. |
| **Estado** | Pendiente |

### BUG-007 — Filtro "Tipo de trámite" en Reportes no incluye todos los tipos existentes

| Campo | Detalle |
| --- | --- |
| **ID** | BUG-007 (caso CP-09) |
| **Descripción** | El filtro "Tipo de trámite" del módulo de Reportes únicamente contempla "Local" o "Foráneo" (tipo de traslado); tipos como "Jornada especial" u "Otros" no aparecen como opción de filtrado, lo que genera confusión sobre el propósito del filtro. |
| **Severidad** | Media |
| **Pasos para Reproducir** | 1. Acceder al módulo de Reportes.<br>2. Abrir el filtro "Tipo de trámite".<br>3. Verificar las opciones disponibles frente a los tipos de trámite reales configurados en el sistema (Comisión, Capacitación, Jornada especial, Otros, etc.). |
| **Estado** | Pendiente |

### BUG-008 — Filtro de Departamento no se aplica en la tabla de Reportes

| Campo | Detalle |
| --- | --- |
| **ID** | BUG-008 (caso CP-09) |
| **Descripción** | Al aplicar el filtro de Departamento en el módulo de Reportes, el criterio no se refleja en la tabla de resultados. |
| **Severidad** | Alta |
| **Pasos para Reproducir** | 1. Acceder al módulo de Reportes.<br>2. Aplicar un filtro por Departamento.<br>3. Observar que la tabla no refleja el filtrado aplicado. |
| **Estado** | Pendiente |

### BUG-009 — Fallo al crear Budget (presupuesto) para un departamento

| Campo | Detalle |
| --- | --- |
| **ID** | BUG-009 (caso CP-13) |
| **Descripción** | Al intentar asignar un presupuesto ("Budget") a un departamento desde la edición, la operación falla y no se asigna el monto ni se muestra un mensaje de éxito. |
| **Severidad** | Alta |
| **Pasos para Reproducir** | 1. Acceder a la tabla de departamentos.<br>2. Hacer clic en "Crear Budget" para un departamento.<br>3. Ingresar un monto (ej. 500,000) y confirmar con "Crear".<br>4. Observar que la operación falla ("Fallo al crear Budget"). |
| **Estado** | Pendiente |

### BUG-010 — Ausencia de validación para evitar tipos de trámite duplicados

| Campo | Detalle |
| --- | --- |
| **ID** | BUG-010 (caso CP-14) |
| **Descripción** | El sistema permite crear tipos de trámite con el mismo nombre de uno ya existente, sin mostrar una validación que impida el duplicado. |
| **Severidad** | Baja |
| **Pasos para Reproducir** | 1. Acceder a "Tipo de trámites".<br>2. Crear un tipo de trámite con un nombre ya existente.<br>3. Observar que el sistema permite el registro sin alertar sobre el duplicado. |
| **Estado** | Pendiente |

### BUG-011 — Creación de nuevo rol rompe la aplicación sin mostrar alerta de error

| Campo | Detalle |
| --- | --- |
| **ID** | BUG-011 (caso CP-18) |
| **Descripción** | Al intentar crear un nuevo rol desde Ajustes > Usuarios como usuario "Super Usuario"/admin, la aplicación se rompe (falla) sin desplegar una alerta de error clara para el usuario. |
| **Severidad** | Alta |
| **Pasos para Reproducir** | 1. Iniciar sesión con un usuario con rol "Super Usuario".<br>2. Ir a Ajustes > Usuarios.<br>3. Hacer clic en "+ Agregar Nuevo" (crear rol).<br>4. Hacer clic en "Crear".<br>5. Observar que la aplicación se rompe sin una alerta de error clara. |
| **Estado** | Pendiente |

### BUG-012 — Importación masiva de usuarios desde Excel no implementada

| Campo | Detalle |
| --- | --- |
| **ID** | BUG-012 (caso CP-19) |
| **Descripción** | La funcionalidad de importación masiva de usuarios desde un archivo Excel no está implementada; además, no existe una plantilla de Excel específica para esta importación. Se clasifica como limitación de la implementación actual, no como una falla transitoria. |
| **Severidad** | Media |
| **Pasos para Reproducir** | 1. Acceder a "Usuarios".<br>2. Hacer clic en el botón "Import".<br>3. Intentar seguir el flujo de importación.<br>4. Confirmar que no hay plantilla ni funcionalidad disponible. |
| **Estado** | Pendiente |

### BUG-013 — Alerta de validación al crear hotel no está traducida al español

| Campo | Detalle |
| --- | --- |
| **ID** | BUG-013 (caso CP-24) |
| **Descripción** | Al completar el formulario de "Crear lista de hoteles", una alerta de validación requerida se muestra en un idioma distinto al español configurado en la interfaz. |
| **Severidad** | Baja |
| **Pasos para Reproducir** | 1. Acceder a "Hoteles" > "Crear lista de hoteles".<br>2. Dejar sin completar un campo requerido y continuar.<br>3. Observar el idioma de la alerta de validación mostrada. |
| **Estado** | Pendiente |

### BUG-014 — Carga masiva de hoteles falla al adjuntar archivo Excel

| Campo | Detalle |
| --- | --- |
| **ID** | BUG-014 (caso CP-25) |
| **Descripción** | Al intentar adjuntar el archivo Excel para la carga masiva de hoteles, la operación falla, impidiendo completar el flujo de importación. |
| **Severidad** | Alta |
| **Pasos para Reproducir** | 1. Ir a "Hoteles" > "Carga Masiva".<br>2. Seleccionar el archivo "hoteles_ejemplo.xlsx".<br>3. Hacer clic en "Siguiente".<br>4. Observar el fallo al adjuntar el archivo. |
| **Estado** | Pendiente |

### BUG-015 — Filtro de columnas mostrar/ocultar en Hoteles expone solo una parte de los beneficios

| Campo | Detalle |
| --- | --- |
| **ID** | BUG-015 (caso CP-26) |
| **Descripción** | El filtro para mostrar u ocultar columnas de beneficios en la tabla de Hoteles solo expone las opciones "Comentario estacionamiento" y "Personal", sin incluir el resto de los beneficios configurables (desayuno, almuerzo, cena, wifi, gimnasio, etc.). |
| **Severidad** | Baja |
| **Pasos para Reproducir** | 1. Acceder a la tabla de Hoteles.<br>2. Abrir el filtro de columnas mostrar/ocultar.<br>3. Observar que solo aparecen 2 opciones de beneficios disponibles para filtrar. |
| **Estado** | Pendiente |

### BUG-016 — No es posible verificar el envío de correo al crear solicitud de viático en el ambiente de prueba

| Campo | Detalle |
| --- | --- |
| **ID** | BUG-016 (caso CP-27) |
| **Descripción** | El envío de notificación por correo al analista de viáticos y al supervisor depende de información extraída de Profit y se dispara directamente desde ese flujo, el cual no está disponible en el ambiente de prueba. Se clasifica como limitación de ambiente, no como defecto funcional confirmado. |
| **Severidad** | No aplica (limitación de ambiente) |
| **Pasos para Reproducir** | 1. Crear una solicitud de viático con un departamento que tenga supervisor asignado.<br>2. Revisar la bandeja de entrada del analista de viáticos y del supervisor.<br>3. Confirmar que no se puede validar el envío en este ambiente. |
| **Estado** | Bloqueado |

### BUG-017 — Notificaciones push no se envían ni se reciben

| Campo | Detalle |
| --- | --- |
| **ID** | BUG-017 (caso CP-28) |
| **Descripción** | Al crear solicitudes de viáticos de prueba para las cuentas solicitante y supervisor, no se observó envío ni recepción de notificaciones push en ninguno de los roles. |
| **Severidad** | Alta |
| **Pasos para Reproducir** | 1. Crear una solicitud de viáticos.<br>2. Verificar la notificación push en la cuenta del solicitante y del supervisor.<br>3. Confirmar que no llega ninguna notificación. |
| **Estado** | Pendiente |

### BUG-018 — Formulario de valoración de hotel accesible en solicitudes no aprobadas o sin hotel registrado

| Campo | Detalle |
| --- | --- |
| **ID** | BUG-018 (caso CP-29) |
| **Descripción** | Es posible registrar una valoración de hotel en solicitudes que no cuentan con hotel registrado o que están canceladas, cuando debería estar disponible únicamente para solicitudes ya aprobadas y con un hotel registrado asociado. |
| **Severidad** | Media |
| **Pasos para Reproducir** | 1. Ubicar una solicitud de viático no aprobada o sin hotel registrado.<br>2. Verificar si el botón "Valorar Hotel" está disponible.<br>3. Completar y enviar la valoración. |
| **Estado** | Pendiente |

### BUG-019 — Validación de correo duplicado rompe la aplicación sin mostrar alerta

| Campo | Detalle |
| --- | --- |
| **ID** | BUG-019 (caso CP-30) |
| **Descripción** | Al intentar crear un usuario con un correo electrónico ya registrado (admin@admin.com), el sistema no muestra ningún mensaje de alerta y la aplicación se rompe, saliendo del formulario. |
| **Severidad** | Alta |
| **Pasos para Reproducir** | 1. Ir a Ajustes > Usuarios > Crear usuario.<br>2. Completar todos los campos obligatorios usando un correo ya registrado (admin@admin.com).<br>3. Hacer clic en Crear.<br>4. Observar que no hay alerta y la aplicación sale del formulario. |
| **Estado** | Pendiente |
