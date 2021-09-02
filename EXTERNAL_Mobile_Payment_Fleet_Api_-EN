[ationetlogo](Content/Images/ATIOnetLogo_250x70.png)
# External PFEP Fleet Mobile Payment Api #

|Document Information||
|--- |--- |
|File:|ATIONet - Dynamic QR Code Payments|
|Doc Version:|1.0|
|Release Date:|26, August 2021|
|Author:|ATIONet LLC|

|Change Log|||
|--- |--- |--- |
|Ver.|Date|Change Summary|
|1.0|2/September/2021|Initial version.|

## Contents ##


- [Overview](#overview)
	- [Introduction](#introduction)
	- [Entities](#Entities)
	- [Sequence diagram Pay at Pump with Above Site Payment Authorization](#Sequence-diagram-Pay-at-Pump-with-Above-Site-Payment-Authorization)
- [Site System Implementation guide](#Site-System-Implementation-guide)
	- [STEP 1 Site Mobile Configuration](#STEP-1-Site-Mobile-Configuration)
	- [STEP 2 Host Mobile Configuation](#STEP2-Host-Mobile-Configuation)
	- [Values descriptions](#Values-descriptions)
	- [Status Codes and Messages](#Status-Codes-and-Messages)
	- [Static QR Image](#Static-QR-Image)
	- [How to generate QR Code Image](#How-to-generate-QR-Code-Image)
- [ATIONet PFEP Fleet Mobile Payment Api](#ATIONet-PFEP-Fleet-Mobile-Payment-Api)
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
</br>


><h3>IMPORTANT: The following document is only valid for the COMMANDER configuration.</h3>


## Introduction

This section describes the Mobile Payment Solution flow in which the PFEP is an external agent to `ATIONet`.

## Sequence diagram Pay at Pump with external PFEP

![ationetTR](Content/Images/SiteSystemCommander/external_PFEP.drawio.svg)

## Message Structure

This section describe the message structure for each API Method available, as well as the responses messages for each one.


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

## Error Handling

Success/failure exits on the Native Transaction Protocol will be handled via HTTP status codes.

Successful request will get a HTTP 200 and the resulting response.

Failure to process the request will be indicated by an HTTP 400’s range status code.

## Field Descriptions

- [Transactions States](ATIONet_Mobile_Payment_Fleet_Api_-EN.md#transactions-states)

