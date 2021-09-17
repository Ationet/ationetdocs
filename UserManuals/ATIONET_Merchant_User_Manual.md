![ationetlogo](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/ATIOnetLogo_250x70.png)

|**Información del Documento**|.|
|--- |--- |
|**Archivo:**|ATIONET_Merchant_User_Manual-ES.md|
|**Versión Doc:**|1.0|
|**Fecha Liberación:**|17, Sep 2021|
|**Autor:**|ATIONET LLC|


|**Bitácora de Cambios**|.|.|
|--- |--- |--- |
|**Ver.**|**Fecha**|**Resumen de Cambios**|
|1.0|17/Sep/2021|- Versión Inicial

# Contenido

- [Resumen](#resumen)
- [Definiciones](#definiciones)
	- [Contrato](#contrato)
	- [Subcuenta](#subcuenta)
	- [Compañía](#compañía)
	- [Identificador](#identificador)
	- [Sitio](#sitio)
	- [Vehículo](#vehículo)
	- [Conductor](#conductor)
	- [Terminal](#terminal)
- [Menú Navegación](#menú-navegación)
- [Mis Preferencias](#mis-preferencias)
- [Tablero](#tablero)
	- [Estado General](#estado-general)
	- [Unidades/Mes](#unidadesmes)
	- [Transacciones del Día](#transacciones-del-día)
	- [Lista de Pre-autorizaciones Pendientes](#lista-de-pre-autorizaciones-pendientes)
	- [Transacciones Marcadas en el Mes Actual](#transacciones-marcadas-en-el-mes-actual)
	- [Contratos Sin Actividad](#contratos-sin-actividad)
	- [Transacciones Recientes](#transacciones-recientes)
	- [Listado de Contratos con Bajo Saldo](#listado-de-contratos-con-bajo-saldo)
	- [Actualizaciones de Identificadores del último mes](#actualizaciones-de-identificadores-del-último-mes)
	- [Estado de Terminales](#estado-de-terminales)
- [Favoritos](#favoritos)
- [Reportes](#reportes)
	- [Sitios](#sitios)
	- [Transacciones](#transacciones)
- [Administración](#administración)
	- [Combustibles](#combustibles)
	- [Documentos Externos](#documentos-externos)
	- [Notificaciones](#notificaciones)
	- [Sitios](#sitios-1)
	- [Terminales/Controladores](#terminales--controladores)
	- [Usuarios](#usuarios)
- [Flotas](#flotas)
	- [Autorizaciones Pendientes](#autorizaciones-pendientes)
	- [Contingencia](#contingencia)
	- [Excepciones](#excepciones)
	- [Transacciones](#transacciones-1)
	- [Transacciones Desconocidas](#transacciones-desconocidas)
	- [Transacciones por Sitio](#transacciones-por-sitio)
	- [Transacciones Rechazadas](#transacciones-rechazadas)
- [Liquidaciones](#liquidaciones)
	- [Cargos Externos](#cargos-externos)
	- [Comprobantes de Comisión](#comprobantes-de-comisión)
	- [Documentos de Cargo](#documentos-de-cargo)
	- [Documentos de Liquidación](#documentos-de-liquidaciones)
	- [Estados de Cuenta](#estados-de-cuenta)
	- [Items Liquidados](#items-liquidados)
- [Inventario](#inventario)
	- [Graficos de Inventario](#graficos-de-inventario)
	- [Inventarios](#inventarios)
	- [Recepciones](#recepciones)
	- [Reconciliación Inventario](#reconciliación-inventario)

# Resumen
ATIONET se basa en la premisa de que las comunicaciones en línea entre los sitios y el portal web son posibles, sin embargo, proporciona sólidos procedimientos de contingencia en caso de un error de comunicación.
La plataforma ATIONET es un servicio de gestión de flotas con una oferta innovadora y única en el mercado. Procesamiento en la nube, 100% basado en la web, acceso multiusuario, disponibilidad y compartición de datos, actualizaciones instantáneas, seguridad, copia de seguridad automática y reducción del papeleo.
ATIONET es un portal web para empresas de servicios de flotas que permite el procesamiento de transacciones desde cualquier aplicación de punto de venta a través de una interfaz sencilla y fiable. 
ATIONET puede instalarse en cualquier estación de servicio con uno o varios programas de servicio de flotas. El portal web permite a los gestores de flotas un acceso completo a la información de sus vehículos.
ATIONET hace posible que el gestor de la flota opere, supervise, cambie y edite la información de la flota en tiempo real.


# Definiciones

## Contrato 
El contrato es la relación que existe entre la Network y el cliente, en la que se orienta, por ejemplo, si será de cantidad o volumen, el precio al que se va a vender el combustible, en qué sitios se puede cargar, entre otros.

## Subcuenta
Cada vez que se asocia un identificador a un vehículo o conductor, se crea una subcuenta. La subcuenta es en definitiva quien va a tener una cuenta corriente, la subcuenta va a poder recibir depósitos de dinero o producto. Las reglas también afectan a la subcuenta.
Las subcuentas dependen jerárquicamente del contrato.

## Compañía
En ATIONET la compañía se refiere a la entidad propietaria de la flota. Es la que gestiona los vehículos, los conductores y las reglas de la flota.

## Identificador
El identificador es el medio físico utilizado por ATIONET para identificar un vehículo o conductor. ATIONET soporta varios tipos de identificadores, como tarjeta, TAG, chip, tarjeta ATIONET, entrada manual, código de barras e iButton. Cuando se asocia un identificador a un vehículo o conductor, se crea una subcuenta.

## Sitio
El Sitio representa la estación de servicio. A un sitio se le asigna un terminal/controlador y también puede tener reglas de localización asociadas.

## Vehículo 
Los vehículos pueden estar asociados o agrupados por una flota, pueden tener reglas asociadas y en el momento de relacionarse con un identificador se crea una subcuenta. También pueden tener un conductor asociado.

## Conductor
El conductor en ATIONET es la persona que se identifica como chófer. Si a este conductor se le asigna un identificador, se crea una subcuenta. Los conductores también pueden tener reglas asociadas.

## Terminal
El terminal (o controlador) es la representación del controlador del dispensador, que debe ser parametrizado de forma particular según el tipo de terminal. Los terminales que maneja ATIONET son: ATIO-NanoCPI, ATIO-Standalone, ATIO-CG, VF-Sapphire, VF-Commander, VF-Ruby, ControlGas, entre otros.


# Menú Navegación
ATIONET tiene un menú de acceso rápido situado en la parte izquierda de la web. Desde este menú se puede acceder a diferentes opciones. El menú está dividido en: Tablero, Favoritos, Reportes, Administración, Flotas, Liquidación, Configuración y Bitácora de Auditoria.

# Mis Preferencias
Dentro de esta sección cada usuario puede personalizar sus preferencias del portal.

1. **Rol por Defecto:** Seleccione el rol por defecto al iniciar la sesión.

![Rol por defecto](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Mis%20Preferencias/Rol%20por%20Defecto.PNG)

2. **Imagen de Perfil:** Cambia la imagen de perfil de tu usuario.

![Imagen de perfil](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Mis%20Preferencias/Foto%20de%20Perfil.PNG)

3. **Cambiar la Contraseña:** Cambia la contraseña de tu usuario.

![Cambiar contraseña](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Mis%20Preferencias/Cambio%20Contrase%C3%B1a.PNG)

Para editar su contraseña, haga clic en el enlace ***change password***.

![Cambiar contraseña nueva](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Mis%20Preferencias/Cambio%20Contrase%C3%B1a%20Nuevo.PNG)

4. **Configuración de Widgets:** Selecciona los widgets que se mostrarán en tu panel de control.

![Configuración de widgets](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Mis%20Preferencias/Widgets.PNG)

# Tablero
El Tablero es una página donde se tiene una visión global del funcionamiento de su Compañía. El tablero cuenta con widgets específicos que le ayudarán a tomar decisiones preventivas o correctivas en función de la información y los datos que muestran. Los datos que se muestran en el Tablero son datos en tiempo real y algunos de los widgets se actualizan automáticamente.

Estos pueden ser eliminados o añadidos según las necesidades del usuario en la opción **Mis Preferencias**. También se pueden colocar en el tablero según el nivel de visibilidad que se quiera dar a cada uno.

## Estado General
Este widget es muy importante a la hora de poner en marcha la Network. Este widget nos da información de los parámetros que necesitamos configurar para estar operativos. Nos avisa cuando, por ejemplo, no tenemos vehículos o identificaciones creadas entre otros parámetros.
Este widget puede mostrar **Avisos** (icono amarillo) cuando el funcionamiento de la red no está en juego, pero si muestra una cruz roja indica que la red no está operativa.

![Estado General](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Tablero/Estado%20General.PNG)

## Unidades/Mes
Las "Unidades/Mes" indican la cantidad de cada combustible dispensado en el último mes. El último mes son los últimos 30 días desde el día de la fecha. Este widget tiene la capacidad de filtrar por Sitio, Ciudad y Flota. Debe seleccionar el filtro y luego introducir el valor por el que se debe filtrar. Este último campo es de tipo "autocompletado".

![Unidades/Meses](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Tablero/Unidades-Mes.PNG)

## Transacciones del Día
Este widget contiene un gráfico circular que muestra muy rápidamente cuántas transacciones fueron aprobadas y cuántas fueron rechazadas durante el día.

![Transacciones del Día](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Tablero/Transacciones%20del%20D%C3%ADa.PNG)

## Lista de Pre-Autorizaciones Pendientes
Este widget de lista muestra todas las pre-autorizaciones que aún no han recibido la finalización de venta. (Para más detalles sobre el flujo de transacciones consulte este [documento]( https://github.com/Ationet/ationetdocs/blob/master/AN-Transaction_Flows-TechGuide.md)).

Muestra 7 columnas:

1. **Código de autorización:** El código de autorización asignado a la transacción.
2. **Compañía:** La empresa a la que pertenece el vehículo en cuestión.
3. **Subcuenta:** La subcuenta que solicitó la pre-autorización.
4. **Sitio:** El sitio donde se realizó la transacción.
5. **Autorizado:** El importe que se autorizó en la pre-autorización.
6. **Pos:** Posición o bomba informada por el punto de venta o controlador.
7. **Age:** El tiempo en minutos que ha estado vigente esta pre-autorización.

Las pre-autorizaciones pendientes deben ser despachos en curso, si hay registros en este widget con una Age alta, significa que el punto de venta o controlador no envió la transacción de finalización o la transacción de cancelación en el caso de que el combustible no haya sido despachado.

![Lista de autorizaciones pendientes](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Tablero/Lista%20de%20Pre-Autorizaciones%20Pendientes.PNG)

## Transacciones Marcadas en el Mes Actual
A continuación se muestran todas las transacciones que fueron rechazadas por alguna de las validaciones realizadas por ATIONET en el proceso de autorización. Ya sea por falta de saldo o por reglas entre otras validaciones.

![Transacciones marcadas](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Tablero/Transacciones%20Marcadas%20en%20el%20Mes%20Actual.PNG)

## Contratos sin Actividad
Muestra la lista de contratos que nunca estuvieron activos.

![Contratos sin actividad](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Tablero/Contratos%20sin%20Actividad.PNG)

## Transacciones Recientes
A continuación se muestran las últimas 20 transacciones realizadas. Muestra los datos más relevantes para poder identificarla, en caso de necesitar más información sobre la transacción puede pulsar sobre el código de autorización, que le llevará a la vista de detalles de la transacción.

![Transacciones recientes](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Tablero/Transacciones%20Recientes.PNG)

## Listado de Contratos con Bajo Saldo
Muestra la lista de contratos con saldo bajo para operar 4 días más. Este cálculo se basa en el uso. La columna **Días restantes** muestra el número de días que le quedan al contrato basado en el análisis de uso. Este número no es exacto y puede variar si el patrón de uso cambia.

![Listado de Saldo Bajo de Contrato](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Tablero/Contratos%20con%20Bajo%20Saldo.PNG)

## Actualizaciones de Identificadores del Último Mes
Este widget muestra la actividad de la administración de identificadores, muestra el número de identificadores que fueron modificados agrupados por estado.

1. **Asignado:** El número de identificaciones que cambiaron al estado **Asignado**.
2. **Disponible:** El número de identificadores que cambiaron al estado **Disponible**.
3. **Cancelado:** El número de identificaciones que cambiaron al estado **Cancelado**.
4. **Reportado:** El número de identificaciones que cambiaron al estado **Reportado**.
5. **Suspendido:** El número de identificaciones que han pasado al estado **Suspendido**.

![Actualizaciones de identificadores del último mes](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Tablero/Actualizaciones%20de%20Identificadores.PNG)

## Estado de Terminales
Todos los terminales que están conectados de forma nativa a ATIONET envían un mensaje regular indicando que están activos. Si el terminal informó del estado en las últimas 5 horas, el terminal se mostrará con el icono verde, si no informó en las últimas 5 horas el icono será rojo.
La columna **Edad** muestra el número de minutos transcurridos desde la última vez que se informó del terminal. 

![Estado del terminal](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Tablero/Estado%20Terminales.PNG)


# Favoritos
Hay entidades que pueden requerir un seguimiento diario por parte de ciertos usuarios. Para facilitar esta tarea, se pueden añadir algunas secciones a la lista de **Favoritos**. Una vez introducida una sección a esta lista, el acceso es más rápido y directo, sin necesidad de introducir filtros cada vez que se quiera buscar.
Una vez dentro de la página de Favoritos, al hacer clic en el enlace de la columna **Tipo**, será redirigido a la vista detallada de esa sección.
Si desea eliminar una sección de la lista de Favoritos, haga clic en el icono de la derecha con forma de cruz.

![Favoritos](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20Merchant%20ATIONet/Favoritos.PNG)

# Reportes
En ATIONET se consideran reportes aquellos listados de información que van a ser impresos y archivados en formato físico. Cuando se imprimen, ATIONET añade automáticamente una cabecera con el logotipo de la suscripción.

## Sitios

## Transacciones
Este informe muestra la lista de transacciones realizadas, ordenadas por fecha. El primer campo del panel de filtros indica por qué campo se ordenará la lista, el campo seleccionado en esta lista se mostrará en la primera columna.

![Transacciones](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20Merchant%20ATIONet/Reportes/Transacciones%20por%20Sitio.PNG)

Una vez seleccionado el filtro pulse el botón ***Imprimir***, esto mostrará una ventana emergente con la información seleccionada.
La información se muestra en un formato listo para imprimir, incluyendo el logotipo de la suscripción y la fecha y hora de generación del informe.

Esta ventana emergente tiene un botón de impresión que al ser pulsado abre la ventana de impresión por defecto del navegador de Internet.

![Transacciones](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20Merchant%20ATIONet/Reportes/Transacciones.PNG)

# Administración
Dentro de este módulo podrá gestionar Combustibles, Notificaciones, Sitios y Terminales entre otras cosas.

## Combustibles
Esta vista enumera las asignaciones de combustible y su respectivo código para todos los sitios que tienen activada la opción **Mapeo de Combustible Requerido** (para más información sobre el mapeo de combustible haga clic [aquí](#sitios)). Para facilitar las consultas, hay un panel de filtros en la parte superior.

![Combustibles](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20Merchant%20ATIONet/Administraci%C3%B3n/Combustibles.PNG)

## Documentos Externos
En esta vista están listados todos los documentos externos cargados por la Compañía (mediante APIs) y la posibilidad de descargarlos. Un documento externo es un documento asociado a una operación realizada externamente a ATIONET.

![Documentos Externos](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20Company%20ATIONet/Administraci%C3%B3n/Documentos%20Externos%20Lista.PNG)

## Notificaciones
En esta sección cada usuario puede seleccionar sus propias notificaciones para recibirlas por correo electrónico o sms.

![Notificaciones](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20Merchant%20ATIONet/Administraci%C3%B3n/Notificaciones.PNG)

1. ***Inventario***
   * **Notificación de nueva entrega:** Recibe una notificación por cada recepción detectada.
   * **Notificación de inventario bajo:** Recibe una notificación cuando el inventario es bajo.
   * **Notificación de altura de agua baja:** Recibe una notificación cuando el nivel de agua es bajo.
2. ***Liquidación***
   * **Comprobantes de Comisión:** Recibe una notificación cuando se detectan comprobantes de comisión.
   * **Cargos externos:** Recibe una notificación cuando se detectan cargos externos.

## Sitios
En ATIONET el sitio representa la estación de servicio. Esta sección muestra los sitios ya creados por la Network. Para facilitar las consultas, hay un panel de filtros en la parte superior.

![Sitios](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20Merchant%20ATIONet/Administraci%C3%B3n/Sitios.PNG)

## Terminales / Controladores
En esta sección se listan todos los terminales/controladores creados por la Network. El terminal es el punto de venta del sitio y el controlador gestiona los surtidores. Para facilitar las consultas, hay un panel de filtros en la parte superior.

![Terminales](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20Merchant%20ATIONet/Administraci%C3%B3n/Terminales-Controladores.PNG)

## Usuarios
En esta sección puede ver, crear o editar usuarios para el Comercio. Puede editarlos haciendo clic en el icono del lápiz en la columna de opciones, activar/desactivar un usuario haciendo clic en el icono del candado y restablecer la contraseña con el icono de la estrella.

![Usuarios](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20Merchant%20ATIONet/Administraci%C3%B3n/Usuarios.PNG)

Para crear un usuario, haga clic en el botón **Nuevo**.

![Usuarios nuevos](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Administraci%C3%B3n/Usuarios%20Nuevo.PNG)

Los campos a completar son los siguientes:

* **Correo del usuario:** La dirección de correo electrónico del usuario.
* **Nombre:** El nombre del usuario.
* **Seguridad Social:** El documento del usuario.
* **Calle 1:** La calle donde reside el usuario.
* **Calle 2:** Otra calle de referencia, como puede ser la de la esquina.
* **País:** El país del usuario.
* **Estado:** El estado del país del usuario.
* **Código postal:** El código postal de la localidad donde reside el usuario.
* **Número de teléfono 1:** El teléfono del usuario.
* **Número de teléfono:** El otro teléfono del usuario si está disponible.

<br>

* **Rol:** El rol que asumirá el nuevo usuario.
* **Entidad:** La entidad asignada al usuario.

Cuando haya terminado de rellenar los campos, presione el botón **Guardar**.

# Flotas
Dentro de este módulo se pueden gestionar Contingencias, Transacciones, Excepciones y Rechazos entre otras cosas.

## Autorizaciones Pendientes
En ATIONET las autorizaciones pendientes son aquellas operaciones que aún no han recibido la transacción de finalización, pero que han sido preautorizadas. La información que se ve en esta vista son los despachos que están actualmente en curso. Si por alguna razón hay preautorizaciones antiguas, es probable que el TPV no haya enviado la transacción de finalización o la transacción de cancelación si el despacho no se ha completado.

Tenga en cuenta que en el momento de la preautorización, ATIONET congeló el importe de la autorización de la cuenta corriente para la subcuenta asociada. Esta vista presenta todos los campos necesarios para identificar la transacción y la subcuenta. Si necesita ver más detalles, al hacer clic en el código de autorización accederá a la vista de detalles de la transacción.

![Autorización pendiente](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Autorizaciones%20Pendientes.PNG)

## Contingencia
En ATIONET una contingencia es una operación introducida manualmente. En esta sección puede consultar y crear contingencias. Tenga en cuenta que las contingencias son transacciones sin autorización previa.

![Contingencia](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Contingencias.PNG)

Para crear una contingencia, haga click en el botón **Nuevo**.

![Contingencias Nueva](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Contingencias%20Nueva.PNG)

Los campos a completar son los siguientes:

* **Motivo:** Seleccione el motivo de la contingencia.
* **Fecha:** Introduzca la fecha de la contingencia.
* **Hora:** Introduzca la hora de la contingencia.
* **Sitio:** Seleccione el sitio asociado a la contingencia.
* **Terminal/Controlador:** Seleccione el terminal/controlador asociado a la contingencia.
* **Cuenta primaria:** Seleccione la subcuenta primaria asociada a la contingencia.
* **Cuenta secundaria:** Seleccione la subcuenta secundaria asociada a la contingencia.
* **Combustible:** Seleccione el combustible asociado a la contingencia.
* **Volumen Despachado:** Introduzca el volumen asociado a la contingencia.
* **Precio Unitario:** Introduzca el precio unitario asociado a la contingencia.
* **Monto Despachado:** Introduzca el monto asociado a la contingencia.
* **Turno:** Introduzca el turno asociado a la contingencia.
* **Surtidor:** Introduzca la bomba asociada a la contingencia.
* **Odómetro:** Introduzca el odómetro del vehículo asociado a la contingencia.
* **Horas de Motor:** Introduzca las horas de motor del vehículo asociado a la contingencia.
* **Id Conductor:** Introduzca el identificador del conductor asociado a la contingencia.
* **Id Vehículo:** Introduzca el identificador del vehículo asociado a la contingencia.
* **Encargado:** Introduzca el encargado asociado a la contingencia.
* **Lado de la Bomba:** Introduzca el lado de la bomba asociado a la contingencia.
* **Misceláneos:** Introduzca el misceláneos del vehículo asociados a la contingencia.
* **Número de Comprobante:** Introduzca el número de comprobante asociado a la contingencia.
* **Número de Orden de Compra:** Introduzca el número de orden de compra asociado a la contingencia.

Cuando haya terminado de rellenar los campos, presione el botón **Guardar**.

## Excepciones
ATIONET separa las transacciones no autorizadas en 2 secciones: **Excepciones** y [Transacciones Rechazadas] (#transacciones-rechazadas). Las excepciones son aquellas transacciones que no pasaron las validaciones duras del sistema o las que se detectan como posibles fraudes.

![Excepciones](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Excepciones.PNG)

En esta vista, al principio se puede filtrar por el tipo de excepción. Los tipos de excepciones disponibles son los siguientes:

![Excepciones Filtros](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Excepciones%20Filtros.PNG)

## Transacciones
La vista de transacciones es una de las más importantes en ATIONET. En esta vista puede ver todas las transacciones exitosas.

El panel de filtro tiene todos estos campos disponibles:

![Trasacciones - Filtro]()

* **Sitio:** Seleccione el sitio asociado a la transacción.
* **Terminal/Controlador:** Seleccione la terminal asociada a la transacción.
* **Combustible:** Seleccione el combustible asociado a la transacción.
* **Surtidor:** Introduzca el número de surtidor asociado a la transacción.
* **Fecha Desde/Hasta:** Introduzca las fechas de inicio y finalización asociadas a la transacción.
* **Hora Desde/Hasta:** Introduzca las horas de inicio y finalización asociadas a la transacción.
* **Modo:** Seleccione el modo de transacción (Contingencia, Fuera de línea o Estándar).

Una vez que haya filtrado, haga clic en ***Buscar*** y se listarán las transacciones que cumplen con el filtro.

![Transacciones]()

Si quiere ver el detalle de la transacción, presione sobre el **Número de Transacción** y esto le llevará a una vista detallada de la misma.

![Transacciones Detalles]()

## Transacciones Desconocidas
Las transacciones desconocidas son aquellas que la Compañía dice desconocer. En esta sección se pueden consultar las transacciones desconocidas, listadas por código, fecha, motivo, estado, número de transacción, compañía, sitio. También está el comentario de la compañía, del comercio y de la network.

![Transacciones desconocidas](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Transacciones%20Desconocidas.PNG)

## Transacciones por Sitio
En esta vista se pueden ver las transacciones agrupadas por el sitio donde se realizaron. Los botones de la parte superior izquierda sirven para imprimir la tabla o crear un archivo Excel a partir de ella, respectivamente.

![Transacciones por Sitio](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Transacciones%20por%20Sitio.PNG)

## Transacciones Rechazadas
ATIONET separa las transacciones no autorizadas en 2 secciones: [Excepciones](#excepciones) y **Transacciones Rechazadas**.

Las Transacciones Rechazadas son aquellas que lograron pasar las autenticaciones duras de ATIONET, pero fueron rechazadas por otras validaciones como una regla insatisfecha o una validación de saldo.

![Transacciones Rechazadas](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Transacciones%20Rechazadas.PNG)

En esta vista, al principio se puede filtrar por el tipo de rechazo. Los tipos de rechazo disponibles son los siguientes:

![Transacciones Rechazadas Filtros](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Transacciones%20Rechazadas%20Filtros.PNG)

# Liquidaciones

## Cargos Externos
En esta sección podrá subir un comprobante asociado a un documento externo. El comprobante toma el importe informado en el documento y se debe adjuntar un archivo/comprobante que respalde la información cargada.

![Cargos Externos](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20Company%20ATIONet/Liquidaci%C3%B3n/Cargos%20Externos.PNG)

Para crear un cargo externo, haga click en el botón **Nuevo**.

![Cargos Externos Nuevo](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20Company%20ATIONet/Liquidaci%C3%B3n/Cargos%20Externos%20Nuevo.PNG)

Los campos a completar son los siguientes:

* **Fecha:** Ingresar la fecha del cargo externo.
* **Documento Externo:** Seleccionar el documento externo asociado al cargo.
* **Descripción:** Ingresar la descripción del cargo externo.
* **Tipo de Comprobante:** Seleccionar el tipo de comprobante asociado al cargo.
* **Numero de Comprobante:** Ingresar el número del comprobante asociado al cargo.
* **Código de Autorización Electrónica:** Ingresar el código de autorización electrónica asociado al cargo.
* **Fecha de expiración:** Ingresar la fecha de expiración del cargo externo.
* **Moneda:** Seleccionar la moneda del cargo externo.
* **Monto Neto:** Ingresar el monto neto del cargo externo.
* **Exento de Impuestos:** Marque esta opción si el cargo es libre de impuestos.

<br>

* **Impuesto:** Ingreasr el impuesto asociado al cargo externo.

Esta vista tiene un flujo de aprobación asociado al mismo, en donde:
* La Compañía ingresa el cargo externo y queda en estado **Nuevo** (se permite editar o eliminar el mismo).
* La misma Compañía puede cambiar el estado a **Aprobado por la Compañía** ó **Rechazado por la Compañía**.

Si el cargo es rechazado, el flujo termina. En cambio, si es aprobado, la Network es responsable de revisar el **cargo externo** y puede de igual manera aprobar o rechazar el mismo.

## Comprobantes de Comisión
En esta sección podrá subir un comprobante asociado a un documento de cargo (un concepto de tipo comisión aplicado al contrato de comercio). El comprobante toma el importe informado en el documento y se debe adjuntar un archivo/comprobante que respalde la información cargada.

![Comprobantes de Comisión]()

Para crear un comprobante de comisión, haga click en el botón **Nuevo**.

![Comprobantes de Comisión Nuevo]()

Los campos a completar son los siguientes:

* **Fecha:** Ingresar la fecha del comprobante de comisión.
* **Número de Liquidación:** Seleccionar el número de liquidación asociado al comprobante.
* **Documento de Cargo:** Seleccionar el documento de cargo asociado al comprobante.
* **Descripción:** Ingresar la descripción del comprobante de comisión.
* **Tipo de Comprobante:** Seleccionar el tipo de comprobante.
* **Numero de Comprobante:** Ingresar el número del comprobante.
* **Código de Autorización Electrónica:** Ingresar el código de autorización electrónica asociado al comprobante.
* **Monto Neto:** Ingresar el monto neto del comprobante de comisión.
* **Exento de Impuestos:** Marque esta opción si el comprobante es libre de impuestos.

<br>

* **Impuesto:** Ingreasr el impuesto asociado al comprobante de comisión.

Esta vista tiene un flujo de aprobación asociado al mismo, en donde:
* El Comercio ingresa el comprobante de comisión y queda en estado **Nuevo** (se permite editar o eliminar el mismo).
* El mismo Comercio puede cambiar el estado a **Aprobado por el Comercio** ó **Rechazado por el Comercio**.

Si el comprobante es rechazado, el flujo termina. En cambio, si es aprobado, la Network es responsable de revisar el **comprobante de comisión** y puede de igual manera aprobar o rechazar el mismo.

## Documentos de Cargo
En esta sección podrá ver todos los conceptos aplicados agrupados por estado de cuenta. Si hace clic en el código, le redirigirá al detalle del mismo.

![Documentos de Cargo](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Liquidaciones/Documentos%20de%20Cargo.PNG)

## Documentos de Liquidaciones
En esta sección se pueden ver todos los estados de registro de los documentos de liquidación solicitados. Los estados posibles son: Pendiente, Procesando, Finalizado o Finalizado con errores.

![Documentos de Liquidaciones](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Liquidaciones/Documentos%20de%20Liquidaciones.PNG)

## Estados de Cuenta
En esta sección podrá ver y descargar los estados de cuenta de su Comercio. También puede generar los estados de cuenta en .pdf uno a uno, o dentro de la **Acción en Lote** generar un paquete.

![Estados de Cuenta](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Liquidaciones/Estados%20de%20Cuenta.PNG)

## Items Liquidados
En esta sección puede ver los conceptos aplicados para cada estado de cuenta.

![Liquidación](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Liquidaciones/Items%20Liquidados.PNG)

# Inventario

## Graficos de Inventario

## Inventarios

## Recepciones

## Reconciliación Inventario

