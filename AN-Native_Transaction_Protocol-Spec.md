![ATIONET Logo](Content/Images/ATIOnetLogo_250x70.png)
# ATIONET - Native Transaction Protocol Specification v1.5  <!-- omit in toc -->

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
			ATIONET-Native_Transaction_Protocol-Spec-v1.5
		</td>
	</tr>
	<tr>
		<td>
			Doc Version:
		</td>
		<td>
			1.5
		</td>
	</tr>
	<tr>
		<td>
			Release Date:
		</td>
		<td>
			TBD
		</td>
	</tr>
	<tr>
		<td>
			Author:
		</td>
		<td>
			ATIONET LLC
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
	<tr valign="top">
		<td>
			<p>1.4</p>
		</td>
		<td>
			<p>2/Dec/2021</p>
		</td>
		<td>
			<p>1.4  Protocol version changes
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>1.5</p>
		</td>
		<td>
			<p>29/Jun/2022</p>
		</td>
		<td>
			<p>1.5  Protocol version changes
			<br> - Add IdTransactionContingency request</p>
		</td>
	</tr>
		<tr valign="top">
		<td>
			<p>1.6</p>
		</td>
		<td>
			<p>06/March/2024</p>
		</td>
		<td>
			<p>1.6  Protocol version changes
			<br> - Add request examples</p>
		</td>
	</tr>
</table>

## Contents ##

1. [ATIONET Integration Documentation Scope](#1-ationet-integration-documentation-scope)
	1. [ATIONET Native Transactions Protocol Specification](#ationet-native-transactions-protocol-specification)
	2. [ATIONET Administrative Transactions Protocol Specification](#ationet-administrative-transactions-protocol-specification)
	3. [ATIONET Native Interface Protocol Specification](#ationet-native-interface-protocol-specification)
	4. [ATIONET Maintenance Interface Protocol Specification](#ationet-maintenance-interface-protocol-specification)
2. [Scope](#2-scope)
	1. [Scope Details](#21-scope-details)
	2. [Supported Transactions](#22-supported-transactions)
3. [Data Security](#3-data-security)
4. [Message Structure](#4-message-structure)
	1. [Request Format](#41-request-format)
	2. [Response Format](#42-response-format)
5.  [Error Handling](#5-error-handling)
6.  [Field Descriptions](#6-field-descriptions)
	1. [System Model and System Version](#system-model-and-system-version)
	2. [Pump Authorization Values](#pump-authorization-values)
	3. [Terminal Identification](#terminal-identification)
	4. [Currency Code](#currency-code)
	5. [Device Type Identifier](#device-type-identifier)
	6. [Transaction Sequence Number](#transaction-sequence-number)
	7. [Entry Method](#entry-method)
	8. [Processing Mode](#processing-mode)
	9. [Track Data](#track-data)
	10. [Batch Number](#batch-number)
	11. [Shift Number](#shift-number)
	12. [Product Fields](#product-fields)
	13. [Customer Data](#customer-data)
	14. [Re-prompting & Dual-Card Identification](#re-prompting--dual-card-identification)
	15. [Authorization Code](#authorization-code)
	16. [PIN Fields](#pin-fields)
	17. [Original Data](#original-data)
7.  [Transaction Request (TREQ) Message Format](#7-transaction-request-treq-message-format)
8.  [Transaction Response (TRESP) Message Format](#8-transaction-response-tresp-message-format)
9.  [Satellite TAG Validation Request (VREQ) Message Format](#9-satellite-tag-validation-request-vreq-message-format)
10. [Satellite TAG Validation Response (VRESP) Message Format](#10-satellite-tag-validation-response-vresp-message-format)
11. [Identification Pin Change Request (PREQ) Message Format](#11-identification-pin-change-request-preq-message-format)
12. [Identification Pin Change Response (PRESP) Message Format](#12-identification-pin-change-response-presp-message-format)
13. [Message Samples](#13-message-samples)
	18. [Pre Authorization Sample](#131-pre-authorization-sample)
	19. [Completion Sample](#132-completion-sample)
14. [Appendix A - Native Authorization Protocol Messages](#appendix-a---native-authorization-protocol-messages)

## Overview

### Introduction

This specification is intended to document ATIONET’s Native Protocol messaging format and related features required for the systems applying for integration with ATIONET. The following sections provide descriptions of the messages themselves, the expected behaviour for each supported transaction type and a common ground for the functionality of each relevant item.

### Definitions

#### **Host**
A computer system that is accessed by a user working at a remote location. In this document, Host is always the ATIONET Host.

#### **Terminal**
An electronic merchant card processing device responsible for transaction capture, display output to the cashier and/or to the cardholder on screen and/or print format.

#### **Controller**
A client system that can send or receive data to and from ATIONET’s Host. A Controller controls or includes one or more terminal. When there is only one Terminal connected to a Controller, Terminal and Controller are equivalent.

#### **TREQ**
Transaction Request.

#### **TRESP**
Transaction Response.

# 1 ATIONET Integration Documentation Scope

Third-party systems integrate with ATIONET via a set of APIs (Application Programming Interfaces). Each ATIONET’s API is described on a separate Protocol Specification. The complete documentation of ATIONET API’s is comprised of:

#### ATIONET Native Transactions Protocol Specification
Covers financial transactions for transaction capture systems (payment terminals, site controllers and point of sale systems), including sales and refunds.

#### ATIONET Administrative Transactions Protocol Specification
Describes a set of functions complementing the transaction-capture business, for example Batch or Shift Close. These functions enhance the capabilities of the integration but their implementation is not mandatory.

#### ATIONET Native Interface Protocol Specification
Covers system-to-system integration capabilities of ATIONET, designed to interact with third-party back-end systems, for example downloading transactions data or sending current-accounts movements to ATIONET. This API is reserved and requires ATIONET and Subscriber permissions.

#### ATIONET Maintenance Interface Protocol Specification
List a set of functions designed to help in the maintenance and support of a network of capture terminals, for example checking terminal’s status via a Keep-alive message. This API is designed to support ATIONET’s own line of capture and gateway devices and thus is a reserved protocol.

In addition to one or more protocol specifications, Integration Projects must have an “Integration Scope Document” detailing the feature-set to be implemented by the capture system, which also defines the acceptance criteria for the project.

## 2 Scope

Version 1.4 of this document covers a particular version of ATIONET’s Host protocol. Although feature’s descriptions are generally not related to a particular version of the protocol, some changes may apply which would be specifically commented and identified on each feature’s description paragraph.

### 2.1 Scope Details

Protocol: ATIONET Native Transaction Protocol

Version: Version 1.4

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
 		 <tr valign="top">
			<td>
				<p align="left">Change PIN</p>
			</td>
			<td>
				<p align="center">1.2</p>
			</td>
			<td></td>
			<td>
				<p align="left">Change the PIN of any identification, providing the valid old one</p>
			</td>
		 	</tr>
		  		 <tr valign="top">
			<td>
				<p align="left">Void</p>
			</td>
			<td>
				<p align="center">1.4</p>
			</td>
			<td></td>
			<td>
				<p align="left">Informs the annulment of a completed non-billed transaction</p>
			</td>
		 </tr>
		 		 </tr>
		  		 <tr valign="top">
			<td>
				<p align="left">Refund</p>
			</td>
			<td>
				<p align="center">1.4</p>
			</td>
			<td></td>
			<td>
				<p align="left">Used to refund a completed transaction. Similar to Void transactions, but may only be used after billing</p>
			</td>
		 </tr>
	</tbody>
</table>

## 3 Data Security

To validate the source of transactions and data encryption, the ATIONET Native Transaction Protocol relies on a SSL connection between the Site’s Terminal or Site’s Controller and the ATIONET Host. The SSL connection is established for each request/response pair, using a certificate property of ATIONET, meaning that each request must include a system-type user and password on the Header. The user will be matched against the related ATIONET actor for each message.

Users to be used on the Transaction Protocol messaging will be created by authorized users via ATIONET Console, with the role “Controller/Terminal”.

At this time there is no provisioning to distribute or update certificates or thumbprints thru a system interface. This information will be provided at request of the Controller’s vendor during the integration project.

## 4 Message Structure

All Transaction API messages share the same base structure with slight modifications depending on which *TransactionCode* you use. All requests must be made with a **POST** method and the body uses a JSON format, as well as their responses. 

Only one request is accepted on each message.

### 4.1 Request Format

*Header:*
```
Accept-Encoding: gzip
Authorization: Basic user:password
```

*Body:*
``` json
{
	"FieldName":"StringValue",
	"FieldName":"StringValue",
	"FieldName":Value
}
```

### 4.2 Response Format

*Header:*
```
Content-Type: application/json; charset=utf-8
```

*Body:*
``` json
{
	"FieldName":"StringValue",
	"FieldName":"StringValue",
	"FieldName":Value
}
```

Note: Alphanumeric fields, stated as Type “A/N” in record format tables below show the maximum possible length as the Size, although in JSON-formatted strings they will be represented with trailing spaces trimmed.

## 5 Error Handling

Success/failure exits on the Native Transaction Protocol will be handled via HTTP status codes.

Successful request will get a HTTP 200 and the resulting response.

Transactions intended to post a command, for example Authorizations and Pre-Authorizations will return a single JSON-formatted item with the *Response Code* and *Response Text*. The body of these responses will never be empty.

Failure to process the request will be indicated by an HTTP 400’s range status code. The body will contain a single JSON-formatted item with the “ResponseCode”, “ResponseMessage” and “ResponseError” fields.

Refer to [Response Codes annex](./Annexes/AN-Native-AuthResponseCodes-Annex.md) for a complete list of supported codes.

## 6 Field Descriptions

This section details the purpose and expected behavior on the Controller system for relevant items on the protocol.

#### **System Model and System Version**
Brand/Model and Firmware/Software version of the client system. Format and content will be assigned for each vendor during the Integration project.

#### **Pump Authorization Values**
Pre-sale Authorizations processed by ATIONET might be (a) Fully-authorized, (b) Partially-authorized, or (c) Declined. Full and partial authorizations may have the same Authorized codes, but a partial authorization only allows to sale a fraction of the requested amount. Controllers must always check the Authorized Amount/Quantity on approved transactions.

The second value relevant for the authorization value is the local authorization limit that can be enforced locally. On any case, the preset sent to the gas pump must be the lesser value between the Authorized Amount/Quantity and the DCR Cutoff Amount.

#### **Terminal Identification**
Terminal ID is a system-wide unique ID for the Controller or Terminal device on the capture side. Terminal ID should be configured on the client system during manual installation. The length of the TID’s code depends on the controller.

#### **Device Type Identifier**
A single digit field, informed by the Controller system, that identifies the type of capture device. (Manned/Unmanned, Indoor/Outdoor). In case the Controller system doesn’t have the capability to inform this distinction, “4 – Other self-service” should be always informed.

#### **Currency Code**
 
Refer to [ISO 4217 Currency Codes standard](<http://en.wikipedia.org/wiki/ISO_4217>)

#### **Transaction Sequence Number**
The Transaction number is a fixed-length integer value from 1 to 999999 and it is assigned and incremented for each transaction sent to the Host, regardless of the result. It must be reset back to 1 every time it reaches the limit.

#### **Entry Method**
The Entry Method code indicates whether the customer identification was manually typed-in, read from a card swipe or any other automatic identification mechanism.

#### **Processing Mode**
Indicates whether the Host must apply an alternative process to the request. Regular transactions must inform “1 = Host processing required”

#### **Track Data**
This field identifies the account of the transaction.

Track Data field must contain the whole identifier’s information (for example, complete Track 2 data on a magnetic card, or all the TAG’s fields on an AVI capture).

There are two Tracks and PINs field pairs, the Primary and Secondary, on the Primary, the Controller must send the track of the identifier used to initiate the capture transaction (first card presented) and the Secondary should contain the complementary identification (if used). For example if the transaction is initiated presenting a Driver Card that also requires a Vehicle Identification, Primary will be the Driver and Secondary will be the Vehicle.

The Primary identification will mandate the sub-account to be charged for the transaction, the Secondary will be used for rules validation but will not be affected on its balance.

#### **Batch Number**
Optional information, if informed, ATIONET will use this field for report filtering and queries.

If used, data must be formatted as an 11 digit number: yyyymmddbbb. Year (4 digits), Month (2 digits), Day (2 digits), Batch/Shift number (3 digits, padded with zeros). Date part must be the starting date of the batch. Batch number must wrap-around to 1 after reaching 999.

If there is no batch functionality at all, the recommended format is Transaction Date plus 3 zeros.

#### **Shift Number**
Optional information, if informed, ATIONET will use this field for report filtering and queries.

The Controller application can manage the Shift Number and meaning as needed. It may be day’s shift number, weekly batches, split-batches, etc., although this is a fixed length field, therefore the format must be maintained.

If there is no batch or shift functionality at all, the recommended format is the business date of the transaction followed of 3 zeros.

#### **Product Fields**
Transaction messages include a list of Product fields, plus a Product Taxes compound field plus and a Product Data compound field, the later will be used only on multi-product transactions.

On single product messages, like a simple fueling transaction, product’s amount and other details must be sent on the fields included in the main body of the message. When the sale includes more than one product, the first one must be sent on the main body and rest on the Product Data structure. Fuel presets will only work for the product in the main body; therefore, first product in the list should be the fuel sale if there is any.

Refer to [Product Data Structure](./Annexes/AN-Native-ProductData-Annex.md) annex for more information about dry products format.

Transaction authorization and register is based on ProductAmount and ProductQuantity; taxes and net amount fields are optional and are not considered by ATIONET during transaction processing, but those fields may be used later for billing and reporting. Therefore, although optional at the protocol level, those might be required for certain integration projects for a given market or functional scope.

ATIONET expects standard NACS product codes. Although it can also map custom product codes for each site, Host-based product mapping is not recommended due to the extra administrative burden.

*Product Restrictions & Authorization limits on Fuel Transactions (FCS)*

Pre-Authorization Requests support different business scenarios:

| Scenario                                 | Relevant fields values                                                | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| ---------------------------------------- | --------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Fill-Up Authorization \ Any product      | ProductAmount = NULL && ProductQuantity = NULL && ProductCode = NULL  | Terminal doesn’t enforce any pre-auth value and the user didn’t select a specific product (or the client system doesn’t have product identification capabilities). ATIONET will authorize according to: <br/><br/>1. If there is any product restriction the host will respond with a ProductCode otherwise will echo the NULL ProductCode, confirming any product authorization.<br/>2. If any price configuration exists and the controller allows price change, the host will respond with that price, otherwise it will echo the ProductUnitPrice recieved whether it was NULL or not<br/>3. Establish amount and quantity limits based on rules and current account.<br/>4. The Terminal Authorization Type will determine which specie (money or volume) to authorize. In case both species are supported, the authorization is made in the current account specie.<br/>5. In case any specie conversion needs to be made (money to volume or volume to money), the ProductUnitPrice becomes mandatory |
| Fill-Up Authorization \ Specific product | ProductAmount = NULL && ProductQuantity = NULL && ProductCode != NULL | Terminal doesn’t enforce any pre-auth value but a specific product. ATIONET will authorize according to:<br/><br/>1. If there is any product restriction will be validated first. <br/>2. The same as a Fill-Up Authorization from step 2 to 5                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| Pre-set Amount Authorization             | ProductAmount >= 0 && ProductQuantity = NULL                          | Same as a Fill-Up Authorization but with an Amount limit requested (0 enforces an amount authorization but does not limit)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| Pre-set Quantity Authorization           | ProductAmount = NULL && ProductQuantity >= 0                          | Same as a Fill-Up Authorization but with a Quantity limit requested (0 enforces a quantity authorization but does not limit)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |

Should the transaction include Dry Products, the *Transaction Amount* field **must match** the sum of all *Dry Product* amounts plus the *Product Amount* (fuel amount) from the request body.

As described above, on certain situations, the Host will answer a Pre-Authorization request with an unsolicited Product Code; the Terminal must enforce such product restriction, otherwise the Completion will be declined.

With commercial and industrial systems that don’t control fuel price, the Controller should use a \$1 unit price for all available products to avoid potential declines due to the lack of unit price to resolve amount restrictions.

#### Customer Data
Customer data on a TREQ contains extra information gathered from prompts to the Cardholder or Attendant. On a TRESP, it contains the list of prompts that must be presented to the Cardholder or Attendant or a list of values to be used by the Terminal at capture, transaction or receipt printing.

Refer to [Customer Data](./Annexes/AN-Native-CustomerData-Annex.md) annex for a complete list of supported field names.

#### Re-prompting & Dual-Card Identification
ATIONET supports variable prompt-set definition for each card-type processed by the Host, allowing collection and validation of different entries for different type of cards, eventually this will allow to enforce different set of rules on different Device types.

There are three ways to implement this functionality on the Controller site:

1.  Devices with fixed-behavior.
    <br>Embedded devices, legacy devices or any other kind of equipment that implements a fixed or locally configurable behavior. In this case
    ATIONET will adapt to the device capabilities, reducing the functionality and eventually the types of cards supported.

2.  Devices depending on host-based re-prompt mechanism.
    <br>Controllers that do not have a local feature for selective prompts will prompt the User or Attendant only after receiving a TRESP requesting additional prompts. In this situation, the controller must retry the TREQ with the requested additional information after gathering the additional data from the cardholder or attendant. Is up to the Controller to handle the special flow of screens and messaging to the Host with or without showing the initial transaction as declined. From ATIONET standpoint, a TREQ requiring additional prompts will be considered Declined.

3.  Devices with pre-configured behavior based on PDL.
    <br>Controllers with the ability to process a full parameter download from the Host, could implement selective prompting before sending the TREQ to the Host, avoiding the need to process a double request.
    <br>It is worth to mention that a failure to submit a required prompt in this kind of devices, will cause a permanent failure to process such type of card, except if the device also has a host-based re-prompt mechanism –as in (b) type.

#### Authorization Code
The Authorization Code is the unique reference code that the Host determines for a specific transaction. Native protocol formats the code as 9 numerical digits, where the first one indicates the mode. Our current algorithm ensures that the codes cannot be repeated in an 8 hour window, giving the host more than enough security that the code is unique.

On Pre-Authorization/Completions message flows, the Controller must keep the Authorization Code sent on the Pre-Authorization TRESP and send it back to the Host on the Completion TREQ. This is a **mandatory** feature.

#### PIN Fields
The PIN entry on plain text, when the whole message or the communication themselves are encrypted.

#### Original Data
Original data on a TREQ contains extra information related to the original transaction that we want to cancel. Used in Cancellation, Void and Refund transactions.

Refer to [Original Data](./Annexes/AN-Native-OriginalData-Annex.md) annex for a complete list of supported field names.

## 7 Transaction Request (TREQ) Message Format

| Field Name                | Size | Type                       | Condition   | Descriptions/Field Value(s)                                                                                                                  |
| ------------------------- | ---- | -------------------------- | ----------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| ApplicationType           | 3    | string                     | Required    | Always “FCS” Fleet Control System                                                                                                            |
| ProcessingMode            | 1    | string                     | Required    | Refer to [Processing Modes](./Annexes/AN-Native-ProcessingModes-Annex.md) annex                                                              |
| TerminalIdentification    | Var  | string                     | Required    | Terminal Identification                                                                                                                      |
| DeviceTypeIdentifier      | 1    | string                     | Required    | “1” = Indoor Payment Terminal “2” = Outdoor Payment Terminal “3” = Card Reader in Dispenser “4” = Other Self-Service                         |
| TransactionCode           | 3    | string                     | Required    | Refer to [Transactions Codes](./Annexes/AN-Native-AuthTransactionCodes-Annex.md) annex                                                       |
| AccountType               | 1    | string                     | Required    | Refer to [Account Types](./Annexes/AN-Native-AccountTypes-Annex.md) annex                                                                    |
| EntryMethod               | 1    | string                     | Required    | “M” Manual Entry “S” Swap Card “T” Tag read                                                                                                  |
| ServiceCode               | 1    | string                     | Optional    | Reserved for future use                                                                                                                      |
| PumpNumber                | 2    | string                     | Optional    | “00”-“99”                                                                                                                                    |
| ProductCode               | Var  | string                     | Optional    | “0”-“9999”                                                                                                                                   |
| ProductUnitPrice          | Var  | decimal                    | Optional    | xxxxxxx.xxx                                                                                                                                  |
| ProductNetAmount          | Var  | decimal                    | Optional    | xxxxxxx.xx                                                                                                                                   |
| ProductTaxes              | Var  | Dictionary                 | Optional    | <”[Tax Description]”, [Tax Value]\>                                                                                                          |
| ProductAmount             | Var  | decimal                    | Optional    | xxxxxxx.xx                                                                                                                                   |
| ProductQuantity           | Var  | decimal                    | Optional    | xxxxxxx.xx                                                                                                                                   |
| TransactionNetAmount      | Var  | decimal                    | Optional    | xxxxxxx.xx                                                                                                                                   |
| ProductData               | Var  | List                       | Conditional | Refer to [Product Fields](#product-fields) in Field Description section                                                                      |
| TransactionAmount         | Var  | decimal                    | Optional    | xxxxxxx.xx                                                                                                                                   |
| UnitCode                  | Var  | string                     | Optional    | Refer to [Measurement Unit Codes](./Annexes/AN-Native-MeasurementUnitCodes-Annex.md) annex                                                   |
| CurrencyCode              | 3    | string                     | Optional    | Refer to [Currency Codes](#117-currency-codes) in Reference Tables Section                                                                   |
| BatchNumber               | Var  | int                        | Optional    | Refer to [Batch Number](#batch-number) in Field Description section                                                                          |
| ShiftNumber               | Var  | string                     | Optional    | Refer to [Shift Number](#shift-number) in Field Description section                                                                          |
| TransactionSequenceNumber | Var  | int                        | Required    | Refer to [Transaction Sequence Number](#transaction-sequence-number) in Field Description section                                            |
| LocalTransactionDate      | 8    | int                        | Required    | Local Transaction Date: yyyymmdd                                                                                                             |
| LocalTransactionTime      | 6    | int                        | Required    | Local Transaction Time: hhmmss                                                                                                               |
| PrimaryTrack              | Var  | string                     | Required    | Refer to [Track Data](#track-data) in Field Description section                                                                              |
| PrimaryPIN                | Var  | string                     | Conditional | Refer to [PIN Field](#pin-field) in Field Description section                                                                                |
| SecondaryTrack            | Var  | string                     | Optional    | Refer to Track Data in Field Description section                                                                                             |
| SecondaryPIN              | Var  | string                     | Optional    | Refer to [PIN Field](#pin-field) in Field Description section                                                                                |
| CustomerData              | Var  | Dictionary<string, string> | Conditional | Refer to [Customer Data](#customer-data) in Field Description section                                                                        |
| TransactionExtendedData   | Var  | string                     | Optional    | Designed to capture OBD extended data (On board Devices)                                                                                     |
| OriginalData              | Var  | Dictionary<string, string> | Conditional | Refer to [Original Data](#original-data) in Field Description section                                                                        |
| AuthorizationCode         | Var  | string                     | Conditional | Refer to [Authorization Code](#authorization-code) in Field Description section                                                              |
| InvoiceNumber             | Var  | string                     | Optional    |                                                                                                                                              |
| ResponseCode              | 5    | string                     | Conditional | Use only when informing a Response not created by the Host (for example a local authorization), otherwise it should not be echoed from TRESP |
| ResponseText              | 20   | string                     | Conditional | Idem Response Code                                                                                                                           |
| LongResponseText          | 200  | string                     | Conditional | Idem Response Code                                                                                                                           |
| OldPin                    | 200  | string                     | Conditional | Only used when sending a 300 Transaction Code                                                                                                |
| NewPin                    | 200  | string                     | Conditional | Only used when sending a 300 Transaction Code                                                                                                |
| ConfirmationPin           | 200  | string                     | Conditional | Only used when sending a 300 Transaction Code                                                                                                |
| IdTransactionContingency  |  -   | Guid                       | Conditional | Only used when sending a 126 Transaction Code. Use to send contingency id                                                                    |


## 8 Transaction Response (TRESP) Message Format

| Field Name                | Size | Type                       | Condition   | Descriptions/Field Value(s)                                                                |
| ------------------------- | ---- | -------------------------- | ----------- | ------------------------------------------------------------------------------------------ |
| ApplicationType           | 3    | string                     | Required    | Echoed from TREQ                                                                           |
| ProcessingMode            | 1    | string                     | Required    | Echoed from TREQ                                                                           |
| MessageFormatVersion      | 3    | string                     | Required    | Echoed from TREQ                                                                           |
| TerminalIdentification    | Var  | string                     | Required    | Echoed from TREQ                                                                           |
| DeviceTypeIdentifier      | 1    | string                     | Required    | Echoed from TREQ                                                                           |
| TransactionCode           | 3    | string                     | Required    | Refer to [Transactions Codes](./Annexes/AN-Native-AuthTransactionCodes-Annex.md) annex     |
| AccountType               | 1    | string                     | Required    | Echoed from TREQ                                                                           |
| EntryMethod               | 1    | string                     | Required    | Echoed from TREQ                                                                           |
| PumpNumber                | 2    | string                     | Optional    | Echoed from TREQ                                                                           |
| ProductCode               | 4    | string                     | Conditional | Refer to [Product Fields](./Annexes/AN-Native-ProductData-Annex.md) annex                  |
| ProductUnitPrice          | Var  | decimal                    | Conditional | xxxxxxx.xxx                                                                                |
| ProductAmount             | Var  | decimal                    | Conditional | xxxxxxx.xx                                                                                 |
| ProductQuantity           | Var  | decimal                    | Conditional | xxxxxxx.xx                                                                                 |
| ProductData               | Var  | List                       | Conditional | Refer to [Product Fields](#product-fields) in Field Description section                    |
| TransactionAmount         | Var  | decimal                    | Conditional | xxxxxxx.xx                                                                                 |
| UnitCode                  | Var  | string                     | Optional    | Refer to [Measurement Unit Codes](./Annexes/AN-Native-MeasurementUnitCodes-Annex.md) annex |
| CurrencyCode              | 3    | string                     | Optional    | Refer to [Currency Code](#currency-code) in Field Description section                      |
| BatchNumber               | Var  | int                        | Optional    | Echoed from TREQ                                                                           |
| ShiftNumber               | Var  | string                     | Optional    | Echoed from TREQ                                                                           |
| TransactionSequenceNumber | Var  | int                        | Required    | Echoed from TREQ                                                                           |
| LocalTransactionDate      | 8    | int                        | Required    | Echoed from TREQ                                                                           |
| LocalTransactionTime      | 6    | int                        | Required    | Echoed from TREQ                                                                           |
| CustomerData              | Var  | Dictionary<string, string> | Conditional | Refer to [Customer Data](./Annexes/AN-Native-CustomerData-Annex.md) annex                  |
| AuthorizationCode         | Var  | string                     | Conditional | Refer to [Authorization Code](#authorization-code) in Field Description section            |
| InvoiceNumber             | Var  | string                     | Optional    |                                                                                            |
| ResponseCode              | 5    | string                     | Required    | Refer to [Response Codes](./Annexes/AN-Native-AuthResponseCodes-Annex.md) annex            |
| ResponseText              | 20   | string                     | Required    | Message from the Network                                                                   |
| ReceiptData               | Var  | Dictionary<string, string> | Conditional |                                                                                            |
| LongResponseText          | 200  | string                     | Conditional |                                                                                            |

## 9 Satellite TAG Validation Request (VREQ) Message Format

| Field Name             | Size | Type   | Condition | Descriptions/Field Value(s)                                                            |
| ---------------------- | ---- | ------ | --------- | -------------------------------------------------------------------------------------- |
| ApplicationType        | 3    | string | Required  | Always “FCS” Fleet Control System                                                      |
| ProcessingMode         | 1    | string | Required  | “0” = Host Capture Only “1” = Host processing required                                 |
| MessageFormatVersion   | 3    | string | Required  | Current Host Message Version = “1.2”                                                   |
| TerminalIdentification | Var  | string | Required  |                                                                                        |
| TransactionCode        | 3    | string | Required  | Refer to [Transactions Codes](./Annexes/AN-Native-AuthTransactionCodes-Annex.md) annex |
| LocalDate              | 8    | int    | Required  | Local Transaction Date: yyyymmdd                                                       |
| LocalTime              | 6    | int    | Required  | Local Transaction Time: hhmmss                                                         |
| TagId1                 | Var  | string | Required  | First TAG’s ID or Secure ID                                                            |
| TagId2                 | Var  | string | Required  | Second TAG’s ID or Secure ID                                                           |
| AuthorizationCode      | Var  | string | Required  | Auth code received for the ongoing transaction                                         |

## 10 Satellite TAG Validation Response (VRESP) Message Format
| Field Name             | Size | Type   | Condition | Descriptions/Field Value(s)                                                            |
| ---------------------- | ---- | ------ | --------- | -------------------------------------------------------------------------------------- |
| ApplicationType        | 3    | string | Required  | Echoed from VREQ                                                                       |
| ProcessingMode         | 1    | string | Required  | Echoed from VREQ                                                                       |
| MessageFormatVersion   | 3    | string | Required  | Echoed from VREQ                                                                       |
| TerminalIdentification | Var  | string | Required  | Echoed from VREQ                                                                       |
| TransactionCode        | 3    | string | Required  | Refer to [Transactions Codes](./Annexes/AN-Native-AuthTransactionCodes-Annex.md) annex |
| LocalDate              | 8    | int    | Required  | Echoed from VREQ                                                                       |
| LocalTime              | 6    | int    | Required  | Echoed from VREQ                                                                       |
| AuthorizationCode      | Var  | string | Required  | Echoed from VREQ                                                                       |
| ResponseCode           | 5    | string | Required  | “0” = Authorized, !”0” = Not Authorized                                                |
| ResponseText           | 20   | string | Required  | Message from the Network                                                               |

## 11 Identification Pin Change Request (PREQ) Message Format
| Field Name             | Size | Type   | Condition | Descriptions/Field Value(s)                                                            |
| ---------------------- | ---- | ------ | --------- | -------------------------------------------------------------------------------------- |
| ApplicationType        | 3    | string | Required  | Echoed from VREQ                                                                       |
| ProcessingMode         | 1    | string | Required  | Echoed from VREQ                                                                       |
| MessageFormatVersion   | 3    | string | Required  | Echoed from VREQ                                                                       |
| TerminalIdentification | Var  | string | Required  | Echoed from VREQ                                                                       |
| TransactionCode        | 3    | string | Required  | Refer to [Transactions Codes](./Annexes/AN-Native-AuthTransactionCodes-Annex.md) annex |
| LocalDate              | 8    | int    | Required  | Echoed from VREQ                                                                       |
| LocalTime              | 6    | int    | Required  | Echoed from VREQ                                                                       |
| AuthorizationCode      | Var  | string | Required  | Echoed from VREQ                                                                       |
| ResponseCode           | 5    | string | Required  | “0” = Authorized, !”0” = Not Authorized                                                |
| ResponseText           | 20   | string | Required  | Message from the Network                                                               |

## 12 Identification Pin Change Response (PRESP) Message Format
| Field Name             | Size | Type   | Condition | Descriptions/Field Value(s)                                                            |
| ---------------------- | ---- | ------ | --------- | -------------------------------------------------------------------------------------- |
| ApplicationType        | 3    | string | Required  | Echoed from VREQ                                                                       |
| ProcessingMode         | 1    | string | Required  | Echoed from VREQ                                                                       |
| MessageFormatVersion   | 3    | string | Required  | Echoed from VREQ                                                                       |
| TerminalIdentification | Var  | string | Required  | Echoed from VREQ                                                                       |
| TransactionCode        | 3    | string | Required  | Refer to [Transactions Codes](./Annexes/AN-Native-AuthTransactionCodes-Annex.md) annex |
| LocalDate              | 8    | int    | Required  | Echoed from VREQ                                                                       |
| LocalTime              | 6    | int    | Required  | Echoed from VREQ                                                                       |
| AuthorizationCode      | Var  | string | Required  | Echoed from VREQ                                                                       |
| ResponseCode           | 5    | string | Required  | “0” = Authorized, !”0” = Not Authorized                                                |
| ResponseText           | 20   | string | Required  | Message from the Network                                                               |

## 13 Message Samples

### 13.1.1 Pre Authorization Request Sample

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
    "ProductUnitPrice": 5,
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
    "ReceiptData": null,
    "IdTransactionContingency": ""
}
```

### 13.1.2 Pre Authorization Response Sample
```json
{
    "ApplicationType": "FCS",
    "ProcessingMode": "1",
    "MessageFormatVersion": "1.3",
    "TerminalIdentification": "AN111111",
    "DeviceTypeIdentifier": "4",
    "TransactionCode": "110",
    "AccountType": "1",
    "EntryMethod": "S",
    "PumpNumber": "1",
    "ProductCode": "3",
    "ProductUnitPrice": 5,
    "ProductAmount": 20,
    "ProductQuantity": 4,
    "ProductData": null,
    "TransactionAmount": null,
    "UnitCode": "l",
    "CurrencyCode": "ARS",
    "BatchNumber": null,
    "ShiftNumber": null,
    "TransactionSequenceNumber": 1,
    "LocalTransactionDate": 20190614,
    "LocalTransactionTime": 121500,
    "CustomerData": {
        "ContractMode": "0"
    },
    "AuthorizationCode": "033031219",
    "InvoiceNumber": null,
    "ResponseCode": "00000",
    "ResponseText": "Authorized",
    "ReceiptData": "{\"CustomerName\":\"Driver Driver\",\"CustomerIdentification\":\"0003\",\"CustomerPlate\":\"\",\"CustomerDriverName\":\"Driver Driver\",\"CustomerPAN\":\"0000040006681541713\",\"CustomerLabel\":\"0000040006681541713\",\"CompanyName\":\"Network Company\",\"CompanyCode\":\"002\",\"TransactionId\":\"f50d47ad-eba6-47f5-bfec-18c90e151794\",\"FuelName\":\"Diesel\",\"AuthorizationType\":0,\"CustomerTruckUnitNumber\":null,\"CustomerOdometer\":\"\",\"CustomerDriverId\":null,\"CustomerCustom0Label\":\"Prueba Personalizable 1\",\"CustomerCustom0Value\":null,\"CustomerCustom1Label\":\"prueba de campo embozado\",\"CustomerCustom1Value\":null,\"CustomerCustom2Label\":\"p3\",\"CustomerCustom2Value\":null,\"CustomerCustom3Label\":\"P4\",\"CustomerCustom3Value\":null,\"CustomerCustomOperation0Label\":\"Prueba Operaciones 1\",\"CustomerCustomOperation0Value\":\"false\",\"CustomerCustomOperation1Label\":\"CO2\",\"CustomerCustomOperation1Value\":\"false\",\"CustomerCustomOperation2Label\":\"CO3\",\"CustomerCustomOperation2Value\":\"false\",\"CustomerCustomOperation3Label\":\"CO4\",\"CustomerCustomOperation3Value\":\"false\",\"CustomerCustomOperation4Label\":\"CO5\",\"CustomerCustomOperation4Value\":\"false\",\"ContractCode\":\"6\",\"CompanyTaxPayerId\":\"654321\",\"CompanyTaxPayerCategory\":null,\"CompanyStreet1\":\"villaroel 1730\",\"CompanyStreet2\":null,\"ContractBalanceMode\":\"1\"}",
    "LongResponseText": "Authorized",
    "CompanyPrice": null
}
```


### 13.2.1 Completion Request Sample

```json
{
    "ProcessingMode": "1",
    "SystemModel": "",
    "SystemVersion": "",
    "TransactionCode": "120",
    "EntryMethod": "S",
    "CurrencyCode": "ARS",
    "UnitCode": "l",
    "ApplicationType": "FCS",
    "AccountType": "1",
    "MessageFormatVersion": "1.3",
    "DeviceTypeIdentifier": "4",
    "PumpNumber": "1",
    "AuthorizationCode": "033031219",
    "TerminalIdentification": "AN111111",
    "TransactionSequenceNumber": 2,
    "LocalTransactionDate": 20190614,
    "LocalTransactionTime": 122000,
    "PrimaryTrack": "9532013015986508780=3905=000000",
    "PrimaryPin": null,
    "SecondaryTrack": null,
    "SecondaryPin": null,
    "ProductCode": "3",
    "ProductQuantity": 4,
    "ProductAmount": 20,
    "TransactionAmount": null,
    "ProductUnitPrice": 5,
    "ProductNetAmount": null,
    "ProductTaxes": null,
    "TransactionNetAmount": null,
    "CustomerData": {},
    "OriginalData": {},
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

### 13.2.2 Completion Response Sample
```json

{
    "ApplicationType": "FCS",
    "ProcessingMode": "1",
    "MessageFormatVersion": "1.3",
    "TerminalIdentification": "AN111111",
    "DeviceTypeIdentifier": "4",
    "TransactionCode": "130",
    "AccountType": "1",
    "EntryMethod": "S",
    "PumpNumber": "1",
    "ProductCode": "3",
    "ProductUnitPrice": 5,
    "ProductAmount": 20,
    "ProductQuantity": 4,
    "ProductData": [],
    "TransactionAmount": null,
    "UnitCode": null,
    "CurrencyCode": null,
    "BatchNumber": null,
    "ShiftNumber": null,
    "TransactionSequenceNumber": 2,
    "LocalTransactionDate": 20190614,
    "LocalTransactionTime": 122000,
    "CustomerData": {
        "ContractMode": "0"
    },
    "AuthorizationCode": "033031219",
    "InvoiceNumber": null,
    "ResponseCode": "00000",
    "ResponseText": "Authorized",
    "ReceiptData": "{\"CustomerName\":\"Driver Driver\",\"CustomerIdentification\":\"0003\",\"CustomerPlate\":\"\",\"CustomerDriverName\":\"Driver Driver\",\"CustomerPAN\":\"0000040006681541713\",\"CustomerLabel\":\"0000040006681541713\",\"CompanyName\":\"Network Company\",\"CompanyCode\":\"002\",\"TransactionId\":\"9afdb073-ffa6-458f-b99b-5fbba5e9bda0\",\"FuelName\":\"Diesel\",\"AuthorizationType\":0,\"CustomerTruckUnitNumber\":null,\"CustomerOdometer\":\"\",\"CustomerDriverId\":null,\"CustomerCustom0Label\":\"Prueba Personalizable 1\",\"CustomerCustom0Value\":null,\"CustomerCustom1Label\":\"prueba de campo embozado\",\"CustomerCustom1Value\":null,\"CustomerCustom2Label\":\"p3\",\"CustomerCustom2Value\":null,\"CustomerCustom3Label\":\"P4\",\"CustomerCustom3Value\":null,\"CustomerCustomOperation0Label\":\"Prueba Operaciones 1\",\"CustomerCustomOperation0Value\":\"false\",\"CustomerCustomOperation1Label\":\"CO2\",\"CustomerCustomOperation1Value\":\"false\",\"CustomerCustomOperation2Label\":\"CO3\",\"CustomerCustomOperation2Value\":\"false\",\"CustomerCustomOperation3Label\":\"CO4\",\"CustomerCustomOperation3Value\":\"false\",\"CustomerCustomOperation4Label\":\"CO5\",\"CustomerCustomOperation4Value\":\"false\",\"ContractCode\":\"6\",\"CompanyTaxPayerId\":\"654321\",\"CompanyTaxPayerCategory\":null,\"CompanyStreet1\":\"villaroel 1730\",\"CompanyStreet2\":null,\"ContractBalanceMode\":\"1\"}",
    "LongResponseText": "Authorized",
    "CompanyPrice": {
        "ProductUnitPrice": 5,
        "ProductUnitPriceBase": 5,
        "ProductAmount": 20,
        "TransactionAmount": 20,
        "Modifiers": []
    }
}



```


## Appendix A - Native Authorization Protocol Messages

Check this [document](AN-Native_Auth_Protocol_Messages.md) to have detailed information about each field in each message under the Native Authorization Protocol 
