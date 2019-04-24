![ationetlogo](Content/Images/ATIOnetLogo_250x70.png)
# ATIONet - Native Device Updater Protocol Specification v1.0

<table>
	<tr>
		<th colspan="2" align="left">
			Document Information
		</th>
	</tr>
	<tr>
		<td>
			File:
		</td>
		<td>
			AN-Native_DeviceUpdater_Protocol-Spec
		</td>
	</tr>
	<tr>
		<td>
			Doc Version:
		</td>
		<td>
			1.0
		</td>
	</tr>
	<tr>
		<td>
			Release Date:
		</td>
		<td>
			21, Feb 2019
		</td>
	</tr>
	<tr>
		<td>
			Author:
		</td>
		<td>
			ATIONet LLC
		</td>
	</tr>
</table>

<table>
	<tr>
		<th colspan="3" align="left">
			Change Log
		</th>
	</tr>
	<tr>
		<td>
			Ver.
		</td>
		<td>
			Date
		</td>
		<td>
			Change Summary
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>1.0</p>
		</td>
		<td>
			<p>21/Feb/2019</p>
		</td>
		<td>
			<p>Initial version.</p>
		</td>
	</tr>
</table>

## Contents

<!-- MarkdownTOC depth=3 -->

- Overview
	- [Introduction](#introduction)
	- [Definitions](#definitions)
- [Scope](#scope)
	- [Scope Details](#scope-details)
	- [Messages](#messages)
- [Data Security](#data-security)
- [Message Structure](#message-structure)
	- [Request Format](#request-format)
	- [Response Format](#response-format)
- [Error Handling](#error-handling)
- [Field Descriptions](#field-descriptions)
- Loyalty Transaction Request (LREQ) Message Format
- Loyalty Transaction Response (LRESP) Message Format
- Reference Tables
	- Transaction Codes
	- Account Type
	- Transaction Data Structure
	- Customer Data
	- Currency Codes
	- Authorization Codes
	- Response Codes

<!-- /MarkdownTOC -->

## Visión General
### Introducción
El objetivo de esta documentación es especificar el formato de mensajería de protocolo nativo de la API de mantenimiento de Terminals Management y las funcionalidades requeridas para los sistemas que solicitan integración con la herramienta. Las siguientes secciones proporcionan descripciones de los mensajes y el comportamiento esperado para cada tipo de operación.

### Definiciones
Terminal
Dispositivo al cual serán aplicadas de forma remota actualizaciones de firmwares, parámetros o recursos descritos en una agenda programada, y del que se llevara un control o monitoreo del estado de operatividad y localización física en la cual se encuentra.

#### Agenda
Cronograma programado de actualización de terminal, en el que se agrupan terminales para aplicar una actualización requerida por el usuario en una fecha y hora especifica; en ella se encuentra definido los detalles de la actualización a efectuar (tipo, modo, definición de parámetros, recursos necesarios). 

#### Parámetros
Valores necesarios de configuración de la terminal para poder operar satisfactoriamente con la herramienta.

#### Novedades
Mensaje que contiene la información o donde obtener la información de la actualización a aplicar en la terminal.

## Alcance de la Documentación
Los sistemas de terceros se integran con Terminals Mangement a través de una API.

El presente documento del protocolo de la API de Terminals Management especifica el protocolo de interfaz de mantenimiento, el cual lista un conjunto de mensajes para ayudar al mantenimiento y soporte de una red de terminales; por ejemplo, verificar el estado de las terminales mediante un mensaje denominado KeepAlive, obtener novedades para las terminales registradas en la herramienta y el reporte de parámetros actuales.

### Detalles del alcance
**Protocolo:** Protocolo de Interfaz de Mantenimiento Terminals Management
**Versión:** 1.0.0000
**API URI:** terminalmanagement-api.azurewebsites.net/v1/maintenance

### Mensajes

<table border="1">
	<thead>
		<tr valign="top">
			<th align="left" valign="middle">
				Nombre
			</th>
			<th align="left" valign="middle">
				Versión Protocolo
			</th>
			<th align="left" valign="middle">
				Descripción
			</th>
		</tr>	
	</thead>
	<tbody>
		<tr valign="top">
			<td>
				<p align="left">Keep-Alive</p>
			</td>
			<td>
				<p align="left">1.0.0000</p>
			</td>
			<td>
				<p align="left">Se utiliza para reportar valores de operatividad de la terminal (Código de Terminal, Número de Serie, Sistema Operativo, Modelo del Sistema, Versión del Sistema, IP, Carga de la Batería, Estado del Papel y Fecha de Reporte), además de obtener información de agendas pendientes por aplicación disponible.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">GetNews</p>
			</td>
			<td>
				<p align="left">1.0.0000</p>
			</td>
			<td>
				<p align="left">Se utiliza para obtener los datos de la próxima actualización disponible por aplicar en la terminal.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ParametersReport</p>
			</td>
			<td>
				<p align="left">1.0.0000</p>
			</td>
			<td>
				<p align="left">Utilizado para reportar los valores de los parámetros actuales que posee la terminal activa.</p>
			</td>
		</tr>
	</tbody>
</table>

## Seguridad de Datos
La interfaz API requiere una conexión SSL entre ambas partes. La conexión SSL se establece para cada par de solicitud / respuesta, utilizando una propiedad de certificado de Terminals Management.

## Estructura del Mensaje
Todos los mensajes de la API comparten la misma estructura, lo único que cambia entre mensaje y mensaje es el código de transacción/operación, que indica la función a realizar, y en base al cual se analizan los valores de los campos enviados y recibidos.

La acción HTTP siempre es POST y tanto las solicitudes como las respuestas utilizan un formato JSON.

Solo se acepta una solicitud en cada mensaje.

### Formato del Request
Header:

Accept-Encoding: gzip

Body:

{“NombreDeCampo1”:“ValorDeCampo1”,“NombreDeCampo2”:“ValorDeCampo2”,...,“NombreDeCampoNNN”:“ValorDeCampoNNN” }

### Formato del Response
Header:

Content-Type: application/json; charset=utf-8

Body:

{“NombreDeCampo1”:“ValorDeCampo1”,“NombreDeCampo2”:“ValorDeCampo2”,...,“NombreDeCampoNNN”:“ValorDeCampoNNN” }

## Mensaje KeepAlive
### Request
Descripción del cuerpo:

<table border="1">
	<thead>
		<tr valign="top">
			<th align="left" valign="middle">
				Nombre
			</th>
			<th align="left" valign="middle">
				Tamaño
			</th>
			<th align="left" valign="middle">
				Tipo
			</th>
			<th align="left" valign="middle">
				Condición
			</th>
			<th align="left" valign="middle">
				Descripción
			</th>
		</tr>	
	</thead>
	<tbody>
		<tr valign="top">
			<td>
				<p align="left">TransactionCode</p>
			</td>
			<td>
				<p align="left">3</p>
			</td>
			<td>
				<p align="left">A</p>
			</td>
			<td>
				<p align="left">Requerido</p>
			</td>
			<td>
				<p align="left">Código de transacción / operación</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">TerminalCode</p>
			</td>
			<td>
				<p align="left">4-20</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Requerido</p>
			</td>
			<td>
				<p align="left">Código de Terminal</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Ip</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Opcional</p>
			</td>
			<td>
				<p align="left">Ip de conexión</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SystemModel</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Opcional</p>
			</td>
			<td>
				<p align="left">Modelo del sistema</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SystemVersion</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Opcional</p>
			</td>
			<td>
				<p align="left">Versión del sistema</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SerialNumber</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Requerido</p>
			</td>
			<td>
				<p align="left">Número de serie de terminal</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">OperatingSystem</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Opcional</p>
			</td>
			<td>
				<p align="left">Sistema Operativo</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">BatteryCharge</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Opcional</p>
			</td>
			<td>
				<p align="left">Cantidad de carga de la batería</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">PaperStatus</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Opcional</p>
			</td>
			<td>
				<p align="left">Estado del papel</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">LastSchedule</p>
			</td>
			<td>
				<p align="left">36</p>
			</td>
			<td>
				<p align="left">GUID</p>
			</td>
			<td>
				<p align="left">Opcional</p>
			</td>
			<td>
				<p align="left">Id de última agenda aplicada</p>
			</td>
		</tr>
	</tbody>
</table>

Ejemplo:

{“TransactionCode”:“600”,“TerminalCode”:“AXN8763542”, “Ip”:“192.168.20.154”, “SystemModel”:“ StandAloneTerminal”,“SystemVersion”:“ 2.0.0150”,“SerialNumber”: “SR937492”,“OperatingSystem”:“ EVO”,“BatteryCharge”:“100%”, “PaperStatus”:“OK”,“LastSchedule”:“ 90BEBD7C-78F8-4711-A304-0E690F2A0466” }

Response
Descripción del Cuerpo:

XXXXXXXXXXXXXXXXXXXXXXXXXXX

Ejemplo:

{“TransactionCode”:“ 601”,“SiteDateTime”:“ 05-11-18 09:10:00”,“SiteTimeZone”:“Argentina Standard Time”,“HostDateTime”:“ null”,“IdSchedule”:“90BEBD7C-78F8-4711-A304-0E690F2A0466”}

Mensaje GetNews
Request
Descripción del Cuerpo:

XXXXXXXXXXXXXXXXXXXXXXXXXX

Ejemplo:

{“TransactionCode”:“602”,“TerminalCode”:“AXN8763542,“SerialNumber”:“SR937492”,“IdSchedule”:“ 90BEBD7C-78F8-4711-A304-0E690F2A0466”}
Response
Descripción del Cuerpo:

XXXXXXXXXXXXXXXXXXXXXXXXX

Ejemplo:

{“TransactionCode”:“603”,“FirmwareUrl”: “https://storage.blob.net/terminalsmanagment/firmwares/45aa5bd5-7344-f8688c6878a14e42483.zip”, “ResourcesUrl”:“https://storage.blob.net/terminalsmanagment/Resources/45aa5bd5-7344-4f86-88c6-878a14e42483.zip”,“ Configurations”:“{“Parámetro1”:“Valor1”,“Parámetro2”:“Valor2”,…,“ParametroN”: “ValorN”}” ,“ ApplicationMethod”:“0”}


Mensaje ParametersReport
Request
Descripción del Cuerpo:

XXXXXXXXXXXXXXXXXXXXXXXXXXXX

Ejemplo:

{“TransactionCode”:“604”,“TerminalCode”:“AXN8763542”,“SerialNumber”:“SR937492”,“ Configurations”:“{“Parámetro1”:“Valor1”,“Parámetro2”:“Valor2”,…,“ParametroN”: “ValorN”}”}

Response
Descripción del Cuerpo:

XXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

Ejemplo:

{“TransactionCode”:“605”,“ResponseMessage”:“OK”}

Códigos de Transacción / Operación
Se refiere a los códigos con lo cual se indica que tipo de transacción/operación se realizará.

XXXXXXXXXXXXXXXXXXXXXXXXXXXXxxxxx