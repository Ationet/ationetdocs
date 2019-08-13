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

#### System Model and System Version
Brand/Model and Firmware/Software version of the client system. Format and content will be assigned for each vendor during the Integration project.

#### Pump Authorization Values
Pre-sale Authorizations processed by ATIONet might be (a) Fully-authorized, (b) Partially-authorized, or (c) Declined. Full and partial authorizations may have the same Authorized codes, but a partial authorization only allows to sale a fraction of the requested amount. Controllers must always check the Authorized Amount/Quantity on approved transactions.

The second value relevant for the authorization value is the local authorization limit that can be enforced locally. On any case, the preset sent to the gas pump must be the lesser value between the Authorized Amount/Quantity and the DCR Cutoff Amount.

#### Terminal Identification
Terminal ID is a system-wide unique ID for the Controller or Terminal device on the capture side. Terminal ID should be configured on the client system during manual installation. The length of the TID’s code depends on the controller.

#### Device Type Identifier
A single digit field, informed by the Controller system, that identifies the type of capture device. (Manned/Unmanned, Indoor/Outdoor). In case the Controller system doesn’t have the capability to inform this distinction, “4 – Other self-service” should be always informed.

#### Transaction Sequence Number
The Transaction number is a fixed-length integer value from 1 to 999999 and it is assigned and incremented for each transaction sent to the Host, regardless of the result. It must be reset back to 1 every time it reaches the limit.

#### Entry Method
The Entry Method code indicates whether the customer identification was manually typed-in, read from a card swipe or any other automatic identification mechanism.

#### Processing Mode
Indicates whether the Host must apply an alternative process to the request. Regular transactions must inform “1 = Host processing required”

#### Track Data
This field identifies the account of the transaction.

Track Data field must contain the whole identifier’s information (for example, complete Track 2 data on a magnetic card, or all the TAG’s fields on an AVI capture).

There are two Tracks and PINs field pairs, the Primary and Secondary, on the Primary, the Controller must send the track of the identifier used to initiate the capture transaction (first card presented) and the Secondary should contain the complementary identification (if used). For example if the transaction is initiated presenting a Driver Card that also requires a Vehicle Identification, Primary will be the Driver and Secondary will be the Vehicle.

The Primary identification will mandate the sub-account to be charged for the transaction, the Secondary will be used for rules validation but will not be affected on its balance.

#### Batch Number
Optional information, if informed, ATIONet will use this field for report filtering and queries.

If used, data must be formatted as an 11 digit number: yyyymmddbbb. Year (4 digits), Month (2 digits), Day (2 digits), Batch/Shift number (3 digits, padded with zeros). Date part must be the starting date of the batch. Batch number must wrap-around to 1 after reaching 999.

If there is no batch functionality at all, the recommended format is Transaction Date plus 3 zeros.

#### Shift Number
Optional information, if informed, ATIONet will use this field for report filtering and queries.

The Controller application can manage the Shift Number and meaning as needed. It may be day’s shift number, weekly batches, split-batches, etc., although this is a fixed length field, therefore the format must be maintained.

If there is no batch or shift functionality at all, the recommended format is the business date of the transaction followed of 3 zeros.

#### Product Fields
Transaction messages include a list of Product fields, plus a Product Taxes compound field plus and a Product Data compound field, the later will be used only on multi-product transactions.

On single product messages, like a simple fueling transaction, product’s amount and other details must be sent on the fields included in the main body of the message. When the sale includes more than one product, the first one must be sent on the main body and rest on the Product Data structure. Fuel presets will only work for the product in the main body; therefore, first product in the list should be the fuel sale if there is any.

Refer to [Product Data Structure](#114-product-data-structure) Table on the Reference Tables Section.

Transaction authorization and register is based on ProductAmount and ProductQuantity; taxes and net amount fields are optional and are not considered by ATIOnet during transaction processing, but those fields may be used later for billing and reporting. Therefore, although optional at the protocol level, those might be required for certain integration projects for a given market or functional scope.

ATIONet expects standard NACS product codes. Although it can also map custom product codes for each site, Host-based product mapping is not recommended due to the extra administrative burden.

*Product Restrictions & Authorization limits on Fuel Transactions (FCS)*

Pre-Authorization Requests support different business scenarios:

**REMOVE**

|Scenario|Relevant fields values|Description|
|--- |--- |--- |
|Zero Authorization \ Any product|Product Amount = 0Product Quantity = 0Product Code = NULLProduct Unit Price = NULL or != NULL|Terminal doesn’t enforce any pre-auth value and the user didn’t select a specific product (or the client system doesn’t have product identification capabilities).ATIONet will authorize according to: <br/><br/>1.  If there is any product restriction the host will respond with a Product Code otherwise will echo the NULL Product code, confirming any product authorization.<br/>2.  If Product Unit Price is NULL and exists any price configuration the host will respond with a Product Unit Price otherwise will echo the Product Unit Price.<br/>3.  Establish amount and quantity limits based on rules and current account.<br/>4.  If the current account is based on quantity and the Terminal supports product authorization, the Host will limit by Product Quantity (with Product Code)<br/>5.  If the current account is based on quantity and the Terminal doesn’t supports product authorization, the Host will limit by Product Amount if exists Product Unit Price, otherwise the transaction will be declined. <br/>6.  If the current account is based on money and the Terminal supports amount authorization, the Host will limit by Product Amount.<br/>7.  If the current account is based on amount and the Terminal doesn’t supports amount authorization, the Host will limit by Product Quantity (with Product Code) if exists Product Unit Price, otherwise the transaction will be declined|
|Zero Authorization \ Specific product|Product Amount = 0 Product Quantity = 0 Product Code != NULL Product Unit Price = NULL or != NULL | Open value transaction for a specific product.ATIONet will authorize according to:<br/><br/>1.  If there is any product restriction will be validated first. <br/>2.  2) 3) 4) 5) 6) and 7) Equal than Zero Authorization any product.|
|Amount Authorization|Product Amount > 0 Product Quantity = 0 Product code = NULL or != NULL Product Unit Price = NULL or != NULL|Amount requested, any or specific product. ATIONet will authorize according to:<br/><br/>1.  If there is any product restriction the host will respond with a Product Code otherwise will echo the NULL Product code, confirming any product authorization.<br/>2.  If Product Unit Price is NULL and exists any price configuration the host will respond with a Product Unit Price otherwise will echo the Product Unit Price.<br/>3.  Establish amount limits based on rules and current account. If exists quantity limits and Product Unit Price is NULL the transaction will be declined.<br/>4.  5) 6) and 7) Equal than Zero Authorization any product.|
|Quantity Authorization|Product Amount = 0 Product Quantity > 0 Product code = NULL or != NULL Product Unit Price = NULL or != NULL|Quantity requested, any or specific product. <br/>ATIONet will authorize according to:<br/>1.  If there is any product restriction the host will respond with a Product Code otherwise will echo the NULL Product code, confirming any product authorization. <br/>2.  If Product Unit Price is NULL and exists any price configuration the host will respond with a Product Unit Price otherwise will echo the Product Unit Price. <br/>3.  Establish quantity limits based on rules and current account. If exists amount limits and Product Unit Price is NULL the transaction will be  declined.<br/>4.  5) 6) and 7) Equal than Zero Authorization any product.|


Transaction Amount is not relevant on Authorization requests in this version of the protocol as Dry Products sale is not yet available, on future versions, the Transaction Amount will be validated against the whole balance of the sub-account while Product figures will be evaluated against fuel product rules and restrictions.

In this version of the protocol, Transaction Amount should always match the Product Amount in Completions and Sales TREQs.

As described above, on certain situations, the Host will answer a Pre-Authorization request with an unsolicited Product Code; the Terminal must enforce such product restriction, otherwise the Completion will be declined.

With commercial and industrial system that don’t control fuel price, the Controller should use a \$1 unit price for all available products to
avoid potential declines due to the lack of unit price to resolve amount restrictions.

#### Customer Data
Customer data on a TREQ contains extra information gathered from prompts to the Cardholder or Attendant. On a TRESP, it contains the list of prompts that must be presented to the Cardholder or Attendant or a list of values to be used by the Terminal at capture, transaction or receipt printing.

*Prompt elements vs. Data elements*

Customer Data subfields can be Prompts or Data. Values contained on a Prompt are sent by the Host to be used by the Terminal to support the local processing of the prompt’s, for example minimum and maximum odometer values. ATIONet can send and receive Data elements.

Refer to Customer Data Codes Table in the Reference Tables section for a complete list of supported field names.


#### Authorization Code
The Host will return the Authorization Code on all approved transactions.
On Pre-Authorization/Completions message flows, the Controller must keep the Authorization Code sent on the Pre-Authorization TRESP and send it
back to the Host on the Completion TREQ. This is a mandatory feature.

Refer to Authorization Codes Table in the Reference Tables section for a complete list of supported codes.

#### PIN Block
The PIN entry on plain text, when the whole message or the communication themselves are encrypted.

#### Original Data
Original data on a TREQ contains extra information related to the original transaction that we want to cancel. Used only in zero completions without authorization code and cancellations transactions.

Refer to [Original Data](#118-original-data) Table in the Reference Tables section for a complete list of supported field names.

## 7 Transaction Structure

|Field Name|Size|Type|Condition|Descriptions/Field Value(s)|
|--- |--- |--- |--- |--- |
|ApplicationType|3|string|Required|Always “FCS” Fleet Control System|
|ProcessingMode|1|string|Required|“0” = Host Capture Only “1” = Host Processing Required“2” = Operator Assisted Capture|
|SiteId|Var|string|Required|Terminal Identification|
|PumpId|Var|string|Required|Terminal Identification|
|DeviceTypeIdentifier|1|string|Required|“1” = Indoor Payment Terminal “2” = Outdoor Payment Terminal “3” = Card Reader in Dispenser “4” = Other Self-Service|
|TransactionCode|3|string|Required|Refer to [Transactions Codes](#111-transaction-codes) in Reference Tables Section|
|AccountType|1|string|Required|Refer to [Account Types](#113-account-type) in Reference Tables Section|
|EntryMethod|1|string|Required|“M” Manual Entry “S” Swap Card “T” Tag read|
|PumpNumber|2|string|Optional|“00”-“99”|
|ProductCode|4|string|Optional|“0”-“9999”|
|ProductUnitPrice|Var|decimal|Optional|xxx.xxx|
|ProductNetAmount|Var|decimal|Optional|xxxxxxx.xx|
|ProductTaxes|Var|Dictionary|Optional|<”[Tax Description]”, [Tax Value]\>|
|ProductAmount|Var|decimal|Optional|xxxxxxx.xx|
|ProductQuantity|Var|decimal|Optional|xxxxxxx.xx|
|TransactionNetAmount|Var|decimal|Optional|xxxxxxx.xx|
|ProductData|Var|List|Conditional|Refer to [Product Fields](#product-fields) in Field Description section|
|TransactionAmount|Var|decimal|Optional|xxxxxxx.xx|
|UnitCode|Var|string|Optional|Refer to [Measurement Unit Codes](#116-measurement-unit-codes) in Reference Tables Section|
|CurrencyCode|3|string|Optional|Refer to [Currency Codes](#117-currency-codes) in Reference Tables Section|
|BatchNumber|Var|int|Optional|Refer to [Batch Number](#batch-number) in Field Description section|
|ShiftNumber|Var|string|Optional|Refer to [Shift Number](#shift-number) in Field Description section|
|LocalTransactionDate|8|int|Required|Local Transaction Date: yyyymmdd|
|LocalTransactionTime|6|int|Required|Local Transaction Time: hhmmss|
|CustomerData|Var|Dictionary|Conditional|Refer to [Customer Data](#customer-data) in Field Description section|
|OriginalData|Var|Dictionary|Conditional|Refer to [Original Data](#original-data) in Field Description section|
|InvoiceNumber|Var|string|Optional|.|


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
