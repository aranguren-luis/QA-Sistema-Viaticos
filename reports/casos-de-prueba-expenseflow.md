**Resumen de Casos de Prueba**** Test de Regresión **

| Estado | Cantidad |
| --- | --- |
| Correctos | 22 |
| Fallidos | 6 |
| Bloqueo | 2 |
| Total, de Casos | 30 |

| Implementación nueva | Test case | Status |
| --- | --- | --- |
| Nuevos campos de beneficios para hoteles (desayuno, almuerzo, cena, estacionamiento, etc.) | CP-23: Visualización de tabla de hoteles<br>CP-24: Creación de lista de hoteles (con toggles de beneficios)<br>CP-26: Edición de hotel: activar/desactivar beneficios | Correcto |
| Sistema de notificaciones por correo electrónico para aprobación de viáticos | CP-27: Envío de correo electrónico al crear solicitud de viático | Bloqueado |
| Sistema de feedback de hoteles (calificación por estrellas y observaciones) | CP-29: Acceso al formulario de valoración de hotel desde solicitud aprobada | Correcto (con observaciones) |
| Nuevo sistema de departamentos (incluyendo integración con Profit) | CP-11: Visualización de tabla de departamentos<br>CP-12: Creación de un nuevo departamento | Correcto |
| Sistema de notificaciones push | CP-28: Envío y recepción de notificación push | Fallido |
| Sistema de presupuestos (budget) | CP-13: Asignación de presupuesto (Budget) a un departamento desde edición | Fallido |
| Importación masiva de hoteles (asistente con archivo Excel) | CP-25: Carga masiva de hoteles desde archivo Excel | Fallido |
| Solución de zona horaria (hora de Venezuela) | — | Correcto |
| Mejoras visuales (nombre de quien aprueba, nombre del hotel en la tabla) | — | Correcto |
| Optimización de filtros (múltiples supervisores, múltiples departamentos, búsqueda por Local/Foráneo, inclusión del día de hoy en rangos de fecha) | CP-09 Reportes | Correcto (con observaciones) |

**Cuentas de Prueba **

ANALIST1.

qa.tester@example.com

cuenta de prueba creada 

Solicitante@example.com

supervisor@example.com ExpenseFlow#2026

CP-01: **Inicio de sesión exitoso en la plataforma de viáticos**
**Descripción:** Verificar que un usuario registrado pueda iniciar sesión correctamente en la plataforma utilizando credenciales válidas.
**Plataforma:** Web
**Precondiciones:**

El usuario debe estar previamente registrado y su cuenta debe estar activa.

**Datos de Prueba:**

Correo electrónico: Solicitante@example.com

Contraseña: ExpenseFlow#2026

**Pasos:**

1. Acceder a la URL https://expenseflow.example.com/admin/login.

2. Introducir el correo electrónico 

3. Introducir la contraseña 

4. Hacer clic en el botón Entrar

**Resultado Esperado:**

El sistema permite el acceso y redirige al usuario al Dashboard mostrando el contenido correspondiente al perfil autenticado.

**Resultado Obtenido:** Carga correctamente al Dashboard 

**Estado:** Correcto 
**Observaciones:****
****
****
**La implementación actual no recuerda información relacionada con el correo y la contraseña, sino que mantiene la sesión actual suele confundir un poco.  
El comportamiento esperado es que si se cierra inesperadamente y volver abrir se dirija directamente al Dashboard. se observa que. 
 La funcionalidad actual guarda la sesión al cerrar la página, independientemente de si la opción está activada o no.
**
**CP-02: **Visualización correcta de los ****KPIs**** en el Dashboard**** / Datos Usuario** 
**Descripción:** Verificar que al acceder al Dashboard se muestren los indicadores KPI "Aprobados", "Por aprobar" y "Rechazados" y datos del usuario correctamente
**Plataforma:** Web
**Precondiciones:**

Usuario autenticado en la plataforma y en la sección Dashboard.

**Datos de Prueba:**

Sesión iniciada con un usuario válido.

**Pasos:**
1. Observar el área de indicadores KPI.

**Resultado Esperado:**

Se visualizan los tres KPI: "Aprobados", "Por aprobar" y "Rechazados" con sus respectivos valores.

**Resultado Obtenido:**  Al realizar clic en los kpi rechazados , por abrobar redirige correctamente a la tabla para esos valores , lo cual no ocurre para aprobados , actualmente a  https://expenseflow.example.com/admin/aprobacion-viaticos?activeTab=Todos   pero debería ser 
  . 

**Estado:** Fallido
**Observaciones:**NA


Actual 



Esperado




Las siglas del usuario son incorrectas: en lugar de tomar la primera letra del nombre y del apellido, está usando las dos primeras letras del nombre.


CP-03: **Visualización de gráfica histórica de viáticos por día**
**Descripción:** Validar que el Dashboard muestre una gráfica histórica de viáticos por día.
Plataforma: Web
**Precondiciones:**

Usuario autenticado y ubicado en el Dashboard.

** Datos de Prueba:**

Sesión iniciada con historial de viáticos registrado.

**Pasos:**

1. Ingresar al Dashboard.

2. Buscar la sección "Histórico" y visualizar la gráfica de viáticos por día.

**Resultado Esperado:**
Se muestra una gráfica con información histórica de viáticos clasificada 

**Resultado Obtenido:**
gráfica con información histórica de viáticos clasificada

**Estado:** Correcto
**Observaciones**:NA


CP-04: **Funcionamiento del botón "Actualizar contraseña" en el Dashboard**
**Descripción:** Verificar que el botón "Actualizar contraseña" redirige o despliega el formulario para cambiar la contraseña del usuario.
**Plataforma:** Web
**Precondiciones:**

Usuario autenticado y ubicado en el Dashboard.

**Datos de Prueba:**

Usuario con perfil editable.

**Pasos:**

1. Ingresar al Dashboard.

2. Hacer clic en el botón "Actualizar contraseña".

**Resultado Esperado:**

Se muestra el formulario para actualizar la contraseña.

**Resultado Obtenido:****
**

Se muestra el formulario para actualizar la contraseña.

**Estado:** Correcto
**Observaciones:** NA


CP-05: **Funcionamiento del botón "Salir" (****Logout****) en el Dashboard**
**Descripción:** Verificar que el botón "Salir" cierre la sesión actual y redirija al usuario a la pantalla de inicio de sesión.
**Plataforma:** Web
**Precondiciones:**

Usuario autenticado y ubicado en el Dashboard.

**Datos de Prueba:**

Sesión iniciada.

**Pasos:**

1. Ingresar al Dashboard.

2. Hacer clic en el botón "Salir".

**Resultado Esperado:****
**

El usuario es desconectado y llevado a la pantalla de login 

**Resultado Obtenido:****
**

El usuario es desconectado y llevado a la pantalla de login 

**Estado:** correcto
**Observaciones:**


Verificar que la sesión se cierre correctamente y que no se pueda volver al Dashboard con el botón de atrás del navegador.









CP-06: **Visualización de opciones de estado en la tabla de Aprobación de Viáticos**
**Descripción:** Verificar que la tabla de "Aprobación de Viáticos" muestre correctamente las opciones de estado: "Rechazados", "Cancelados", "Por aprobar analista" y "Aprobado por sup. y analista" y permita exportar los datos a Excel .
**Plataforma:** Web
**Precondiciones:**


Usuario autenticado con permisos para acceder al módulo de aprobación de viáticos.

**Datos de Prueba:****
**

Viáticos registrados previamente en diferentes estados.

**Pasos:**

1. Hacer clic en la sección "Aprobación de viáticos" desde el menú principal.

2. Observar la tabla y sus opciones de filtro o visualización.

**Resultado Esperado:**

La tabla muestra correctamente los estados: "Rechazados", "Cancelados", "Por aprobar analista", "Aprobado por sup. y analista".

**Resultado Obtenido:****
**

La tabla muestra correctamente los estados: "Rechazados", "Cancelados", "Por aprobar analista", "Aprobado por sup. y analista".

**Estado:** Correcto
**Observaciones:**NA

CP-07: **Revisión de detalles y observaciones de una solicitud de viático**
**Descripción:** Validar que al seleccionar un viático de la tabla se muestren correctamente los detalles y las observaciones de la solicitud.
**Plataforma:** Web
**Precondiciones:**


Usuario autenticado.

Viáticos cargados en la tabla.

**Datos de Prueba:****
**

Un viático seleccionable con detalles y observaciones registrados.

**Pasos:****
**

1. En la pantalla de tabla de aprobación de viáticos, hacer clic en algún registro de viático.

2. Observar los detalles y el campo de observaciones de la solicitud.

**Resultado Esperado:****
**

Se despliega  los detalles y observaciones específicos del viático seleccionado.

**Resultado Obtenido:****
**

Se despliega  los detalles y observaciones específicos del viático seleccionado.

**Estado:** Correcto 
**Observaciones:**NA



CP-08: **Creación exitosa de una solicitud de viáticos con todos los campos y opciones**
**Descripción:** Verificar que el usuario puede crear correctamente una solicitud de viáticos llenando todos los campos requeridos, utilizando los toggles de "Incluirme" y "Desea agregar más información", y cumpliendo con la restricción del campo de observaciones (máximo 50 caracteres para el resumen).
**Plataforma:** Web
**Precondiciones:**

Usuario autenticado en la plataforma.

Permisos para crear solicitudes de viático.

**Datos de Prueba:**

Solicitante: "Equipo Thomas"

Tipo de trámite

Fecha de salida

Fecha de retorno

Acompañante 

Incluirme: Toggle en "Sí"

Observaciones/resumen 

Desea agregar más información: Toggle en "si"

**Pasos:**

1. Hacer clic en la sección "Solicitud de viáticos" desde el menú principal.

2. Hacer clic en el botón "Crear solicitud de viáticos".

3. Llenar el formulario con la información indicada en los Datos de Prueba.

4. Usar el toggle "Incluirme" y establecerlo en "Sí".

5. Ingresar el resumen en observaciones, verificando que no exceda los 50 caracteres.

6. Usar el toggle "Desea agregar más información" y establecerlo en "No".

7. Guardar o enviar la solicitud.

**Resultado ****Esperado:**La solicitud es creada exitosamente; se muestra un mensaje de confirmación y la solicitud aparece en la lista de solicitudes.

**Resultado Obtenido:**
La solicitud es creada exitosamente; se muestra un mensaje de confirmación y la solicitud aparece en la lista de solicitudes.

**Estado:** Correcto 
**Observaciones:**




Al borrar el campo Tasa BCV debería visualizarse nuevamente , actualmente queda vacio o en 0  



Para selector zona con opciones correspondientes a ciudades , la opción de hotel  se muestra vacía o opcional 






CP-9**: Visualización de solicitudes de viáticos en el módulo de Reportes**
**Descripción:** Verificar que el módulo de Reportes muestre la tabla de solicitudes de viáticos clasificadas por estado: sin aprobar, aprobadas y rechazadas.

**Plataforma:** Web
**Precondiciones:**

Usuario autenticado en la plataforma.

Existencia de solicitudes de viáticos en los estados "sin aprobar", "aprobados" y "rechazados".

**Datos de Prueba:**

Solicitudes de viáticos previamente registradas en distintos estados.

**Pasos:**

1. Hacer clic en la sección "Reportes" desde el menú principal.

2. Observar la tabla principal que contiene las solicitudes de viáticos.

**Resultado Esperado:****
**

La tabla muestra, de manera diferenciada, las solicitudes de viáticos en estado "sin aprobar", "aprobados" y "rechazados", permitiendo visualizarlos correctamente.

**Resultado Obtenido:****
**

La tabla muestra, de manera diferenciada, las solicitudes de viáticos en estado "sin aprobar", "aprobados" y "rechazados", permitiendo visualizarlos correctamente.

**Estado:** Correcto (Realizar ajuste en selectores)
**Observaciones:**   Se observa selector selecciona 2 o 3 opciones a la vez 
[enlace de grabación interno omitido]


Jornada especial , Otros no aparecen en el filtrado  Tipo de tramite , unicamente para Local o Foraneo , la razón de ello explicado a los requerimientos es que se necesita  es filtrar por tipo de traslado , se sugiere agregar los otros tipos de tramites al filtrado o cambiar el label para evitar confusión . 


Filtrado Departamento , no aparece en la tabla
CP-10: **Visualización correcta del histórico de actualización de viáticos**
**Descripción**: Verificar que al ingresar en “Histórico de actualización de viáticos” se muestra una tabla con las columnas: autorizado por, modificación de status, fecha de actualización, fecha de salida, fecha de retorno y observaciones.
**Plataforma:** Web
**Precondiciones:**

Usuario autenticado en la plataforma.

Existen registros de actualizaciones sobre solicitudes de viáticos en el sistema.

**Datos de Prueba:**

Actualizaciones de solicitudes de viáticos previamente realizadas por diferentes usuarios y con diferentes fechas/estados.

**Pasos:**

1. Hacer clic en la sección "Histórico de actualización de viáticos" desde el menú principal.

2. Visualizar la tabla que muestra el histórico de actualizaciones.

**Resultado Esperado:**

La tabla se despliega correctamente y contiene las columnas: autorizado por, modificación de status, fecha de actualización, fecha de salida, fecha de retorno y observaciones.

**Resultado Obtenido:**

Se observa toda la información de los viáticos realizados y se aplica las opciones de filtro

**Estado:** Correcto 
**Observaciones:**NA






CP-11: **Visualización de la tabla de departamentos en Ajustes****
Descripción:** Verificar que al ingresar a "Ajustes Departamentos" se muestre una tabla con las columnas: código, departamento, supervisor, y presupuesto total.
**Plataforma:** Web
**Precondiciones:**

Usuario autenticado con permisos de administración.

Departamentos registrados previamente en el sistema.

**Datos de Prueba:**

Múltiples departamentos cargados con código, nombre, supervisor asignado y presupuesto total.

**Pasos:**

1. Hacer clic en la sección "Ajustes Departamentos" desde el menú.

2. Visualizar la tabla principal de departamentos.

**Resultado Esperado:****
**

La tabla muestra correctamente las columnas: código, departamento, supervisor, y presupuesto total para cada registro.

**Resultado Obtenido:****
**

La tabla muestra correctamente las columnas: código, departamento, supervisor, y presupuesto total para cada registro.

**Estado:** Correcto 
**Observaciones:**NA


 





CP-12: **Creación de un nuevo departamento****
Descripción:** Verificar que el usuario puede crear un nuevo departamento llenando todos los campos requeridos mediante el formulario y usando las opciones de guardar.
**Plataforma:** Web
**Precondiciones:**

Usuario autenticado con permisos de creación.

**Datos de Prueba:**

Código Profit Interno: " DPTO-PRUEBA-01 "

Nombre del departamento

Supervisor

**Pasos:**

1. Hacer clic en "Ajustes Departamentos".

2. Hacer clic en el botón "Crear Departamento".

3. Llenar los campos: Código Profit Interno y Nombre del departamento.

4. Asignar supervisor de sede/área en el correspondiente campo.

5. Elegir una de las opciones de guardar: "Crear", "Crear y crear otro" o cancelar la operación.

**Resultado Esperado:**

Si se elige "Crear" o "Crear y crear otro", el departamento es registrado y aparece en la tabla; si se cancela, no se registra ningún dato.

**Resultado Obtenido:**

Se crea correctamente el  Departamento nuevo 

**Estado:** Correcto 
**Observaciones:**NA

CP-13: **Asignación de presupuesto (Budget) a un departamento desde edición**
**Descripción:** Verificar la funcionalidad de asignación de “Budget” o presupuesto específico a un departamento mediante el botón “crear Budget”.
**Plataforma:** Web
**Precondiciones:**

Usuario autenticado con permiso de edición sobre departamentos.

Departamento previamente creado y visible en la tabla.

**Datos de Prueba:**

Monto a asignar: 500,000

**Pasos:**

1. En la tabla de departamentos, hacer clic en el botón "Crear Budget" para un departamento.

2. Se despliega el campo "amount".

3. Ingresar el monto deseado y confirmar con el botón "Crear".

**Resultado Esperado:**

El presupuesto es asignado exitosamente al departamento; se actualiza la información y muestra mensaje de éxito.

**Resultado Obtenido:**

Fallo al crear Budget

**Estado:** Fallido
**Observaciones:**NA



El campo “amount” no debe aceptar valores no numéricos o negativos.




CP-14: **Visualización de la tabla de tipo de trámites**** – ****Creacion** 
**Descripción:** Verificar que al ingresar a la sección "Tipo de trámites" se visualice una tabla con las columnas "Tipo de trámite" y "Fecha de creación".
**Plataforma:** Web
**Precondiciones:**

Usuario autenticado con acceso a la sección correspondiente.

Existe al menos un tipo de trámite previamente registrado en el sistema.

**Datos de Prueba:**

Tipos de trámite de ejemplo: "Comisión", "Capacitación" (con sus fechas de creación).

**Pasos:**

1. Hacer clic en la opción "Tipo de trámites" en el menú.

2. Observar la tabla que se presenta en pantalla.

**Resultado Esperado:**

La tabla muestra correctamente columnas para "Tipo de trámite" y "Fecha de creación" con datos válidos.

**Resultado Obtenido:**

**Estado:** Correcto
**Observaciones:** Se puede crear correctamente el trámite sin embargo se sugiere añadir una validación para evitar registros con tipo de tramite duplicado 



CP-15: **Visualización de la tabla de usuarios**
**Descripción:** Verificar que al ingresar a la sección "Usuarios" se muestra una tabla con las columnas: cédula, nombre, apellido, empresa, departamento y rol.
**Plataforma:** Web
**Precondiciones:**

Usuario autenticado con permisos para ver usuarios.

Usuarios registrados previamente en el sistema.

**Datos de Prueba:****NA****
**Pasos:

1. Hacer clic en "Usuarios" en el menú principal.

2. Observar la tabla presentada en pantalla.

Resultado Esperado:

La tabla muestra correctamente los campos cédula, nombre, apellido, empresa, departamento y rol para cada usuario registrado.

Resultado Obtenido:
La tabla muestra correctamente los campos cédula, nombre, apellido, empresa, departamento y rol para cada usuario registrado.

Estado: Correcto
Observaciones:  Se propone Agregar buscador para los usuarios 




CP-16: **Edición de usuario**
**Descripción:** Verificar que, al hacer clic para editar un usuario, se despliega un formulario donde se puede modificar rol e información  
**Plataforma:** Web
**Precondiciones:**

Usuario autenticado con permisos administrador

Usuario existente en el sistema.

Datos de Prueba:NA

**Pasos:**

1. En la lista de usuarios, hacer clic en el botón de editar correspondiente.

2. Guardar los cambios.

**Resultado Esperado:**

Se actualiza la información del usuario y se refleja en la tabla.

**Resultado Obtenido:****
**

Se actualiza la información del usuario y se refleja en la tabla.

**Estado:** Correcto
**Observaciones:** NA








CP-17: **Creación de un usuario nuevo**
Descripción: Verificar que el formulario de creación de usuario permite ingresar todos los campos requeridos y crear uno o varios usuarios, o cancelar sin guardar.
 Plataforma: Web
Precondiciones:

Usuario autenticado con permiso para crear usuarios.

**Datos de Prueba:**

Nombre: “Luis”

Apellido: “Gómez”

Cédula: “45678901”

Rol: “Operador”

Empresa: “BetaCorp”

Departamento: “Logística”

Email: “luis.gomez@betacorp.com”

Contraseña: “LuisGomez2026*”

**Pasos:**

1. Hacer clic en “Usuarios”.

2. Hacer clic en el botón “Crear usuario”.

3. Completar todos los campos del formulario según los datos de prueba.

4. Probar las siguientes opciones:

  a) Hacer clic en “Crear”.
  b) Hacer clic en “Crear y crear otro”.
  c) Hacer clic en “Cancelar”.
**Resultado Esperado:** El usuario se agrega y aparece en la tabla.

**Resultado Obtenido:** El usuario se agrega y aparece en la tabla.**
****Estado:** Correcto
**Observaciones:**NA


CP-18: **Creación de nuevo rol específico por parte de ****un Usuario**** ****admin****
Descripción:** Validar que un usuario con rol “admin” pueda acceder al formulario de creación de rol y guardar exitosamente. 
**Plataforma:** Web.
**Precondiciones:**

Usuario con rol “Super Usuario” ha iniciado sesión en el sistema.

Pasos:

En el menú lateral, ir a Ajustes > Usuarios.

Hacer clic en el botón + Agregar Nuevo (o “Crear”).

Hacer clic en el botón Crear (o Crear y crear otro según se requiera).

Observar el mensaje de éxito y verificar el nuevo rol en el listado.

**Resultado Esperado:**

Al hacer clic en “Crear”, se guarda el nuevo rol correctamente y se muestra un mensaje 

**Resultado Obtenido:** Alerta de error 
**Estado:** Fallido
**Observaciones:** La aplicación se rompe, no existe alerta de error 


CP-19: **Importación masiva de usuarios desde archivo Excel**
**Descripción:** Verificar que la funcionalidad de importación de usuarios a través de un archivo Excel permite cargar correctamente nuevos usuarios, revisar y editar antes de confirmar la importación.
**Plataforma:** Web
**Precondiciones:**


Usuario autenticado con permisos para importación.

Archivo Excel válido con datos de usuarios estructurados correctamente.

**Datos de Prueba:** Template Excell con campos para la creación de usuario

**Pasos:**

1. Hacer clic en “Usuarios”.

2. Hacer clic en el botón “Import”.

3. Seleccionar el archivo “usuarios_import.xlsx”.

4. Hacer clic en “Siguiente”.

5. Revisar la previsualización; editar registros si es posible.

6. Confirmar la importación.

**Resultado Esperado:**** **Recepción de correo 

**Resultado Obtenido:**** **NA
**Estado:** Bloqueado
**Observaciones:**** **No se ah implementado , no se cuenta con plantilla de Excel en especifico
 

CP-20: **Creación de un nuevo tipo de trámite**
**Descripción:** Validar que el usuario puede crear un nuevo tipo de trámite a través del formulario correspondiente, y que el nuevo tipo de trámite aparece luego en la tabla.
**Plataforma:** Web
**Precondiciones:**

Usuario autenticado con permisos 

**Datos de Prueba:**

Tipo de trámite: “Prueba”

**Pasos:**

1. Hacer clic en "Tipo de trámites" en el menú.

2. Hacer clic en el botón "Crear tipo de trámite".

3. Llenar el campo Tipo de trámite, seleccionar Traslado Foraneo o local 

4. Guardar la información.

**Resultado Esperado:**

El nuevo tipo de trámite se guarda correctamente y es visible en la tabla junto con la fecha de creación.

**Resultado Obtenido:**

El nuevo tipo de trámite se guarda correctamente y es visible en la tabla junto con la fecha de creación.

**Estado:** Correcto 
**Observaciones:**NA




CP-21: **Visualización de la tabla de zonas**
**Descripción:** Verificar que al hacer clic en la opción "Zonas" se muestra una tabla con las columnas "Zona" y "Fecha de creación".
**Plataforma:** Web
**Precondiciones:**

Usuario autenticado con acceso a la sección.

Al menos una zona registrada previamente en el sistema.

**Datos de Prueba:**NA

**Pasos:**

1. Hacer clic en el menú “Zonas”.

2. Observar la tabla presentada.

**Resultado Esperado:**** **La tabla muestra correctamente las columnas "Zona" y "Fecha de creación" con datos válidos y correctamente alineados.

**Resultado Obtenido:**** **La tabla muestra correctamente las columnas "Zona" y "Fecha de creación" con datos válidos y correctamente alineados.

**Estado:** Correcto 
**Observaciones:**NA


CP-22: **Creación de una nueva zona**
**Descripción:** Validar que al hacer clic en el botón “Crear Zona” se despliega el formulario con los campos requeridos, y que es posible crear una zona llenando los campos y usando las opciones de guardar.
**Plataforma:** Web
**Precondiciones:**

Usuario autenticado con permisos de creación para esta sección.

**Datos de Prueba:**

Zona: "Prueba"

Descripción: "Prueba"

**Pasos:**

1. Hacer clic en “Zonas”.

2. Hacer clic en el botón “Crear Zona”.

3. Completar los campos: Zona y Descripción.

4. Hacer clic en “Crear”.

**Resultado Esperado:** La zona es creada correctamente y aparece en la tabla de zonas.

**Resultado Obtenido:** La zona es creada correctamente y aparece en la tabla de zonas.

**Estado:** Correcto
**Observaciones:**


Verificar la validación de campos obligatorios, mensajes de éxito y correcto refresco en la tabla.

CP-23: **Visualización de la tabla de hoteles****
****Descripción:** Verificar que al hacer clic en la sección “Hoteles” se despliega una tabla con las columnas: zona, hotel, dirección y beneficios.
**Plataforma:** Web
**Precondiciones:**

Usuario autenticado 

Al menos un hotel registrado en el sistema.

**Datos de Prueba:** NA
**Pasos:**

1. Hacer clic en "Hoteles" en el menú principal.

2. Observar la tabla desplegada.

**Resultado Esperado:** La tabla muestra correctamente los campos de zona, hotel, dirección y beneficios para cada registro disponible.

**Resultado Obtenido:** La tabla muestra correctamente los campos de zona, hotel, dirección y beneficios para cada registro disponible.
**Estado:** correcto
**Observaciones:**NA
















CP-24: **Creación de lista de hoteles** 
**Descripción:** Validar que al hacer clic en “Crear lista de hoteles” se despliega un formulario con todos los campos requeridos, incluyendo selección de zona, datos generales, bancarios, beneficios (toggles), tarifas y otros detalles, y que el registro se completa exitosamente.
**Plataforma:** Web
**Precondiciones:**

Usuario autenticado con permiso 

Zonas previamente registradas para selección.

**Datos de Prueba:**

Zona

Nombre hotel

Razón social

Dirección

Número de teléfono

Número local

Datos bancarios

Beneficios

Tarifas

**Pasos:**

1. Hacer clic en “Hoteles”.

2. Hacer clic en “Crear lista de hoteles”.

3. Desplegar y completar todos los campos del formulario 

4. Hacer clic en el botón “Crear”.

**Resultado ****Esperado:** El hotel se registra correctamente y aparece en la tabla general, mostrando todos los campos, incluidas las tarifas y beneficios seleccionados.

 **Resultado Obtenido:** El hotel se registra correctamente y aparece en la tabla general, mostrando todos los campos, incluidas las tarifas y beneficios seleccionados.

**Estado:** Correcto 
**Observaciones:**NA
 





Validación requerida alerta cambiar a español 





CP-25: **Carga**** masiva de hoteles desde archivo Excel**
**Descripción:** Validar el flujo de carga masiva de hoteles, desde la selección del archivo tipo Excel hasta la revisión y posible edición antes de confirmar la carga.
Plataforma: Web
**Precondiciones:**

Usuario autenticado 

Archivo Excel con estructura válida y al menos 2 hoteles de ejemplo.

Datos de Prueba: Archivo Excel

**Pasos:**

1. Ir a “Hoteles”.

2. Hacer clic en el botón “Carga Masiva”.

3. Seleccionar el archivo “hoteles_ejemplo.xlsx” en el campo correspondiente.

4. Hacer clic en “Siguiente”.

6. Confirmar la carga.

**Resultado Esperado:**

Los hoteles en el archivo aparecen en la tabla tras carga masiva, con la información correctamente distribuida en cada campo.

**Resultado Obtenido:** fallo al adjuntar archivo 
**Estado: **Fallido**
Observaciones:**


CP-26: **Edición de hotel: activar y desactivar beneficios existentes**

**Descripción:** Verificar que se puedan activar y desactivar beneficios de un hotel existente y que los cambios se reflejen en la tabla.

**Plataforma:** Web

**Precondiciones**: Existir un hotel con beneficios ya asignados. El usuario debe tener permisos de edición.

**Datos de Prueba:** Hotel con beneficios preexistentes (ej. "wifi" activado, "gimnasio" desactivado).

**Pasos:**

En el listado de hoteles, seleccionar un hotel que ya tenga algunos beneficios asignados.

Hacer clic en "Editar".

Activar un beneficio que antes no tenía 

Desactivar un beneficio que sí tenía 

Guardar los cambios.

Volver a la tabla de hoteles y verificar los beneficios mostrados.

**Resultado Esperado:** Los cambios se guardan correctamente. En la tabla, el hotel refleja el nuevo estado: el beneficio activado aparece, el desactivado desaparece.

**Resultado Obtenido:** Edición de beneficios correcto.

**Estado:** Correcto

**Observaciones:** Para el filtrado de las columnas mostrar o ocultar solo se observan como opciones “Comentario estacionamiento “, “Personal”, se sugiere agregar el resto de opciones al filtrado



CP-27: **Envío de correo electrónico al crear solicitud de viático**

**Descripción:** Verificar que, al crear una nueva solicitud de viático, se envíen correos electrónicos de notificación al analista de viáticos y al supervisor correspondiente.

**Plataforma:** Web

**Precondiciones:** Empleado con sesión activa cuyo departamento tenga un supervisor asignado. Tener un analista de viáticos configurado en el sistema.

**Datos de Prueba:** Usuario solicitante, supervisor asignado, analista de viáticos.

**Pasos:**

Iniciar sesión 

Crear una nueva solicitud de viático (completar todos los datos requeridos).

Guardar la solicitud.

Revisar la bandeja de entrada del analista de viáticos y del supervisor del departamento.

**Resultado Esperado:** El analista de viáticos y el supervisor reciben un correo electrónico con la información de la solicitud: nombre del solicitante, datos de las personas que viajan, y un botón que redirige a la página de revisión de viáticos.
**Estado:** Bloqueado

**Resultado Obtenido:**  No es posible verificar la recepción de correo ya que extrae la información de profit y envia directamente los correos  no disponible en el ambiente de prueba

Observaciones: NA

CP-28: **Envío y recepción de notificación ****push**

**Descripción:** **Verificar que se puedan enviar y recibir notificaciones ****push** 

**Plataforma:** Web

**Precondiciones:** Usuarios con sesión activa.

**Datos de Prueba:** Usuario administrador, usuario destinatario (solicitante y supervisor).

**Pasos:**

Crear solicitud de viáticos 

Verificar notificación push por cada rol 

**Resultado Esperado:** La notificación push aparece en la interfaz del usuario destinatario 

**Resultado Obtenido:** Se crearon viáticos de prueba para las cuentas solicitante@example.com y supervisor@example.com. No se observó envío o recepción de notificaciones push.

**Estado:** Fallido

**Observaciones**: N/A


Rechazo en una solicitud de viatico notificación Error

  

CP-29: **Acceso al formulario de valoración de hotel desde solicitud aprobada**

**Descripción:** Verificar que el botón para valorar un hotel esté visible y accesible desde una solicitud de viático que ya se encuentra aprobada.

**Plataforma:** Web

**Precondiciones**: Existir una solicitud de viático en estado "Aprobada" que esté asociada a un hotel.

**Datos de Prueba**: Solicitud de viático aprobada con hotel registrado.

Pasos:

Como usuario, ingresar al módulo de solicitudes de viático.

Buscar una solicitud que ya esté aprobada.

Localizar el botón amarillo "Valorar Hotel".

Hacer clic en el botón.

**Resultado Esperado:** Se abre un modal o formulario que permite calificar el hotel 

**Resultado Obtenido:** Función de valoración activa, registro de valoración de hotel en solicitudes aun sin aprobar / sin hotel registrado. 

**Estado:** Correcto (Con observaciones)

**Observaciones:**  Actualmente, es posible realizar una valoración en solicitudes que no cuentan con hoteles registrados o que están canceladas, se sugiere estar activas por ejemplo únicamente para aquellas solicitudes que ya han sido aprobadas y que cumplen con la condición de tener hoteles ya registrado el cual valorar.

CP-30: **Validación de correo duplicado en creación de usuario**
**Descripción:** Verificar que al intentar crear un usuario con un correo electrónico que ya está registrado, la aplicación muestre alerta de error claro y no permita la creación.
**Plataforma:** Web.
**Precondiciones:**

Usuario con permisos de administración 

**Pasos:**

Navegar a Ajustes > Usuarios y hacer clic en “Crear usuario”.

Completar todos los campos obligatorios nombre , Apellido , Cedula , Rol , Empresa , Departamento , Correo electrónico , Contraseña .

En el campo “Correo electrónico”, ingresar “admin@admin.com”.

Hacer clic en el botón Crear.

Observar el mensaje mostrado en pantalla.

**Resultado Esperado:**

El sistema debe mostrar un mensaje de error indicando que el correo electrónico ya está registrado (ej. “El correo electrónico ya existe”).

No debe permitirse la creación del usuario y el formulario debe permanecer en pantalla sin recargarse completamente (o con los datos ingresados).

**Resultado Obtenido:**  Sin mensaje de alerta, app se rompe sale del formulario.
**Estado: **Fallido

 **Observaciones:** NA


