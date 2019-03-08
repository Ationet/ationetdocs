![ationetlogo](Content/Images/ATIOnetLogo_250x70.png)
# ATIONet - Native Device Updater Protocol Specification v1.0

<table>
	<tr>
		<th colspan="2" align="left">
			Document Information
		</th>
	</tr>
	<tr>
		<td>
			File:
		</td>
		<td>
			AN-Native_DeviceUpdater_Protocol-Spec
		</td>
	</tr>
	<tr>
		<td>
			Doc Version:
		</td>
		<td>
			1.0
		</td>
	</tr>
	<tr>
		<td>
			Release Date:
		</td>
		<td>
			21, Feb 2019
		</td>
	</tr>
	<tr>
		<td>
			Author:
		</td>
		<td>
			ATIONet LLC
		</td>
	</tr>
</table>

<table>
	<tr>
		<th colspan="3" align="left">
			Change Log
		</th>
	</tr>
	<tr>
		<td>
			Ver.
		</td>
		<td>
			Date
		</td>
		<td>
			Change Summary
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>1.0</p>
		</td>
		<td>
			<p>21/Feb/2019</p>
		</td>
		<td>
			<p>Initial version.</p>
		</td>
	</tr>
</table>

## Contents

<!-- MarkdownTOC depth=3 -->

- Overview
	- Introduction
	- Definitions
- ATIOnet Integration Documentation Scope
- Scope
	- Scope Details
	- Supported Transactions
- Data Security
- Message Structure
	- Request Format
	- Response
- Error Handling
- Field Descriptions
- Loyalty Transaction Request (LREQ) Message Format
- Loyalty Transaction Response (LRESP) Message Format
- Reference Tables
	- Transaction Codes
	- Account Type
	- Transaction Data Structure
	- Customer Data
	- Currency Codes
	- Authorization Codes
	- Response Codes

<!-- /MarkdownTOC -->

## Overview

### Introduction

El objetivo de esta documentación es especificar el formato de mensajería de protocolo nativo de la API de mantenimiento de Terminals Management y las funcionalidades requeridas para los sistemas que solicitan integración con la herramienta. Las siguientes secciones proporcionan descripciones de los mensajes y el comportamiento esperado para cada tipo de operación.

### Definitions

#### Terminal
Dispositivo al cual serán aplicadas de forma remota actualizaciones de firmwares, parámetros o recursos descritos en una agenda programada, y del que se llevara un control o monitoreo del estado de operatividad y localización física en la cual se encuentra.

#### Agenda
Cronograma programado de actualización de terminal, en el que se agrupan terminales para aplicar una actualización requerida por el usuario en una fecha y hora especifica; en ella se encuentra definido los detalles de la actualización a efectuar (tipo, modo, definición de parámetros, recursos necesarios). 

#### Parámetros
Valores necesarios de configuración de la terminal para poder operar satisfactoriamente con la herramienta.

#### Novedades
Mensaje que contiene la información o donde obtener la información de la actualización a aplicar en la terminal.


## Documentation Scope

Los sistemas de terceros se integran con Terminals Mangement a través de una API.

El presente documento del protocolo de la API de Terminals Management especifica el protocolo de interfaz de mantenimiento, el cual lista un conjunto de mensajes para ayudar al mantenimiento y soporte de una red de terminales; por ejemplo, verificar el estado de las terminales mediante un mensaje denominado KeepAlive, obtener novedades para las terminales registradas en la herramienta y el reporte de parámetros actuales.

## Scope

Version 1.0 of this document covers a particular version of ATIONet’s Loyalty Host protocol. Although feature’s descriptions are generally not related to a particular version of the protocol, some changes may apply which would be specifically commented and identified on each feature’s
description paragraph.

### Scope Details

**Protocol:** ATIONet Native Transaction Protocol

**Version:** Version 1.0

**API URI:** native.ationet.com/v1/loyalty

### Messages

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
				<p align="left">Accumulation</p>
			</td>
			<td>
				<p align="center">1.0</p>
			</td>
			<td></td>
			<td>
				<p align="left">Used to post a credit to the affiliate's account.</p>
			</td>
		 </tr>
		 <tr valign="top">
			<td>
				<p align="left">Redemption</p>
			</td>
			<td>
				<p align="center">1.0</p>
			</td>
			<td></td>
			<td>
				<p align="left">Informs a debit to the affiliate's account.</p>
			</td>
		 </tr>
		 <tr valign="top">
			<td>
				<p align="left">Enquiry</p>
			</td>
			<td>
				<p align="center">1.0</p>
			</td>
			<td></td>
			<td>
				<p align="left">Retrieves affiliate's current balance.</p>
			</td>
		 </tr>
		 <tr valign="top">
			<td>
				<p align="left">Transfer</p>
			</td>
			<td>
				<p align="center">1.0</p>
			</td>
			<td></td>
			<td>
				<p align="left">Grants points from one loyalty account to another one</p>
			</td>
		 </tr>
		 <tr valign="top">
			<td>
				<p align="left">Adjustments</p>
			</td>
			<td>
				<p align="center">1.0</p>
			</td>
			<td></td>
			<td>
				<p align="left">Posts a positive or negative (credit or debit) discretionary movement to an affiliate's account</p>
			</td>
		 </tr>
	</tbody>
</table>

## Data Security

To validate the source of transactions and data encryption, the ATIONet Native Transaction Protocol relies on a SSL connection between the Site’s Terminal or Site’s Controller and the ATIONet Host. The SSL connection is established for each request/response pair, using a certificate property of ATIONet, meaning that each request must include a system-type user and password on the Header. The user will be matched against the related ATIONet actor for each message.

Users to be used on the Transaction Protocol messaging will be created by authorized users via ATIONet Console, with the role “Controller/Terminal”.

At this time there is no provisioning to distribute or update certificates or thumbprints thru a system interface. This information will be provided at request of the Controller’s vendor during the integration project.

## Message Structure

All Transaction API messages share the same structure, what change from message to message are the Transaction Code, which indicates the actual transaction function, the value fields sent and received, and the HTTP action (POST, GET, REQUEST) which changes depending on the Transaction Code.

Both, requests and responses use a JSON format.

Only one request is accepted on each message.

### Request Format

*Header:*

	Accept-Encoding: gzip

	Authorization: Basic user:password

*Body:*
	{“Fieldname”:”StringValue”,”FieldName”:”StringValue”,”FieldName”:Value}

### Response

*Header:*

	Content-Type: application/json; charset=utf-8

*Body:*
	{“Fieldname”:”StringValue”,”FieldName”:”StringValue”,”FieldName”:Value}

Note: Alphanumeric fields, stated as Type “A/N” in record format tables below show the maximum possible length as the Size, although in JSON-formatted strings they will be represented with trailing spaces trimmed.

## Error Handling

Success/failure exits on the Native Transaction Protocol will be handled via HTTP status codes.

Successful request will get a HTTP 200 and the resulting response.

Transactions intended to post a command, for example Authorizations and Pre-Authorizations will return a single JSON-formatted item with the “Response Code” and “Response Text”. The body of these responses will never be empty.

Failure to process the request will be indicated by an HTTP 400’s range status code. The body will contain a single JSON-formatted item with the “ResponseCode”, “ResponseMessage” and “ResponseError” fields.

Refer to Response Codes Table in the Reference Tables section for a complete list of supported codes.

## Field Descriptions

This section details the purpose and expected behavior on the Controller system for relevant items on the protocol.

#### System Model and System Version
Brand/Model and Firmware/Software version of the client system. Format and content will be assigned for each vendor during the Integration project.

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

There are two Tracks fields, the Primary and Secondary.
Primary track is mandatory and the only one used on all messages except for the Transfer request. In the Transfer request, the Primary Track is the origin account (gets the debit movement) and the Secondary Track identifies the destination account (gets the credit movement).

#### Batch Number
Optional information, if informed, ATIONet will use this field for report filtering and queries.

If used, data must be formatted as an 11 digit number: yyyymmddbbb. Year (4 digits), Month (2 digits), Day (2 digits), Batch/Shift number (3 digits, padded with zeros). Date part must be the starting date of the batch. Batch number must wrap-around to 1 after reaching 999.

If there is no batch functionality at all, the recommended format is Transaction Date plus 3 zeros.

#### Shift Number
Optional information, if informed, ATIONet will use this field for report filtering and queries.

The Controller application can manage the Shift Number and meaning as needed. It may be day’s shift number, weekly batches, split-batches, etc., although this is a fixed length field, therefore the format must be maintained.

If there is no batch or shift functionality at all, the recommended format is the business date of the transaction followed of 3 zeros.

#### Customer Data
Customer data on a LREQ contains extra information gathered from prompts to the Cardholder or Attendant. On a LRESP, it contains the list of prompts that must be presented to the Cardholder or Attendant or a list of values to be used by the Terminal at capture, transaction or receipt printing.

#### Authorization Code
The Host will return the Authorization Code on all approved transactions.
On Pre-Authorization/Completions message flows, the Controller must keep the Authorization Code sent on the Pre-Authorization LRESP and send it
back to the Host on the Completion LREQ. This is a mandatory feature.

Refer to Authorization Codes Table in the Reference Tables section for a complete list of supported codes.

## Loyalty Transaction Request (LREQ) Message Format

<table>
	<thead>
		<tr valign="top">
			<th align="left">
				Field Name
			</th>
			<th align="left">
				Size
			</th>
			<th align="left">
				Type
			</th>
			<th align="left">
				Condition
			</th>
			<th align="left">
				Descriptions/Field Value(s)
			</th>
		</tr>
	</thead>
	<tbody>
		<tr valign="top">
			<td>
				<p align="left">ApplicationType</p>
			</td>
			<td>
				<p align="left">4</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">Required</p>
			</td>
			<td>
				<p align="left">Always “LTY” Loyalty System</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ProcessingMode</p>
			</td>
			<td>
				<p align="left">1</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">Required</p>
			</td>
			<td>
				<p align="left">“0” = Host Capture Only
				<br>“1” = Host Processing Required
				<br>“2” = Operator Assisted Capture</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">MessageFormatVersion</p>
			</td>
			<td>
				<p align="left">3</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">Required</p>
			</td>
			<td>
				<p align="left">Current Host Message Version = “1.0”</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">TerminalIdentification</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">Required</p>
			</td>
			<td>
				<p align="left">Terminal Identification</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">DeviceTypeIdentifier</p>
			</td>
			<td>
				<p align="left">1</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">Required</p>
			</td>
			<td>
				<p align="left">“1” = Indoor Payment Terminal
				<br>“2” = Outdoor Payment Terminal
				<br>“3” = Card Reader in Dispenser
				<br>“4” = Other Self-Service</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SystemModel</p>
			</td>
			<td>
				<p align="left">10</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">Required</p>
			</td>
			<td>
				<p align="left">Refer to System Model and System Version in Field Description section</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SystemVersion</p>
			</td>
			<td>
				<p align="left">10</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">Required</p>
			</td>
			<td>
				<p align="left">Refer to System Model and System Version in Field Description section</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">TransactionCode</p>
			</td>
			<td>
				<p align="left">3</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">Required</p>
			</td>
			<td>
				<p align="left">Refer to Transaction Codes in Reference Tables Section</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">AccountType</p>
			</td>
			<td>
				<p align="left">1</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">Required</p>
			</td>
			<td>
				<p align="left">Refer to Account Types in Reference Tables Section</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">EntryMethod</p>
			</td>
			<td>
				<p align="left">1</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">Required</p>
			</td>
			<td>
				<p align="left">“M” Manual Entry
				<br>“S” Swap Card
				<br>“T” Tag read</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ServiceCode</p>
			</td>
			<td>
				<p align="left">1</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">Reserved for future use</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">TransactionData</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">String<PurchaseData></p>
			</td>
			<td>
				<p align="left">Conditional</p>
			</td>
			<td>
				<p align="left">Refer to Accumulation section</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CustomerData</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">Dictionary<string, string></p>
			</td>
			<td>
				<p align="left">Conditional</p>
			</td>
			<td>
				<p align="left">Refer to Customer Data in Field Description section</p>
			</td>
		</tr>

		<tr valign="top">
			<td>
				<p align="left">TransactionAmount</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">decimal, signed</p>
			</td>
			<td>
				<p align="left">Conditional</p>
			</td>
			<td>
				<p align="left">xxxxxxx.xx </br> Refer to Accumulation section</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">LoyaltyPoints</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">decimal, signed</p>
			</td>
			<td>
				<p align="left">Conditional</p>
			</td>
			<td>
				<p align="left">xxxxxxx.xx </br> Refer to Fields description section</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CurrencyCode</p>
			</td>
			<td>
				<p align="left">3</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">Refer to Currency Codes in Reference Tables Section</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">BatchNumber</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">int</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">Refer to Batch Number in Field Description section</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ShiftNumber</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">Refer to Shift Number in Field Description section</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">TransactionSequenceNumber</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">int</p>
			</td>
			<td>
				<p align="left">Required</p>
			</td>
			<td>
				<p align="left">Refer to Transaction Sequence Number in Field Description section</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">LocalTransactionDate</p>
			</td>
			<td>
				<p align="left">8</p>
			</td>
			<td>
				<p align="left">int</p>
			</td>
			<td>
				<p align="left">Required</p>
			</td>
			<td>
				<p align="left">Local Transaction Date: yyyymmdd</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">LocalTransactionTime</p>
			</td>
			<td>
				<p align="left">6</p>
			</td>
			<td>
				<p align="left">int</p>
			</td>
			<td>
				<p align="left">Required</p>
			</td>
			<td>
				<p align="left">Local Transaction Time: hhmmss</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">PrimaryTrack</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">Required</p>
			</td>
			<td>
				<p align="left">Refer to Track Data in Field Description section</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SecondaryTrack</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">Required</p>
			</td>
			<td>
				<p align="left">Refer to Track Data in Field Description section</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">InvoiceNumber</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
	</tbody>
</table>	
  
## Loyalty Transaction Response (LRESP) Message Format

<table>
	<thead>
		<tr valign="top">
			<th align="left">
				Field Name
			</th>
			<th align="left">
				Size
			</th>
			<th align="left">
				Type
			</th>
			<th align="left">
				Condition
			</th>
			<th align="left">
				Descriptions/Field Value(s)
			</th>
		</tr>
	</thead>
	<tbody>
		<tr valign="top">
			<td>
				<p align="left">ApplicationType</p>
			</td>
			<td>
				<p align="left">3</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">Required</p>
			</td>
			<td>
				<p align="left">Echoed from LREQ</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ProcessingMode</p>
			</td>
			<td>
				<p align="left">1</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">Required</p>
			</td>
			<td>
				<p align="left">Echoed from LREQ</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">MessageFormatVersion</p>
			</td>
			<td>
				<p align="left">3</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">Required</p>
			</td>
			<td>
				<p align="left">Echoed from LREQ</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">TerminalIdentification</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">Required</p>
			</td>
			<td>
				<p align="left">Echoed from LREQ</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">DeviceTypeIdentifier</p>
			</td>
			<td>
				<p align="left">1</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">Required</p>
			</td>
			<td>
				<p align="left">Echoed from LREQ</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">TransactionCode</p>
			</td>
			<td>
				<p align="left">3</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">Required</p>
			</td>
			<td>
				<p align="left">Refer to Transaction Codes in Reference Tables Section</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">AccountType</p>
			</td>
			<td>
				<p align="left">1</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">Required</p>
			</td>
			<td>
				<p align="left">Echoed from LREQ</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">EntryMethod</p>
			</td>
			<td>
				<p align="left">1</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">Required</p>
			</td>
			<td>
				<p align="left">Echoed from LREQ</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">TransactionAmount</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">decimal</p>
			</td>
			<td>
				<p align="left">Conditional</p>
			</td>
			<td>
				<p align="left">xxxxxxx.xx</p>
			</td>
		</tr>		
		<tr valign="top">
			<td>
				<p align="left">CurrencyCode</p>
			</td>
			<td>
				<p align="left">3</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">Refer to Currency Codes in Reference Tables Section</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">BatchNumber</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">int</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">Echoed from LREQ</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ShiftNumber</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">Echoed from LREQ</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">TransactionSequenceNumber</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">int</p>
			</td>
			<td>
				<p align="left">Required</p>
			</td>
			<td>
				<p align="left">Echoed from LREQ</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">LocalTransactionDate</p>
			</td>
			<td>
				<p align="left">8</p>
			</td>
			<td>
				<p align="left">int</p>
			</td>
			<td>
				<p align="left">Required</p>
			</td>
			<td>
				<p align="left">Echoed from LREQ</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">LocalTransactionTime</p>
			</td>
			<td>
				<p align="left">6</p>
			</td>
			<td>
				<p align="left">int</p>
			</td>
			<td>
				<p align="left">Required</p>
			</td>
			<td>
				<p align="left">Echoed from LREQ</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">AuthorizationCode</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">Conditional</p>
			</td>
			<td>
				<p align="left">Refer to Authorization Code in Field Description section</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">InvoiceNumber</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">LoyaltyPoints</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">Conditional</p>
			</td>
			<td>
				<p align="left">Refer to Fields description section</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">AfterBalance</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">decimal</p>
			</td>
			<td>
				<p align="left">Conditional</p>
			</td>
			<td>
				<p align="left">xxxxxxx.xx</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ReceiptData</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">Conditional</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ResponseCode</p>
			</td>
			<td>
				<p align="left">5</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">Required</p>
			</td>
			<td>
				<p align="left">“0” = Authorized, !”0” = Not Authorized</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ResponseText</p>
			</td>
			<td>
				<p align="left">20</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">Required</p>
			</td>
			<td>
				<p align="left">Message from the Network</p>
			</td>
		</tr>
	</tbody>
</table>


## Reference Tables

This section brings together the code tables and reference values used in messaging.

### Transaction Codes

<table>
	<thead>
		<tr valign="top">
			<th align="left">
				Code
			</th>
			<th align="left">
				Message
			</th>
			<th align="left">
				Description
			</th>
		</tr>
	</thead>
	<tbody>
		<tr valign="top">
			<td>
				<p align="left">“510”</p>
			</td>
			<td>
				<p align="left">LREQ</p>
			</td>
			<td>
				<p align="left">Accumulation REQ</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">“511”</p>
			</td>
			<td>
				<p align="left">LRESP</p>
			</td>
			<td>
				<p align="left">Accumulation RESP</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">“520”</p>
			</td>
			<td>
				<p align="left">LREQ</p>
			</td>
			<td>
				<p align="left">Redemption REQ</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">“521”</p>
			</td>
			<td>
				<p align="left">LRESP</p>
			</td>
			<td>
				<p align="left">Redepmtion RESP</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">“530”</p>
			</td>
			<td>
				<p align="left">LREQ</p>
			</td>
			<td>
				<p align="left">Balance Enquiry REQ</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">“531”</p>
			</td>
			<td>
				<p align="left">LRESP</p>
			</td>
			<td>
				<p align="left">Balance Enquiry RESP</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">“540”</p>
			</td>
			<td>
				<p align="left">LREQ</p>
			</td>
			<td>
				<p align="left">Transfer REQ</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">“541”</p>
			</td>
			<td>
				<p align="left">LRESP</p>
			</td>
			<td>
				<p align="left">Transfer RESP</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">“550”</p>
			</td>
			<td>
				<p align="left">LREQ</p>
			</td>
			<td>
				<p align="left">Adjustment REQ</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">“551”</p>
			</td>
			<td>
				<p align="left">LRESP</p>
			</td>
			<td>
				<p align="left">Adjustment RESP</p>
			</td>
		</tr>
	</tbody>
</table>
	
### Account Type

<table>
	<thead>
		<tr valign="top">
			<th align="left">
				Type
			</th>
			<th align="left">
				Description
			</th>
		</tr>
	</thead>
	<tbody>
		<tr valign="top">
			<td>
				<p align="left">“2”</p>
			</td>
			<td>
				<p align="left">ATIONet native loyalty track</p>
			</td>
		</tr>
	</tbody>
</table>	

### Transaction Data Structure

<table>
	<thead>
		<tr valign="top">
			<th align="left">
				Field Name
			</th>
			<th align="left">
				Size
			</th>
			<th align="left">
				Type
			</th>
			<th align="left">
				Condition
			</th>
			<th align="left">
				Descriptions/Field Value(s)
			</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td colspan="5" align="left">
				Product List section (one per product in transaction)
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ServiceCode</p>
			</td>
			<td>
				<p align="left">1</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>	
				<p align="left">Required</p>
			</td>
		</tr>
		<tr valign="top">
			<td>    
				<p align="left">ProductCode</p>
			</td>
			<td>	
				<p align="left">4</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">Required</p>
			</td>
			<td>
				<p align="left">“0”-“9999”</p>
			</td>
		</tr>
		<tr valign="top">		
			<td>	
				<p align="left">ProductUnitPrice</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">decimal</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">xxx.xxx</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ProductNetAmount</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">decimal</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">xxxxxxx.xx</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ProductTaxes</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">Dictionary<string, decimal></p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left"><”[Tax Description]”, [Tax Value]></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ProductAmount</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">decimal</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">xxxxxxx.xx</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ProductQuantity</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">decimal</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">xxxxxxx.xx</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">UnitCode</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">Refer to Measurement Unit Codes in Reference Tables Section</p>
			</td>
		</tr>
		<tr>
			<td colspan="5" align="left">
				Method-of-Payment List section (one per MoP in transaction)
			</td>
		</tr>
		<tr valign="top">
			<td>    
				<p align="left">MoPCode</p>
			</td>
			<td>	
				<p align="left">4</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">Required</p>
			</td>
			<td>
				<p align="left">“0”-“9999”</p>
			</td>
		</tr>
		<tr valign="top">		
			<td>	
				<p align="left">Amount</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">decimal</p>
			</td>
			<td>
				<p align="left">Required</p>
			</td>
			<td>
				<p align="left">xxxx.xx</p>
			</td>
		</tr>
	</tbody>
</table>	
			
### Customer Data
    
*Prompt elements*
<table>
	<thead>
		<tr valign="top">
			<th align="left">
				Field Name
			</th>
		</tr>
	</thead>
	<tbody>
		<tr valign="top">
			<td>
				<p align="left">PromptOdometer</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">PromptMiscellaneous</p>
			</td>
		</tr>
	</tbody>
</table>	

### Currency Codes
 
Refer to ISO 4217 Currency Codes standard (<http://en.wikipedia.org/wiki/ISO_4217>)

### Authorization Codes

<table>
	<thead>
		<tr valign="top">
			<th align="left">
				ResponseCode
			</th>
			<th align="left">
				ResponseMessage
			</th>
		</tr>
	</thead>
	<tbody>
		<tr valign="top">
			<td>
				<p align="left">00000</p>
			</td>
			<td>
				<p align="left">Authorized</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left"><b>Validations</b></p>
			</td>
			<td></td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10000</p>
			</td>
			<td>
				<p align="left">Date Invalid</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10001</p>
			</td>
			<td>
				<p align="left">Time Invalid</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10002</p>
			</td>
			<td>
				<p align="left">Seq Num Invalid</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10003</p>
			</td>
			<td>
				<p align="left">Term does not exist</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10004</p>
			</td>
			<td>
				<p align="left">Netw does not exist</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10005</p>
			</td>
			<td>
				<p align="left">Id does not exist</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10006</p>
			</td>
			<td>
				<p align="left">SecId does not exist</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10007</p>
			</td>
			<td>
				<p align="left">Fuel does not exist</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10008</p>
			</td>
			<td>
				<p align="left">Merch not found</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10009</p>
			</td>
			<td>
				<p align="left">Site not found</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10010</p>
			</td>
			<td>
				<p align="left">Prot not found</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10011</p>
			</td>
			<td>
				<p align="left">TType not found</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10012</p>
			</td>
			<td>
				<p align="left">Comp not found</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10013</p>
			</td>
			<td>
				<p align="left">Contr not found</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10014</p>
			</td>
			<td>
				<p align="left">Subacc not found</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10015</p>
			</td>
			<td>
				<p align="left">SecSubacc not found</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10016</p>
			</td>
			<td>
				<p align="left">Empty subaccount</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10017</p>
			</td>
			<td>
				<p align="left">Empty sec subaccount</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10018</p>
			</td>
			<td>
				<p align="left">Ids both veh</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10019</p>
			</td>
			<td>
				<p align="left">Ids both driv</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10020</p>
			</td>
			<td>
				<p align="left">Subacc in diff cont</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10021</p>
			</td>
			<td>
				<span lang=EN-US style='color:black'>Dri or Veh not found</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10022</p>
			</td>
			<td>
				<p align="left">Id is not active</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10023</p>
			</td>
			<td>
				<p align="left">SecId is not active</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10024</p>
			</td>
			<td>
				<p align="left">Id has expired</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10025</p>
			</td>
			<td>
				<p align="left">SecId has expired</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10026</p>
			</td>
			<td>
				<p align="left">Vehicle not enabled</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10027</p>
			</td>
			<td>
				<p align="left">Driver not enabled</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10028</p>
			</td>
			<td>
				<p align="left">Contract has expired</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10029</p>
			</td>
			<td>
				<p align="left">Site not in contr</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10030</p>
			</td>
			<td>
				<p align="left">Fuel not in contr</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10031</p>
			</td>
			<td>
				<p align="left">Fuel not in vehclas</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10032</p>
			</td>
			<td>
				<p align="left">Driver not related</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10033</p>
			</td>
			<td>
				<p align="left">Vehicle not related</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10034</p>
			</td>
			<td>
				<p align="left">Sec Track needed</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10035</p>
			</td>
			<td>
				<p align="left">Fuel needed</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10036</p>
			</td>
			<td>
				<p align="left">Fuel mapping needed</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10037</p>
			</td>
			<td>
				<p align="left">Already completed</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10038</p>
			</td>
			<td>
				<p align="left">NetComp not found</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10039</p>
			</td>
			<td>
				<p align="left">NetMerch not found</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10040</p>
			</td>
			<td>
				<p align="left">Auth does not exists</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10041</p>
			</td>
			<td>
				<p align="left">Auth not authorized</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10042</p>
			</td>
			<td>
				<p align="left">Auth with diff fuel</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10043</p>
			</td>
			<td>
				<p align="left">Auth with diff PPU</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10044</p>
			</td>
			<td>
				<p align="left">Auth amount exceeded</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10045</p>
			</td>
			<td>
				<p align="left">Auth qty exceeded</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10046</p>
			</td>
			<td>
				<p align="left">Auth with diff id</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10047</p>
			</td>
			<td>
				<p align="left">Auth with diff secid</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10048</p>
			</td>
			<td>
				<p align="left">Auth with diff term</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10049</p>
			</td>
			<td>
				<p align="left">Auth with diff netw</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10050</p>
			</td>
			<td>
				<p align="left">Auth with diff merch</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10051</p>
			</td>
			<td>
				<p align="left">Auth with diff nwmr</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10052</p>
			</td>
			<td>
				<p align="left">Auth with diff site</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10053</p>
			</td>
			<td>
				<p align="left">Auth with diff prot</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10054</p>
			</td>
			<td>
				<p align="left">Auth with diff tt</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10055</p>
			</td>
			<td>
				<p align="left">Auth with diff comp</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10056</p>
			</td>
			<td>
				<p align="left">Auth with diff nwcp</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10057</p>
			</td>
			<td>
				<p align="left">Auth with diff contr</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10058</p>
			</td>
			<td>
				<p align="left">Auth with diff subacc</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10059</p>
			</td>
			<td>
				<span lang=EN-US style='color:black'>Auth with diff sec sa</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10060</p>
			</td>
			<td>
				<p align="left">Auth with diff vehicle</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10061</p>
			</td>
			<td>
				<p align="left">Auth with diff driver</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10062</p>
			</td>
			<td>
				<p align="left">Proc Code Not Supp</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10063</p>
			</td>
			<td>
				<p align="left">TType qty exceded</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10064</p>
			</td>
			<td>
				<p align="left">TType amount exceded</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">10065</p>
			</td>
			<td>
				<p align="left">Tag PIN Invalid</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left"><b>LocationRule</b></p>
			</td>
			<td></td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40100</p>
			</td>
			<td>
				<p align="left">Site not authorized</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40101</p>
			</td>
			<td>
				<p align="left">Site not authorized</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40102</p>
			</td>
			<td>
				<p align="left">Site not authorized</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40103</p>
			</td>
			<td>
				<p align="left">Site not authorized</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left"><b>FuelRule</b></p>
			</td>
			<td></td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40200</p>
			</td>
			<td>
				<p align="left">Product not authorized</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40201</p>
			</td>
			<td>
				<p align="left">Product not authorized</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40202</p>
			</td>
			<td>
				<p align="left">Product not authorized</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40203</p>
			</td>
			<td>
				<p align="left">Product not authorized</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left"><b>TransactionRule</b></p>
			</td>
			<td></td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">20300</p>
			</td>
			<td>
				<p align="left">Quota not set</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40300</p>
			</td>
			<td>
				<p align="left">Veh money excedeed</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40301</p>
			</td>
			<td>
				<p align="left">Driv money excedeed</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40302</p>
			</td>
			<td>
				<p align="left">Prod money excedeed</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40303</p>
			</td>
			<td>
				<p align="left">Site money excedeed</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40304</p>
			</td>
			<td>
				<p align="left">Fleet money excedeed</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40305</p>
			</td>
			<td>
				<p align="left">Veh fuel excedeed</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40306</p>
			</td>
			<td>
				<p align="left">Driv fuel excedeed</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40307</p>
			</td>
			<td>
				<p align="left">Prod fuel excedeed</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40308</p>
			</td>
			<td>
				<p align="left">Site fuel excedeed</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40309</p>
			</td>
			<td>
				<p align="left">Fleet fuel excedeed</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left"><b>QuotaRule</b></p>
			</td>
			<td></td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">20400</p>
			</td>
			<td>
				<p align="left">Quota not set</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40400</p>
			</td>
			<td>
				<p align="left">Veh money excedeed</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40401</p>
			</td>
			<td>
				<p align="left">Driv money excedeed</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40402</p>
			</td>
			<td>
				<p align="left">Prod money excedeed</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40403</p>
			</td>
			<td>
				<p align="left">Site money excedeed</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40404</p>
			</td>
			<td>
				<p align="left">Fleet money excedeed</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40405</p>
			</td>
			<td>
				<p align="left">Veh fuel excedeed</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40406</p>
			</td>
			<td>
				<p align="left">Driv fuel excedeed</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40407</p>
			</td>
			<td>
				<p align="left">Prod fuel excedeed</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40408</p>
			</td>
			<td>
				<p align="left">Site fuel excedeed</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40409</p>
			</td>
			<td>
				<p align="left">Fleet fuel excedeed</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40410</p>
			</td>
			<td>
				<p align="left">Veh tran excedeed</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40411</p>
			</td>
			<td>
				<p align="left">Driv tran excedeed</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40412</p>
			</td>
			<td>
				<p align="left">Prod tran excedeed</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40413</p>
			</td>
			<td>
				<p align="left">Site tran excedeed</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40414</p>
			</td>
			<td>
				<p align="left">Fleet tran excedeed</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left"><b>PromptingRule</b></p>
			</td>
			<td></td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">20500</p>
			</td>
			<td>
				<p align="left">Retries exceded</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40500</p>
			</td>
			<td>
				<p align="left">Prompting needed</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40501</p>
			</td>
			<td>
				<p align="left">Pri PIN needed</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40502</p>
			</td>
			<td>
				<p align="left">Sec PIN needed</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40503</p>
			</td>
			<td>
				<p align="left">Pri PIN invalid</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40504</p>
			</td>
			<td>
				<p align="left">Sec PIN invalid</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left"><b>DaysRule</b></p>
			</td>
			<td></td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">20600</p>
			</td>
			<td>
				<p align="left">Week days not set</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40600</p>
			</td>
			<td>
				<p align="left">Day not authorized</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40601</p>
			</td>
			<td>
				<p align="left">Day not authorized</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40602</p>
			</td>
			<td>
				<p align="left">Day not authorized</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40603</p>
			</td>
			<td>
				<p align="left">Day not authorized</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40604</p>
			</td>
			<td>
				<p align="left">Day not authorized</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left"><b>DateTimeRule</b></p>
			</td>
			<td></td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">20700</p>
			</td>
			<td>
				<p align="left">DateTime not set</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40700</p>
			</td>
			<td>
				<p align="left">DateTime not auth</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40701</p>
			</td>
			<td>
				<p align="left">DateTime not auth</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40702</p>
			</td>
			<td>
				<p align="left">DateTime not auth</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40703</p>
			</td>
			<td>
				<p align="left">DateTime not auth</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40704</p>
			</td>
			<td>
				<p align="left">DateTime not auth</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40705</p>
			</td>
			<td>
				<p align="left">DateTime not auth</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40706</p>
			</td>
			<td>
				<p align="left">DateTime not auth</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40707</p>
			</td>
			<td>
				<p align="left">DateTime not auth</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40708</p>
			</td>
			<td>
				<p align="left">DateTime not auth</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40709</p>
			</td>
			<td>
				<p align="left">DateTime not auth</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40710</p>
			</td>
			<td>
				<p align="left">DateTime not auth</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40711</p>
			</td>
			<td>
				<p align="left">DateTime not auth</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40712</p>
			</td>
			<td>
				<p align="left">DateTime not auth</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40713</p>
			</td>
			<td>
				<p align="left">DateTime not auth</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40714</p>
			</td>
			<td>
				<p align="left">DateTime not auth</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40715</p>
			</td>
			<td>
				<p align="left">DateTime not auth</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40716</p>
			</td>
			<td>
				<p align="left">DateTime not auth</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40717</p>
			</td>
			<td>
				<p align="left">DateTime not auth</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40718</p>
			</td>
			<td>
				<p align="left">DateTime not auth</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40719</p>
			</td>
			<td>
				<p align="left">DateTime not auth</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40720</p>
			</td>
			<td>
				<p align="left">DateTime not auth</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40721</p>
			</td>
			<td>
				<p align="left">DateTime not auth</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40722</p>
			</td>
			<td>
				<p align="left">DateTime not auth</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40723</p>
			</td>
			<td>
				<p align="left">DateTime not auth</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40724</p>
			</td>
			<td>
				<p align="left">DateTime not auth</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40725</p>
			</td>
			<td>
				<p align="left">DateTime not auth</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40726</p>
			</td>
			<td>
				<p align="left">DateTime not auth</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40727</p>
			</td>
			<td>
				<p align="left">DateTime not auth</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40728</p>
			</td>
			<td>
				<p align="left">DateTime not auth</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40729</p>
			</td>
			<td>
				<p align="left">DateTime not auth</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left"><b>DaysTimeRule</b></p>
			</td>
			<td></td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">20800</p>
			</td>
			<td>
				<p align="left">Week days not set</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">20801</p>
			</td>
			<td>
				<p align="left">Time not set</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40800</p>
			</td>
			<td>
				<p align="left">Day not authorized</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40801</p>
			</td>
			<td>
				<p align="left">Day not authorized</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40802</p>
			</td>
			<td>
				<p align="left">Day not authorized</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40803</p>
			</td>
			<td>
				<p align="left">Day not authorized</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40804</p>
			</td>
			<td>
				<p align="left">Day not authorized</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40805</p>
			</td>
			<td>
				<p align="left">DaysTime not auth</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40806</p>
			</td>
			<td>
				<p align="left">DaysTime not auth</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40807</p>
			</td>
			<td>
				<p align="left">DaysTime not auth</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40808</p>
			</td>
			<td>
				<p align="left">DaysTime not auth</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40809</p>
			</td>
			<td>
				<p align="left">DaysTime not auth</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40810</p>
			</td>
			<td>
				<p align="left">DaysTime not auth</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40811</p>
			</td>
			<td>
				<p align="left">DaysTime not auth</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40812</p>
			</td>
			<td>
				<p align="left">DaysTime not auth</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40813</p>
			</td>
			<td>
				<p align="left">DaysTime not auth</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40814</p>
			</td>
			<td>
				<p align="left">DaysTime not auth</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left"><b>EstablishLimits</b></p>
			</td>
			<td></td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">20900</p>
			</td>
			<td>
				<p align="left">Unit price needed</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">20901</p>
			</td>
			<td>
				<p align="left">Max quota not set</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40900</p>
			</td>
			<td>
				<p align="left">CA quota exceeded</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40901</p>
			</td>
			<td>
				<p align="left">Offline lim exceeded</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left"><b>Warnings</b></p>
			</td>
			<td>
				<p align="left">&nbsp;</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">30000</p>
			</td>
			<td>
				<p align="left">Pim Track not match</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">30001</p>
			</td>
			<td>
				<p align="left">Sec Track not match</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">30002</p>
			</td>
			<td>
				<p align="left">Fuels not match</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">30003</p>
			</td>
			<td>
				<p align="left">PPU not match</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left"><b>AplicationError</b></p>
			</td>
			<td></td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">50000</p>
			</td>
			<td>
				<p align="left">App Error</p>
			</td>
		</tr>	
	</tbody>
</table>

### Response Codes

<table>
	<thead>
		<tr valign="top">
			<th align="left">
				ResponseCode
			</th>
			<th align="left">
				ResponseMessage
			</th>
		</tr>
	</thead>
	<tbody>
		<tr valign="top">
			<td>
				<p align="left">00000</p>
			</td>
			<td>
				<p align="left">Operation Succeeded</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40000</p>
			</td>
			<td>
				<p align="left">Invalid Identification Data</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40001</p>
			</td>
			<td>
				<p align="left">Invalid Filter Data</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40002</p>
			</td>
			<td>
				<p align="left">User not allowed to use this action</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40003</p>
			</td>
			<td>
				<p align="left">Invalid Action Code</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40004</p>
			</td>
			<td>
				<p align="left">Invalid user name or password</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">40005</p>
			</td>
			<td>
				<p align="left">Movement not allowed</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">50000</p>
			</td>
			<td>
				<p align="left">Internal Server Error</p>
			</td>
		</tr>
	</tbody>
</table>
