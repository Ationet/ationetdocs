![ationetlogo](Content/Images/ATIOnetLogo_250x70.png)
# ATIONet - Dynamic QR Code Payments #

|Document Information||
|--- |--- |
|File:|ATIONet - Dynamic QR Code Payments|
|Doc Version:|1.0|
|Release Date:|26, August 2021|
|Author:|ATIONet LLC|

|Change Log|||
|--- |--- |--- |
|Ver.|Date|Change Summary|
|1.0|26/August/2021|Initial version.|

## Contents ##

- [Visión general](#Visión-general)
	- [Introduction](#Introduccion)
	- [Descripcion general del codigo QR Dinámico](#Descripcion-general-del-codigo-QR-dinamico)
- [Secuencia de pagos con código QR](#Secuencia-de-pagos-con-código-QR)
- [Implementación de pagos con códido QR dinámico](#Implementación-de-pagos-con-código-QR-dinámico)	
	- [Introducción](#Introducción)
	- [PASO 1 Obtener sus claves de autenticación(Pendiente/En desarrollo)](#PASO-1-Obtener-sus-claves-de-autenticación)
	- [PASO 2 Crear código QR dinámico](#PASO-2-Crear-código-QR-dinámico)
	- [PASO 3 Confirmar el estado de la Transacción](#PASO-3-Confirmar-el-estado-de-la-Transacción)
	- [PASO 4 El cliente escanea el código QR dinámico](#PASO-4-El-cliente-escanea-el-código-QR-dinámico)
	- [Lista de verificación de integración](#Lista-de-verificación-de-integración)
- [Documentación de API](#Documentación-de-API)
	 - [Método obtener Venta](#Método-obtener-Venta)
		- [Descripción](#Descripción)
		- [Formato de solicitud](#Formato-de-solicitud)
		- [Formato de respuesta](#Formato-de-respuesta)
		- [Solicitud de ejemplo del metodo Obtener una-venta](#Solicitud-de-ejemplo-del-metodo-Obtener-una-venta)
	- [Metodo Venta](#Metodo-Venta)
		- [Descripción](#Descripción)
		- [Formato de solicitud](#Formato-de-solicitud)
		- [Formato de respuesta](#Formato-de-respuesta)
		- [Solicitud de ejemplo del metodo venta](#Solicitud-de-ejemplo-del-metodo-venta)
- [Manejo de errores](#Manejo-de-errores)
- [Mensajes de ejemplo](#Mensajes-de-ejemplo)
	- [Ejemplo Obtener una venta](#Ejemplo-Obtener-una-venta)
	- [Ejemplo método venta](#Ejemplo-método-venta)


## Visión general

![ationetTR](Content/Images/DynamicQRPayments/schemaDarkLight.png)

### Introduccion

Ationet fleet Mobile payments - Dynamic QR permite generar el código QR dinámico desde su POS / Sistema de facturación para un pedido / factura específico y debe pasar la información específica del pedido, como el Dispatch ID, el monto del pedido, etc., mientras se genera el código. El cliente puede escanear este QR para realizar un pago y el Backend del POS puede verificar el estado de la transacción utilizando el ID de envío.

``` 
Nota: Se requiere una pantalla orientada al cliente, que le mostrará el QR generado dinámicamente para poder
escanearlo y generar la venta.

```

### Descripcion general del codigo QR dinamico

<ol>
	<li>El cliente elige los productos / servicios en una tienda y muestra la intención de pago usando la aplicación Ationet Driver.</li>
	<li>El cajero crea un pedido con el monto de la factura y un Dispatch ID único en el sistema POS.</li>
	<li>El servidor backend de POS crea un código QR y se lo muestra al cliente en la pantalla de cara al consumidor.</li>
	<li>El cliente escanea el codigo QR usando Ationet Driver App.</li>
	<li>El servidor de back-end de POS comienza a sondear automáticamente el estado de la transacción cada 8 veces / minuto utilizando el Dispatch ID.</li>
</ol>



![ationetTR](Content/Images/DynamicQRPayments/demoQR.gif)

## Secuencia de pagos con código QR

![ationetTR](Content/Images/DynamicQRPayments/seq_darklight.svg)

## Implementación de pagos con código QR dinámico

### Introducción

La sección describe los pasos de integración necesarios para integrar los pagos con código QR dinámico de ATIONet con el punto de venta de facturación para aceptar pagos sin contacto de su cliente mediante el pago de la aplicación Ationet Driver.

### PASO 1 Obtener sus claves de autenticación
```
Importante: Pendiente/En desarrollo. No tener en cuenta este paso.
```
<ul>
	<li>Clave de backend de POS: una clave secreta única que se utiliza para asegurar el cifrado de cada solicitud. Esto debe mantenerse en el lado del servidor y no debe compartirse con nadie.</li>
</ul>

```
Nota: Nunca comparta la clave secreta de backend de su POS con nadie.
```


### PASO 2 Crear código QR dinámico

El Backend de POS solo codifica la información mínima de venta en QR, es la que proviene del controlador del sitio (Site controller) al generar una venta. El resto de la información de la trama se completa con el Backend del POS. La siguiente tabla describe cada campo en la tabla, su descripción y su origen.

```
Importante: La trama debe estar en formato JSON. La imagen del código QR debe ser de tipo texto libre.

```

<table>
	<thead>
		<tr valign="center">
			<th rowspan="2"  align="left">
				Nombre
			</th>
			<th rowspan="2" align="center">
				Tipo
			</th>
			<th rowspan="2" align="left">
				Origen
			</th>
			<th rowspan="8" align="left">
				Descripción
			</th>
		</tr>
	</thead>
	<tbody>
		<tr valign="top">
			<td>
				<p align="left">IDDispatch</p>
			</td>
			<td>
				<p align="center">(string) Guid</p>
			</td>
			<td>
			 	<p align="center">Site controller or POS Backend</p>
			 </td>
			<td>
				<p>XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX</p>
			</td>
		 </tr>
		 <tr valign="top">
			<td>
				<p align="left">PumpNumber</p>
			</td>
			<td>
				<p align="center">string</p>
			</td>
			<td>
			 	<p align="center">Site controller</p>
			 </td>
			<td>
				<p>“00”-“99”</p>
			</td>
		 </tr>
		 <tr valign="top">
			<td>
				<p align="left">TransactionSequenceNumber</p>
			</td>
			<td>
				<p align="center">integer</p>
			</td>
			<td>
			 	<p align="center">Site controller</p>
			 </td>
			<td>
				<p>Consulte Número de secuencia de transacción en la sección <a href="AN-Native_Transaction_Protocol-Spec.md#transaction-sequence-number">Descripción del campo.</a></p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
				<p align="left">LocalTransactionDate</p>
			</td>
			<td>
				<p align="center">integer</p>
			</td>
			<td>
			 	<p align="center">Site controller</p>
			 </td>
			<td>
				<p>Fecha local de la transacción: aaaammdd</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
				<p align="left">LocalTransactionTime</p>
			</td>
			<td>
				<p align="center">integer</p>
			</td>
			<td>
			 	<p align="center">Site controller</p>
			 </td>
			<td>
				<p>Hora local de la transacción: hhmmss</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
				<p align="left">TerminalIdentification</p>
			</td>
			<td>
				<p align="center">string</p>
			</td>
			<td>
			 	<p align="center">Site controller/POS IdentificationAtionet</p>
			 </td>
			<td>
				<p>Debe solicitarse a ATIONet</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
				<p align="left">TransactionAmount</p>
			</td>
			<td>
				<p align="center">double</p>
			</td>
			<td>
			 	<p align="center">Site controller</p>
			 </td>
			<td>
				<p>xxxxxxx.xx</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
				<p align="left">ProductCode</p>
			</td>
			<td>
				<p align="center">string</p>
			</td>
			<td>
			 	<p align="center">Site controller</p>
			 </td>
			<td>
				<p>“0”-“9999”</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
				<p align="left">ProductUnitPrice</p>
			</td>
			<td>
				<p align="center">double</p>
			</td>
			<td>
			 	<p align="center">Site controller</p>
			 </td>
			<td>
				<p>xxx.xx</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
				<p align="left">ProductAmount</p>
			</td>
			<td>
				<p align="center">double</p>
			</td>
			<td>
			 	<p align="center">Site controller</p>
			 </td>
			<td>
				<p>xxxxxxx.xx</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
				<p align="left">ProductQuantity</p>
			</td>
			<td>
				<p align="center">double</p>
			</td>
			<td>
			 	<p align="center">Site controller</p>
			 </td>
			<td>
				<p>xxxxxxx.xx</p>
			</td>
		 </tr>
		</tbody>
</table>

### Ejemplos

#### Ejemplo de Trama

```
Ejemplo completo de una de trama en formato JSON:

{
    "IDDispatch": "dc152309-6b50-45cc-939c-a43d69ec817a",
    "PumpNumber": "1",
    "TransactionSequenceNumber": 808,
    "LocalTransactionDate": 20210812, 
    "LocalTransactionTime": 113152, 
    "TerminalIdentification": "S2G321",
    "TransactionAmount": 99,
    "ProductCode": "1",
    "ProductUnitPrice": 1,
    "ProductAmount": 99,
    "ProductQuantity": 99
}
	
```
#### Ejemplo de imagen QR

![ationetTR](Content/Images/DynamicQRPayments/miniQr3.png)

### PASO 3 Confirmar el estado de la Transacción

Cuando se genera el código QR para una Transacción específica, el backend del POS obtiene el estado de la transacción con un proceso de sondeo mediante la [Api de estado de una Transaccion](#Método-obtener-Venta).

```
Sondeo : Configure un proceso de sondeo después de intervalos regulares utilizando la API de estado de transacción.
Para obtener los mejores resultados de una consulta de estado, debe verificar el estado 8 veces por minuto.

```

### PASO 4 El cliente escanea el código QR dinámico

Cuando se genera el código QR para una transacción específica, el cliente escanea ese código QR y paga mediante la aplicación Ationet Driver. Se notifica al cliente sobre el estado del pago en su aplicación Ationet Driver después de completar con éxito el pago. Si desea implementar una nueva aplicación de cliente, puede verificar la especificación de [API Crear venta](#Metodo-Venta).


```
Nota: Los clientes no pueden cambiar el monto de la transacción en su aplicación al escanear el código QR del pedido en particular.
```


### Lista de verificación de integración

Una vez finalizada la integración en su entorno de ensayo, es obligatorio probar la integración antes de pasar a un entorno en producción. Los siguientes puntos deben tenerse en cuenta durante el flujo integración:

<ol>
   <li>El estado de la Transacción debe verificarse a través de la API de estado de la transacción en el flujo de pago.</li>	
   <li>El Dispacht ID enviado a to ATIONet dee ser único.</li>	
   <li>La cantidad no debe contener más de 2 puntos decimales, comas o caracteres especiales.</li>	 
   <li>El parámetro Dispatch ID es obligatorio para crear QR.</li>	
</ol>

## Documentación de API 

*URL:  ationetmobilepayment-appshost-test.azurewebsites.net* </br>

### Método obtener Venta

#### Descripción

Devuelve la informacion de una venta.

#### Formato de solicitud

*URL: /api/ContactlessPayment/GetSale* </br>
*Method: POST* </br>

```
Body {"IDDispatch": "string"}
```

#### Formato de respuesta
Header:
```
Content-Type: application/json; charset=utf-8
content-encoding: gzip 
```
```
body [

    {
        "TransactionId": "string",
        "SubscriberCode": "string",
        "TransactionSequenceNumber": "string",
        "AuthorizationCode": "string",
        "ResponseCode": "string",
        "ResponseMessage": "string",
        "Status": 3,
        "Mode": 0,
        "StatusDescription": "string",
        "HostDateTime": "string",
        "SubscriberDateTime": "string",
        "SubscriberTimeZone": "string",
        "SiteDateTime": "string",
        "SiteTimeZone": "string",
        "DateTime": "string",
        "MerchantCode": "string",
        "MerchantContractCode": "string",
        "MerchantName": "string",
        "MerchantCustomField0": null,
        "MerchantCustomField1": null,
        "MerchantCustomField2": null,
        "MerchantCustomField3": null,
        "SiteCode": "string",
        "SiteName": "string",
        "SiteShortName": "string",
        "TerminalCode": "string",
        "TerminalType": "string",
        "TerminalId": "string",
        "TerminalTypeId": "string",
        "SubAccountId": "string",
        "SecondarySubAccountId": null,
        "AccountTypeDescription": "string",
        "VehicleCode": "string",
        "DriverCode": null,
        "TransactionNetAmount": null,
        "ProductUnitPriceRequested": double,
        "ProductVolumeRequested": double,
        "ProductAmountRequested": double,
        "TransactionAmountRequested": double,
        "ProductUnitPriceAuthorized": double,
        "ProductVolumeAuthorized": double,
        "ProductAmountAuthorized": double,
        "TransactionAmountAuthorized": double,
        "ProductUnitPriceDispensed": double,
        "ProductVolumeDispensed": double,
        "ProductAmountDispensed": double,
        "ProductNetAmountDispensed": null,
        "TransactionAmountDispensed": double,
        "ProductUnitPriceCompany": double,
        "ProductUnitPriceMerchant": double,
        "ProductAmountCompany": double,
        "ProductAmountMerchant": double,
        "TransactionAmountCompany": double,
        "TransactionAmountMerchant": double,
        "MeasurementUnitCode": null,
        "CurrencyCode": "string",
        "FuelCode": "string",
        "FuelMasterCode": "string",
        "FuelMasterDescription": "string",
        "InvoiceNumber": null,
        "BatchNumber": null,
        "ShiftNumber": null,
        "PumpNumber": "string",
        "EntryMethod": "string",
        "CompanyCode": "string",
        "CompanyName": "string",
        "CompanyCustomField0": null,
        "CompanyCustomField1": null,
        "CompanyCustomField2": null,
        "CompanyCustomField3": null,
        "CompaniesGroupCode": "",
        "ClassificationLabel1": "string",
        "ClassificationLabel2": "string",
        "ClassificationLabel3": "string",
        "ClassificationLabel4": "string",
        "ContractCode": "string",
        "CompanyContractClassificationValue1": "string",
        "CompanyContractClassificationValue2": "string",
        "CompanyContractClassificationValue3": "string",
        "CompanyContractClassificationValue4": "string",
        "CompanyContractCustomField0": null,
        "CompanyContractCustomField1": null,
        "CompanyContractCustomField2": null,
        "CompanyContractCustomField3": null,
        "SubContractCode": "string",
        "PrimaryIdentificationTrack": "string",
        "SecondaryIdentificationTrack": null,
        "PrimaryIdentificationPAN": "string",
        "SecondaryIdentificationPAN": null,
        "PrimaryIdentificationLabel": "string",
        "SecondaryIdentificationLabel": null,
        "PrimaryIdentificationModelDescription": "string",
        "SecondaryIdentificationModelDescription": null,
        "FleetCode": "string",
        "FleetName": "string",
        "VehiclePlate": "string",
        "VehicleClassDescription": null,
        "VehicleClassificationValue1": null,
        "VehicleClassificationValue2": null,
        "VehicleClassificationValue3": null,
        "VehicleClassificationValue4": null,
        "DriverName": null,
        "DriverClassificationValue1": null,
        "DriverClassificationValue2": null,
        "DriverClassificationValue3": null,
        "DriverClassificationValue4": null,
        "CustomerData": {},
        "FastTrackData": {},
        "TaxesData": {},
        "FeesData": [
            {
                "Name": "string",
                "Value": double,
                "Id": "string"
            }
        ],
        "CompanyTaxpayerId": "string",
        "ApplicationCode": null,
        "DisputeDate": null,
        "Reason": null,
        "State": null,
        "DisputeCommentCompany": null,
        "ResolvedDate": null,
        "DisputeResolveNetworkComment": null,
        "Odometer": null,
        "SiteCountryId": "string",
        "SiteCountry": "string",
        "SiteAddress": "string",
        "SiteStateId": "string",
        "SiteState": "string",
        "SiteCity": "string",
        "SiteZipCode": null,
        "SiteClassificationValue1": "string",
        "SiteClassificationValue2": null,
        "SiteClassificationValue3": null,
        "SiteClassificationValue4": null,
        "SiteCustomField0": null,
        "SiteCustomField1": null,
        "SiteCustomField2": null,
        "SiteCustomField3": null,
        "DriverFirstName": null,
        "DriverLastName": null,
        "GPSVirtualOdometer": null,
        "GPSDistance": null,
        "GPSAddress": null,
        "GPSComment": null,
        "DriverCustomField0": null,
        "DriverCustomField1": null,
        "DriverCustomField2": null,
        "DriverCustomField3": null,
        "VehicleCustomField0": null,
        "VehicleCustomField1": null,
        "VehicleCustomField2": null,
        "VehicleCustomField3": null,
        "IdProgram": "string",
        "ProgramDescription": "string",
        "LatitudeStart": null,
        "LongitudeStart": null,
        "AltitudeStart": null,
        "LatitudeEnd": null,
        "LongitudeEnd": null,
        "AltitudeEnd": null,
        "ContingencyReason": null,
        "AuthorizationType": 0,
        "AttendantCode": null,
        "PumpSide": null,
        "VehicleBrand": "string",
        "VehicleModel": null,
        "Subsidized": null,
        "SiteCountryCode": "string",
        "CompanyContractCustomInterface0": bool,
        "CompanyContractCustomInterface1": bool,
        "CompanyContractCustomInterface2": bool,
        "CompanyContractCustomInterface3": bool,
        "CompanyContractCustomInterface4": bool,
        "CompanyContractCustomOperation0": bool,
        "CompanyContractCustomOperation1": bool,
        "CompanyContractCustomOperation2": bool,
        "CompanyContractCustomOperation3": bool,
        "CompanyContractCustomOperation4": bool,
        "ProductsData": [],
        "ModifiersData": []
    }
]
```

#### Solicitud de ejemplo del metodo Obtener una venta 

```
{
    "IDDispatch": "d27a1c89-ab2f-469e-91aa-3a20943ab79c"
}
```

### Método Venta

#### Descripción

Crea una venta. Recibe  un Dispatch ID que deberá ser único.

#### Formato de solicitud

*URL: /api/ContactlessPayment/ProcessSale* </br>
*Method: POST* </br>
```
Body { 
	"IDDispatch": "string",
	"PumpNumber": "string", 
	"TransactionSequenceNumber": integer,
	"LocalTransactionDate": integer,
	"LocalTransactionTime": integer,
	"TerminalIdentification": "string",
	"PrimaryTrack": "string", 
	"TransactionAmount": integer, 
	"ProductCode": "string",
	"ProductUnitPrice": double, 
	"ProductAmount": double, 
	"ProductQuantity": double,
	
}
```
#### Formato de respuesta

Header:
```
Content-Type: application/json; charset=utf-8
content-encoding: gzip 
```

```
Body {
    "ApplicationType": "string",
    "ProcessingMode": "string",
    "MessageFormatVersion": "string",
    "TerminalIdentification": "string",
    "DeviceTypeIdentifier": "string",
    "TransactionCode": "string",
    "AccountType": "string",
    "EntryMethod": "string",
    "PumpNumber": "string",
    "ProductCode": string,
    "ProductUnitPrice": double,
    "ProductAmount": double,
    "ProductQuantity": double,
    "ProductData": [],
    "TransactionAmount": double,
    "UnitCode": string,
    "CurrencyCode": string,
    "BatchNumber": integerer,
    "ShiftNumber": string,
    "TransactionSequenceNumber": integer,
    "LocalTransactionDate": integerr,
    "LocalTransactionTime": integer,
    "CustomerData": {
        "ContractMode": "string"
    },
    "AuthorizationCode": "string",
    "InvoiceNumber": string,
    "ResponseCode": "string",
    "ResponseText": "string",
    "ReceiptData": "{ "CustomerName":"string", 
    		      "CustomerIdentification":"string", 
		      "CustomerPlate":"string", 
		      "CustomerPAN":"string", 
		      "CustomerLabel":"string",
		      "CompanyName":"string",
		      "CompanyCode":"string",
		      "TransactionId":"string",
		      "AuthorizationType":integer,
		      "CustomerVehiclePlate":"string",
		      "CustomerVehicleCode":"string",
		      "CustomerVehicleModel":"string",
		      "CustomerVehicleBrand":"string",
		      "CustomerTruckUnitNumber":"string",
		      "CustomerOdometer":"string", 
		      "CustomerDriverId":"string", 
		      "ContractCode":"string",
		      "CompanyTaxPayerId":"string",
		      "CompanyStreet1":"string",
		      "CompanyStreet2":"string",
		      "ContractBalanceMode":"string" }",
    "LongResponseText": "Autorizado"
}
```

#### Solicitud de ejemplo del metodo venta

```
{
    "IDDispatch": "d27a1c89-ab2f-469e-91aa-3a20943ab79c",
    "PumpNumber": "1",
    "TransactionSequenceNumber": 123,
    "TerminalIdentification": "S2G321",
    "PrimaryTrack": "0000000000001",
    "TransactionAmount": 99,
    "ProductCode": "1",
    "ProductUnitPrice": 1,
    "ProductAmount": 99,
    "ProductQuantity": 99
}
```
### Manejo de errores

Las salidas exitosas / fallidas en la API de la interfaz se manejarán a través de códigos de estado HTTP.

La solicitud exitosa obtendrá un HTTP 200 y la respuesta resultante.

Las acciones destinadas a devolver datos, por ejemplo, el grupo Descargas de transacciones pueden devolver muchos registros, solo un registro o incluso ningún registro y aunque se considerarán exitosas si las solicitudes cumplen con los criterios de validación. Estas acciones siempre devolverán una lista de registros con formato JSON, encerrada entre corchetes “[…]”. Una respuesta vacía contendrá [] como cuerpo.

Las acciones destinadas a publicar un comando, por ejemplo, el grupo Cargos de declaración devolverán un solo elemento con formato JSON con los campos "ResponseCode", "ResponseMessage" y "ResponseError". El cuerpo de estas respuestas nunca estará vacío.

Si no se procesa la solicitud, se indicará mediante un código de estado de rango HTTP 400. El cuerpo contendrá un solo elemento con formato JSON con los campos "ResponseCode", "ResponseMessage" y "ResponseError".


## Mensajes de ejemplo

### Ejemplo Obtener una venta

#### Ejemplo Formato de solicitud


```
{ "IDDispatch": "d27a1c89-ab2f-469e-91aa-3a20943ab79c" }
```

#### Ejemplo Formato de respuesta example

```
[
    {
        "TransactionId": "d27a1c89-ab2f-469e-91aa-3a20943ab79c",
        "SubscriberCode": "S2G",
        "TransactionSequenceNumber": "120",
        "AuthorizationCode": "075532151",
        "ResponseCode": "00000",
        "ResponseMessage": "Autorizado",
        "Status": 3,
        "Mode": 0,
        "StatusDescription": "Confirmed",
        "HostDateTime": "2021/08/06 15:31:52",
        "SubscriberDateTime": "2021/08/06 12:31:52",
        "SubscriberTimeZone": "Argentina Standard Time",
        "SiteDateTime": "2021/08/06 12:31:52",
        "SiteTimeZone": "Argentina Standard Time",
        "DateTime": "2021/08/06 12:31:52",
        "MerchantCode": "04012",
        "MerchantContractCode": "123",
        "MerchantName": "fuel company ",
        "MerchantCustomField0": null,
        "MerchantCustomField1": null,
        "MerchantCustomField2": null,
        "MerchantCustomField3": null,
        "SiteCode": "1524",
        "SiteName": "lomas",
        "SiteShortName": "lomas",
        "TerminalCode": "S2G321",
        "TerminalType": "ATIONET Mobile Payment",
        "TerminalId": "09c5e5fa-af46-49a3-a0ba-041535f5e870",
        "TerminalTypeId": "70e808d3-47d2-4ba8-893a-20babab46f91",
        "SubAccountId": "1200318c-1a25-4263-b75b-291ac3d28853",
        "SecondarySubAccountId": null,
        "AccountTypeDescription": "Vehicle",
        "VehicleCode": "5924",
        "DriverCode": null,
        "TransactionNetAmount": null,
        "ProductUnitPriceRequested": 1.000000,
        "ProductVolumeRequested": 99.000000,
        "ProductAmountRequested": 99.000000,
        "TransactionAmountRequested": 99.000000,
        "ProductUnitPriceAuthorized": 0.000000,
        "ProductVolumeAuthorized": 0.000000,
        "ProductAmountAuthorized": 0.000000,
        "TransactionAmountAuthorized": 0.000000,
        "ProductUnitPriceDispensed": 1.000000,
        "ProductVolumeDispensed": 99.000000,
        "ProductAmountDispensed": 99.000000,
        "ProductNetAmountDispensed": null,
        "TransactionAmountDispensed": 99.000000,
        "ProductUnitPriceCompany": 1.000000,
        "ProductUnitPriceMerchant": 1.000000,
        "ProductAmountCompany": 99.000000,
        "ProductAmountMerchant": 99.000000,
        "TransactionAmountCompany": 99.000000,
        "TransactionAmountMerchant": 99.000000,
        "MeasurementUnitCode": null,
        "CurrencyCode": "ARS",
        "FuelCode": "1",
        "FuelMasterCode": "022",
        "FuelMasterDescription": "Compressed Natural Gas",
        "InvoiceNumber": null,
        "BatchNumber": null,
        "ShiftNumber": null,
        "PumpNumber": "1",
        "EntryMethod": "S",
        "CompanyCode": "40206",
        "CompanyName": "CON'AUTO",
        "CompanyCustomField0": null,
        "CompanyCustomField1": null,
        "CompanyCustomField2": null,
        "CompanyCustomField3": null,
        "CompaniesGroupCode": "",
        "ClassificationLabel1": "Clasificador 1 Departamentos",
        "ClassificationLabel2": "Classification 2",
        "ClassificationLabel3": "Classification 3",
        "ClassificationLabel4": "Classification 4",
        "ContractCode": "40206",
        "CompanyContractClassificationValue1": "",
        "CompanyContractClassificationValue2": "",
        "CompanyContractClassificationValue3": "",
        "CompanyContractClassificationValue4": "",
        "CompanyContractCustomField0": null,
        "CompanyContractCustomField1": null,
        "CompanyContractCustomField2": null,
        "CompanyContractCustomField3": null,
        "SubContractCode": "40206",
        "PrimaryIdentificationTrack": "0000000000001",
        "SecondaryIdentificationTrack": null,
        "PrimaryIdentificationPAN": "004",
        "SecondaryIdentificationPAN": null,
        "PrimaryIdentificationLabel": "Identification1 ATIONet",
        "SecondaryIdentificationLabel": null,
        "PrimaryIdentificationModelDescription": "Card",
        "SecondaryIdentificationModelDescription": null,
        "FleetCode": "4210",
        "FleetName": "CONAUTO Fleet",
        "VehiclePlate": "HAL180",
        "VehicleClassDescription": null,
        "VehicleClassificationValue1": null,
        "VehicleClassificationValue2": null,
        "VehicleClassificationValue3": null,
        "VehicleClassificationValue4": null,
        "DriverName": null,
        "DriverClassificationValue1": null,
        "DriverClassificationValue2": null,
        "DriverClassificationValue3": null,
        "DriverClassificationValue4": null,
        "CustomerData": {},
        "FastTrackData": {},
        "TaxesData": {},
        "FeesData": [
            {
                "Name": "descuentos",
                "Value": 496.366000,
                "Id": "715a7981-84f1-477f-9360-626bf6addb41"
            }
        ],
        "CompanyTaxpayerId": "15024",
        "ApplicationCode": null,
        "DisputeDate": null,
        "Reason": null,
        "State": null,
        "DisputeCommentCompany": null,
        "ResolvedDate": null,
        "DisputeResolveNetworkComment": null,
        "Odometer": null,
        "SiteCountryId": "e8812e4f-406c-49dc-8b99-d985361af691",
        "SiteCountry": "Argentina",
        "SiteAddress": "Av. Muñiz 366, () (Martinez) Buenos Aires Argentina",
        "SiteStateId": "785f7886-3429-4f2e-b633-049e802a4ece",
        "SiteState": "Buenos Aires",
        "SiteCity": "Martinez",
        "SiteZipCode": null,
        "SiteClassificationValue1": "ZONA GOBIERNO 2",
        "SiteClassificationValue2": null,
        "SiteClassificationValue3": null,
        "SiteClassificationValue4": null,
        "SiteCustomField0": null,
        "SiteCustomField1": null,
        "SiteCustomField2": null,
        "SiteCustomField3": null,
        "DriverFirstName": null,
        "DriverLastName": null,
        "GPSVirtualOdometer": null,
        "GPSDistance": null,
        "GPSAddress": null,
        "GPSComment": null,
        "DriverCustomField0": null,
        "DriverCustomField1": null,
        "DriverCustomField2": null,
        "DriverCustomField3": null,
        "VehicleCustomField0": null,
        "VehicleCustomField1": null,
        "VehicleCustomField2": null,
        "VehicleCustomField3": null,
        "IdProgram": "d112c23a-4bdb-4c68-9bde-43cd334627c5",
        "ProgramDescription": "Classic",
        "LatitudeStart": null,
        "LongitudeStart": null,
        "AltitudeStart": null,
        "LatitudeEnd": null,
        "LongitudeEnd": null,
        "AltitudeEnd": null,
        "ContingencyReason": null,
        "AuthorizationType": 0,
        "AttendantCode": null,
        "PumpSide": null,
        "VehicleBrand": "TOYOTA",
        "VehicleModel": null,
        "Subsidized": null,
        "SiteCountryCode": "ARG",
        "CompanyContractCustomInterface0": false,
        "CompanyContractCustomInterface1": false,
        "CompanyContractCustomInterface2": false,
        "CompanyContractCustomInterface3": false,
        "CompanyContractCustomInterface4": false,
        "CompanyContractCustomOperation0": false,
        "CompanyContractCustomOperation1": false,
        "CompanyContractCustomOperation2": false,
        "CompanyContractCustomOperation3": false,
        "CompanyContractCustomOperation4": false,
        "ProductsData": [],
        "ModifiersData": []
    }
]
```

### Ejemplo método venta

#### Ejemplo formato de solicitud 

```
{
    "IDDispatch": "d27a1c89-ab2f-469e-91aa-3a20943ab79c",
    "PumpNumber": "1",
    "TransactionSequenceNumber": 123,
    "TerminalIdentification": "S2G321",
    "PrimaryTrack": "0000000000001",
    "TransactionAmount": 99,
    "ProductCode": "1",
    "ProductUnitPrice": 1,
    "ProductAmount": 99,
    "ProductQuantity": 99
}
```

#### Ejemplo formato de respuesta

```
{
    "ApplicationType": "FCS",
    "ProcessingMode": "1",
    "MessageFormatVersion": "1.3",
    "TerminalIdentification": "S2G321",
    "DeviceTypeIdentifier": "4",
    "TransactionCode": "210",
    "AccountType": "1",
    "EntryMethod": "S",
    "PumpNumber": "1",
    "ProductCode": null,
    "ProductUnitPrice": null,
    "ProductAmount": null,
    "ProductQuantity": null,
    "ProductData": [],
    "TransactionAmount": null,
    "UnitCode": null,
    "CurrencyCode": null,
    "BatchNumber": null,
    "ShiftNumber": null,
    "TransactionSequenceNumber": 296,
    "LocalTransactionDate": 20210827,
    "LocalTransactionTime": 125346,
    "CustomerData": {
        "ContractMode": "1"
    },
    "AuthorizationCode": "052554144",
    "InvoiceNumber": null,
    "ResponseCode": "00000",
    "ResponseText": "Autorizado",
    "ReceiptData": "{\"CustomerName\":\"5924 - HAL180\",\"CustomerIdentification\":\"5924\",\"CustomerPlate\":\"HAL180\",\"CustomerPAN\":\"004\",\"CustomerLabel\":\"Identification1 ATIONet\",\"CompanyName\":\"CON'AUTO\",\"CompanyCode\":\"40206\",\"TransactionId\":\"00e49ed2-210f-4d0d-8093-dd80996c05e7\",\"AuthorizationType\":0,\"CustomerVehiclePlate\":\"HAL180\",\"CustomerVehicleCode\":\"5924\",\"CustomerVehicleModel\":null,\"CustomerVehicleBrand\":\"TOYOTA\",\"CustomerTruckUnitNumber\":null,\"CustomerOdometer\":\"\",\"CustomerDriverId\":null,\"ContractCode\":\"40206\",\"CompanyTaxPayerId\":\"15024\",\"CompanyStreet1\":\"Av. Conauto\",\"CompanyStreet2\":null,\"ContractBalanceMode\":\"4\"}",
    "LongResponseText": "Autorizado"
}
```

