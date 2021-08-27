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
- [Description](#description)
- [Details](#api-details)	
- [Supported Transactions](#supported-transactions)
- [Message Structure](#message-structure)
	- [MobilePayments](#mobilePayments)
	- [PreAuthorizedPayments](#preAuthorizedPayments)
	- [GetTransaction](#getTransaction)
	- [Cancel](#cancel)
- [Error Handling](#error-handling)
- [Field Descriptions](#field-descriptions)
- [Transactions States](#transactions-states)
	- [Transaction states sequence diagram on Pre authorization Request](#transactionstates-sequence-diagram-on-pre-authorization-request)
	- [Transaction states sequence diagram on Cancelation Request](#transaction-states-sequence-diagram-on-cancelation-request)
- [Response Codes](#response-codes)
	- [ MobilePayments | PreAuthorizedPayments Response codes](#mobilePayments-|-preAuthorizedpaymentsresponse-codes)
	- [ Cancelation Response codes](#cancelation-response-codes)
- [Message Samples](#message-samples)
	- [MobilePayments ](#mobilePayments)
	- [PreAuthorizedPayments ](#preAuthorizedpayments)
	- [GetTransaction ](#gettransaction)
	- [Cancel ](#cancel)
	

## Overview

![ationetTR](Content/Images/DynamicQRPayments/schema.png)

### Introduction

ATIONet Dynamic QR Code Payments allows to generate the dynamic QR code from their Billing POS/System for a specific order/bill and must pass the order-specific information such as Order ID, Order Amount, etc. while generating the code. The customer can scan this QR to make a payment and the merchant can check the transaction status using the Dispatch ID and accordingly close the order/bill.

``` 
Note: A customer-facing screen is required, which will show the dynamically generated QR to him in order to be able to
scan it and generate the sale.

```

### Overview of Dynamic QR Code

<ol>
	<li>Customer chooses the goods/service in a store and shows the intent to the cashier for Ationet Driver App payment.</li>
	<li>Cashier creates an order with the bill amount and a unique Dispatch ID in the POS system.</li>
	<li>Merchant’s backend server  Create QR Code  and displays the QR Code to the Customer on the consumer-facing screen.</li>
	<li>Customer scans QR code via Paytm or any Ationet Driver App.</li>
	<li>Customer enters the  pin in the respective tionet Driver App app to complete the payment XXXXX</li>
	<li>Merchant's server receives the transaction confirmation by pulling them from an API to get the transaction confirmation against the order.</li>
	<li>Merchant's POS system closes the bill/order and shares the payment response with the customer..</li>
</ol>



![ationetTR](Content/Images/DynamicQRPayments/demoQR.gif)

## QR code Payments squence

![ationetTR](Content/Images/DynamicQRPayments/sequence.svg)

## Dynamic QR Code Payments Implementation

### Introduction

The section describes the integration steps required to integrate ATIONe's Dynamic QR Code Payments with billing POS to accept contactless payment from your customer using the Ationet Driver App payment.

## STEP 1: Get your authentication keys XXX

<ul>
	<li>Merchant Key: A unique secret key used to secure encryption of every request. This needs to be kept on server-side and should not be shared with anyone.</li>
</ul>

```
Note: Never share your secret Merchant Key with anyone.
```


## STEP 2: Create Dynamic QR Code

Merchant Backend only encodes the minimum sale information in QR, It is the one that comes from site controller when generating a sale. The rest of the trama information is completed by the Merchant Backend (point of sale).The following table describes each field in the table, its description and its origin, being QR for values that have to be coded and POS for values that are completed by Merchant Backend.

```
Important: Trama have to be in JSON format.

```
### The following table  contains all static  properties that the Merchant Backend must complete to do a sale.

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
				<p align="left">ProcessingMode</p>
			</td>
			<td>
				<p align="center">string</p>
			</td>
			<td>
			 	<p align="center">POS</p>
			 </td>
			<td>
				<p>“0” = Host Capture Only “1” = Host Processing Required“2” = Operator Assisted Capture</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
				<p align="left">SystemModel</p>
			</td>
			<td>
				<p align="center">string</p>
			</td>
			<td>
			 	<p align="center">POS</p>
			 </td>
			<td>
				<p>It is the environment from which the request is made</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
				<p align="left">SystemVersion</p>
			</td>
			<td>
				<p align="center">string</p>
			</td>
			<td>
			 	<p align="center">POS</p>
			 </td>
			<td>
				<p>By default is NB</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
				<p align="left">TransactionCode</p>
			</td>
			<td>
				<p align="center">string</p>
			</td>
			<td>
			 	<p align="center">POS</p>
			 </td>
			<td>
				<p>Refer to Transactions Codes in Reference <a href="AN-Native_Transaction_Protocol-Spec.md#111-transaction-codes.md">Tables Section</a>.Use 200 for a Sale request</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
				<p align="left">EntryMethod</p>
			</td>
			<td>
				<p align="center">string</p>
			</td>
			<td>
			 	<p align="center">POS</p>
			 </td>
			<td>
				<p>“M” Manual Entry “S” Swap Card “T” Tag read</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
				<p align="left">ApplicationType</p>
			</td>
			<td>
				<p align="center">string</p>
			</td>
			<td>
			 	<p align="center">POS</p>
			 </td>
			<td>
				<p>“Always “FCS” Fleet Control System</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
				<p align="left">AccountType</p>
			</td>
			<td>
				<p align="center">string</p>
			</td>
			<td>
			 	<p align="center">POS</p>
			 </td>
			<td>
				<p>Refer to Account Types in <a href="AN-Native_Transaction_Protocol-Spec.md#track-data">Tables Section.</a> Use 1 for QR Payments</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
				<p align="left">MessageFormatVersion</p>
			</td>
			<td>
				<p align="center">string</p>
			</td>
			<td>
			 	<p align="center">POS</p>
			 </td>
			<td>
				<p>For QR Payments use 1.3</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
				<p align="left">CurrencyCode</p>
			</td>
			<td>
				<p align="center">string</p>
			</td>
			<td>
			 	<p align="center">POS</p>
			 </td>
			<td>
				<p>Refer to Currency Codes in Reference <a href="AN-Native_Transaction_Protocol-Spec.md#117-currency-codes">Tables Section.</a>.</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
				<p align="left">DeviceTypeIdentifier</p>
			</td>
			<td>
				<p align="center">string</p>
			</td>
			<td>
			 	<p align="center">POS</p>
			 </td>
			<td>
				<p>“1” = Indoor Payment Terminal “2” = Outdoor Payment Terminal “3” = Card Reader in Dispenser “4” = Other Self-Service</p>
			</td>
		 </tr>
		</tbody>
</table>

### The following table  contains all properties that come from the Site controller.

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
				<p>Refer to Transaction Sequence Number in <a href="AN-Native_Transaction_Protocol-Spec.md#transaction-sequence-number">Field Description section</a></p>
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
				<p>Local Transaction Date: yyyymmdd</p>
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
				<p>Local Transaction Time: hhmmss</p>
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
			 	<p align="center">Site controller</p>
			 </td>
			<td>
				<p>Terminal Identification</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
				<p align="left">PrimaryTrack</p>
			</td>
			<td>
				<p align="center">string</p>
			</td>
			<td>
			 	<p align="center">Site controller</p>
			 </td>
			<td>
				<p>Refer to Track Data in <a href="AN-Native_Transaction_Protocol-Spec.md#track-data">Field Description section</a></p>
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
				<p>xxx.xxx</p>
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
				<p align="left">DispatchID</p>
			</td>
			<td>
				<p align="center">(string) Guid ID</p>
			</td>
			<td>
			 	<p align="center">Site controller</p>
			 </td>
			<td>
				<p>XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX</p>
			</td>
		 </tr>
		</tbody>
</table>

```
Complete Trama example in JSON Format:

{
    "ProcessingMode": "1", 
    "SystemModel": "POSTMAN",
    "SystemVersion": "NB", 
    "TransactionCode": "200", 
    "EntryMethod": "S",
    "ApplicationType": "FCS", 
    "AccountType": "1", 
    "MessageFormatVersion": "1.3", 
    "CurrencyCode": "ARS",
    "DeviceTypeIdentifier": "4", 
    "PumpNumber": "1",
    "TransactionSequenceNumber": 808,
    "LocalTransactionDate": 20210812, 
    "LocalTransactionTime": 113152, 
    "TerminalIdentification": "S2G321",
    "PrimaryTrack": "0000000000001",
    "TransactionAmount": 99,
    "ProductCode": "1",
    "ProductUnitPrice": 1,
    "ProductAmount": 99,
    "ProductQuantity": 99
    "DispatchID": guid ID
}
	
```

## STEP 3: Customer scans Dynamic QR code

When the QR code is generated for an specific order, the customer scans that QR code and pays using the Ationet Driver App from. The customer is notified about the payment status on their Ationet Driver App after the successful completion of payment.

```
Note: Customers cannot change the order amount in their app on scanning the particular order QR code.
```

## STEP 4: Confirm the Transaction Status

Once the payment is completed by a customer, the merchant can confirm the transaction status by Polling  the Transaction Status API.

```
Polling - Setup a polling process after regular intervals using the Transaction Status API.

```

## STEP 5: Manage Refunds XXX


### Integration Checklist

Post completion of integration in your staging environment, it is mandatory to test the integration before moving into the live environment with production. Below points should be taken care of during the integration of the flow:

<ol>
   <li>The transaction status should be verified through the Transaction Status API in the payment flow.</li>	
   <li>The Dispacht ID passed to Ationet should be unique.</li>	
   <li>The amount must not contain more than 2 decimal points, comma, or any special characters.</li>	 XXX
   <li>Dispatch ID parameter is mandatory for creating QR.</li>	
   <li>For any local errors implemented in POS, user-friendly messages should be displayed to the cashier.</li>	
   <li></li>	
</ol>

### API Documentation

*URL:  http://native-beta.ationet.com* </br>

### Request Format 

*URL: v1/auth* </br>
*Method: POST* </br>
*Body { "ProcessingMode": "string",
	"SystemModel": "string,</br>  
	"SystemVersion": "string",</br> 
	"TransactionCode": "string",</br> 
	"EntryMethod": "string",</br> 
	"ApplicationType": "string",</br> 
	"AccountType": "string",</br> 
	"MessageFormatVersion": "string",</br>
	"CurrencyCode": "string",</br> 
	"DeviceTypeIdentifier": "string",</br> 
	"PumpNumber": "string",</br> 
	"TransactionSequenceNumber": integer,</br>
	"LocalTransactionDate": integer,</br>
	"LocalTransactionTime": integer,</br>
	"TerminalIdentification": "string",</br>
	"PrimaryTrack": "string",</br> 
	"TransactionAmount": integer,</br> 
	"ProductCode": "string",</br>
	"ProductUnitPrice": double,</br> 
	"ProductAmount": double,</br> 
	"ProductQuantity": double,</br>
	"DispatchId": "string"</br>
}*

### Response Format 

*Body {
    "ApplicationType": "string",</br>
    "ProcessingMode": "string",</br>
    "MessageFormatVersion": "string",</br>
    "TerminalIdentification": "string",</br>
    "DeviceTypeIdentifier": "string",</br>
    "TransactionCode": "string",</br>
    "AccountType": "string",</br>
    "EntryMethod": "string",</br>
    "PumpNumber": "string",</br>
    "ProductCode": string,</br>
    "ProductUnitPrice": double,</br>
    "ProductAmount": double,</br>
    "ProductQuantity": double,</br>
    "ProductData": [],</br>
    "TransactionAmount": double,</br>
    "UnitCode": string,</br>
    "CurrencyCode": string,</br>
    "BatchNumber": integerer,</br>
    "ShiftNumber": string,</br>
    "TransactionSequenceNumber": integer,</br>
    "LocalTransactionDate": integerr,</br>
    "LocalTransactionTime": integer,</br>
    "CustomerData": {</br>
        "ContractMode": "string"</br>
    },</br>
    "AuthorizationCode": "string",</br>
    "InvoiceNumber": string,</br>
    "ResponseCode": "string",</br>
    "ResponseText": "string",</br>
    "ReceiptData": "{ "CustomerName":"string",</br> 
    		      "CustomerIdentification":"string",</br> 
		      "CustomerPlate":"string",</br> 
		      "CustomerPAN":"string",</br> 
		      "CustomerLabel":"string",</br>
		      "CompanyName":"string",</br>
		      "CompanyCode":"string",</br>
		      "TransactionId":"string",</br>
		      "AuthorizationType":integer,</br>
		      "CustomerVehiclePlate":"string",</br>
		      "CustomerVehicleCode":"string",</br>
		      "CustomerVehicleModel":"string",</br>
		      "CustomerVehicleBrand":"string",</br>
		      "CustomerTruckUnitNumber":"string",</br>
		      "CustomerOdometer":"string",</br> 
		      "CustomerDriverId":"string",</br> 
		      "ContractCode":"string",</br>
		      "CompanyTaxPayerId":"string",</br>
		      "CompanyStreet1":"string",</br>
		      "CompanyStreet2":"string",</br>
		      "ContractBalanceMode":"string" }",</br>
    "LongResponseText": "Autorizado"</br>
}*

### QR Code 

Merchant Backend only encodes the minimum sale information in QR, It is the one that comes from a terminal when generating a sale. The rest of the trama information is completed by the Merchant Backend (point of sale).The following table describes each field in the table, its description and its origin, being QR for values that have to be coded and POS for values that are completed by Merchant Backend.





