![ationetlogo](Content/Images/ATIOnetLogo_250x70.png)
# Ationet Fleet Mobile Payment POS Integration #

|Document Information||
|--- |--- |
|Archivo:|ATIONet - POS Integration|
|Version:|1.0|
|Fecha de lanzamiento:|22, February 2024|
|Autor:|ATIONet LLC|

|Change Log|||
|--- |--- |--- |
|Ver.|Fecha|Cambios|
|1.0|22/February/2024|Initial version.|


##Objetivo##
Esta especificación está destinada a documentar el formato de mensajería para operaciones de autorizaciones de despachos de flotas a través de la aplicación móvil ATIONET Driver. Las siguientes secciones brindan descripciones de los propios mensajes y el comportamiento esperado para cada tipo de transacción admitida en la comunicación entre el ATIONET Driver y el host de ATIONET.

## Diagrama General de la solución ##


![image](https://github.com/Ationet/ationetdocs/assets/96298341/bc1c9001-5762-4f5f-8d4b-86933fc8512e)


### ATIONET Driver Operaciones ###
A continuación, se listan las operaciones realizadas por Ationet Driver, en las mismas se asume que la negociación de token es siempre correcta.

## Listado de Transacciones ##
 
![image](https://github.com/Ationet/ationetdocs/assets/96298341/254870a1-28ef-4f02-bab1-935a562a5373)

Detalle del flujo

1.	Login: Usuario ingresa credenciales
2.	Connect/Token: Ationet Driver negocia el token con el STS
3.	Get /Transactions: Ationet Driver solicita el listado de transacciones 
4.	Data Lookup: Fidelidad API busca el listado de transacciones en la base de ATIONET (flotas y fidelidad).  Ationet Driver App muestra los datos por pantalla


### Listado de pre autorizaciones pendientes ###
![image](https://github.com/Ationet/ationetdocs/assets/96298341/d04390ff-9b66-4db7-be93-c86efa2fa0ae)

Detalle del flujo

1.	Login: Usuario ingresa credenciales
2.	Connect/Token: Ationet Driver negocia el token con el STS
3.	Get /Transactions: Ationet Driver solicita el listado de transacciones 
4.	Data Lookup: MobileAppsHost API busca el listado de transacciones de tipo preautorización en la base de MobileAppsHost.  Ationet Driver App muestra los datos por pantalla


### Listado de identificadores/registro de tarjetas ###
![image](https://github.com/Ationet/ationetdocs/assets/96298341/ae3bc073-f768-4eed-a137-e12046ddb518)

Detalle del flujo

1.	Login: Usuario ingresa credenciales
2.	Connect/Token: Ationet Driver negocia el token con el STS
3.	Get /Transactions: Ationet Driver solicita el listado de identificadores, dependiendo del flujo el mismo podrá ser filtrado para buscar por patente de vehículo
4.	Data Lookup: Fidelidad API busca el listado de identificadores asociados al usuario driver de acuerdo a la configuración de contratos de compañía.  Ationet Driver App muestra los datos por pantalla
5.	Con la data listada Ationet Driver App dará al usuario la opción de registrar el/los identificadores necesarios para operar mediante la misma.



# Operaciones de despacho #

Nota: Para simplificación del diagrama no se ha incluido la negociación del token, por lo cual esta debe ser tomada en cuenta al momento de realizar la acción.

## Pre Authorizaciones (Inicio en Ationet Driver App) ##

![image](https://github.com/Ationet/ationetdocs/assets/96298341/76541877-fed7-45c6-a9e6-cf3f4e2f1d87)



Detalle del flujo

1.	Prepaid Request: el usuario driver inicia el flujo desde la app móvil seleccionando posición de carga, combustible, cantidad, monto para generar una solicitud de pre-autorización
2.	Authorize Request: Ationet Driver App solicita la autorización de la solicitud de pre-autorización
3.	Authorize Request: Mobile Apps host solicita la autorización de la solicitud de pre-autorización a fidelidad native protocol.
4.	Generate QR: La app driver genera un código QR con los datos de pre-autorización para que la app terminal pueda leer los datos de la misma
5.	Get Transaction Status (PreAuth): Ationet driver app inicia un proceso de polling para obtener el estado de la transacción con el fin de detectar los estados del despacho, el mismo se da hacia la API mobile apps host
6.	Get Auth Data: Este paso es opcional, se ejecuta si el operador de la terminal decide ingresar manualmente los datos de la autorización pudiendo:
a.	Escanear el QR que genera la aplicación móvil.
b.	Ingresar manualmente el código de autorización presentado en la aplicación móvil.
7.	Get Pending Auths: Este paso es opcional, se ejecuta si el operador de la terminal decide listar las autorizaciones pendientes para luego seleccionar la que desea presetear
8.	Get Auth Detail: La terminal consulta el detalle de la autorización seleccionada/escaneada o ingresada manualmente en Fidelidad Native protocol
9.	Preset: se selecciona la posición de carga en la terminal y se realiza el pedido de preset hacia FUSION
10.	Reserve Notification: Fusion informa a la terminal la aprobación del preset, la terminal pide la autorización del despacho
11.	Authorization Notification: Fusion informa a la terminal la autorización del despacho
12.	Authorization Notification: la terminal informa a fidelidad native protocol autorización del despacho
13.	Authorization Notification: fidelidad native protocol informa a mobile app hosts la autorización del despacho
14.	Authorization Notification: Fusion informa a la terminal el inicio del despacho despacho de combustible
15.	Authorization Notification: la terminal informa a fidelidad native protocol el inicio del despacho despacho de combustible
16.	Authorization Notification: fidelidad native protocol informa a mobile app el inicio del despacho despacho de combustible
17.	Authorization Notification: Fusion informa a la terminal el fin del despacho despacho de combustible
18.	Authorization Notification: la terminal informa a fidelidad native protocol el fin del despacho despacho de combustible
19.	Authorization Notification: fidelidad native protocol informa a mobile app el fin del despacho despacho de combustible
20.	End Transaction: En este punto la terminal puede imprimir el ticket del despacho y Ationet Driver muestra por pantalla la finalización del despacho


## Mensajería ##

### Estructura de Mensajes ###

Todos los Requests soportan los mismos headers, ya sea el de autenticación o el de compresión. El body en aquellos Requests que lo requieran, también deberá incluirse en formato JSON. 
Como respuesta a cualquier request, ATIONet devolverá un Response totalmente estándar con HTTP, donde el HTTP Response Code es el primer valor que se deberá chequear, donde se toma como respuesta correcta el 200, cualquier otro Response Code, es considerado un error y el cliente deberá actuar en consecuencia. Para mayor información sobre HTTP Response codes puede chequear este link

## Formato Del Request ##
Headers:
<p>
Accept-Encoding: gzip
 
Authorization: Bearer [Token generado por STS]

o

Authorization: Basic [Credenciales] para el caso de fidelidadnativeprotocol api

</p>

## Authorize Request ##
Paso 2. Ationet Driver App realiza la pre autorización
```
HTTP Verb: POST
URL: https://{URL}/api/PreAuth/Authorize
Input: application/json
Output: application/json
Formato Request/Body: application/json 
Scope: Mobile Payment API

Header
Content-Type: application/json; charset=utf-8
content-encoding: gzip

Body
{
    "SiteCode": "{siteCode}",
    "PumpNumber": {pumpNumber},
    "FuelCode": "{fuelCode}",
    "Amount": {amount},
    "PrimaryTrack": "{primaryTrack}",
    "TerminalCode":"{terminalCode}",
    "MobileMode": {mode},
    "PotencyKeyId": "{new guid id format string}",
    "ExternalReferenceId": ""
}
```

## PreAuth Request (Get Transaction) ##
Paso 5. Ationet Driver App obtiene el estado de la pre autorización generada. Esto queda iterando para ir conociendo el estado de la transacción.
```
HTTP Verb: GET
URL: https://{URL}/v1/MobileApps/?Id={TransactionId}
Input: application/json
Output: application/json
Formato Request/Body: application/json 
Scope: Native Protocol

Header
Content-Type: application/json; charset=utf-8
content-encoding: gzip
Body: Empty
```


## Get Pending Auths ##
Paso 7. Este paso es opcional, se ejecuta si el operador de la terminal decide listar las autorizaciones pendientes para luego seleccionar la que desea presetear.
Mediante el SiteCode permite listar las autorizaciones pendientes para posteriormente permitir que la Terminal pueda seleccionar la misma para operar.
```
HTTP Verb: GET
URL: https://{URL}/v1/MobileApps/List?siteCode={siteCode}&terminalCode=&authCode=&trackNumber=
Input: application/json
Output: application/json
Formato Request/Body: application/json 
Scope: Native Protocol
Body: Empty
```

## Get Auth Detail ##
Paso 8.  La terminal consulta el detalle de la autorización seleccionada/escaneada o ingresada manualmente en Fidelidad Native protocol. Esto se relaiza de la misma forma que se obtiene el detalle de la transacción ya que se hace una consulta por ID.
```
HTTP Verb: GET
URL: https://{URL}/v1/MobileApps/?Id={TransactionId}
Input: application/json
Output: application/json
Formato Request/Body: application/json 
Scope: Native Protocol

Header
Content-Type: application/json; charset=utf-8
content-encoding: gzip
Body: Empty
```
