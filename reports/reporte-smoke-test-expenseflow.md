# Informe de Pruebas — ExpenseFlow (10.4.2026)

**Objetivo de las pruebas**

Verificar el correcto funcionamiento de los módulos que componen el sistema ExpenseFlow, asegurando que:

- Los flujos de creación, aprobación y cancelación de solicitudes operen según lo esperado.
- Los módulos administrativos (departamentos, usuarios, zonas, hoteles, tipos de trámite, presupuestos) permitan la gestión completa de los datos.
- Las integraciones (correos electrónicos, notificaciones push, sincronización con Profit) funcionen adecuadamente.
- Las validaciones (fechas, rangos de calificación, campos obligatorios, filtrado) se apliquen correctamente.

**Resumen de resultados**

| Estado | Cantidad |
| --- | --- |
| Correcto | 11 |
| Fallido | 6 |
| Bloqueado | 14 |
| Total, de casos | 32 |

---

## 1. Login

| ID | Descripción | Resultado Esperado | Resultado Obtenido | Estado |
| --- | --- | --- | --- | --- |
| CP01 | Verificar que un usuario registrado pueda iniciar sesión con credenciales válidas. | Redirección al Dashboard con contenido del perfil. | Carga correctamente al Dashboard. | Correcto |
| CP02 | Verificar que el botón "Salir" cierre la sesión y redirija al login. | Desconexión y redirección a pantalla de login; no se puede volver al Dashboard con el botón atrás. | Se realiza el logout; se observa la alerta del navegador "Estás a punto de enviar una información no segura". | Correcto |
| CP03 | Verificar que el botón "Actualizar contraseña" despliegue el formulario correspondiente. | Se muestra el formulario para actualizar la contraseña; validación de nueva contraseña de exactamente 9 caracteres, con letras, números y símbolos. | Funciona correctamente la validación de contraseña. | Correcto |

#### CP01 — Inicio de sesión exitoso

| Campo | Detalle |
| --- | --- |
| **Precondiciones** | Usuario registrado y cuenta activa. Credenciales: admin@admin.com / 123456 |
| **Pasos** | 1. Acceder a https://expenseflow.example.com/admin/login.<br>2. Introducir correo electrónico y contraseña.<br>3. Hacer clic en "Entrar". |
| **Resultado Esperado** | Redirección al Dashboard con contenido del perfil. |
| **Resultado Obtenido** | Carga correctamente al Dashboard. La sesión se mantiene al cerrar la página inesperadamente, independientemente de si se tiene marcada o no la opción "recuérdame". |
| **Captura** | NA |
| **Estado** | Correcto |
| **Observaciones** | Ver BUG-001. |

#### CP02 — Cierre de sesión (Logout)

| Campo | Detalle |
| --- | --- |
| **Precondiciones** | Usuario autenticado en el Dashboard. |
| **Pasos** | 1. Hacer clic en "Salir". |
| **Resultado Esperado** | Desconexión y redirección a pantalla de login; no se puede volver al Dashboard con el botón atrás. |
| **Resultado Obtenido** | Se realiza la acción de logout; se observa la alerta "Estás a punto de enviar una información no segura". |
| **Captura** | — |
| **Estado** | Correcto |
| **Observaciones** | Ver BUG-002. |

#### CP03 — Cambio de contraseña desde Dashboard

| Campo | Detalle |
| --- | --- |
| **Precondiciones** | Usuario autenticado. |
| **Pasos** | 1. En el Dashboard, hacer clic en "Actualizar contraseña". |
| **Resultado Esperado** | Se muestra el formulario para actualizar la contraseña y validación de nueva contraseña debe ser exactamente 9 caracteres, incluir letras, números y símbolos. |
| **Resultado Obtenido** | Funciona correctamente la validación de contraseña. |
| **Captura** | NA |
| **Estado** | Correcto |
| **Observaciones** | NA |

---

## 2. Administración – Aprobación de viáticos

| ID | Descripción | Resultado Esperado | Resultado Obtenido | Estado |
| --- | --- | --- | --- | --- |
| CP04 | Verificar que los indicadores "Aprobados", "Por aprobar" y "Rechazados" se muestren y redirijan correctamente. | Los valores son visibles. | No ejecutado. | Bloqueado |
| CP05 | Validar que la tabla muestre los estados "Rechazados", "Cancelados", "Por aprobar analista" y "Aprobado por sup. y analista", y permita exportar a Excel. | Tabla correcta, exportación funcional. | No ejecutado. | Bloqueado |
| CP06 | Verificar que al seleccionar un viático se muestren detalles y observaciones. | Se despliega el detalle con observaciones. | No ejecutado. | Bloqueado |
| CP07 | Validar que los filtros permitan selección múltiple (supervisores, departamentos, Local/Foráneo) y que el día de hoy se incluya en rangos de fecha. | Los listados muestran las solicitudes correctas. | No ejecutado. | Bloqueado |

#### CP04 — Visualización de KPIs en Dashboard

| Campo | Detalle |
| --- | --- |
| **Precondiciones** | Usuario autenticado, existencia de solicitudes. |
| **Pasos** | 1. Observar los tres KPI en el Dashboard.<br>2. Hacer clic en cada uno. |
| **Resultado Esperado** | Los valores son visibles. |
| **Resultado Obtenido** | NA |
| **Captura** | NA |
| **Estado** | Bloqueado |
| **Observaciones** | Ver BUG-003. |

#### CP05 — Tabla de aprobación de viáticos (estados y exportación)

| Campo | Detalle |
| --- | --- |
| **Precondiciones** | Usuario con permisos, solicitudes en diferentes estados. |
| **Pasos** | 1. Acceder a "Aprobación de viáticos".<br>2. Observar opciones de filtro y tabla.<br>3. Exportar selección múltiple a Excel. |
| **Resultado Esperado** | Tabla correcta, exportación funcional. |
| **Resultado Obtenido** | NA |
| **Captura** | NA |
| **Estado** | Bloqueado |
| **Observaciones** | Ver BUG-003. |

#### CP06 — Detalle y observaciones de una solicitud

| Campo | Detalle |
| --- | --- |
| **Precondiciones** | Solicitudes cargadas en la tabla. |
| **Pasos** | 1. Hacer clic en un registro de la tabla de aprobación. |
| **Resultado Esperado** | Se despliega el detalle con observaciones. |
| **Resultado Obtenido** | NA |
| **Captura** | NA |
| **Estado** | Bloqueado |
| **Observaciones** | Ver BUG-003. |

#### CP07 — Filtros optimizados (múltiples supervisores, múltiples departamentos, Local/Foráneo, rango de fechas con hoy)

| Campo | Detalle |
| --- | --- |
| **Precondiciones** | Usuario autenticado, solicitudes variadas. |
| **Pasos** | 1. Aplicar filtro por 2 supervisores.<br>2. Aplicar filtro por 3 departamentos.<br>3. Filtrar por "Foráneo".<br>4. Filtrar fecha desde "hoy" hasta "hoy". |
| **Resultado Esperado** | Los listados muestran las solicitudes correctas. |
| **Resultado Obtenido** | NA |
| **Captura** | NA |
| **Estado** | Bloqueado |
| **Observaciones** | Ver BUG-003. |

---

## 3. Gestión

### 3.1 Solicitud de viáticos

| ID | Descripción | Resultado Esperado | Resultado Obtenido | Estado |
| --- | --- | --- | --- | --- |
| CP08 | Crear solicitud con zona, fechas, tipo de trámite, al menos un empleado y envío (flujo wizard). | Solicitud creada con estado "Por Aprobar Supervisor". Correo enviado a analista y supervisor. | 504 Gateway Time-out. | Fallido |
| CP09 | Impedir envío cuando la fecha de salida es posterior a la fecha de retorno. | Validación impide el envío. Mensaje de error claro en español. | No ejecutado. | Bloqueado |
| CP10 | Calcular automáticamente la logística (alimentación, hospedaje, transporte) según tarifas de zona. | Alimentación/hospedaje/transporte calculados según tarifas. | Bloqueado por falla en CP08. | Bloqueado |
| CP11 | Validar las transiciones de estado del flujo de aprobación (workflow). | Cada acción cambia el estado correctamente y envía notificaciones. | No ejecutado. | Bloqueado |
| CP12 | Calificar hotel con estrellas (1-5) y observación desde una solicitud aprobada y finalizada. | Calificación guardada. | No ejecutado. | Bloqueado |
| CP13 | Verificar que las fechas registradas usen la hora de Venezuela (-4 UTC). | Se muestra el formato de hora correcto. | No ejecutado. | Bloqueado |

#### CP08 — Creación completa de solicitud (flujo wizard)

| Campo | Detalle |
| --- | --- |
| **Precondiciones** | Usuario logueado como solicitante. |
| **Pasos** | 1. Completar wizard (zona, fechas, tipo trámite).<br>2. Agregar al menos un empleado.<br>3. Enviar. |
| **Resultado Esperado** | Solicitud creada con estado "Por Aprobar Supervisor". Correo enviado a analista y supervisor. |
| **Resultado Obtenido** | 504 Gateway Time-out. |
| **Captura** | — |
| **Estado** | Fallido |
| **Observaciones** | Ver BUG-004. |

#### CP09 — Validación de fechas incorrectas (salida > retorno)

| Campo | Detalle |
| --- | --- |
| **Precondiciones** | Usuario autenticado. |
| **Pasos** | 1. Seleccionar fecha de salida posterior a fecha de retorno.<br>2. Intentar enviar. |
| **Resultado Esperado** | Validación impide el envío. Mensaje de error claro en español. |
| **Resultado Obtenido** | NA |
| **Captura** | NA |
| **Estado** | Bloqueado |
| **Observaciones** | Caso no ejecutado; ver BUG-004 (el fallo de CP08 condiciona la ejecución de la suite de este módulo). |

#### CP10 — Cálculo automático de logística (alimentación, hospedaje, transporte)

| Campo | Detalle |
| --- | --- |
| **Precondiciones** | Zona con costos configurados. |
| **Pasos** | 1. Crear solicitud con zona que tiene costos predefinidos.<br>2. Ver tabla de logística generada. |
| **Resultado Esperado** | Alimentación/hospedaje/transporte calculados según tarifas. |
| **Resultado Obtenido** | Bloqueado por falla en CP08. |
| **Captura** | N/A |
| **Estado** | Bloqueado |
| **Observaciones** | Ver BUG-004 (cascada explícita desde CP08). |

#### CP11 — Flujo de aprobación (workflow)

| Campo | Detalle |
| --- | --- |
| **Precondiciones** | Solicitud en estado correspondiente. |
| **Pasos** | No se pudo ejecutar; depende de contar con una solicitud creada (ver BUG-004). |
| **Resultado Esperado** | Cada acción cambia el estado correctamente y envía notificaciones. |
| **Resultado Obtenido** | NA |
| **Captura** | NA |
| **Estado** | Bloqueado |
| **Observaciones** | Ver BUG-004 (cascada probable desde CP08). |

#### CP12 — Valoración de hotel desde solicitud aprobada

| Campo | Detalle |
| --- | --- |
| **Precondiciones** | Solicitud aprobada y finalizada, asociada a un hotel. |
| **Pasos** | 1. Seleccionar estrellas. |
| **Resultado Esperado** | Calificación guardada. |
| **Resultado Obtenido** | NA |
| **Captura** | NA |
| **Estado** | Bloqueado |
| **Observaciones** | Ver BUG-004 (cascada probable desde CP08). |

#### CP13 — Zona horaria (hora Venezuela)

| Campo | Detalle |
| --- | --- |
| **Precondiciones** | Crear solicitud a las 2:00 PM UTC (10:00 AM VET). |
| **Pasos** | 1. Crear solicitud. |
| **Resultado Esperado** | Muestra el formato de hora correcto. |
| **Resultado Obtenido** | NA |
| **Captura** | NA |
| **Estado** | Bloqueado |
| **Observaciones** | Ver BUG-004 (cascada probable desde CP08). |

### 3.2 Reportes

| ID | Descripción | Resultado Esperado | Resultado Obtenido | Estado |
| --- | --- | --- | --- | --- |
| CP14 | Verificar que el módulo Reportes muestre la tabla clasificada por pestañas (sin aprobar, aprobadas, rechazadas). | Muestra solo las solicitudes del estado seleccionado. | No ejecutado. | Bloqueado |

#### CP14 — Visualización de solicitudes por estado (sin aprobar, aprobadas, rechazadas)

| Campo | Detalle |
| --- | --- |
| **Precondiciones** | Solicitudes en diferentes estados. |
| **Pasos** | 1. Acceder a "Reportes".<br>2. Hacer clic en la pestaña "Rechazados", etc. |
| **Resultado Esperado** | Muestra solo las solicitudes del estado seleccionado. |
| **Resultado Obtenido** | NA |
| **Captura** | Nota interna de redacción pendiente de mejora. |
| **Estado** | Bloqueado |
| **Observaciones** | Ver BUG-005. |

### 3.3 Histórico de actualización de viáticos

| ID | Descripción | Resultado Esperado | Resultado Obtenido | Estado |
| --- | --- | --- | --- | --- |
| CP15 | Verificar que la tabla muestre: autorizado por, modificación de status, fecha de actualización, fecha salida, fecha retorno, observaciones. | Tabla con las columnas especificadas. | Se muestra correctamente, con filtros aplicables. | Bloqueado* |

\* Inconsistencia en la fuente original: el "Resultado Obtenido" describe un comportamiento correcto, pero el campo "Estado" quedó registrado como "Bloqueado". Se preserva el valor tal como está documentado, sin asumir cuál de los dos campos es el correcto; se recomienda confirmar con el ambiente real antes de reclasificar este caso.

#### CP15 — Columnas del histórico

| Campo | Detalle |
| --- | --- |
| **Precondiciones** | Existen actualizaciones de solicitudes. |
| **Pasos** | 1. Ir a "Histórico de actualización de viáticos". |
| **Resultado Esperado** | Tabla con las columnas especificadas. |
| **Resultado Obtenido** | Se muestra correctamente, con filtros aplicables. |
| **Evidencia o captura** | Nota interna de redacción pendiente de mejora. |
| **Estado** | Bloqueado (ver nota de inconsistencia arriba) |
| **Observaciones** | NA |

### 3.4 Gastos de departamentos

Módulo completo bloqueado; no se registraron casos de prueba ejecutados en la fuente original.

---

## 4. Ajustes

### 4.1 Departamentos

| ID | Descripción | Resultado Esperado | Resultado Obtenido | Estado |
| --- | --- | --- | --- | --- |
| CP16 | Mostrar código, departamento, supervisor y presupuesto total. | Columnas correctas. | Correcto. | Correcto |
| CP17 | Crear departamento con código Profit, nombre, supervisor, presupuesto. | Departamento creado y visible en el listado. | No ejecutado. | Bloqueado |
| CP18 | Asignar monto presupuestario desde la edición del departamento. | Presupuesto asignado y actualizado en tabla. | No ejecutado. | Bloqueado |

#### CP16 — Visualización de tabla de departamentos

| Campo | Detalle |
| --- | --- |
| **Precondiciones** | Departamentos registrados. |
| **Pasos** | 1. Ir a "Ajustes → Departamentos". |
| **Resultado Esperado** | Columnas correctas. |
| **Resultado Obtenido** | Correcto. |
| **Captura** | Nota interna de redacción/traducción pendiente de mejora. |
| **Estado** | Correcto |
| **Observaciones** | NA |

#### CP17 — Creación de nuevo departamento

| Campo | Detalle |
| --- | --- |
| **Pasos** | 1. Clic en "Crear departamento".<br>2. Ingresar datos.<br>3. Guardar (opciones: Crear / Crear y crear otro / Cancelar). |
| **Resultado Esperado** | Departamento creado y visible en listado. |
| **Resultado Obtenido** | NA |
| **Captura** | NA |
| **Estado** | Bloqueado |
| **Observaciones** | Ver BUG-006. |

#### CP18 — Asignación de presupuesto (Budget) a un departamento

| Campo | Detalle |
| --- | --- |
| **Precondiciones** | Departamento existente. |
| **Pasos** | 1. Clic en "Crear Budget".<br>2. Ingresar monto (ej. 500,000).<br>3. Guardar. |
| **Resultado Esperado** | Presupuesto asignado y actualizado en tabla. |
| **Resultado Obtenido** | NA |
| **Captura** | NA |
| **Estado** | Bloqueado |
| **Observaciones** | Ver BUG-006. |

### 4.2 Tipo de trámites

| ID | Descripción | Resultado Esperado | Resultado Obtenido | Estado |
| --- | --- | --- | --- | --- |
| CP19 | La tabla debe mostrar "Tipo de trámite" y "Fecha de creación". | Columnas correctas. | Trámite creado correctamente. | Correcto |
| CP20 | Crear tipo de trámite con los campos "Tipo de trámite" y "Traslado" (Local/Foráneo). | Validación de campos obligatorios; el registro aparece en el listado; "Crear y crear otro" restablece el formulario. | Correcto; se creó el trámite con Traslado "Foráneo" y "Local". | Correcto (sugerencia: validación de duplicados) |

#### CP19 — Visualización de tabla de tipos de trámite

| Campo | Detalle |
| --- | --- |
| **Precondiciones** | Tipos de trámite existentes. |
| **Pasos** | 1. Ir a "Ajustes → Tipo de trámites". |
| **Resultado Esperado** | Columnas correctas. |
| **Resultado Obtenido** | Trámite creado correctamente. |
| **Captura** | NA |
| **Estado** | Correcto |
| **Observaciones** | NA |

#### CP20 — Creación de nuevo tipo de trámite

| Campo | Detalle |
| --- | --- |
| **Precondiciones** | Usuario con permisos. |
| **Pasos** | 1. Clic en "New tipo tramite".<br>2. Completar "Tipo de Trámite*" y "Traslado*".<br>3. Probar las 2 acciones de guardado. |
| **Resultado Esperado** | Validación de campos obligatorios. Al guardar, el registro aparece en el listado. La opción "Crear y crear otro" permite generar un nuevo trámite y restablece el formulario. |
| **Resultado Obtenido** | Correcto. Se creó el trámite con Traslado "Foráneo" y "Local". |
| **Captura** | Pendiente traducir alerta. |
| **Estado** | Correcto (sugerencia: agregar validación para evitar registros duplicados) |
| **Observaciones** | Ver BUG-007 (alerta no traducida) y BUG-008 (falta validación de duplicados). |

### 4.3 Usuarios

| ID | Descripción | Resultado Esperado | Resultado Obtenido | Estado |
| --- | --- | --- | --- | --- |
| CP21 | La tabla debe mostrar cédula, nombre, apellido, empresa, departamento y rol. | Columnas correctas. | Correcto; se sugiere agregar buscador. | Correcto |
| CP22 | Crear usuario con campos: Nombre*, Apellido*, Cédula, Rol, Empresa, Departamento*, Correo Electrónico, Contraseña*. | Usuario creado y visible en tabla; validación de campos obligatorios. | 504 Gateway Time-out. | Fallido |
| CP23 | Crear un nuevo rol de usuario desde Ajustes → Roles. | El rol se crea exitosamente. | Internal Server Error: "Select field [data.role_id] must have a [createOptionUsing()] closure set." | Fallido* |
| CP24 | Modificar rol u otros campos de un usuario existente. | Cambios guardados. | Correcto. | Correcto |
| CP25 | No permitir crear usuario con correo ya registrado. | Mensaje de error claro (ej. "El correo electrónico ya existe") y no se crea. | No ejecutado. | Bloqueado |

\* Estado no indicado explícitamente en la fuente original para CP23; se clasifica como "Fallido" por el Internal Server Error devuelto en el Resultado Obtenido.

#### CP21 — Visualización de tabla de usuarios

| Campo | Detalle |
| --- | --- |
| **Precondiciones** | Usuarios registrados. |
| **Pasos** | 1. Ir a "Ajustes → Usuarios". |
| **Resultado Esperado** | Columnas correctas. |
| **Resultado Obtenido** | Correcto. Se sugiere agregar buscador. |
| **Captura** | Pendiente traducir. |
| **Estado** | Correcto |
| **Observaciones** | Ver BUG-009 (encabezados no traducidos). Sugerencia de buscador registrada como mejora, no como defecto. |

#### CP22 — Creación de usuario

| Campo | Detalle |
| --- | --- |
| **Precondiciones** | Permisos de administración. |
| **Pasos** | 1. Clic en "Crear usuario".<br>2. Completar todos los campos.<br>3. Probar las tres acciones (Crear / Crear y crear otro / Cancelar). |
| **Resultado Esperado** | Usuario creado y visible en tabla; validación de campos obligatorios. |
| **Resultado Obtenido** | 504 Gateway Time-out. |
| **Captura** | — |
| **Estado** | Fallido |
| **Observaciones** | Ver BUG-010. |

#### CP23 — Crear nuevo rol

| Campo | Detalle |
| --- | --- |
| **Precondiciones** | Usuario autenticado con permisos de administrador. |
| **Pasos** | 1. Navegar a Ajustes → Roles.<br>2. Hacer clic en el botón "Crear rol" (o "Create").<br>3. Completar los campos obligatorios: Name* (ej. "QA"), Description* (ej. "ROL DE PRUEBA").<br>4. Hacer clic en el botón "Create" (o "Crear"). |
| **Resultado Esperado** | El rol se crea exitosamente. |
| **Resultado Obtenido** | Al intentar crear el rol, el sistema arroja error *Internal Server Error*: "Select field [data.role_id] must have a [createOptionUsing()] closure set." |
| **Captura** | — |
| **Estado** | Fallido (ver nota de inferencia arriba) |
| **Observaciones** | Ver BUG-011. |

#### CP24 — Edición de usuario

| Campo | Detalle |
| --- | --- |
| **Pasos** | 1. En listado, clic en "Edit".<br>2. Modificar datos.<br>3. Guardar. |
| **Resultado Esperado** | Cambios guardados. |
| **Resultado Obtenido** | Correcto. |
| **Captura** | Pendiente verificar si los datos se están guardando correctamente en la tabla. |
| **Estado** | Correcto |
| **Observaciones** | Verificación de persistencia de datos pendiente de confirmar (no se reporta como defecto confirmado). |

#### CP25 — Validación de correo duplicado en creación de usuario

| Campo | Detalle |
| --- | --- |
| **Precondiciones** | Existe usuario con correo admin@admin.com. |
| **Pasos** | 1. Crear nuevo usuario.<br>2. Ingresar admin@admin.com en campo Correo.<br>3. Intentar guardar. |
| **Resultado Esperado** | Mensaje de error claro (ej. "El correo electrónico ya existe") y no se crea. |
| **Resultado Obtenido** | NA |
| **Captura** | NA |
| **Estado** | Bloqueado |
| **Observaciones** | Ver BUG-012. |

### 4.4 Zonas

| ID | Descripción | Resultado Esperado | Resultado Obtenido | Estado |
| --- | --- | --- | --- | --- |
| CP26 | La tabla debe mostrar "Zona" y "Fecha de creación". | Columnas correctas. | Internal Server Error (500). | Fallido |
| CP27 | Crear zona con nombre y descripción. | Zona creada y visible en tabla; validación de campos obligatorios. | No ejecutado. | Bloqueado |

#### CP26 — Visualización de tabla de zonas

| Campo | Detalle |
| --- | --- |
| **Precondiciones** | Zonas registradas. |
| **Pasos** | 1. Ir a "Ajustes → Zonas". |
| **Resultado Esperado** | Columnas correctas. |
| **Resultado Obtenido** | Internal Server Error, status 500. |
| **Captura** | — |
| **Estado** | Fallido |
| **Observaciones** | Ver BUG-013. |

#### CP27 — Creación de nueva zona

| Campo | Detalle |
| --- | --- |
| **Pasos** | 1. Clic en "Crear Zona".<br>2. Completar "Zona" y "Descripción".<br>3. Guardar. |
| **Resultado Esperado** | Zona creada y visible en tabla; validación de campos obligatorios. |
| **Resultado Obtenido** | NA |
| **Captura** | NA |
| **Estado** | Bloqueado |
| **Observaciones** | Ver BUG-014 (posible cascada del error 500 de CP26, no confirmado explícitamente en la fuente). |

### 4.5 Hoteles

| ID | Descripción | Resultado Esperado | Resultado Obtenido | Estado |
| --- | --- | --- | --- | --- |
| CP28 | La tabla debe mostrar zona, hotel, dirección y beneficios (con íconos sí/no). | Columnas correctas y beneficios visibles. | No ejecutado. | Correcto |
| CP29 | Crear hotel con todos los campos: zona, datos generales, bancarios, beneficios (toggles), tarifas. | Hotel registrado, aparece en tabla con beneficios seleccionados. | Correcto. | Correcto |
| CP30 | Modificar beneficios de un hotel existente y ver reflejo en tabla. | Guardar edición. | Correcto, se sugiere que al editar y guardar los cambios se regrese al listado de hoteles; actualmente no se cierra el formulario de edición. | Correcto |
| CP31 | Subir archivo .xlsx con columnas correctas, revisar datos en wizard editable y confirmar importación. | Hoteles insertados en BD. Mensaje de error si columnas incorrectas. | No ejecutado. | No ejecutado |

#### CP28 — Visualización de tabla de hoteles

| Campo | Detalle |
| --- | --- |
| **Precondiciones** | Hoteles registrados. |
| **Pasos** | 1. Ir a "Ajustes → Hoteles". |
| **Resultado Esperado** | Columnas correctas y beneficios visibles. |
| **Resultado Obtenido** | NA |
| **Captura** | NA |
| **Estado** | Correcto |
| **Observaciones** | NA |

#### CP29 — Creación de hotel

| Campo | Detalle |
| --- | --- |
| **Pasos** | 1. Clic en "Crear lista de hoteles".<br>2. Completar formulario.<br>3. Guardar. |
| **Resultado Esperado** | Hotel registrado, aparece en tabla con beneficios seleccionados. |
| **Resultado Obtenido** | Correcto. |
| **Captura** | — |
| **Estado** | Correcto |
| **Observaciones** | NA |

#### CP30 — Edición de hoteles (activar/desactivar beneficios)

| Campo | Detalle |
| --- | --- |
| **Pasos** | 1. Editar un hotel.<br>2. Activar un beneficio nuevo, desactivar uno existente.<br>3. Guardar. |
| **Resultado Esperado** | Guardar edición. |
| **Resultado Obtenido** | Correcto; se sugiere que al editar y guardar los cambios se regrese al listado de hoteles. Actualmente no se cierra el formulario de edición. |
| **Evidencia o captura** | NA |
| **Estado** | Correcto |
| **Observaciones** | Ver BUG-015. |

#### CP31 — Importación masiva de hoteles desde Excel

| Campo | Detalle |
| --- | --- |
| **Precondiciones** | Archivo Excel válido. |
| **Pasos** | 1. Ir a "Importar Hoteles".<br>2. Subir archivo.<br>3. Revisar y editar datos si es necesario.<br>4. Confirmar. |
| **Resultado Esperado** | Hoteles insertados en BD. Mensaje de error si columnas incorrectas. |
| **Resultado Obtenido** | NA |
| **Captura** | NA |
| **Estado** | No ejecutado |
| **Observaciones** | Ver BUG-016. |

---

## 5. Validaciones Transversales

| ID | Descripción | Resultado Esperado | Resultado Obtenido | Estado |
| --- | --- | --- | --- | --- |
| CP32 | Recorrer todos los módulos y detectar combinaciones de idioma inglés-español en textos, botones, alertas y etiquetas. | Textos en español, claro y consistente. | Textos con idiomas mezclados. | Fallido |

#### CP32 — Idioma de interfaz y mensajes

| Campo | Detalle |
| --- | --- |
| **Pasos** | 1. Ingresar a cada módulo (Login, Dashboard, Aprobación, Solicitud, Reportes, Histórico, Departamentos, Tipos de trámite, Usuarios, Zonas, Hoteles, Costo viáticos, Términos). |
| **Resultado Esperado** | Textos en español, claro y consistente. |
| **Resultado Obtenido** | Textos con idiomas mezclados. |
| **Captura** | — |
| **Estado** | Fallido |
| **Observaciones** | Ver BUG-017. |

---

## 6. Registro de Hallazgos

17 hallazgos identificados en la corrida de smoke test.

### BUG-001 — Persistencia de sesión no respeta la opción "Recuérdame"

| Campo | Detalle |
| --- | --- |
| **ID** | BUG-001 (caso CP01) |
| **Descripción** | La sesión se mantiene al cerrar inesperadamente la página, independientemente de si la opción "recuérdame" está marcada o no. |
| **Severidad** | Media |
| **Pasos para Reproducir** | 1. Iniciar sesión sin marcar "recuérdame".<br>2. Cerrar la página inesperadamente.<br>3. Volver a abrir la URL de login.<br>4. Observar que la sesión se mantiene activa igualmente. |
| **Estado** | Pendiente |

### BUG-002 — Alerta del navegador "información no segura" al cerrar sesión

| Campo | Detalle |
| --- | --- |
| **ID** | BUG-002 (caso CP02) |
| **Descripción** | Al hacer clic en "Salir", se observa la alerta del navegador "Estás a punto de enviar una información no segura" antes de completar el logout, lo que sugiere un reenvío de formulario o un recurso servido sin HTTPS en ese flujo. |
| **Severidad** | Baja (el logout finalmente se completa, pero la alerta es inusual y amerita revisión) |
| **Pasos para Reproducir** | 1. Iniciar sesión.<br>2. Hacer clic en "Salir".<br>3. Observar la alerta del navegador antes de la redirección al login. |
| **Estado** | Pendiente |

### BUG-003 — Módulo de Aprobación de viáticos bloqueado sin causa especificada (CP04-CP07)

| Campo | Detalle |
| --- | --- |
| **ID** | BUG-003 (casos CP04, CP05, CP06, CP07) |
| **Descripción** | Los cuatro casos del módulo "Administración – Aprobación de viáticos" (KPIs del Dashboard, tabla de estados con exportación, detalle de solicitud y filtros optimizados) quedaron con resultado "NA" y Estado "Bloqueado", sin que la fuente original documente la causa del bloqueo. Se registra como hallazgo ambiguo que requiere confirmación: no es posible determinar desde el reporte si se trata de un defecto del módulo o de una limitación/indisponibilidad del ambiente de pruebas en el momento de la ejecución. |
| **Severidad** | No determinada (ambigüedad a escalar) |
| **Pasos para Reproducir** | No documentados en la fuente original para estos 4 casos. |
| **Estado** | Pendiente de aclaración |

### BUG-004 — Error crítico 504 Gateway Time-out al crear una solicitud de viáticos

| Campo | Detalle |
| --- | --- |
| **ID** | BUG-004 (caso CP08; bloquea en cascada CP09, CP10, CP11, CP12, CP13) |
| **Descripción** | Al completar el wizard de creación de solicitud de viáticos (zona, fechas, tipo de trámite, empleados) y enviar, el sistema responde con un error 504 Gateway Time-out, impidiendo la creación de la solicitud. Este fallo bloquea toda la funcionalidad principal del sistema que depende de tener una solicitud creada: CP10 señala explícitamente "Bloqueado por falla en CP08"; CP09, CP11, CP12 y CP13 quedaron igualmente sin ejecutar. |
| **Severidad** | Crítica |
| **Pasos para Reproducir** | 1. Iniciar sesión como solicitante.<br>2. Completar el wizard de solicitud de viáticos (zona, fechas, tipo de trámite).<br>3. Agregar al menos un empleado.<br>4. Enviar la solicitud.<br>5. Observar el error 504 Gateway Time-out. |
| **Estado** | Pendiente |

### BUG-005 — Módulo de Reportes bloqueado sin causa especificada (CP14)

| Campo | Detalle |
| --- | --- |
| **ID** | BUG-005 (caso CP14) |
| **Descripción** | El caso de visualización de solicitudes por estado en el módulo de Reportes quedó con resultado "NA" y Estado "Bloqueado", sin que la fuente original documente la causa. |
| **Severidad** | No determinada (ambigüedad a escalar) |
| **Pasos para Reproducir** | 1. Acceder a "Reportes".<br>2. Hacer clic en las pestañas de estado (Rechazados, etc.). |
| **Estado** | Pendiente de aclaración |

### BUG-006 — Creación de departamento y asignación de presupuesto bloqueadas sin causa especificada (CP17, CP18)

| Campo | Detalle |
| --- | --- |
| **ID** | BUG-006 (casos CP17, CP18) |
| **Descripción** | Los casos de creación de un nuevo departamento y de asignación de presupuesto (Budget) quedaron con resultado "NA" y Estado "Bloqueado", sin causa documentada en la fuente original. |
| **Severidad** | No determinada (ambigüedad a escalar) |
| **Pasos para Reproducir** | CP17: 1. Clic en "Crear departamento". 2. Ingresar datos. 3. Guardar.<br>CP18: 1. Clic en "Crear Budget" para un departamento. 2. Ingresar monto. 3. Guardar. |
| **Estado** | Pendiente de aclaración |

### BUG-007 — Alerta no traducida al crear un nuevo tipo de trámite

| Campo | Detalle |
| --- | --- |
| **ID** | BUG-007 (caso CP20) |
| **Descripción** | Al crear un nuevo tipo de trámite, se observa una alerta del sistema que no está traducida al español. |
| **Severidad** | Baja |
| **Pasos para Reproducir** | 1. Ir a "Tipo de trámites".<br>2. Crear un nuevo tipo de trámite.<br>3. Observar el idioma de la alerta mostrada. |
| **Estado** | Pendiente |

### BUG-008 — Ausencia de validación para evitar tipos de trámite duplicados

| Campo | Detalle |
| --- | --- |
| **ID** | BUG-008 (caso CP20) |
| **Descripción** | El sistema permite registrar tipos de trámite duplicados sin advertir al usuario. |
| **Severidad** | Baja |
| **Pasos para Reproducir** | 1. Ir a "Tipo de trámites".<br>2. Crear un tipo de trámite con un nombre ya existente.<br>3. Observar que el sistema permite el registro. |
| **Estado** | Pendiente |

### BUG-009 — Encabezados de la tabla de Usuarios no traducidos al español

| Campo | Detalle |
| --- | --- |
| **ID** | BUG-009 (caso CP21) |
| **Descripción** | Al visualizar la tabla de Usuarios con el idioma de interfaz configurado en español, se observan elementos pendientes de traducir (nota de captura: "Traducir"). |
| **Severidad** | Baja |
| **Pasos para Reproducir** | 1. Ir a "Ajustes → Usuarios".<br>2. Observar los encabezados y etiquetas de la tabla con el idioma en español. |
| **Estado** | Pendiente |

### BUG-010 — Error crítico 504 Gateway Time-out al crear un usuario

| Campo | Detalle |
| --- | --- |
| **ID** | BUG-010 (caso CP22) |
| **Descripción** | Al completar el formulario de creación de usuario y confirmar, el sistema responde con un error 504 Gateway Time-out. Comparte el mismo patrón de error de infraestructura que BUG-004 (creación de solicitud de viáticos). |
| **Severidad** | Crítica |
| **Pasos para Reproducir** | 1. Ir a Ajustes → Usuarios.<br>2. Clic en "Crear usuario".<br>3. Completar todos los campos.<br>4. Confirmar la creación.<br>5. Observar el error 504 Gateway Time-out. |
| **Estado** | Pendiente |

### BUG-011 — Internal Server Error al crear un nuevo rol (role_id sin createOptionUsing)

| Campo | Detalle |
| --- | --- |
| **ID** | BUG-011 (caso CP23) |
| **Descripción** | Al intentar crear un nuevo rol desde Ajustes → Roles, el sistema arroja el error *Internal Server Error*: "Select field [data.role_id] must have a [createOptionUsing()] closure set.", impidiendo la creación del rol. |
| **Severidad** | Alta |
| **Pasos para Reproducir** | 1. Navegar a Ajustes → Roles.<br>2. Hacer clic en "Crear rol".<br>3. Completar Name* y Description*.<br>4. Hacer clic en "Create".<br>5. Observar el Internal Server Error. |
| **Estado** | Pendiente |

### BUG-012 — Validación de correo duplicado bloqueada sin causa especificada

| Campo | Detalle |
| --- | --- |
| **ID** | BUG-012 (caso CP25) |
| **Descripción** | El caso de validación de correo duplicado en creación de usuario quedó con resultado "NA" y Estado "Bloqueado", sin causa documentada en la fuente original. |
| **Severidad** | No determinada (ambigüedad a escalar) |
| **Pasos para Reproducir** | 1. Crear nuevo usuario.<br>2. Ingresar un correo ya registrado (admin@admin.com).<br>3. Intentar guardar. |
| **Estado** | Pendiente de aclaración |

### BUG-013 — Internal Server Error (500) al visualizar la tabla de Zonas

| Campo | Detalle |
| --- | --- |
| **ID** | BUG-013 (caso CP26) |
| **Descripción** | Al acceder a la tabla de Zonas en Ajustes, el sistema responde con un Internal Server Error, status 500, impidiendo visualizar el listado. |
| **Severidad** | Alta |
| **Pasos para Reproducir** | 1. Ir a Ajustes → Zonas.<br>2. Observar el Internal Server Error (500). |
| **Estado** | Pendiente |

### BUG-014 — Creación de zona bloqueada (posible cascada del error 500 de BUG-013)

| Campo | Detalle |
| --- | --- |
| **ID** | BUG-014 (caso CP27) |
| **Descripción** | El caso de creación de nueva zona quedó sin ejecutar (resultado "NA", Estado "Bloqueado"). La fuente original no confirma explícitamente la causa, pero es consistente con una cascada del error 500 reportado en CP26 (BUG-013) sobre el mismo módulo de Zonas. |
| **Severidad** | No determinada (dependiente de BUG-013) |
| **Pasos para Reproducir** | 1. Clic en "Crear Zona".<br>2. Completar "Zona" y "Descripción".<br>3. Guardar. |
| **Estado** | Pendiente de aclaración |

### BUG-015 — El formulario de edición de hotel no se cierra tras guardar los cambios

| Campo | Detalle |
| --- | --- |
| **ID** | BUG-015 (caso CP30) |
| **Descripción** | Al editar y guardar los cambios de beneficios de un hotel, el formulario de edición permanece abierto en vez de regresar al listado de hoteles, generando incertidumbre sobre si el guardado fue exitoso. |
| **Severidad** | Media |
| **Pasos para Reproducir** | 1. Editar un hotel existente.<br>2. Activar/desactivar beneficios.<br>3. Guardar.<br>4. Observar que el formulario de edición no se cierra ni regresa al listado. |
| **Estado** | Pendiente |

### BUG-016 — Importación masiva de hoteles no ejecutada

| Campo | Detalle |
| --- | --- |
| **ID** | BUG-016 (caso CP31) |
| **Descripción** | El caso de importación masiva de hoteles desde Excel quedó registrado como "No ejecutado" en la fuente original; no hay evidencia de que se haya corrido, por lo que no se considera un defecto confirmado, sino un caso pendiente de ejecución. |
| **Severidad** | No aplica (caso no ejecutado, no concluyente) |
| **Pasos para Reproducir** | 1. Ir a "Importar Hoteles".<br>2. Subir archivo .xlsx.<br>3. Revisar y confirmar. |
| **Estado** | No ejecutado |

### BUG-017 — Inconsistencia de idioma en toda la interfaz (textos mezclados inglés/español)

| Campo | Detalle |
| --- | --- |
| **ID** | BUG-017 (caso CP32) |
| **Descripción** | Al recorrer todos los módulos del sistema, se detectaron textos, botones, alertas y etiquetas en inglés mezclados con español, a pesar de que el idioma de interfaz configurado es español. Ejemplos reportados: "List", "Create", "New tipo tramite", y mensajes de alerta en inglés. |
| **Severidad** | Media |
| **Pasos para Reproducir** | 1. Ingresar a cada módulo (Login, Dashboard, Aprobación, Solicitud, Reportes, Histórico, Departamentos, Tipos de trámite, Usuarios, Zonas, Hoteles, Costo viáticos, Términos).<br>2. Verificar el idioma de todos los textos, botones y alertas. |
| **Estado** | Pendiente |

---

## Resumen de Hallazgos Críticos

- **Error crítico 504 Gateway Time-out** (BUG-004, BUG-010): impide la creación de solicitudes y de usuarios, bloqueando funcionalidad principal del sistema.
- **Idioma inconsistente** (BUG-017): textos en inglés mezclados con español (botones, alertas, etiquetas). Ejemplo: "List", "Create", "New tipo tramite", mensajes de alerta en inglés.

**Elaborado por:** Luis Aranguren — Analista QA
**Fecha de la corrida:** 2026-04-10
