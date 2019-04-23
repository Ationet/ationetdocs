![ationetlogo](Content/Images/ATIOnetLogo_250x70.png)
# ATIONet Inventory Client - Manual de Usuario

<table>
	<tr>
		<th colspan="2" align="left">Información documento</th>
	</tr>
	<tr>
		<td>Archivo:</td>
		<td>ANInventoryClient-UserManal-SP</td>
	</tr>
	<tr>
		<td>Versión documento:</td>
		<td>1.0</td>
	</tr>
	<tr>
		<td>Fecha:</td>
		<td>1 Abril 2019</td>
	</tr>
	<tr>
		<td>Autor:</td>
		<td>ATIONet LLC</td>
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
		<td>1 Abril 2019</td>
		<td>Versión inicial.</td>
	</tr>
</table>

## Contenido
<!-- MarkdownTOC depth=3 -->
- Introdución
- Descarga / Instalación
- Configuración
	- Valores de Configuración
- Iniciar el servicio
- Detener el servicio

<!-- /MarkdownTOC -->

## Introdución
ATIONet Inventory Client es un servicio que permite la descarga automática de datos de inventarios y despachos desde un ATG con protocolo VeederRoot, Pv4 o ControlGas instalado en los sitios y actualiza dichos datos en el portal de ATIONet.

## Descarga / Instalación
ATIONet Inventory Client es muy sencillo de instalar. Para realizar la instalación del servicio debe disponer del paquete instalador del mismo, con el nombre "ATIONet Inventory Client" (proporcionado por ATIONet) y hacer doble click en dicho archivo para ejecutarlo. Se desplegará la siguiente vista:

<center><img src="Content/Includes/ANInventoryClient-Manual/1.png" width="50%"></center>

Una vez se despliega esta imagen de bienvenida al instalador, se debe presionar siguiente (Next) para continuar con la misma o cancelar (Cancel) si no se desea continuar con el procedimiento de instalación.

Al presionar siguiente (Next) aparecerá una nueva ventana donde se solicita o configura la ubicación/directorio donde serán almacenados los archivos de nuestro servicio.

<center><img src="Content/Includes/ANInventoryClient-Manual/2.png" width="50%"></center>

Seguido a la selección de ubicación se debe hacer click en siguiente (Next)
 y confirmar la instalación de nuestro servicio ATIONet Inventory Client en la nueva ventana desplegada. A continuación se muestra la ventana de solicitud de confirmación de instalación:

<center><img src="Content/Includes/ANInventoryClient-Manual/3.png" width="50%"></center>

Al culminar el proceso se desplegará una nueva ventana informando que se ha completado la instalación y se encuentra disponible el servicio para ser configurado e iniciado. 

<center><img src="Content/Includes/ANInventoryClient-Manual/4.png" width="50%"></center>


## Configuración
Para configurar nuestro servicio se debe acceder a la carpeta/directorio seleccionada previamente en la instalación donde fueron almacenados los archivos (Ejemplo C:\Program Files (x86)\ATIONet\ATIONet Inventory Client); seleccione el archivo "InventoryClient.exe" y proceda a abrirlo en un "WordPad" o un editor de texto, en modo administrador.

<center><img src="Content/Includes/ANInventoryClient-Manual/Directorio.png" width="80%"></center>

Una vez abierto el archivo "InventoryClient.exe" en modo administrador, ubicar dentro del mismo el sector "appSetting" y modifique los valores necesarios para que el servicio funcione correctamente. Culminado las modificaciones en la configuración, guarde el archivo e inicie el servicio.

<center><img src="Content/Includes/ANInventoryClient-Manual/Config.png" width="70%"></center>

#### Valores de Configuración
Los campos configurables en el archivo poseen el siguiente formato: 
'add key="NOMBRE_CAMPO" value="VALOR_CAMPO"'.

##### Definiciones:
    
- PollingRateSeconds, PollingRateMinutes, PollingRateHours: Campos de valores enteros de espera para corrida del proceso, se puede realizar combinación entre ellos. Ejemplo: si se desea estipular que el proceso se ejecute una vez cada hora con 20 minutos y 30 segundos se debe colocar los siguientes valores en el config:
	- add key="PollingRateSeconds" value="30"'
	- add key="PollingRateMinutes" value="20"'
	- add key="PollingRateHours" value="1"'
- Socket.TimeOut: Tiempo de espera de respuesta en la comunicación.
- Serial.WriteEcho: Valor booleano usado para lectura de bytes en comunicaciones seriales.
- ModeLA: Valor booleano para indicar si se conectara con Local Agent para enviar Data a ATIONet.
- IPLA: IP de conexión de Local Agent.
- PortLA: Puerto de comunicación del Local Agent.
- TerminalLA: Código de Terminal registrado en ATIONet.
- AtgProtocol: Campo con valor entero para indicar el Protocolo ATG a utilizar: 
	- 0:VedeerRoot
	- 1:ControlGas
	- 2:Pv4
- AtgPassword: Contraseña del ATG (opcional, si es requerida).
- iConnType: Valor entero para indicar el tipo de comunicación a establecer
	- 0:Serial
	- 1:Tcp
- TcpPort: Puerto por medio del cual se establecerá la comunicación. Usada para comunicaciones Tcp.
- TcpHostIP: Dirección IP de conexión; usaba para comunicaciones Tcp.
- SerialPort: Puerto por el cual se establecerá la comunicación; usado para comunicación de tipo Serial.
- SerialBaudios: Valor entero para indicar el número de Baudios; usado para comunicación de tipo Serial
- SerialDataBits: Valor entero para indicar el número de bits de transmisión; usado para comunicación de tipo Serial.
- SerialParity: Valor entero para indicar paridad; usado para conexión de tipo Serial.


## Iniciar el Servicio
Para iniciar la ejecución del servicio se puede hacer de dos formas:

- **Modo Consola:** para ejecutar el servicio en modo consola se debe ingresar al directorio donde se encuentran los archivos instalados, previamente seleccionado durante la instalación (Ejemplo C:\Program Files (x86)\ATIONet\ATIONet Inventory Client) y crear un acceso directo para el archivo "InventoryClient". Una vez que se cree el acceso directo se debe hacer click derecho sobre el mismo y seleccionar propiedades.

<center><img src="Content/Includes/ANInventoryClient-Manual/Property.png" width="25%"></center>


Luego de desplegar la ventana de propiedades se debe agregar al final en el campo "Destino" el texto " -console" y aceptar/aplicar los cambios.

<center><img src="Content/Includes/ANInventoryClient-Manual/Property2.png" width="35%"></center>

Posteriormente se debe hacer doble click sobre el acceso directo creado y el servicio ATIONet Inventory Client levantará una consola y comenzará su ejecución.

<center><img src="Content/Includes/ANInventoryClient-Manual/Console.png" width="70%"></center>


- **Modo Servicio de Windows:** si se desea que ATIONet Inventory Client corra como un servicio de Windows, se deben seguir los siguientes pasos:
	1. Abra el Administrador de control de servicios. <div class="pull-right"><img src="Content/Includes/ANInventoryClient-Manual/ServiciosMenu.png" width="20%"></div>
	2. Seleccionar el servicio con el nombre "ATIONet Inventory Client Service".
	3. Hacer click en Iniciar el Servicio. <center><img src="Content/Includes/ANInventoryClient-Manual/ServicioIni.png" width="90%"></center>


## Detener el Servicio
- **Modo Consola:** si el servicio se encuentra en ejecución en este modo y se desea detener, se debe ingresar en la consola la palabra "stop" y presionar "Enter"; esta acción hará que se cierre la consola y se detendrá el servicio. <div><center><img src="Content/Includes/ANInventoryClient-Manual/ConsoleStop.png" width="70%"></center></div>

- **Modo Servicio de Window:** para detener ATIONet Inventory Client si se encuentra corriendo en este modo, debe seguir los siguientes pasos:
	1. Abra el Administrador de control de servicios. <div class="pull-right"><img src="Content/Includes/ANInventoryClient-Manual/ServiciosMenu.png" width="20%"></div>
	2. Seleccionar el servicio con el nombre "ATIONet Inventory Client Service".
	3. Hacer click en Detener el  Servicio. <center><img src="Content/Includes/ANInventoryClient-Manual/ServicioStop.png" width="90%"></center>