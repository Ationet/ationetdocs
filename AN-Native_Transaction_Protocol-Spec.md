![ationetlogo](Content/Images/ATIOnetLogo_250x70.png)
# ATIONet - Native Transaction Protocol Specification v1.2 #

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
			ATIONet-Native_Transaction_Protocol-Spec-v1.2
		</td>
	</tr>
	<tr>
		<td>
			Doc Version:
		</td>
		<td>
			1.2
		</td>
	</tr>
	<tr>
		<td>
			Release Date:
		</td>
		<td>
			16, July 2014
		</td>
	</tr>
	<tr>
		<td>
			Author:
		</td>
		<td>
			ATIO International LLC
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
			<p>04/Jan/2013</p>
		</td>
		<td>
			<p>Initial version. Covers Fleet Fueling Transactions. No Dry products support.</p>
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>1.1</p>
		</td>
		<td>
			<p>05/Jan/2013</p>
		</td>
		<td>
			<p>1.1  Protocol version changes
			<br> - Enhanced Limits explanation
			<br> - Converted message format to JSON</p>
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>1.2</p>
		</td>
		<td>
			<p>17/July/2014</p>
		</td>
		<td>
			<p>1.2  Protocol version changes
			<br> - Add contingency request
			<br> - Add sale request
			<br> - Add cancellation request
			<br> - Enhanced Customer Data and Product Data fields description
			<br> - Add Original Data Field in TREQ messages
			<br> - Enhanced Transaction Codes table
			<br> - Enhanced Customer Data and Product reference tables
			<br> - Add Authorization Codes table
			<br> - Add Response Codes table
			<br> - Add Original Data tables</p>	
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>1.3</p>
		</td>
		<td>
			<p>5/Dec/2017</p>
		</td>
		<td>
			<p>1.3  Protocol version changes
			<br> - Update Response Codes table </p>	
		</td>
	</tr>
</table>

## Contents ##

- [1 ATIOnet Integration Documentation Scope](#1-ationet-integration-documentation-scope)

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
	= [Original Data](#original-data)

- [7 Transaction Request (TREQ) Message Format](#7-transaction-request-treq-message-format)

- [8 Transaction Response (TRESP) Message Format](#8-transaction-response-tresp-message-format)

- [9 Satellite TAG Validation Request (VREQ) Message Format](#9-satellite-tag-validation-request-vreq-message-format)

- [10 Satellite TAG Validation Response (VRESP) Message Format](#10-satellite-tag-validation-response-vresp-message-format)

- [11 Reference Tables](#11-reference-tables)
	- [11.1 Transaction Codes](#111-transaction-codes)
	- [11.2 Account Type](#112-account-type)
	- [11.3 Product Data Structure](#113-product-data-structure)
	- [11.4 Customer Data](#114-customer-data)
	- [11.5 Measurement Unit Codes](#115-measurement-unit-codes)
	- [11.6 Currency Codes](#116-currency-codes)
	- [11.7 Authorization Codes](#117-authorization-codes)
	- [11.8 Response Codes](#118-response-codes)
	- [11.9 Original Data](#119-original-data)
- [Appendix A - Native Authorization Protocol Messages](#appendix-a---native-authorization-protocol-messages)

## Overview

### Introduction

This specification is intended to document ATIONet’s Native Protocol messaging format and related features required for the systems applying for integration with ATIONet. The following sections provide descriptions of the messages themselves, the expected behaviour for each supported transaction type and a common ground for the functionality of each relevant item.

### Definitions

#### Host
A computer system that is accessed by a user working at a remote location. In this document, Host is always the ATIONet Host.

#### Terminal
An electronic merchant card processing device responsible for transaction capture, display output to the cashier and/or to the cardholder on screen and/or print format.

#### Controller
A client system that can send or receive data to and from ATIONet’s Host. A Controller controls or includes one or more terminal. When there is only one Terminal connected to a Controller, Terminal and Controller are equivalent.

#### TREQ
Transaction Request.

#### TRESP
Transaction Response.

## 1 ATIOnet Integration Documentation Scope

Third-party systems integrate with ATIOnet via a set of APIs (Application Programming Interfaces). Each ATIOnet’s API is described on a separate Protocol Specification. The complete documentation of ATIOnet API’s is comprised of:

#### ATIOnet Native Transactions Protocol Specification: 
Covers financial transactions for transaction capture systems (payment terminals, site controllers and point of sale systems), including sales and refunds.

#### ATIOnet Administrative Transactions Protocol Specification: 
Describes a set of functions complementing the transaction-capture business, for example Batch or Shift Close. These functions enhance the capabilities of the integration but their implementation is not mandatory.

#### ATIOnet Native Interface Protocol Specification: 
Covers system-to-system integration capabilities of ATIOnet, designed to interact with third-party back-end systems, for example downloading transactions data or sending current-accounts movements to ATIOnet. This API is reserved and requires ATIOnet and Subscriber permissions.

#### ATIOnet Maintenance Interface Protocol Specification: 
List a set of functions designed to help in the maintenance and support of a network of capture terminals, for example checking terminal’s status via a Keep-alive message. This API is designed to support ATIOnet’s own line of capture and gateway devices and thus is a reserved protocol.

In addition to one or more protocol specifications, Integration Projects must have an “Integration Scope Document” detailing the feature-set to be implemented by the capture system, which also defines the acceptance criteria for the project.

## 2 Scope

Version 1.2 of this document covers a particular version of ATIONet’s Host protocol. Although feature’s descriptions are generally not related to a particular version of the protocol, some changes may apply which would be specifically commented and identified on each feature’s
description paragraph.

### 2.1 Scope Details

Protocol: ATIONet Native Transaction Protocol

Version: Version 1.2

API URI: native.ationet.com/v1/auth

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
				<p align="left">Pre-Authorization</p>
			</td>
			<td>
				<p align="center">1.0</p>
			</td>
			<td></td>
			<td>
				<p align="left">Used to validate a sale request and obtain transaction limits before performing the sale transaction.</p>
			</td>
		 </tr>
		 <tr valign="top">
			<td>
				<p align="left">Completion</p>
			</td>
			<td>
				<p align="center">1.0</p>
			</td>
			<td></td>
			<td>
				<p align="left">Informs a sale initiated with a Pre-Authorization.</p>
			</td>
		 </tr>
		 <tr valign="top">
			<td>
				<p align="left">Completion</p>
			</td>
			<td>
				<p align="center">1.0</p>
			</td>
			<td></td>
			<td>
				<p align="left">Informs a sale initiated with a Pre-Authorization.</p>
			</td>
		 </tr>
		 <tr valign="top">
			<td>
				<p align="left">Offline Completion</p>
			</td>
			<td>
				<p align="center">1.0</p>
			</td>
			<td></td>
			<td>
				<p align="left">Informs a Completion that was authorized locally at the site.</p>
			</td>
		 </tr>
		 <tr valign="top">
			<td>
				<p align="left">Satellite TAG Validation</p>
			</td>
			<td>
				<p align="center">1.1</p>
			</td>
			<td></td>
			<td>
				<p align="left">Validates a second ID sent for an already authorized transaction. Designed for acquiring a second TAG on a master-satellite pump fueling.</p>
			</td>
		 </tr>
		 <tr valign="top">
			<td>
				<p align="left">Contingency Completion</p>
			</td>
			<td>
				<p align="center">1.2</p>
			</td>
			<td></td>
			<td>
				<p align="left">Informs a Completion that was authorized in contingency.</p>
			</td>
		 </tr>
		 <tr valign="top">
			<td>
				<p align="left">Sales</p>
			</td>
			<td>
				<p align="center">1.2</p>
			</td>
			<td></td>
			<td>
				<p align="left">Informs a Sale.</p>
			</td>
		 </tr>
		 <tr valign="top">
			<td>
				<p align="left">Cancellation</p>
			</td>
			<td>
				<p align="center">1.2</p>
			</td>
			<td></td>
			<td>
				<p align="left">Cancels a Completion or a Sale.</p>
			</td>
		 </tr>
	</tbody>
</table>

## 3 Data Security

To validate the source of transactions and data encryption, the ATIONet Native Transaction Protocol relies on a SSL connection between the Site’s Terminal or Site’s Controller and the ATIONet Host. The SSL connection is established for each request/response pair, using a certificate property of ATIONet, meaning that each request must include a system-type user and password on the Header. The user will be matched against the related ATIONet actor for each message.

Users to be used on the Transaction Protocol messaging will be created by authorized users via ATIONet Console, with the role “Controller/Terminal”.

At this time there is no provisioning to distribute or update certificates or thumbprints thru a system interface. This information will be provided at request of the Controller’s vendor during the integration project.

## 4 Message Structure

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

## 5 Error Handling

Success/failure exits on the Native Transaction Protocol will be handled via HTTP status codes.

Successful request will get a HTTP 200 and the resulting response.

Transactions intended to post a command, for example Authorizations and Pre-Authorizations will return a single JSON-formatted item with the “Response Code” and “Response Text”. The body of these responses will never be empty.

Failure to process the request will be indicated by an HTTP 400’s range status code. The body will contain a single JSON-formatted item with the “ResponseCode”, “ResponseMessage” and “ResponseError” fields.

Refer to Response Codes Table in the Reference Tables section for a complete list of supported codes.

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

Refer to Product Data Structure Table on the Reference Tables Section.

Transaction authorization and register is based on ProductAmount and ProductQuantity; taxes and net amount fields are optional and are not considered by ATIOnet during transaction processing, but those fields may be used later for billing and reporting. Therefore, although optional at the protocol level, those might be required for certain integration projects for a given market or functional scope.

ATIONet expects standard NACS product codes. Although it can also map custom product codes for each site, Host-based product mapping is not recommended due to the extra administrative burden.

*Product Restrictions & Authorization limits on Fuel Transactions (FCS)*

Pre-Authorization Requests support different business scenarios:

<table>
	<thead>
		<tr valign="top">
			<th align="left">
				Scenario
			</th>
			<th align="left">
				Relevant fields values
			</th>
			<th align="left">
				Description
			</th>
		</tr>
	</thead>
	<tbody>
		<tr valign="top">
			<td>
				<p align="left">Zero Authorization \ Any product</p>
			</td>
			<td>
				<p align="left">
					Product Amount = 0
					<br>Product Quantity = 0
					<br>Product Code = NULL
					<br>Product Unit Price = NULL or != NULL
				</p>
			</td>
			<td>
				<p align="left">
					Terminal doesn’t enforce any pre-auth value and the user didn’t select a specific product (or the client system doesn’t have product identification capabilities).
					<br>
					ATIONet will authorize according to:
					<br>
					<br>1.  If there is any product restriction the host will respond with a Product Code otherwise will echo the NULL Product code, confirming any product authorization.
					<br>2.  If Product Unit Price is NULL and exists any price configuration the host will respond with a Product Unit Price otherwise will echo the Product Unit Price.
					<br>3.  Establish amount and quantity limits based on rules and current account.
					<br>4.  If the current account is based on quantity and the Terminal supports product authorization, the Host will limit by Product Quantity (with Product Code)
					<br>5.  If the current account is based on quantity and the Terminal doesn’t supports product authorization, the Host will limit by Product Amount if exists Product Unit Price, otherwise the transaction will be declined
					<br>6.  If the current account is based on money and the Terminal supports amount authorization, the Host will limit by Product Amount.
					<br>7.  If the current account is based on amount and the Terminal doesn’t supports amount authorization, the Host will limit by Product Quantity (with Product Code) if exists Product Unit Price, otherwise the transaction will be declined
				</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Zero Authorization \ Specific product</p>
			</td>
			<td>
				<p align="left">
					Product Amount = 0
					<br>Product Quantity = 0
					<br>Product Code != NULL
					<br>Product Unit Price = NULL or != NULL
				</p>
			</td>
			<td>
				<p align="left">
					Open value transaction for a specific product.
					<br>
					ATIONet will authorize according to:
					<br>
					<br>1.  If there is any product restriction will be validated first.
					<br>2.  2) 3) 4) 5) 6) and 7) Equal than Zero Authorization any product.
				</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Amount Authorization</p>
			</td>
			<td>
				<p align="left">
					Product Amount > 0
					<br>Product Quantity = 0
					<br>Product code = NULL or != NULL
					<br>Product Unit Price = NULL or != NULL
				</p>
			</td>
			<td>
				<p align="left">
					Amount requested, any or specific product.
					<br>
					ATIONet will authorize according to:
					<br>
					<br>1.  If there is any product restriction the host will respond with a Product Code otherwise will echo the NULL Product code, confirming any product authorization.
					<br>2.  If Product Unit Price is NULL and exists any price configuration the host will respond with a Product Unit Price otherwise will echo the Product Unit Price.
					<br>3.  Establish amount limits based on rules and current account. If exists quantity limits and Product Unit Price is NULL the transaction will be declined.
					<br>4.  5) 6) and 7) Equal than Zero Authorization any product.
				</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Quantity Authorization</p>
			</td>
			<td>
				<p align="left">
					Product Amount = 0
					<br>Product Quantity > 0
					<br>Product code = NULL or != NULL
					<br>Product Unit Price = NULL or != NULL
				</p>
			</td>
			<td>
				<p align="left">
					Quantity requested, any or specific product.
					<br>
					ATIONet will authorize according to:
					<br>
					<br>1.  If there is any product restriction the host will respond with a Product Code otherwise will echo the NULL Product code, confirming any product authorization.
					<br>2.  If Product Unit Price is NULL and exists any price configuration the host will respond with a Product Unit Price otherwise will echo the Product Unit Price.
					<br>3.  Establish quantity limits based on rules and current account. If exists amount limits and Product Unit Price is NULL the transaction will be  declined.
					<br>4.  5) 6) and 7) Equal than Zero Authorization any product.
				</p>
			</td>
		</tr>
	</tbody>
</table>

Transaction Amount is not relevant on Authorization requests in this version of the protocol as Dry Products sale is not yet available, on future versions, the Transaction Amount will be validated against the whole balance of the sub-account while Product figures will be evaluated against fuel product rules and restrictions.

In this version of the protocol, Transaction Amount should always match the Product Amount in Completions and Sales TREQs.

As described above, on certain situations, the Host will answer a Pre-Authorization request with an unsolicited Product Code; the Terminal must enforce such product restriction, otherwise the Completion will be declined.

With commercial and industrial system that don’t control fuel price, the Controller should use a \$1 unit price for all available products to
avoid potential declines due to the lack of unit price to resolve amount restrictions.

####Customer Data####
Customer data on a TREQ contains extra information gathered from prompts to the Cardholder or Attendant. On a TRESP, it contains the list of prompts that must be presented to the Cardholder or Attendant or a list of values to be used by the Terminal at capture, transaction or receipt printing.

*Prompt elements vs. Data elements*

Customer Data subfields can be Prompts or Data. Values contained on a Prompt are sent by the Host to be used by the Terminal to support the local processing of the prompt’s, for example minimum and maximum odometer values. ATIONet can send and receive Data elements.

Refer to Customer Data Codes Table in the Reference Tables section for a complete list of supported field names.

####Re-prompting & Dual-Card Identification####
ATIONet supports variable prompt-set definition for each card-type processed by the Host, allowing collection and validation of different entries for different type of cards, eventually this will allow to enforce different set of rules on different Device types.

There are three ways to implement this functionality on the Controller site:

1.  Devices with fixed-behavior.
    <br>Embedded devices, legacy devices or any other kind of equipment that implements a fixed or locally configurable behavior. In this case
    ATIONet will adapt to the device capabilities, reducing the functionality and eventually the types of cards supported.

2.  Devices depending on host-based re-prompt mechanism.
    <br>Controllers that do not have a local feature for selective prompts will prompt the User or Attendant only after receiving a TRESP requesting additional prompts. In this situation, the controller must retry the TREQ with the requested additional information after gathering the additional data from the cardholder or attendant. Is up to the Controller to handle the special flow of screens and messaging to the Host with or without showing the initial transaction as declined. From ATIONet standpoint, a TREQ requiring additional prompts will be considered Declined.

3.  Devices with pre-configured behavior based on PDL.
    <br>Controllers with the ability to process a full parameter download from the Host, could implement selective prompting before sending the TREQ to the Host, avoiding the need to process a double request.
    <br>It is worth to mention that a failure to submit a required prompt in this kind of devices, will cause a permanent failure to process such type of card, except if the device also has a host-based re-prompt mechanism –as in (b) type.

####Authorization Code####
The Host will return the Authorization Code on all approved transactions.
On Pre-Authorization/Completions message flows, the Controller must keep the Authorization Code sent on the Pre-Authorization TRESP and send it
back to the Host on the Completion TREQ. This is a mandatory feature.

Refer to Authorization Codes Table in the Reference Tables section for a complete list of supported codes.

####PIN Block####
The PIN entry on plain text, when the whole message or the communication themselves are encrypted.

####Original Data####
Original data on a TREQ contains extra information related to the original transaction that we want to cancel. Used only in zero completions without authorization code and cancellations transactions.

Refer to Original Data Table in the Reference Tables section for a complete list of supported field names.

##7 Transaction Request (TREQ) Message Format##

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
				<p align="left">Always “FCS” Fleet Control System</p>
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
				<p align="left">PumpNumber</p>
			</td>
			<td>
				<p align="left">2</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">“00”-“99”</p>
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
				<p align="left">Optional</p>
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
				<p align="left">Dictionary<string, decimal\></p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left"><”[Tax Description]”, [Tax Value]\></p>
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
				<p align="left">TransactionNetAmount</p>
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
				<p align="left">ProductData</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">List<AtionetProduct></p>
			</td>
			<td>
				<p align="left">Conditional</p>
			</td>
			<td>
				<p align="left">Refer to Product Fields in Field Description section</p>
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
				<p align="left">PrimaryPIN</p>
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
				<p align="left">Refer to PIN Block in Field Description section</p>
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
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">Refer to Track Data in Field Description section</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SecondaryPIN</p>
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
				<p align="left">Refer to PIN Block in Field Description section</p>
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
				<p align="left">TransactionExtendedData</p>
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
				<p align="left">Designed to capture OBD extended data (On board Devices)</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">OriginalData</p>
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
				<p align="left">Refer to Original Data in Field Description section</p>
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
				<p align="left">ResponseCode</p>
			</td>
			<td>
				<p align="left">5</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">Conditional</p>
			</td>
			<td>
				<p align="left">Use only when informing a Response not created by the Host (for example a local authorization), otherwise it should not be echoed from TRESP</p>
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
				<p align="left">Conditional</p>
			</td>
			<td>
				<p align="left">Idem Response Code</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">LongResponseText</p>
			</td>
			<td>
				<p align="left">200</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">Conditional</p>
			</td>
			<td>
				<p align="left">Idem Response Code</p>
			</td>
		</tr>
	</tbody>
</table>	
  
##8 Transaction Response (TRESP) Message Format##

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
				<p align="left">Echoed from TREQ</p>
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
				<p align="left">Echoed from TREQ</p>
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
				<p align="left">Echoed from TREQ</p>
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
				<p align="left">Echoed from TREQ</p>
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
				<p align="left">Echoed from TREQ</p>
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
				<p align="left">Echoed from TREQ</p>
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
				<p align="left">Echoed from TREQ</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">PumpNumber</p>
			</td>
			<td>
				<p align="left">2</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">Echoed from TREQ</p>
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
				<p align="left">Conditional</p>
			</td>
			<td>
				<p align="left">Refer to Product Fields in Field Description section</p>
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
				<p align="left">Conditional</p>
			</td>
			<td>
				<p align="left">xxx.xxx</p>
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
				<p align="left">Conditional</p>
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
				<p align="left">Conditional</p>
			</td>
			<td>
				<p align="left">xxxxxxx.xx</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ProductData</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">List<AtionetProduct></p>
			</td>
			<td>
				<p align="left">Conditional</p>
			</td>
			<td>
				<p align="left">Refer to Product Fields in Field Description section</p>
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
				<p align="left">Echoed from TREQ</p>
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
				<p align="left">Echoed from TREQ</p>
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
				<p align="left">Echoed from TREQ</p>
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
				<p align="left">Echoed from TREQ</p>
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
				<p align="left">Echoed from TREQ</p>
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
				<p align="left">LongResponseText</p>
			</td>
			<td>
				<p align="left">200</p>
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
	</tbody>
</table>

##9 Satellite TAG Validation Request (VREQ) Message Format##

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
				<p align="left">Always “FCS” Fleet Control System</p>
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
				<p align="left">
				“0” = Host Capture Only
				<br>“1” = Host processing required
				</p>
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
				<p align="left">Current Host Message Version = “1.2”</p>
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
				<p align="left"></p>
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
				<p align="left">LocalDate</p>
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
				<p align="left">LocalTime</p>
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
				<p align="left">TagId1</p>
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
				<p align="left">First TAG’s ID or Secure ID</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">TagId2</p>
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
				<p align="left">Second TAG’s ID or Secure ID</p>
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
				<p align="left">Required</p>
			</td>
			<td>
				<p align="left">Auth code received for the ongoing transaction</p>
			</td>
		</tr>
	</tbody>
</table>

##10 Satellite TAG Validation Response (VRESP) Message Format##

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
				<p align="left">Echoed from VREQ</p>
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
				<p align="left">Echoed from VREQ</p>
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
				<p align="left">Echoed from VREQ</p>
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
				<p align="left">Echoed from VREQ</p>
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
				<p align="left">LocalDate</p>
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
				<p align="left">Echoed from VREQ</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">LocalTime</p>
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
				<p align="left">Echoed from VREQ</p>
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
				<p align="left">Required</p>
			</td>
			<td>
				<p align="left">Echoed from VREQ</p>
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

##11 Reference Tables##

This section brings together the code tables and reference values used in messaging.

###11.1 Transaction Codes###

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
				<p align="left">“100”</p>
			</td>
			<td>
				<p align="left">TREQ</p>
			</td>
			<td>
				<p align="left">Pre-Authorization REQ</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">“101”</p>
			</td>
			<td>
				<p align="left">VREQ</p>
			</td>
			<td>
				<p align="left">Satellite TAG Validation REQ</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">“110”</p>
			</td>
			<td>
				<p align="left">TRESP</p>
			</td>
			<td>
				<p align="left">Pre-Authorization RESP</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">“111”</p>
			</td>
			<td>
				<p align="left">VRESP</p>
			</td>
			<td>
				<p align="left">Satellite TAG Validation RESP</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">“120”</p>
			</td>
			<td>
				<p align="left">TREQ</p>
			</td>
			<td>
				<p align="left">Completion REQ</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">“125”</p>
			</td>
			<td>
				<p align="left">TREQ</p>
			</td>
			<td>
				<p align="left">Offline REQ</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">“126”</p>
			</td>
			<td>
				<p align="left">TREQ</p>
			</td>
			<td>
				<p align="left">Contingency REQ</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">“130”</p>
			</td>
			<td>
				<p align="left">TRESP</p>
			</td>
			<td>
				<p align="left">Completion RESP</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">“200”</p>
			</td>
			<td>
				<p align="left">TREQ</p>
			</td>
			<td>
				<p align="left">Sale REQ</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">“210”</p>
			</td>
			<td>
				<p align="left">TRESP</p>
			</td>
			<td>
				<p align="left">Sale RESP</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">“400”</p>
			</td>
			<td>
				<p align="left">TREQ</p>
			</td>
			<td>
				<p align="left">Cancellation REQ</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">“410”</p>
			</td>
			<td>
				<p align="left">TRESP</p>
			</td>
			<td>
				<p align="left">Cancellation RESP</p>
			</td>
		</tr>
	</tbody>
</table>
	
###11.2 Account Type###

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
				<p align="left">“1”</p>
			</td>
			<td>
				<p align="left">ATIONet native track</p>
			</td>
		</tr>
	</tbody>
</table>	

###11.3 Product Data Structure###

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
	</tbody>
</table>	
			
###11.4 Customer Data###
    
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
				<p align="left">Last Odometer</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Min Odometer</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Max Odometer</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">PromptDriverId</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">PromptTruckUnitNumber</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">PromptTrailerNumber</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">PromptEngine Hours</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Last Engine Hours</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Min Engine Hours</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Max Engine Hours</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">PromptMiscellaneous</p>
			</td>
		</tr>
	</tbody>
</table>	

*Data elements*
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
				<p align="left">TruckUnitNumber</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">TrailerNumber</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Odometer</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">EngineHours</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">DriverId</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Miscellaneous</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">DriverLicenseState</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">DriverLicenseNumber</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">TripNumber</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">PurchaseOrderNumber</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ClientSupportsReceiptDownloading</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">TrailerHourMeterReading</p>
			</td>
		</tr>	
	</tbody>
</table>

###11.5 Measurement Unit Codes###

<table>
	<thead>
		<tr valign="top">
			<th align="left">
				Value
			</th>
			<th align="left">
				Description
			</th>
		</tr>
	</thead>
	<tbody>
		<tr valign="top">
			<td>
				<p align="left">“usgal”</p>
			</td>
			<td>
				<p align="left">Gallon USA</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">“ukgal”</p>
			</td>
			<td>
				<p align="left">Gallon UK</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">“l”</p>
			</td>
			<td>
				<p align="left">Litro</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">“m3”</p>
			</td>
			<td>
				<p align="left">Metro Cúbico</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">“kg”</p>
			</td>
			<td>
				<p align="left">Kilogramo</p>
			</td>
		</tr>	
	</tbody>
</table>

###11.6 Currency Codes###
 
Refer to ISO 4217 Currency Codes standard (<http://en.wikipedia.org/wiki/ISO_4217>)

###11.7 Authorization Codes###

<table>
	<thead>
		<tr valign="top">
            <th>
                <p align="left">Code</p>
            </th>
            <th>
                <p align="left">Response Message</p>
            </th>
            <th>
                <p align="left">Long Response Message</p>
            </th>
            <th>
                <p align="left">Description</p>
            </th>
        </tr>
	</thead>
	<tbody>
        <tr valing="top">
           <td colspan="4">
                <p align="left"><b>Authorized</b></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">00000</p>
            </td>
            <td>
                <p align="left">Authorized</p>
            </td>
            <td>
                <p align="left">Authorized</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valing="top">
           <td colspan="4">
                <p align="left"><b>Request Validations</b></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">10000</p>
            </td>
            <td>
                <p align="left">Invalid date </p>
            </td>
            <td>
                <p align="left">Invalid date </p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">10001</p>
            </td>
            <td>
                <p align="left">Invalid time </p>
            </td>
            <td>
                <p align="left">Invalid time </p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">10002</p>
            </td>
            <td>
                <p align="left">Invalid seq num</p>
            </td>
            <td>
                <p align="left">Invalid sequence number</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">10003</p>
            </td>
            <td>
                <p align="left">Invalid acc type</p>
            </td>
            <td>
                <p align="left">Invalid account type</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">10004</p>
            </td>
            <td>
                <p align="left">Invalid app type</p>
            </td>
            <td>
                <p align="left">Invalid application type</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">10005</p>
            </td>
            <td>
                <p align="left">Invalid proc mode</p>
            </td>
            <td>
                <p align="left">Invalid processing mode</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">10006</p>
            </td>
            <td>
                <p align="left">Invalid mess format</p>
            </td>
            <td>
                <p align="left">Invalid message format</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">10007</p>
            </td>
            <td>
                <p align="left">Invalid dev type</p>
            </td>
            <td>
                <p align="left">Invalid device type</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">10008</p>
            </td>
            <td>
                <p align="left">Invalid sys model</p>
            </td>
            <td>
                <p align="left">Invalid system model</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">10009</p>
            </td>
            <td>
                <p align="left">Invalid sys ver</p>
            </td>
            <td>
                <p align="left">Invalid system version</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">10010</p>
            </td>
            <td>
                <p align="left">Invalid entry method</p>
            </td>
            <td>
                <p align="left">Invalid entry method</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">10011</p>
            </td>
            <td>
                <p align="left">Invalid unit code</p>
            </td>
            <td>
                <p align="left">Invalid unit code</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">10012</p>
            </td>
            <td>
                <p align="left">Invalid unit code</p>
            </td>
            <td>
                <p align="left">Invalid datetime</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">10013</p>
            </td>
            <td>
                <p align="left">Invalid pri track</p>
            </td>
            <td>
                <p align="left">Invalid primary track</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">10014</p>
            </td>
            <td>
                <p align="left">Invalid prod data</p>
            </td>
            <td>
                <p align="left">Invalid product data</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">10015</p>
            </td>
            <td>
                <p align="left">Prod data req</p>
            </td>
            <td>
                <p align="left">Product data required</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">10016</p>
            </td>
            <td>
                <p align="left">Invalid batch number</p>
            </td>
            <td>
                <p align="left">Invalid batch number</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">10017</p>
            </td>
            <td>
                <p align="left">Invalid respone code</p>
            </td>
            <td>
                <p align="left">Invalid respone code</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">10018</p>
            </td>
            <td>
                <p align="left">Invalid terminal </p>
            </td>
            <td>
                <p align="left">Invalid terminal </p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">10019</p>
            </td>
            <td>
                <p align="left">Invalid old PIN</p>
            </td>
            <td>
                <p align="left">Invalid old PIN</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">10020</p>
            </td>
            <td>
                <p align="left">Invalid new PIN</p>
            </td>
            <td>
                <p align="left">Invalid new PIN</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">10021</p>
            </td>
            <td>
                <p align="left">Invalid orig data</p>
            </td>
            <td>
                <p align="left">Invalid original data</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valing="top">
           <td colspan="4">
                <p align="left"><b>Integrity Validations</b></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">11000</p>
            </td>
            <td>
                <p align="left">Merch not found</p>
            </td>
            <td>
                <p align="left">Merchant not found</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">11001</p>
            </td>
            <td>
                <p align="left">NetMerch not found</p>
            </td>
            <td>
                <p align="left">Network merchant not found</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">11002</p>
            </td>
            <td>
                <p align="left">Site not found</p>
            </td>
            <td>
                <p align="left">Site not found</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">11003</p>
            </td>
            <td>
                <p align="left">Prot not found</p>
            </td>
            <td>
                <p align="left">Protocol not found</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">11004</p>
            </td>
            <td>
                <p align="left">TType not found</p>
            </td>
            <td>
                <p align="left">Terminal type not found</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">11005</p>
            </td>
            <td>
                <p align="left">Fuel mapping needed</p>
            </td>
            <td>
                <p align="left">Fuel mapping needed</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">11006</p>
            </td>
            <td>
                <p align="left">Fuel not found</p>
            </td>
            <td>
                <p align="left">Fuel not found</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">11007</p>
            </td>
            <td>
                <p align="left">Comp not found</p>
            </td>
            <td>
                <p align="left">Company not found</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">11008</p>
            </td>
            <td>
                <p align="left">NetComp not found</p>
            </td>
            <td>
                <p align="left">Network company not found</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">11009</p>
            </td>
            <td>
                <p align="left">Contr not found</p>
            </td>
            <td>
                <p align="left">Contract not found</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">11010</p>
            </td>
            <td>
                <p align="left">Subacc not found</p>
            </td>
            <td>
                <p align="left">Sub account not found</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">11011</p>
            </td>
            <td>
                <p align="left">SecSubacc not found</p>
            </td>
            <td>
                <p align="left">Secondary sub account not found</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">11012</p>
            </td>
            <td>
                <p align="left">Veh or dri not found</p>
            </td>
            <td>
                <p align="left">Vehicle or driver not found</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">11013</p>
            </td>
            <td>
                <p align="left">Empty subaccount</p>
            </td>
            <td>
                <p align="left">Empty sub account</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">11014</p>
            </td>
            <td>
                <p align="left">Empty sec subaccount</p>
            </td>
            <td>
                <p align="left">Empty secondary sub account</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">11015</p>
            </td>
            <td>
                <p align="left">Fuel needed</p>
            </td>
            <td>
                <p align="left">Fuel needed</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">11016</p>
            </td>
            <td>
                <p align="left">Fuel not in contr</p>
            </td>
            <td>
                <p align="left">Fuel not in contract</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">11017</p>
            </td>
            <td>
                <p align="left">Fuel not in vehclas</p>
            </td>
            <td>
                <p align="left">Fuel not in vehicle class</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">11018</p>
            </td>
            <td>
                <p align="left">Comp money needed</p>
            </td>
            <td>
                <p align="left">Company money needed</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">11019</p>
            </td>
            <td>
                <p align="left">Merch money needed</p>
            </td>
            <td>
                <p align="left">Merchant money needed</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">11020</p>
            </td>
            <td>
                <p align="left">Comp qty needed</p>
            </td>
            <td>
                <p align="left">Company quantity needed</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">11021</p>
            </td>
            <td>
                <p align="left">Merch qty needed</p>
            </td>
            <td>
                <p align="left">Merchant quantity needed</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">11022</p>
            </td>
            <td>
                <p align="left">Fleet not found</p>
            </td>
            <td>
                <p align="left">Fleet not found</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">11023</p>
            </td>
            <td>
                <p align="left">Trans not found</p>
            </td>
            <td>
                <p align="left">Transaction not found</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valing="top">
           <td colspan="4">
                <p align="left"><b>To Review Validations</b></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">12000</p>
            </td>
            <td>
                <p align="left">Auth amount exceeded</p>
            </td>
            <td>
                <p align="left">Authorized amount exceeded</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">12001</p>
            </td>
            <td>
                <p align="left">Auth qty exceeded</p>
            </td>
            <td>
                <p align="left">Authorized quantity exceeded</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">12002</p>
            </td>
            <td>
                <p align="left">Auth with diff PPU</p>
            </td>
            <td>
                <p align="left">Authorization with different PPU</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">12003</p>
            </td>
            <td>
                <p align="left">Tr amount exceeded</p>
            </td>
            <td>
                <p align="left">Transaction amount exceeded</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valing="top">
           <td colspan="4">
                <p align="left"><b>Unlawful Validations</b></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">13000</p>
            </td>
            <td>
                <p align="left">Term does not exist</p>
            </td>
            <td>
                <p align="left">Terminal does not exist</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">13001</p>
            </td>
            <td>
                <p align="left">Netw does not exist</p>
            </td>
            <td>
                <p align="left">Network does not exist</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">13002</p>
            </td>
            <td>
                <p align="left">Id does not exist</p>
            </td>
            <td>
                <p align="left">Id does not exist</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">13003</p>
            </td>
            <td>
                <p align="left">SecId does not exist</p>
            </td>
            <td>
                <p align="left">Secondary Id does not exist</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">13004</p>
            </td>
            <td>
                <p align="left">Both veh ids</p>
            </td>
            <td>
                <p align="left">Both are vehicle identifications</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">13005</p>
            </td>
            <td>
                <p align="left">Both driv ids  </p>
            </td>
            <td>
                <p align="left">Both are driver identifications</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">13006</p>
            </td>
            <td>
                <p align="left">Subacc in diff cont</p>
            </td>
            <td>
                <p align="left">Sub account in different contract</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">13007</p>
            </td>
            <td>
                <p align="left">Id is not active</p>
            </td>
            <td>
                <p align="left">Identification is not active</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">13008</p>
            </td>
            <td>
                <p align="left">Id has expired</p>
            </td>
            <td>
                <p align="left">Identification has expired</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">13009</p>
            </td>
            <td>
                <p align="left">SecId is not active</p>
            </td>
            <td>
                <p align="left">Secondary identification is not active</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">13010</p>
            </td>
            <td>
                <p align="left">SecId has expired</p>
            </td>
            <td>
                <p align="left">Secondary identification has expired</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">13011</p>
            </td>
            <td>
                <p align="left">Vehicle not enabled</p>
            </td>
            <td>
                <p align="left">Vehicle not enabled</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">13012</p>
            </td>
            <td>
                <p align="left">Driver not enabled</p>
            </td>
            <td>
                <p align="left">Driver not enabled</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">13013</p>
            </td>
            <td>
                <p align="left">Contract has expired</p>
            </td>
            <td>
                <p align="left">Contract has expired</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">13014</p>
            </td>
            <td>
                <p align="left">Site not in contr</p>
            </td>
            <td>
                <p align="left">Site not in contract</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">13015</p>
            </td>
            <td>
                <p align="left">Driver Needed</p>
            </td>
            <td>
                <p align="left">Driver needed</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">13016</p>
            </td>
            <td>
                <p align="left">Driver not related</p>
            </td>
            <td>
                <p align="left">Driver not related</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">13017</p>
            </td>
            <td>
                <p align="left">Vehicle Needed</p>
            </td>
            <td>
                <p align="left">Vehicle needed</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">13018</p>
            </td>
            <td>
                <p align="left">Vehicle not related</p>
            </td>
            <td>
                <p align="left">Vehicle not related</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">13019</p>
            </td>
            <td>
                <p align="left">Duplicate TSN</p>
            </td>
            <td>
                <p align="left">Duplicate TSN</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">13020</p>
            </td>
            <td>
                <p align="left">Retry does not match</p>
            </td>
            <td>
                <p align="left">Retry does not match</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">13021</p>
            </td>
            <td>
                <p align="left">Auth does not exist</p>
            </td>
            <td>
                <p align="left">Authorization does not exist</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">13022</p>
            </td>
            <td>
                <p align="left">Auth not authorized</p>
            </td>
            <td>
                <p align="left">Authorization not authorized</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">13023</p>
            </td>
            <td>
                <p align="left">Auth with diff secid</p>
            </td>
            <td>
                <p align="left">Authorization with different secondary id</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">13024</p>
            </td>
            <td>
                <p align="left">Auth with diff id</p>
            </td>
            <td>
                <p align="left">Authorization with different id</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">13025</p>
            </td>
            <td>
                <p align="left">Auth with diff fuel</p>
            </td>
            <td>
                <p align="left">Authorization with different fuel</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">13026</p>
            </td>
            <td>
                <p align="left">Auth with diff term</p>
            </td>
            <td>
                <p align="left">Authorization with different terminal</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">13027</p>
            </td>
            <td>
                <p align="left">Auth with diff netw</p>
            </td>
            <td>
                <p align="left">Authorization with different network</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">13028</p>
            </td>
            <td>
                <p align="left">Auth with diff merch</p>
            </td>
            <td>
                <p align="left">Authorization with different merchant</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">13029</p>
            </td>
            <td>
                <p align="left">Auth with diff nwmr</p>
            </td>
            <td>
                <p align="left">Authorization with different network-merchant</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">13030</p>
            </td>
            <td>
                <p align="left">Auth with diff site</p>
            </td>
            <td>
                <p align="left">Authorization with different site</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">13031</p>
            </td>
            <td>
                <p align="left">Auth with diff prot</p>
            </td>
            <td>
                <p align="left">Authorization with diff protocol</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">13032</p>
            </td>
            <td>
                <p align="left">Auth with diff tt</p>
            </td>
            <td>
                <p align="left">Authorization with different terminal type</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">13033</p>
            </td>
            <td>
                <p align="left">Auth with diff comp</p>
            </td>
            <td>
                <p align="left">Authorization with different company</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">13034</p>
            </td>
            <td>
                <p align="left">Auth with diff nwcp</p>
            </td>
            <td>
                <p align="left">Authorization with diff network-company</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">13035</p>
            </td>
            <td>
                <p align="left">Auth with dif contr</p>
            </td>
            <td>
                <p align="left">Authorization with different contract</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">13036</p>
            </td>
            <td>
                <p align="left">Auth with diff subacc</p>
            </td>
            <td>
                <p align="left">Authorization with different sub account</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">13037</p>
            </td>
            <td>
                <p align="left">Auth with dif sec sa</p>
            </td>
            <td>
                <p align="left">Authorization with different secondary sub account</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">13038</p>
            </td>
            <td>
                <p align="left">Auth with diff vehicle</p>
            </td>
            <td>
                <p align="left">Authorization with different vehicle</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">13039</p>
            </td>
            <td>
                <p align="left">Auth with diff driver</p>
            </td>
            <td>
                <p align="left">Authorization with different driver</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">13040</p>
            </td>
            <td>
                <p align="left">Not contingency Auth </p>
            </td>
            <td>
                <p align="left">Not a contingency authorization</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">13041</p>
            </td>
            <td>
                <p align="left">Invalid driver code</p>
            </td>
            <td>
                <p align="left">Invalid driver code</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">13042</p>
            </td>
            <td>
                <p align="left">Invalid vehicle code</p>
            </td>
            <td>
                <p align="left">Invalid vehicle code</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">13043</p>
            </td>
            <td>
                <p align="left">Network not enabled</p>
            </td>
            <td>
                <p align="left">Network not enabled</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">13044</p>
            </td>
            <td>
                <p align="left">Company not enabled</p>
            </td>
            <td>
                <p align="left">Company not enabled</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">13045</p>
            </td>
            <td>
                <p align="left">Merchant not enabled</p>
            </td>
            <td>
                <p align="left">Merchant not enabled</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">13046</p>
            </td>
            <td>
                <p align="left">Invalid sec ident</p>
            </td>
            <td>
                <p align="left">Invalid secondary identification</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">13047</p>
            </td>
            <td>
                <p align="left">Invalid sec ident</p>
            </td>
            <td>
                <p align="left">Invalid secondary identification</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valing="top">
           <td colspan="4">
                <p align="left"><b>Current Account Validations</b></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">14000</p>
            </td>
            <td>
                <p align="left">CA movement declined</p>
            </td>
            <td>
                <p align="left">Current account movement declined</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">14001</p>
            </td>
            <td>
                <p align="left">Merchant CA mov dec</p>
            </td>
            <td>
                <p align="left">Merchant current account movement declined</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valing="top">
           <td colspan="4">
                <p align="left"><b>Establish Limits</b></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">20000</p>
            </td>
            <td>
                <p align="left">Unit price needed</p>
            </td>
            <td>
                <p align="left">Unit price needed</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">20001</p>
            </td>
            <td>
                <p align="left">Max quota not set</p>
            </td>
            <td>
                <p align="left">Maximum quiota not set</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40000</p>
            </td>
            <td>
                <p align="left">Insufficient balance</p>
            </td>
            <td>
                <p align="left">Insufficient balance</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40001</p>
            </td>
            <td>
                <p align="left">Unable prods auth</p>
            </td>
            <td>
                <p align="left">Unable to authorize by product</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40002</p>
            </td>
            <td>
                <p align="left">Veh-class qty exc</p>
            </td>
            <td>
                <p align="left">Vahicle class tank capacity excedeed</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40003</p>
            </td>
            <td>
                <p align="left">TType qty exc</p>
            </td>
            <td>
                <p align="left">Terminal type quantity excedeed</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40004</p>
            </td>
            <td>
                <p align="left">Term qty excedeed</p>
            </td>
            <td>
                <p align="left">Terminal quantity excedeed</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40005</p>
            </td>
            <td>
                <p align="left">Term money excedeed</p>
            </td>
            <td>
                <p align="left">Terminal money excedeed</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40006</p>
            </td>
            <td>
                <p align="left">Offline lim excedeed</p>
            </td>
            <td>
                <p align="left">Offline limit excedeed</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valing="top">
           <td colspan="4">
                <p align="left"><b>Location Rule</b></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40100</p>
            </td>
            <td>
                <p align="left">Site not authorized</p>
            </td>
            <td>
                <p align="left">Site not authorized</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40101</p>
            </td>
            <td>
                <p align="left">Site not authorized</p>
            </td>
            <td>
                <p align="left">Site not authorized</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40102</p>
            </td>
            <td>
                <p align="left">Site not authorized</p>
            </td>
            <td>
                <p align="left">Site not authorized</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40103</p>
            </td>
            <td>
                <p align="left">Site not authorized</p>
            </td>
            <td>
                <p align="left">Site not authorized</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valing="top">
           <td colspan="4">
                <p align="left"><b>Fuel Rule</b></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40200</p>
            </td>
            <td>
                <p align="left">Fuel not authorized</p>
            </td>
            <td>
                <p align="left">Fuel not authorized</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40201</p>
            </td>
            <td>
                <p align="left">Fuel not authorized</p>
            </td>
            <td>
                <p align="left">Fuel not authorized</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40202</p>
            </td>
            <td>
                <p align="left">Fuel not authorized</p>
            </td>
            <td>
                <p align="left">Fuel not authorized</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40203</p>
            </td>
            <td>
                <p align="left">Fuel not authorized</p>
            </td>
            <td>
                <p align="left">Fuel not authorized</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valing="top">
           <td colspan="4">
                <p align="left"><b>Transaction Rule</b></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">20300</p>
            </td>
            <td>
                <p align="left">Quota not set</p>
            </td>
            <td>
                <p align="left">Quota not set</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40300</p>
            </td>
            <td>
                <p align="left">Veh money excedeed</p>
            </td>
            <td>
                <p align="left">Vehicle money excedeed</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40301</p>
            </td>
            <td>
                <p align="left">Driv money excedeed</p>
            </td>
            <td>
                <p align="left">Driver money excedeed</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40302</p>
            </td>
            <td>
                <p align="left">Fuel money excedeed</p>
            </td>
            <td>
                <p align="left">Fuel money excedeed</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40303</p>
            </td>
            <td>
                <p align="left">Site money excedeed</p>
            </td>
            <td>
                <p align="left">Site money excedeed</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40304</p>
            </td>
            <td>
                <p align="left">Fleet money excedeed</p>
            </td>
            <td>
                <p align="left">Fleet money excedeed</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40305</p>
            </td>
            <td>
                <p align="left">Veh qty excedeed</p>
            </td>
            <td>
                <p align="left">Veh quantity excedeed</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40306</p>
            </td>
            <td>
                <p align="left">Driv qty excedeed</p>
            </td>
            <td>
                <p align="left">Driv quantity excedeed</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40307</p>
            </td>
            <td>
                <p align="left">Fuel qty excedeed</p>
            </td>
            <td>
                <p align="left">Fuel quantity excedeed</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40308</p>
            </td>
            <td>
                <p align="left">Site qty excedeed</p>
            </td>
            <td>
                <p align="left">Site quantity excedeed</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40309</p>
            </td>
            <td>
                <p align="left">Fleet qty excedeed</p>
            </td>
            <td>
                <p align="left">Fleet quantity excedeed</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valing="top">
           <td colspan="4">
                <p align="left"><b>Quota Rule</b></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">20400</p>
            </td>
            <td>
                <p align="left">Quota not set</p>
            </td>
            <td>
                <p align="left">Quota not set</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40400</p>
            </td>
            <td>
                <p align="left">Veh money excedeed</p>
            </td>
            <td>
                <p align="left">Vehicle money excedeed</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40401</p>
            </td>
            <td>
                <p align="left">Driv money excedeed</p>
            </td>
            <td>
                <p align="left">Driver money excedeed</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40402</p>
            </td>
            <td>
                <p align="left">Fuel money excedeed</p>
            </td>
            <td>
                <p align="left">Fuel money excedeed</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40403</p>
            </td>
            <td>
                <p align="left">Site money excedeed</p>
            </td>
            <td>
                <p align="left">Site money excedeed</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40404</p>
            </td>
            <td>
                <p align="left">Fleet money excedeed</p>
            </td>
            <td>
                <p align="left">Fleet money excedeed</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40405</p>
            </td>
            <td>
                <p align="left">Veh qty excedeed</p>
            </td>
            <td>
                <p align="left">Veh quantity excedeed</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40406</p>
            </td>
            <td>
                <p align="left">Driv qty excedeed</p>
            </td>
            <td>
                <p align="left">Driv quantity excedeed</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40407</p>
            </td>
            <td>
                <p align="left">Fuel qty excedeed</p>
            </td>
            <td>
                <p align="left">Fuel quantity excedeed</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40408</p>
            </td>
            <td>
                <p align="left">Site qty excedeed</p>
            </td>
            <td>
                <p align="left">Site quantity excedeed</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40409</p>
            </td>
            <td>
                <p align="left">Fleet qty excedeed</p>
            </td>
            <td>
                <p align="left">Fleet quantity excedeed</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40410</p>
            </td>
            <td>
                <p align="left">Veh tran excedeed</p>
            </td>
            <td>
                <p align="left">Vehicle transactions excedeed</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40411</p>
            </td>
            <td>
                <p align="left">Driv tran excedeed</p>
            </td>
            <td>
                <p align="left">Driv transactions excedeed</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40412</p>
            </td>
            <td>
                <p align="left">Prod tran excedeed</p>
            </td>
            <td>
                <p align="left">Prod transactions excedeed</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40413</p>
            </td>
            <td>
                <p align="left">Site tran excedeed</p>
            </td>
            <td>
                <p align="left">Site transactions excedeed</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40414</p>
            </td>
            <td>
                <p align="left">Fleet tran excedeed</p>
            </td>
            <td>
                <p align="left">Fleet transactions excedeed</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valing="top">
           <td colspan="4">
                <p align="left"><b>Prompting Rule</b></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">20500</p>
            </td>
            <td>
                <p align="left">Retries exceeded</p>
            </td>
            <td>
                <p align="left">Retries exceeded</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40500</p>
            </td>
            <td>
                <p align="left">Prompting needed</p>
            </td>
            <td>
                <p align="left">Prompting needed</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40501</p>
            </td>
            <td>
                <p align="left">Pri PIN needed</p>
            </td>
            <td>
                <p align="left">Primary PIN needed</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40502</p>
            </td>
            <td>
                <p align="left">Sec PIN needed</p>
            </td>
            <td>
                <p align="left">Secondary PIN needed</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40503</p>
            </td>
            <td>
                <p align="left">Invalid  pri PIN</p>
            </td>
            <td>
                <p align="left">Invalid primary PIN</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40504</p>
            </td>
            <td>
                <p align="left">Invalid sec PIN</p>
            </td>
            <td>
                <p align="left">Invalid secondary PIN</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40505</p>
            </td>
            <td>
                <p align="left">Sec Track needed</p>
            </td>
            <td>
                <p align="left">Secondary track needed</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40506</p>
            </td>
            <td>
                <p align="left">Invalid odometer</p>
            </td>
            <td>
                <p align="left">Invalid odometer</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40507</p>
            </td>
            <td>
                <p align="left">Invalid eng hours</p>
            </td>
            <td>
                <p align="left">Invalid engine hours</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valing="top">
           <td colspan="4">
                <p align="left"><b>Days Rule</b></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">20600</p>
            </td>
            <td>
                <p align="left">Week days not set</p>
            </td>
            <td>
                <p align="left">Week days not set</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40600</p>
            </td>
            <td>
                <p align="left">Day not authorized</p>
            </td>
            <td>
                <p align="left">Day not authorized</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40601</p>
            </td>
            <td>
                <p align="left">Day not authorized</p>
            </td>
            <td>
                <p align="left">Day not authorized</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40602</p>
            </td>
            <td>
                <p align="left">Day not authorized</p>
            </td>
            <td>
                <p align="left">Day not authorized</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40603</p>
            </td>
            <td>
                <p align="left">Day not authorized</p>
            </td>
            <td>
                <p align="left">Day not authorized</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40604</p>
            </td>
            <td>
                <p align="left">Day not authorized</p>
            </td>
            <td>
                <p align="left">Day not authorized</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valing="top">
           <td colspan="4">
                <p align="left"><b>DateTime Rule</b></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">20700</p>
            </td>
            <td>
                <p align="left">DateTime not set</p>
            </td>
            <td>
                <p align="left">DateTime not set</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40700</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40701</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40702</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40703</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40704</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40705</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40706</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40707</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40708</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40709</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40710</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40711</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40712</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40713</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40714</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40715</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40716</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40717</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40718</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40719</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40720</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40721</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40722</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40723</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40724</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40725</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40726</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40727</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40728</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40729</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left">DateTime not auth</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valing="top">
           <td colspan="4">
                <p align="left"><b>DaysTime Rule</b></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">20800</p>
            </td>
            <td>
                <p align="left">Week days not set</p>
            </td>
            <td>
                <p align="left">Week days not set</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">20801</p>
            </td>
            <td>
                <p align="left">Time not set</p>
            </td>
            <td>
                <p align="left">Time not set</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40800</p>
            </td>
            <td>
                <p align="left">Day not authorized</p>
            </td>
            <td>
                <p align="left">Day not authorized</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40801</p>
            </td>
            <td>
                <p align="left">Day not authorized</p>
            </td>
            <td>
                <p align="left">Day not authorized</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40802</p>
            </td>
            <td>
                <p align="left">Day not authorized</p>
            </td>
            <td>
                <p align="left">Day not authorized</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40803</p>
            </td>
            <td>
                <p align="left">Day not authorized</p>
            </td>
            <td>
                <p align="left">Day not authorized</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40804</p>
            </td>
            <td>
                <p align="left">Day not authorized</p>
            </td>
            <td>
                <p align="left">Day not authorized</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40805</p>
            </td>
            <td>
                <p align="left">DaysTime not auth</p>
            </td>
            <td>
                <p align="left">Day not authorized</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40806</p>
            </td>
            <td>
                <p align="left">DaysTime not auth</p>
            </td>
            <td>
                <p align="left">Day not authorized</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40807</p>
            </td>
            <td>
                <p align="left">DaysTime not auth</p>
            </td>
            <td>
                <p align="left">Day not authorized</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40808</p>
            </td>
            <td>
                <p align="left">DaysTime not auth</p>
            </td>
            <td>
                <p align="left">Day not authorized</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40809</p>
            </td>
            <td>
                <p align="left">DaysTime not auth</p>
            </td>
            <td>
                <p align="left">Day not authorized</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40810</p>
            </td>
            <td>
                <p align="left">DaysTime not auth</p>
            </td>
            <td>
                <p align="left">Day not authorized</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40811</p>
            </td>
            <td>
                <p align="left">DaysTime not auth</p>
            </td>
            <td>
                <p align="left">Day not authorized</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40812</p>
            </td>
            <td>
                <p align="left">DaysTime not auth</p>
            </td>
            <td>
                <p align="left">Day not authorized</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40813</p>
            </td>
            <td>
                <p align="left">DaysTime not auth</p>
            </td>
            <td>
                <p align="left">Day not authorized</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40814</p>
            </td>
            <td>
                <p align="left">DaysTime not auth</p>
            </td>
            <td>
                <p align="left">Day not authorized</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valing="top">
           <td colspan="4">
                <p align="left"><b>Dry Transaction Rule</b></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">20900</p>
            </td>
            <td>
                <p align="left">Quota Not Set</p>
            </td>
            <td>
                <p align="left">Quota not set</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40900</p>
            </td>
            <td>
                <p align="left">Veh money exceeded</p>
            </td>
            <td>
                <p align="left">Vehicle money exceeded</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40901</p>
            </td>
            <td>
                <p align="left">Driv money exceeded</p>
            </td>
            <td>
                <p align="left">Driver money exceeded</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40902</p>
            </td>
            <td>
                <p align="left">Site money exceeded</p>
            </td>
            <td>
                <p align="left">Site money exceeded</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">40903</p>
            </td>
            <td>
                <p align="left">Fleet money exceeded</p>
            </td>
            <td>
                <p align="left">Fleet money exceeded</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valing="top">
           <td colspan="4">
                <p align="left"><b>Dry Quota Rule</b></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">21000</p>
            </td>
            <td>
                <p align="left">Quota not set</p>
            </td>
            <td>
                <p align="left">Quota not set</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">41000</p>
            </td>
            <td>
                <p align="left">Veh money exceeded</p>
            </td>
            <td>
                <p align="left">Vehicle money exceeded</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">41001</p>
            </td>
            <td>
                <p align="left">Driv money exceeded</p>
            </td>
            <td>
                <p align="left">Driver money exceeded</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">41002</p>
            </td>
            <td>
                <p align="left">Site money exceeded</p>
            </td>
            <td>
                <p align="left">Site money exceeded</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">41003</p>
            </td>
            <td>
                <p align="left">Fleet money exceeded</p>
            </td>
            <td>
                <p align="left">Fleet money exceeded</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valing="top">
           <td colspan="4">
                <p align="left"><b>Process Messages</b></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">50000</p>
            </td>
            <td>
                <p align="left">App error</p>
            </td>
            <td>
                <p align="left">Application error</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
        <tr valign="top">
            <td>
                <p align="left">50001</p>
            </td>
            <td>
                <p align="left">Not available in off</p>
            </td>
            <td>
                <p align="left">Not available in offline mode</p>
            </td>
            <td>
                <p align="left"></p>
            </td>
        </tr>
	</tbody>
</table>

###11.8 Response Codes###

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
 
###11.9 Original Data

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
				<p align="left">TransactionCode</p>
			</td>
		</tr>	
		<tr valign="top">	
			<td>
				<p align="left">TransactionSequenceNumber</p>
			</td>
		</tr>	
		<tr valign="top">	
			<td>
				<p align="left">LocalTransactionDate</p>
			</td>
		</tr>	
		<tr valign="top">	
			<td>
				<p align="left">LocalTransactionTime</p>
			</td>
		</tr>
	</tbody>
</table>

## Appendix A - Native Authorization Protocol Messages

Check this [document](AN-Native_Auth_Protocol_Messages.md) to have detailed information about each field in each message under the Native Authorization Protocol 
