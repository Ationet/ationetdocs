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

- [Overview](#overview)
	- [Introduction](#introduction)
	- [Overview of Dynamic QR Code](#Overview-of-Dynamic-QR-Code)
- [QR code Payments squence](#QR-code-Payments-squence)
- [Dynamic QR Code Payments Implementation](#Dynamic-QR-Code-Payments-Implementation)	
	- [Introduction](#Introduction)
	- [STEP 1 Get your authentication keys (Pending/ In progress)](#STEP-1-Get-your-authentication-keys)
	- [STEP 2 Create Dynamic QR Code](#STEP-2-Create-Dynamic-QR-Code)
	- [STEP 3 Customer scans Dynamic QR code](#STEP-3-Customer-scans-Dynamic-QR-code)
	- [STEP 4 Confirm the Transaction Status](#STEP-4-Confirm-the-Transaction-Status)
	- [Integration Checklist](#Integration-Checklist)
- [API Documentation](#API-Documentation)
	- [Create method](#Create-method)
	- [Get Transaction status](#Get-Transaction-status)
	- [Sale Payment Request Method](#Sale-Payment-Request-Method)
	- [Process Sale Payment Method](#Process-Sale-Payment-Method)
	- [Refuse Payment Method](#Refuse-Payment-Method)
- [Error handling](#Error-handling)
- [Messages samples](#Messages-samples)
	- [Create method sample](#Create-method-sample)
	- [Get Transaction status sample](#Get-Transaction-status-sample)
	- [Sale Payment Request Method sample](#Sale-Payment-Request-Method-sample)
	- [Process Sale Payment Method sample](#Process-Sale-Payment-Method-sample)
	- [Refuse Payment Method sample](#Refuse-Payment-Method-sample)
	
## Overview

![ationetTR](Content/Images/DynamicQRPayments/schemaDarkLight.png)

### Introduction

Ationet fleet Mobile payments - Dynamic QR  allows to generate the dynamic QR code from their Billing POS/System for a specific order/bill and must pass the order-specific information such as Dispatch ID, Order Amount, etc. while generating the code. The customer can scan this QR to make a payment and the POS's Backend can check the transaction status using the Dispatch ID.

``` 
Note: A customer-facing screen is required, which will show the dynamically generated QR to him in order to be able to
scan it and generate the sale.

```

### Overview of Dynamic QR Code

<ol>
	<li>Customer chooses the goods/service in a store and shows the intent to the cashier for Ationet Driver App payment.</li>
	<li>Cashier creates an order with the bill amount and a unique Dispatch ID in the POS system.</li>
	<li>POS’s backend server  Create QR Code  and displays it to the Customer on the consumer-facing screen.</li>
	<li>Customer scans QR code via Ationet Driver App.</li>
	<li>POS’s backend server automatically starts polling the Transaction status every 8 times/minute using Dispatch ID.</li>
</ol>



![ationetTR](Content/Images/DynamicQRPayments/demoQR.gif)

## QR code Payments squence

![ationetTR](Content/Images/DynamicQRPayments/dinamicQrFlow2-en.drawio.png)

## Dynamic QR Code Payments Implementation

### Introduction

The section describes the integration steps required to integrate ATIONet's Dynamic QR Code Payments with billing POS to accept contactless payment from your customer using the Ationet Driver App payment.

### STEP 1 Get your authentication keys

>You must required your keys from ATIONET

<ul>
	<li>POS's Backend Key: A unique secret key used to secure encryption of every request. This needs to be kept on server-side and should not be shared with anyone.</li>
</ul>

```
Note: Never share your secret POS's Backend Key with anyone.
```


### STEP 2 Create Dynamic QR Code

POS's Backend only encodes the minimum sale information in QR, it is the one that comes from site controller when generating a sale. The rest of the plot information is completed by the POS's Backend. The following table describes each field in the table, its description and its origin.

```
Important: the request body have to be in JSON format. QR image must be free text type.

```

<table>
	<thead>
		<tr valign="center">
			<th rowspan="2"  align="left">
				Name
			</th>
			<th rowspan="2" align="center">
				Type
			</th>
			<th rowspan="2" align="left">
				Origin
			</th>
			<th rowspan="8" align="left">
				Description
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
				<p align="left">TerminalIdentification</p>
			</td>
			<td>
				<p align="center">string</p>
			</td>
			<td>
			 	<p align="center">Site controller/POS IdentificationAtionet</p>
			 </td>
			<td>
				<p>It must be requested from ATIONet</p>
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
		<tr valign="top">
			<td>
				<p align="left">ProductDescription</p>
			</td>
			<td>
				<p align="center">string</p>
			</td>
			<td>
			 	<p align="center">Site controller</p>
			 </td>
			<td>
				<p>(OPCIONAL) Is the product description</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
				<p align="left">ImageRequired</p>
			</td>
			<td>
				<p align="center">bool</p>
			</td>
			<td>
			 	<p align="center">Site controller or POS Backend</p>
			 </td>
			<td>
				<p>If you send it true, the response will return the property `image` with the QR Image enconde in base 64. By default is 					false.</p>
			</td>
		 </tr>
		</tbody>
</table>

### Examples

In [Create method](#create-method) section you can find a request body sample in `Json` format.

#### QR Image example

![ationetTR](Content/Images/DynamicQRPayments/DynamicQr5.png)

### STEP 3 Confirm the Transaction Status

When the QR code is generated for an specific transaction, the POS's Backend Get The Transaction status with a polling process using the [Transaction status API](#Get-Sale-Method). `You have to do the polling  ussing IdDispatch`.

```
Polling : Setup a polling process after regular intervals using the Transaction Status API. 
To get the best results out of a status query, you should check the status 8 times/minute.

```

### STEP 4 Customer scans Dynamic QR code

When the QR code is generated for an specific transaction, the customer scans that QR code and pays using Ationet Driver App. The customer is notified about the payment status on their Ationet Driver App  after the successful completion of payment. If you want to implement a new client app you can check the specification of the [create sale api](#Sale-Method).


```
Note: Customers cannot change the Transaction amount in their app on scanning the particular order QR code.
```

### Dynamic QR Transaction States

<table>
	<thead>
		<tr valign="center">
			<th rowspan="2" align="left">
				Name
			</th>
			<th rowspan="8" align="left">
				Description
			</th>
		</tr>
	</thead>
	<tbody>
		<tr valign="top">
			<td>
				<p align="left">Post Paid Created</p>
			</td>
			<td>
				<p>The sale data is received and the Transaction is created</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
				<p align="left">Post Paid Read</p>
			</td>
			<td>
				<p>The Customer scan the QR Code image</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
				<p align="left">Post Paid Confirmed</p>
			</td>
			<td>
				<p>The Customer confirm the QR Payment and the Transaction is approved</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
				<p align="left">Post Paid Cancelled</p>
			</td>
			<td>
				<p>The Customer refuse the QR Payments</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
				<p align="left">Transaction Refused</p>
			</td>
			<td>
				<p>The Transaction is refuse by Payment processor</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
				<p align="left">Cancelled By MPPA</p>
			</td>
			<td>
				<p>The Transaction es cancelled by time out</p>
			</td>
		 </tr>
		</tbody>
</table>

### Integration Checklist

Post completion of integration in your staging environment, it is mandatory to test the integration before moving into the live environment with production. Below points should be taken care of during the integration of the flow:

<ol>
   <li>The Transaction status should be verified through the Transaction Status API in the payment flow.</li>	
   <li>The Dispacht ID passed to Ationet should be unique.</li>	
   <li>The amount must not contain more than 2 decimal points, comma, or any special characters.</li>	 
   <li>Dispatch ID parameter is mandatory for creating QR.</li>	
</ol>

## API Documentation

*Production URL:  ationetmobilepayment-appshost.azurewebsites.net* </br>
*QA URL:  ationetmobilepayment-appshost-test.azurewebsites.net* </br>

### Create method

#### Description

Receive the sale's information. Returns the Transaction's Id, the QR Type, the URL to do the Sale and the QR Code Image encode in base 64 format.

The IdDispatch sent should be unique.

>`WARNING`: You have 120 secs to confirm the payment. After that the Transaction won't available. 

>This method require basic auth through header. Example `Basic user:pass`.

#### Request Format

*URL: /api/PostPaid/Create* <br>
*Method: HttpPost*

```
body {
  "Sale": {
    "IdDispatch":"string",    
    "PumpNumber": "string",
    "TerminalIdentification": "string",
    "ProductCode": "string",
    "ProductUnitPrice": double,
    "ProductAmount": double,
    "ProductQuantity": double,
    "ProductDescription": "string"
  },
  "ImageRequired": bool
}

```

>You can check the description values in [STEP 2 Create Dynamic QR Code](#STEP-2-Create-Dynamic-QR-Code) section.

#### Response Format

Header:
```
Content-Type: application/json; charset=utf-8
content-encoding: gzip

```

```
body { 
	"transactionId":"string",
	"qrData":"string",
	"image":"string",
	"mpqrType":int
}
```

Response properties description
	
```
"IdTransaction": The transaction Id.
"qrData": Contains the data to be enconde in a QR Image.
"image": The Qr Image enconde in base 64 or a empty value.
"mpqrType": Is the QR Image type. By default the number 2 indicates that image is for Dynamic QR.

```

### Get Transaction status

#### Description

Return a Transaction information.

>This method require basic auth through header. Example `Basic user:pass`.

#### Request Format

*URL: /api/PostPaid/GetTransactionStatus* </br>
*Method: HttpPost* </br>

```
Body { "idDispatch": "string" }

```

##### Properties description

<table>
	<thead>
		<tr valign="center">
			<th rowspan="2"  align="left">
				Name
			</th>
			<th rowspan="8" align="left">
				Description
			</th>
		</tr>
	</thead>
	<tbody>
		<tr valign="top">
			<td>
				<p align="left">idDispatch</p>
			</td>
			<td>
				<p>Is the Transaccion Id</p>
			</td>
		 </tr>
		</tbody>
</table>

#### Response Format

Header:
```
Content-Type: application/json; charset=utf-8
content-encoding: gzip 
```

```
body 
{ 
	"AuthorizationCode": "string", 
	"ResponseCode": "string", 
	"ResponseMessage":  "string", 
	"TransactionStatus":
		{
			"name":"string",
			"id": int
		} 
}

```

### Sale Payment Request Method

#### Description

Receive the idDispatch. Returns the Sale information.

>This method require basic auth through header. Example `Basic user:pass`.

#### Request Format

*URL: /api/PostPaid/SalePaymentRequest/{IdDispatch}* </br>
*Method: HttpGet* </br>

##### Parameters description

<table>
	<thead>
		<tr valign="center">
			<th rowspan="2"  align="left">
				Name
			</th>
			<th rowspan="8" align="left">
				Description
			</th>
		</tr>
	</thead>
	<tbody>
		<tr valign="top">
			<td>
				<p align="left">IdDispatch</p>
			</td>
			<td>
				<p>Is the Dispatch Id</p>
			</td>
		 </tr>		
		</tbody>
</table>

#### Response Format 

Header:
```
Content-Type: application/json; charset=utf-8
content-encoding: gzip 
```

```
{
    "idTransaction": "string",
    "saleContent": {
        "productCode": "string",
        "productAmout": double,
        "productUnitPrice": double,
        "productQuantity": double,
        "productDescription": "string"
    },
    "content": "string"
}
```

### Process Sale Payment Method

#### Description

Create a Sale. Receive  the transaction id and the primaryTrack from driver.

>This method require basic auth through header. Example `Basic user:pass`.

#### Request format

*URL: /api/PostPaid/ProcessSalePayment* </br>
*Method: HTTPPost* </br>

```
Body { "idTransaction": "string", "primaryTrack": "string" }

```

##### Properties description

<table>
	<thead>
		<tr valign="center">
			<th rowspan="2"  align="left">
				Name
			</th>
			<th rowspan="8" align="left">
				Description
			</th>
		</tr>
	</thead>
	<tbody>
		<tr valign="top">
			<td>
				<p align="left">id</p>
			</td>
			<td>
				<p>The transacction Id.</p>
			</td>
		 </tr>	
		<tr valign="top">
			<td>
				<p align="left">primaryTrack</p>
			</td>
			<td>
				<p>The driver identifier</p>
			</td>
		 </tr>	
		</tbody>
</table>


#### Response format

Header:
```
Content-Type: application/json; charset=utf-8
content-encoding: gzip 
```

```
body 
{ 
	"AuthorizationCode": "string", 
	"ResponseCode": "string", 
	"ResponseMessage":  "string", 
    	"IdTransaction": "string",
  	"CustomerData": {
		"PromptPrimaryPin": "string",
		"PromptSecondaryTrack": "string",
		"PromptOdometer": "string",
		"LastOdometer": "string",
		"MinOdometer": "string",
		"MaxOdometer": "string"
		"PromptDriverId": "string",
		"PromptVehicleId": "string",
		"PromptTruckUnitNumber": "string",
		"PromptTrailerNumber": "string",
		"PromptEngineHours": "string",
		"PromptMiscellaneous": "string"
	}
}
```


### Refuse Payment Method

#### Description

Refuse the payment request for a sale as long as its status is `Post Paid Read`. Receive the Transaction ID

>This method require basic auth through header. Example `Basic user:pass`.

#### Request format

*URL: /api/PostPaid/RefusePaymentRequest* </br>
*Method: HTTPPost* </br>

```
Body { "idTransaction": "string" }

```

##### Properties description

<table>
	<thead>
		<tr valign="center">
			<th rowspan="2"  align="left">
				Name
			</th>
			<th rowspan="8" align="left">
				Description
			</th>
		</tr>
	</thead>
	<tbody>
		<tr valign="top">
			<td>
				<p align="left">idTransaction</p>
			</td>
			<td>
				<p>The transacction Id.</p>
			</td>
		 </tr>	
		</tbody>
</table>


#### Response format

Header:
```
Content-Type: application/json; charset=utf-8
content-encoding: gzip 
```

```
body { "AuthorizationCode": "string", "ResponseCode": "string", "ResponseMessage":  "string", "TransactionId": "string" }

```

## Error handling

Success/failure exits on the Interface API will be handled via HTTP status codes.

Successful request will get a HTTP 200 and the resulting response.

Failure to process the request will be indicated by an HTTP 400’s range status code. The body will contain a single JSON-formatted item with the “ResponseCode”, “ResponseMessage” and “ResponseError” fields.


## Messages samples

### Create method sample

#### Request example

```
body:

{
  "sale": {
    "IdDispatch":"de1ae20c-858c-4989-a334-43992df5c45c",
    "PumpNumber": "1",
    "TerminalIdentification": "S2G321",
    "ProductCode": "1",
    "ProductUnitPrice": 1,
    "ProductAmount": 10,
    "ProductDescription": "SUPER",
    "productQuantity": 299
},
  "imageRequired": true
}

```

#### Response example

```
{
    "idTransaction": "9e19d7a7-34c3-400e-8fb6-d7fe9ff5d55e",
    "qrData": "https://ationetmobilepayment-appshost-test.azurewebsites.net/api/PostPaid/SalePaymentRequest/?IdDispatch=de1ae20c-858c-4989-a334-43992df5c45c",
    "image": "iVBORw0KGgoAAAANSUhEUgAABRQAAAUUCAYAAACu5p7oAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAAJcEhZcwAADsMAAA7DAcdvqGQAAP+lSURBVHhe7NhRqizZtiPR1/9OV3XADvjGxA3lXC",
    "mpqrType": 2
}

```

### Get Transaction status sample

#### Request example

```
{ "idDispatch": "3fa85f64-5717-4562-b3fc-2c963f66afa6" }

```

#### Response example

```
{
    "authorizationCode": "030744119",
    "responseCode": "00000",
    "responseMessage": "Autorizado",
    "transactionStatus": {
        "name": "Post Paid Confirmed",
        "id": 22
    }
}



```

### Sale Payment Request sample

#### Request example

```
api/PostPaid/ProccessSale/?IdDispatch=a11be318-07dd-4318-bcc3-41704c54c995

```

#### Response example

```
{
    "idTransaction": "624b8dc0-dfd5-46d3-b13a-61a4aac784af",
    "saleContent": {
        "productCode": "1",
        "productAmout": 10.00,
        "productUnitPrice": 1.00,
        "productQuantity": 299.00,
        "productDescription": "SUPER"
    },
    "content": "{\"ProcessingMode\":\"1\",\"SystemModel\":\"MOBILE\",\"SystemVersion\":\"NB\",\"TransactionCode\":\"200\",\"EntryMethod\":\"S\",\"ApplicationType\":\"FCS\",\"AccountType\":\"1\",\"MessageFormatVersion\":1.3,\"CurrencyCode\":\"ARS\",\"DeviceTypeIdentifier\":4,\"TransactionSequenceNumber\":0,\"LocalTransactionDate\":20211019,\"LocalTransactionTime\":140632,\"SiteCode\":null,\"TransactionAmount\":10,\"PrimaryTrack\":null,\"IdDispatch\":\"c421eea9-5b04-40ff-b857-67dfc71866d0\",\"PumpNumber\":\"1\",\"TerminalIdentification\":\"S2G321\",\"ProductCode\":\"1\",\"ProductUnitPrice\":1,\"ProductAmount\":10,\"ProductQuantity\":10,\"ProductDescription\":null}"
}

```


### Process Sale Payment sample

#### Request example

```
{ "idDispatch": "3fa85f64-5717-4562-b3fc-2c963f66afa6", "primaryTrack": "00000001" }

```

#### Response example

```
{
    "idTransaction": "3f34bdf9-15e2-4ef4-9134-f5a53ac360a8",
    "authorizationCode": "035657109",
    "responseCode": "40500",
    "responseMessage": "Solicitud requerida",
    "customerData": {
        "PromptEngineHours": "true",
        "MinEngineHours": "66",
        "ContractMode": "2"
    }
}
```

### Refuse Payment Method sample

#### Request example

```
{
  "idTransaction": "480ba3a1-ea50-48c8-911a-e0474af9a3da"
}
```

#### Response example

```
{}

```
