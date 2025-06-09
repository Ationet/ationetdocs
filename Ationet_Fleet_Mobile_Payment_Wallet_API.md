![ationetlogo](Content/Images/ATIOnetLogo_250x70.png)
# Ationet Fleet Mobile Payment - Wallet Implementation #

|Información de Documento||
|--- |--- |
|Archivo:|ATIONet - Fleet Mobile Payment Wallet Implementation|
|Doc Version:|1.0|
|Fecha:|06-06-2025|
|Autor:|Alexis E. Yañez|

|Control de Cambios |||
|--- |--- |--- |
|Ver.|Fecha|Cambios|
|1.0|06-06-2025|Initial version.|

## Contenido ##
- [Introducción](#Introducción)
- [Mensajería Transaccional](#mensajería-transaccional)
  - [Pre Paid](#prepaid)
     - [Authorize](#authorize)
     - [Get Transaction](#transaction-data)
     - [Notification](#notification-prepaid)
  - [Post Paid](#postpaid)
     - [Payment Request](#payment-request)
     - [Get Transaction](#transaction-data)
     - [Notification](#notification-prepaid)
  - [Endpoint Wallet Payment Object](#endpoint-wallet-payment-object)


## Introducción
Este documento describe la operación que debe implementar una billetera que se quiere integrar con el servicio de Fleet Mobile Payment de Ationet.


## Mensajería Transaccional
A continuación se describe las operaciones que debe implementar la billetera para integrarse con el servicio de Ationet Fleet Mobile Payment.
Como primer paso, se debe registar una nueva billetera en el ambiente de Ationet con el fin de obtener el WalletId el cual se utilizará para confeccionar el request.
Esta nueva billetera deberá proporcionar un Endpoint donde ir a buscar el objeto pago con el fin de validar la notificación enviada.


### Prepaid

#### Authorize 

<b>Relative URL:</b> URLAmbiente/v{{Version}}/MPA/prepaid/{{PosId}}/{{WalletId}}/Authorize</br>
<b>Method:</b> POST </br>
<b>Input:</b> application/json </br>
<b>Output:</b> application/json </br>
<b>Uso:</b> Permite generar una transacción que será procesada por el flujo PrePago 
<b>Request Body:</b>
Vacío
<b>Response Body:</b>
Se obtiene un HTTP Response 200 o 400 dependiendo si se pudo procesar correctamente el request. 
En el caso de obtener un HTTP Code 200, se obtiene:
1) El TransactionId creado.
2) La información necesaria para procesar la operación: selección de producto, URL de notificación de pago, fecha de creación de la transacción, flag que identifica si el request fue procesado correctamente (IsSuccess).

```json
{
    "IsSuccess": boolean,
    "ResponseCode": string,
    "ResponseMessage": string,
    "TransactionId": guid,
    "NotificationUrl": string,
    "DateCreated": DateTime,
    "Nozzles": [
          {
            "nozzleNo": string,
            "productNo": string,
            "tankNo1": string,
            "prices": [
                {
                  "fuelUnitPrice": {
                      "value": string,
                      "currency": string
                  },
                  "priceTier": string,
                  "modeNo": string
                }
            ],
            "productCode": string
          }
    ]
}
```



#### Transaction Data
<b>Relative URL:</b> URLAmbiente/v{{Version}}/MPA/prepaid/Transaction/{transactionId}</br>
<b>Method:</b> GET </br>
<b>Input:</b> application/json </br>
<b>Output:</b> application/json </br>
<b>Uso:</b> Permite obtener los datos de una transacción generada por el Authorize
<b>Request Body:</b>
Vacío
<b>Response Body:</b>
```json
{
  "id": guid,
  "siteCode": string,
  "primaryTrack": string,
  "odometer": long,
  "terminalIdentification": string,
  "transactionSequenceNumber": long,
  "state_Name": string,
  "state_Id": int,
  "paymentProcessorReferenceId": string,
  "paymentProcessorMessage": string,
  "siteSystemMessage": string,
  "fuelPointNumber": int,
  "paymentMethod": string,
  "requestedAmount": decimal,
  "authorizedAmount": decimal,
  "dispatchedAmount": decimal,
  "dispatchedQuantity": decimal?,
  "productCode": string,
  "productDescription": string,
  "productUnitPrice": decimal?,
  "unitMeasure": string,
  "createDateTime": Datetime,
  "updateDateTime": Datetime,
  "idDispatch": guid
}
```

#### Notification Postpaid
<b>Relative URL:</b> URLAmbiente/v{{Version}}/MPA/prepaid/Notifications/{{TransactionId}}?topic={{topic}}&id={{paymentId}}</br>
<b>Method:</b> GET </br>
<b>Input:</b> application/json </br>
<b>Output:</b> application/json </br>
<b>Uso:</b> Permite a la billetera enviar la notificación de pago correspondiente a una transacción. El PaymentId debe correspoder al ID de pago que Ationet utilizará para obtener el pago del EndPoint que proporcione la billetera para validar el pago enviado. 
<b>Request Body:</b>
Vacío
<b>Response Body:</b>
Vacío


### Postpaid

#### Paymnet Request 

<b>Relative URL:</b> URLAmbiente/v{{Version}}/MPA/postpaid/{{PosId}}/{{WalletId}}/PaymentRequest</br>
<b>Method:</b> POST </br>
<b>Input:</b> application/json </br>
<b>Output:</b> application/json </br>
<b>Uso:</b> Permite generar una transacción que será procesada por el flujo Postpago
<b>Request Body:</b>
Vacío
<b>Response Body:</b>
Se obtiene un HTTP Response 200 o 400 dependiendo si se pudo procesar correctamente el request. 
En el caso de obtener un HTTP Code 200, se obtiene:
1) El TransactionId creado.
2) Flag que identifica si el request fue procesado correctamente (IsSuccess).

```json
{
    "IsSuccess": boolean,
    "ResponseCode": string,
    "ResponseMessage": string,
    "TransactionId": guid
}
```



#### Transaction Data
<b>Relative URL:</b> URLAmbiente/v{{Version}}/MPA/postpaid/Transaction/{transactionId}</br>
<b>Method:</b> GET </br>
<b>Input:</b> application/json </br>
<b>Output:</b> application/json </br>
<b>Uso:</b> Permite obtener los datos de una transacción generada por el Authorize
<b>Request Body:</b>
Vacío
<b>Response Body:</b>
```json
{
  "id": guid,
  "siteCode": string,
  "primaryTrack": string,
  "odometer": long,
  "terminalIdentification": string,
  "transactionSequenceNumber": long,
  "state_Name": string,
  "state_Id": int,
  "paymentProcessorReferenceId": string,
  "paymentProcessorMessage": string,
  "siteSystemMessage": string,
  "fuelPointNumber": int,
  "paymentMethod": string,
  "requestedAmount": decimal,
  "authorizedAmount": decimal,
  "dispatchedAmount": decimal,
  "dispatchedQuantity": decimal?,
  "productCode": string,
  "productDescription": string,
  "productUnitPrice": decimal?,
  "unitMeasure": string,
  "createDateTime": Datetime,
  "updateDateTime": Datetime,
  "idDispatch": guid
}
```

#### Notification Postpaid
<b>Relative URL:</b> URLAmbiente/v{{Version}}/MPA/postpaid/Notifications/{{TransactionId}}?topic={{topic}}&id={{paymentId}}</br>
<b>Method:</b> GET </br>
<b>Input:</b> application/json </br>
<b>Output:</b> application/json </br>
<b>Uso:</b> Permite a la billetera enviar la notificación de pago correspondiente a una transacción. El PaymentId debe correspoder al ID de pago que Ationet utilizará para obtener el pago del EndPoint que proporcione la billetera para validar el pago enviado. 
<b>Request Body:</b>
Vacío
<b>Response Body:</b>
Vacío



###Endpoint Wallet Payment Object
<b>Relative URL:</b> URLWallet/{{PaymentId}}?access_token={{Access_token}}</br>
<b>Method:</b> GET </br>
<b>Input:</b> application/json </br>
<b>Output:</b> application/json </br>
<b>Uso:</b> Es un Endpoint expuesto por la billetera el cual permite obtener el objeto pago. Este endpoint tiene en su query string el valor del payment id enviado en la notificación de pago y un Access_Token que permite autenticar la petición hacia la billetera de manera de que Ationet pueda obtener el objeto pago.
El Status del objeto pago debe ser approved en caso de pago exitoso. 
<b>Request Body:</b>
Vacío
<b>Response Body:</b>
```json
{
  "id": long?,
  "externalReference": string,
  "statementDescriptor": string,
  "status": string,
  "currencyId": string,
  "dateCreated": DateTime?,
  "authCode": string,
  "transactionAmount": string,
  "collectorId": int?,
  "description": string,
  "paymentMethodId": string,
  "paymentTypeId": string,
  "product": {
        "code": null,
        "productNo": null
      }
}
```
