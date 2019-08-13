![ationetlogo](Content/Images/ATIOnetLogo_250x70.png)
# ATIONet - Mercado Pago Transaction Protocol Specification v1.1 #

||Document Information|
|--- |--- |
|File:|AN-MercadoPago_Transaction_Protocol-Spec|
|Doc Version:|1.0|
|Release Date:|10, August 2019|
|Author:|ATIONet LLC|


|||Change Log|
|--- |--- |--- |
|Ver.|Date|Change Summary|
|1.0|10, August 2019|Initial version. Covers POST and GET Transactions|



## Contents ##

- [2 Scope](#2-scope)
	- [2.1 Scope Details](#21-scope-details)
	- [2.2 Supported Transactions](#22-supported-transactions)

- [3 Data Security](#3-data-security)

- [4 Message Structure](#4-message-structure)
	- [Request Format](#request-format)
	- [Response Format](#response-format)

- [5 Error Handling](#5-error-handling)

- [6 Field descriptions](#6-field-descriptions)
	- [System Model and System Version](#system-model-and-system-version)
	- [Pump Authorization Values](#pump-authorization-values)
	- [Terminal Identification](#terminal-identification)
	- [Device Type Identifier](#device-type-identifier)
	- [Transaction Sequence Number](#transaction-sequence-number)
	- [Entry Method](#entry-method)
	- [Processing Mode](#processing-mode)
	- [Track Data](#track-data)
	- [Batch Number](#batch-number)
	- [Shift Number](#shift-number)
	- [Product Fields](#product-fields)
	- [Customer Data](#customer-data)
	- [Re-prompting & Dual-Card Identification](#re-prompting--dual-card-identification)
	- [Authorization Code](#authorization-code)
	- [PIN Block](#pin-block)
	- [Original Data](#original-data)

- [7 Transaction Request (TREQ) Message Format](#7-transaction-request-treq-message-format)

- [8 Reference Tables](#11-reference-tables)
	- [8.1 Transaction Codes](#91-transaction-codes)
	- [8.2 Response Codes](#92-response-codes)	
	- [8.3 Account Types](#93-account-type)
	- [8.4 Product Data Structure](#94-product-data-structure)
	- [8.5 Customer Data](#95-customer-data)
	- [8.6 Measurement Unit Codes](#96-measurement-unit-codes)
	- [8.7 Currency Codes](#97-currency-codes)
	- [8.8 Original Data](#98-original-data)
- [9 Message Samples](#10-message-samples)
	- [9.1 Pre Authorization Sample](#101-pre-authorization-samples)
	- [9.2 Completion Sample](#102-completion-sample)
- [Appendix A - Native Authorization Protocol Messages](#appendix-a---native-authorization-protocol-messages)

## Overview

### Introduction

This specification is intended to document ATIONet’s Mercado Pago Protocol messaging format and related features required for the systems applying for integration with ATIONet. The following sections provide descriptions of the messages themselves, the expected behavior for each supported transaction type and a common ground for the functionality of each relevant item.

## 2 Scope

Version 1.0 of this document covers a particular version of ATIONet’s Host protocol. Although feature’s descriptions are generally not related to a particular version of the protocol, some changes may apply which would be specifically commented and identified on each feature’s
description paragraph.

### 2.1 Scope Details

**Protocol**: ATIONet Mercado Pago Transaction Protocol

**Version**: Version 1.0

**API Base URI**: mercadopago.ationet.com/v1/

### 2.2 Supported Transactions
|Name|Version|Description|
|--- |--- |--- |--- |
|Send Transaction|1.0|Used to receive and store transactions from gas stations.|
|Get Transaction|1.0|Send to client the latest transaction done in the specified fueling point.|


## 3 Data Security

To validate the source of transactions and data encryption, the ATIONet Native Transaction Protocol relies on a SSL connection between the Site’s Terminal or Site’s Controller and the ATIONet Host. The SSL connection is established for each request/response pair, using a certificate property of ATIONet, meaning that each request must include a system-type user and password on the Header. The user will be matched against the related ATIONet actor for each message.

Users to be used on the Transaction Protocol messaging will be created by authorized users via ATIONet Console, with the role “Controller/Terminal”.

At this time there is no provisioning to distribute or update certificates or thumbprints thru a system interface. This information will be provided at request of the Controller’s vendor during the integration project.

## 4 Error Handling

Success/failure exits on the Mercado Pago Transaction Protocol will be handled via HTTP status codes.

Successful request will get a HTTP 200 and the resulting response.

Any interaction with the API will return a single JSON-formatted item with the “Response Code” and “Response Text”. The body of these responses will never be empty.

Failure to process the request will be indicated by an HTTP 400’s range status code. The body will contain a single JSON-formatted item with the “ResponseCode”, “ResponseMessage” and “ResponseError” fields.



- **ResponseCode**: Will contain a unique code for that specific error
- **ResponseMessage**: A short message describing the error
- **ResponseError**: Will contain the stack trace of the error, this helps debug process.

*Sample JSON body*

	{“ResponseCode”:”40001”,”ResponseMessage”:”Site not Found”,”ResponseError”:""}

Refer to [Response Codes](#112-response-codes) Table in the Reference Tables section for a complete list of supported codes.

## 5 Message Structure

At the moment of writing the "Transactions Controller" is supporting two HTTP actions, POST and GET, this actions are handle in the following URL: **mercadopago.ationet.com/v1/transactions**.


### HTTP POST 
#### Request

*Header:*

	Accept-Encoding: gzip

	Authorization: Basic user:password

*Body:*
In the body a Transaction structure should be placed (in JSON format)

	{“Fieldname”:”StringValue”,”FieldName”:”StringValue”,”FieldName”:Value}

#### Response

*Header:*

	Content-Type: application/json; charset=utf-8

*Body:*
If the HTTP response code is different than 200, then the following structure is return 

	{“ResponseCode”:”StringValue”,”ResponseMessage”:”StringValue”,”ResponseError”:StringValue}

### HTTP GET 
#### Request

*Header:*

	Accept-Encoding: gzip

	Authorization: Basic user:password

*Body:*

	{“SiteId”:”33335b11-455a-498c-9e60-9a3d41b35135”,”PumpId”:”09”}

#### Response

*Header:*

	Content-Type: application/json; charset=utf-8

*Body:*
If the HTTP request response code is 200, the body will contain the Transaction structure described in section 7.
If the HTTP response code is different than 200, the structure described in section 4 is return 

	{“Fieldname”:”StringValue”,”FieldName”:”StringValue”,”FieldName”:Value}

Note: Alphanumeric fields, stated as Type “A/N” in record format tables below show the maximum possible length as the Size, although in JSON-formatted strings they will be represented with trailing spaces trimmed.

## 6 Field Descriptions

This section details the purpose and expected behavior on the Controller system for relevant items on the protocol.


## 7 Order object
|Field Name|Type|Condition|Descriptions/Field Value(s)|
|--- |--- |--- |--- |--- |
|collector_id|Long|Required| Identificador de la cuenta de Mercado Pago a la que se le acreditarán los pagos.|
|sponsor_id|Long|Required|Identificador de una cuenta de Mercado Pago que integra la solución.|
|external_reference|String|Required|Referencia para sincronizar con tu sistema.|
|notification_url|String|Required|URL a la cual se enviarán las notificaciones, definida por el integrador.|
|items|Array|Required|Lista de los productos, donde cada item es un object con los siguientes campos|
|loyalty|Object|Required|Datos necesarios para sumar puntos en un determinado programa de fidelización|

##7.1 Items object
|Field Name|Type|Condition|Descriptions/Field Value(s)|
|--- |--- |--- |--- |--- |
|title|String|Required|Nombre del producto.|
|quantity|Entero|Required|Cantidad de este producto.|
|unit_price|Decimal|Required|Precio unitario del producto.|

##7.2 Loyalty object
|Field Name|Type|Condition|Descriptions/Field Value(s)|
|--- |--- |--- |--- |--- |
|program|String|Required|Programa de fidelización (serviclub, payback, etc.)|
|transaction_id|String|Required|Número de transacción.|
|invoice_number|String|Required|Número de comprobante.|
|transaction_date|String|Required|Fecha y hora de la transacción (ISO 8601).|
|transaction_amount|Decimal|Required|Importe total de la transacció.|
|store_id|String|Required|Identificador único del negocio (identificador de estación de servicio o APIES).|
|products|Array|Required|Lista de los productos comprados con los siguientes atributos|
|code|String|Required|Código del producto.|
|quantity|Decimal o entero|Required|Por ejemplo 20.50 litros.|
|unit_price|Decimal|Required|Precio unitario del producto.|
|unit|String|Required|Unidad de medida si aplica (litre, etc.)|
|cashier_identification|Object|Required|Datos del empleado|
|type|String|Required|Tipo de documento (DNI, INE, etc.)|
|number|String|Required|Id de documento.|
|period|String|Required|Número del período.|
|shift|String|Required|Número del turno.|
|affinity_plan|String|Required|Plan de afinidad.|

## 8 Reference Tables

This section brings together the code tables and reference values used in messaging.


### 8.2 Response Codes
|Code|Response Message|Long Response Message|Description|
|--- |--- |--- |--- |
|**Authorized**||||
|00000|Authorized|Authorized||
|**Request Validations**||||
|10000|Invalid date|Invalid date||
|10001|Invalid time|Invalid time||
|10002|Invalid seq num|Invalid sequence number||
|10003|Invalid acc type|Invalid account type||
|10004|Invalid app type|Invalid application type||
|10005|Invalid proc mode|Invalid processing mode||
|10006|Invalid mess format|Invalid message format||
|10007|Invalid dev type|Invalid device type||
|10008|Invalid sys model|Invalid system model||
|10009|Invalid sys ver|Invalid system version||
|10010|Invalid entry method|Invalid entry method||
|10011|Invalid unit code|Invalid unit code||
|10012|Invalid unit code|Invalid datetime||
|10013|Invalid pri track|Invalid primary track||
|10014|Invalid prod data|Invalid product data||
|10015|Prod data req|Product data required||
|10016|Invalid batch number|Invalid batch number||
|10017|Invalid respone code|Invalid respone code||
|10018|Invalid terminal|Invalid terminal||
|10019|Invalid old PIN|Invalid old PIN||
|10020|Invalid new PIN|Invalid new PIN||
|10021|Invalid orig data|Invalid original data||
	
### 8.3 Account Type

|Type|Description|
|--- |--- |
|“1”|ATIONet native track|	

### 8.4 Product Data Structure

|Field Name|Size|Type|Condition|Descriptions/Field Value(s)|
|--- |--- |--- |--- |--- |
|ServiceCode|1|string|Required||
|ProductCode|4|string|Required|“0”-“9999”|
|ProductUnitPrice|Var|decimal|Optional|xxx.xxx|
|ProductNetAmount|Var|decimal|Optional|xxxxxxx.xx|
|ProductTaxes|Var|Dictionary|Optional|<”[Tax Description]”, [Tax Value]>|
|ProductAmount|Var|decimal|Optional|xxxxxxx.xx|
|ProductQuantity|Var|decimal|Optional|xxxxxxx.xx|
|UnitCode|Var|string|Optional|Refer to Measurement Unit Codes in Reference Tables Section|
			
### 8.5 Customer Data
    
|Field Name|
|--- |
|TruckUnitNumber|
|TrailerNumber|
|Odometer|
|EngineHours|
|DriverId|
|Miscellaneous|
|DriverLicenseState|
|DriverLicenseNumber|
|TripNumber|
|PurchaseOrderNumber|
|ClientSupportsReceiptDownloading|
|TrailerHourMeterReading|

### 8.6 Measurement Unit Codes

|Value|Description|
|--- |--- |
|“usgal”|Gallon USA|
|“ukgal”|Gallon UK|
|“l”|Litro|
|“m3”|Metro Cúbico|
|“kg”|Kilogramo|


### 8.7 Currency Codes
 
Refer to ISO 4217 Currency Codes standard (<http://en.wikipedia.org/wiki/ISO_4217>)


### 8.8 Original Data

|Field Name|
|--- |
|TransactionCode|
|TransactionSequenceNumber|
|LocalTransactionDate|
|LocalTransactionTime|

## 9 Message Samples

### 9.1 POST Sample

```json
{
    "ProcessingMode": "1",
    "SystemModel": "",
    "SystemVersion": "",
    "TransactionCode": "100",
    "EntryMethod": "M",
    "CurrencyCode": "ARS",
    "UnitCode": "l",
    "ApplicationType": "FCS",
    "AccountType": "1",
    "MessageFormatVersion": "1.3",
    "DeviceTypeIdentifier": "4",
    "PumpNumber": "1",
    "TerminalIdentification": "AN111111",
    "TransactionSequenceNumber": 1,
    "LocalTransactionDate": 20190614,
    "LocalTransactionTime": 121500,
    "PrimaryTrack": "9532013015986508780=3905=000000",
    "PrimaryPin": null,
    "SecondaryTrack": null,
    "SecondaryPin": null,
    "ProductCode": "3",
    "ProductAmount": 20,
    "ProductQuantity": null,
    "ProductUnitPrice": null,
    "OriginalData": {},
    "ProductNetAmount": null,
    "ProductTaxes": null,
    "TransactionNetAmount": null,
    "TransactionAmount": null,
    "AuthorizationCode": null,
    "ServiceCode": null,
    "BatchNumber": null,
    "ShiftNumber": null,
    "TransactionExtendedData": null,
    "InvoiceNumber": null,
    "ResponseCode": null,
    "ResponseText": null,
    "ReceiptData": null
}
```
