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
|1.0|2/August/2021|Initial version.|

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

<div class="mxgraph" style="max-width:100%;border:1px solid transparent;" data-mxgraph="{&quot;highlight&quot;:&quot;#0000ff&quot;,&quot;nav&quot;:true,&quot;resize&quot;:true,&quot;toolbar&quot;:&quot;zoom layers lightbox&quot;,&quot;edit&quot;:&quot;_blank&quot;,&quot;xml&quot;:&quot;&lt;mxfile host=\&quot;app.diagrams.net\&quot; modified=\&quot;2021-08-26T15:20:45.833Z\&quot; agent=\&quot;5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/92.0.4515.159 Safari/537.36\&quot; etag=\&quot;MlVm3O5r17GQgmDcWvGk\&quot; version=\&quot;14.9.3\&quot; type=\&quot;google\&quot;&gt;&lt;diagram name=\&quot;QR Dinámico\&quot; id=\&quot;74e2e168-ea6b-b213-b513-2b3c1d86103e\&quot;&gt;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&lt;/diagram&gt;&lt;/mxfile&gt;&quot;}"></div>
<script type="text/javascript" src="https://viewer.diagrams.net/js/viewer-static.min.js"></script>
### Introduction

This specification is intended to document ATIONet’s Mobile Payment fleet API messaging format and related features required for usarage. The following sections provide descriptions of the messages themselves, the expected behaviour for each supported transaction type and a common ground for the functionality of each relevant item.

## Description 

This service receives the requests from the client and stores them in a Queue in Azure to later be unqueued and processed.

### API Details

API URI: *ationetmobilepayment-appshost-test.azurewebsites.net/*

### Supported Transactions

<table>
	<thead>
		<tr valign="center">
			<th rowspan="2" width="125" align="left">
				Name
			</th>
			<th colspan="2" align="center">
				Ver.
			</th>
			<th rowspan="2" align="left">
				Description
			</th>
		</tr>
		 <tr valign="top">
			  <th align="center">
					Initial
			  </th>
			  <th align="center">
					Change
			  </th>
		 </tr>
	</thead>
	<tbody>
		 <tr valign="top">
			<td>
				<p align="left">MobilePayments</p>
			</td>
			<td>
				<p align="center">1.0</p>
			</td>
			<td></td>
			<td>
				<p align="left">Used to validate a sale request, return the Transaction ID. If the Sale already exists, returns the ID</p>
			</td>
		 </tr>
		 <tr valign="top">
			<td>
				<p align="left">PreAuthorizedPayments</p>
			</td>
			<td>
				<p align="center">1.0</p>
			</td>
			<td></td>
			<td>
				<p align="left">Used to do a sale request with external approval, returns Transaction ID. If the Sale already exists, returns the ID</p>
			</td>
		 </tr>
		 <tr valign="top">
			<td>
				<p align="left">GetTransaction</p>
			</td>
			<td>
				<p align="center">1.0</p>
			</td>
			<td></td>
			<td>
				<p align="left">Returns a Sale information.</p>
			</td>
		 </tr>
		 <tr valign="top">
			<td>
				<p align="left">Cancel</p>
			</td>
			<td>
				<p align="center">1.1</p>
			</td>
			<td></td>
			<td>
				<p align="left">Cancels a Sale.</p>
			</td>
		 </tr>
		 
	
</table>


## Message Structure

This section describe the message structure for each API Method available, as well as the responses messages for each one.

### MobilePayments 

Create a Sale with Ationet authorization. The sale creation recibes an ID, if this ID already exists then the method returns the Sale's Id.

#### Request Format

*URL: /api/MobilePayments* </br>
*Method: POST* </br>
*Body: { "siteCode":"string", "pumpNumber": integer, "fuelCode": "string", "amount": double, "primaryTrack": string, "terminalCode": "string", "mobilePaymentMode": integer, "potencyKeyId": "string" ,  "externalReferanceID":"string" }* </br>

#### Response Format

*Header:*

	Content-Type: application/json; charset=utf-8
	content-encoding: gzip 

*Body:	{ “TransactionId”:”StringValue” }*


### PreAuthorizedPayments

Create a Sale with external authorization. The sale creation recibes an ID, if this ID already exists then the method returns the Sale's Id.

#### Request Format

*URL: /api/PreAuthorizedPayments* </br>
*Method: POST* </br>
*Body: { "siteCode":"string", "pumpNumber":integer, "fuelCode":"string", "amount":double, "mobilePaymentMode":integer, "potencyKeyId":"string", "externalReferanceID":"string" }* </br>

#### Response Format

*Header:*

	Content-Type: application/json; charset=utf-8
	content-encoding: gzip 

*Body: { “TransactionId”:”StringValue” }*

### GetTransaction

#### Request Format

*URL: /api/MobilePayments/GetTransaction/{id}* </br>
*Method: GET* </br>
*Body: { "id": "string" }* </br>

#### Response Format

*Header:*

	Content-Type: application/json; charset=utf-8
	content-encoding: gzip 

*Body: {
  "id":"string", </br>
  "siteCode":"string", </br>
  "primaryTrack":"string", </br>
  "odometer": double, </br>
  "terminalIdentification":"string", </br>
  "transactionSequenceNumber":integer, </br>
  "state_Name":"string",</br>
  "state_Id":integer,</br>
  "paymentProcessorReferenceId":"string",</br>
  "paymentProcessorMessage":"string",</br>
  "siteSystemMessage":"string",</br>
  "fuelPointNumber":integer,</br>
  "paymentMethod":"string",</br>
  "requestedAmount":double,</br>
  "authorizedAmount":double,</br>
  "dispatchedAmount":double,</br>
  "dispatchedQuantity":double,</br>
  "productCode":"string",</br>
  "productDescription":"string",</br>
  "productUnitPrice":double,</br>
  "unitMeasure":"string",</br>
  "createDateTime":"string",</br>
  "updateDateTime":"string"</br>
}*

### Cancel 

Cancels a Sale that is in course as long as your status is correct. In the following diagram you can check all cancellable transaction statuses - [Transaction states sequence diagram on Cancelation Request](#transaction-states-sequence-diagram-on-cancelation-request)

#### Request Format

*URL: /api/MobilePayments/Cancel* </br>
*Method: POST* </br>
*Body:{ “TransactionId”:”StringValue” }* </br>

#### Response Format

*Header:*

	Content-Type: application/json; charset=utf-8
	content-encoding: gzip 

*Body:{ ”transactionId”: ”StringValue”, ”isSuccessCanceled”: ”bool”, ”responseCode"”: ”string”, ”responseMessage”: ”string” }*


## Error Handling

Success/failure exits on the Native Transaction Protocol will be handled via HTTP status codes.

Successful request will get a HTTP 200 and the resulting response.

Failure to process the request will be indicated by an HTTP 400’s range status code.

## Field Descriptions

This section describe through a table  all parameters from request.

<table>
	<thead>
		<tr valign="center">
			<th rowspan="3" width="400" align="left">
				Request
			</th>
			<th rowspan="3" width="125" align="left">
				Paramether
			</th>
			<th rowspan="3" width="125" align="left">
				Type
			</th>
			<th rowspan="3" width="225" align="left">
				Description
			</th>
		</tr>
	</thead>
	<tbody>
		 <tr valign="top">
			<td>
				<p align="left">MobilePayments | PreAuthorizedPayments</p>
			</td>
			<td>
				<p align="left">siteCode</p>
			</td>
			<td>
			 	<p align="left">string</p>
			 </td>
			<td>
				<p align="left">The site code</p>
			</td>
		 </tr>
		 <tr valign="top">
			<td>
				<p align="left">MobilePayments | PreAuthorizedPayments</p>
			</td>
			<td>
				<p align="left">pumpNumber</p>
			</td>
			<td>
			 	<p align="left">integer</p>
			 </td>
			<td>
				<p align="left">The pump number</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
				<p align="left">MobilePayments | PreAuthorizedPayments</p>
			</td>
			<td>
				<p align="left">fuelCode</p>
			</td>
			<td>
			 	<p align="left">string</p>
			 </td>
			<td>
				<p align="left">The fuel code</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
				<p align="left">MobilePayments | PreAuthorizedPayments</p>
			</td>
			<td>
				<p align="left">amount</p>
			</td>
			<td>
			 	<p align="left">double</p>
			 </td>
			<td>
				<p align="left">Number of liters of fuel to dispatch</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
				<p align="left">MobilePayments</p>
			</td>
			<td>
				<p align="left">primaryTrack</p>
			</td>
			<td>
			 	<p align="left">string</p>
			 </td>
			<td>
				<p align="left">The number associated with the card</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
				<p align="left">MobilePayments</p>
			</td>
			<td>
				<p align="left">terminalCode</p>
			</td>
			<td>
			 	<p align="left">string</p>
			 </td>
			<td>
				<p align="left">The terminal code</p>
			</td>
		 </tr>		
		<tr valign="top">
			<td>
				<p align="left">MobilePayments | PreAuthorizedPayments</p>
			</td>
			<td>
				<p align="left">mobilePaymentMode</p>
			</td>
			<td>
			 	<p align="left">integer</p>
			 </td>
			<td>
				<p align="left">The operation mode Code. It can be for 1 for Fullintegrated</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
				<p align="left">MobilePayments | PreAuthorizedPayments</p>
			</td>
			<td>
				<p align="left">potencyKeyId</p>
			</td>
			<td>
			 	<p align="left">string</p>
			 </td>
			<td>
				<p align="left">The Transaction's ID</p>
			</td>
		 </tr>		
		<tr valign="top">
			<td>
				<p align="left">PreAuthorizedPayments</p>
			</td>
			<td>
				<p align="left">externalReferenceID</p>
			</td>
			<td>
			 	<p align="left">string</p>
			 </td>
			<td>
				<p align="left">Authorization reference ID</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
				<p align="left">GetTransaction | Cancel</p>
			</td>
			<td>
				<p align="left">transactionId</p>
			</td>
			<td>
			 	<p align="left">string</p>
			 </td>
			<td>
				<p align="left">Transaction ID</p>
			</td>
		 </tr>
</table>


## Transactions States

This section describe through a table  all  states that a sale can have.


<table>
	<thead>
		<tr valign="center">
			<th rowspan="2" width="125" align="left">
				State name
			</th>			
			<th rowspan="2" width="125" align="left">
				ID
			</th>			
			<th rowspan="2" width="125" align="left">
				Message
			</th>
		</tr>		
	</thead>
	<tbody>
		 <tr valign="top">
			<td>
				<p align="left">Created</p>
			</td>
			<td>
				<p align="center">1</p>
			</td>
			<td>
				<p align="left">Created</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
				<p align="left">PreauthorizationAccepted</p>
			</td>
			<td>
				<p align="center">2</p>
			</td>
			<td>
				<p align="left">Preauthorization Accepted</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
				<p align="left">PreauthorizationRejected</p>
			</td>
			<td>
				<p align="center">3</p>
			</td>
			<td>
				<p align="left">Preauthorization Rejected</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
				<p align="left">FuelPointAuthorizationRequested</p>
			</td>
			<td>
				<p align="center">4</p>
			</td>
			<td>
				<p align="left">FuelPoint Authorization Requested</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
				<p align="left">PumpReserveAccepted</p>
			</td>
			<td>
				<p align="center">5</p>
			</td>
			<td>
				<p align="left">Site System Accept Pump Reserve</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
				<p align="left">PumpReserveRefused</p>
			</td>
			<td>
				<p align="center">6</p>
			</td>
			<td>
				<p align="left">Site System not Accept Pump Reserve</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
				<p align="left">FuelPointAuthorized</p>
			</td>
			<td>
				<p align="center">7</p>
			</td>
			<td>
				<p align="left">Fuel Point Authorized</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
				<p align="left">CanceledByFuelPoint</p>
			</td>
			<td>
				<p align="center">8</p>
			</td>
			<td>
				<p align="left">Canceled By Fuel Point</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
				<p align="left">Fueling</p>
			</td>
			<td>
				<p align="center">9</p>
			</td>
			<td>
				<p align="left">Fueling</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
				<p align="left">Complete</p>
			</td>
			<td>
				<p align="center">10</p>
			</td>
			<td>
				<p align="left">Complete</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
				<p align="left">CompleteFailed</p>
			</td>
			<td>
				<p align="center">11</p>
			</td>
			<td>
				<p align="left">Complete Failed</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
				<p align="left">CancelationRequested</p>
			</td>
			<td>
				<p align="center">12</p>
			</td>
			<td>
				<p align="left">Cancelation Requested</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
				<p align="left">CanceledByUser</p>
			</td>
			<td>
				<p align="center">13</p>
			</td>
			<td>
				<p align="left">Canceled By User</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
				<p align="left">CanceledBySiteSystem</p>
			</td>
			<td>
				<p align="center">14</p>
			</td>
			<td>
				<p align="left">Canceled By Site System</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
				<p align="left">FuelPointDeauthorizationRequested</p>
			</td>
			<td>
				<p align="center">15</p>
			</td>
			<td>
				<p align="left">Fuel Point Deauthorization Requested</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
				<p align="left">SessionError</p>
			</td>
			<td>
				<p align="center">16</p>
			</td>
			<td>
				<p align="left">Session not available</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
				<p align="left">UnknownError</p>
			</td>
			<td>
				<p align="center">17</p>
			</td>
			<td>
				<p align="left">Unknown error when trying to connect with session</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
				<p align="left">SiteSystemError</p>
			</td>
			<td>
				<p align="center">18</p>
			</td>
			<td>
				<p align="left">Site System Generic error</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
				<p align="left">SiteSystemError</p>
			</td>
			<td>
				<p align="center">19</p>
			</td>
			<td>
				<p align="left">Cancelled By MPPA</p>
			</td>
		 </tr>
</table>


### Transaction states sequence diagram on Pre authorization Request


![ationetTR](Content/Images/MobilePaymentFleet/MobilePaymentFleetTransactionStates.PNG)


### Transaction states sequence diagram on Cancelation Request


![ationetTRCancel](Content/Images/MobilePaymentFleet/MobilePaymentFleetCancelationState.png)

## Response Codes

### MobilePayments | PreAuthorizedPayments Response codes
	
Both methos response the same codes.

<table>
	<thead>
		<tr valign="center">
			<th rowspan="3" width="125" align="left">
				Code
			</th>
			<th rowspan="3" width="125" align="left">
				Description
			</th>
		</tr>
	</thead>
	<tbody>
		<tr valign="top">
			<td>
			<p align="left">200</p>
			</td>
			<td>
				<p align="left">Success</p>
			</td>
		 </tr>
			<tr valign="top">
			<td>
			<p align="left">400</p>
			</td>
			<td>
				<p align="left">Bad request</p>
			</td>
		 </tr>
	 </tbody>
		
</table>


### Cancelation Response codes

<table>
	<thead>
		<tr valign="center">
			<th rowspan="3" width="225" align="left">
				Code
			</th>
			<th rowspan="3" width="225" align="left">
				Response
			</th>
			<th rowspan="3" width="225" align="left">
				Response body Code
			</th>
			<th rowspan="3" width="225" align="left">
				Response body Message
			</th>
		</tr>
	</thead>
		<tbody>
		<tr valign="top">
			<td>
			<p align="left">200</p>
			</td>
			<td>
				<p align="left">Success</p>
			</td>
			<td>
				<p align="left">00000</p>
			</td>
			<td>
				<p align="left">Successfully Canceled</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
			<p align="left">200</p>
			</td>
			<td>
				<p align="left">Success</p>
			</td>
			<td>
				<p align="left">-10000</p>
			</td>
			<td>
				<p align="left">Invalid state - Transaction not updated</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
			<p align="left">200</p>
			</td>
			<td>
				<p align="left">Success</p>
			</td>
			<td>
				<p align="left">04001</p>
			</td>
			<td>
				<p align="left">Invalid state - Transaction status is alredy cancel</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
			<p align="left">200</p>
			</td>
			<td>
				<p align="left">Success</p>
			</td>
			<td>
				<p align="left">02001</p>
			</td>
			<td>
				<p align="left">Cancel by Generic error</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
			<p align="left">200</p>
			</td>
			<td>
				<p align="left">Success</p>
			</td>
			<td>
				<p align="left">04003</p>
			</td>
			<td>
				<p align="left">Invalid state - dispenser is fueling</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
			<p align="left">200</p>
			</td>
			<td>
				<p align="left">Success</p>
			</td>
			<td>
				<p align="left">04004</p>
			</td>
			<td>
				<p align="left">Invalid state - Transaction status is completed</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
			<p align="left">200</p>
			</td>
			<td>
				<p align="left">Success</p>
			</td>
			<td>
				<p align="left">04007</p>
			</td>
			<td>
				<p align="left">Unknow transaction or authorization</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
			<p align="left">200</p>
			</td>
			<td>
				<p align="left">Success</p>
			</td>
			<td>
				<p align="left">04008</p>
			</td>
			<td>
				<p align="left">Invalid state - Cancelation is alredy requested</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
			<p align="left">200</p>
			</td>
			<td>
				<p align="left">Success</p>
			</td>
			<td>
				<p align="left">04009</p>
			</td>
			<td>
				<p align="left">Invalid state - dispenser is fueling</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
			<p align="left">200</p>
			</td>
			<td>
				<p align="left">Success</p>
			</td>
			<td>
				<p align="left">04010</p>
			</td>
			<td>
				<p align="left">Transacion canceled by Session not available</p>
			</td>
		 </tr>
		<tr valign="top">
			<td>
			<p align="left">200</p>
			</td>
			<td>
				<p align="left">Success</p>
			</td>
			<td>
				<p align="left">04011</p>
			</td>
			<td>
				<p align="left">Transacion canceled by unknow error</p>
			</td>
		 </tr>
			<tr valign="top">
			<td>
			<p align="left">400</p>
			</td>
			<td>
				<p align="left">Bad request</p>
			</td>
			<td>
				<p align="center">-</p>
			</td>
			<td>
				<p align="center">-</p>
			</td>
		 </tr>
	 </tbody>

</table>
	
## Message Samples

### MobilePayments Sample
	
```
{
  "siteCode": "1524",
  "pumpNumber": 1,
  "fuelCode": "3",
  "amount": 9,
  "primaryTrack": "0000000000001",
  "terminalCode": "S2G321",
  "mobilePaymentMode": 1,
  "potencyKeyId": "5734cbb9-f78f-4ad4-aa87-79ed95181c5a"
}
	
```
	
### PreAuthorizedPayments

```
{
  "siteCode": "1524",
  "pumpNumber": 1,
  "fuelCode": "3",
  "amount": 9,
  "mobilePaymentMode": 1,
  "potencyKeyId": "5734cbb9-f78f-4ad4-aa87-79ed95181c5a",
  "externalReferanceID": "854712"
}

```
	
### GetTransaction

```
{
  "id": 5734cbb9-f78f-4ad4-aa87-79ed95181c5a
}
```
	
### Cancel

```
{
  "transactionId": "5664cbb9-f78f-4ad4-aa87-79ed95181c5a"
}
```
