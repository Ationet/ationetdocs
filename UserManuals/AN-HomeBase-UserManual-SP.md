![ationetlogo](Content/Images/ATIOnetLogo_250x70.png)
# ATIONet - Manual de Usuario Autoconsumo

<table>
	<tr>
		<th colspan="2" align="left">Información documento</th>
	</tr>
	<tr>
		<td>Archivo:</td>
		<td>AN-HomeBase-UserManal-SP</td>
	</tr>
	<tr>
		<td>Version documento:</td>
		<td>1.2</td>
	</tr>
	<tr>
		<td>Fecha:</td>
		<td>15 Enero 2016</td>
	</tr>
	<tr>
		<td>Autor:</td>
		<td>ATIO International LLC</td>
	</tr>
</table>

<table>
	<tr>
		<th colspan="3" align="left">Change Log</th>
	</tr>
	<tr>
		<td>Ver.</td>
		<td>Fecha</td>
		<td>Detalle cambio</td>
	</tr>
	<tr valign="top">
		<td>1.0</td>
		<td>15 Enero 2016</td>
		<td>Version inicial.</td>
	</tr>
</table>

## Contents

<!-- MarkdownTOC depth=3 -->

- Visión general
- [Definiciones](#definiciones)
	- [Contrato](#contrato) 
	- [Sub cuenta](#sub-cuenta)
	- [Compañía](#compañía)
	- [Identificador](#identificador)
	- [Sitio](#sitio)
	- [Vehículo](#vehículo)
	- [Conductor](#conductor)
	- [Modulo offline](#modulo-offline)
- [Menú de Navegación](#menú-de-navegación)
	- [Tablero](#tablero)
		- [Estado General](#estado-general)
		- [Litros-Mes](#litros-mes)
		- [Transacciones del Día](#transacciones-del-día)
		- [Lista de Pre-Autorizaciones Pendientes](#lista-de-pre-autorizaciones-pendientes)
		- [Transacciones marcadas en ultimo mes](#transacciones-marcadas-en-ultimo-mes)
		- [Instalaciones](#instalaciones)
		- [Sub-cuentas con excepciones](#sub-cuentas-con-excepciones)
		- [Actualizaciones de Identificador en ultimo mes](#actualizaciones-de-identificador-en-ultimo-mes)
		- [Transacciones recientes](#transacciones-recientes)
		- [Listado de Sub-cuentas con bajo saldo](#listado-de-sub-cuentas-con-bajo-saldo)
		- [Estado de Terminales](#estado-de-terminales)
		- [Contratos sin actividad](#contratos-sin-actividad)
		- [Listado de contratos con bajo saldo](#listado-de-contratos-con-bajo-saldo)
	- [Favoritos](#favoritos)	
	- [Vistas](#vistas)
		- [Autorizaciones Pendientes](#autorizaciones-pendientes)
		- [Batch](#batch)
		- [Conductores](#conductores)
		- [Cuentas corrientes de Compañia](#cuentas-corrientes-de-compañía)
		- [Excepciones](#excepciones)
		- Rendimiento por Transacción
		- Rendimiento por Vehículo
		- [Transacciones](#transacciones)
		- Transacciones por Conductor
		- Transacciones por Flota
		- Transacciones por Sitio
		- Transacciones por Vehículo
		- [Transacciones Rechazadas](#transacciones-rechazadas)
		- [Transacciones sin Control](#transacciones-sin-control)
		- [Vehiculos](#vehiculos)
	- [Reportes](#reportes)
		- [Conductor](#conductor)
		- [Detalle de actividad por Vehículo](#detalle-de-actividad-por-vehículo)
		- [Sitios](#sitios)
		- [Transacciones](#transacciones)
		- [Vehiculo](#vehiculos)
	- Inventario
		- Grafico de Inventarios
		- Inventario
		- Recepciones
		- Reconciliazión Inventario 
	- [Administración](#administración)
		- [Clases de Vehículos](#clases-de-vehículos)
		- [Combustibles](#combustibles)
		- [Conceptos](#conceptos)
		- [Conductores](#conductores)
		- [Configuración](#configuración)
		- [Configuración de Fast Track](#configuración-de-fast-track)
		- [Contratos de Compañía](#Ccontratos-de-Compañia)
		- [Familias de Conceptos](#familias-de-conceptos)
		- [Flotas](#flotas)
		- [Identificaciones Solicitadas](#identificaciones-solicitadas)
		- [Identificadores](#Identificadores)
		- [Impuestos](#impuestos)
		- [Metodos de Pago](#metodos-de-pago)
		- [Modelos de Identificador](#modelo-de-identificador)
		- [Programas](#programas)
		- [Reglas](#reglas)
		- [Sitios](#Sitios)
		- [Terminales / Controladores](#Terminales/Controladores)
		- [Tipos de Documentos](#tipos-de-documentos)
		- [Transacciones Desconocidas](#transacciones-desconocidas)
		- [Transacciones Fuera de Sitio](#transacciones-fuera-de-sitio)
		- [Usuarios](#usuarios)
		- [Vehículos](#vehículos)
- [Mis Filtros](#mis-filtros)
- [Solución de Problemas](#solucion-de-problemas)
- [Mis Preferencias](#mis-preferencias)
- [Configuración Nano CPI para ATIONet](#configuración-nano-cpi-para-ationet)

<!-- /MarkdownTOC -->

## Visión General

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus mollis quam ac ligula maximus, vitae dictum lorem consequat. Curabitur interdum pretium cursus. Vestibulum pharetra sodales enim, ut vestibulum dui semper quis. Aliquam convallis nulla eu neque vestibulum eleifend. Nam feugiat leo a bibendum rutrum. Duis quis augue et dui vulputate rhoncus. Sed vitae felis fringilla, lacinia est vel, imperdiet leo. Sed suscipit neque risus, eu pharetra dolor rhoncus ac.

## Definiciones

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus mollis quam ac ligula maximus, vitae dictum lorem consequat. Curabitur interdum pretium cursus. Vestibulum pharetra sodales enim, ut vestibulum dui semper quis. Aliquam convallis nulla eu neque vestibulum eleifend. Nam feugiat leo a bibendum rutrum. Duis quis augue et dui vulputate rhoncus. Sed vitae felis fringilla, lacinia est vel, imperdiet leo. Sed suscipit neque risus, eu pharetra dolor rhoncus ac.

### Contrato 

En el tipo de suscripción auto consumo esta opción no es utilizada y no esta disponible.

### Sub Cuenta 

Cada vez que se asocia un identificador a un vehículo o un conductor se crea una sub cuenta. La sub cuenta es en definitiva quien va a tener una cuenta corriente, la sub cuenta va a poder recibir depósitos de dinero o producto. Las reglas también impactan a la sub cuenta.

Las sub cuentas dependen jerarquicamente del contrato.

### Compañía 

En el tipo de suscripción auto consumo esta opción no es utilizada y no esta disponible.

### Identificador 

El identificador es el medio físico que utiliza ATIONet para poder identificar un vehículo o un conductor. ATIONet soporte varios tipos de identificaciones, como ser tarjeta, tag (anillo), chip, tarjeta ATIONet, entrada manual, código de barras e iButton. Cuando se asocia un identificador a un Vehículo o Conductor se crea una sub cuenta.

### Sitio 

El Sitio representa a la estación de servicio. A un sitio se le asigna la terminal y también puede tener asociadas reglas de Ubicación.

### Vehículo 

Los vehículos pueden ser asociados o agrupados por una flota, pueden tener reglas asociadas y al momento de ser relacionados con un identificador se crea una sub cuenta. También pueden tener un conductor asociado.

### Conductor 

El Conductor es la persona que esta identificado en ATIONet como un conductor. Si a este conductor se le asigna un identificador, se crea una sub cuenta. Los conductores también pueden tener reglas asociadas.

### Modulo Offline 

El modulo offline de ATIONet se activa automáticamente cuando la estación de servicio se queda sin conexión a internet y las autorizaciones no se pueden procesar online. En este momento entra en juego el modulo offline. Para el controlador Nano CPI es totalmente transparente. Cuando el modulo offline recupera la conectividad envía toda la información procesada localmente y también baja las novedades. Mientras haya conectividad el modulo offline esta continuamente bajando las novedades (saldos, identificadores, reglas, etc) de ATIONet.

### Terminal 

La terminal (o controlador) es la representación del controlador de surtidores, que necesita parametrizarse de manera particular según el tipo de terminal. Las terminales que ATIONet maneja son ATIO-NanoCPI, ATIO-Standalone, ATIO-CG, VF-Standalone, VF-Sapphire, VF-Ruby, ControlGas y OPW-FSC3000. 

## Menú de Navegación

Ationet posee un menú de acceso rápido ubicado en la parte izquierda de la pagina. Desde este menú usted podrá acceder a las distintas opciones. el menú esta dividido en 7 secciones. (Tablero, Favoritos, Vistas, Reportes, Inventario, Administración y Bitácora)

### Tablero

El Tablero es una pagina donde usted tendrá una visión global de la operación de su red. El tablero posee widgets específicos que lo ayudaran a tomar decisiones preventiva o correctivas según la información y los datos que muestren. Los datos que se muestran en el Tablero, son datos en tiempo real. Algunos de los widgets se refrescan automáticamente.
Estos se pueden quitar o agregar según las necesidades del usuario. También se pueden acomodar en el tablero según el nivel de visibilidad que le quiera dar a cada uno.
La lista completa de widgets disponibles para las suscripciones "Autoconsumo" es la siguiente:

#### Estado General ####

Este widget es de suma importancia al poner en marcha la red. Este widget nos da información de que parámetros necesitamos configurar para quedar operativos. Nos advierte cuando por ejemplo no tenemos vehículos o identificaciones creadas entre otros parámetros.
Este widget puede mostrar "Advertencias" (ícono amarillo)cuando no esta en juego la operación de la red, pero si muestra una cruz roja indica que la red no esta operativa. 

![Estado General](Content/Includes/AN-HomeBase-UserManal-SP/estadoGeneral.png)
![Estado General](Content/Includes/AN-HomeBase-UserManal-SP/estadoGeneral2.png)

#### Litros-Mes

El de "Litros/Mes indica la cantidad que se despachó de cada combustible en el ultimo mes. Como ultimo mes se entiende a los últimos 30 días contando desde el día de la fecha. Este widget posee la capacidad de filtrar por Sitio, Ciudad y Flota. Se debe seleccionar el filtro y después se ingresa el valor por el cual se debe filtrar. Este ultimo campo es del tipo "auto complete".

![Litros Mes](Content/Includes/AN-HomeBase-UserManal-SP/litrosMes.png)

#### Transacciones del Día

Este widget contiene un gráfico de torta que en forma muy rápida se pueden ver cuantas transacciones se aprobaron y cuantas se rechazaron en el día.

![Transacciones Día](Content/Includes/AN-HomeBase-UserManal-SP/transaccionesDia.png)

#### Lista de Pre-Autorizaciones Pendientes

Este widget del tipo lista, muestra todas las pre autorizaciones que todavía no recibieron la transacción de finalización. (para mas detalles sobre el flujo de transacciones consulte este [documento](AN-Transaction_Flows-TechGuide.md)).
Este muestra 7 columnas:

1. ***Código de Autorización:*** El código de autorización asignado a la transacción
2. ***Compañía:*** La compañía a la que pertenece el vehículo en cuestión
3. ***Patente:*** La patente del vehículo
4. ***Sitio:*** El sitio donde se llevo a cabo la transacción
5. ***Autorizado:*** El monto que fue autorizado en la pre autorización
6. ***Pos:*** Posición o bomba informada por el punto de venta o controlador
7. ***Age:*** El tiempo en minutos que lleva vigente esa pre autorización

Las pre autorizaciones pendientes deberían ser despachos en curso, si hay registros en este widget con un Age alto, significa que el punto de venta o controlador no enviaron la transacción de finalización o la transacción de cancelación en el caso que no se haya despachado combustible.

![Pre Auth Pendientes](Content/Includes/AN-HomeBase-UserManal-SP/preauthPendientes.png)

#### Transacciones marcadas en ultimo mes

El siguiente muestra todas las transacciones que fueron rechazadas por cualquiera de las validaciones que hace Ationet en el proceso de autorización. Ya sean por falta de saldo o reglas entre otras validaciones. Para mas detalles sobre "Transacciones Rechazadas" consulte este documento: [TODO](#todo) 

![Transacciones Marcadas](Content/Includes/AN-HomeBase-UserManal-SP/transaccionesMarcadasUltimoMes.png)

#### Instalaciones

Cuando la red utiliza algún medio de identificación que requiera ser instalado (como por ejemplo un anillo o ring tag), Ationet administra la lista de instalaciones. Este widget muestra las instalaciones realizadas en las ultimas 5 semanas

![Instalaciones](Content/Includes/AN-HomeBase-UserManal-SP/instalaciones.png)

#### Sub-cuentas con excepciones

Este muestra todas las sub cuentas que tengan algo que prestarle atención, como por ejemplo:

1. ***Sin Identificadores:*** Son los vehículos o conductores que no tienen un identificador asociado
2. ***Con Identificadores inactivos:*** Son subcuentas que que tienen un identificador asociado que ha sido desactivado desde el portal
3. ***Con Identificadores suspendidos:*** Son subcuentas que que tienen un identificador que ha sido suspendido. ***Solo Ationet puede suspender un identificador***.
4. ***Con conductores o vehículos inactivos:*** Son subcuentas que que tienen un vehículo o conductor que no ha sido desactivado desde el portal

Para mas detalles sobre sub cuentas consulte: [Esta sección](#sub-cuenta)

![sub Cuentas con Excepciones](Content/Includes/AN-HomeBase-UserManal-SP/subcuentasConExcepciones.png)

#### Actualizaciones de Identificador en ultimo mes

Este widget muestra la actividad de la administración de los identificadores, muestra la cantidad de identificadores que fueron modificados agrupado por estado.

1. ***Asignada:*** La cantidad de identificadores que cambiaron al estado "Asignada"
2. ***Disponible:*** La cantidad de identificadores que cambiaron al estado "Disponible"
3. ***Cancelada:*** La cantidad de identificadores que cambiaron al estado "Cancelada"
4. ***Denunciada:*** La cantidad de identificadores que cambiaron al estado "Denunciada"
5. ***Suspendida:*** La cantidad de identificadores que cambiaron al estado "Suspendida"

![Actualizaciones de Identificadores](Content/Includes/AN-HomeBase-UserManal-SP/actualizacionIdentificadoresUltimoMes.png)

#### Transacciones recientes

El siguiente muestra las ultimas 20 transacciones finalizadas. Se muestran los datos mas relevantes para poder identificarla, en el caso de necesitar mas información sobre la transacción se puede hacer click sobre el código de autorización, eso lo llevara a la vista de detalles de la transacción.

![Transacciones Recientes](Content/Includes/AN-HomeBase-UserManal-SP/transaccionesRecientes.png)

#### Listado de Sub-cuentas con bajo saldo

Muestra la lista de sub cuentas que contengan bajo saldo para operar 4 días mas. Este calculo se hace en base al uso de cada sub cuenta. La columna "Días disponibles" muestra cantidad de días que le quedan a la sub cuenta basada en el análisis de uso. Este numero no es exacto y podría variar si el patrón de uso cambia.

![Sub Cuentas Bajo Saldo](Content/Includes/AN-HomeBase-UserManal-SP/subcuentasBajoSaldo.png)

#### Estado de Terminales

Todas las terminales que estén conectadas en forma nativa a ATIONet, envían en forma regular un mensaje indicando que están activas. Si la terminal reporto el estado en las ultimas 5 horas, la terminal se mostrara con el ícono verde, sino se reporto en las ultimas 5 horas el ícono sera rojo.
La columna ***"Age"*** muestra la cantidad de minutos que pasaron desde la ultima vez que se reporta la terminal. 

![Estado Terminales](Content/Includes/AN-HomeBase-UserManal-SP/estadoTerminales1.png)
![Estado Terminales](Content/Includes/AN-HomeBase-UserManal-SP/estadoTerminales2.png)

#### Contratos sin actividad

Muestra la lista de contratos que nunca tuvieron actividad.

![Contrato Sin Actividad](Content/Includes/AN-HomeBase-UserManal-SP/contratosSinActividad.png)

#### Listado de contratos con bajo saldo

Muestra la lista de contratos que contengan bajo saldo para operar 4 días mas. Este calculo se hace en base al uso. La columna "Días disponibles" muestra cantidad de días que le quedan al contrato basada en el análisis de uso. Este numero no es exacto y podría variar si el patrón de uso cambia.

![Contrato Bajo Saldo](Content/Includes/AN-HomeBase-UserManal-SP/contratoBajoSaldo.png)

### Favoritos

Las entidades Vehículos, Conductores, Sitios y Flotas son entidades que podrían requerir un control diario por parte de ciertos usuarios. Para facilitar esta tarea usted puede agregar alguna de estas entidades a la lista de Favoritos. Una vez ingresada una entidad a esta lista el acceso es mas rápido y directo, sin necesidad de ingresar filtros cada vez que la desea buscar. 

Una vez dentro de la pagina de Favoritos, al hacer click sobre el link de la columna "Tipo", usted sera redireccionado a la vista detallada de esa entidad. 

Si desea remover una entidad de la lista de Favoritos, haga click sobre el ícono de la derecha con forma de cruz.

![Favoritos](Content/Includes/AN-HomeBase-UserManal-SP/favoritos.png)

### Vistas

ATIONet dispone de una serie de vistas donde se puede visualizar información de la operación de la red. ATIONet considera una vista a toda aquella pantalla que ademas de poder visualizar información, también es exportable para un post procesamiento. A diferencia de los [***Reportes***](#reportes) que son pantallas que muestran información con un formato pensado para ser impreso y guardado.
Todas las vistas en ATIONet respetan una consistencia en estética y funcionalidad. Todas las vistas poseen una barra de herramientas con todas estas funciones (o al menos alguna de ellas)

![Vistas](Content/Includes/AN-HomeBase-UserManal-SP/vistas.png) 

1. ***Vista Condensada:*** Esta opción viene activa de defecto cuando se abre la vista, esta opción muestra en la grilla los datos mínimos en un solo renglón.
2. ***Vista Detallada:*** Esta opción activa un segundo renglón en cada registro dentro de la grilla y muestra mas información de cada uno de los registros.
3. ***Imprimir:*** Al hacer click en esta opción, se abre una nueva ventana con los datos mostrados en la grilla pero con un formato orientado a ser impreso, se incluye una cabecera con el logo que el subscriptor configuro.
4. ***Exportar:*** Al hacer click en esta opción la información mostrada en ese momento en la grilla es exportada a Excel. Se iniciara una descarga automática en su navegador.
5. ***Actualizar:*** Algunas vistas donde la frecuencia de cambio de información es alta, podría ser de utilidad querer refrescar la grilla. Esta opción refresca los datos en forma inmediata.  

Algunas vistas también poseen un panel de filtros. Por defecto este panel aparece colapsado, para desplegarlo haga click en la barra que dice "Filtros". Cada vista posee campos específicos por los cuales se puede filtrar. Una vez que haya ingresado los valores deseados presione el botón "Buscar".

![Vistas](Content/Includes/AN-HomeBase-UserManal-SP/vistas3.png)

Las vistas también poseen paginación y el usuario podrá definir cuantos registros por pagina se muestran. Esta configuración se realiza desde [***Mis Preferencias***](#mis-preferencias)
La siguiente es la vista de Vehículos de ATIONet:

![Vistas](Content/Includes/AN-HomeBase-UserManal-SP/vistas2.png)

#### Autorizaciones Pendientes

Las autorizaciones pendientes son aquellas transacciones que todavía no recibieron la transacción de finalización. Los registros que se ven en esta vista son despachos que se están llevando a cabo en este momento. Si por alguna razón existen pre autorizaciones viejas, es probable que el POS no haya enviado la transacción de finalización o la de cancelación si el despacho no fue realizado.

Tenga en cuenta que al momento de pre autorizar, ATIONet congelo el monto de la autorización de la cuenta corriente de la sub cuenta.
Esta vista presenta todos los campos necesarios para poder identificar la transacción y el vehículo. Si necesita ver mas detalles, al hacer click en el código de autorización lo llevara a la vista de detalles de la transacción.

![Autorizaciones Pendientes](Content/Includes/AN-HomeBase-UserManal-SP/autorizacionesPendientes.png)

Si aparecen transacciones pendientes viejas y usted esta seguro que no es un despacho en curso, puede cancelarlas y devolver el saldo a la cuenta corriente.
Para hacer esto tiene 2 maneras, en forma individual, haciendo click en el ícono de la "X" a la derecha de la grilla o en forma masiva seleccionando las transacciones, desplegar el menú "Acciones en Lote" y seleccionar "Cancelar". Esto cancelara las transacciones y devolverá el saldo a cada una de las cuentas corrientes.

![Autorizaciones Pendientes](Content/Includes/AN-HomeBase-UserManal-SP/autorizacionesPendientes2.png)

(para mas detalles sobre el flujo de transacciones consulte este [documento](AN-Transaction_Flows-TechGuide.md))

#### Batch

El proceso Batch, es un proceso por el cual la terminal se asegura que envió todo lo que proceso y que el host lo recibió. La manera de asegurarse es enviando una transacción de "Cierre de Lote".
No todas las terminales tienen la capacidad de implementar este mensaje, si la terminal lo soporta en esta vista se listaran todos los  cierres de lote enviados por las terminales. 

![Batch](Content/Includes/AN-HomeBase-UserManal-SP/batch.png)

#### Conductores

En esta vista se listan los conductores que han sido dados de alta. Recuerde que no es obligatorio cargar conductores para poder operar, solo es necesario si usted decide asociar los identificadores a conductores.

![Batch](Content/Includes/AN-HomeBase-UserManal-SP/conductores.png)

#### Cuentas corrientes de compañía

La vista de Cuentas corrientes de compañía es la vista en donde se consultan los saldos disponibles de las sub cuentas (Recuerde que la sub cuenta es la unión entre un vehículo/conductor y un identificador. Para mas detalles sobre sub cuentas consulte: [Esta sección](#sub-cuenta)).
En ATIONet el termino compañía se refiere a la empresa dueña de la flota, en una suscripción del tipo auto consumo (home base) la única compañía es la propia empresa suscriptora. Para mas detalles sobre compañías consulte: [Esta sección](#compañía)

Esta  vista posee al igual que el resto de las vistas un panel de filtros.
La primer opción en el panel de filtros es el tipo de reporte que queremos ver:

![Cuentas Corrientes](Content/Includes/AN-HomeBase-UserManal-SP/cuentasCorrientes2.png)

1. ***Lista de Sub-cuentas:*** Esta opción lista las subcuentas con su respectivo saldo, pero no da detalles de los movimientos, es una vista que resume los datos de cada una de las subcuentas.

	![Cuentas Corrientes](Content/Includes/AN-HomeBase-UserManal-SP/cuentasCorrientes.png)

2. ***Movimientos de Sub-cuentas:*** Esta opción de la vista muestra en detalle cada uno de los movimientos de la subcuenta, tanto los créditos como los débitos.   

	![Cuentas Corrientes](Content/Includes/AN-HomeBase-UserManal-SP/cuentasCorrientes3.png)

Al seleccionar esta segunda opción se habilitan varios filtros mas:

* ***Estado de Cuenta:*** Numero del extracto de cuenta.
* ***Subcuenta:*** Ingresando uno o varios nombres de subcuenta, solo se listaran los movimientos de esas subcuentas. Tenga en cuenta que este campo es "autocomplete", se completara a medida que escribe, si presiona la barra espaciadora mostrara todas las subcuentas.
* ***Fecha Desde / Fecha Hasta:*** Ingresando estos valores, filtrara los movimientos entre ambas fechas.
* ***Hora Desde / Hora Hasta:*** Ingresando estos valores, filtrara los movimientos entre ambas horas.
* ***Monto Desde / Monto Hasta:*** Ingresando estos valores filtrara, los movimientos cuyo monto este entre ambos valore.
* ***Especies:*** Se puede filtrar por la especie (Producto)
* ***Débito / Crédito:*** Se puede seleccionar que tipo de movimientos se desean ver, si los de débito o los de crédito.
* ***Tipo:*** Que tipo de movimiento genero el movimiento en la cuenta corriente
* ***Origen:*** Origen del movimiento, ya sea la consola de ATIONet, una aplicación móvil o una llamada a la API desde una aplicación de terceros.
* ***Movimientos Transitorios:*** Tildando esta opción se mostraran los movimientos internos que genera ATIONet. Por ejemplo cada vez que se congela saldo después de una pre autorización y se recibe una transacción de finalización, ATIONet devuelve el saldo congelado y posteriormente debita el monto final informado. La devolución del saldo congelado es considerado un movimiento transitorio y no se muestran si esta opción no esta seleccionada.

#### Excepciones

ATIONet separa las transacciones no autorizadas en 2 secciones, las Excepciones y las [Transacciones Rechazadas](#transacciones-rechazadas).
Las Excepciones son aquellas transacciones que no llegaron a pasar las validaciones duras del sistema o las que se detectan como posibles fraudes.

En la vista de Excepciones podemos filtrar por el tipo de Excepción primero. Los tipo de Excepciones disponibles son los siguientes:

![Cuentas Corrientes](Content/Includes/AN-HomeBase-UserManal-SP/excepciones2.png)

Esta vista también posee el panel de filtros mencionada anteriormente. Vale la pena resaltar el filtro  ***"Transacciones Off-line"***, al tildar esta opción, también se mostraran aquellas transacciones que fueron marcadas como Excepciones en el modulo Offline. 
(para mas detalles sobre el modulo Offline consulte esta [sección](#modulo-offline))

![Cuentas Corrientes](Content/Includes/AN-HomeBase-UserManal-SP/excepciones4.png)

Una vez que selecciono los filtros, presiona ***"Buscar"*** y se listaran todas las transacciones marcadas como Excepciones.

Algunas transacciones quedan en estado "Revisión" bajo algunas situaciones, como por ejemplo cuando se despacha mas de lo autorizado (por un error en el controlador o el POS). En estos casos es necesario aprobar o rechazar la transacción mediante uno de los 2 íconos a la derecha de cada registro.

![Cuentas Corrientes](Content/Includes/AN-HomeBase-UserManal-SP/excepciones.png)

#### Rendimiento por Transacción

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus mollis quam ac ligula maximus, vitae dictum lorem consequat. Curabitur interdum pretium cursus. Vestibulum pharetra sodales enim, ut vestibulum dui semper quis. Aliquam convallis nulla eu neque vestibulum eleifend. Nam feugiat leo a bibendum rutrum. Duis quis augue et dui vulputate rhoncus. Sed vitae felis fringilla, lacinia est vel, imperdiet leo. Sed suscipit neque risus, eu pharetra dolor rhoncus ac.

#### Rendimiento por Vehículo

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus mollis quam ac ligula maximus, vitae dictum lorem consequat. Curabitur interdum pretium cursus. Vestibulum pharetra sodales enim, ut vestibulum dui semper quis. Aliquam convallis nulla eu neque vestibulum eleifend. Nam feugiat leo a bibendum rutrum. Duis quis augue et dui vulputate rhoncus. Sed vitae felis fringilla, lacinia est vel, imperdiet leo. Sed suscipit neque risus, eu pharetra dolor rhoncus ac.

#### Transacciones

La vista de transacciones es una de las mas importantes en ATIONet. en esta vista se ven las transacciones que se realizaron y fueron aprobadas.

El panel de Filtros posee todos estas posibilidades:

![Transacciones](Content/Includes/AN-HomeBase-UserManal-SP/transactions.png)

* ***Cod. Autoriz.:*** Código de Autorización entregado por ATIONet.
* ***Vehículo:*** Vehículo o Vehículos (campo autocomplete y de selección múltiple, presionando la barra espaciadora listara los primeros 20 vehículos).
* ***Flota:*** El nombre de la flota. (campo autocomplete y de selección múltiple)
* ***Sitio:*** El nombre del sitio. (campo autocomplete y de selección múltiple)
* ***Fecha Desde / Fecha Hasta:*** Rango de fechas
* ***Hora Desde / Hora Hasta:*** Rango de horas.
* ***Rendimiento por Periodo:*** [TODO]
* ***Transacciones Off-line:*** Tildando esta opción también se listaran las transacciones aprobadas en modo Offline. (para mas detalles sobre el modulo Offline consulte esta [sección](#modulo-offline))
* ***Turno:*** El turno en el que ocurrió la transacción. (siempre y cuando la terminal o el POS lo informen)
* ***Conductor:*** El nombre del conductor. (campo autocomplete y de selección múltiple).
* ***Terminal / Controlador:*** Nombre de la terminal que registro la transacción. (campo autocomplete y de selección múltiple).
* ***Combustible:*** El producto que intervino en la transacción. (campo autocomplete y de selección múltiple)
* ***Mostrar Transacciones Completas en Cero:*** Tildando esta opción también mostrara las transacciones que se hayan enviado con monto o volumen en 0.
* ***Transacciones con Producto:*** Tildando esta opción también se mostraran transacciones que contengan productos secos.

Una vez seleccionado el filtro deseado se presiona ***"Buscar"*** y listara las transacciones que cumplan con el filtro.

![Transacciones](Content/Includes/AN-HomeBase-UserManal-SP/transactions2.png)

En la grilla se muestran los datos principales de la transacción, en la columna acciones se puede desconocer una transacción y entrara en el proceso de desconocimiento. (para mas detalles sobre el desconocimiento de transacciones consulte esta [sección](#transacciones-desconocidas)).

Si desea ver el detalle de la transacción, haga click en el Código de Autorización, esto lo llevara a una vista con el detalle de la transacción.

![Transacciones](Content/Includes/AN-HomeBase-UserManal-SP/transactions3.png)
 

#### Transacciones por Conductor

En esta vista se pueden ver las transacciones, agrupadas por  el conductor que la realizó. Los botones que estan colocados en la parte superior izquierda son para imprimir la tabla o crear un archivo Excel de la tabla, respectivamente.

![Transacciones por Sitio](Content/Includes/AN-HomeBase-UserManal-SP/transaccionesPorConductor.png)

El panel de filtros posee las siguientes posibilidades:

![Transacciones por Sitio](Content/Includes/AN-HomeBase-UserManal-SP/filtrosTransaccionesPorConductor.png)

* ***Agrupar por:***  Sitio, Flota, Programa, Id Vehículo y/o Fecha.
* ***Conductor:*** Filtrar por el conductor que despachó.
* ***Flota:*** Filtrar por flota a la cual pertenece el vehículo que realizó el despachó.
* ***Id Vehículo:*** Filtrar por el Id del vehículo que realizó el despachó.
* ***Sitio:*** Filtrar por sitio donde se realizó el despacho.
* ***Terminal/Controlador:*** Filtrar por terminal/controlador que despachó.
* ***Combustible:*** Filtrar por el combustible que se despachó.
* ***Fecha desde/Fecha hasta:*** Rango de fechas a filtrar.
* ***Hora desde/Hora hasta:*** Rango de horas a filtrar.

Cuando termine de llenar el formulario, cliquee "Buscar" para aplicar el filtro, o "Crear filtro" para guardar el filtro hecho.

#### Transacciones por Flota

En esta vista se pueden ver las transacciones que se realizaron, agrupadas por flota. Los botones que estan colocados en la parte superior izquierda son para imprimir la tabla o crear un archivo Excel de la tabla, respectivamente.

![Transacciones por Sitio](Content/Includes/AN-HomeBase-UserManal-SP/transaccionesPorFlota.png)

El panel de filtros posee las siguientes posibilidades:

![Transacciones por Sitio](Content/Includes/AN-HomeBase-UserManal-SP/filtrosTransaccionesPorFlota.png)

* ***Agrupar por:***  Sitio, Vehículo, Id Conductor y/o Fecha.
* ***Flota:*** Filtrar por flota a la cual pertenece el vehículo que realizó el despacho.
* ***Vehículo:*** Filtrar por el vehículo que realizó el despacho.
* ***Id Conductor:*** Filtrar por el Id del conductor que realizó el despacho.
* ***Sitio:*** Filtrar por sitio donde se realizó el despacho.
* ***Combustible:*** Filtrar por el combustible que se despachó.
* ***Terminal/Controlador:*** Filtrar por terminal/controlador que despachó.
* ***Fecha desde/Fecha hasta:*** Rango de fechas a filtrar.
* ***Hora desde/Hora hasta:*** Rango de horas a filtrar.

Cuando termine de llenar el formulario, cliquee "Buscar" para aplicar el filtro, o "Crear filtro" para guardar el filtro hecho.

#### Transacciones por Sitio

En esta vista se pueden ver las transacciones que se realizaron, agrupadas por  el sitio donde ocurrieron. Los botones que estan colocados en la parte superior izquierda son para imprimir la tabla o crear un archivo Excel de la tabla, respectivamente.

![Transacciones por Sitio](Content/Includes/AN-HomeBase-UserManal-SP/transaccionesPorSitio.png)

El panel de filtros posee las siguientes posibilidades:

![Transacciones por Sitio](Content/Includes/AN-HomeBase-UserManal-SP/filtrosTransaccionesPorSitio.png)

* ***Agrupar por:***  Combustible, Flota, Programa, Turno y/o Fecha.
* ***Sitio:*** Filtrar por sitio donde se realizó el despacho.
* ***Combustible:*** Filtrar por el combustible que se despachó.
* ***Flota:*** Filtrar por flota a la cual pertenece el vehículo que realizó el despacho.
* ***Terminal/Controlador:*** Filtrar por terminal/controlador que despachó.
* ***Fecha desde/Fecha hasta:*** Rango de fechas a filtrar.
* ***Hora desde/Hora hasta:*** Rango de horas a filtrar.

Cuando termine de llenar el formulario, cliquee "Buscar" para aplicar el filtro, o "Crear filtro" para guardar el filtro hecho.

#### Transacciones por Vehículo

En esta vista se pueden ver las transacciones, agrupadas por el vehículo que las realizó. Los botones que estan colocados en la parte superior izquierda son para imprimir la tabla o crear un archivo Excel de la tabla, respectivamente.

![Transacciones por Vehiculo](Content/Includes/AN-HomeBase-UserManal-SP/transaccionesPorVehiculo.png)

El panel de filtros posee las siguientes posibilidades:

![Transacciones por Sitio](Content/Includes/AN-HomeBase-UserManal-SP/filtrosTransaccionesPorVehiculo.png)

* ***Agrupar por:***  Sitio, Flota, Programa, Id Conductor y/o Fecha.
* ***Vehículo:*** Filtrar por vehículo que realizó el despacho.
* ***Flota:*** Filtrar por flota a la cual pertenece el vehículo que realizó el despacho.
* ***Id Conductor:*** Filtrar por el Id del conductor que realizó el despacho.
* ***Sitio:*** Filtrar por sitio donde se realizó el despacho.
* ***Terminal/Controlador:*** Filtrar por terminal/controlador que despachó.
* ***Combustible:*** Filtrar por el combustible que se despachó.
* ***Fecha desde/Fecha hasta:*** Rango de fechas a filtrar.
* ***Hora desde/Hora hasta:*** Rango de horas a filtrar.

Cuando termine de llenar el formulario, cliquee "Buscar" para aplicar el filtro, o "Crear filtro" para guardar el filtro hecho.

#### Transacciones Rechazadas

ATIONet separa las transacciones NO autorizadas en 2 secciones, las [Excepciones](#excepciones) y las Transacciones Rechazadas.
Las Transacciones Rechazadas son aquellas transacciones que lograron pasar las validaciones duras de ATIONet pero fueron rechazadas por otras validaciones como ser alguna regla no satisfecha o validación de saldo.

En la vista de Transacciones Rechazadas podemos filtrar por el tipo de rechazo primero. Los tipo de rechazos disponibles son los siguientes:

![Transacciones Rechazadas](Content/Includes/AN-HomeBase-UserManal-SP/transaccionesRechazadas.png)

Esta vista también posee el panel de filtros mencionada anteriormente. Vale la pena resaltar el filtro  ***"Transacciones Off-line"***, al tildar esta opción, también se mostraran aquellas transacciones que fueron marcadas como rechazadas en el modulo Offline. 
(para mas detalles sobre el modulo Offline consulte esta [sección](#modulo-offline))

![Cuentas Corrientes](Content/Includes/AN-HomeBase-UserManal-SP/excepciones4.png)

Una vez que selecciono los filtros, presiona ***"Buscar"*** y se listaran todas las transacciones marcadas como rechazadas.

![Transacciones Rechazadas](Content/Includes/AN-HomeBase-UserManal-SP/transaccionesRechazadas2.png)

Cabe aclarar que existe la posibilidad de que una transacción sea rechazada pero que el combustible haya sido entregado. Esto ocurre cuando el rechazo se produce en la transacción de terminación.
Algunos de los motivos mas comunes de esta situación los los siguientes:

* La pre autorización esta vencida (mas de 3hs entre la fecha de creación de la pre autorización y la fecha de creación de la terminación. Esto no se relaciona con el tiempo que puede tardar en llegar la terminación en modo offline)
* No existe una pre autorización existente para esa transacción
* La pre autorización fue cancelada manualmente
* La transacción de terminación contiene información invalida (errores en la terminal o controlador)
* La transacción de terminación se ejecuto con errores en el host
* La transacción de terminación contiene información diferente a la de pre autorización, como por ejemplo
* La transacción de terminación informa mas volumen o importe que el que fue autorizado. En este caso se puede aprobar la autorización. 

#### Transacciones sin Control

Las transacciones sin control son aquellas transacciones que se generan porque el controlador detecto una diferencia de aforadores y envía una transacción por la diferencia. Estas transacciones no contienen datos sobre el identificador ya que fueron generadas automáticamente y no se iniciaron con la presentación de un identificador. Al no tener un identificador asignado tampoco se impactan en ninguna cuenta corriente ni cuentan para calculo de reglas.
Esta vista también el panel de filtros para hacer búsquedas mas especificas.

![Transacciones sin Control](Content/Includes/AN-HomeBase-UserManal-SP/transaccionesFueraDeControl.png)

#### Vehículos

En esta vista se listan los vehículos que han sido dados de alta. Recuerde que no es obligatorio cargar vehículos para poder operar, solo es necesario si usted decide asociar los identificadores a vehículos.

Esta vista posee  el panel de filtros para poder especificar mas la búsqueda. Cabe destacar el filtro "Sin Identificación", seleccionando esta opción, se mostraran solo aquellos vehículos que no han sido asignados a un identificador. 

![Vehicles](Content/Includes/AN-HomeBase-UserManal-SP/vehicles.png)

Para ver mas detalles del vehículo, haga click en el código:

![Vehicles](Content/Includes/AN-HomeBase-UserManal-SP/vehicles2.png)

Al final de la vista encontrara 3 secciones, ***Conductores***, ***Reglas de Vehículos*** y ***Reglas de Flota***. Si el vehículo posee uno o mas conductores asociados se mostraran en la primer sección, y si el vehículo tiene una regla asociada, ya sea en forma directa a o a través de una flota aparecerán en las ultimas 2 secciones.

### Reportes

En ATIONet los reportes son considerados aquellos listados de información que si o si van a ser impresos y archivados en formato físico. Al ser impresos ATIONet les agrega una cabecera con el logo de la suscripción automáticamente.

#### Conductor

El reporte de Conductor se puede filtrar por nombre / código de conductor o por identificación.
Una vez seleccionado el filtro se presiona el botón ***Imprimir***, esto desplegara un popup con la información seleccionada.
La información es mostrada con un formato listo para ser impreso, incluyendo el logo de la suscripción y la fecha y la hora de generación del reporte.

Este popup posee un botón imprimir que al apretarlo se abre la ventana de impresión por defecto del navegador de internet.

![Drivers](Content/Includes/AN-HomeBase-UserManal-SP/driversReport.png)

#### Detalle de actividad por Vehículo

Este reporte muestra la actividad de cada vehículo. Muestra la lista de transacciones que cada vehículo realizó, ordenadas por fecha. Una vez seleccionado el filtro se presiona el botón ***Imprimir***, esto desplegara un popup con la información seleccionada.
La información es mostrada con un formato listo para ser impreso, incluyendo el logo de la suscripción y la fecha y la hora de generación del reporte.

Este popup posee un botón imprimir que al apretarlo se abre la ventana de impresión por defecto del navegador de internet.
 

![Drivers](Content/Includes/AN-HomeBase-UserManal-SP/vehicleDetailedActivity.png)

#### Sitios

Este reporte muestra la lista de sitios. Esta vista no posee un panel de filtros. Al presionar el botón ***Imprimir***, esto desplegara un popup con toda la información.
La información es mostrada con un formato listo para ser impreso, incluyendo el logo de la suscripción y la fecha y la hora de generación del reporte.

Este popup posee un botón imprimir que al apretarlo se abre la ventana de impresión por defecto del navegador de internet.

![Sites](Content/Includes/AN-HomeBase-UserManal-SP/siteReport.png)

#### Transacciones

Este reporte muestra la lista de transacciones realizadas, ordenadas por fecha. Este reporte posee varios filtros para ajustar la busqueda. El primer campo del panel de filtros  indica porque campo se va a ordenar la lista, el campo seleccionado en esta lista sera mostrado en la primer columna.

![Transactions](Content/Includes/AN-HomeBase-UserManal-SP/transactionReport.png)

Una vez seleccionado el filtro se presiona el botón ***Imprimir***, esto desplegara un popup con la información seleccionada.
La información es mostrada con un formato listo para ser impreso, incluyendo el logo de la suscripción y la fecha y la hora de generación del reporte.

Este popup posee un botón imprimir que al apretarlo se abre la ventana de impresión por defecto del navegador de internet.

![Transactions](Content/Includes/AN-HomeBase-UserManal-SP/transactionReport2.png)


#### Vehículo

Este reporte muestra la lista de vehículos. Este reporte posee varios filtros para ajustar la búsqueda. El primer campo del panel de filtros  indica porque campo se va a ordenar la lista, el campo seleccionado en esta lista sera mostrado en la primer columna.

![Vehicles](Content/Includes/AN-HomeBase-UserManal-SP/vehiclesReport.png)

Una vez seleccionado el filtro se presiona el botón ***Imprimir***, esto desplegara un popup con la información seleccionada.
La información es mostrada con un formato listo para ser impreso, incluyendo el logo de la suscripción y la fecha y la hora de generación del reporte.

Este popup posee un botón imprimir que al apretarlo se abre la ventana de impresión por defecto del navegador de internet.

![Vehicles](Content/Includes/AN-HomeBase-UserManal-SP/vehiclesReport2.png)

### Administración


#### Clases de Vehículos

Si usted desea tener su flota organizada por clase de vehículo, puede hacerlo utilizando esta funcionalidad de ATIONet. Al hacer click en la opción del menú de navegación le mostrara la pagina con la lista de "Clases de Vehículos".

![Vehicle Class](Content/Includes/AN-HomeBase-UserManal-SP/vehicleClass.png)

Para crear una nueva clase de vehículo, haga click en ***"Nuevo"*** y navegara hasta la pagina de alta de nueva clase de vehículo. En esta pagina deberá cargar los siguientes campos:

* ***Tipo de Vehículo:*** Una lista pre cargada de los tipos de vehículo que se esta cargando. Este campo es obligatorio.
* ***Consumo teórico:*** El indice de consumo informado por el fabricante  (galones/litros por kilómetro/milla. Este campo es obligatorio.
* ***Marca:*** La marca del vehículo. Este campos es obligatorio.
* Modelo (obligatorio)
* Kilometraje mínimo (hoy son solo informativos)
* Kilometraje máximo (hoy son solo informativos)

Después existe una sección llamada ***"Combustibles"*** en la que se puede indicar en tipo de combustible que usa el vehículo y también la capacidad del tanque. ***Este ultimo valor se valida en cada transacción del vehículo.*** 

![Vehicle Class](Content/Includes/AN-HomeBase-UserManal-SP/vehicleClass2.png)

Si un vehículo tiene una clase de vehículo asociada y esa clase de vehículo tiene un combustible asociado con su correspondiente capacidad de tanque de 60 litros y llega una pre autorización para el vehículo por 70 litros, la transacción sera rechazada ya que se podría asumir que es un fraude o que el combustible no va a ser entregado en el vehículo configurado. En esta sección se pueden agregar mas de un combustible ya que algunos vehículos cargan mas de 1, como por ejemplo combustible y GNC.
 
#### Combustibles

ATIONet posee una tabla de productos maestros codificada en base al estándar NACS. Llegado el caso que su controlador o POS tenga configurado códigos distintos a los estándar o que su red sea multi marca y para un mismo producto, diferentes sitios manejen distintos códigos, ATIONet posee un mecanismo para resolver esta situación. Este mecanismo es el ***"Mapeo de Combustible"***. 
Cuando un sitio necesita mapear códigos de productos deberá editar el sitio y marcar el tilde ***"Requiere Mapeo de Combustibles"***. 
Cuando al menos un sitio tiene este parámetro activado se mostrara en el menú de administración la opción ***Combustibles***. 

***Tenga en cuenta que por defecto los sitios no están marcados con esta opción, por consecuencia la opción "Combustible" en el menú de Administración tampoco se mostrara inicialmente.***

![Combustible](Content/Includes/AN-HomeBase-UserManal-SP/combustibles.png)


Al hacer click en la opción Combustibles vera la lista de mapeo de códigos de combustibles. En esta grilla se mostrara el nuevo código asignado, el producto al cual el código mapea y el sitio al cual pertenece este mapeo. 

![Combustible](Content/Includes/AN-HomeBase-UserManal-SP/combustibles2.png)

Para dar de alta un nuevo código de producto, haga click en ***Nuevo***. 

Primero deberá seleccionar el sitio al cual aplicara este mapeo, el producto maestro, y finalmente deberá proveer el código que la terminal o el POS enviara. Tenga en cuenta que no es posible tener el mismo código de mapeo para 2 productos maestros distintos.

![Combustible](Content/Includes/AN-HomeBase-UserManal-SP/combustibles3.png)


La tabla maestra de productos de ATIONet es la siguiente:

<table>
    <tr>
        <th>
            C&#243;digo
        </th>
        <th>
            Descripción
        </th>
    </tr>
        <tr>
            <td>022
            </td>
            <td>Compressed Natural Gas
            </td>
        </tr>
        <tr>
            <td>019
            </td>
            <td>Regular Diesel
            </td>
        </tr>
        <tr>
            <td>399
            </td>
            <td>Other Fuel
            </td>
        </tr>
        <tr>
            <td>003
            </td>
            <td>Unleaded Super
            </td>
        </tr>
        <tr>
            <td>300
            </td>
            <td>Kerosene
            </td>
        </tr>
        <tr>
            <td>023
            </td>
            <td>Liquid Propane Gas
            </td>
        </tr>
        <tr>
            <td>001
            </td>
            <td>Unleaded Regular
            </td>
        </tr>
        <tr>
            <td>020
            </td>
            <td>Premium Diesel
            </td>
        </tr>
        <tr>
            <td>002
            </td>
            <td>Unleaded Plus
            </td>
        </tr>
</table>

#### Conceptos

#### Conductores

Se listan los conductores por código, nombre completo, identificaciones y balance. Por defecto la vista es condensada, como se muestra en la imagen de abajo.

La columna "Habilitado" muestra el estado del conductor; para habilitar o deshabilitar un conductor, haga click en el ícono del candado en la columna "Opciones".

![Conductores Administracion](Content/Includes/AN-HomeBase-UserManal-SP/opcionesConductoresAdministracion.png)

En la columna opciones también puede asignarle una identificación al conductor, haciendo click en el primer ícono, contando de izquierda a derecha; asignarle una regla, haciendo click en el segundo ícono; editar la información del conductor, haciendo click en el tercer ícono, o marcarlo como favorito haciendo click en el ultimo ícono de la fila. Los conductores que marque como favoritos aparecerán en la sección favoritos en el apartado de la izquierda de la página.

![Conductores Administracion](Content/Includes/AN-HomeBase-UserManal-SP/conductoresAdministracion.png)

Para cambiar a una vista detallada de la información de los conductores, haga click en el ultimo ícono de la imagen de abajo.

![Conductores Administracion](Content/Includes/AN-HomeBase-UserManal-SP/botonVistaDetalladaResaltadoConductoresAdministracion.png)

La vista detallada es la siguiente: 

![Conductores Administracion](Content/Includes/AN-HomeBase-UserManal-SP/vistaDetallladaConductoresAdministracion.png)


##### Crear un nuevo conductor

Para crear un nuevo conductor, haga click en el botón "Nuevo".

![Conductores Administracion](Content/Includes/AN-HomeBase-UserManal-SP/botonNuevoResaltadoConductoresAdministracion.png)

El formulario para crear un nuevo conductor recibe los siguientes parámetros:

![Conductores Administracion](Content/Includes/AN-HomeBase-UserManal-SP/crearNuevoConductorAdministracion.png)

* ***Código:*** El código de identificacion del conductor.
* ***Apellidos:*** El apellido o apellidos del conductor.
* ***Nombre:*** El nombre del conductor.
* ***Licencia:*** El numero de licencia del conductor.
* ***Lic. País:*** El país al cual pertenece la licencia.
* ***Lic. Provincia:*** La provincia a la cual pertenece la licencia.
* ***Teléfono 1:*** El teléfono del conductor.
* ***Teléfono 2:*** Otro teléfono del conductor.
* ***Correo:*** El correo electrónico del conductor.
* ***Fecha de nacimiento:*** La fecha de nacimiento del conductor.

* **Identificadores:** Para asignarle un identificador, o, crear uno nuevo si no existe y luego cliquear "Alta rápida".

* **Vehículo:** Para asignarle un vehículo ya existente.

* **Reglas:** Para asignarle una regla ya existente.

Cuando termine de realizar los cambios, cliquée el botón "Guardar".

#### Configuración

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus mollis quam ac ligula maximus, vitae dictum lorem consequat. Curabitiur interdum pretium cursus. Vestibulum pharetra sodales enim, ut vestibulum dui semper quis. Aliquam convallis nulla eu neque vestibulum eleifend. Nam feugiat leo a bibendum rutrum. Duis quis augue et dui vulputate rhoncus. Sed vitae felis fringilla, lacinia est vel, imperdiet leo. Sed suscipit neque risus, eu pharetra dolor rhoncus ac.

![Configuracion Administracion](Content/Includes/AN-HomeBase-UserManal-SP/configuracionAdministracion.png)

#### Configuración de Fast Track

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus mollis quam ac ligula maximus, vitae dictum lorem consequat. Curabitur interdum pretium cursus. Vestibulum pharetra sodales enim, ut vestibulum dui semper quis. Aliquam convallis nulla eu neque vestibulum eleifend. Nam feugiat leo a bibendum rutrum. Duis quis augue et dui vulputate rhoncus. Sed vitae felis fringilla, lacinia est vel, imperdiet leo. Sed suscipit neque risus, eu pharetra dolor rhoncus ac.

![Configuracion de Fast Track Administracion](Content/Includes/AN-HomeBase-UserManal-SP/configuracionFastTrackAdministracion.png)

#### Contratos de Compañía

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus mollis quam ac ligula maximus, vitae dictum lorem consequat. Curabitur interdum pretium cursus. Vestibulum pharetra sodales enim, ut vestibulum dui semper quis. Aliquam convallis nulla eu neque vestibulum eleifend. Nam feugiat leo a bibendum rutrum. Duis quis augue et dui vulputate rhoncus. Sed vitae felis fringilla, lacinia est vel, imperdiet leo. Sed suscipit neque risus, eu pharetra dolor rhoncus ac.

![Contratos de Compañia](Content/Includes/AN-HomeBase-UserManal-SP/contratosDeCompaniaAdministracion.png)



![Contratos de Compañia](Content/Includes/AN-HomeBase-UserManal-SP/filtrosContratosDeCompaniaAdministracion.png)

#### Familias de Conceptos

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus mollis quam ac ligula maximus, vitae dictum lorem consequat. Curabitur interdum pretium cursus. Vestibulum pharetra sodales enim, ut vestibulum dui semper quis. Aliquam convallis nulla eu neque vestibulum eleifend. Nam feugiat leo a bibendum rutrum. Duis quis augue et dui vulputate rhoncus. Sed vitae felis fringilla, lacinia est vel, imperdiet leo. Sed suscipit neque risus, eu pharetra dolor rhoncus ac.

#### Flotas

Las flotas son los conjuntos de vehículos de los cual dispone la empresa. Abajo se listan por código y nombre las flotas que tiene. En la columna opciones puede asignarle una regla a la flota, o editarla.

![Flotas Administracion](Content/Includes/AN-HomeBase-UserManal-SP/flotasAdministracion.png)

###### Crear una nueva flota

Para crear una nueva flota, cliquée el botón "Nuevo" que se encuentra en el lado superior izquierdo.

El formulario para crear una nueva flota recibe los siguientes parámetros:

![Flotas Administracion](Content/Includes/AN-HomeBase-UserManal-SP/crearNuevaFlotaAdministracion.png)

* ***Código:*** El código de identificación de la flota.
* ***Nombre:*** El nombre de la flota.

* ***Reglas:*** Asignarle reglas ya creadas a la flota.

Cuando termine de realizar los cambios, cliquée el botón "Guardar".

#### Identificaciones Solicitadas

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus mollis quam ac ligula maximus, vitae dictum lorem consequat. Curabitur interdum pretium cursus. Vestibulum pharetra sodales enim, ut vestibulum dui semper quis. Aliquam convallis nulla eu neque vestibulum eleifend. Nam feugiat leo a bibendum rutrum. Duis quis augue et dui vulputate rhoncus. Sed vitae felis fringilla, lacinia est vel, imperdiet leo. Sed suscipit neque risus, eu pharetra dolor rhoncus ac.

![Identificaciones Solicitadas Administracion](Content/Includes/AN-HomeBase-UserManal-SP/identificacionesSolicitadasAdministracion.png)

#### Identificadores

El identificador es el medio físico que utiliza ATIONet para poder identificar un vehículo o un conductor. ATIONet soporte varios tipos de identificaciones, como ser tarjeta, tag (anillo), chip, tarjeta ATIONet, entrada manual, código de barras e iButton. Cuando se asocia un identificador a un Vehículo o Conductor se crea una sub cuenta. En esta seccion, se mostraran los identificadores ya creados. En la columna opciones puede editar el identificador, habilitarlo o deshabilitarlo, o libearlo.

![Identificadores Administracion](Content/Includes/AN-HomeBase-UserManal-SP/identificadoresAdministracion.png)

###### Crear un nuevo identificador

Para crear un nuevo identificador haga click en el botón nuevo que se encuentra en el lado superior izquierdo.

El formulario para crear un nuevo identificador recibe los siguientes parámetros:

![Nuevo Identificador Adminstracion](Content/Includes/AN-HomeBase-UserManal-SP/crearNuevoIdentificadorAdministracion.png)

* ***Tipo:*** Puede ser Tarjeta, TAG, Chipkey, Entrada Manual, Tarjeta ATIOnet o ATIOnet TAG.
* ***Modelo:*** El modelo del tipo de identificador seleccionado en ***Tipo***.
* ***Tipo de uso:*** Puede ser de flota, fidelidad o dual.
* ***Programa:*** El programa al cual se le va a asignar este identificador
* ***Programa de fidelidad:*** El programa de fidelidad al cual se le va a asignar este identificador
* ***Etiqueta:*** El nombre que lleva la tarjeta (Ej. Pablo Pérez)
* ***Track:*** ?
* ***PAN:*** Número de entre 1 y 19 caracteres 
* ***PIN:*** El PIN que 

Notesé que depende el tipo de identificador, pedirá ciertos ítems. Por ejemplo, el TAG no necesita de un PIN. Asimismo, si usted en tipo de programa selecciona "Flota", no le pedira que ingrese un programa de fidelidad.

En segunda instancia, el formulario se completa asignandole la identificación a un vehículo o conductor.


#### Impuestos

La tabla de impuestos muestra:

* ***Código:*** Código del impuesto.
* ***Descripción:*** Descripción del impuesto.
* ***Tipo:*** Tipo de impuesto (Puede ser un impuesto fijo, un impuesto porcentual o un impuesto fijo por unidad).
* ***Monto:*** El monto del impuesto (En el caso del impuesto porcentual, el porcentaje).
* ***Fecha Desde / Fecha Hasta:*** Rango de fechas.
* ***Opciones:*** Editar el impuesto.

![Impuestos Administracion](Content/Includes/AN-HomeBase-UserManal-SP/impuestosAdministracion.png)

###### Crear un nuevo impuesto

Para crear un nuevo impuesto, cliquée el botón "Nuevo" que se encuentra en el lado superior izquierdo.

El formulario para crear un nuevo impuesto recibe los siguientes parámetros:

![Nuevo Impuesto Administracion](Content/Includes/AN-HomeBase-UserManal-SP/crearNuevoImpuestoAdministracion.png) 

* ***Código:*** El código del nuevo impuesto.
* ***Descripción:*** La descripción del nuevo impuesto.
* ***Tipo:*** Tipo de impuesto (Puede ser un impuesto fijo, un impuesto porcentual o un impuesto fijo por unidad)
* ***Fecha desde:*** La fecha en la que entra en vigencia el impuesto.
* ***Monto:*** El monto del impuesto (En el caso del impuesto porcentual, el porcentaje)

Luego de llenar los campos de ***Fecha desde*** y ***Monto*** cliquée el botón alta. 

Cuando termine de realizar los cambios, cliquée el botón "Guardar".

#### Métodos de Pago

Los medios de pago son las distintas formas en las que se puede pagar un compra: efectivo, tarjeta de crédito, tarjeta de debito, gift cards, etc. ATIONET es una herramienta para que que un comerciante cree un medio de pago propio: una tarjeta de pago para combustibles.

![Metodos De Pago Administracion](Content/Includes/AN-HomeBase-UserManal-SP/metodosDePagoAdministracion.png)

###### Crear un nuevo método de pago

Para crear un nuevo método de pago, cliquée el botón "Nuevo" que se encuentra en el lado superior izquierdo.

El formulario para crear un nuevo método de pago recibe los siguientes parámetros:

![Nuevo Metodo De Pago Administracion](Content/Includes/AN-HomeBase-UserManal-SP/crearNuevoMetodoDePagoAdministracion.png)

* ***Código:*** El código del nuevo método de pago.
* ***Descripción:*** La descripción del nuevo método de pago.

Cuando termine de realizar los cambios, cliquée el botón "Guardar".

#### Modelos de Identificador

Los modelos de identificador varian segun la necesidad del cliente, pueden ser de tipo Tarjeta (Una tarjeta magnética), TAG (Anillo), Chipkey o Entrada Manual (Un código ingresado a mano).

![Modelos De Identificador Administracion](Content/Includes/AN-HomeBase-UserManal-SP/modelosDeIdentificadorAdministracion.png)

###### Crear un nuevo modelo de identificador

Para crear un nuevo modelo de identificador, cliquée el botón "Nuevo" que se encuentra en el lado superior izquierdo.

El formulario para crear un nuevo modelo de identificador recibe los siguientes parámetros:

![Nuevo Modelo De Idcentificador Administracion](Content/Includes/AN-HomeBase-UserManal-SP/crearNuevoModeloDeIdentificadorAdministracion.png)

* ***Tipo:*** Puede ser de tipo Tarjeta, TAG, Chipkey o Entrada Manual.
* ***Descripción:*** La descripción del nuevo modelo de identificador.
* ***Instalable:*** Si es instalable o no.
* ***Personalizado:*** Si es personalizado o no.
* ***Reusable:*** Si es reusable o no.
* ***Soporta múltiples asignaciones:*** Si soporta múltiples asignaciones o no.
* ***Valida fecha de expiración:*** Si valida la fecha de expiración o no.
* ***Ignorar comportamiento de id vehículo en terminal:*** Si ignora el comportamiento de id vehículo en terminal o no.
* ***Requiere PIN:*** Si requiere PIN o no.

Cuando termine de realizar los cambios, cliquée el botón "Guardar".

#### Programas

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus mollis quam ac ligula maximus, vitae dictum lorem consequat. Curabitur interdum pretium cursus. Vestibulum pharetra sodales enim, ut vestibulum dui semper quis. Aliquam convallis nulla eu neque vestibulum eleifend. Nam feugiat leo a bibendum rutrum. Duis quis augue et dui vulputate rhoncus. Sed vitae felis fringilla, lacinia est vel, imperdiet leo. Sed suscipit neque risus, eu pharetra dolor rhoncus ac.

![Programas Administracion](Content/Includes/AN-HomeBase-UserManal-SP/programasAdministracion.png)

###### Crear un nuevo programa

Para crear un nuevo programa, cliquée el botón "Nuevo" que se encuentra en el lado superior izquierdo.

El formulario para crear un nuevo programa recibe los siguientes parámetros:

![Nuevo Programa Administracion](Content/Includes/AN-HomeBase-UserManal-SP/crearNuevoProgramaAdministracion.png)

* ***Descripción:*** La descripción del nuevo programa.
* ***Aplicar sitios del Contrato:*** Puede ser no afectado, forzado o no forzado.
* ***Modo del saldo:*** Puede ser no afectado, dispersado, sin dispersar, sin límite o de llenado automático.
* ***Soporta contingencias:*** Puede ser no afectado, forzado o no forzado.
* ***Soporta offline:*** Puede ser no afectado, forzado o no forzado.
* ***Tarjeta de regalo:*** Si incluye tarjeta de regalo o no. Si esta opción es chequeada, aparecerán tres parámetros más:
* ***Monto de tarjeta de regalo:*** El monto de la tarjeta de regalo.
* ***Recargable:*** Si es recargable.
* ***Compañia:*** La compañia a la cuál se le es asignada.

Cuando termine de realizar los cambios, cliquée el botón "Guardar".

#### Reglas

Las reglas son, limitaciones que se le asignan a vehículos, flotas, combustibles, sitios o conductores. Si no se le aplicara ninguna regla a, por ejemplo, un conductor, el conductor podría, por ejemplo, cargar cualquier combustible en cualquier sitio. En esta sección usted puede ver las reglas que ya creó, listadas por Tipo y Descripción. Si hace click en la descripción, puede ver el detalle de la regla y a que vehículos, flotas, combustibles, sitios o conductores se les ha aplicado la regla. Para editar la regla haga click en el ícono del lápiz que se encuentra en la columna "Opciones"; para eliminar la regla, haga click en el ícono de la cruz que se encuentra en la columna opciones.

![Reglas Administracion](Content/Includes/AN-HomeBase-UserManal-SP/reglasAdministracion.png)

##### Crear una nueva regla

Para crear una nueva regla, cliquée el botón "Nuevo" que se encuentra en el lado superior izquierdo.

El formulario para crear una nueva regla recibe los siguientes parámetros:

![Nueva Regla Administracion](Content/Includes/AN-HomeBase-UserManal-SP/crearNuevaReglaAdministracion.png)

* ***Descripción:*** La descripción de la nueva regla.
* ***Tipo:*** El tipo de regla. Dependiendo el tipo de regla que seleccione, se carga un distinto tipo de formulario.

###### Nueva regla de tipo Cuota

El formulario para crear una nueva regla de tipo cuota es el siguiente:

![Nueva Regla Cuota](Content/Includes/AN-HomeBase-UserManal-SP/nuevaReglaCuota.png)

* ***Frecuencia:*** La frecuencia se compone de valor (numérico) y de unidad de tiempo (Ej. Días, Semanas). Si, por ejemplo, se introduce 2 - Días, la frecuencia con la que será evaluada toda la regla sera de 2 días.

**Transacciones**

* ***Cantidad:*** La cantidad máxima de transacciones que se pueden realizar en el lapso de tiempo especificado en ***Frecuencia***.

**Volumen**

* ***Cuota:*** La cantidad máxima de combustible que puede cargar en el lapso de tiempo especificado en **Frecuencia**.

**Importe**

* ***Cuota:*** La cantidad máxima de dinero que puede gastar en el lapso de tiempo especificado en **Frecuencia**.

**Aplicar a:** Aplicar la regla a cierta flota, vehículo, conductor, sitio y/o combustible.

Ejemplo: Si se le aplica a una flota una regla de tipo cuota, con una frecuencia de dos semanas, y la cantidad máxima de transacciones que pueden realizar es 120, podrán realizar como máximo 120 transacciones cada dos semanas.

Cuando termine, cliquée el botón "Guardar".

###### Nueva Regla de tipo Rango de Fechas

El formulario para crear una nueva regla de tipo Rango de Fechas es el siguiente:

![Nueva Regla Rango de Fechas](Content/Includes/AN-HomeBase-UserManal-SP/nuevaReglaRangoDeFechas.png)

* ***Fecha desde/Fecha hasta:*** Rango de fechas en las que se podrá realizar una transacción.
* ***Hora desde/Hora Hasta:*** Rango de horas en las que se podrá realizar una transacción.

**Aplicar a:** Aplicar la regla a cierta flota, vehículo, conductor, sitio y/o combustible.

Ejemplo: Si se le aplica a un combustible una regla de tipo rango de fechas, con un rango de fechas del 10 de Junio del 2017 al 17 de Junio del 2017, ese combustible solo se podrá despachar en dicho rango de fechas.

Cuando termine, cliquée el botón "Guardar".

###### Nueva Regla de tipo Ubicación

El formulario para crear una nueva regla de tipo Ubicación es el siguiente:

![Nueva Regla Ubicacion](Content/Includes/AN-HomeBase-UserManal-SP/nuevaReglaUbicacion.png) 

* ***Sitio:*** El sitio (o sitios) donde **solamente** podrán cargar las flotas, vehículos, etc., a las cuáles se les aplique esta regla.

**Aplicar a:** Aplicar la regla a cierta flota, vehículo, conductor o combustible.

Ejemplo: Si se le aplica a una flota una regla de tipo ubicación, siendo el sitio "ABC", esa flota **solamente** podrá cargar en el sitio ABC.

Cuando termine, cliquée el botón "Guardar".

###### Nueva Regla de tipo Combustible

El formulario para crear una nueva regla de tipo Combustible es el siguiente:

![Nueva Regla Combustible](Content/Includes/AN-HomeBase-UserManal-SP/nuevaReglaCombustible.png)

* ***Combustible:*** El combustible (o combustibles) que **solamente** podrán cargar las flotas, vehículos, etc., a las cuáles se les aplique esta regla.

**Aplicar a:** Aplicar la regla a cierta flota, vehículo, conductor o sitio.

Ejemplo: Si se le aplica a un vehículo una regla de tipo combustible, siendo el combustible "Premium Diesel", ese vehículo **solamente** podrá cargar el combustible "Premium Diesel".

Cuando termine, cliquée el botón "Guardar".

###### Nueva Regla de tipo Límite por Transacción

El formulario para crear una nueva regla de tipo Límite por Transacción es el siguiente:

![Nueva Regla Limite Por Transaccion](Content/Includes/AN-HomeBase-UserManal-SP/nuevaReglaLimitePorTransaccion.png)

**Volumen:**

* ***Cuota:*** La cantidad máxima de combustible que se podrá despachar por transacción.

**Importe** 

* ***Cuota:*** La cantidad máxima de dinero que puede costar una transacción.

**Aplicar a:** Aplicar la regla a cierta flota, vehículo, conductor, sitio o combustible.

Ejemplo: Si un vehículo tiene un límite por transacción de 50 litros, solo podrá cargar 50 litros como máximo en una sola transacción.

Cuando termine, cliquée el botón "Guardar".

###### Nueva Regla de tipo Días

El formulario para crear una nueva regla de tipo Días es el siguiente:

![Nueva Regla Dias](Content/Includes/AN-HomeBase-UserManal-SP/nuevaReglaDias.png)

* ***Días de la semana habilitados:*** Los días de la semana en los que se pueden realizar transacciones.

**Aplicar a:** Aplicar la regla a una flota, vehículo, conductor, sitio o combustible.

Ejemplo: Si se le aplica una regla de tipo días a un combustible, siendo Martes, Jueves y Viernes los días de la semana habilitados, ese combustible solo se podrá despachar los Martes, Jueves y Viernes.

Cuando termine, cliquée el botón "Guardar".

###### Nueva Regla de tipo Días/Horas

El formulario para crear una nueva regla de tipo Días/Horas es el siguiente:

![Nueva Regla Dias/Horas](Content/Includes/AN-HomeBase-UserManal-SP/nuevaReglaDiasHoras.png)

* ***Días de la semana habilitados:*** Los días de la semana en los que se pueden realizar transacciones.
* ***Hora desde/Hora hasta:*** Rango de horas en el cual se pueden realizar transacciones.

**Aplicar a:** Aplicar la regla a una flota, vehículo, conductor, sitio o combustible.

Ejemplo: Si se le aplica una regla de tipo días/horas a un vehículo, siendo Martes el día de la semana habilitado, y 10:50hs a 14:30hs el rango de horas, ese vehículo solo podrá realizar transacciones los días Martes entre las 10:50hs y las 14:30hs.

Cuando termine, cliquée el botón "Guardar".

###### Nueva Regla de tipo Solicitudes

Antes de completar la transacción, la terminal requerirá el ingreso de cierta información para completarla, como por ejemplo el PIN del Conductor.

El formulario para crear una nueva regla de tipo Solicitudes es el siguiente:

![Nueva Regla Solicitudes](Content/Includes/AN-HomeBase-UserManal-SP/nuevaReglaSolicitudes.png)

* ***Reintentos:*** La cantidad máxima de errores que se le permite al usuario.

* ***Conductor PIN:*** Si quiere que se requiera el PIN del conductor, chequée esta opción.
* ***Id Conductor:*** Si quiere que se requiera el Id del conductor, chequée esta opción.
* ***Vehículo PIN:*** Si quiere que se requiera el PIN del vehículo, chequée esta opción.
* ***Id Vehículo:*** Si quiere que se requiera el Id del vehículo, chequée esta opción.
* ***Num. Unidad del camión:*** Si quiere que se requiera el número de unidad del camión, chequée esta opción.
* ***Num. del remolque:*** Si quiere que se requiera el número del remolque, chequée esta opción.
* ***Misceláneo:*** Campo libre, para que requiera cualquier tipo de información que usted quiera.
* ***Odómetro actual:*** La cantidad de horas que tiene el odómetro actualmente.
* ***Horas de motor actual:*** La cantidad de horas que tiene el motor actualmente

**Aplicar a:** Aplicar la regla a una flota, vehículo, conductor, sitio o combustible.

Ejemplo: Si se chequean las opciones de Conductor PIN y Vehículo PIN, y se ingresa en ***Reintentos*** el valor 2, cuando el conductor quiera realizar la transacción, la terminal le requerirá que ingrese el PIN del conductor y el PIN del vehículo. Si el conductor ingresa bien estos valores correctamente, errando 2 o menos veces, la transacción se realizara, de errar mas 2 dos veces, la transacción se rechazará.

Cuando termine, cliquée el botón "Guardar".

###### Nueva Regla de tipo Límite de Producto por Transacción

El formulario para crear una nueva regla de tipo Límite de Producto por Transacción es el siguiente:

![Nueva Regla Limite De Producto Por Transaccion](Content/Includes/AN-HomeBase-UserManal-SP/nuevaReglaLimiteDeProductoPorTransaccion.png)

**Importe**

* ***Cuota:*** Cantidad máxima de dinero en productos secos (Ej. Cigarrillos) que puede haber en una única transacción.

**Aplicar a:** Aplicar la regla a una flota, vehículo, conductor o sitio.

Ejemplo: Si se le aplica una regla de tipo Límite de Producto por Transacción a un conductor, con una cuota de $50, en la factura solo puede haber, como máximo, $50 correspondientes a productos secos, de lo contrario, la transacción sera rechazada.

Cuando termine, cliquee el botón "Guardar".

###### Nueva Regla de tipo Cuota por Producto

El formulario para crear una nueva regla de cuota por producto es el siguiente:

![Nueva Regla Cuota Por Producto](Content/Includes/AN-HomeBase-UserManal-SP/nuevaReglaCuotaPorProducto.png)

* ***Frecuencia:*** La frecuencia se compone de valor (numérico) y de unidad de tiempo (Ej. Días, Semanas). Si, por ejemplo, se introduce 2 - Días, la frecuencia con la que será evaluada toda la regla será de 2 días.

**Importe**

* ***Cuota:*** Cantidad máxima de dinero en productos secos (Ej. Cigarrillos) que puede gastar en el lapso de tiempo especificado en frecuencia.

**Aplicar a:** Aplicar la regla a una flota, vehículo, conductor o sitio.

Ejemplo: Si se le aplica una regla de tipo Cuota por Producto a un conductor, con una cuota de $200, con una frecuencia de 2 semanas, podrá gastar como máximo $200 en productos secos (Ej. Cigarrillos) cada 2 semanas.

Cuando termine, cliquée el botón "Guardar".

#### Sitios

El Sitio representa a la estación de servicio. A un sitio se le asigna la terminal y también puede tener asociadas reglas de Ubicación. En esta sección se listan los sitios ya ingresados en el sistema y sus características. En la columna opciones puede editar el sitio, o asignarle una regla al sitio.

![Sitios Administracion](Content/Includes/AN-HomeBase-UserManal-SP/sitiosAdministracion.png)

####### Crear nuevo sitio

Para crear un nuevo sitio, cliquée el botón "Nuevo" que se encuentra en el lado superior izquierdo.

El formulario para crear un nuevo sitio recibe los siguientes parámetros:

![Nuevo Sitio Administracion](Content/Includes/AN-HomeBase-UserManal-SP/crearNuevoSitioAdministracion.png)

* ***Código:*** El código que se le quiere asignar al sitio.
* ***Idioma:*** El lenguaje de mensajería que se va a usar en el sitio.
* ***Nombre corto:*** El nombre corto del sitio.
* ***Nombre completo:*** El nombre completo del sitio.
* ***Calle:*** La calle donde se encuentra el sitio.
* ***Calle 2:*** La otra calle donde se encuentra el sitio (Si se encontrara en una esquina)
* ***Zona horaria:*** La zona horaria del sitio.
* ***Código Postal:*** El código postal del sitio.
* ***Ciudad:*** Ciudad donde se encuentra el sitio.
* ***País:*** País donde se encuentra el sitio.
* ***Estado:*** Estado donde se encuentra el sitio.
* ***Teléfono 1:*** Teléfono del sitio.
* ***Teléfono 2:*** Otro teléfono del sitio.
* ***Dif. Máxima de volumen permitida:*** La diferencia máxima de volumen permitida entre un despacho y una autorización del sitio.
* ***Dif. Máxima de importe permitida:*** La diferencia máxima de importe permitida entre un despacho y una autorización del sitio.
* ***Requiere mapeo de combustible:*** Si requiere mapeo de combustible o no.
* ***Latitud:*** La coordenada de latitud del sitio.
* ***Longitud:*** La coordenada de longitud del sitio.

Cuando termine de realizar los cambios, cliquée el botón "Guardar".

#### Terminales / Controladores

La terminal (o controlador) es la representación del controlador de surtidores, que necesita parametrizarse de manera particular según el tipo de terminal. Las terminales que ATIONet maneja son ATIO-NanoCPI, ATIO-Standalone, ATIO-CG, VF-Standalone, VF-Sapphire, VF-Ruby, ControlGas y OPW-FSC3000. En esta seccion se listan las terminales que ya están dadas de alta en el sistema. Puede editarla haciendo click en el ícono del lapiz que se encuentra en la columna opciones.

![Terminales Administracion](Content/Includes/AN-HomeBase-UserManal-SP/terminalesAdministracion.png)

###### Crear una nueva terminal

Para crear una nueva terminal, cliquée el botón "Nuevo" que se encuentra en el lado superior izquierdo.

El formulario para crear una nueva terminal recibe los siguientes parámetros:

![Nueva Terminal Administracion](Content/Includes/AN-HomeBase-UserManal-SP/crearNuevaTerminalAdministracion.png)

* ***Sitio:*** El sitio al que se le asigna esta terminal.
* ***Terminal/Tipo de controlador:*** La terminal/tipo de controlador.
* ***Protocolo:*** El protocolo que va a seguir esta terminal.
* ***Código:*** El código de la terminal/tipo de controlador. Es asignado automáticamente dependiendo de la terminal/tipo de controlador que sea.
* ***Descripción:*** La descripción de la terminal/controlador.
* ***Lector de TAG instalado:*** Si tiene un lector de TAG instalado o no.
* ***Uso del ID del conductor:*** Puede ser ninguno, track secundario o validación de código.
* ***Uso del ID del vehículo:*** Puede ser ninguno, track secundario o validación de código.
* ***Combustible:*** El combustible de la terminal/controlador.
* ***Límite máximo de volumen:*** El límite máximo de volumen de la terminal/controlador.
* ***Límite máximo de monto:*** El límite máximo de monto de la terminal/controlador.

Cuando termine de realizar los cambios, cliquée el botón "Guardar".

#### Tipos de Documentos

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus mollis quam ac ligula maximus, vitae dictum lorem consequat. Curabitur interdum pretium cursus. Vestibulum pharetra sodales enim, ut vestibulum dui semper quis. Aliquam convallis nulla eu neque vestibulum eleifend. Nam feugiat leo a bibendum rutrum. Duis quis augue et dui vulputate rhoncus. Sed vitae felis fringilla, lacinia est vel, imperdiet leo. Sed suscipit neque risus, eu pharetra dolor rhoncus ac.

#### Transacciones Desconocidas

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus mollis quam ac ligula maximus, vitae dictum lorem consequat. Curabitur interdum pretium cursus. Vestibulum pharetra sodales enim, ut vestibulum dui semper quis. Aliquam convallis nulla eu neque vestibulum eleifend. Nam feugiat leo a bibendum rutrum. Duis quis augue et dui vulputate rhoncus. Sed vitae felis fringilla, lacinia est vel, imperdiet leo. Sed suscipit neque risus, eu pharetra dolor rhoncus ac.

#### Transacciones Fuera de Sitio

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus mollis quam ac ligula maximus, vitae dictum lorem consequat. Curabitur interdum pretium cursus. Vestibulum pharetra sodales enim, ut vestibulum dui semper quis. Aliquam convallis nulla eu neque vestibulum eleifend. Nam feugiat leo a bibendum rutrum. Duis quis augue et dui vulputate rhoncus. Sed vitae felis fringilla, lacinia est vel, imperdiet leo. Sed suscipit neque risus, eu pharetra dolor rhoncus ac.

#### Usuarios

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus mollis quam ac ligula maximus, vitae dictum lorem consequat. Curabitur interdum pretium cursus. Vestibulum pharetra sodales enim, ut vestibulum dui semper quis. Aliquam convallis nulla eu neque vestibulum eleifend. Nam feugiat leo a bibendum rutrum. Duis quis augue et dui vulputate rhoncus. Sed vitae felis fringilla, lacinia est vel, imperdiet leo. Sed suscipit neque risus, eu pharetra dolor rhoncus ac.

#### Vehículos

En esta sección se muestran los vehiculos que usted dio de alta, listados por código, patente e identificación. Se muestra tambien a que flota pertenece el vehículo y la marca del vehículo. En la columna opciones usted puede asignar una identificación, asignar una regla, editar la informacion del vehículo, o habilitar/deshabilitar el vehículo.

![Vehiculos Administracion](Content/Includes/AN-HomeBase-UserManal-SP/vehiculosAdministracion.png)

###### Crear nuevo vehículo

Para crear un nuevo vehículo, cliquée el botón "Nuevo" que se encuentra en el lado superior izquierdo.

El formulario para crear un nuevo vehículo recibe los siguientes parámetros:

![Nuevo Vehiculo Administracion](Content/Includes/AN-HomeBase-UserManal-SP/crearNuevoVehiculoAdministracion.png)

En primera instancia, la información del vehículo.

![Nuevo Vehiculo Informacion](Content/Includes/AN-HomeBase-UserManal-SP/crearNuevoVehiculoInformacion.png)

* ***Código:*** El código del vehículo.
* ***Flota:*** La flota a la cual pertenece el vehículo.
* ***Patente:*** La patente del vehículo.
* ***Clase de Vehículo:*** La clase de vehículo.
* ***Tipo:*** El tipo de vehículo (Ej. Auto, Camión, Avioneta).
* ***Año:*** El año del vehículo.
* ***Marca:*** La marca del vehículo.
* ***Color:*** El color del vehículo.
* ***Tipo de servicio:*** Se puede seleccionar ruta urbana variable, ruta urbana fija, inter urbana, larga distancia o ninguna.
* ***Descripción de servicio:*** La descripción del servicio.
* ***Número de motor:*** El número de identificación del motor.
* ***Número de chasis:*** El número de identificación del chasis.
* ***Odómetro inicial:*** La cantidad de kilómetros que tiene el vehículo al momento de darlo de alta.
* ***Odómetro actual:*** La cantidad de kilómetros que tiene el vehículo actualmente. Este campo se va actualizando automáticamente tomando en cuenta los despachos realizados por el vehículo.
* ***Fecha de último odómetro:*** La fecha de la última vez que se sabe cuantos kilómetros tiene el vehículo.
* ***Horas de motor actuales:*** La cantidad de horas de motor que tiene el vehículo actualmente. Este campo se va actualizando automáticamente tomando en cuenta los despachos realizados por el vehículo.
* ***Fecha de ultima hora de motor:*** La fecha de la última vez que se sabe cuántas horas de motor tiene el vehículo.

En segunda instancia, los identificadores del vehículo que se le quieran asignar, o, de no existir, crearlos, haciendo luego click en el botón "Alta rápida"

![Nuevo Vehiculo Identificadores](Content/Includes/AN-HomeBase-UserManal-SP/crearNuevoVehiculoIdentificadores.png)

En tercera instancia, los conductores que se le quieren asignar al vehículo.

![Nuevo Vehiculo Conductores](Content/Includes/AN-HomeBase-UserManal-SP/crearNuevoVehiculoConductores.png)

En cuarta instancia, las reglas que se le quieren asignar al vehículo.

![Nuevo Vehiculo Reglas](Content/Includes/AN-HomeBase-UserManal-SP/crearNuevoVehiculoReglasDeVehiculo.png)

Por último, si las hubiera, se listarán las reglas que están asociadas a la flota a la cual pertenece el vehículo, la cual se seleccionó en ***Flota***.

![Nuevo Vehiculo Reglas De Flota](Content/Includes/AN-HomeBase-UserManal-SP/crearNuevoVehiculoReglasDeFlota.png)

Cuando termine de realizar los cambios, cliquée el botón "Guardar".

## Mis Filtros

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus mollis quam ac ligula maximus, vitae dictum lorem consequat. Curabitur interdum pretium cursus. Vestibulum pharetra sodales enim, ut vestibulum dui semper quis. Aliquam convallis nulla eu neque vestibulum eleifend. Nam feugiat leo a bibendum rutrum. Duis quis augue et dui vulputate rhoncus. Sed vitae felis fringilla, lacinia est vel, imperdiet leo. Sed suscipit neque risus, eu pharetra dolor rhoncus ac.

## Solución de Problemas

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus mollis quam ac ligula maximus, vitae dictum lorem consequat. Curabitur interdum pretium cursus. Vestibulum pharetra sodales enim, ut vestibulum dui semper quis. Aliquam convallis nulla eu neque vestibulum eleifend. Nam feugiat leo a bibendum rutrum. Duis quis augue et dui vulputate rhoncus. Sed vitae felis fringilla, lacinia est vel, imperdiet leo. Sed suscipit neque risus, eu pharetra dolor rhoncus ac.

## Mis Preferencias

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus mollis quam ac ligula maximus, vitae dictum lorem consequat. Curabitur interdum pretium cursus. Vestibulum pharetra sodales enim, ut vestibulum dui semper quis. Aliquam convallis nulla eu neque vestibulum eleifend. Nam feugiat leo a bibendum rutrum. Duis quis augue et dui vulputate rhoncus. Sed vitae felis fringilla, lacinia est vel, imperdiet leo. Sed suscipit neque risus, eu pharetra dolor rhoncus ac.

## Configuración Nano CPI para ATIONet

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus mollis quam ac ligula maximus, vitae dictum lorem consequat. Curabitur interdum pretium cursus. Vestibulum pharetra sodales enim, ut vestibulum dui semper quis. Aliquam convallis nulla eu neque vestibulum eleifend. Nam feugiat leo a bibendum rutrum. Duis quis augue et dui vulputate rhoncus. Sed vitae felis fringilla, lacinia est vel, imperdiet leo. Sed suscipit neque risus, eu pharetra dolor rhoncus ac.


