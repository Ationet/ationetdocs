![ationetlogo](Content/Images/ATIOnetLogo_250x70.png)
# ATIONet - Native Retail Protocol Specification v1.0

<table>
	<tr>
		<th colspan="2" align="left">Document Information</th>
	</tr>
	<tr>
		<td>File:</td>
		<td>ATIONet-Native_Retail_Protocol-Spec-v1</td>
	</tr>
	<tr>
		<td>Doc Version:</td>
		<td>1.0</td>
	</tr>
	<tr>
		<td>Release Date:</td>
		<td>20, March 2015</td>
	</tr>
	<tr>
		<td>Author:</td>
		<td>ATIO International LLC</td>
	</tr>
</table>

<table>
	<tr>
		<th colspan="3" align="left">Change Log</th>
	</tr>
	<tr>
		<td>Ver.</td>
		<td>Date</td>
		<td>Change Summary</td>
	</tr>
	<tr valign="top">
		<td>1.0</td>
		<td>20/March/2015</td>
		<td>Initial version.</td>
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
- Retail Transaction Request (RREQ) Message Format
- Retail Transaction Response (RRESP) Message Format
- Retail Summary Movements Request (RSUMREQ) Message Format
- Retail Summary Movements Response (RSUMRESP) Message Format
- Transaction Data Structures
- Reference Tables
	- Transaction Codes
	- Currency Codes
	- Authorization Codes

<!-- /MarkdownTOC -->

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

#### RREQ
Transaction Request.

#### RRESP
Transaction Response.

## ATIOnet Integration Documentation Scope

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

## Scope

.

### Scope Details

Protocol: ATIONet Native Retail Protocol

Version: Version 1.0

API URI: native.ationet.com/v1/retail

### Supported Transactions

<table>
	<thead>
		<tr valign="center">
			<th rowspan="2" width="250" align="left">Name</th>
			<th colspan="2" align="center">Protocol Ver.</th>
			<th rowspan="2" align="left">Description</th>
		</tr>
		<tr valign="top">
			<th align="center">	Initial</th>
			<th align="center">Change</th>
		 </tr>
	</thead>
	<tbody>
		 <tr valign="top">
			<td align="left">Sale Records Upload</td>
			<td align="center">1.0</td>
			<td></td>
			<td align="left">Used to post a sale by sale POS data.</td>
		 </tr>
		 <tr valign="top">
			<td align="left">Movements Summary Upload</td>
			<td align="center">1.0</td>
			<td></td>
			<td align="left">Used to post summary shift data from POS.</td>
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

#### Shift Number
Site's business period ID

The Controller application can manage the Shift Number and meaning as needed. It may be day’s shift number, weekly batches, split-batches, etc., although this is a fixed length field, therefore the format must be maintained.

#### Customer Data
Customer data on a RREQ contains extra information gathered from prompts to the Cardholder or Attendant.

#### Authorization Code
The Host will return the Authorization Code on all approved transactions.

## Retail Transaction Request (RREQ) Message Format

<table>
	<thead>
		<tr valign="top">
			<th align="left">Field Name</th>
			<th align="center">Size</th>
			<th align="left" width="200">Type</th>
			<th align="left">Condition</th>
			<th align="left">Descriptions/Field Value(s)</th>
		</tr>
	</thead>
	<tbody>
		<tr valign="top">
			<td align="left">ApplicationType</td>
			<td align="left">4</td>
			<td align="left">string</td>
			<td align="left">Required</td>
			<td align="left">Always “LTY” Loyalty System</td>
		</tr>
		<tr valign="top">
			<td align="left">ProcessingMode</td>
			<td align="left">1</td>
			<td align="left">string</td>
			<td align="left">Required</td>
			<td align="left">Always “0” = Host Capture Only in this version.</td>
		</tr>
		<tr valign="top">
			<td align="left">MessageFormatVersion</td>
			<td align="left">3</td>
			<td align="left">string</td>
			<td align="left">Required</td>
			<td align="left">Current Host Message Version = “1.0”</td>
		</tr>
		<tr valign="top">
			<td align="left">TerminalIdentification</td>
			<td align="left">Var</td>
			<td align="left">string</td>
			<td align="left">Required</td>
			<td align="left">Terminal Identification</td>
		</tr>
		<tr valign="top">
			<td align="left">DeviceTypeIdentifier</td>
			<td align="left">1</td>
			<td align="left">string</td>
			<td align="left">Required</td>
			<td align="left">“1” = Indoor Payment Terminal
				<br>“2” = Outdoor Payment Terminal
				<br>“3” = Card Reader in Dispenser
				<br>“4” = Other Self-Service</td>
		</tr>
		<tr valign="top">
			<td align="left">SystemModel</td>
			<td align="left">10</td>
			<td align="left">string</td>
			<td align="left">Required</td>
			<td align="left">Refer to System Model and System Version in Field Description section</td>
		</tr>
		<tr valign="top">
			<td align="left">SystemVersion</td>
			<td align="left">10</td>
			<td align="left">string</td>
			<td align="left">Required</td>
			<td align="left">Refer to System Model and System Version in Field Description section</td>
		</tr>
		<tr valign="top">
			<td align="left">TransactionSequenceNumber</td>
			<td align="left">Var</td>
			<td align="left">int</td>
			<td align="left">Required</td>
			<td align="left">Refer to Transaction Sequence Number in Field Description section</td>
		</tr>
		<tr valign="top">
			<td align="left">TransactionCode</td>
			<td align="left">3</td>
			<td align="left">string</td>
			<td align="left">Required</td>
			<td align="left">Refer to Transaction Codes in Reference Tables Section</td>
		</tr>
		<tr valign="top">
			<td align="left">SiteCode</td>
			<td align="left">10</td>
			<td align="left">string</td>
			<td align="left">Required</td>
			<td align="left">Site ID. Does not need to match an ATIOnet Site in this version</td>
		</tr>
		<tr valign="top">
			<td align="left">RegisterCode</td>
			<td align="left">10</td>
			<td align="left">string</td>
			<td align="left">Required</td>
			<td align="left">Register or Point of Sale ID</td>
		</tr>
		<tr valign="top">
			<td align="left">TransactionTypeCode</td>
			<td align="left">3</td>
			<td align="left">string</td>
			<td align="left">Required</td>
			<td align="left">“101” = Sale, taxable document
				<br>“101” = Sale, non-taxable document
				<br>“110” = Automatic receipt taxable
				<br>“111” = Automatic receipt non-taxable
				<br>“120” = Fuelings summary receipt taxable
				<br>“121” = Fuelings summary receipt non-taxable
				<br>“130” = Delivery Note taxable
				<br>“131” = Delivery Note non-taxable
				<br>“200” = Full refund of a taxable document
				<br>“210” = Partial Refund refund of a taxable document
				<br>“201” = Full refund of a non-taxable document
				<br>“211” = Partial Refund refund of a non-taxable document
				<br>“300” = Not-for-sale Internal use
				<br>“310” = Other non-sale</p>			
			</td>
		</tr>
		<tr valign="top">
			<td align="left">FullDocumentNumber</td>
			<td align="left">30</td>
			<td align="left">string</td>
			<td align="left">Required</td>
			<td align="left">Transaction's receipt complete numeration, including masking characters if any, as mandated by fiscal regulations</td>
		<tr valign="top">
			<td align="left">ReferencedFullDocumentNumber</td>
			<td align="left">30</td>
			<td align="left">string</td>
			<td align="left">Conditional</td>
			<td align="left">When transaction is a Refund, this field must contain the original sale or delivery note being voided, including masking characters if any, as mandated by fiscal regulations</td>
		<tr valign="top">
			<td align="left">CashierCode</td>
			<td align="left">10</td>
			<td align="left">string</td>
			<td align="left">Optional</td>
			<td align="left">Code of user or employee who ringed the sale</td>
		</tr>
		<tr valign="top">
			<td align="left">CustomerCode</td>
			<td align="left">10</td>
			<td align="left">string</td>
			<td align="left">Optional</td>
			<td align="left">Transaction's customer code matching a valid ATIOnet Company Code. When using ATIOnet Companies as customers, Company Data section is not mandatory.</td>
		<tr valign="top">
			<td align="left">TransactionAmount</td>
			<td align="left">Var</td>
			<td align="left">decimal, signed</td>
			<td align="left">Required</td>
			<td align="left">xxxxxxx.xx </br>Grand Total of the transaction</td>
		</tr>
		<tr valign="top">
			<td align="left">CurrencyCode</td>
			<td align="left">3</td>
			<td align="left">string</td>
			<td align="left">Optional</td>
			<td align="left">Refer to Currency Codes in Reference Tables Section</td>
		</tr>
		<tr valign="top">
			<td align="left">ShiftNumber</td>
			<td align="left">Var</td>
			<td align="left">string</td>
			<td align="left">Optional</td>
			<td align="left">Refer to Shift Number in Field Description section</td>
		</tr>
		<tr valign="top">
			<td align="left">LocalTransactionDate</td>
			<td align="left">8</td>
			<td align="left">int</td>
			<td align="left">Required</td>
			<td align="left">Local Transaction Date: yyyymmdd</td>
		</tr>
		<tr valign="top">
			<td align="left">LocalTransactionTime</td>
			<td align="left">6</td>
			<td align="left">int</td>
			<td align="left">Required</td>
			<td align="left">Local Transaction Time: hhmmss</td>
		</tr>
		<tr valign="top">
			<td align="left">ItemsData</td>
			<td align="left">Var</td>
			<td align="left">String < ItemsData > </td>
			<td align="left">Required</td>
			<td align="left">Refer to Item Data  in the Transaction Data Structures section</td>
		</tr>
		<tr valign="top">
			<td align="left">CompanyData</td>
			<td align="left">Var</td>
			<td align="left">Dictionary string, string</td>
			<td align="left">Conditional</td>
			<td align="left">Refer to Company Data in the Transaction Data Structures section</td>
		</tr>
		<tr valign="top">
			<td align="left">LoyaltyData</td>
			<td align="left">Var</td>
			<td align="left">Dictionary string, string</td>
			<td align="left">Conditional</td>
			<td align="left">Refer to Loyalty Data in the Transaction Data Structures section</td>
		</tr>
		<tr valign="top">
			<td align="left">CustomerData</td>
			<td align="left">Var</td>
			<td align="left">Dictionary string, string</td>
			<td align="left">Conditional</td>
			<td align="left">Refer to Customer Data in the Transaction Data Structures section</td>
		</tr>
		<tr valign="top">
			<td align="left">DocumentData</td>
			<td align="left">Var</td>
			<td align="left">Dictionary string, string</td>
			<td align="left">Required</td>
			<td align="left">Refer to Document Data in the Transaction Data Structures section</td>
		</tr>
		<tr valign="top">
			<td align="left">TaxesData</td>
			<td align="left">Var</td>
			<td align="left">Dictionary string, string</td>
			<td align="left">Conditional</td>
			<td align="left">Refer to Taxes Data in the Transaction Data Structures section</td>
		</tr>
		<tr valign="top">
			<td align="left">MoPData</td>
			<td align="left">Var</td>
			<td align="left">Dictionary string, string</td>
			<td align="left">Optional</td>
			<td align="left">Refer to Method-of-Payment Data in the Transaction Data Structures section</td>
		</tr>
	</tbody>
</table>	

## Retail Transaction Response (RRESP) Message Format

<table>
	<thead>
		<tr valign="top">
			<th align="left">Field Name</th>
			<th align="left">Size</th>
			<th align="left">Type</th>
			<th align="left">Condition</th>
			<th align="left">Descriptions/Field Value(s)</th>
		</tr>
	</thead>
	<tbody>
		<tr valign="top">
			<td align="left">ApplicationType</td>
			<td align="left">3</td>
			<td align="left">string</td>
			<td align="left">Required</td>
			<td align="left">Echoed from LREQ</td>
		</tr>
		<tr valign="top">
			<td align="left">ProcessingMode</td>
			<td align="left">1</td>
			<td align="left">string</td>
			<td align="left">Required</td>
			<td align="left">Echoed from LREQ</td>
		</tr>
		<tr valign="top">
			<td align="left">MessageFormatVersion</td>
			<td align="left">3</td>
			<td align="left">string</td>
			<td align="left">Required</td>
			<td align="left">Echoed from LREQ</td>
		</tr>
		<tr valign="top">
			<td align="left">TerminalIdentification</td>
			<td align="left">Var</td>
			<td align="left">string</td>
			<td align="left">Required</td>
			<td align="left">Echoed from LREQ</td>
		</tr>
		<tr valign="top">
			<td align="left">DeviceTypeIdentifier</td>
			<td align="left">1</td>
			<td align="left">string</td>
			<td align="left">Required</td>
			<td align="left">Echoed from LREQ</td>
		</tr>
		<tr valign="top">
			<td align="left">TransactionCode</td>
			<td align="left">3</td>
			<td align="left">string</td>
			<td align="left">Required</td>
			<td align="left">Refer to Transaction Codes in Reference Tables Section</td>
		</tr>
		<tr valign="top">
			<td align="left">TransactionSequenceNumber</td>
			<td align="left">Var</td>
			<td align="left">int</td>
			<td align="left">Required</td>
			<td align="left">Echoed from LREQ</td>
		</tr>
		<tr valign="top">
			<td align="left">AuthorizationCode</td>
			<td align="left">Var</td>
			<td align="left">string</td>
			<td align="left">Conditional</td>
			<td align="left">Refer to Authorization Code in Field Description section</td>
		</tr>
		<tr valign="top">
			<td align="left">ResponseCode</td>
			<td align="left">5</td>
			<td align="left">string</td>
			<td align="left">Required</td>
			<td align="left">“0” = Authorized, !”0” = Not Authorized</td>
		</tr>
		<tr valign="top">
			<td align="left">ResponseText</td>
			<td align="left">20</td>
			<td align="left">string</td>
			<td align="left">Required</td>
			<td align="left">Message from the Network</td>
		</tr>
	</tbody>
</table>	


## Retail Summary Movements Request (RSUMREQ) Message Format

<table>
	<thead>
		<tr valign="top">
			<th align="left">Field Name</th>
			<th align="center">Size</th>
			<th align="left" width="200">Type</th>
			<th align="left">Condition</th>
			<th align="left">Descriptions/Field Value(s)</th>
		</tr>
	</thead>
	<tbody>
		<tr valign="top">
			<td align="left">ApplicationType</td>
			<td align="left">4</td>
			<td align="left">string</td>
			<td align="left">Required</td>
			<td align="left">Always “RTL” Retail System</td>
		</tr>
		<tr valign="top">
			<td align="left">ProcessingMode</td>
			<td align="left">1</td>
			<td align="left">string</td>
			<td align="left">Required</td>
			<td align="left">Always “0” = Host Capture Only in this version.</td>
		</tr>
		<tr valign="top">
			<td align="left">MessageFormatVersion</td>
			<td align="left">3</td>
			<td align="left">string</td>
			<td align="left">Required</td>
			<td align="left">Current Host Message Version = “1.0”</td>
		</tr>
		<tr valign="top">
			<td align="left">TerminalIdentification</td>
			<td align="left">Var</td>
			<td align="left">string</td>
			<td align="left">Required</td>
			<td align="left">Terminal Identification</td>
		</tr>
		<tr valign="top">
			<td align="left">DeviceTypeIdentifier</td>
			<td align="left">1</td>
			<td align="left">string</td>
			<td align="left">Required</td>
			<td align="left">“1” = Indoor Payment Terminal
				<br>“2” = Outdoor Payment Terminal
				<br>“3” = Card Reader in Dispenser
				<br>“4” = Other Self-Service</td>
		</tr>
		<tr valign="top">
			<td align="left">SystemModel</td>
			<td align="left">10</td>
			<td align="left">string</td>
			<td align="left">Required</td>
			<td align="left">Refer to System Model and System Version in Field Description section</td>
		</tr>
		<tr valign="top">
			<td align="left">SystemVersion</td>
			<td align="left">10</td>
			<td align="left">string</td>
			<td align="left">Required</td>
			<td align="left">Refer to System Model and System Version in Field Description section</td>
		</tr>
		<tr valign="top">
			<td align="left">TransactionSequenceNumber</td>
			<td align="left">Var</td>
			<td align="left">int</td>
			<td align="left">Required</td>
			<td align="left">Refer to Transaction Sequence Number in Field Description section</td>
		</tr>
		<tr valign="top">
			<td align="left">TransactionCode</td>
			<td align="left">3</td>
			<td align="left">string</td>
			<td align="left">Required</td>
			<td align="left">Refer to Transaction Codes in Reference Tables Section</td>
		</tr>
		<tr valign="top">
			<td align="left">SiteCode</td>
			<td align="left">10</td>
			<td align="left">string</td>
			<td align="left">Required</td>
			<td align="left">Site ID. Does not need to match an ATIOnet Site in this version</td>
		</tr>
		<tr valign="top">
			<td align="left">SiteSubCode</td>
			<td align="left">10</td>
			<td align="left">string</td>
			<td align="left">Optional</td>
			<td align="left">Business sub-division on the site structure, may represent a business line, store area, forecourt Id on a multi-forecourt site or pumps group on a single-forecourt site.</td>
		<tr valign="top">
			<td align="left">ShiftNumber</td>
			<td align="left">Var</td>
			<td align="left">string</td>
			<td align="left">Required</td>
			<td align="left">Refer to Shift Number in Field Description section</td>
		</tr>
		<tr valign="top">
			<td align="left">ShiftNumberSecondary</td>
			<td align="left">Var</td>
			<td align="left">string</td>
			<td align="left">Optional</td>
			<td align="left">Refer to Shift Number in Field Description section</td>
		</tr>
		<tr valign="top">
			<td align="left">CurrencyCode</td>
			<td align="left">3</td>
			<td align="left">string</td>
			<td align="left">Optional</td>
			<td align="left">Refer to Currency Codes in Reference Tables Section</td>
		</tr>
		<tr valign="top">
			<td align="left">BusinessDate</td>
			<td align="left">8</td>
			<td align="left">int</td>
			<td align="left">Optional</td>
			<td align="left">The accounting date of the reported period: yyyymmdd</td>
		</tr>
		<tr valign="top">
			<td align="left">LocalApprovalDate</td>
			<td align="left">8</td>
			<td align="left">int</td>
			<td align="left">Optional</td>
			<td align="left">Date of reconciliation or approval of the reported period: yyyymmdd</td>
		</tr>
		<tr valign="top">
			<td align="left">LocalApprovalTime</td>
			<td align="left">6</td>
			<td align="left">int</td>
			<td align="left">Optional</td>
			<td align="left">Time  of reconciliation or approval of the reported period: hhmmss</td>
		</tr>
		<tr valign="top">
			<td align="left">PeriodStartingDate</td>
			<td align="left">8</td>
			<td align="left">int</td>
			<td align="left">Required</td>
			<td align="left">From date of the reported period: yyyymmdd</td>
		</tr>
		<tr valign="top">
			<td align="left">PeriodStartingTime</td>
			<td align="left">6</td>
			<td align="left">int</td>
			<td align="left">Required</td>
			<td align="left">From time of the reported period: hhmmss</td>
		</tr>
		<tr valign="top">
			<td align="left">PeriodEndingDate</td>
			<td align="left">8</td>
			<td align="left">int</td>
			<td align="left">Required</td>
			<td align="left">To date of the reported period: yyyymmdd</td>
		</tr>
		<tr valign="top">
			<td align="left">PeriodEndingTime</td>
			<td align="left">6</td>
			<td align="left">int</td>
			<td align="left">Required</td>
			<td align="left">To time of the reported period: hhmmss</td>
		</tr>
		<tr valign="top">
			<td align="left">SalesByMethodOfPaymentData</td>
			<td align="left">Var</td>
			<td align="left">Dictionary  string, string</td>
			<td align="left">Optional</td>
			<td align="left">List of code and total pairs. One entry for each MethodOfPayment with sales on the reported period
				<p>Refer to Sales By Method-Of-Payment Data in the Transaction Data Structures section </p>
			</td>
		</tr>
			<td align="left">SalesByCashierData</td>
			<td align="left">Var</td>
			<td align="left">Dictionary  string, string</td>
			<td align="left">Optional</td>
			<td align="left">List of code and total pairs. One entry for each Cashier with sales on the reported period
				<p>Refer to Sales By Cashier Data in the Transaction Data Structures section </p>
			</td>
		</tr>
		<tr>
			<td align="left">SalesByRegisterData</td>
			<td align="left">Var</td>
			<td align="left">Dictionary < string, string ></td>
			<td align="left">Optional</td>
			<td align="left">List of code and total pairs. One entry for each Register or POS with sales on the reported period
				<p>Refer to Sales By Register Data in the Transaction Data Structures section</p>
			</td>
		</tr>
		<tr valign="top">
			<td align="left">SalesByMerchandiseCodeData</td>
			<td align="left">Var</td>
			<td align="left">String SalesByMerchandiseData</td>
			<td align="left">Optional</td>
			<td align="left">Dry Stock sales by product code.
				<p>Refer to Sales By Merchandise Code in the Transaction Data Structures section</p>
			</td>
		</tr>
		<tr valign="top">
			<td align="left">SalesByFuelGradeData</td>
			<td align="left">Var</td>
			<td align="left">String SalesByFuelGradeData</td>
			<td align="left">Optional</td>
			<td align="left">Fuel grade sales by grade code
				<p>Refer to Sales By Fuel Grade in the Transaction Data Structures section</p>
			</td>
		</tr>
		<tr valign="top">
			<td align="left">PumpTotalsData</td>
			<td align="left">Var</td>
			<td align="left">Dictionary < string, string > </td>
			<td align="left">Optional</td>
			<td align="left">One entry for each fueling position active during the period.
				<p>Refer to Pumps Totals Data in the Transaction Data Structures section</p>
			</td>
		</tr>
	</tbody>
</table>	

## Retail Summary Movements Response (RSUMRESP) Message Format

<table>
	<thead>
		<tr valign="top">
			<th align="left">Field Name</th>
			<th align="left">Size</th>
			<th align="left">Type</th>
			<th align="left">Condition</th>
			<th align="left">Descriptions/Field Value(s)</th>
		</tr>
	</thead>
	<tbody>
		<tr valign="top">
			<td align="left">ApplicationType</td>
			<td align="left">3</td>
			<td align="left">string</td>
			<td align="left">Required</td>
			<td align="left">Echoed from LREQ</td>
		</tr>
		<tr valign="top">
			<td align="left">ProcessingMode</td>
			<td align="left">1</td>
			<td align="left">string</td>
			<td align="left">Required</td>
			<td align="left">Echoed from LREQ</td>
		</tr>
		<tr valign="top">
			<td align="left">MessageFormatVersion</td>
			<td align="left">3</td>
			<td align="left">string</td>
			<td align="left">Required</td>
			<td align="left">Echoed from LREQ</td>
		</tr>
		<tr valign="top">
			<td align="left">TerminalIdentification</td>
			<td align="left">Var</td>
			<td align="left">string</td>
			<td align="left">Required</td>
			<td align="left">Echoed from LREQ</td>
		</tr>
		<tr valign="top">
			<td align="left">DeviceTypeIdentifier</td>
			<td align="left">1</td>
			<td align="left">string</td>
			<td align="left">Required</td>
			<td align="left">Echoed from LREQ</td>
		</tr>
		<tr valign="top">
			<td align="left">TransactionCode</td>
			<td align="left">3</td>
			<td align="left">string</td>
			<td align="left">Required</td>
			<td align="left">Refer to Transaction Codes in Reference Tables Section</td>
		</tr>
		<tr valign="top">
			<td align="left">TransactionSequenceNumber</td>
			<td align="left">Var</td>
			<td align="left">int</td>
			<td align="left">Required</td>
			<td align="left">Echoed from LREQ</td>
		</tr>
		<tr valign="top">
			<td align="left">AuthorizationCode</td>
			<td align="left">Var</td>
			<td align="left">string</td>
			<td align="left">Conditional</td>
			<td align="left">Refer to Authorization Code in Field Description section</td>
		</tr>
		<tr valign="top">
			<td align="left">ResponseCode</td>
			<td align="left">5</td>
			<td align="left">string</td>
			<td align="left">Required</td>
			<td align="left">“0” = Authorized, !”0” = Not Authorized</td>
		</tr>
		<tr valign="top">
			<td align="left">ResponseText</td>
			<td align="left">20</td>
			<td align="left">string</td>
			<td align="left">Required</td>
			<td align="left">Message from the Network</td>
		</tr>
	</tbody>
</table>	

## Transaction Data Structures
<table>
	<thead>
		<tr valign="top">
			<td align="left">Field Name</td>
			<td align="left">Size</td>
			<td align="left">Type</td>
			<td align="left">Condition</td>
			<td align="left">Descriptions/Field Value(s)</td>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td colspan="5" align="left" valign="bottom">
				<p>Product List section (one per product in transaction)</p>
			</td>
		</tr>
		<tr valign="top">
			<td align="left">ServiceCode</td>
			<td align="left">1</td>
			<td align="left">string</td>
			<td align="left">Required</td>
			<td align="left">Always "0" in this version</td>
		</tr>
		<tr valign="top">
			<td align="left">ItemCode</td>
			<td align="left">14</td>
			<td align="left">string</td>
			<td align="left">Required</td>
			<td align="left">Code used to ring the item (be it a PLU or a Barcode)</td>
		</tr>
		<tr valign="top">
			<td align="left">SKU</td>
			<td align="left">14</td>
			<td align="left">string</td>
			<td align="left">Required</td>
			<td align="left">SKU related to the item sold</td>
		</tr>
		<tr valign="top">
			<td align="left">ItemDesc</td>
			<td align="left">40</td>
			<td align="left">string</td>
			<td align="left">Optional</td>
			<td align="left">Item description as shown on the ticket, truncated to 40 chars if longer</td>
		</tr>
		<tr valign="top">		
			<td align="left">RegularPrice</td>
			<td align="left">Var</td>
			<td align="left">decimal</td>
			<td align="left">Optional</td>
			<td align="left">xxxx.xxx</td>
		</tr>
		<tr valign="top">		
			<td align="left">ActualSalePrice</td>
			<td align="left">Var</td>
			<td align="left">decimal</td>
			<td align="left">Optional</td>
			<td align="left">xxxx.xxx</td>
		</tr>
		<tr valign="top">		
			<td align="left">ActualSalePrice</td>
			<td align="left">Var</td>
			<td align="left">decimal</td>
			<td align="left">Optional</td>
			<td align="left">xxxx.xxx</td>
		</tr>
		<tr valign="top">
			<td align="left">ProductNetAmount</td>
			<td align="left">Var</td>
			<td align="left">decimal</td>
			<td align="left">Optional</td>
			<td align="left">xxxxxxx.xx</td>
		</tr>
		<tr valign="top">
			<td align="left">ProductTaxes</td>
			<td align="left">Var</td>
			<td align="left">Dictionary string, decimal</td>
			<td align="left">Optional</td>
			<td align="left">”[Tax Description]”, [Tax Value]</td>
		</tr>
		<tr valign="top">
			<td align="left">ProductAmount</td>
			<td align="left">Var</td>
			<td align="left">decimal</td>
			<td align="left">Optional</td>
			<td align="left">xxxxxxx.xx</td>
		</tr>
		<tr valign="top">
			<td align="left">ProductQuantity</td>
			<td align="left">Var</td>
			<td align="left">decimal</td>
			<td align="left">Optional</td>
			<td align="left">xxxxxxx.xx</td>
		</tr>
		<tr valign="top">
			<td align="left">UnitCode</td>
			<td align="left">Var</td>
			<td align="left">string</td>
			<td align="left">Optional</td>
			<td align="left">Refer to Measurement Unit Codes in Reference Tables Section</td>
		</tr>
		<tr>
			<td colspan="5" align="left" valign="bottom">
				<p>Method-of-Payment List section (one per MoP in transaction)</p>
			</td>
		</tr>
		<tr valign="top">
			<td align="left">MoPCode</td>
			<td align="left">8</td>
			<td align="left">string</td>
			<td align="left">Required</td>
			<td align="left">“0”-“9999”</td>
		</tr>
		<tr valign="top">		
			<td align="left">Amount</td>
			<td align="left">Var</td>
			<td align="left">decimal</td>
			<td align="left">Required</td>
			<td align="left">xxxx.xx</td>
		</tr>
		<tr>
			<td colspan="5" align="left" valign="bottom">
				<p>Sales By Method-of-Payment Data List section</p>
			</td>
		</tr>
		<tr valign="top">
			<td align="left">MoPCode</td>
			<td align="left">Var</td>
			<td align="left">string</td>
			<td align="left">Required</td>
			<td align="left">“0”-“9999”</td>
		</tr>
		<tr valign="top">		
			<td align="left">Amount</td>
			<td align="left">Var</td>
			<td align="left">decimal</td>
			<td align="left">Required</td>
			<td align="left">xxxx.xx</td>
		</tr>
		<tr>
			<td colspan="5" align="left" valign="bottom">
				<p>Sales By Cashier Data List section</p>
			</td>
		</tr>
		<tr valign="top">
			<td align="left">CashierCode</td>
			<td align="left">Var</td>
			<td align="left">string</td>
			<td align="left">Required</td>
			<td align="left">“0”-“9999”</td>
		</tr>
		<tr valign="top">		
			<td align="left">Amount</td>
			<td align="left">Var</td>
			<td align="left">decimal</td>
			<td align="left">Required</td>
			<td align="left">xxxx.xx</td>
		</tr>
		<tr>
			<td colspan="5" align="left" valign="bottom">
				<p>Sales By Register Data List section</p>
			</td>
		</tr>
		<tr valign="top">
			<td align="left">RegisterCode</td>
			<td align="left">Var</td>
			<td align="left">string</td>
			<td align="left">Required</td>
			<td align="left">“0”-“9999”</td>
		</tr>
		<tr valign="top">		
			<td align="left">Amount</td>
			<td align="left">Var</td>
			<td align="left">decimal</td>
			<td align="left">Required</td>
			<td align="left">xxxx.xx</td>
		</tr>
		<tr>
			<td colspan="5" align="left" valign="bottom">
				<p>Sales By Merchandise Data List section</p>
			</td>
		</tr>
		<tr valign="top">
			<td align="left">MerchandiseCode</td>
			<td align="left">Var</td>
			<td align="left">string</td>
			<td align="left">Required</td>
			<td align="left">“0”-“99999999”</td>
		</tr>
		<tr valign="top">		
			<td align="left">Quantity</td>
			<td align="left">Var</td>
			<td align="left">decimal</td>
			<td align="left">Required</td>
			<td align="left">xxxx.xx</td>
		</tr>
		<tr valign="top">		
			<td align="left">ActualSalePrice</td>
			<td align="left">Var</td>
			<td align="left">decimal</td>
			<td align="left">Required</td>
			<td align="left">xxxx.xx</td>
		</tr>
		<tr valign="top">		
			<td align="left">Amount</td>
			<td align="left">Var</td>
			<td align="left">decimal</td>
			<td align="left">Required</td>
			<td align="left">xxxx.xx</td>
		</tr>
		<tr>
			<td colspan="5" align="left" valign="bottom">
				<p>Sales By Fuel Grade Data List section</p>
			</td>
		</tr>
		<tr valign="top">
			<td align="left">FuelGradeCode</td>
			<td align="left">Var</td>
			<td align="left">string</td>
			<td align="left">Required</td>
			<td align="left">“0”-“99999999”</td>
		</tr>
		<tr valign="top">		
			<td align="left">Volume</td>
			<td align="left">Var</td>
			<td align="left">decimal</td>
			<td align="left">Required</td>
			<td align="left">xxxx.xxx</td>
		</tr>
		<tr valign="top">		
			<td align="left">ActualSalePrice</td>
			<td align="left">Var</td>
			<td align="left">decimal</td>
			<td align="left">Required</td>
			<td align="left">xxxx.xx</td>
		</tr>
		<tr valign="top">		
			<td align="left">PriceLevel</td>
			<td align="left">1</td>
			<td align="left">Int</td>
			<td align="left">Required</td>
			<td align="left">x</td>
		</tr>
		<tr valign="top">		
			<td align="left">Amount</td>
			<td align="left">Var</td>
			<td align="left">decimal</td>
			<td align="left">Required</td>
			<td align="left">xxxx.xx</td>
		</tr>
		<tr>
			<td colspan="5" align="left" valign="bottom">
				<p>Pump Totals Data List section</p>
			</td>
		</tr>
		<tr valign="top">
			<td align="left">PumpNumber</td>
			<td align="left">2</td>
			<td align="left">Int</td>
			<td align="left">Required</td>
			<td align="left">“0”-“99”</td>
		</tr>
		<tr valign="top">
			<td align="left">HoseNumber</td>
			<td align="left">1</td>
			<td align="left">Int</td>
			<td align="left">Required</td>
			<td align="left">“0”-“9”</td>
		</tr>
		<tr valign="top">
			<td align="left">GradeCode</td>
			<td align="left">2</td>
			<td align="left">Int</td>
			<td align="left">Required</td>
			<td align="left">“0”-“99”</td>
		</tr>
		<tr valign="top">		
			<td align="left">SalesVolume</td>
			<td align="left">Var</td>
			<td align="left">decimal</td>
			<td align="left">Required</td>
			<td align="left">xxxx.xxx</td>
		</tr>
		<tr valign="top">		
			<td align="left">SalesAmount</td>
			<td align="left">Var</td>
			<td align="left">decimal</td>
			<td align="left">Required</td>
			<td align="left">xxxx.xx</td>
		</tr>
		<tr valign="top">		
			<td align="left">PumpTestVolume</td>
			<td align="left">Var</td>
			<td align="left">decimal</td>
			<td align="left">Optional</td>
			<td align="left">xxxx.xxx</td>
		</tr>
		<tr valign="top">		
			<td align="left">PumpTestAmount</td>
			<td align="left">Var</td>
			<td align="left">decimal</td>
			<td align="left">Optional</td>
			<td align="left">xxxx.xx</td>
		</tr>
		<tr valign="top">		
			<td align="left">NRTotalsVolumeStarting</td>
			<td align="left">Var</td>
			<td align="left">decimal</td>
			<td align="left">Optional</td>
			<td align="left">xxxx.xxx</td>
		</tr>
		<tr valign="top">		
			<td align="left">NRTotalsAmountStarting</td>
			<td align="left">Var</td>
			<td align="left">decimal</td>
			<td align="left">Optional</td>
			<td align="left">xxxx.xx</td>
		</tr>
		<tr valign="top">		
			<td align="left">NRTotalsVolumeEnding</td>
			<td align="left">Var</td>
			<td align="left">decimal</td>
			<td align="left">Optional</td>
			<td align="left">xxxx.xxx</td>
		</tr>
		<tr valign="top">		
			<td align="left">NRTotalsAmountEnding</td>
			<td align="left">Var</td>
			<td align="left">decimal</td>
			<td align="left">Optional</td>
			<td align="left">xxxx.xx</td>
		</tr>
	</tbody>
</table>

## Reference Tables

This section brings together the code tables and reference values used in messaging.

### Transaction Codes

<table>
	<thead>
		<tr valign="top">
			<th align="left">Code</th>
			<th align="left">Message</th>
			<th align="left">Description</th>
		</tr>
	</thead>
	<tbody>
		<tr valign="top">
			<td align="left">“610”</td>
			<td align="left">RREQ</td>
			<td align="left">Sale Records Upload REQ</td>
		</tr>
		<tr valign="top">
			<td align="left">“611”</td>
			<td align="left">RRESP</td>
			<td align="left">Sale Records Upload RESP</td>
		</tr>
		<tr valign="top">
			<td align="left">“620”</td>
			<td align="left">RSUMREQ</td>
			<td align="left">Movements Summary Upload REQ</td>
		</tr>
		<tr valign="top">
			<td align="left">“621”</td>
			<td align="left">RRESP</td>
			<td align="left">Movements Summary Upload RESP</td>
		</tr>
	</tbody>
</table>

### Currency Codes
 
Refer to ISO 4217 Currency Codes standard (<http://en.wikipedia.org/wiki/ISO_4217>)

### Authorization Codes

Refer to AN-Native_Response_Codes-Spec document for a complete list of ATIOnet Host Response Codes and Texts.