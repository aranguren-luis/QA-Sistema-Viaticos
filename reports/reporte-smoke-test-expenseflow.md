**INFORME DE PRUEBAS – EXPENSEFLOW**** (****10****.4.2026)**

**Objetivo de las pruebas**

Verificar el correcto funcionamiento de los módulos que componen el sistema ExpenseFlow, asegurando que:

Los flujos de creación, aprobación y cancelación de solicitudes operen según lo esperado.

Los módulos administrativos (departamentos, usuarios, zonas, hoteles, tipos de trámite, presupuestos) permitan la gestión completa de los datos.

Las integraciones (correos electrónicos, notificaciones push, sincronización con Profit) funcionen adecuadamente.

Las validaciones de (fechas, rangos de calificación, campos obligatorios, filtrado) se apliquen correctamente.

**Resumen de resultados**

| Estado | Cantidad |
| --- | --- |
| Correcto | 11 |
| Fallido | 6 |
| Bloqueado | 14 |
| Total, de casos | 32 |

**Detalle de casos de prueba por módulo**

**1. Login**

**CP0****1**** – Inicio de sesión exitoso**

**Descripción:** Verificar que un usuario registrado pueda iniciar sesión con credenciales válidas.

**Precondiciones:** Usuario registrado y cuenta activa. Credenciales: admin@admin.com / 123456

**Pasos:**

Acceder a https://expenseflow.example.com/admin/login

Introducir correo electrónico y contraseña

Hacer clic en "Entrar"

**Resultado esperado:** Redirección al Dashboard con contenido del perfil.

**Resultado obtenido:** Carga correctamente al Dashboard. La sesión se mantiene al cerrar la página inesperadamente indiferentemente si se tiene tildada o no la opción recuérdame. 

**Captura****:** NA

**Estado:** Correcto
















**CP0****2**** – Cierre de sesión (Logout)**

**Descripción:** Verificar que el botón "Salir" cierre la sesión y redirija al login.

**Precondiciones:** Usuario autenticado en el Dashboard.

**Pasos:**

Hacer clic en "Salir"

**Resultado esperado:** Desconexión y redirección a pantalla de login; no se puede volver al Dashboard con botón atrás.

**Resultado obtenido:**** **Se realiza acción de logout, se observa “Alerta estas a punto de enviar una información no segura “.

**C****aptura:**  

**Estado:** Correcto











**CP0****3**** – Cambio de contraseña desde Dashboard**

**Descripción:** Verificar que el botón "Actualizar contraseña" despliegue el formulario correspondiente.

**Precondiciones:** Usuario autenticado.

**Pasos:**

En el Dashboard, hacer clic en "Actualizar contraseña"

**Resultado esperado:** Se muestra el formulario para actualizar la contraseña y validación de nueva contraseña debe ser exactamente 9 caracteres, incluir letras, números y símbolos. 

**Resultado obtenido:** Funciona correctamente la validación de contraseña. 

**Captura****:** NA

**Estado:** Correcto







**
****2. Administración – Aprobación de viáticos**

**CP0****4****– Visualización de ****KPIs**** en Dashboard**

**Descripción:** Verificar que los indicadores "Aprobados", "Por aprobar" y "Rechazados" se muestren y redirijan correctamente.

**Precondiciones:** Usuario autenticado, existencia de solicitudes.

**Pasos:**

Observar los tres KPI en el Dashboard.

Hacer clic en cada uno.

**Resultado esperado:** Los valores son visibles

**Resultado obtenido:** NA

**Captura****:** NA

**Estado:** Bloqueado

**CP0****5**** – Tabla de aprobación de viáticos (estados y exportación)**

**Descripción:** Validar que la tabla muestre los estados "Rechazados", "Cancelados", "Por aprobar analista" y "Aprobado por sup. y analista", y permita exportar a Excel.

**Precondiciones:** Usuario con permisos, solicitudes en diferentes estados.

**Pasos:**

Acceder a "Aprobación de viáticos"

Observar opciones de filtro y tabla.

Exportar selección múltiple a Excel.

**Resultado esperado:** Tabla correcta, exportación funcional.

**Resultado obtenido:** NA

**Captura****:** NA

**Estado:** Bloqueado




















**CP0****6**** – Detalle y observaciones de una solicitud**

**Descripción:** Verificar que al seleccionar un viático se muestren detalles y observaciones.

**Precondiciones:** Solicitudes cargadas en la tabla.

**Pasos:**

Hacer clic en un registro de la tabla de aprobación.

**Resultado esperado:** Se despliega el detalle con observaciones.

**Resultado obtenido:** NA

**C****aptura:** NA

**Estado:** Bloqueado

























**CP0****7**** – Filtros optimizados (múltiples supervisores, múltiples departamentos, Local/Foráneo, rango de fechas con hoy)**

**Descripción:** Validar que los filtros permitan selección múltiple y que el día de hoy se incluya en rangos.

**Precondiciones:** Usuario autenticado, solicitudes variadas.

**Pasos:**

Aplicar filtro por 2 supervisores.

Aplicar filtro por 3 departamentos.

Filtrar por "Foráneo".

Filtrar fecha desde "hoy" hasta "hoy".

**Resultado esperado:** Los listados muestran las solicitudes correctas.

**Resultado obtenido:** NA

**C****aptura:** NA

**Estado:** Bloqueado

**3. Gestión**

**3.1 Solicitud de viáticos**

**CP0****8**** – Creación completa de solicitud (flujo ****wizard****)**

**Descripción:** Crear solicitud con zona, fechas, tipo de trámite, al menos un empleado y envío.

**Precondiciones:** Usuario logueado como solicitante.

**Pasos:**

Completar wizard (zona, fechas, tipo trámite).

Agregar ≥1 empleado.

Enviar.

**Resultado esperado:** Solicitud creada con estado "Por Aprobar Supervisor". Correo enviado a analista y supervisor.

**Resultado obtenido:**  504 Gateway Time-out 

**C****aptura:** 

**Estado:** Fallido












**CP0****9**** – Validación de fechas incorrectas (salida > retorno)**

**Descripción:** Impedir envío cuando fecha de salida es posterior a fecha de retorno.

**Precondiciones:** Usuario autenticado.

**Pasos:**

Seleccionar fecha salida posterior a fecha retorno.

Intentar enviar.

**Resultado esperado:** Validación impide envío. Mensaje de error claro en español.

**Resultado ****obtenido:**NA

**C****aptura:** NA

**Estado:** Bloqueado



**CP****10**** – Cálculo automático de logística (alimentación, hospedaje, transporte)**

**Descripción:** Al crear solicitud con zona de costos predefinidos, se debe generar tabla de logística con tarifas.

**Precondiciones:** Zona con costos configurados.

**Pasos:**

Crear solicitud con zona que tiene costos predefinidos.

Ver tabla de logística generada.

**Resultado esperado:** Alimentación/hospedaje/transporte calculados según tarifas.

**Resultado obtenido:** Bloqueado por falla en CP08

**C****aptura:** N/A

**Estado:** Bloqueado





**CP1****1**** – Flujo de aprobación (****workflow****)**

**Descripción:** Validar transiciones de estado:

**Precondiciones:** Solicitud en estado correspondiente.

**Pasos:**

**Resultado esperado:** Cada acción cambia el estado correctamente y envía notificaciones.

**Resultado obtenido:** NA

**C****aptura:** NA

**Estado:** Bloqueado

**CP1****2**** – Valoración de hotel desde solicitud aprobada**

**Descripción:** Calificar hotel con estrellas (1-5) y observación.

**Precondiciones:** Solicitud aprobada y finalizada, asociada a un hotel.

**Pasos:**

Seleccionar estrellas 

**Resultado esperado:** Calificación guardada

**Resultado obtenido:** NA

**C****aptura:** NA

**Estado:** Bloqueado

**CP1****3**** – Zona horaria (Hora Venezuela)**

**Descripción:** Las fechas registradas deben usar hora de Venezuela (-4 UTC).

**Precondiciones:** Crear solicitud a las 2:00 PM UTC (10:00 AM VET).

**Pasos:**

Crear solicitud.

**Resultado esperado:** Muestra formato correcto 

**Resultado obtenido:** NA

**C****aptura:** NA

**Estado:** Bloqueado






**3.2 Reportes**

**CP1****4**** – Visualización de solicitudes por estado (sin aprobar, aprobadas, rechazadas)**

**Descripción:** El módulo Reportes debe mostrar tabla clasificada por pestañas.

**Precondiciones:** Solicitudes en diferentes estados.

**Pasos:**

Acceder a "Reportes".

Clic en pestaña "Rechazados", etc.

**Resultado esperado:** Muestra solo solicitudes del estado seleccionado.

**Resultado obtenido:** NA

**C****aptura:** 
1. Mejorar redacción 

**Estado:**  Bloqueado 












**3.3 Histórico de actualización de viáticos**

**CP1****5**** – Columnas del histórico**

**Descripción:** Verificar que la tabla muestre: autorizado por, modificación de status, fecha de actualización, fecha salida, fecha retorno, observaciones.

**Precondiciones:** Existen actualizaciones de solicitudes.

**Pasos:**

Ir a "Histórico de actualización de viáticos".

**Resultado esperado:** Tabla con las columnas especificadas.

**Resultado obtenido:** Se muestra correctamente, con filtros aplicables.

**Evidencia o captura:** 

1. Mejorar redacción 

**Estado:** Bloqueado














**3.4 Gastos de departamentos****
Bloqueado **

**4. Ajustes**

**4.1 Departamentos**

**CP1****6**** – Visualización de tabla de departamentos**

**Descripción:** Mostrar código, departamento, supervisor y presupuesto total.

**Precondiciones:** Departamentos registrados.

**Pasos:**

Ir a "Ajustes → Departamentos".

**Resultado esperado:** Columnas correctas.

**Resultado obtenido:** Correcto.

**C****aptura:** 
1. Mejorar redacción traducir

**Estado:** Correcto







**CP1****7**** – Creación de nuevo departamento**

**Descripción:** Crear departamento con código Profit, nombre, supervisor, presupuesto.

**Pasos:**

Clic en "Crear departamento".

Ingresar datos.

Guardar (opciones: Crear / Crear y crear otro / Cancelar).

**Resultado esperado:** Departamento creado y visible en listado.

**Resultado obtenido:** NA

**C****aptura:** NA

**Estado:** Bloqueado
























**CP1****8**** – Asignación de presupuesto (Budget) a un departamento**

**Descripción:** Desde edición del departamento, asignar monto presupuestario.

**Precondiciones:** Departamento existente.

**Pasos:**

Clic en "Crear Budget".

Ingresar monto (ej. 500,000).

Guardar.

**Resultado esperado:** Presupuesto asignado y actualizado en tabla.

**Resultado obtenido:** NA

**C****aptura:** NA

**Estado:** Bloqueado

**4.2 Tipo de trámites**

**CP1****9**** – Visualización de tabla de tipos de trámite**

**Descripción:** La tabla debe mostrar "Tipo de trámite" y "Fecha de creación".

**Precondiciones:** Tipos de trámite existentes.

**Pasos:**

Ir a "Ajustes → Tipo de trámites".

**Resultado esperado:** Columnas correctas.

**Resultado obtenido:** Tramite Creado correctamente 

**C****aptura:** NA

**Estado:** Correcto


**CP****20**** – Creación de nuevo tipo de trámite**

**Descripción:** Crear tipo de trámite con campos "Tipo de trámite" y "Traslado" (Local/Foráneo). Usar botones Create, Create & create another, Cancel.

**Precondiciones:** Usuario con permisos.

**Pasos:**

Clic en "New tipo tramite".

Completar "Tipo de Tramite*" y "Traslado*".

Probar las 2 acciones de guardado.

**Resultado esperado:**  Validación de campos obligatorios. Al guardar, el registro aparece en el listado. La opción "Crear y crear otro" permite generar un nuevo trámite y restablece el formulario

**Resultado obtenido:** Correcto. Se creó trámite con Traslado "Foráneo" y "Local"

**C****aptura:** 
1.Traducir alerta


**Estado:** Correcto (sugerencia: Agregar validación para evitar registros duplicados)

**
****4.3 Usuarios**

**CP21 – Visualización de tabla de usuarios**

**Descripción:** La tabla debe mostrar cédula, nombre, apellido, empresa, departamento y rol.

**Precondiciones:** Usuarios registrados.

**Pasos:**

Ir a "Ajustes → Usuarios".

**Resultado esperado:** Columnas correctas.

**Resultado obtenido:** Correcto. Se sugiere agregar buscador.

**C****aptura:** 
1. Traducir 

**Estado:** Correcto













**CP22 – Creación de usuario **

**Descripción:** Crear usuario con campos: Nombre*, Apellido*, Cédula, Rol, Empresa, Departamento*, Correo Electrónico, Contraseña*. Usar botones Create, Create & create another, Cancel.

**Precondiciones:** Permisos de administración.

**Pasos:**

Clic en "Crear usuario".

Completar todos los campos.

Probar las tres acciones.

**Resultado esperado:** Usuario creado y visible en tabla; validación de campos obligatorios.

**Resultado obtenido:** >504 Gateway Time-out

**Captura****:** 

**Estado:** Fallido







**CP2****3**** – Crear nuevo rol**
• **Descripción:** Crear un nuevo rol de usuario desde el panel de administración (Ajustes → Roles).
• **Precondiciones:** Usuario autenticado con permisos de administrador.
• **Pasos:**

Navegar a Ajustes → Roles.

Hacer clic en el botón “Crear rol” (o “Create”).

Completar los campos obligatorios: Name* (ej. “QA”), Description* (ej. “ROL DE PRUEBA”).

Hacer clic en el botón “Create” (o “Crear”).

• **Resultado esperado:** El rol se crea exitosamente 
• **Resultado obtenido:** Al intentar crear el rol, el sistema arroja error *Internal** Server Error*: “Select field [data.role_id] must have a [createOptionUsing()] closure set.” 
• **Captura:** 

**CP2****4**** – Edición de usuario**

**Descripción:** Modificar rol u otros campos de un usuario existente.

**Pasos:**

En listado, clic en "Edit".

Modificar datos.

Guardar.

**Resultado esperado:** Cambios guardados

**Resultado obtenido:** Correcto.

**C****aptura:** 
pendiente verificar si los datos se están guardando correctamente en la tabla. 

**Estado:** Correcto

**CP2****5**** – Validación de correo duplicado en creación de usuario**

**Descripción:** No permitir crear usuario con correo ya registrado.

**Precondiciones:** Existe usuario con correo admin@admin.com.

**Pasos:**

Crear nuevo usuario.

Ingresar admin@admin.com en campo Correo.

Intentar guardar.

**Resultado esperado:** Mensaje de error claro (ej. "El correo electrónico ya existe") y no se crea.

**Resultado obtenido:** NA

**C****aptura:** NA

**Estado:** Bloqueado






















**4.4 Zonas**

**CP2****6**** – Visualización de tabla de zonas**

**Descripción:** La tabla debe mostrar "Zona" y "Fecha de creación".

**Precondiciones:** Zonas registradas.

**Pasos:**

Ir a "Ajustes → Zonas".

**Resultado esperado:** Columnas correctas.

**Resultado obtenido:** Internal Server Error status 500 

**C****aptura:** 

**Estado:** Fallido












**CP2****7**** – Creación de nueva zona**

**Descripción:** Crear zona con nombre y descripción.

**Pasos:**

Clic en "Crear Zona".

Completar "Zona" y "Descripción".

Guardar.

**Resultado esperado:** Zona creada y visible en tabla; validación de campos obligatorios.

**Resultado obtenido:** NA

**C****aptura:** NA

**Estado:** Bloqueado
























**4.5 Hoteles **

**CP2****8**** – Visualización de tabla de hoteles**

**Descripción:** La tabla debe mostrar zona, hotel, dirección y beneficios (con íconos sí/no).

**Precondiciones:** Hoteles registrados.

**Pasos:**

Ir a "Ajustes → Hoteles".

**Resultado esperado:** Columnas correctas y beneficios visibles.

**Resultado obtenido:** NA

**C****aptura:** NA

**Estado:** Correcto
























**CP2****9****– Creación de hotel **

**Descripción:** Crear hotel con todos los campos: zona, datos generales, bancarios, beneficios Toggles (desayuno, wifi, etc.), tarifas.

**Pasos:**

Clic en "Crear lista de hoteles".

Completar formulario.

Guardar.

**Resultado esperado:** Hotel registrado, aparece en tabla con beneficios seleccionados.

**Resultado obtenido:** Correcto.

**C****aptura:** 

**Estado:** Correcto














**CP****30**** – Edición de hoteles (activar/desactivar beneficios)**

**Descripción:** Modificar beneficios de un hotel existente y ver reflejo en tabla.

**Pasos:**

Editar un hotel.

Activar un beneficio nuevo, desactivar uno existente.

Guardar.

**Resultado esperado:** Guardar edición.

**Resultado obtenido:** Correcto, se sugiere que al editar y guardar los cambios  se regrese al listado de hoteles. actualmente no se cierra el formulario de edición. 

**Evidencia o captura:** NA

**Estado:** Correcto 

**CP3****1**** – Importación masiva de hoteles desde Excel**

**Descripción:** Subir archivo .xlsx con columnas correctas, revisar datos en wizard editable y confirmar importación.

**Precondiciones:** Archivo Excel válido.

**Pasos:**

Ir a "Importar Hoteles".

Subir archivo.

Revisar y editar datos si es necesario.

Confirmar.

**Resultado esperado:** Hoteles insertados en BD. Mensaje de error si columnas incorrectas.

**Resultado obtenido:** NA

**C****aptura:** NA

**Estado:** No ejecutado

- Inconsistencias de idioma 

**CP32 – Idioma de interfaz y mensajes**

**Descripción:** Recorrer todos los módulos y detectar  combinaciones inglés-español.

**Pasos:**

Ingresar a cada módulo (Login, Dashboard, Aprobación, Solicitud, Reportes, Histórico, Departamentos, Tipos de trámite, Usuarios, Zonas, Hoteles, Costo viáticos, Términos).

**Resultado esperado:**  textos en español, claro y consistente.

**Resultado obtenido:** Textos con idiomas mezclados.

**C****aptura:** 




**
****
****Estado:** Fallido 

**
****
****
****
****
****Re****sumen  ****
****
****
****Error crítico 504 Gateway Time-****out**

Impide la creación de solicitudes 

Bloquea toda la funcionalidad principal del sistema.

**
****Idioma inconsistente**

Textos en inglés mezclados con español (botones, alertas, etiquetas).

Ejemplo: “List”, “Create”, “New tipo tramite”, mensajes de alerta en inglés.

**Elaborado por:**  Luis Aranguren Analista QA 
**Fecha:** 2026-04-10
