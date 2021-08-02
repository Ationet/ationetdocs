![ationetlogo](Content/Images/ATIOnetLogo_250x70.png)
# ATIONet - Mobile Payment Fleet Api v1.0 #

|Document Information||
|--- |--- |
|File:|ATIONet-Mobile Payment Fleet Api|
|Doc Version:|1.0|
|Release Date:|2, August 2021|
|Author:|ATIONet LLC|

|Change Log|||
|--- |--- |--- |
|Ver.|Date|Change Summary|
|1.0|2/August/2021|Initial version.|

## Contents ##

- [Overview](#overview)
	- [Introduction](#introduction)
	- [Purpose](#purpose)
	- [Scope](#scope)
	- [Definitions, Acronyms and Abbreviations](#definitions,acronyms-and-abbreviations)
	- [Reference](#references)
- [Solution Architecture](#solution-architecture)
- [Messaging Flow](#messaging-flow)
- [Communication](#communication)
	- [Error Handling](#error-handling)
	- [Messages Structure](#messages-structure)
	

- [1 ATIOnet Integration Documentation Scope](#1-ationet-integration-documentation-scope)



## Overview


### Introduction

This specification is intended to document ATIONet’s Mobile Payment fleet Protocol messaging format and related features required for usarage. The following sections provide descriptions of the messages themselves, the expected behaviour for each supported transaction type and a common ground for the functionality of each relevant item.

### Definitions



## 2 API 

This service receives the requests from the client and stores them in a Queue in Azure to later be unqueued and processed.

### 2.1 API Details

API URI: ationetmobilepayment-appshost-test.azurewebsites.net/api/resource

### 2.2 Supported Transactions

<table>
	<thead>
		<tr valign="center">
			<th rowspan="2" width="125" align="left">
				Name
			</th>
			<th colspan="2" align="center">
				Protocol Ver.
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
				<p align="left">Used to validate a sale request and obtain transaction Guid ID.</p>
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
				<p align="left">Used to do a sale request with external approval and obtain transaction Guid ID.</p>
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
				<p align="left">Returns sale information.</p>
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


## 4 Message Structure

### MobilePayments 

#### Request Format

*URL: /api/MobilePayments* </br>
*Method: POST* </br>
*Body: { siteCode: string, pumpNumber: integer, fuelCode: string, amount: double, primaryTrack: string, terminalCode: string, mobilePaymentMode: integer, potencyKeyId: string ,  externalReferanceID:string } * </br>

#### Response Format

*Header:*

	Content-Type: application/json; charset=utf-8
	content-encoding: gzip 

*Body:	{“TransactionId”:”StringValue”}*


### PreAuthorizedPayments

#### Request Format

*URL: /api/PreAuthorizedPayments* </br>
*Method: POST* </br>
*Body: { siteCode: string, pumpNumber: integer, fuelCode: string, amount: double, mobilePaymentMode: integer, potencyKeyId: string , externalReferanceID": string } * </br>

#### Response Format

*Header:*

	Content-Type: application/json; charset=utf-8
	content-encoding: gzip 

*Body: {“TransactionId”:”StringValue”} *

### GetTransaction

#### Request Format

*URL: /api/MobilePayments/GetTransaction/{id}* </br>
*Method: GET* </br>
*Body: { id: string } * </br>

#### Response Format

*Header:*

	Content-Type: application/json; charset=utf-8
	content-encoding: gzip 

*Body: {
  id: string, </br>
  siteCode: string, </br>
  primaryTrack: string, </br>
  odometer: double, </br>
  terminalIdentification: string, </br>
  transactionSequenceNumber: integer, </br>
  state_Name: string,</br>
  state_Id: integer,</br>
  dispatchedAmount: double,</br>
  paymentProcessorReferenceId: string,</br>
  paymentProcessorMessage: string,</br>
  siteSystemMessage: string,</br>
  fuelPointNumber: integer,</br>
  paymentMethod: string,</br>
  requestedAmount: double,</br>
  authorizedAmount: double,</br>
  createDateTime: string,</br>
  updateDateTime: string</br>
}*

### Cancel 

#### Request Format

*URL: /api/MobilePayments/Cancel* </br>
*Method: POST* </br>
*Body:*
	{ “TransactionId”:”StringValue” } </br>

#### Response Format

*Header:*

	Content-Type: application/json; charset=utf-8
	content-encoding: gzip 

*Body:{ ”transactionId”: ”StringValue”, ”isSuccessCanceled”: ”bool”, ”responseCode"”: ”string”, ”responseMessage”: ”string” }*


## 5 Error Handling

Success/failure exits on the Native Transaction Protocol will be handled via HTTP status codes.

Successful request will get a HTTP 200 and the resulting response.

Failure to process the request will be indicated by an HTTP 400’s range status code.

Refer to [Response Codes](#112-response-codes) Table in the Reference Tables section for a complete list of supported codes.

## 6 Field Descriptions

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


## 7 Transactions States

This section describe through a table  all transactions states.

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


![ationetTR](Content/Images/MobilePaymentFleet/MobilePaymentFleetTransactionStates.PNG)
