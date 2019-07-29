![ationetlogo](../Content/Images/ATIOnetLogo_250x70.png)
# ATIONet - Manual de Usuario Network (Suscripción tipo Network)

<table>
	<tr>
		<th colspan="2" align="left">Información documento</th>
	</tr>
	<tr>
		<td>Archivo:</td>
		<td>AN-Network-UserManal-SP</td>
	</tr>
	<tr>
		<td>Version documento:</td>
		<td>1.0</td>
	</tr>
	<tr>
		<td>Fecha:</td>
		<td>2 Agosto 2017</td>
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
		<td>2 Agosto 2017</td>
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
		- [Conductores](#conductores)
		- [Cuentas corrientes de Comercio](#cuentas-corrientes-de-comercio)
		- [Cuentas corrientes de Compañia](#cuentas-corrientes-de-compañía)
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
		- [Transacciones](#transacciones)
		- [Vehiculo](#vehiculos)
	- [Inventario](#inventario)
		- Grafico de Inventarios
		- Inventario
		- Recepciones
		- Reconciliación Inventario 
	- [Administración](#administración)
		- [Categorías de SKUs](#categorías-de-skus)
		- [Comercios](#comercios)
		- [Compañias](#compañias)
		- [Conceptos](#conceptos)
		- [Configuración de Fast Track](#configuración-de-fast-track)
		- [Contingencia](#contingencia)
		- [Contratos de Comercios](#contratos-de-comercios)
		- [Contratos de Compañias](#contratos-de-compañias)
		- [Cuentas corrientes de Comercio](#cuentas-corrientes-de-comercio)
		- [Cuentas corrientes de Compañia](#cuentas-corrientes-de-compañia)
		- [Depositos](#depositos)
		- [Familias de Conceptos](#familias-de-conceptos)
		- [Identificaciones Solicitadas](#identificaciones-solicitadas)
		- [Identificadores](#identificadores)
		- [Impuestos](#impuestos)
		- [Instalaciones](#instalaciones)
		- [Métodos de Pago](#metodos-de-pago)
		- [Modelos de Identificador](#modelos-de-identificador)
		- [Programas](#programas)
		- [Sitios](#sitios)
		- [SKUs](#skus)
		- [Tarjeta de Regalo](#tarjeta-de-regalo)
		- [Tarjetas de Regalo Solicitadas](#tarjetas-de-regalo-solicitadas)
		- [Transacciones Desconocidas](#transacciones-desconocidas)
		- [Usuarios](#usuarios)
- [Mis Filtros](#mis-filtros)
- [Solución de Problemas](#solucion-de-problemas)
- [Mis Preferencias](#mis-preferencias)
- [Configuración Nano CPI para ATIONet](#configuración-nano-cpi-para-ationet)

<!-- /MarkdownTOC -->

## Visión General

ATIOnet se basa en la premisa de que las comunicaciones online entre sitios y el portal web son posibles, sin embargo, provee sólidos procedimientos de contingencia en el caso de que ocurra un error de comunicación.

La plataforma de ATIOnet es un servicio de administración de flotas con una innovadora y única oferta de mercado. Procesamiento en la nube, 100% web-based, acceso multi-usuario, disponibilidad y compartimiento de datos, actualizaciones instantáneas, seguridad, back-up automático y reducción de papeleo.

ATIOnet es un portal web para compañías de servicios de flotas que permite el procesamiento de transacciones desde cualquier aplicación de punto de venta mediante una interfaz simple y confiable. 

ATIOnet puede ser instalado en cualquier estación de servicio con uno o múltiples programas de servicios de flotas. El portal web le permite a los administradores de flotas acceso total a la información de sus vehículos.

ATIOnet hace posible que el administrador de flota opere, monitoree, cambie y edite la información de la flota en tiempo real.

## Definiciones

### Contrato 

El contrato es la relación que existe entre la network y el cliente, en el que se pauta, por ejemplo, si sera de importe o volumen, el precio al que se le va a vender el combustible, en que sitios puede cargar, entre otros.

### Sub Cuenta 

Cada vez que se asocia un identificador a un vehículo o un conductor se crea una sub cuenta. La sub cuenta es en definitiva quien va a tener una cuenta corriente, la sub cuenta va a poder recibir depósitos de dinero o producto. Las reglas también impactan a la sub cuenta.

Las sub cuentas dependen jerarquicamente del contrato.

### Compañía 

En ATIOnet, la compañía se refiere a la empresa dueña de la flota.

### Identificador 

El identificador es el medio físico que utiliza ATIONet para poder identificar un vehículo o un conductor. ATIONet soporte varios tipos de identificaciones, como ser tarjeta, tag (anillo), chip, tarjeta ATIONet, entrada manual, código de barras e iButton. Cuando se asocia un identificador a un Vehículo o Conductor se crea una sub cuenta.

### Sitio 

El Sitio representa a la estación de servicio. A un sitio se le asigna la terminal y también puede tener asociadas reglas de Ubicación.

### Vehículo 

Los vehículos pueden ser asociados o agrupados por una flota, pueden tener reglas asociadas y al momento de ser relacionados con un identificador se crea una sub cuenta. También pueden tener un conductor asociado.

### Conductor 

El Conductor es la persona que esta identificado en ATIONet como un conductor. Si a este conductor se le asigna un identificador, se crea una sub cuenta. Los conductores también pueden tener reglas asociadas.

### Modulo Offline 

El modulo offline de ATIONet se activa automáticamente cuando la estación de servicio se queda sin conexión a Internet y las autorizaciones no se pueden procesar online. En este momento entra en juego el modulo offline. Para el controlador Nano CPI es totalmente transparente. Cuando el modulo offline recupera la conectividad envía toda la información procesada localmente y también baja las novedades. Mientras haya conectividad el modulo offline esta continuamente bajando las novedades (saldos, identificadores, reglas, etc) de ATIONet.

### Terminal

La terminal (o controlador) es la representación del controlador de surtidores, que necesita parametrizarse de manera particular según el tipo de terminal. Las terminales que ATIONet maneja son ATIO-NanoCPI, ATIO-Standalone, ATIO-CG, VF-Standalone, VF-Sapphire, VF-Ruby, ControlGas y OPW-FSC3000. 

## Menú de Navegación

ATIOnet posee un menú de acceso rápido ubicado en la parte izquierda de la pagina. Desde este menú usted podrá acceder a las distintas opciones. el menú esta dividido en 7 secciones. (Tablero, Favoritos, Vistas, Reportes, Inventario, Administración y Bitácora)

### Tablero

El Tablero es una pagina donde usted tendrá una visión global de la operación de su red. El tablero posee widgets específicos que lo ayudaran a tomar decisiones preventiva o correctivas según la información y los datos que muestren. Los datos que se muestran en el Tablero, son datos en tiempo real. Algunos de los widgets se refrescan automáticamente.
Estos se pueden quitar o agregar según las necesidades del usuario en la ventana mis preferencias. También se pueden acomodar en el tablero según el nivel de visibilidad que le quiera dar a cada uno.
La lista completa de widgets disponibles para las suscripciones "Network" es la siguiente:

#### Estado General

Este widget es de suma importancia al poner en marcha la red. Este widget nos da información de que parámetros necesitamos configurar para quedar operativos. Nos advierte cuando por ejemplo no tenemos vehículos o identificaciones creadas entre otros parámetros.
Este widget puede mostrar "Advertencias" (ícono amarillo) cuando no esta en juego la operación de la red, pero si muestra una cruz roja indica que la red no esta operativa. 

![Estado General](../Content/Includes/AN-HomeBase-UserManal-SP/estadoGeneral.png)
![Estado General](../Content/Includes/AN-HomeBase-UserManal-SP/estadoGeneral2.png)

#### Litros-Mes

El de "Litros/Mes indica la cantidad que se despachó de cada combustible en el ultimo mes. Como ultimo mes se entiende a los últimos 30 días contando desde el día de la fecha. Este widget posee la capacidad de filtrar por Sitio, Ciudad y Flota. Se debe seleccionar el filtro y después se ingresa el valor por el cual se debe filtrar. Este ultimo campo es del tipo "auto complete".

![Litros Mes](../Content/Includes/AN-HomeBase-UserManal-SP/litrosMes.png)

#### Transacciones del Día

Este widget contiene un gráfico de torta que en forma muy rápida se pueden ver cuantas transacciones se aprobaron y cuantas se rechazaron en el día.

![Transacciones Día](../Content/Includes/AN-HomeBase-UserManal-SP/transaccionesDia.png)

#### Lista de Pre-Autorizaciones Pendientes

Este widget del tipo lista, muestra todas las pre autorizaciones que todavía no recibieron la transacción de finalización. (para mas detalles sobre el flujo de transacciones consulte este [documento](AN-Transaction_Flows-TechGuide.md)).
Este muestra 7 columnas:

1. ***Código de Autorización:*** El código de autorización asignado a la transacción.
2. ***Compañía:*** La compañía a la que pertenece el vehículo en cuestión.
3. ***Patente:*** La patente del vehículo.
4. ***Sitio:*** El sitio donde se llevo a cabo la transacción.
5. ***Autorizado:*** El monto que fue autorizado en la pre autorización.
6. ***Pos:*** Posición o bomba informada por el punto de venta o controlador.
7. ***Age:*** El tiempo en minutos que lleva vigente esa pre autorización.

Las pre autorizaciones pendientes deberían ser despachos en curso, si hay registros en este widget con un Age alto, significa que el punto de venta o controlador no enviaron la transacción de finalización o la transacción de cancelación en el caso que no se haya despachado combustible.

![Pre Auth Pendientes](../Content/Includes/AN-HomeBase-UserManal-SP/preauthPendientes.png)

#### Transacciones marcadas en ultimo mes

El siguiente muestra todas las transacciones que fueron rechazadas por cualquiera de las validaciones que hace ATIONet en el proceso de autorización. Ya sean por falta de saldo o reglas entre otras validaciones. Para mas detalles sobre "Transacciones Rechazadas" consulte este documento: [TODO](#todo)

![Transacciones Marcadas](../Content/Includes/AN-HomeBase-UserManal-SP/transaccionesMarcadasUltimoMes.png)

#### Contratos sin actividad

Muestra la lista de contratos que nunca tuvieron actividad.

![Contrato Sin Actividad](../Content/Includes/AN-HomeBase-UserManal-SP/contratosSinActividad.png)

#### Sub-cuentas con excepciones

Este muestra todas las sub cuentas que tengan algo que prestarle atención, como por ejemplo:

1. ***Sin Identificadores:*** Son los vehículos o conductores que no tienen un identificador asociado.
2. ***Con Identificadores inactivos:*** Son subcuentas que que tienen un identificador asociado que ha sido desactivado desde el portal.
3. ***Con Identificadores suspendidos:*** Son subcuentas que que tienen un identificador que ha sido suspendido. ***Solo ATIONet puede suspender un identificador***.
4. ***Con conductores o vehículos inactivos:*** Son subcuentas que que tienen un vehículo o conductor que no ha sido desactivado desde el portal.

Para mas detalles sobre sub cuentas consulte: [Esta sección](#sub-cuenta)

![sub Cuentas con Excepciones](../Content/Includes/AN-HomeBase-UserManal-SP/subcuentasConExcepciones.png)

#### Transacciones recientes

El siguiente muestra las ultimas 20 transacciones finalizadas. Se muestran los datos mas relevantes para poder identificarla, en el caso de necesitar mas información sobre la transacción se puede hacer click sobre el código de autorización, eso lo llevara a la vista de detalles de la transacción.

![Transacciones Recientes](../Content/Includes/AN-HomeBase-UserManal-SP/transaccionesRecientes.png)

#### Listado de contratos con bajo saldo

Muestra la lista de contratos que contengan bajo saldo para operar 4 días mas. Este calculo se hace en base al uso. La columna "Días disponibles" muestra cantidad de días que le quedan al contrato basada en el análisis de uso. Este numero no es exacto y podría variar si el patrón de uso cambia.

![Contrato Bajo Saldo](../Content/Includes/AN-HomeBase-UserManal-SP/contratoBajoSaldo.png)

#### Listado de Sub-cuentas con bajo saldo

Muestra la lista de sub cuentas que contengan bajo saldo para operar 4 días mas. Este calculo se hace en base al uso de cada sub cuenta. La columna "Días disponibles" muestra cantidad de días que le quedan a la sub cuenta basada en el análisis de uso. Este numero no es exacto y podría variar si el patrón de uso cambia.

![Sub Cuentas Bajo Saldo](../Content/Includes/AN-HomeBase-UserManal-SP/subcuentasBajoSaldo.png)

#### Actualizaciones de Identificador en ultimo mes

Este widget muestra la actividad de la administración de los identificadores, muestra la cantidad de identificadores que fueron modificados agrupado por estado.

1. ***Asignada:*** La cantidad de identificadores que cambiaron al estado "Asignada".
2. ***Disponible:*** La cantidad de identificadores que cambiaron al estado "Disponible".
3. ***Cancelada:*** La cantidad de identificadores que cambiaron al estado "Cancelada".
4. ***Denunciada:*** La cantidad de identificadores que cambiaron al estado "Denunciada".
5. ***Suspendida:*** La cantidad de identificadores que cambiaron al estado "Suspendida".

![Actualizaciones de Identificadores](../Content/Includes/AN-HomeBase-UserManal-SP/actualizacionIdentificadoresUltimoMes.png)

#### Estado de Terminales

Todas las terminales que estén conectadas en forma nativa a ATIONet, envían en forma regular un mensaje indicando que están activas. Si la terminal reporto el estado en las ultimas 5 horas, la terminal se mostrara con el ícono verde, sino se reporto en las ultimas 5 horas el ícono sera rojo.
La columna ***"Age"*** muestra la cantidad de minutos que pasaron desde la ultima vez que se reporta la terminal. 

![Estado Terminales](../Content/Includes/AN-HomeBase-UserManal-SP/estadoTerminales1.png)
![Estado Terminales](../Content/Includes/AN-HomeBase-UserManal-SP/estadoTerminales2.png)

### Favoritos

Las entidades Vehículos, Conductores, Sitios y Flotas son entidades que podrían requerir un control diario por parte de ciertos usuarios. Para facilitar esta tarea usted puede agregar alguna de estas entidades a la lista de Favoritos. Una vez ingresada una entidad a esta lista el acceso es mas rápido y directo, sin necesidad de ingresar filtros cada vez que la desea buscar. 

Una vez dentro de la pagina de Favoritos, al hacer click sobre el link de la columna "Tipo", usted sera redireccionado a la vista detallada de esa entidad. 

Si desea remover una entidad de la lista de Favoritos, haga click sobre el ícono de la derecha con forma de cruz.

![Favoritos](../Content/Includes/AN-HomeBase-UserManal-SP/favoritos.png)

### Vistas

ATIONet dispone de una serie de vistas donde se puede visualizar información de la operación de la red. ATIONet considera una vista a toda aquella pantalla que ademas de poder visualizar información, también es exportable para un post procesamiento. A diferencia de los [***Reportes***](#reportes) que son pantallas que muestran información con un formato pensado para ser impreso y guardado.
Todas las vistas en ATIONet respetan una consistencia en estética y funcionalidad. Todas las vistas poseen una barra de herramientas con todas estas funciones (o al menos alguna de ellas)

![Vistas](../Content/Includes/AN-HomeBase-UserManal-SP/vistas.png) 

1. ***Vista Condensada:*** Esta opción viene activa de defecto cuando se abre la vista, esta opción muestra en la grilla los datos mínimos en un solo renglón.
2. ***Vista Detallada:*** Esta opción activa un segundo renglón en cada registro dentro de la grilla y muestra mas información de cada uno de los registros.
3. ***Imprimir:*** Al hacer click en esta opción, se abre una nueva ventana con los datos mostrados en la grilla pero con un formato orientado a ser impreso, se incluye una cabecera con el logo que el subscriptor configuro.
4. ***Exportar:*** Al hacer click en esta opción la información mostrada en ese momento en la grilla es exportada a Excel. Se iniciara una descarga automática en su navegador.
5. ***Actualizar:*** Algunas vistas donde la frecuencia de cambio de información es alta, podría ser de utilidad querer refrescar la grilla. Esta opción refresca los datos en forma inmediata.  

Algunas vistas también poseen un panel de filtros. Por defecto este panel aparece colapsado, para desplegarlo haga click en la barra que dice "Filtros". Cada vista posee campos específicos por los cuales se puede filtrar. Una vez que haya ingresado los valores deseados presione el botón "Buscar".

![Vistas](../Content/Includes/AN-HomeBase-UserManal-SP/vistas3.png)

Las vistas también poseen paginación y el usuario podrá definir cuantos registros por pagina se muestran. Esta configuración se realiza desde [***Mis Preferencias***](#mis-preferencias)
La siguiente es la vista de Vehículos de ATIONet:

![Vistas](../Content/Includes/AN-HomeBase-UserManal-SP/vistas2.png)

#### Autorizaciones Pendientes

Las autorizaciones pendientes son aquellas transacciones que todavía no recibieron la transacción de finalización. Los registros que se ven en esta vista son despachos que se están llevando a cabo en este momento. Si por alguna razón existen pre autorizaciones viejas, es probable que el POS no haya enviado la transacción de finalización o la de cancelación si el despacho no fue realizado.

Tenga en cuenta que al momento de pre autorizar, ATIONet congelo el monto de la autorización de la cuenta corriente de la sub cuenta.
Esta vista presenta todos los campos necesarios para poder identificar la transacción y el vehículo. Si necesita ver mas detalles, al hacer click en el código de autorización lo llevara a la vista de detalles de la transacción.

![Autorizaciones Pendientes](../Content/Includes/AN-Network-UserManal-SP/autorizacionesPendientes.png)

Si aparecen transacciones pendientes viejas y usted esta seguro que no es un despacho en curso, puede cancelarlas y devolver el saldo a la cuenta corriente.
Para hacer esto tiene 2 maneras, en forma individual, haciendo click en el ícono de la "X" a la derecha de la grilla o en forma masiva seleccionando las transacciones, desplegar el menú "Acciones en Lote" y seleccionar "Cancelar". Esto cancelara las transacciones y devolverá el saldo a cada una de las cuentas corrientes.

![Autorizaciones Pendientes](../Content/Includes/AN-Network-UserManal-SP/autorizacionesPendientes2.png)

(para más detalles sobre el flujo de transacciones consulte este [documento](AN-Transaction_Flows-TechGuide.md))

#### Conductores

En esta vista se listan los conductores que han sido dados de alta. Puede filtrarlos por nombre, identificacion, compañía, regla de alerta o estatus. También, en la columna de opciones que se encuentra a la derecha, puede elegir asignar una identificacion, editarla o marcar al conductor como favorito.

![Conductores](../Content/Includes/AN-Network-UserManal-SP/conductores.png)

#### Cuentas corrientes de Comercio

La vista de Cuentas corrientes de comercio es la vista donde se consultan los balances y movimientos de los comercios.
En ATIONet el termino comercio se refiere a la empresa dueña de los sitios.

Esta vista posee al igual que el resto de las vistas un panel de filtros.
La primer opción en el panel es el tipo de reporte que queremos ver.

![Cuentas Corrientes de Comercio](../Content/Includes/AN-Network-UserManal-SP/cuentasCorrientesDeComercio.png)

#### Cuentas corrientes de Compañía

La vista de Cuentas corrientes de compañía es la vista en donde se consultan los saldos disponibles de las sub cuentas (Recuerde que la sub cuenta es la unión entre un vehículo/conductor y un identificador. Para mas detalles sobre sub cuentas consulte: [Esta sección](#sub-cuenta)).
En ATIONet el termino compañía se refiere a la empresa dueña de la flota. Para mas detalles sobre compañías consulte: [Esta sección](#compañía)

Esta vista posee al igual que el resto de las vistas un panel de filtros.
La primer opción en el panel de filtros es el tipo de reporte que queremos ver:

![Cuentas Corrientes](../Content/Includes/AN-Network-UserManal-SP/tiposDeCuentasCorrientesDeCompañia.PNG)

1. ***Lista de Contratos:*** Esta opción lista los contratos con su respectivo saldo, pero no da detalles de los movimientos, es una vista que resume los datos de cada una de las subcuentas.

	![Cuentas Corrientes](../Content/Includes/AN-Network-UserManal-SP/listaDeContratos.png)

2. ***Movimientos de Contratos:*** Esta opción lista las subcuentas con su respectivo saldo, pero no da detalles de los movimientos, es una vista que resume los datos de cada una de las subcuentas.

	![Cuentas Corrientes](../Content/Includes/AN-Network-UserManal-SP/movimientosDeContratos.png)

3. ***Lista de Sub-cuentas:*** Esta opción lista las subcuentas con su respectivo saldo, pero no da detalles de los movimientos, es una vista que resume los datos de cada una de las subcuentas.

	![Cuentas Corrientes](../Content/Includes/AN-Network-UserManal-SP/listaDeSubCuentas.png)

4. ***Movimientos de Sub-cuentas:*** Esta opción de la vista muestra en detalle cada uno de los movimientos de la subcuenta, tanto los créditos como los débitos.   

	![Cuentas Corrientes](../Content/Includes/AN-HomeBase-UserManal-SP/cuentasCorrientes3.png)

Al seleccionar esta segunda opción se habilitan varios filtros mas:

* ***Estado de Cuenta:*** Numero del extracto de cuenta.
* ***Subcuenta:*** Ingresando uno o varios nombres de subcuenta, solo se listarán los movimientos de esas subcuentas. Tenga en cuenta que este campo es "autocomplete", se completara a medida que escribe, si presiona la barra espaciadora mostrara todas las subcuentas.
* ***Fecha Desde / Fecha Hasta:*** Ingresando estos valores, filtrara los movimientos entre ambas fechas.
* ***Hora Desde / Hora Hasta:*** Ingresando estos valores, filtrara los movimientos entre ambas horas.
* ***Monto Desde / Monto Hasta:*** Ingresando estos valores filtrara, los movimientos cuyo monto este entre ambos valores.
* ***Especies:*** Se puede filtrar por la especie (Producto).
* ***Débito / Crédito:*** Se puede seleccionar que tipo de movimientos se desean ver, si los de débito o los de crédito.
* ***Tipo:*** Que tipo de movimiento genero el movimiento en la cuenta corriente
* ***Origen:*** Origen del movimiento, ya sea la consola de ATIONet, una aplicación móvil o una llamada a la API desde una aplicación de terceros.
* ***Movimientos Transitorios:*** Tildando esta opción se mostraran los movimientos internos que genera ATIONet. Por ejemplo cada vez que se congela saldo después de una pre autorización y se recibe una transacción de finalización, ATIONet devuelve el saldo congelado y posteriormente debita el monto final informado. La devolución del saldo congelado es considerado un movimiento transitorio y no se muestran si esta opción no esta seleccionada.

#### Excepciones

ATIONet separa las transacciones no autorizadas en 2 secciones, las Excepciones y las [Transacciones Rechazadas](#transacciones-rechazadas).
Las Excepciones son aquellas transacciones que no llegaron a pasar las validaciones duras del sistema o las que se detectan como posibles fraudes.

En la vista de Excepciones podemos filtrar por el tipo de Excepción primero. Los tipo de Excepciones disponibles son los siguientes:

![Cuentas Corrientes](../Content/Includes/AN-HomeBase-UserManal-SP/excepciones2.png)

Esta vista también posee el panel de filtros mencionada anteriormente. Vale la pena resaltar el filtro  ***"Transacciones Off-line"***, al tildar esta opción, también se mostraran aquellas transacciones que fueron marcadas como Excepciones en el modulo Offline. 
(para mas detalles sobre el modulo Offline consulte esta [sección](#modulo-offline))

![Cuentas Corrientes](../Content/Includes/AN-HomeBase-UserManal-SP/excepciones4.png)

Una vez que seleccionó los filtros, presione ***"Buscar"*** y se listarán todas las transacciones marcadas como Excepciones.

Algunas transacciones quedan en estado "Revisión" bajo algunas situaciones, como por ejemplo cuando se despacha más de lo autorizado (por un error en el controlador o el POS). En estos casos es necesario aprobar o rechazar la transacción mediante uno de los 2 íconos a la derecha de cada registro.

![Cuentas Corrientes](../Content/Includes/AN-HomeBase-UserManal-SP/excepciones.png)

#### Transacciones

La vista de transacciones es una de las mas importantes en ATIONet. en esta vista se ven las transacciones que se realizaron y fueron aprobadas.

El panel de Filtros posee todos estas posibilidades:

![Transacciones](../Content/Includes/AN-HomeBase-UserManal-SP/transactions.png)

* ***Cod. Autoriz.:*** Código de Autorización entregado por ATIONet.
* ***Vehículo:*** Vehículo o Vehículos (campo autocomplete y de selección múltiple, presionando la barra espaciadora listara los primeros 20 vehículos).
* ***Flota:*** El nombre de la flota. (campo autocomplete y de selección múltiple)
* ***Sitio:*** El nombre del sitio. (campo autocomplete y de selección múltiple)
* ***Fecha Desde / Fecha Hasta:*** Rango de fechas.
* ***Hora Desde / Hora Hasta:*** Rango de horas.
* ***Rendimiento por Periodo:*** ?
* ***Transacciones Off-line:*** Tildando esta opción también se listaran las transacciones aprobadas en modo Offline. (para mas detalles sobre el modulo Offline consulte esta [sección](#modulo-offline))
* ***Turno:*** El turno en el que ocurrió la transacción. (siempre y cuando la terminal o el POS lo informen)
* ***Conductor:*** El nombre del conductor. (campo autocomplete y de selección múltiple).
* ***Terminal / Controlador:*** Nombre de la terminal que registro la transacción. (campo autocomplete y de selección múltiple).
* ***Combustible:*** El producto que intervino en la transacción. (campo autocomplete y de selección múltiple)
* ***Mostrar Transacciones Completas en Cero:*** Tildando esta opción también mostrara las transacciones que se hayan enviado con monto o volumen en 0.
* ***Transacciones con Producto:*** Tildando esta opción también se mostraran transacciones que contengan productos secos.

Una vez seleccionado el filtro deseado se presiona ***"Buscar"*** y listara las transacciones que cumplan con el filtro.

![Transacciones](../Content/Includes/AN-HomeBase-UserManal-SP/transactions2.png)

En la grilla se muestran los datos principales de la transacción, en la columna acciones se puede desconocer una transacción y entrara en el proceso de desconocimiento. (para mas detalles sobre el desconocimiento de transacciones consulte esta [sección](#transacciones-desconocidas)).

Si desea ver el detalle de la transacción, haga click en el Código de Autorización, esto lo llevará a una vista con el detalle de la transacción.

![Transacciones](../Content/Includes/AN-HomeBase-UserManal-SP/transactions3.png)
 

#### Transacciones por Conductor

En esta vista se pueden ver las transacciones, agrupadas por  el conductor que la realizó. Los botones que están colocados en la parte superior izquierda son para imprimir la tabla o crear un archivo Excel de la tabla, respectivamente.

![Transacciones por Sitio](../Content/Includes/AN-HomeBase-UserManal-SP/transaccionesPorConductor.png)

El panel de filtros posee las siguientes posibilidades:

![Transacciones por Sitio](../Content/Includes/AN-HomeBase-UserManal-SP/filtrosTransaccionesPorConductor.png)

* ***Agrupar por:***  Sitio, Flota, Programa, Id Vehículo y/o Fecha.
* ***Conductor:*** Filtrar por el conductor que despachó.
* ***Flota:*** Filtrar por flota a la cual pertenece el vehículo que realizó el despachó.
* ***Id Vehículo:*** Filtrar por el Id del vehículo que realizó el despachó.
* ***Sitio:*** Filtrar por sitio donde se realizó el despacho.
* ***Terminal/Controlador:*** Filtrar por terminal/controlador que despachó.
* ***Combustible:*** Filtrar por el combustible que se despachó.
* ***Fecha desde/Fecha hasta:*** Rango de fechas a filtrar.
* ***Hora desde/Hora hasta:*** Rango de horas a filtrar.

Cuando termine de llenar el formulario, cliquée "Buscar" para aplicar el filtro, o "Crear filtro" para guardar el filtro hecho.

#### Transacciones por Flota

En esta vista se pueden ver las transacciones que se realizaron, agrupadas por flota. Los botones que están colocados en la parte superior izquierda son para imprimir la tabla o crear un archivo Excel de la tabla, respectivamente.

![Transacciones por Sitio](../Content/Includes/AN-HomeBase-UserManal-SP/transaccionesPorFlota.png)

El panel de filtros posee las siguientes posibilidades:

![Transacciones por Sitio](../Content/Includes/AN-HomeBase-UserManal-SP/filtrosTransaccionesPorFlota.png)

* ***Agrupar por:***  Sitio, Vehículo, Id Conductor y/o Fecha.
* ***Flota:*** Filtrar por flota a la cual pertenece el vehículo que realizó el despacho.
* ***Vehículo:*** Filtrar por el vehículo que realizó el despacho.
* ***Id Conductor:*** Filtrar por el Id del conductor que realizó el despacho.
* ***Sitio:*** Filtrar por sitio donde se realizó el despacho.
* ***Combustible:*** Filtrar por el combustible que se despachó.
* ***Terminal/Controlador:*** Filtrar por terminal/controlador que despachó.
* ***Fecha desde/Fecha hasta:*** Rango de fechas a filtrar.
* ***Hora desde/Hora hasta:*** Rango de horas a filtrar.

Cuando termine de llenar el formulario, cliquée "Buscar" para aplicar el filtro, o "Crear filtro" para guardar el filtro hecho.

#### Transacciones por Sitio

En esta vista se pueden ver las transacciones que se realizaron, agrupadas por  el sitio donde ocurrieron. Los botones que están colocados en la parte superior izquierda son para imprimir la tabla o crear un archivo Excel de la tabla, respectivamente.

![Transacciones por Sitio](../Content/Includes/AN-HomeBase-UserManal-SP/transaccionesPorSitio.png)

El panel de filtros posee las siguientes posibilidades:

![Transacciones por Sitio](../Content/Includes/AN-HomeBase-UserManal-SP/filtrosTransaccionesPorSitio.png)

* ***Agrupar por:*** Combustible, Flota, Programa, Turno y/o Fecha.
* ***Sitio:*** Filtrar por sitio donde se realizó el despacho.
* ***Combustible:*** Filtrar por el combustible que se despachó.
* ***Flota:*** Filtrar por flota a la cual pertenece el vehículo que realizó el despacho.
* ***Terminal/Controlador:*** Filtrar por terminal/controlador que despachó.
* ***Fecha desde/Fecha hasta:*** Rango de fechas a filtrar.
* ***Hora desde/Hora hasta:*** Rango de horas a filtrar.

Cuando termine de llenar el formulario, cliquée "Buscar" para aplicar el filtro, o "Crear filtro" para guardar el filtro hecho.

#### Transacciones por Vehículo

En esta vista se pueden ver las transacciones, agrupadas por el vehículo que las realizó. Los botones que están colocados en la parte superior izquierda son para imprimir la tabla o crear un archivo Excel de la tabla, respectivamente.

![Transacciones por Vehículo](../Content/Includes/AN-HomeBase-UserManal-SP/transaccionesPorVehiculo.png)

El panel de filtros posee las siguientes posibilidades:

![Transacciones por Sitio](../Content/Includes/AN-HomeBase-UserManal-SP/filtrosTransaccionesPorVehiculo.png)

* ***Agrupar por:***  Sitio, Flota, Programa, Id Conductor y/o Fecha.
* ***Vehículo:*** Filtrar por vehículo que realizó el despacho.
* ***Flota:*** Filtrar por flota a la cual pertenece el vehículo que realizó el despacho.
* ***Id Conductor:*** Filtrar por el Id del conductor que realizó el despacho.
* ***Sitio:*** Filtrar por sitio donde se realizó el despacho.
* ***Terminal/Controlador:*** Filtrar por terminal/controlador que despachó.
* ***Combustible:*** Filtrar por el combustible que se despachó.
* ***Fecha desde/Fecha hasta:*** Rango de fechas a filtrar.
* ***Hora desde/Hora hasta:*** Rango de horas a filtrar.

Cuando termine de llenar el formulario, cliquée "Buscar" para aplicar el filtro, o "Crear filtro" para guardar el filtro hecho.

#### Transacciones Rechazadas

ATIONet separa las transacciones NO autorizadas en 2 secciones, las [Excepciones](#excepciones) y las Transacciones Rechazadas.
Las Transacciones Rechazadas son aquellas transacciones que lograron pasar las validaciones duras de ATIONet pero fueron rechazadas por otras validaciones como ser alguna regla no satisfecha o validación de saldo.

En la vista de Transacciones Rechazadas podemos filtrar por el tipo de rechazo primero. Los tipo de rechazos disponibles son los siguientes:

![Transacciones Rechazadas](../Content/Includes/AN-HomeBase-UserManal-SP/transaccionesRechazadas.png)

Esta vista también posee el panel de filtros mencionada anteriormente. Vale la pena resaltar el filtro  ***"Transacciones Off-line"***, al tildar esta opción, también se mostraran aquellas transacciones que fueron marcadas como rechazadas en el modulo Offline. 
(para mas detalles sobre el modulo Offline consulte esta [sección](#modulo-offline))

![Cuentas Corrientes](../Content/Includes/AN-HomeBase-UserManal-SP/excepciones4.png)

Una vez que selecciono los filtros, presiona ***"Buscar"*** y se listaran todas las transacciones marcadas como rechazadas.

![Transacciones Rechazadas](../Content/Includes/AN-HomeBase-UserManal-SP/transaccionesRechazadas2.png)

Cabe aclarar que existe la posibilidad de que una transacción sea rechazada pero que el combustible haya sido entregado. Esto ocurre cuando el rechazo se produce en la transacción de terminación.
Algunos de los motivos mas comunes de esta situación los los siguientes:

* La pre autorización esta vencida (mas de 3hs entre la fecha de creación de la pre autorización y la fecha de creación de la terminación. Esto no se relaciona con el tiempo que puede tardar en llegar la terminación en modo offline).
* No existe una pre autorización existente para esa transacción.
* La pre autorización fue cancelada manualmente.
* La transacción de terminación contiene información invalida (errores en la terminal o controlador).
* La transacción de terminación se ejecuto con errores en el host.
* La transacción de terminación contiene información diferente a la de pre autorización, como por ejemplo.
* La transacción de terminación informa mas volumen o importe que el que fue autorizado. En este caso se puede aprobar la autorización.

#### Transacciones sin Control

Las transacciones sin control son aquellas transacciones que se generan porque el controlador detecto una diferencia de aforadores y envía una transacción por la diferencia. Estas transacciones no contienen datos sobre el identificador ya que fueron generadas automáticamente y no se iniciaron con la presentación de un identificador. Al no tener un identificador asignado tampoco se impactan en ninguna cuenta corriente ni cuentan para calculo de reglas.
Esta vista también el panel de filtros para hacer búsquedas mas especificas.

![Transacciones sin Control](../Content/Includes/AN-HomeBase-UserManal-SP/transaccionesFueraDeControl.png)

#### Vehículos

En esta vista se listan los vehículos que han sido dados de alta. Recuerde que no es obligatorio cargar vehículos para poder operar, solo es necesario si usted decide asociar los identificadores a vehículos.

Esta vista posee  el panel de filtros para poder especificar mas la búsqueda. Cabe destacar el filtro "Sin Identificación", seleccionando esta opción, se mostraran solo aquellos vehículos que no han sido asignados a un identificador. 

![Vehicles](../Content/Includes/AN-Network-UserManal-SP/vehiculos.png)

Para ver mas detalles del vehículo, haga click en el código:

![Vehicles](../Content/Includes/AN-HomeBase-UserManal-SP/vehicles2.png)

### Reportes

En ATIONet los reportes son considerados aquellos listados de información que si o si van a ser impresos y archivados en formato físico. Al ser impresos ATIONet les agrega una cabecera con el logo de la suscripción automáticamente.

#### Conductor

El reporte de Conductor se puede filtrar por nombre / código de conductor o por identificación.
Una vez seleccionado el filtro se presiona el botón ***Imprimir***, esto desplegará un popup con la información seleccionada.
La información es mostrada con un formato listo para ser impreso, incluyendo el logo de la suscripción y la fecha y la hora de generación del reporte.

Este popup posee un botón imprimir que al apretarlo se abre la ventana de impresión por defecto del navegador de Internet.

![Drivers](../Content/Includes/AN-HomeBase-UserManal-SP/driversReport.png)


#### Transacciones

Este reporte muestra la lista de transacciones realizadas, ordenadas por fecha. Este reporte posee varios filtros para ajustar la búsqueda. El primer campo del panel de filtros  indica porque campo se va a ordenar la lista, el campo seleccionado en esta lista sera mostrado en la primer columna.

![Transactions](../Content/Includes/AN-HomeBase-UserManal-SP/transactionReport.png)

Una vez seleccionado el filtro se presiona el botón ***Imprimir***, esto desplegara un popup con la información seleccionada.
La información es mostrada con un formato listo para ser impreso, incluyendo el logo de la suscripción y la fecha y la hora de generación del reporte.

Este popup posee un botón imprimir que al apretarlo se abre la ventana de impresión por defecto del navegador de Internet.

![Transactions](../Content/Includes/AN-HomeBase-UserManal-SP/transactionReport2.png)


#### Vehículo

Este reporte muestra la lista de vehículos. Este reporte posee varios filtros para ajustar la búsqueda. El primer campo del panel de filtros  indica porque campo se va a ordenar la lista, el campo seleccionado en esta lista sera mostrado en la primer columna.

![Vehicles](../Content/Includes/AN-HomeBase-UserManal-SP/vehiclesReport.png)

Una vez seleccionado el filtro se presiona el botón ***Imprimir***, esto desplegará un popup con la información seleccionada.
La información es mostrada con un formato listo para ser impreso, incluyendo el logo de la suscripción y la fecha y la hora de generación del reporte.

Este popup posee un botón imprimir que al apretarlo se abre la ventana de impresión por defecto del navegador de Internet.

![Vehicles](../Content/Includes/AN-HomeBase-UserManal-SP/vehiclesReport2.png)

### Inventario

#### Gráfico de Inventarios

![Grafico de Inventarios](../Content/Includes/AN-Network-UserManal-SP/graficoDeInventarios.png)

#### Inventarios

![Inventarios](../Content/Includes/AN-Network-UserManal-SP/inventarios.png)

![Inventarios](../Content/Includes/AN-Network-UserManal-SP/nuevoInventario.png)

#### Recepciones

![Recepciones](../Content/Includes/AN-Network-UserManal-SP/recepciones.png)

![Recepciones](../Content/Includes/AN-Network-UserManal-SP/nuevoRecepciones.png)

#### Reconciliación Inventario

![Reconciliacion Inventario](../Content/Includes/AN-Network-UserManal-SP/reconciliacionInventario.png)

### Administración
 
#### Categorías de SKUs

En esta sección usted puede consultar las categorías de SKUs (Stock Keeping Units) ya creados y, si quiere, editarlos haciendo click en el icono del lápiz que se encuentra en la columna opciones. Para hacer las búsquedas mas fáciles, en caso de tener muchas, puede filtrarlas buscando por código, nombre y/o descripción corta.

Para crear un nuevo SKU, cliquée en el botón "Nuevo".

![SKUs](../Content/Includes/AN-Network-UserManal-SP/categoriasDeSkus.png)

###### Crear una nueva categoría de SKU

Para crear una nueva categoría de SKU, debe llenar el siguiente formulario:

![SKUs](../Content/Includes/AN-Network-UserManal-SP/nuevaCategoriaDeSkus.png)

* **Código**: El código de la categoría de SKU.
* **Nombre**: El nombre de la categoría de SKU.
* **Descripción Corta**: Una descripción corta de la categoría de SKU.
* **Primera/Segunda Categoría Padre**: Por ejemplo, si la categoría de SKU fuera "Cigarrillos Camel", la primera categoría padre podría seria "Tabaco" y la segunda seria "Cigarrillos".
* **Es POS**: Tilde esta opción si la categoría de SKU se puede comprar en el punto de venta.
* **Es Seco de Flota**: Tilde esta opción si la categoría de SKU es seco de flota.
* **Es Recompensa**: Tilde esta opción si se puede canjear por puntos de fidelidad.
* **Es Servicio**: Tilde esta opción si es un servicio.
* **Acumula puntos**: Tilde esta opción si la compra del producto acumula puntos de fidelidad. 

#### Comercios

En ATIOnet el termino comercio se refiere a la empresa dueña de los sitios. En esta sección puede ver los comercios existentes con sus detalles y editarlas si quiere.

![Comercios](../Content/Includes/AN-Network-UserManal-SP/comerciosAdministracion.png)

#### Compañías

En ATIOnet el termino compañía se refiere a la empresa dueña de la flota. En esta sección puede ver las compañías existentes con sus detalles y editarlas si quiere. También puede filtrarlas por nombre y/o código.

![Compañías](../Content/Includes/AN-Network-UserManal-SP/compañias.png)

#### Conceptos

En esta sección usted puede consultar los Conceptos ya creados, listados por Código, Nombre, Tipo de Concepto, Familia de Conceptos, Clase, Tipo, Modelo y Estado. Si quiere editarlos, puede hacerlo cliqueando en el icono del lápiz que se encuentra en la columna opciones.

Para crear un nuevo concepto, haga click en el botón "Nuevo".

![Conceptos](../Content/Includes/AN-Network-UserManal-SP/conceptos.png)

###### Crear un nuevo concepto

Para crear un nuevo concepto, debe llenar el siguiente formulario:

![Conceptos](../Content/Includes/AN-Network-UserManal-SP/nuevoConcepto.png)

En la sección información, debe llenar los siguientes campos:

* **Tipo de Concepto**: Seleccione si es de tipo Producto, Descuento o Comisión.
* **Código**: El código del concepto.
* **Nombre**: El nombre del concepto.
* **Familia de Conceptos**: Seleccione a que familia de conceptos pertenece.
* **Clase**: Seleccione a que clase de concepto pertenece.
* **Tipo**: El tipo de concepto.
* **Modelo** El modelo de concepto.
* **Impuestos incluidos**: Tilde esta opción si esta incluido en el monto de la transacción.

En la sección lista de precios, debe llenar los siguientes campos:

* **Fecha desde**: La fecha en la que entra en vigencia el concepto.
* **Moneda**: En que divisa esta el concepto.
* **Precio**: El precio del concepto.

Cuando termine de llenar estos campos, haga click en "Alta".

En la sección impuestos, debe llenar el campo Impuesto con el código del impuesto a aplicar al concepto.

Cuando termine de llenar el formulario, haga click en "Guardar".

#### Configuración de Fast Track

?

![Configuración de Fast Track Administración](../Content/Includes/AN-HomeBase-UserManal-SP/configuracionFastTrackAdministracion.png)

#### Contingencia

En esta sección, usted puede consultar las contingencias de la Network. Para hacer las consultas mas fáciles, usted cuenta con un panel de filtros.

Las contingencias son las transacciones que se realizaron sin una pre-autorización, ya sea porque la terminal estaba off-line o porque no contaba con una.

![Contingencia](../Content/Includes/AN-Network-UserManal-SP/contingencias.png)

Para crear una nueva contingencia, haga click en el botón "Nuevo".

![Contigencia](../Content/Includes/AN-Network-UserManal-SP/nuevaContingencia.png)

Los campos a completar son los siguientes:

* **Código de Autorización**: El código de autorización para la contingencia.
* **Fecha**: La fecha de la contingencia.
* **Hora**: La hora de la contingencia.
* **Sitio**: El sitio donde ocurre la contingencia.
* **Terminal/Controlador**: La terminal/controlador donde ocurre la contingencia.
* **Cuenta Primaria**: ?
* **Cuenta Secundaria**: ?
* **Combustible**: El combustible que se despacho.
* **Volumen Despachado**: La cantidad de combustible despachado.
* **Precio Unitario**: El precio unitario del despacho.
* **Monto Despachado**: ?
* **Turno**: ?
* **Surtidor**: El surtidor de donde se despacho el combustible.
* **Odometro**: La cantidad de kilómetros que marca el odometro del vehículo.
* **Horas de Motor**: La cantidad de horas de motor que tiene el vehículo.
* **Id Conductor**: El identificador del conductor.
* **Id Vehículo**: El identificador del vehículo.
* **Miscelaneos**: ?

#### Contratos de Comercios

En ATIONet el termino comercio se refiere a la empresa dueña de los sitios. En esta sección usted puede consultar los contratos.

![Contratos de Comercio](../Content/Includes/AN-Network-UserManal-SP/contratosDeComercio.png)

Para crear un nuevo contrato de Compañía, haga click en el botón Nuevo.

Los campos a completar son los siguientes:

![Contratos de Compañia](../Content/Includes/AN-Network-UserManal-SP/nuevoContratoDeComercio.png)

* **Código**: El código que le quiere asignar al contrato.
* **Descripción**: Ingrese una descripción del contrato.
* **Comercio**: Seleccione un comercio.
* **Usuario de Comercio**: Ingrese un Usuario de Comercio.
* **Fecha Inicio**: Ingrese la fecha en la que entra en vigencia el contrato.
* **Duración** Ingrese la duración del contrario.
* **Modo de Cuenta Corriente**: Puede seleccionar entre Productos o Importe.

Luego de llenar estos campos, deberá ingresar el combustible asignado al contrato, y llenar los campos Volumen, Limite de Seguridad, Sobregiro, Fechas de Inicio y Finalización del Sobregiro, la moneda en la que se encuentra el Valor del Combustible y el precio del combustible.

![Contratos de Compañía](../Content/Includes/AN-Network-UserManal-SP/nuevoContratoDeComercio2.png)

Lo siguiente es dar de alta diferentes ítems.

Lo primero es la Alta de Sitios. Ingrese el sitio y se cargara abajo, solicitándole que proporcione el precio de los combustibles, y la moneda en la que se encuentran.

Luego de eso, tendrá que llenar el formulario de Configuración de Liquidaciones.

Los campos a completar son los siguientes:

![Contratos de Compañia](../Content/Includes/AN-Network-UserManal-SP/nuevoContratoDeComercio3.png)

* **Tipo de Proceso de Billing**: Seleccione el tipo de proceso de Billing que quiere.
* **Periodicidad**: ?
* **Manual**: Tilde esta opción si ?
* **Hora de Corte**: ?
* **Cargos Deducen del Saldo de Contrato**: Tilde esta opción si los cargos se deducen del saldo del contrato.
* **Separar Documento de Cargos**: ?
* **ID Contribuyente**: ?
* **Nombre**: ?
* **Calle**: ?
* **Calle 2**: ?
* **Código Postal**: ?
* **Ciudad**: ?
* **País**: ?
* **Estado**: ?
* **Moneda**: ?

Por ultimo, debe llenar el formulario de Alta de Conceptos.

![Contratos de Compañía](../Content/Includes/AN-Network-UserManal-SP/nuevoContratoCompañia5.png)

Ingrese un concepto y luego se desplegara otro formulario.

![Contratos de Compañía](../Content/Includes/AN-Network-UserManal-SP/nuevoContratoCompañia6.png)

* **Precio Real**: ?
* **Moneda**: Seleccione la moneda en la que se encuentra el precio.
* **Cantidad**: ?
* **Clearing**: Tilde esta opción si ?
* **Evento de Liquid.**: Seleccione entre Periodo de Contrato, Próxima Corrida del Proceso de Liquidación o Periodo de Resumen. ?
* **Aplicación**: ?

Luego, en la segunda solapa, de Descuentos/Incrementos, debe llenar los siguientes campos.

![Contratos de Compañía](../Content/Includes/AN-Network-UserManal-SP/nuevoContratoCompañia7.png)

* **Clase**: Seleccione si el concepto es de Descuento o de Incremento.
* **Incluido**: Tilde esta opción si ?
* **Tipo**: Seleccione si el concepto es por Monto, Unidades, Porcentual o si es de Monto por unidad.
* **Tipo de Rango**: Seleccione si el tipo de rango es por monto o por unidades.
* **Escalonado**: Tilde esta opción si ?
* **Tipo de Techo**: Seleccione si el tipo de techo es por monto o por unidades.
* **Techo**: Ingrese el valor del techo.

En la sección de Escalones debe llenar los siguientes campos.

* **Rango desde**: ?
* **Rango hasta**: ?
* **Valor**: ?

Cuando termine de llenar estos campos, haga click en el botón "Alta" para darlo de alta.

#### Contratos de Compañía

En ATIONet el termino compañía se refiere a la empresa dueña de la flota. En esta sección usted puede consultar los contratos. 

![Contratos de Compañía](../Content/Includes/AN-HomeBase-UserManal-SP/contratosDeCompaniaAdministracion.png)

Para hacer las consultas mas fáciles existe una ventana de filtros aplicables. Puede filtrar por el código, la compañía, el modo (crédito o débito), la descripción o especies.

![Contratos de Compañía](../Content/Includes/AN-Network-UserManal-SP/filtrosContratosDeCompañia.png)

Para crear un nuevo contrato de Compañía, haga click en el botón Nuevo.

Los campos a completar son los siguientes:

![Contratos de Compañía](../Content/Includes/AN-Network-UserManal-SP/nuevoContratoCompañia.png)

* **Código**: El código que le quiere asignar al contrato.
* **Modo**: Puede elegir si el contrato es de crédito o de débito.
* **Descripción**: Ingrese una descripción del contrato.
* **Compañía**: Seleccione una compañía.
* **Usuario de Compañía**: Ingrese un Usuario de Compañía.
* **Fecha Inicio**: Ingrese la fecha en la que entra en vigencia el contrato.
* **Duración** Ingrese la duración del contrario.
* **Modo de Cuenta Corriente**: Puede seleccionar entre Productos o Importe.
* **Modo del Saldo**: Puede elegir entre Dispersión, Sin Dispersar y Llenado automático.
* **Máxima cantidad de cuentas**: Ingrese la cantidad máximas de cuenta que va a permitir.
* **Validar Sitios**: Tilde esta opción si quiere que valide los sitios.
* **Tarjeta de Regalo**: Tilde esta opción si ?

Luego de llenar estos campos, deberá ingresar el combustible asignado al contrato, y llenar los campos Volumen, Limite de Seguridad, Sobregiro, Fechas de Inicio y Finalización del Sobregiro, la moneda en la que se encuentra el Valor del Combustible y el precio del combustible.

![Contratos de Compañia](../Content/Includes/AN-Network-UserManal-SP/nuevoContratoCompañia2.png)

Lo siguiente es dar de alta diferentes ítems.

Lo primero es la Alta de Sitios. Ingrese el sitio y se cargara abajo, solicitándole que proporcione el precio de los combustibles, y la moneda en la que se encuentran.

Luego, en la sección "Alta identificadores" ingrese los identificadores que quiere relacionar con el contrato.

![Contratos de Compañía](../Content/Includes/AN-Network-UserManal-SP/nuevoContratoCompañia3.png)

Luego de eso, tendrá que llenar el formulario de Configuración de Liquidaciones.

Los campos a completar son los siguientes:

![Contratos de Compañia](../Content/Includes/AN-Network-UserManal-SP/nuevoContratoCompañia4.png)

* **Tipo de Proceso de Billing**: Seleccione el tipo de proceso de Billing que quiere.
* **Periodicidad**: ?
* **Manual**: Tilde esta opción si ?
* **Hora de Corte**: ?
* **Cargos Deducen del Saldo de Contrato**: Tilde esta opcion si los cargos se deducen del saldo del contrato.
* **Separar Documento de Cargos**: ?
* **ID Contribuyente**: ?
* **Calle**: ?
* **Calle 2**: ?
* **Código Postal**: ?
* **Ciudad**: ?
* **País**: ?
* **Estado**: ?
* **Moneda**: ?

Por ultimo, debe llenar el formulario de Alta de Conceptos.

![Contratos de Compañia](../Content/Includes/AN-Network-UserManal-SP/nuevoContratoCompañia5.png)

Ingrese un concepto y luego se desplegara otro formulario.

![Contratos de Compañia](../Content/Includes/AN-Network-UserManal-SP/nuevoContratoCompañia6.png)

* **Precio Real**: ?
* **Moneda**: Seleccione la moneda en la que se encuentra el precio.
* **Cantidad**: ?
* **Evento de Liquid.**: Seleccione entre Periodo de Contrato, Próxima Corrida del Proceso de Liquidación o Periodo de Resumen. ?
* **Aplicación**: ?

Luego, en la segunda solapa, de Descuentos/Incrementos, debe llenar los siguientes campos.

![Contratos de Compañia](../Content/Includes/AN-Network-UserManal-SP/nuevoContratoCompañia7.png)

* **Clase**: Seleccione si el concepto es de Descuento o de Incremento.
* **Incluido**: Tilde esta opción si ?
* **Tipo**: Seleccione si el concepto es por Monto, Unidades, Porcentual o si es de Monto por unidad.
* **Tipo de Rango**: Seleccione si el tipo de rango es por monto o por unidades.
* **Escalonado**: Tilde esta opción si ?
* **Tipo de Techo**: Seleccione si el tipo de techo es por monto o por unidades.
* **Techo**: Ingrese el valor del techo.

En la sección de Escalones debe llenar los siguientes campos.

* **Rango desde**: ?
* **Rango hasta**: ?
* **Valor**: ?

Cuando termine de llenar estos campos, haga click en el botón "Alta" para darlo de alta.

#### Cuentas corrientes de Comercio

En esta sección, usted puede crear una nueva cuenta corriente de Comercio. Los datos a ingresar son la descripción del contrato, el nombre del comercio, el contrato de comercio y el tipo.

![Contratos de Comercio](../Content/Includes/AN-Network-UserManal-SP/nuevaCuentaCorrienteDeComercio.png)

#### Cuentas corrientes de Compañía

En esta sección, usted puede crear una nueva cuenta corriente de compañía. Los datos a ingresar son la descripción de la compañía, el nombre de la compañía, el contrato de compañía y el tipo.

![Contratos de Compañía](../Content/Includes/AN-Network-UserManal-SP/nuevaCuentaCorrienteDeCompania.png)

#### Depósitos

Los depósitos son los lugares físicos en donde se guardan los identificadores.

En esta sección, usted puede consultar los depósitos creados, listados por código y descripción. También los puede editar haciendo click en el icono del lápiz que se encuentra en la columna opciones. Para crear un deposito nuevo, cliquée en el botón "Nuevo" que se encuentra sobre la columna "Código".

![Depósitos](../Content/Includes/AN-Network-UserManal-SP/depositos.png)

Para crear un nuevo deposito, complete los campos código y descripción y cliquée el botón "Guardar".

![Depósitos](../Content/Includes/AN-Network-UserManal-SP/nuevoDeposito.png)

#### Familias de Conceptos

En esta sección, usted puede consultar las familias de conceptos creadas, listadas por Código y Descripción. Si desea editarla, puede hacer click en el icono del lápiz que se encuentra a la derecha.

En ATIOnet, las familias de conceptos son ?

![Depósitos](../Content/Includes/AN-Network-UserManal-SP/familiaDeConceptos.png)

Para crear una nueva familia de conceptos, haga click en el botón "Nuevo" y llene los campos Código y Descripción.

![Depósitos](../Content/Includes/AN-Network-UserManal-SP/nuevoFamiliaDeConceptos.png)

#### Identificaciones Solicitadas

En esta sección usted puede consultar las identificaciones solicitadas, solicitar identificadores de flota y/o fidelidad. También puede realizar acciones como establecer las identificaciones como en producción o como entregadas.

También cuenta con un panel para filtrar las identificaciones solicitadas y así hacer mas fácil la búsqueda. Puede filtrar por nombre de la compañía, numero de orden, programa, contrato, estado y/o programa de fidelidad.

![Identificaciones Solicitadas](../Content/Includes/AN-Network-UserManal-SP/identificacionesSolicitadas.png)

Para solicitar un identificador de flota, haga click en el botón "Solicitar Identificadores de Flota". Cuando lo haga, se abrirá un formulario a llenar. Los campos a completar son:

* **Tipo**: Puede ser de tipo Tarjeta, TAG, Chipkey, Entrada Manual, Tarjeta ATIOnet o ATIOnet TAG.
* **Modelo**: El modelo. Solo se mostraran aquellos que tengan track personalizado.
* **Compañía**: El nombre de la compañía.
* **Contrato**: El contrato.
* **Programa**: Seleccione el programa para el identificador.
* **Cantidad**: La cantidad de identificadores.

Cuando termine de llenar los campos, cliquée el botón "Solicitar identificaciones".

![Identificaciones Solicitadas](../Content/Includes/AN-Network-UserManal-SP/solicitarIdentificadoresDeFlota.png)

Para solicitar un identificador de fidelidad, haga click en el botón "Solicitar Identificadores de Fidelidad". Cuando lo haga, se abrirá un formulario a llenar. Los campos a completar son:

* **Modelo**: El modelo de la Tarjeta ATIOnet.
* **Programa de fidelidad**: El programa de fidelidad al que pertenece el identificador solicitado.
* **Cantidad**: La cantidad de identificadores que quiere solicitar.

Cuando termine de llenar los campos, cliquée el botón "Solicitar identificaciones".

![Identificaciones Solicitadas](../Content/Includes/AN-Network-UserManal-SP/solicitarIdentificadoresDeFidelidad.png)

#### Identificadores

El identificador es el medio físico que utiliza ATIONet para poder identificar un vehículo o un conductor. ATIONet soporte varios tipos de identificaciones, como ser tarjeta, tag (anillo), chip, tarjeta ATIONet, entrada manual, código de barras e iButton. Cuando se asocia un identificador a un Vehículo o Conductor se crea una sub cuenta. En esta sección, se mostraran los identificadores ya creados. En la columna opciones puede editar el identificador, habilitarlo o deshabilitarlo, o liberarlo.

![Identificadores Administracion](../Content/Includes/AN-HomeBase-UserManal-SP/identificadoresAdministracion.png)

###### Crear un nuevo identificador

Para crear un nuevo identificador haga click en el botón nuevo que se encuentra en el lado superior izquierdo.

El formulario para crear un nuevo identificador recibe los siguientes parámetros:

![Nuevo Identificador Administración](../Content/Includes/AN-HomeBase-UserManal-SP/crearNuevoIdentificadorAdministracion.png)

* ***Tipo:*** Puede ser Tarjeta, TAG, Chipkey, Entrada Manual, Tarjeta ATIOnet o ATIOnet TAG.
* ***Modelo:*** El modelo del tipo de identificador seleccionado en ***Tipo***.
* ***Tipo de uso:*** Puede ser de flota, fidelidad o dual.
* ***Programa:*** El programa al cual se le va a asignar este identificador.
* ***Programa de fidelidad:*** El programa de fidelidad al cual se le va a asignar este identificador
* ***Etiqueta:*** El nombre que lleva la tarjeta (Ej. Pablo Pérez)
* ***Track:*** El track es la información que lleva grabada dentro suyo el identificador. Este esta dividido en tres partes. En este campo usted puede editar lo que contiene el segundo campo del track. 
* ***PAN:*** Número de entre 1 y 19 caracteres que se encuentra en el identificador. 
* ***PIN:*** El PIN del identificador.

Nótese que depende el tipo de identificador, pedirá ciertos ítems. Por ejemplo, el TAG no necesita de un PIN. Asimismo, si usted en tipo de programa selecciona "Flota", no le pedirá que ingrese un programa de fidelidad.

En segunda instancia, el formulario se completa asignándole la identificación a un vehículo o conductor.

#### Impuestos

La tabla de impuestos muestra:

* ***Código:*** Código del impuesto.
* ***Descripción:*** Descripción del impuesto.
* ***Tipo:*** Tipo de impuesto (Puede ser un impuesto fijo, un impuesto porcentual o un impuesto fijo por unidad).
* ***Monto:*** El monto del impuesto (En el caso del impuesto porcentual, el porcentaje).
* ***Fecha Desde / Fecha Hasta:*** Rango de fechas.
* ***Opciones:*** Editar el impuesto.

![Impuestos Administración](../Content/Includes/AN-HomeBase-UserManal-SP/impuestosAdministracion.png)

###### Crear un nuevo impuesto

Para crear un nuevo impuesto, cliquée el botón "Nuevo" que se encuentra en el lado superior izquierdo.

El formulario para crear un nuevo impuesto recibe los siguientes parámetros:

![Nuevo Impuesto Administración](../Content/Includes/AN-HomeBase-UserManal-SP/crearNuevoImpuestoAdministracion.png) 

* ***Código:*** El código del nuevo impuesto.
* ***Descripción:*** La descripción del nuevo impuesto.
* ***Tipo:*** Tipo de impuesto (Puede ser un impuesto fijo, un impuesto porcentual o un impuesto fijo por unidad)
* ***Fecha desde:*** La fecha en la que entra en vigencia el impuesto.
* ***Monto:*** El monto del impuesto (En el caso del impuesto porcentual, el porcentaje)

Luego de llenar los campos de ***Fecha desde*** y ***Monto*** cliquée el botón alta. 

Cuando termine de realizar los cambios, cliquée el botón "Guardar".

#### Instalaciones

En ATIOnet, se refiere a Instalaciones el hecho de que un técnico coloque un identificador. 

En esta sección, usted puede consultar todas las instalaciones realizadas, listadas por Fecha, Orden de Trabajo, los identificadores colocados, el vehículo en el que fue colocado el identificador, el deposito de donde se saco el identificador, el técnico que lo coloco y ?

![Instalaciones](../Content/Includes/AN-HomeBase-UserManal-SP/instalaciones.png)

Para crear una nueva Instalación, cliquée en el botón "Nuevo".

![Instalaciones](../Content/Includes/AN-Network-UserManal-SP/nuevoInstalaciones.png)

Los campos que tiene que completar son los siguientes:

* **Orden de Trabajo**: ?
* **Técnico**: El técnico que realizo la instalación.
* **Compañía**: La compañía de la cual era parte el vehículo al que se le realizo la instalación.
* **Fecha**: La fecha en la que se realizo la instalación.
* **Contrato**: El contrato al cual esta ligado el vehículo.
* **Vehículo**: El vehículo al cual se le realizo la instalación.
* **Deposito**: El deposito es el lugar físico de donde se saco el identificador para colocarlo.
* **Tiene OBD**: Tilde esta opción si ?

Si tiene OBD, se desplegaran mas campos:

* **ID**: Ingrese el ID del OBD.
* **Modelo**: Seleccione el modelo del OBD.
* **Sensor**: Tilde esta opción si el OBD cuenta con un sensor.
* **Odometro Inicial**: Ingrese el odometro inicial.
* **Proporción**: ?

Luego, en la sección identificadores, ingrese el identificador.

Cuando termine, cliquée el botón "Guardar"

#### Métodos de Pago

Los métodos de pago son las distintas formas en las que se puede pagar un compra: efectivo, tarjeta de crédito, tarjeta de débito, gift cards, etc. ATIONET es una herramienta para que que un comerciante cree un medio de pago propio: una tarjeta de pago para combustibles.

![Métodos De Pago Administración](../Content/Includes/AN-HomeBase-UserManal-SP/metodosDePagoAdministracion.png)

###### Crear un nuevo método de pago

Para crear un nuevo método de pago, cliquée el botón "Nuevo" que se encuentra en el lado superior izquierdo.

El formulario para crear un nuevo método de pago recibe los siguientes parámetros:

![Nuevo Método De Pago Administración](../Content/Includes/AN-HomeBase-UserManal-SP/crearNuevoMetodoDePagoAdministracion.png)

* ***Código:*** El código del nuevo método de pago.
* ***Descripción:*** La descripción del nuevo método de pago.

Cuando termine de realizar los cambios, cliquée el botón "Guardar".

#### Modelos de Identificador

Los modelos de identificador varían según la necesidad del cliente, pueden ser de tipo Tarjeta (Una tarjeta magnética), TAG (Anillo), Chipkey o Entrada Manual (Un código ingresado a mano).

![Modelos De Identificador Administracion](../Content/Includes/AN-HomeBase-UserManal-SP/modelosDeIdentificadorAdministracion.png)

###### Crear un nuevo modelo de identificador

Para crear un nuevo modelo de identificador, cliquée el botón "Nuevo" que se encuentra en el lado superior izquierdo.

El formulario para crear un nuevo modelo de identificador recibe los siguientes parámetros:

![Nuevo Modelo De Idcentificador Administración](../Content/Includes/AN-HomeBase-UserManal-SP/crearNuevoModeloDeIdentificadorAdministracion.png)

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

Los programas en ATIOnet son ?

![Programas Administración](../Content/Includes/AN-HomeBase-UserManal-SP/programasAdministracion.png)

Para crear un nuevo programa haga click en el botón "Nuevo".

![Programas Administración](../Content/Includes/AN-Network-UserManal-SP/nuevoPrograma.png)

Los campos a completar son los siguientes:

* **Descripción**: La descripción del programa.
* **Aplicar sitios del Contrato**:
* **Modo del Saldo**:
* **Soporta contigencias**:
* **Soporta off-line**:
* **Tarjeta de Regalo**: Tilde esta opción si ?

###### Crear un nuevo programa

Para crear un nuevo programa, cliquée el botón "Nuevo" que se encuentra en el lado superior izquierdo.

El formulario para crear un nuevo programa recibe los siguientes parámetros:

![Nuevo Programa Administración](../Content/Includes/AN-HomeBase-UserManal-SP/crearNuevoProgramaAdministracion.png)

* ***Descripción:*** La descripción del nuevo programa.
* ***Aplicar sitios del Contrato:*** Puede ser no afectado, forzado o no forzado.
* ***Modo del saldo:*** Puede ser no afectado, dispersado, sin dispersar, sin límite o de llenado automático.
* ***Soporta contingencias:*** Puede ser no afectado, forzado o no forzado.
* ***Soporta offline:*** Puede ser no afectado, forzado o no forzado.
* ***Tarjeta de regalo:*** Si incluye tarjeta de regalo o no. Si esta opción es chequeada, aparecerán tres parámetros más:
* ***Monto de tarjeta de regalo:*** El monto de la tarjeta de regalo.
* ***Recargable:*** Si es recargable.
* ***Compañía:*** La compañía a la cuál se le es asignada.

Cuando termine de realizar los cambios, cliquée el botón "Guardar".

#### Sitios

El Sitio representa a la estación de servicio. A un sitio se le asigna la terminal y también puede tener asociadas reglas de Ubicación. En esta sección se listan los sitios ya ingresados en el sistema y sus características. En la columna opciones puede asignarle un impuesto al sitio.

![Sitios Administracion](../Content/Includes/AN-HomeBase-UserManal-SP/sitiosAdministracion.png)

#### SKUs

Los SKUs (Stock Keeping Units, por sus siglas en ingles) son los productos que no son combustible. En esta sección usted puede consultar los creados, editarlos haciendo click en el icono del lápiz que se encuentra en la columna de opciones.

Para buscar mas fácilmente, esta el panel de filtros donde puede filtrar por ciertos parámetros.

Para crear un nuevo SKU, haga click en el botón "Nuevo".

![SKUs](../Content/Includes/AN-Network-UserManal-SP/skus.png)

Los campos a completar son los siguientes:

![SKUs](../Content/Includes/AN-Network-UserManal-SP/nuevoSku1.png)
![SKUs](../Content/Includes/AN-Network-UserManal-SP/nuevoSku2.png)
![SKUs](../Content/Includes/AN-Network-UserManal-SP/nuevoSku3.png)

* **Código**: El código del SKU.
* **Descripción** La descripción del SKU.
* **Descripción Corta**: Una descripción corta del SKU.
* **Descripción Ultra Corta**: Una descripción muy breve del SKU.

* **Tipo de Producto POS**: Seleccione que tipo de producto es.
* **Producto Combustible**: Tilde esta opción si el SKU es un producto combustible?
* **Categoría de SKU**: Ingrese la categoría a la cual pertenece el SKU.
* **Unidad de Medida**: Ingrese la unidad en la que se mide el SKU.
* **Vendible**: Tilde esta opción si el SKU es vendible.
* **Pesable**: Tilde esta opción si el SKU es pesable.
* **Fraccionable**: Tilde esta opción si el SKU es fraccionable.
* **Almacenable**: Tilde esta opción si el SKU es almacenable.
* **En consignación**: Tilde esta opción si el SKU esta en consignación.

* **Disponibilidad Desde/Hasta**: Seleccione las fechas entre las que el SKU esta disponible.
* **Es POS**: Tilde esta opción si el SKU se vende en el punto de venta.
* **Es seco de flota**: Tilde esta opción si el SKU es un producto seco.
* **Es recompensa**: Tilde esta opción si el SKU se puede canjear por puntos de recompensa.
* **Es servicio**: Tilde esta opción si el SKU es un servicio.
* **Acumula Puntos**: Tilde esta opción si el SKU acumula puntos.

* **Stock Volumen Min/Max Default**: ?
* **Días de Restock Default**: ?
* **Volumen de Restock Default**: ?

Lista de Precios.

* **Sitio**: Seleccione el sitio al cual le va a cargar el precio del SKU.
* **Fecha Desde**: Seleccione la fecha en la que entra en vigencia el SKU.
* **Precio**: Indique el precio del SKU.
* **Moneda**: Seleccione la moneda en la que esta el precio del SKU.

Ítems.

* **Formato de Código POS**: Seleccione el formato de código de punto de venta.
* **Código de POS**: Ingrese un código de punto de venta.

Cuando termine de llenar esos dos campos, cliquée el botón "Alta".

* **Impuesto**: Ingrese el código del impuesto al SKU.

#### Tarjeta de Regalo

En esta sección usted puede consultar las tarjetas de regalo creadas. Puede realizar acciones en lote como activarlas o desactivarlas. Para hacer las consultas mas fáciles, cuenta con un panel de filtros en la parte superior.

Para crear una nueva Tarjeta de Regalo, cliquée el botón de "Nuevo".

![Tarjeta de Regalo](../Content/Includes/AN-Network-UserManal-SP/tarjetasDeRegalo.png)

Los campos a completar para crear una nueva tarjeta de regalo son los siguientes:

![Tarjeta de Regalo](../Content/Includes/AN-Network-UserManal-SP/nuevaTarjetaDeRegalo.png)

* **Programa**: El programa al cual va a estar asociada la tarjeta de regalo.
* **Contrato**: El contrato al cual va a estar asociada la tarjeta de regalo.
* **Etiqueta**: La etiqueta es la inscripción que lleva la tarjeta al dorso.
* **PAN**: El PAN es el numero de entre 1 y 19 caracteres que se encuentra en la tarjeta de regalo.
* **Track**: El Track es la información que contiene la tarjeta dentro de ella, que esta dividido en tres partes. En este campo, usted puede personalizar lo que contiene el segundo campo del track.
* **Tipo**: Seleccione si la tarjeta de regalo es de tipo Tarjeta, TAG, Chipkey, Entrada Manual, Tarjeta ATIOnet o ATIOnet TAG.
* **Modelo**: El modelo de la tarjeta de regalo.
* **Fecha de expiración**: La fecha de expiración de la tarjeta de regalo.

Cuando termine de llenar los campos, cliquée el botón "Guardar".

#### Tarjetas de Regalo Solicitadas

En esta sección, usted puede consultar y solicitar lotes de tarjetas de regalo.

![Tarjetas de Regalo Solicitadas](../Content/Includes/AN-Network-UserManal-SP/tarjetasDeRegaloSolicitadas.png)

Para pedir un nuevo lote de tarjetas de regalo, cliquée el botón "Nueva Solicitación".

![Tarjetas de Regalo Solicitadas](../Content/Includes/AN-Network-UserManal-SP/nuevoTarjetasDeRegaloSolicitadas.png)

Los campos a completar son los siguientes:

* **Programa**: Seleccione el programa asignado al lote de tarjetas que esta solicitando.
* **Contrato**: Seleccione el contrato del programa asignado al lote de tarjetas que esta solicitando.
* **Cantidad**: Ingrese la cantidad de tarjetas que quiere solicitar.
* **Fecha de expiración**: Ingrese la fecha en la que vencen las tarjetas de regalo.
* **Tipo**: Seleccione el tipo. Puede ser Tarjeta, TAG, Chipkey, Entrada Manual, Tarjeta ATIOnet o ATIOnet TAG.
* **Modelo**: Seleccione el modelo. Puede ser ATIOnet CG, Tarjeta, Tarjeta Magnética Dorada o Tarjeta Regalo.

#### Transacciones Desconocidas

Las transacciones desconocidas son aquellas que alguna de las dos partes (Comercio o Compañía) dice desconocer.

En esta sección usted puede consultar las transacciones desconocidas, listadas por código, fecha, motivo, estado, numero de transacción, compañía, comercio, sitio. También se encuentra el comentario de la compañía, del comercio y de la red.

Para hacer las consultas mas fáciles, esta sección cuenta con un panel de filtros en la parte superior.

![Transacciones Desconocidas](../Content/Includes/AN-Network-UserManal-SP/transaccionesDesconocidas.png)

#### Usuarios

En esta vista puede consultar los usuarios de la Network. Puede editarlos, haciendo click en el icono del lápiz que se encuentra en la columna opciones. Para habilitar/deshabilitar un usuario, haga click en el icono del candado.

Para crear un nuevo Usuario, haga click en el botón "Nuevo".

![Usuarios](../Content/Includes/AN-Network-UserManal-SP/usuarios.png)

Los campos a completar son los siguientes:

![Usuarios](../Content/Includes/AN-Network-UserManal-SP/nuevoUsuario.png)

* **Correo**: El correo electrónico del usuario.
* **Nombre**: El nombre del usuario.
* **Documento**: El documento del usuario.
* **Calle**: La calle donde reside el usuario.
* **Calle 2**: Otra calle de referencia, como puede ser la de la esquina.
* **País**: El país del usuario.
* **Estado**: El estado del país del usuario.
* **Código Postal**: El código postal de la localidad donde reside el usuario.
* **Teléfono 1**: El teléfono del usuario.
* **Teléfono 2**: Otro teléfono del usuario en caso de que tenga.

* **Rol**: El rol que va a asumir el nuevo usuario.
* **Entidad**: La entidad asignada al usuario.

## Mis Filtros

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus mollis quam ac ligula maximus, vitae dictum lorem consequat. Curabitur interdum pretium cursus. Vestibulum pharetra sodales enim, ut vestibulum dui semper quis. Aliquam convallis nulla eu neque vestibulum eleifend. Nam feugiat leo a bibendum rutrum. Duis quis augue et dui vulputate rhoncus. Sed vitae felis fringilla, lacinia est vel, imperdiet leo. Sed suscipit neque risus, eu pharetra dolor rhoncus ac.

## Solución de Problemas

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus mollis quam ac ligula maximus, vitae dictum lorem consequat. Curabitur interdum pretium cursus. Vestibulum pharetra sodales enim, ut vestibulum dui semper quis. Aliquam convallis nulla eu neque vestibulum eleifend. Nam feugiat leo a bibendum rutrum. Duis quis augue et dui vulputate rhoncus. Sed vitae felis fringilla, lacinia est vel, imperdiet leo. Sed suscipit neque risus, eu pharetra dolor rhoncus ac.

## Mis Preferencias

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus mollis quam ac ligula maximus, vitae dictum lorem consequat. Curabitur interdum pretium cursus. Vestibulum pharetra sodales enim, ut vestibulum dui semper quis. Aliquam convallis nulla eu neque vestibulum eleifend. Nam feugiat leo a bibendum rutrum. Duis quis augue et dui vulputate rhoncus. Sed vitae felis fringilla, lacinia est vel, imperdiet leo. Sed suscipit neque risus, eu pharetra dolor rhoncus ac.

## Configuración Nano CPI para ATIONet

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus mollis quam ac ligula maximus, vitae dictum lorem consequat. Curabitur interdum pretium cursus. Vestibulum pharetra sodales enim, ut vestibulum dui semper quis. Aliquam convallis nulla eu neque vestibulum eleifend. Nam feugiat leo a bibendum rutrum. Duis quis augue et dui vulputate rhoncus. Sed vitae felis fringilla, lacinia est vel, imperdiet leo. Sed suscipit neque risus, eu pharetra dolor rhoncus ac.


