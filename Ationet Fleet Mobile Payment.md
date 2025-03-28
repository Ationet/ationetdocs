![ationetlogo](Content/Images/ATIOnetLogo_250x70.png)
# Ationet Fleet Mobile Payment - Fleet Authorization #

|Información de Documento||
|--- |--- |
|Archivo:|ATIONet - Fleet Mobile Payment Fleet Authorization|
|Doc Version:|1.0|
|Fecha:|25-03-2025|
|Autor:|Alexis E. Yañez|

|Control de Cambios |||
|--- |--- |--- |
|Ver.|Fecha|Cambios|
|1.0|25-03-2025|Initial version.|

## Contenido ##
- [Introducción](#Introducción)
- [Mensajería de Configuración](#mensajería-de-configuración)
  - [Flujo de Inicialización](#flujo-de-inicialización)
  - [Connection](#Connection)
  - [Mobile Events](#Mobile_Events)
  - [Site Data](#site-data)
  - [Products](#products)
  - [Dispensers](#Dispensers)
  - [Modes](#Modes)
  - [Country Settings](#country-settings)
- [Mensajería Transaccional](#mensajería-transaccional)
  - [Flujo Transaccional](#flujo-transaccional)
  - [Mensajería del Host al SiteSystem](#mensajería-del-host-al-siteSystem)
    - [Descripción General SSE](#descripción-general-sse)   
    - [FPReserveRequest](#fpreserveRequest)   
    - [AuthorizeRequest](#authorizeRequest)    
    - [FPReserveCancelRequest](#fpreserveCancelRequest)
  - [Mensajería del SiteSystem al Host](#mensajería-del-SiteSystem-al-Host)
     - [Descripción General](#descripción-general)
     - [Reserve Notification POST](#reserve-notification-post)
     - [Reserve Notification DELETE](#reserve-notification-delete)
     - [Transaction Info](#transaction-info)
     - [Authorization Notification](#authorization-notification)
     - [Begin Fueling Notification](#begin-fueling-notification)
     - [Finalize Transaction Notification](#finalize-transaction-notification)
- [Colección Postman](#colección-postman)
- [Ejemplo en C#](#ejemplo-en-c)



## Introducción
Este documento describe la operación para efectuar una transacción con una autorización por medio del autorizador de flota de Ationet a travez de nuestra aplicación móvil.

## Mensajería de Configuración

### Flujo de Inicialización 

<div align="center">
  <img src="https://github.com/user-attachments/assets/1a3643c2-3583-4efc-afa3-407f0b6ebfeb" alt="Diagrama de Secuencia de Conexión SSE">
</div>


### Connection

<b>Relative URL:</b> /connection </br>
<b>Method:</b> POST </br>
<b>Input:</b> application/json </br>
<b>Output:</b> application/json </br>
<b>Uso:</b> Verificación de conexión y heartbeat. El Site System enviará este mensaje periódicamente cada 45 segundos. En caso de no recibir respuesta, se cerrará la conexión SSE, la cual se establecerá nuevamente tan pronto como el MPPA responda satisfactoriamente a este mensaje.
En caso de recibir respuesta y que el Status Code sea un 400 (Bad Request), el Site System cerrará la conexión SSE (en caso de tenerlo abierto) y se establecerá una nueva conexión.

<b>Request Body:</b>
```json
{
  "applicationSender": "{{SiteCode}}",
  "workstationID": "{{SiteCode}}",
  "timestamp": "2009-11-20T17:30:50",
  "interfaceVersion": "1.0"
}
```

<b>Definición de Campos:</b> </br>
<b>applicationSender:</b> Debe contener el SiteCode del sitio que se encuentra operando.</br>
<b>workstationID:</b>  Debe contener el SiteCode del sitio que se encuentra operando.</br>
<b>timestamp:</b> fecha y hora de la solicitud</br>
<b>interfaceVersion:</b> valor fijo</br>

<b>Response Body:</b>
Se obtiene un HTTP Response 200 o 400 dependiendo si se pudo procesar correctamente el request, sin body.


### Mobile Events

<b>Relative URL:</b> /mobileEvents </br>
<b>Method:</b> GET </br>
<b>Input:</b> application/json </br>
<b>Output:</b> application/json </br>
<b>Uso:</b> Permite solicitar al MPPA Host una nueva sesión con el fin de que esta sea utilizada para operar. En su respuesta entrega una URL (propiedad url del body del response) con la cual se ejecutarán los mensajes de configuración siguientes y se podrá obtener el ID de sesión con la cual se operará.
Los mensajes de configuración de la sesión se realizan agregando a esta URL la acción que se desea configurar.

<b>Request Header:</b> Dentro del header se debe enviar la Key ApplicationSender cuyo valor será el SiteCode utilizado. Esto se hace para realizar una detección temprana sobre que sitio está solicitando la creación de una nueva sesión. 

<b>Request Body:</b>
Vacío

<b>Response Body:</b>
Se obtiene un HTTP Response 200 o 400 dependiendo si se pudo procesar correctamente el request. 
El Body del response es el siguiente, donde la propiedad errorCode debe contener el valor "ERRCD_OK" el cual indica que la configuración se pudo realizar de forma correcta.

```json
{
    "url": "URLAmbiente/v1/SiteSystem/sse/c14e1013-5acd-43d5-aad4-68679f295a39",
    "errorCode": "ERRCD_OK",
    "endpointType": "SSE"
}
```


### Site Data

<b>Relative URL:</b> URLAmbiente/v{{Version}}/SiteSystem/SSE/{{SiteSessionId}}/siteData </br>
<b>Method:</b> POST </br>
<b>Tipo de Configuración:</b> Obligatoria </br>
<b>Input:</b> application/json </br>
<b>Output:</b> application/json </br>
<b>Uso:</b> Permite configurar en la sesión creada en el MobileEvents, el sitio el cual está operando. Esto se realiza en la propiedad Id del objeto siteIDs. 

<b>Request Body:</b>
```json
{
     "name" : "IFSF/Conexxus Station",   
     "siteIDs" : [
             { "type":"SHIPTO", "id": "{{SiteCode}}" } 
     ],
     "addressLines" : [
       "Delta 1A, Building L’Aimant",   
       "Business Park Ijsseloord 2"
     ]
}
```

<b>Response Body:</b>
Se obtiene un HTTP Response 200 o 400 dependiendo si se pudo procesar correctamente el request. 
El Body del response es el siguiente, donde la propiedad error debe contener el valor "ERRCD_OK" el cual indica que la configuración se pudo realizar de forma correcta.

```json
{
    "timestamp": "2025-03-21T21:33:23.4991943+00:00",
    "result": "success",
    "error": "ERRCD_OK",
    "message": "Operation completed successfully"
}
```



### Products

<b>Relative URL:</b> URLAmbiente/v{{Version}}/SiteSystem/SSE/{{SiteSessionId}}/products </br>
<b>Method:</b> POST </br>
<b>Tipo de Configuración:</b> Obligatoria </br>
<b>Input:</b> application/json </br>
<b>Output:</b> application/json </br>
<b>Uso:</b> Permite configurar en la sesión creada en el MobileEvents, los productos con los cuales operará el sitio. Esto se realiza con el objeto fuelProducts. </br> </br>
<b>IMPORTANTE: la propiedad fuelPrice que se encuentra dentro del objeto producto que viaja en el array "fuelProducts" es de caracter obligatoria ya que de esta propiedad toma el valor el autorizador de flota para opear</b>

<b>Request Body:</b>
```json
{
   "fuelProducts":[
      {
         "productNo":"1",
         "productName":"Premium",
         "productCode":"CODE1",
         "prices":[
            {
               "fuelUnitPrice":{
                  "value":"20.00",
                  "currency":""
               },
               "priceTier":"cash",
               "modeNo":"1"
            },
            {
               "fuelUnitPrice":{
                  "value":"25.00",
                  "currency":""
               },
               "priceTier":"cash",
               "modeNo":"2"
            }
         ],
         "fuelPrice": {
            "value":"20.00",
            "currency":"USD"
         }
      },
      {
         "productNo":"2",
         "productName":"Diesel",
         "productCode":"CODE2",
         "prices":[
            {
               "fuelUnitPrice":{
                  "value":"30.00",
                  "currency":""
               },
               "priceTier":"cash",
               "modeNo":"1"
            },
            {
               "fuelUnitPrice":{
                  "value":"35.00",
                  "currency":""
               },
               "priceTier":"cash",
               "modeNo":"2"
            }
         ],
         "fuelPrice": {
            "value":"10.00",
            "currency":"USD"
         }
      }
   ]
}
```

<b>Response Body:</b>
Se obtiene un HTTP Response 200 o 400 dependiendo si se pudo procesar correctamente el request. 
El Body del response es el siguiente, donde la propiedad error debe contener el valor "ERRCD_OK" el cual indica que la configuración se pudo realizar de forma correcta.

```json
{
    "timestamp": "2025-03-21T21:33:23.4991943+00:00",
    "result": "success",
    "error": "ERRCD_OK",
    "message": "Operation completed successfully"
}
```


### Dispensers

<b>Relative URL:</b> URLAmbiente/v{{Version}}/SiteSystem/SSE/{{SiteSessionId}}/dsps </br>
<b>Method:</b> POST </br>
<b>Tipo de Configuración:</b> Obligatoria </br>
<b>Input:</b> application/json </br>
<b>Output:</b> application/json </br>
<b>Uso:</b> Permite configurar en la sesión creada en el MobileEvents, la lista de Dispensers con los que operará el sitio. Esto se realiza con el objeto dispensersConfiguration. 

<b>Request Body:</b>
```json
{
  "dispensersConfiguration": [
    {
      "dispenserID": "1",
      "fuelingPoints": [
        {
          "fuelingPointID": "1",
          "nozzles": [
            {
              "nozzleNo": "1",
              "productNo": "1",
              "tankNo1": "1"
            },
            {
              "nozzleNo": "2",
              "productNo": "2",
              "tankNo1": "2"
            },
            {
              "nozzleNo": "3",
              "productNo": "3",
              "tankNo1": "3"
            },
            {
              "nozzleNo": "4",
              "productNo": "4",
              "tankNo1": "4"
            }
          ]
        }
      ]
    },
    {
      "dispenserID": "2",
      "fuelingPoints": [
        {
          "fuelingPointID": "2",
          "nozzles": [
            {
              "nozzleNo": "1",
              "productNo": "1",
              "tankNo1": "1"
            },
            {
              "nozzleNo": "2",
              "productNo": "2",
              "tankNo1": "2"
            },
            {
              "nozzleNo": "3",
              "productNo": "3",
              "tankNo1": "3"
            },
            {
              "nozzleNo": "4",
              "productNo": "4",
              "tankNo1": "4"
            }
          ]
        }
      ]
    }
  ]
}
```

<b>Response Body:</b>
Se obtiene un HTTP Response 200 o 400 dependiendo si se pudo procesar correctamente el request. 
El Body del response es el siguiente, donde la propiedad error debe contener el valor "ERRCD_OK" el cual indica que la configuración se pudo realizar de forma correcta.

```json
{
    "timestamp": "2025-03-21T21:33:23.4991943+00:00",
    "result": "success",
    "error": "ERRCD_OK",
    "message": "Operation completed successfully"
}
```



### Modes

<b>Relative URL:</b> URLAmbiente/v{{Version}}/SiteSystem/SSE/{{SiteSessionId}}/modes </br>
<b>Method:</b> POST </br>
<b>Tipo de Configuración:</b> Opcional </br>
<b>Input:</b> application/json </br>
<b>Output:</b> application/json </br>
<b>Uso:</b> Permite configurar en la sesión creada en el MobileEvents, los modos de operación. Esto se realiza con el objeto fuelModes. 

<b>Request Body:</b>
```json
{
  "fuelModes":
      [
        {
          "modeNo": "1",
          "modeName": "FullServ"
        },
        {
          "modeNo": "2",
          "modeName": "SelfServ"
        }
      ]
}
```

<b>Response Body:</b>
Se obtiene un HTTP Response 200 o 400 dependiendo si se pudo procesar correctamente el request. 
El Body del response es el siguiente, donde la propiedad error debe contener el valor "ERRCD_OK" el cual indica que la configuración se pudo realizar de forma correcta.

```json
{
    "timestamp": "2025-03-21T21:33:23.4991943+00:00",
    "result": "success",
    "error": "ERRCD_OK",
    "message": "Operation completed successfully"
}
```



### Country Settings

<b>Relative URL:</b> URLAmbiente/v{{Version}}/SiteSystem/SSE/{{SiteSessionId}}/CountrySettings </br>
<b>Method:</b> POST </br>
<b>Tipo de Configuración:</b> Opcional </br>
<b>Input:</b> application/json </br>
<b>Output:</b> application/json </br>
<b>Uso:</b> Permite configurar en la sesión creada en el MobileEvents, los valores de unidades / lenguaje / código de país / moneda. Esto se realiza con el objeto countrySettings. 

<b>Request Body:</b>
```json
{
  "countrySettings":
      {
        "volumeUnit": "GLL",
        "countryCode": "US",
        "language": "eng",
        "localCurrencies":
          [
            "USD"
          ]
      } 
}
```

<b>Response Body:</b>
Se obtiene un HTTP Response 200 o 400 dependiendo si se pudo procesar correctamente el request. 
El Body del response es el siguiente, donde la propiedad error debe contener el valor "ERRCD_OK" el cual indica que la configuración se pudo realizar de forma correcta.

```json
{
    "timestamp": "2025-03-21T21:33:23.4991943+00:00",
    "result": "success",
    "error": "ERRCD_OK",
    "message": "Operation completed successfully"
}
```


## Mensajería Transaccional


### Flujo Transaccional

<div align="center">
  <img src="https://github.com/user-attachments/assets/4e47c24e-3d12-4cfa-9e7d-b6702c0ab355" alt="Diagrama de Secuencia de Operación">
</div>


### Mensajería del Host al SiteSystem

#### Descripción General SSE
A continuación se detallan todos los mensajes que el SiteSystem podrá recibir mediante el canal SSE (Server-Sent Events), mediante long-lived HTTP connection

#### FPReserveRequest

<b>Output:</b> application/json </br>
<b>Uso:</b> Mediante este evento el Host le notificará al SiteSystem que debe reservar una posición de carga. 
<b>Body:</b>
```json
{
  "id": "FPReserveRequest",
  "retry": 1,
  "event": "FPReserveRequest",
  "data": {
        "eventMessage": "fueling point reserve request event",
        "timestamp": "2009-11-20T17:30:50",
        "UMTI": "1af2f8ee-a656-45e6-8e9c-f2659f94be2f",
        "fuelingPointID": "1"
        }
}
```

<b>Definición de Campos:</b> </br>
<b>id:</b> Corresponde al tipo de mensaje que el servidor le esta notificando al SiteSystem</br>
<b>eventMessage:</b>  Descripción del tipo de mensaje.</br>
<b>timestamp:</b> fecha y hora de la solicitud</br>
<b>UMTI:</b> Id de la transacción en curso</br>
<b>fuelingPointID:</b> Posición que se desea reservar</br>


#### AuthorizeRequest

<b>Output:</b> application/json </br>
<b>Uso:</b> Mediante este evento el Host le notificará al SiteSystem que debe authorizar una posición de carga. Para esto el SiteSystem deberá obtener el detalle de la transacción notificada (UMTI) mediante una solicitud GET (Método trxs/{TransactionId}), a fin de obtener el detalle de la transacción y poder determinar el valor de la operación que se debe autorizar. 
<b>Body:</b>
```json
{
  "id": "authorizeRequest",
  "retry": 1,
  "event": "authorizeRequest",
  "data": {
        "eventMessage": "authorize request event",
        "timestamp": "2009-11-20T17:30:50",
        "UMTI": "1af2f8ee-a656-45e6-8e9c-f2659f94be2f"
        }
}
```

<b>Definición de Campos:</b> </br>
<b>id:</b> Corresponde al tipo de mensaje que el servidor le esta notificando al SiteSystem</br>
<b>eventMessage:</b>  Descripción del tipo de mensaje.</br>
<b>timestamp:</b> fecha y hora de la solicitud</br>
<b>UMTI:</b> Id de la transacción en curso</br>


#### FPReserveCancelRequest

<b>Output:</b> application/json </br>
<b>Uso:</b> Mediante este evento el Host le notificará al SiteSystem que posterior a la reserva de la posición de carga ocurrió un error y el flujo no puede avanzar. Por tal motivo el SiteSystem deberá liberar la posición de carga que se encontraba reservada.
<b>Body:</b>
```json
{
  "id": "FPReserveCancelRequest",
  "retry": 1,
  "event": "FPReserveCancelRequest",
  "data": {
        "eventMessage": "authorize request event",
        "timestamp": "2009-11-20T17:30:50",
        "UMTI": "1af2f8ee-a656-45e6-8e9c-f2659f94be2f",
        "fuelingPointID": "1"
        }
}
```

<b>Definición de Campos:</b> </br>
<b>id:</b> Corresponde al tipo de mensaje que el servidor le esta notificando al SiteSystem</br>
<b>eventMessage:</b>  Descripción del tipo de mensaje.</br>
<b>timestamp:</b> fecha y hora de la solicitud</br>
<b>UMTI:</b> Id de la transacción en curso</br>
<b>fuelingPointID:</b> Posición que se desea liberar</br>



### Mensajería del SiteSystem al Host

#### Descripción General
Esta mensajería es la que deberá implementar el SiteSystem para actuar en consecuencia a las operaciones que se llevan a cabo en base a los mensajes recibidos en el canal SSE. 

#### Reserve Notification (POST)

<b>Relative URL:</b> URLAmbiente/v{{Version}}/SiteSystem/trxs/{{TransactionId}}/FPs/{{FuelPointId}}/reserveNotification</br>
<b>Method:</b> POST </br>
<b>Input:</b> application/json </br>
<b>Output:</b> application/json </br>
<b>Uso:</b> Permite al SiteSystem notificar al Host que la reserva del FuelPoint fue correcta 

<b>Request Body:</b>
```json
{
    "timestamp": "2023-06-02T12:20:50.311Z",
    "result": "success",
    "error": "00000",
    "message": "THE FUELING POINT WAS RESERVED SUCCESSFULLY",
    "UMTI": "{{TransactionId}}",
    "TransactionStatus": "PUMPRESERVED",
    "FuelingPointId": "{{FuelPointId}}",
    "MerchantId": "0192-7509",
    "SiteId": {
        "Type": "SAP",
        "Id": "{{SiteCode}}"
        }
}
```

<b>Definición de Campos:</b> </br>
<b>result:</b> Corresponde al resultado de la operación. Para este caso solo puede ser success</br>
<b>message:</b>  Descripción del tipo de mensaje.</br>
<b>timestamp:</b> fecha y hora de la solicitud</br>
<b>UMTI:</b> Id de la transacción en curso</br>
<b>FuelingPointId:</b> Posición que se desea liberar</br>


<b>Response Body:</b>
Se obtiene un HTTP Response 200 o 400 dependiendo si se pudo procesar correctamente el request. 
El Body del response es el siguiente, donde la propiedad error debe contener el valor "ERRCD_OK" el cual indica que la configuración se pudo realizar de forma correcta.

```json
{
    "timestamp": "2025-03-21T21:33:23.4991943+00:00",
    "result": "success",
    "error": "ERRCD_OK",
    "message": "Operation completed successfully"
}
```


#### Reserve Notification (DELETE)

<b>Relative URL:</b> URLAmbiente/v{{Version}}/SiteSystem/trxs/{{TransactionId}}/FPs/{{FuelPointId}}/reserveNotification</br>
<b>Method:</b> DELETE </br>
<b>Input:</b> application/json </br>
<b>Output:</b> application/json </br>
<b>Uso:</b> Permite al SiteSystem notificar al Host que no pudo procesar la reserva del FuelPoint 

<b>Request Body:</b>
Vacío

<b>Response Body:</b>
Se obtiene un HTTP Response 200 o 400 dependiendo si se pudo procesar correctamente el request. 
El Body del response es el siguiente, donde la propiedad error debe contener el valor "ERRCD_OK" el cual indica que la configuración se pudo realizar de forma correcta.

```json
{
    "timestamp": "2025-03-21T21:33:23.4991943+00:00",
    "result": "success",
    "error": "ERRCD_OK",
    "message": "Operation completed successfully"
}
```


#### Transaction Info

<b>Relative URL:</b> URLAmbiente/v{{Version}}/SiteSystem/trxs/{{TransactionId}}</br>
<b>Method:</b> GET </br>
<b>Input:</b> application/json </br>
<b>Output:</b> application/json </br>
<b>Uso:</b> Permite al SiteSystem obtener el detalle de una transacción

<b>Request Body:</b>
Vacío


<b>Response Body:</b>
Se obtiene un HTTP Response 200 o 400 dependiendo si se pudo procesar correctamente el request. 
El SiteSystem podrá obtener el monto autorizado de la propiedad "value" que se encuentra dentro del objeto "finalAmount". "finalAmount" a su vez se encuentra dentro del objeto "paymentInfo".
El Body del response en el caso de obtener un 200, es el siguiente:

```json
{
    "trxInfo": {
        "timestamp": "2025-01-30T17:48:53.3941524+00:00",
        "result": "success",
        "error": "ERRCD_OK",
        "message": "Complete",
        "UMTI": "7a74d97d-d7e0-41d7-871a-bfe89a30babb",
        "transactionStatus": "authorized",
        "fuelingPointID": "1",
        "merchantID": "",
        "siteID": {
            "type": "",
            "id": "15241"
        }
    },
    "paymentInfo": {
        "paymentMethod": null,
        "finalAmount": {
            "value": "3.00",
            "currency": null
        },
        "hostAuthNumber": "004745154",
        "cardType": null,
        "cardCircuit": null
    },
    "fuelingInfo": {
        "fuelProducts": [
            {
                "productNo": null,
                "productName": null,
                "productCode": "1",
                "prices": null,
                "fuelPrice": {
                    "value": "3.00",
                    "currency": "USD"
                },
                "fuelUnitOfMeasurement": null,
                "gradeAllowed": "yes",
                "merchandiseCode": null,
                "taxId": null
            }
        ],
        "fuelingPointID": "1",
        "fuelAmount": {
            "value": "3.00",
            "currency": "USD"
        },
        "quantity": {
            "value": "1",
            "uom": null
        },
        "serviceLevel": "full",
        "modeNo": "1",
        "priceTier": "credit"
    },
    "customerPreferences": {
        "receipt": null
    }
}
```



#### Authorization Notification

<b>Relative URL:</b> URLAmbiente/v{{Version}}/SiteSystem/trxs/{{TransactionId}}/authorizationNotification</br>
<b>Method:</b> POST </br>
<b>Input:</b> application/json </br>
<b>Output:</b> application/json </br>
<b>Uso:</b> Permite al SiteSystem notificar al Host que la autorización del FuelPoint fue correcta o incorrecta. 
Para esto deberá modificar el campo "result". 
1. En el caso de que el valor notificado sea "success", el host interpretará que la autorización fue correcta.
2. En el caso de que el valor notificado sea "fail", el host interpretará que la autorización no pudo ser efectuada correctamente por el SiteSystem.


<b>Request Body:</b>
```json
{ 
    "timestamp": "2023-06-02T15:36:50.311Z", 
    "result": "success", 
    "error": "00000", 
    "message": "the fueling point was approved successfully", 
    "UMTI": "{{TransactionId}}", 
    "transactionStatus": "authorized", 
    "fuelingPointID": "{{FuelPointId}}", 
    "merchantID": "0192-7509", 
    "siteID": 
        { 
            "type": "SAP", 
            "id": "{{SiteCode}}" 
        } 
}
```

<b>Definición de Campos:</b> </br>
<b>result:</b> Corresponde al resultado de la operación. Para este caso, puede ser success o fail</br>
<b>message:</b>  Descripción del tipo de mensaje.</br>
<b>timestamp:</b> fecha y hora de la solicitud</br>
<b>UMTI:</b> Id de la transacción en curso</br>
<b>FuelingPointId:</b> Posición que se desea liberar</br>


<b>Response Body:</b>
Se obtiene un HTTP Response 200 o 400 dependiendo si se pudo procesar correctamente el request. 
El Body del response es el siguiente, donde la propiedad error debe contener el valor "ERRCD_OK" el cual indica que la configuración se pudo realizar de forma correcta.

```json
{
    "timestamp": "2025-03-21T21:33:23.4991943+00:00",
    "result": "success",
    "error": "ERRCD_OK",
    "message": "Operation completed successfully"
}
```


#### Begin Fueling Notification

<b>Relative URL:</b> URLAmbiente/v{{Version}}/SiteSystem/trxs/{{TransactionId}}/beginFuelingNotification</br>
<b>Method:</b> POST </br>
<b>Input:</b> application/json </br>
<b>Output:</b> application/json </br>
<b>Uso:</b> Permite al SiteSystem notificar al Host que el despacho pudo comenzar o que existió algún inconveniente. 
Para esto deberá modificar el campo "result". 
1. En el caso de que el valor notificado sea "success", el host interpretará que la autorización fue correcta.
2. En el caso de que el valor notificado sea "fail", el host interpretará que la autorización no pudo ser efectuada correctamente por el SiteSystem.


<b>Request Body:</b>
```json
{
    "timestamp": "2023-06-02T13:36:50.311Z",
    "result": "success",
    "error": "00000",
    "message": "the fueling point is fueling",
    "UMTI": "{{TransactionId}}",
    "transactionStatus": "beginFueling",
    "fuelingPointID": "{{FuelPointId}}",
    "fuelingPointState": "FUELING",
    "merchantID": "0192-7509",
    "siteID": {
        "type": "SAP",
        "id": "{{SiteCode}}"
        }
}
```

<b>Definición de Campos:</b> </br>
<b>result:</b> Corresponde al resultado de la operación. Para este caso, puede ser success o fail</br>
<b>message:</b>  Descripción del tipo de mensaje.</br>
<b>timestamp:</b> fecha y hora de la solicitud</br>
<b>UMTI:</b> Id de la transacción en curso</br>
<b>FuelingPointId:</b> Posición que se desea liberar</br>


<b>Response Body:</b>
Se obtiene un HTTP Response 200 o 400 dependiendo si se pudo procesar correctamente el request. 
El Body del response es el siguiente, donde la propiedad error debe contener el valor "ERRCD_OK" el cual indica que la configuración se pudo realizar de forma correcta.

```json
{
    "timestamp": "2025-03-21T21:33:23.4991943+00:00",
    "result": "success",
    "error": "ERRCD_OK",
    "message": "Operation completed successfully"
}
```


#### Finalize Transaction Notification

<b>Relative URL:</b> URLAmbiente/v{{Version}}/SiteSystem/trxs/{{TransactionId}}/finalizeTrxNotification</br>
<b>Method:</b> POST </br>
<b>Input:</b> application/json </br>
<b>Output:</b> application/json </br>
<b>Uso:</b> Permite al SiteSystem notificar al Host que el despacho pudo comenzar o que existió algún inconveniente. 
Para esto deberá modificar el campo "result". 
1. En el caso de que el valor notificado sea "success", el host interpretará que la autorización fue correcta.
2. En el caso de que el valor notificado sea "fail", el host interpretará que la autorización no pudo ser efectuada correctamente por el SiteSystem.


<b>Request Body:</b>
```json
{
    "TrxInfo": { 
        "timestamp": "2023-06-02T15:36:50.311Z", 
        "result": "success", 
        "error": "00000", 
        "message": "the fueling point was approved successfully", 
        "UMTI": "{{TransactionId}}", 
        "transactionStatus": "finalized", 
        "fuelingPointID": "{{FuelPointId}}", 
        "merchantID": "0192-7509", 
        "siteID": 
            { 
                "type": "SAP", 
                "id": "1234" 
            } 
    },
    "paymentInfo": {
        "cardCircuit": "MCB",
        "paymentMethod": "credit",
        "finalAmount": {
            "value": "1",
            "currency": null
        },
        "hostAuthNumber": "312350",
        "cardType": "MASTERCARD"
        },
    "fuelingInfo": {
        "fuelProducts": [{
        "productNo": "{{FuelCode}}",
        "productName": "{{FuelCode}}",
        "productCode": "{{FuelCode}}",
        "fuelPrice": {"value":"{{fuelPrice}}"},
        "fuelUnitOfMeasurement": "GLL",
        "gradeAllowed": "true"
      }],
        "fuelingPointID": "{{fuelingPointId}}",
        "fuelAmount": {
            "value": "{{Amount}}",
            "currency": null
        },
        "quantity": {
            "value": "{{Quantity}}",
            "uom": "l"
        },
        "serviceLevel": "full",
        "modeNo": "1"
        },
    "receiptInfo": [
    "WELCOME",
    "IBERA 2141 CABA",
    "ORIONTECH S.A.",
    "CUIT 30-12331129-2",
    "DATE 09/07/16  12:29",
    "TRAN# 9030038",
    "FP# 02",
    "SERVICE LEVEL: FullServ",
    "PRODUCT: PLUS",
    "GALLONS: 0.926",
    "PRICE/G: $ 2.159",
    "FUEL SALE  $ 2.00",
    "THANK YOU",
    "HAVE A NICE DAY"
    ]
}
```

<b>Definición de Campos:</b> </br>
<b>result:</b> Corresponde al resultado de la operación. Para este caso, puede ser success o fail</br>
<b>message:</b>  Descripción del tipo de mensaje.</br>
<b>timestamp:</b> fecha y hora de la solicitud</br>
<b>UMTI:</b> Id de la transacción en curso</br>
<b>FuelingPointId:</b> Posición de carga</br>
<b>FuelCode:</b> Corresponde al Código de producto despachado</br>
<b>productName:</b>  Corresponde al nombre de producto despachado</br>
<b>productCode:</b> Corresponde al Código de producto despachado</br>
<b>Amount:</b> Es el monto despachado</br>
<b>Quantity:</b> Es el volumen despachado</br>
<b>fuelPrice:</b> Es el precio del combustible despachado</br>

<b>Response Body:</b>
Se obtiene un HTTP Response 200 o 400 dependiendo si se pudo procesar correctamente el request. 
El Body del response es el siguiente, donde la propiedad error debe contener el valor "ERRCD_OK" el cual indica que la configuración se pudo realizar de forma correcta.

```json
{
    "timestamp": "2025-03-21T21:33:23.4991943+00:00",
    "result": "success",
    "error": "ERRCD_OK",
    "message": "Operation completed successfully"
}
```



## Colección Postman

Link de Descarga

Nota: Para utilizar la colección se debe solicitar a Ationet que envíe y configure:
URL del ambiente
Usuario
Password
Sitio


## Ejemplo en C#

Link de Descarga

Nota: Para utilizar esta solución se debe solicitar a Ationet que envíe y configure:
URL del ambiente
Usuario
Password
Sitio
