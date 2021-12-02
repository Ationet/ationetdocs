![ationetlogo](Content/Images/ATIOnetLogo_250x70.png)
# ATIONet Native Interface API Protocol Specification

|Document Information|.|
|--- |--- |
|File:|ATIONet-Native_Interface_Protocol-Spec|
|Doc Version:|1.6|
|Release Date:|29, March 2021|
|Author:|ATIONet LLC|


|Change Log|||
|--- |--- |--- |
|Ver.|Date|Change Summary|
|1.0|04/Jan/2013|- Initial version. <br> - General information Actions: Statement Charges (partial)<br> - Transactions Download|
|1.1|07/Jan/2013|**Statement Charges**<br> - Added Action 902 Negative Balance transfer to a sub-account<br> - New group of actions: 941 – 950 Account Inquiries (partial)<br> - Actions: 941 Sub-account Balance Enquiry <br> - 942 Sub-account Limit Enquiry <br> - Transactions Downloads <br> - Consolidated Classification Fields for Vehicles and Drivers <br> - Reorganized Response record, moved Classification fields after Driver Fields.|
|1.2|30/10/2013|**Account Inquiries** <br> - Added Action 943 Contract Balance Enquiry <br> - New group of actions: 951 – 959 Account Download (partial) <br> Actions: 951 Sub-Account Movements Download <br> - 952 Contract Movements Download|
|1.3|05/07/2014|**Statement Charges** <br> - Added Action 903 Transfer balance from sub-account to a sub-account<br> - Added Action 904 Transfer balance from contract to a sub-account <br> - Added Action 905 Transfer balance from sub-account to a contract <br> - Change and reorganize request and response records<br> **Transactions Downloads** <br> - Change and reorganize request and response records <br> - Account Inquiries <br> - Remove Action 943 Contract Balance Enquiry <br> - Change and reorganize request and response records **Account Downloads** <br> - Remove Action 952 Contract Movements Download <br> - Change Action 951 Sub-Account Movements Download to 951 Movements Download <br> - Change and reorganize request and response records <br>**Error Handling** <br> - Include “ResponseError” in response record for actions intended to post a command|
|1.4|27/11/2018|**FastTrack** <br> - Added Action 971 Request insertion of new FastTrack <br> - Added Action 972 Request FastTrack list download|
|1.5|29/03/2021|**API Interface Messages** <br> - Updated lists of Action Codes|
|1.5|13/07/2021|**Inventory Interface Messages** <br> - Updated lists of Action Codes|
|1.6|29/11/2021|**Inventory & Delivery Interface Update** <br> - Update Inventory Download Response <br> - Update Delivery Download Response <br>|

## Contents

- [1 Scope](#1-scope)
	- [1.1 Scope details](#11-scope-details)

- [2 System Interface API](#2-system-interface-api)
	- [2.1 Interface API Messages](#21-interface-api-messages)
		- [2.1.1 Current Account Messages](#211-current-account-messages)
		- [2.1.2 Transaction Messages](#212-transaction-messages)

- [3 Data security](#3-data-security)

- [4 Message Structure](#4-message-structure)

- [5 Error handling](#5-error-handling)

- [6 Current Account Movements Interface](#6-current-account-movements-interface)
	- [6.1 Action Codes](#61-action-codes)
	- [6.2 Identification](#62-identification)
	- [6.3 Current Account Movements (POST) – Body Section Record Format](#63-current-account-movements-post--body-section-record-format)

- [7 Transactions Download Interface](#7-transactions-download-interface)
	- [7.1 Action Codes](#71-action-codes)
	- [7.2 Transactions Download (POST) – Body Section Format Request](#72-transactions-download-post--body-section-format-request)
	- [7.3 Transactions Download (POST) – Body Section Format Response](#73-transactions-download-post--body-section-format-response)

- [8 FastTrack Interface](#8-fasttrack-interface)
	- [8.1 Action Codes](#81-action-codes)
	- [8.2 FastTracks Order Insert (POST) – Body Section Format Request](#82-fasttracks-order-insert-post--body-section-format-request)
	- [8.3 FastTracks Download (POST) – Body Section Format Request](#83-fasttracks-download-post--body-section-format-request)
	- [8.4 FastTracks Download (POST) – Body Section Format Response](#84-fasttracks-download-post--body-section-format-response)
	
- [9 Account Enquiries](#9-account-enquiries)
	- [9.1 Action Codes](#91-action-codes)
	- [9.2 Identification](#92-identification)
	- [9.3 Account Enquiry (POST) – Body Section Record Format Request](#93-account-enquiry-post--body-section-record-format-request)
	- [9.4 Account Enquiry (POST) – Body Section Record Format Response](#94-account-enquiry-post--body-section-record-format-response)

- [10 Account Downloads](#10-account-downloads)
	- [10.1 Action Codes](#101-action-codes)
	- [10.2 Account Download (POST) – Body Section Format Request](#102-account-download-post--body-section-format-request)
	- [10.3 Account Download (POST) – Body Section Format Response](#103-account-download-post--body-section-format-response)

- [11 Inventory and deliveries Downloads](#11-Inventory-and-deliveries-Downloads)
	- [11.1 Action Codes](#111-Action-Codes)
	- [11.2 Deliveries Download (POST) – Body Section Format Request](#112-Deliveries-Download-POST--Body-Section-Format-Request)
	- [11.3 Deliveries Download (POST) – Body Section Format *Response*](#113-Deliveries-Download-POST--Body-Section-Format-Response)
	- [11.4 Delivery GPS Download - Body Section Format *Response*](#114-Delivery-GPS-Download--Body-Section-Format-Response)
	- [11.5 Inventories Download (POST) – Body Section Format *Request*](#115-Inventories-Download-POST--Body-Section-Format-Request)
	- [11.6 Inventories Download (POST) – Body Section Format *Response*](#116-Inventories-Download-POST--Body-Section-Format-Response)

- [12 Examples](#12-Examples)
	- [12.1 C# example](#121-C-example)

## Overview

### Introduction

This specification is intended to document ATIONet’s Native Interface
API messaging format and related features required for the systems
applying for integration with ATIONet.

The Interface API allows the The following sections provide descriptions
of the messages themselves, the expected behaviour for each supported
action type and a common ground for the functionality of each relevant
item.

### Definitions

#### Subscriber
ATIONet’s subscription owner. The person or company who
runs the service.

#### Homebase
A type of ATIONet subscription where the subscriber owns
the site(s) but also the fleet(s) of vehicles.

#### Network
A type of ATIONet subscription where the subscriber enrolls
Fleet Companies and retail or commercial sites to operate with its own
method-of-payment. The Network company doesn’t own the site(s) or the
vehicles.

#### Retail
A type of ATIONet subscription where the subscriber owns the
sites and enrolls Fleet Companies to operate with its own
method-of-payment.

#### Merchant
On a Network type subscription, the Merchant is the
company who own the sites.

#### Company
On a Network or Retail type subscription, the Company is
the company who own the fleet.

#### Terminal
Transaction capture device at the site.

## 1 Scope

Version 1.4 of this document covers a particular version of ATIONet’s
Host protocol. Although feature’s descriptions are generally not related
to a particular version of the protocol, some changes may apply which
would be specifically commented and identified on each feature’s
description paragraph.

### 1.1 Scope details

Protocol: ATIONet Native Interface API

Version: Version 1.4

API URI: native.ationet.com/v1/interface

## 2 System Interface API

The Interface API provide system-to-system access to certain features of
ATIONet otherwise only available via the ATIONet Console, and it’s
intended to allow direct interaction of third-party systems on
Subscribers, Merchants and fleet Companies with ATIONet.

Availability of part or all the functionality of the Interface API is
subject to the business type and contract terms of the ATIONet
subscriber.

### 2.1 Interface API Messages

Commands ATIONet to process a movement on the account of a driver or vehicle, given an action type indicated on the message body.
Availability of this message and the type of actions allowed depend on the subscriber type and its contracting terms.

#### 2.1.1 Current Account Messages

<table class="tg">
<thead>
  <tr>
    <th class="tg-gvcd"><span style="font-weight:bold">Type</span></th>
    <th class="tg-gvcd"><span style="font-weight:bold">Action Code</span></th>
    <th class="tg-gvcd"><span style="font-weight:bold">Description</span></th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-rjo2" rowspan="12">Current Accounts</td>
    <td class="tg-eygw">901</td>
    <td class="tg-eygw">Balance transfer to a sub-account</td>
  </tr>
  <tr>
    <td class="tg-gvcd">902</td>
    <td class="tg-gvcd">Balance withdrawal from a sub-account</td>
  </tr>
  <tr>
    <td class="tg-eygw">903</td>
    <td class="tg-eygw">Balance transfer from sub-account to a sub-account</td>
  </tr>
  <tr>
    <td class="tg-gvcd">904</td>
    <td class="tg-gvcd">Balance transfer from contract to a sub-account</td>
  </tr>
  <tr>
    <td class="tg-eygw">905</td>
    <td class="tg-eygw">Balance transfer from sub-account to a contract</td>
  </tr>
  <tr>
    <td class="tg-gvcd">906</td>
    <td class="tg-gvcd">Balance transfer to contract</td>
  </tr>
  <tr>
    <td class="tg-eygw">907</td>
    <td class="tg-eygw">Balance withdrawal from contract</td>
  </tr>
  <tr>
    <td class="tg-eygw">941</td>
    <td class="tg-eygw">Balance download of sub-account</td>
  </tr>
  <tr>
    <td class="tg-gvcd">942</td>
    <td class="tg-gvcd">Balance download of contract</td>
  </tr>
  <tr>
    <td class="tg-eygw">951</td>
    <td class="tg-eygw">Movements download of company</td>
  </tr>
  <tr>
    <td class="tg-gvcd">952</td>
    <td class="tg-gvcd">Movements download of company group</td>
  </tr>
</tbody>
</table>

#### 2.1.2 Transaction Messages

<table class="tg">
<thead>
  <tr>
    <th class="tg-gvcd"><span style="font-weight:bold">Type</span></th>
    <th class="tg-gvcd"><span style="font-weight:bold">Action Code</span></th>
    <th class="tg-gvcd"><span style="font-weight:bold">Description</span></th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-rjo2" rowspan="11">Transactions</td>
    <td class="tg-eygw">931</td>
    <td class="tg-eygw">Transactions download</td>
  </tr>
  <tr>
    <td class="tg-gvcd">932</td>
    <td class="tg-gvcd">Merchant transactions download</td>
  </tr>
  <tr>
    <td class="tg-eygw">933</td>
    <td class="tg-eygw">Exceptions download</td>
  </tr>
  <tr>
    <td class="tg-gvcd">934</td>
    <td class="tg-gvcd">Uncontrolled transactions download</td>
  </tr>
  <tr>
    <td class="tg-eygw">935</td>
    <td class="tg-eygw">Transactions disputes download</td>
  </tr>
  <tr>
    <td class="tg-gvcd">936</td>
    <td class="tg-gvcd">GPS transactions download</td>
  </tr>
  <tr>
    <td class="tg-eygw">937</td>
    <td class="tg-eygw">GPS transactions update</td>
  </tr>
  <tr>
    <td class="tg-gvcd">938</td>
    <td class="tg-gvcd">GiftCard transactions download</td>
  </tr>
  <tr>
    <td class="tg-eygw">939</td>
    <td class="tg-eygw">GiftCard exceptions download</td>
  </tr>
  <tr>
    <td class="tg-gvcd">943</td>
    <td class="tg-gvcd">ConsumerCard transactions download</td>
  </tr>
  <tr>
    <td class="tg-eygw">944</td>
    <td class="tg-eygw">ConsumerCard exceptions download</td>
  </tr>
</tbody>
</table>

## 3 Data security

The Interface API requires an SSL connection between both parties. The
SSL connection is established for each request/response pair, using a
certificate property of ATIONet, meaning that each request must include
a system-type user and password on the Header. The user will be matched
against the related ATIONet actor for each message. (for example: when a
Transactions Download request is received, the Interface will first
check whether the company of the authenticated user matches with the
Company code in the request).

Users to be used on the Interface API messaging will be created by
authorized users via ATIONet Console, with the role “Interface API”.

At this time there is no provisioning to distribute or update
certificates or thumbprint thru a system interface. This information
will be provided at request of the Subscriber.

## 4 Message Structure

All Interface API messages share the same structure, what change from
message to message are the Action Code, which indicates the actual
interface function, the value fields sent and received, and the HTTP
action (POST, GET, REQUEST) which changes depending on the Action Code.

Both, requests and responses use a JSON format.

Only one request is accepted on each message, although some requests and
many responses will contain multiple records.

### Request Format

*Header:*

	Accept-Encoding: gzip

	Authorization: Basic user:password

*Body:*

	{“ActionCode”:”nnn”,”FieldName”:”StringValue”,”FieldName”:Value}

### Response

*Header:*

	Content-Type: application/json; charset=utf-8

*Body:*

	[{“Fieldname”:”StringValue”,”FieldName”:”StringValue”,”FieldName”:Value},
	{“Fieldname”:”StringValue”,”FieldName”:”StringValue”,”FieldName”:Value}]


Note: Some Action Codes returns a single response row, for example the
Statement charges.

Note: Alphanumeric fields, stated as Type “A/N” in record format tables
below show the maximum possible length as the Size, although in
JSON-formatted strings they will be represented with trailing spaces
trimmed.

## 5 Error handling

Success/failure exits on the Interface API will be handled via HTTP
status codes.

Successful request will get a HTTP 200 and the resulting response.

Actions intended to return data, for example the Transactions Downloads
group may return many records, just a single record or even no records
at all and even though will be considered successful if the requests met
the validation criteria. These Actions will always return a
JSON-formatted list of records, enclosed in curly brackets “[…]”. An
empty response will contain [] as body.

Actions intended to post a command, for example the Statement Charges
group will return a single JSON-formatted item with the “ResponseCode”,
“ResponseMessage” and “ResponseError” fields. The body of these
responses will never be empty.

Failure to process the request will be indicated by an HTTP 400’s range
status code. The body will contain a single JSON-formatted item with the
“ResponseCode”, “ResponseMessage” and “ResponseError” fields.

## 6 Current Account Movements Interface

The Current Account Movements message sends an instruction to ATIONet to apply a
well-defined action on the current account subsystem. The subject of the
action will be a sub-account of a contract, lets say a Vehicle or a
Driver account.

Depending on the type of charge this message might be used by one or
the other party of the contract (the subscriber or the fleet company).

### 6.1 Action Codes

The Action Code specifies the type of accounting transactions requested
by a Statement Charge Message. The submitted code must match one of the
pre-defined operation types. Not all operation types are available for
all subscribers and/or fleet companies, availability depends on
subscription types but also on contract terms with ATIONet.

<table class="tg">
<thead>
  <tr>
    <th class="tg-gvcd"><span style="font-weight:bold">Action Code</span></th>
    <th class="tg-gvcd"><span style="font-weight:bold">Title</span></th>
    <th class="tg-gvcd">Function</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-eygw">901</td>
    <td class="tg-dqd0">Balance transfer to a sub-account</td>
    <td class="tg-eygw">Transfers a given value from the global balance of the contract to the sub-account related to the vehicle or driver.<br><br>Contract balance must have enough funds (or product volume) to allow the transfer; otherwise the action will be rejected by the current accounts system.<br><br>The action will first trigger a deposit action on the contract and then a contract to sub-account transfer.</td>
  </tr>
  <tr>
    <td class="tg-gvcd">902</td>
    <td class="tg-bthj">Balance withdrawal from a sub-account</td>
    <td class="tg-gvcd">Withdraws a given value from the sub-account related to the vehicle or driver.<br><br>Sub-account balance must have enough funds (or product volume) to allow the withdrawal; otherwise the action will be rejected by the current accounts subsystem.</td>
  </tr>
  <tr>
    <td class="tg-eygw">903</td>
    <td class="tg-dqd0">Balance transfer from sub-account to a sub-account</td>
    <td class="tg-eygw">Transfers a given value from the original sub-account (related to the original vehicle or driver) to another sub-account related to the vehicle or driver.<br><br>Original sub-account balance must have enough funds (or product volume) to allow the transfer; otherwise the action will be rejected by the current accounts system.</td>
  </tr>
  <tr>
    <td class="tg-gvcd">904</td>
    <td class="tg-bthj">Balance transfer from contract to a sub-account</td>
    <td class="tg-gvcd">Transfers a given value from the contract to the sub-account related to the vehicle or driver.<br><br>Contract balance must have enough funds (or product volume) to allow the transfer; otherwise the action will be rejected by the current accounts subsystem.</td>
  </tr>
  <tr>
    <td class="tg-eygw">905</td>
    <td class="tg-dqd0">Balance transfer from sub-account to a contract</td>
    <td class="tg-dm8k">Transfers a given value from the sub-account related to the vehicle or driver contract.<br><br>Sub-account balance must have enough funds (or product volume) to allow the withdrawal; otherwise the action will be rejected by the current accounts subsystem.</td>
  </tr>
  <tr>
    <td class="tg-gvcd">906</td>
    <td class="tg-bthj">Balance transfer to contract</td>
    <td class="tg-gvcd">Transfers a given value to a contract.</td>
  </tr>
  <tr>
    <td class="tg-eygw">907</td>
    <td class="tg-dqd0">Balance withdrawal from contract</td>
    <td class="tg-eygw">Withdraws a given value from a contract.</td>
  </tr>
  <tr>
    <td class="tg-gvcd">941</td>
    <td class="tg-bthj">Balance download of sub-account</td>
    <td class="tg-gvcd">Downloads the balance of all sub-accounts related to the vehicle or driver of a determined contract.</td>
  </tr>
  <tr>
    <td class="tg-eygw">942</td>
    <td class="tg-dqd0">Balance download of contract</td>
    <td class="tg-eygw">Downloads the balance of all contracts related to the network.</td>
  </tr>
  <tr>
    <td class="tg-gvcd">951</td>
    <td class="tg-bthj">Movements download of company</td>
    <td class="tg-gvcd">Downloads the movements of all contracts of a determined company.<br><br>A contract can also be specified in order to download all movements only for that contract related to the company.</td>
  </tr>
  <tr>
    <td class="tg-eygw">952</td>
    <td class="tg-dqd0">Movements download of company group</td>
    <td class="tg-eygw">Downloads the movements of a determined company group.</td>
  </tr>
</tbody>
</table>

### 6.2 Identification

When a movement request is received, ATIONet will try to identify the
Subscriber, the Species (Currency Code or Master Fuel Code) and the
Identifier of the sub-account (Vehicle or Driver). This can be performed
thru several combinations of the Identification Fields on the body of
the message:

1.  Any Identifier field (Identifier, Driver Code, Vehicle Code, Vehicle
    Plate, SubAccount External Code and SubAccount Id) only. Only
    accepted for Home-base subscriptions.

2.  Company Code + Identifier.

3.  Company Code + Contract Code + (Driver Code or Vehicle Code or
    Vehicle Plate)

### 6.3 Current Account Movements (POST) – Body Section Record Format

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
				<p align="left">SubscriberCode</p>
			</td>
			<td>
				<p align="left">3</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Required</p>
			</td>
			<td>
				<p align="left">Fixed. To be assigned by ATIONet</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ActionCode</p>
			</td>
			<td>
				<p align="left">3</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Required</p>
			</td>
			<td>
				<p align="left">Operation type code.
				<br>See Action Code Section.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyCode</p>
			</td>
			<td>
				<p align="left">30</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">See Identification section</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ContractCode</p>
			</td>
			<td>
				<p align="left">20</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">See Identification section</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">DriverCode</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">See Identification section</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">VehicleCode</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">See Identification section</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">VehiclePlate</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">See Identification section</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SubAccountExternalCode</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">See Identification section</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SubAccountId</p>
			</td>
			<td>
				<p align="left">36</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">See Identification section</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Identifier</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">Public ID of the identification device (chipkey ID, account number on a mag card, RFID serial number, etc.)</p>
				<p align="left">See Identification section</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">DriverCodeOrigin</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">See Identification section</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">VehicleCodeOrigin</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">See Identification section</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">VehiclePlateOrigin</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">See Identification section</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SubAccountExternalCodeOrigin</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">See Identification section</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SubAccountIdOrigin</p>
			</td>
			<td>
				<p align="left">36</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">See Identification section</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">IdentifierOrigin</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">Public ID of the identification device (chipkey ID, account number on a mag card, RFID serial number, etc.)</p>
				<p align="left">See Identification section</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">MasterFuelCode</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Conditional</p>
			</td>
			<td>
				<p align="left">Required if Charge Volume is specified</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CurrencyCode 
				</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A</p>
			</td>
			<td>
				<p align="left">Conditional</p>
			</td>
			<td>
				<p align="left">Required if Charge Amount is specified</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Amount</p>
			</td>
			<td>
				<p align="left">10</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Required</p>
			</td>
			<td>
				<p align="left">Charge Amount or Charge Volume 
				</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Description</p>
			</td>
			<td>
				<p align="left">1000</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">A description for the current account movement</p>
			</td>
		</tr>
	</tbody>
</table>

## 7 Transactions Download Interface

The Transactions Download Interface are POST actions to recover all the
payment transactions processed by ATIONet for a given Terminal, Contract
Code or Company Code depending on the particular Action Code.

The Action Code is validated against the type of company of the
authenticated user. Request not passing this validation will be
rejected.

The download will be limited by dates (from and to), which must be
included in the request

### 7.1 Action Codes

The Action Code specifies the type of record transaction to be
retrieved; this differentiation is based on the different roles on an
ATIONet operation (Fleet Company, Merchant, Network, Home-base), which
also mandates different ways to identify the requester and scope of
transactions to download.

<table>
	<tr valign="top">
		<th align="left">
			Action Code
		</th>
		<th colspan="2" align="left">
			Description
		</th>
	</tr>
	<tr valign="top">
		<td rowspan="4">
			<p>931</p>
		</td>
		<td>
			<p>Title:</p>
		</td>
		<td>
			<p>Transactions Download</p>
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>Function:</p>
		</td>
		<td>
			<p>Download complete transactions records</p>
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>Allowed for:</p>
		</td>
		<td>
			<p>Subscribers and Fleet Companies</p>
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>Identification:</p>
		</td>
		<td>
			<p>Subscriber Code</p>
			<p>Merchant Code (Optional, if included will act as a filter)</p>
			<p>Company Code (Optional, if included will act as a filter)</p>
			<p>Terminal Code(Optional, if included will act as a filter)</p>
			<p>Contract Code (Optional, if included will act as a filter)</p>
		</td>
	</tr>
	<tr valign="top">
		<td rowspan="4">
			<p>932</p>
		</td>
		<td>
			<p>Title:</p>
		</td>
		<td>
			<p>Transactions Download for Merchants</p>
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>Function:</p>
		</td>
		<td>
			<p>Download transactions records (fueling details subset)</p>
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>Allowed for:</p>
		</td>
		<td>
			<p>Merchants on a three-layer subscription model</p>
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>Identification:</p>
		</td>
		<td>
			<p>Subscriber Code</p>
			<p>Merchant Code</p>
			<p>Terminal Code (Optional, if included will act as a filter)</p>
		</td>
	</tr>
</table>

### 7.2 Transactions Download (POST) – Body Section Format *Request*

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
				<p align="left">SubscriberCode</p>
			</td>
			<td>
				<p align="left">3</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Required</p>
			</td>
			<td>
				<p align="left">Fixed. To be assigned by ATIONet</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ActionCode</p>
			</td>
			<td>
				<p align="left">3</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Required</p>
			</td>
			<td>
				<p align="left">See Action Codes section above</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">MerchantCode</p>
			</td>
			<td>
				<p align="left">30</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Conditional</p>
			</td>
			<td>
				<p align="left">See Action Codes section above</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyCode</p>
			</td>
			<td>
				<p align="left">30</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Conditional</p>
			</td>
			<td>
				<p align="left">See Action Codes section above</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ContractCode</p>
			</td>
			<td>
				<p align="left">20</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">See Action Codes section above</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">TerminalCode</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">See Action Codes section above</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">DateFrom</p>
			</td>
			<td>
				<p align="left">19</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Required</p>
			</td>
			<td>
				<p align="left">From date to filter transactions</p>
				<p align="left">&ldquo;yyyy/MM/dd hh:mm:ss&rdquo;</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">DateTo</p>
			</td>
			<td>
				<p align="left">19</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">To date to filter transactions</p>
				<p align="left">&ldquo;yyyy/MM/dd hh:mm:ss&rdquo;</p>
			</td>
		</tr>
	</tbody>
</table><table>
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
				<p align="left">SubscriberCode</p>
			</td>
			<td>
				<p align="left">3</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Required</p>
			</td>
			<td>
				<p align="left">Fixed. To be assigned by ATIONet</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ActionCode</p>
			</td>
			<td>
				<p align="left">3</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Required</p>
			</td>
			<td>
				<p align="left">See Action Codes section above</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">MerchantCode</p>
			</td>
			<td>
				<p align="left">30</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Conditional</p>
			</td>
			<td>
				<p align="left">See Action Codes section above</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyCode</p>
			</td>
			<td>
				<p align="left">30</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Conditional</p>
			</td>
			<td>
				<p align="left">See Action Codes section above</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ContractCode</p>
			</td>
			<td>
				<p align="left">20</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">See Action Codes section above</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">TerminalCode</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">See Action Codes section above</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">DateFrom</p>
			</td>
			<td>
				<p align="left">19</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Required</p>
			</td>
			<td>
				<p align="left">From date to filter transactions</p>
				<p align="left">&ldquo;yyyy/MM/dd hh:mm:ss&rdquo;</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">DateTo</p>
			</td>
			<td>
				<p align="left">19</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">To date to filter transactions</p>
				<p align="left">&ldquo;yyyy/MM/dd hh:mm:ss&rdquo;</p>
			</td>
		</tr>
	</tbody>
</table>

### 7.3 Transactions Download (POST) – Body Section Format *Response*

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
				Descriptions/Field Value(s)
			</th>
		</tr>
	</thead>
	<tbody>
		<tr valign="top">
			<td>
				<p>TransactionID</p>
			</td>
			<td>
				<p>36</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Transaction&rsquo;s UID</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>SubscriberCode</p>
			</td>
			<td>
				<p>3</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Code of the subscriber who owns the transaction</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>TransactionSequenceNumber</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Transaction ID as received from the site&rsquo;s controller system. Usually a transaction counter. Site-based, might repeat from site to site.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>AuthorizationCode</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Authorization Code</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>ResponseCode</p>
			</td>
			<td>
				<p>5</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Host response code sent to the terminal</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>ResponseMessage</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Host response text sent to the terminal</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>Status</p>
			</td>
			<td>
				<p>1</p>
			</td>
			<td>
				<p>N</p>
			</td>
			<td>
				<p>2- &ldquo;Completed&rdquo;, 3- &ldquo;Confirmed&rdquo;</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>Mode</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>Type</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>StatusDescription</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>&ldquo;Completed&rdquo; or &ldquo;Confirmed&rdquo;</p>
				<p>A transaction is Completed when the completion message sent from the site&rsquo;s terminal is processed and approved by ATIONet, meaning that the sale or delivery transaction was successfully performed at the site.</p>
				<p>A transaction is Confirmed when the site&rsquo;s terminal receives an acknowledge message of the successful processing of completion message from ATIONet.</p>
				<p>Thus, Confirmed or Completed transactions are considered valid records of a successful transaction at the site. But, a transaction that is only Completed (not confirmed) might indicate that the site&rsquo;s terminal is not aware of ATIONet status. Depending on the site&rsquo;s system, this could lead to differences between site&rsquo;s and ATIONet sales totals.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>HostDateTime</p>
			</td>
			<td>
				<p>19</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>ATIONet&rsquo;s transaction datetime &ldquo;yyyy/mm/dd hh:mm:ss&rdquo;. 
				</p>
				<p>ATIONet Host date time is UCT</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>SubscriberDateTime</p>
			</td>
			<td>
				<p>19</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Subscriber transaction datetime &ldquo;yyyy/mm/dd hh:mm:ss&rdquo;.</p>
				<p>Subscriber date time is Subscriber TimeZone</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>SubscriberTimeZone</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>TimeZone code of the subscriber (abbreviation)</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>SiteDateTime</p>
			</td>
			<td>
				<p>19</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p align="left">Site transaction datetime &ldquo;yyyy/mm/dd hh:mm:ss&rdquo;.</p>
				<p>Site date time is Site TimeZone</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>SiteTimeZone</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p align="left">TimeZone code of the site (abbreviation)</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>DateTime</p>
			</td>
			<td>
				<p>19</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Site&rsquo;s transaction date &ldquo;yyyy/mm/dd hh:mm:ss&rdquo;.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>MerchantCode</p>
			</td>
			<td>
				<p>30</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Code of the company who owns the site</p>
				<p>N/A to Homebase subscribers</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>MerchantContractCode</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>MerchantName</p>
			</td>
			<td>
				<p>250</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Name of the company who owns the site</p>
				<p>N/A to Homebase subscriber</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>MerchantCustomField0</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>MerchantCustomField1</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>MerchantCustomField2</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>MerchantCustomField3</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>SiteCode</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Site Code</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>SiteName</p>
			</td>
			<td>
				<p>100</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Name of the Site</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>SiteShortName</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>TerminalCode</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Site&rsquo;s Terminal identification code.</p>
				<p>A Terminal is the device or system that captures the transaction at the site, depending on the controller (system) type at the site, it may be the actual terminal (for example the specific OPT) or the whole system (several OPTs served by a single controller).</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>TerminalType</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>TerminalId</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>TerminalTypeId</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>SubAccountId</p>
			</td>
			<td>
				<p>36</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>SubAccount&rsquo;s UID</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>SecondarySubAccountId</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>AccountTypeDescription</p>
			</td>
			<td>
				<p>10</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>&ldquo;Driver&rdquo; or &ldquo;Vehicle&rdquo;</p>
				<p>This field indicates whether the sub-account charged with the transaction is a Vehicle or a Driver.</p>
				<p>NOTE: The rest of the fields related to Vehicle or Driver in the transaction will be populated or not depending on this value and should be evaluated accordingly.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>VehicleCode</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Vehicle Code</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>DriverCode</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Driver Code</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>TransactionNetAmount</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>ProductUnitPriceRequested</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>ProductAmountRequested</p>
			</td>
			<td>
				<p>10</p>
			</td>
			<td>
				<p>N</p>
			</td>
			<td>
				<p>Amount (money) requested on a single-product pre-authorization. </p>
				<p>xxxxxxx.xx</p>
				<p>NOTE: ATIONet Native Transaction Protocol allows for one product to be included directly on the message body. More products could be included in the Product Data structure, therefore &ldquo;Product&rdquo; figures might be different (lesser) than &ldquo;Transaction&rdquo; figures, which always represents total values. On most situations (just one fueling per transaction, without dry products), &ldquo;Product&rdquo; and &ldquo;Transaction&rdquo; value-fields would have the same values.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>ProductVolumeRequested</p>
			</td>
			<td>
				<p>10</p>
			</td>
			<td>
				<p>N</p>
			</td>
			<td>
				<p>Volume requested on a single-product pre-authorization. xxxxxxx.xx</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>ProductVolumeAuthorized</p>
			</td>
			<td>
				<p>10</p>
			</td>
			<td>
				<p>N</p>
			</td>
			<td>
				<p>Volume authorized. xxxxxxx.xx</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>ProductAmountAuthorized</p>
			</td>
			<td>
				<p>10</p>
			</td>
			<td>
				<p>N</p>
			</td>
			<td>
				<p>Amount authorized. xxxxxxx.xx</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>ProductVolumeDispensed</p>
			</td>
			<td>
				<p>10</p>
			</td>
			<td>
				<p>N</p>
			</td>
			<td>
				<p>Actual fueling volume (adjusted by the completion message). xxxxxxx.xx</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>ProductAmountDispensed</p>
			</td>
			<td>
				<p>10</p>
			</td>
			<td>
				<p>N</p>
			</td>
			<td>
				<p>Actual fueling amount (adjusted by the completion message). xxxxxxx.xx</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>TransactionAmountRequested</p>
			</td>
			<td>
				<p>10</p>
			</td>
			<td>
				<p>N</p>
			</td>
			<td>
				<p>Transaction amount requested on the pre-authorization. xxxxxxx.xx</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>ProductUnitPriceAuthorized</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>TransactionAmountAuthorized</p>
			</td>
			<td>
				<p>10</p>
			</td>
			<td>
				<p>N</p>
			</td>
			<td>
				<p>Transaction amount authorized.
				<br>xxxxxxx.xx</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>ProductUnitPriceDispensed</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>ProductNetAmountDispensed</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>ProductUnitPriceCompany</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>ProductUnitPriceMerchant</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>ProductAmountCompany</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>ProductAmountMerchant</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>TransactionAmountCompany</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>TransactionAmountMerchant</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>TransactionAmountDispensed</p>
			</td>
			<td>
				<p>10</p>
			</td>
			<td>
				<p>N</p>
			</td>
			<td>
				<p>Actual amount fueled. xxxxxxx.xx</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>MeasurementUnitCode</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Unit of measuring for the volume fields, according to site&rsquo;s configuration.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>CurrencyCode</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Currency of the amount fields, according to site&rsquo;s configuration</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>FuelCode</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>N</p>
			</td>
			<td>
				<p>Site&rsquo;s product code</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>FuelMasterCode</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Standardized product code. Helps to identify a fuel product category across multiple Merchant brands and site&rsquo;s product codes</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>FuelMasterDescription</p>
			</td>
			<td>
				<p>100</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Standardized product description. Helps to identify a fuel product category across multiple Merchant brands and site&rsquo;s product codes</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>InvoiceNumber</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Number assigned by the Terminal to the document issued for the transaction. May be empty.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>BatchNumber</p>
			</td>
			<td>
				<p>11</p>
			</td>
			<td>
				<p>N</p>
			</td>
			<td>
				<p>Batch Identification. Informed by the site&rsquo;s controller. Persisted on ATIONet for information purposes only. May be empty</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>ShiftNumber</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Shift (or Date+Shift) Identification. Informed by the site&rsquo;s controller. Persisted on ATIONet for information purposes only. May be empty</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>PumpNumer</p>
			</td>
			<td>
				<p>2</p>
			</td>
			<td>
				<p>N</p>
			</td>
			<td>
				<p>Fueling position number. Informed by the terminal.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>EntryMethod</p>
			</td>
			<td>
				<p>1</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">1 = Manual Entry</p>
				<p align="left">2 = Magnetic Card Swipe</p>
				<p align="left">3 = Smart Card</p>
				<p align="left">4 = AVI</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>CompanyCode</p>
			</td>
			<td>
				<p>30</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Company code</p>
				<p>Not meaningful for Homebase subscribers</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>CompanyName</p>
			</td>
			<td>
				<p>250</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Company name</p>
				<p>Not meaningful for Homebase subscribers</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>CompanyCustomField0</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>CompanyCustomField1</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>CompanyCustomField2</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>CompanyCustomField3</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>CompaniesGroupCode</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>ClassificationLabel1</p>
			</td>
			<td>
				<p>200</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Classifications</p>
				<p>ATIONet allows for up to four user-defined classification field for Vehicles or Drivers.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>ClassificationLabel2</p>
			</td>
			<td>
				<p>200</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td></td>
		</tr>
		<tr valign="top">
			<td>
				<p>ClassificationLabel3</p>
			</td>
			<td>
				<p>200</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td></td>
		</tr>
		<tr valign="top">
			<td>
				<p>ClassificationLabel4</p>
			</td>
			<td>
				<p>200</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td></td>
		</tr>
		<tr valign="top">
			<td>
				<p>ContractCode</p>
			</td>
			<td>
				<p>20</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Contract code</p>
				<p>Not meaningful for Homebase subscribers</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>CompanyContractClassificationValue1</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>CompanyContractClassificationValue2</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>CompanyContractClassificationValue3</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>CompanyContractClassificationValue4</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>CompanyContractCustomField0</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>CompanyContractCustomField1</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>CompanyContractCustomField2</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>CompanyContractCustomField3</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>SubContractCode</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>SubContract code</p>
				<p>Not meaningful for Homebase subscribers</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>PrimaryIdentificationTrack</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>SecondaryIdentificationTrack</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>PrimaryIdentificationPAN</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>SecondaryIdentificationPAN</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>PrimaryIdentificationLabel</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p align="left">Public ID of the primary identification device (chipkey ID, account number on a mag card, RFID serial number, etc.)</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>SecondaryIdentificationLabel</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Public ID of the secondary identification device (chipkey ID, account number on a mag card, RFID serial number, etc.)</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>PrimaryIdentificationModelDescription</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>SecondaryIdentificationModelDescription</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>FleetCode</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Fleet Code</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>FleetName</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Fleet Name</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>VehiclePlate</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Licence plate</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>VehicleClassDescription</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Vehicle Class</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>VehicleClassificationValue1</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p><br>
				</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>VehicleClassificationValue2</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p><br>
				</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>VehicleClassificationValue3</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p><br>
				</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>VehicleClassificationValue4</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p><br>
				</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>DriverName</p>
			</td>
			<td>
				<p>100</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Name of Driver</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>DriverClassificationValue1</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p><br>
				</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>DriverClassificationValue2</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p><br>
				</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>DriverClassificationValue3</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p><br>
				</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>DriverClassificationValue4</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p><br>
				</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>CustomerData</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>FastTrackData</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>TaxesData</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>FeesData</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>CompanyTaxpayerId</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>ApplicationCode</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>DisputeDate</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>Reason</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>State</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>DisputeCommentCompany</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>ResolvedDate</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>DisputeResolveNetworkComment</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>Odometer</p>
			</td>
			<td>
				<p>10</p>
			</td>
			<td>
				<p>N</p>
			</td>
			<td>
				<p>Odometer prompt result</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>SiteCountryId</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>SiteCountry</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>SiteAddress</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>SiteStateId</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>SiteState</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>SiteCity</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>SiteZipCode</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>SiteClassificationValue1</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>SiteClassificationValue2</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>SiteClassificationValue3</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>SiteClassificationValue4</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>SiteCustomField0</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>SiteCustomField1</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>SiteCustomField2</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>SiteCustomField3</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>DriverFirstName</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>DriverLastName</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>GPSVirtualOdometer</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>GPSDistance</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>GPSAddress</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>GPSComment</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>DriverCustomField0</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>DriverCustomField1</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>DriverCustomField2</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>DriverCustomField3</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>VehicleCustomField0</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>VehicleCustomField1</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>VehicleCustomField2</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>VehicleCustomField3</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>IdProgram</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>ProgramDescription</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>LatitudeStart</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>LongitudeStart</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>AltitudeStart</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>LatitudeEnd</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>LongitudeEnd</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>AltitudeEnd</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>ContingencyReason</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>AuthorizationType</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>AttendantCode</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>PumpSide</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>VehicleBrand</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>VehicleModel</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>Subsidized</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>SiteCountryCode</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>CompanyContractCustomInterface0</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>CompanyContractCustomInterface1</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>CompanyContractCustomInterface2</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>CompanyContractCustomInterface3</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>CompanyContractCustomInterface4</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>CompanyContractCustomOperation0</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>CompanyContractCustomOperation1</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>CompanyContractCustomOperation2</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>CompanyContractCustomOperation3</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>CompanyContractCustomOperation4</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>ProductsData</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>ModifiersData</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>ERPData</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>FuelERPCode</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>TransactionCurrency</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
			<td>
				<p>FILL</p>
			</td>
		</tr>
	</tbody>
</table>

**TransactionCurrency Response fields**

<table>
	<thead>
		<tr valign="top">
			<th align="left">
				Field Name
			</th>			
			<th align="left">
				Descriptions/Field Value(s)
			</th>
		</tr>
	</thead>
	<tbody>
		<tr valign="top">
			<td>
				<p align="left">IdCurrencySite</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteCurrencyCode</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteCurrencyFactor</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteProductAmountDispensed</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteProductAmountAuthorized</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteProductAmountRequested</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteProductAmountCompany</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteProductAmountMerchant</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteProductUnitPriceDispensed</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteProductUnitPriceAuthorized</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteProductUnitPriceRequested</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteProductUnitPriceMerchant</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteProductUnitPriceCompany</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteTransactionAmountDispensed</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteTransactionAmountAuthorized</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteTransactionAmountRequested</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteTransactionAmountCompany</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteTransactionAmountMerchant</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">IdCurrencyConversion</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConversionCurrencyCode</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConversionProductAmountDispensed</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConversionProductAmountAuthorized</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConversionProductAmountRequested</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConversionProductAmountCompany</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConversionProductAmountMerchant</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConversionProductUnitPriceDispensed</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConversionProductUnitPriceAuthorized</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConversionProductUnitPriceRequested</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConversionProductUnitPriceMerchant</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConversionProductUnitPriceCompany</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConversionTransactionAmountDispensed</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConversionTransactionAmountAuthorized</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConversionTransactionAmountRequested</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConversionTransactionAmountCompany</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConversionTransactionAmountMerchant</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">IdCurrencyConciliation</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConciliationCurrencyCode</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConciliationCurrencyFactor</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConciliationProductAmountDispensed</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConciliationProductAmountAuthorized</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConciliationProductAmountRequested</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConciliationProductAmountMerchant</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConciliationProductAmountCompany</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConciliationProductUnitPriceDispensed</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConciliationProductUnitPriceAuthorized</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConciliationProductUnitPriceRequested</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConciliationProductUnitPriceMerchant</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConciliationProductUnitPriceCompany</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConciliationTransactionAmountDispensed</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConciliationTransactionAmountAuthorized</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConciliationTransactionAmountRequested</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConciliationTransactionAmountCompany</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConciliationTransactionAmountMerchant</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">IdCurrencyMerchant</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">MerchantCurrencyCode</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">MerchantCurrencyFactor</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">MerchantProductAmountDispensed</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">MerchantProductAmountAuthorized</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">MerchantProductAmountRequested</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">MerchantProductAmount</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">MerchantProductUnitPriceDispensed</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">MerchantProductUnitPriceAuthorized</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">MerchantProductUnitPriceRequested</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">MerchantProductUnitPrice</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">MerchantTransactionAmountDispensed</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">MerchantTransactionAmountAuthorized</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">MerchantTransactionAmountRequested</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">MerchantTransactionAmount</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">IdCurrencyCompany</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyCurrencyCode</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyCurrencyFactor</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyProductAmountDispensed</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyProductAmountAuthorized</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyProductAmountRequested</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyProductAmount</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyProductUnitPriceDispensed</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyProductUnitPriceAuthorized</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyProductUnitPriceRequested</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyProductUnitPrice</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyTransactionAmountDispensed</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyTransactionAmountAuthorized</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyTransactionAmountRequested</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyTransactionAmount</p>
			</td>
			<td>
				<p align="left">FILL</p>
			</td>
		</tr>
	</tbody>
</table>

## 8 FastTrack Interface

The FastTrack interface includes actions to either insert a new FastTrack creation
request, or to demand the list of all FastTrack from ATIONet, or all that fulfill 
certain criteria according to the user filter parameters, such as Driver, Vehicle 
or such.

Depending on the particular Action Code, one of these actions is selected.
Request not passing this validation will be rejected.

The download can be limited by dates (from and to), but are not required necessarily
included in the request

### 8.1 Action Codes

The Action Code specifies the type of record transaction to be
retrieved; this differentiation is based on which action the user
needs requesting (Insert or Download), which in turn defines which
additional parameters are needed for the request to be fulfilled.

<table>
	<tr valign="top">
		<th align="left">
			Action Code
		</th>
		<th colspan="2" align="left">
			Description
		</th>
	</tr>
	<tr valign="top">
		<td rowspan="4">
			<p>971</p>
		</td>
		<td>
			<p>Title:</p>
		</td>
		<td>
			<p>Insert FastTrack Order</p>
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>Function:</p>
		</td>
		<td>
			<p>Adds a new FastTrack to ATIONet</p>
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>Allowed for:</p>
		</td>
		<td>
			<p>Subscribers and Fleet Companies</p>
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>Identification:</p>
		</td>
		<td>
			<p>Subscriber Code</p>
			<p>Company Code (Optional, unless user is a Company)</p>
			<p>Amount</p>
			<p>Vehicle Code, Driver Code, Vehicle Plate, IdSubaccount, Identifier (Only one is necessary)</p>
			<p>Site Code(Optional)</p>
			<p>FuelMaster Code, Currency Code (Only one is necessary)</p>
			<p>Description(Optional)</p>
			<p>Order Number(Optional)</p>
			<p>DateFrom (Optional)</p>
			<p>DateTo (Optional)</p>
			<p>Custom Parameters (Optional)</p>
		</td>
	</tr>
	<tr valign="top">
		<td rowspan="4">
			<p>972</p>
		</td>
		<td>
			<p>Title:</p>
		</td>
		<td>
			<p>FastTracks Download</p>
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>Function:</p>
		</td>
		<td>
			<p>Download FastTrack records</p>
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>Allowed for:</p>
		</td>
		<td>
			<p>Subscriber and Fleet Companies</p>
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>Identification:</p>
		</td>
		<td>
			<p>Subscriber Code</p>
			<p>Filter Parameters (Optional)</p>
		</td>
	</tr>
</table>


### 8.2 FastTracks Order Insert (POST) – Body Section Format *Request*

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
				<p align="left">SubscriberCode</p>
			</td>
			<td>
				<p align="left">3</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Required</p>
			</td>
			<td>
				<p align="left">Fixed. To be assigned by ATIONet</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ActionCode</p>
			</td>
			<td>
				<p align="left">3</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Required</p>
			</td>
			<td>
				<p align="left">See Action Codes section above</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyCode</p>
			</td>
			<td>
				<p align="left">30</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Conditional</p>
			</td>
			<td>
				<p align="left">Filter by company code</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ContractCode</p>
			</td>
			<td>
				<p align="left">20</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">See Action Codes section above</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">DriverCode</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">Is used to find SubAccount to link</p>
				<p align="left"> the new FastTrack</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">VehicleCode</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Required</p>
			</td>
			<td>
				<p align="left">Is used to find SubAccount to link</p>
				<p align="left"> the new FastTrack</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">VehiclePlate</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">Is used to find SubAccount to link</p>
				<p align="left"> the new FastTrack</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Identifier</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">Is used to find SubAccount to link</p>
				<p align="left"> the new FastTrack</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SubAccountId</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">Is used to find SubAccount to link</p>
				<p align="left"> the new FastTrack</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteCode</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">Limits where FastTrack can be used</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">MasterFuelCode</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Required if no Currency Code</p>
			</td>
			<td>
				<p align="left">Sets whether FastTrack amount corresponds</p>
				<p align="left">to fuel volume, and which one</p>
			</td>
		</tr><tr valign="top">
			<td>
				<p align="left">CurrencyCode</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Required if no Fuel Master Code</p>
			</td>
			<td>
				<p align="left">Sets whether FastTrack amount corresponds</p>
				<p align="left">to fuel value, and which one</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Amount</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Required</p>
			</td>
			<td>
				<p align="left">To date to filter transactions</p>
				<p align="left">&ldquo;yyyy/MM/dd hh:mm:ss&rdquo;</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">OrderNumber</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">Order number for user to set</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">DateFrom</p>
			</td>
			<td>
				<p align="left">19</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">From date to activate FastTrack</p>
				<p align="left">&ldquo;yyyy/MM/dd hh:mm:ss&rdquo;</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">DateTo</p>
			</td>
			<td>
				<p align="left">19</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">To date to end FastTrack</p>
				<p align="left">&ldquo;yyyy/MM/dd hh:mm:ss&rdquo;</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Custom* (0-9)</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">Additional parameters set by user</p>
				<p align="left">&ldquo;yyyy/MM/dd hh:mm:ss&rdquo;</p>
			</td>
		</tr>
		
	</tbody>
</table>

### 8.3 FastTracks Download (POST) – Body Section Format *Request*

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
				<p align="left">SubscriberCode</p>
			</td>
			<td>
				<p align="left">3</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Required</p>
			</td>
			<td>
				<p align="left">Fixed. To be assigned by ATIONet</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ActionCode</p>
			</td>
			<td>
				<p align="left">3</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Required</p>
			</td>
			<td>
				<p align="left">See Action Codes section above</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyCode</p>
			</td>
			<td>
				<p align="left">30</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">Used to filter FastTrack by company</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">OrderNumber</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">Find by order number</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SubAccountsIds</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">Filter by SubAccount Ids</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteId</p>
			</td>
			<td>
				<p align="left">30</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">Filter by Site Id</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteName</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">Filter by Site Name</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Site Code</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">Filter by Site Code</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">FuelMasterId</p>
			</td>
			<td>
				<p align="left">30</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">Filter by FuelMaster Id</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">FuelMasterCode</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">Filter by Fuel Master Code</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">IdentifierLabel</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">Filter by Identifier Label</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CurrencyCode</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">Filter by Currency Code</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">VehicleCode</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">Filter by Vehicle Code</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">VehiclePlate</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">Filter by VehiclePlate</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">DriverCode</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">Filter by Driver Code</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ContractCode</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">Filter by Contract Code</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">DateFrom</p>
			</td>
			<td>
				<p align="left">19</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">From date of Fast Track creation</p>
				<p align="left">&ldquo;yyyy/MM/dd hh:mm:ss&rdquo;</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">DateTo</p>
			</td>
			<td>
				<p align="left">19</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">To date of Fast Track creation</p>
				<p align="left">&ldquo;yyyy/MM/dd hh:mm:ss&rdquo;</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ValidFrom</p>
			</td>
			<td>
				<p align="left">19</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">From date of Fast Track enabled</p>
				<p align="left">&ldquo;yyyy/MM/dd hh:mm:ss&rdquo;</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">DateTo</p>
			</td>
			<td>
				<p align="left">19</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">To date of Fast Track finalization</p>
				<p align="left">&ldquo;yyyy/MM/dd hh:mm:ss&rdquo;</p>
			</td>
		</tr>
		
		
	</tbody>
</table>


### 8.4 FastTracks Download (POST) – Body Section Format *Response*

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
				Descriptions/Field Value(s)
			</th>
		</tr>
	</thead>
	<tbody>
		<tr valign="top">
			<td>
				<p align="left">FastTrackId</p>
			</td>
			<td>
				<p align="left">30</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">FastTrack Id in ATIONet</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SubscriberCode</p>
			</td>
			<td>
				<p align="left">3</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Fixed. To be assigned by ATIONet</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SubscriberName</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">User network's name</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ResponseCode</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Response code from when FastTrack</p>
				<p align="left">was inserted</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ResponseMessage</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Response message from when FastTrack</p>
				<p align="left">was inserted</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Status</p>
			</td>
			<td>
				<p align="left">1</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">FastTrack's current status</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteCode</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">FastTrack site's code (if any)</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteName</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">FastTrack site's full name (if any)</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Amount</p>
			</td>
			<td>
				<p align="left">18</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">FastTrack's value amount (currency/volume)</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">FuelMasterCode</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">FastTrack fuel master's code (if any)</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">FuelMasterDescription</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">FastTrack fuel master's name (if any)</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyName</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">FastTrack company's name</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyCode</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">FastTrack company's code</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ContractCode</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">FastTrack contract's code</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ContractDescription</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">FastTrack contract's description</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SubAccountId</p>
			</td>
			<td>
				<p align="left">30</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">FastTrack sub account's Id</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CurrencyCode</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">FastTrack currency's code (if any)</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CurrencyDescription</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">FastTrack currency's description (if any)</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CurrencyCountryDescription</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">FastTrack currency's country description</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">MessageFormatVersion</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Message version of FastTrack insert request</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SystemModel</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">System's model of FastTrack insert request</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">DriverCode</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">FastTrack driver's code (if any)</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">VehicleCode</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">FastTrack vehicle's code (if any)</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">VehiclePlate</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">FastTrack vehicle's plate (if any)</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Identifier</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">FastTrack identifier</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ValidFrom</p>
			</td>
			<td>
				<p align="left">19</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">Date since FastTrack is enabled</p>
				<p align="left">&ldquo;yyyy/MM/dd hh:mm:ss&rdquo;</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ValidUntil</p>
			</td>
			<td>
				<p align="left">19</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">Date until FastTrack is disabled</p>
				<p align="left">&ldquo;yyyy/MM/dd hh:mm:ss&rdquo;</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CreationDate</p>
			</td>
			<td>
				<p align="left">19</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">Date when FastTrack was created (UTC)</p>
				<p align="left">&ldquo;yyyy/MM/dd hh:mm:ss&rdquo;</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CreationDateNetwork</p>
			</td>
			<td>
				<p align="left">19</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">Date when FastTrack was created (Network's timezone)</p>
				<p align="left">&ldquo;yyyy/MM/dd hh:mm:ss&rdquo;</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Custom* (0-9)</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">Additional parameters set by user</p>
				<p align="left">&ldquo;yyyy/MM/dd hh:mm:ss&rdquo;</p>
			</td>
		</tr>
		
	</tbody>
</table>

## 9 Account Enquiries

The Account Enquiries messages retrieve data from ATIONet, specific to a
Contract or Sub-Account (Vehicle or Driver types).

Depending on the type of enquiry, this message might be used by one or
the other party of the contract (the subscriber or the fleet company).

### 9.1 Action Codes

The Action Code specifies the type of enquiry requested. The submitted
code must match one of the pre-defined operation types. Not all
operation types are available for all subscribers and/or fleet
companies; availability depends on subscription types but also on
contract terms with ATIONet.

<table>
	<tr valign="top">
		<th align="left">
			Action Code
		</th>
		<th colspan="2" align="left">
			Description
		</th>
	</tr>
	<tr valign="top">
		<td rowspan="2">
			<p>941</p>
		</td>
		<td>
			<p>Title:</p>
		</td>
		<td>
			<p>Sub-account Balance Enquiry</p>
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>Function:</p>
		</td>
		<td>
			<p>Retrieves the total Balance for a given Sub-Account (Vehicle or Driver). Works with product or money based current accounts. On a product account, it returns the volume balance and the master product code. May return up to two product-volume pair when the vehicle is a dual-product unit.</p>
			<p>This message only retrieves information from ATIONet&rsquo;s Current Account subsystem, without considering any other business rule that may apply to the Site, Vehicle and/or Driver, which may potentially impact on the amount or limit that would be authorized at transaction time.</p>
		</td>
	</tr>
</table>

### 9.2 Identification

When an Account Enquiry is received, ATIONet will try to identify the
Company and the Identifier of the sub-account (Vehicle or Driver), this
can be performed thru several combinations of the Identification Fields
on the body of the message:

1.  Any Identifier field (Identifier, Driver Code, Vehicle Code, Vehicle
    Plate, SubAccount External Code and SubAccount Id) only. Only
    accepted for Home-base subscriptions.

2.  Company Code + Identifier.

3.  Company Code + Contract Code + (Driver Code or Vehicle Code or
    Vehicle Plate)

### 9.3 Account Enquiry (POST) – Body Section Record Format *Request*

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
				<p align="left">SubscriberCode</p>
			</td>
			<td>
				<p align="left">3</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Required</p>
			</td>
			<td>
				<p align="left">Fixed. To be assigned by ATIONet</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ActionCode</p>
			</td>
			<td>
				<p align="left">3</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Required</p>
			</td>
			<td>
				<p align="left">Operation type code.
				<br>See Action Code Section.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyCode</p>
			</td>
			<td>
				<p align="left">30</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">See Identification section</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ContractCode</p>
			</td>
			<td>
				<p align="left">20</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">See Identification section</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">DriverCode</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">See Identification section</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">VehicleCode</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">See Identification section</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">VehiclePlate</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">See Identification section</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SubAccountExternalCode</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">See Identification section</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SubAccountId</p>
			</td>
			<td>
				<p align="left">36</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">See Identification section</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Identifier</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">Public ID of the identification device (chipkey ID, account number on a mag card, RFID serial number, etc.)</p>
				<p align="left">See Identification section</p>
			</td>
		</tr>
	</tbody>
</table>

### 9.4 Account Enquiry (POST) – Body Section Record Format *Response*

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
				Descriptions/Field Value(s)
			</th>
		</tr>
	</thead>
	<tbody>
		<tr valign="top">
			<td>
				<p align="left">SubscriberCode</p>
			</td>
			<td>
				<p align="left">3</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Fixed. To be assigned by ATIONet</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyCode</p>
			</td>
			<td>
				<p align="left">30</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Company identification. Should be ignored on Homebase subscribers.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyName</p>
			</td>
			<td>
				<p align="left">250</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Company name. Should be ignored on Homebase subscribers.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ContractCode</p>
			</td>
			<td>
				<p align="left">20</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Contract identification. Should be ignored on Homebase subscribers.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>SubContractCode</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>SubContract code</p>
				<p>Not meaningful for Homebase subscribers</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>SubAccountId</p>
			</td>
			<td>
				<p>36</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>SubAccount&rsquo;s UID</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>SubAccountExternalCode</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>SubAccount&rsquo;s external code</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">DriverCode</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">See Identification section</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">VehicleCode</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">See Identification section</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">VehiclePlate</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">See Identification section</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Identifier</p>
			</td>
			<td>
				<p align="left">250</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Identifications related to
				subaccount</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>FuelMasterCode</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Standardized product code. Helps to identify a fuel product category across multiple Merchant brands and site&rsquo;s product codes</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>FuelMasterDescription</p>
			</td>
			<td>
				<p>100</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Standardized product description. Helps to identify a fuel product category across multiple Merchant brands and site&rsquo;s product codes</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CurrencyCode</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A</p>
			</td>
			<td>
				<p align="left">Currency configured for the Contract</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Amount</p>
			</td>
			<td>
				<p align="left">10</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Amount balance for the sub-account.</p>
				<p align="left">xxxxxxx.xx</p>
			</td>
		</tr>
	</tbody>
</table>

## 10 Account Downloads

The Account Download messages are POST actions to recover all the
currents accounts movements processed by ATIONet for a given Company
Code depending on the particular Action Code.

The Action Code is validated against the type of company of the
authenticated user. Request not passing this validation will be
rejected.

The download will be limited by dates (from and to), which must be
included in the request

### 10.1 Action Codes

The Action Code specifies the type of record transaction to be
retrieved; this differentiation is based on the different roles on an
ATIONet operation (Fleet Company, Merchant, Network, Home-base), which
also mandates different ways to identify the requester and scope of
transactions to download.

<table>
	<tr valign="top">
		<th align="left">
			Action Code
		</th>
		<th colspan="2" align="left">
			Description
		</th>
	</tr>
	<tr valign="top">
		<td rowspan="4">
			<p>951</p>
		</td>
		<td>
			<p>Title:</p>
		</td>
		<td>
			<p>Movements Download</p>
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>Function:</p>
		</td>
		<td>
			<p>Download complete current account movements records</p>
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>Allowed for:</p>
		</td>
		<td>
			<p>Subscribers and Fleet Companies</p>
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>Identification:</p>
		</td>
		<td>
			<p>Subscriber Code</p>
			<p>Company Code (Optional, if included will act as a filter)</p>
		</td>
	</tr>
</table>

### 10.2 Account Download (POST) – Body Section Format *Request*

|Field Name|Size|Type|Condition|Descriptions/Field Value(s)|
|--- |--- |--- |--- |--- |
|SubscriberCode|3|A/N|Required|Fixed. To be assigned by ATIONet|
|ActionCode|3|N|Required|See Action Codes section above|
|CompanyCode|30|A/N|Conditional|See Action Codes section above|
|DateFrom|19|A/N|Required|From date to filter movements "yyyy/MM/dd hh:mm:ss"|
|DateTo|19|A/N|Optional|To date to filter movements "yyyy/MM/dd hh:mm:ss"|

### 10.3 Account Download (POST) – Body Section Format *Response*

|Field Name|Size|Type|Descriptions/Field Value(s)|
|--- |--- |--- |--- |
|Id|36|A/N|Current account’s UID|
|MovementId|36|A/N|Movements’s UID|
|SubscriberCode|3|A/N|Code of the subscriber who owns the transaction|
|HostDateTime|19|A/N|ATIONet’s transaction date time "yyyy/mm/dd hh:mm:ss" (ATIONet Host date time is UCT)|
|DateTime|19|A/N|movement date expressed in subscriber time zone (yyyy/mm/dd hh:mm:ss)|
|SubscriberTimeZone|50|A/N|TimeZone code of the subscriber (abbreviation)|
|Type|1|N|Internal ATIOnet movement type code|
|TypeDescription|50|A/N|Movement type description|
|Origin|1|N|Internal ATIOnet code for the origin of the movement|
|OriginDescription|50|A/N|Description for the origin of the movement|
|Description|1000|A/N|Movement description|
|SubAccountId|36|A/N|SubAccount’s UID|
|SubAccountExternalCode|50|A/N|SubAccount’s external code|
|CompanyCode|30|A/N|Company code (Not meaningful for Homebase subscribers)|
|CompanyName|250|A/N|Company name (Not meaningful for Homebase subscribers)|
|ContractCode|20|A/N|Contract code (Not meaningful for Homebase subscribers)|
|SubContractCode|50|A/N|SubContract code (Not meaningful for Homebase subscribers)|
|IsDebit|1|N|Indicates that’s a debit or credit movement (1 = "True", 2= "False")|
|FuelMasterCode|50|A/N|Standardized product code. Helps to identify a fuel product category across multiple Merchant brands and site’s product codes|
|FuelMasterDescription|100|A/N|Standardized product description. Helps to identify a fuel product category across multiple Merchant brands and site’s product codes|
|CurrencyCode|50|A/N|Currency of the amount fields|
|Amount|10|N|Amount balance for the sub-account. (xxxxxxx.xx)|


## 11 Inventory and deliveries Downloads

The Inventory and Delivery Download messages are POST actions to recover all the
transactions processed by ATIONET for a given Merchant or the complete Subscriber
Code depending on the particular Action Code.

The Action Code is validated against the type of company of the
authenticated user. Request not passing this validation will be
rejected.

The download will be limited by dates (from and to), which must be
included in the request

### 11.1 Action Codes

The Action Code specifies the type of record transaction to be
retrieved; this differentiation is based on the different roles on an
ATIONet operation (Merchant, Network), which
also mandates different ways to identify the requester and scope of
transactions to download.

<table>
	<tr valign="top">
		<th align="left">
			Action Code
		</th>
		<th colspan="2" align="left">
			Description
		</th>
	</tr>
	<tr valign="top">
		<td rowspan="4">
			<p>981</p>
		</td>
		<td>
			<p>Title:</p>
		</td>
		<td>
			<p>Deliveries Download</p>
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>Function:</p>
		</td>
		<td>
			<p>Download complete deliveries movements records</p>
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>Allowed for:</p>
		</td>
		<td>
			<p>Subscribers and Merchants</p>
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>Identification:</p>
		</td>
		<td>
			<p>Subscriber Code</p>
			<p>Merchant Code (If logged in with with the ROL MC Interfce API , if logged with ROL NW Interface API and included will act as a filter)</p>
		</td>
	</tr>
	<tr valign="top">
		<td rowspan="4">
			<p>982</p>
		</td>
		<td>
			<p>Title:</p>
		</td>
		<td>
			<p>Inventories Download</p>
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>Function:</p>
		</td>
		<td>
			<p>Download complete inventories movements records</p>
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>Allowed for:</p>
		</td>
		<td>
			<p>Subscribers and Merchants</p>
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>Identification:</p>
		</td>
		<td>
			<p>Subscriber Code</p>
			<p>Merchant Code (If logged in with with the ROL MC Interfce API , if logged with ROL NW Interface API and included will act as a filter)</p>
		</td>
	</tr>
</table>

### 11.2 Deliveries Download (POST) – Body Section Format *Request*

|Field Name|Size|Type|Condition|Descriptions/Field Value(s)|
|--- |--- |--- |--- |--- |
|SubscriberCode|3|A/N|Required|Fixed. To be assigned by ATIONet|
|ActionCode|3|A/N|Required|See Action Codes section above|
|CompanyCode|30|A/N|Conditional|See Action Codes section above|
|DateFrom|19|A/N|Required|From date to filter movements ("yyyy/MM/dd hh:mm:ss")|
|DateTo|19|A/N|Optional|To date to filter movements ("yyyy/MM/dd hh:mm:ss")|

### 11.3 Deliveries Download (POST) – Body Section Format *Response*

|Field Name|Size|Type|Descriptions/Field Value(s)|
|--- |--- |--- |--- |
|DeliveryId|36|A/N|Delivery UID|
|MerchantName|250|A/N|Name of the company who owns the site|
|SiteCode|50|A/N|Site Code|
|SiteShortName|50|A/N|The short name of the site|
|TerminalCode|50|A/N|Site’s Terminal identification code.|
|TerminalDescription|50|A/N|Terminal description.|
|FuelMasterCode|50|A/N|Standardized product code. Helps to identify a fuel product category across multiple Merchant brands and site’s product codes|
|FuelMasterDescription|100|A/N|Standardized product description. Helps to identify a fuel product category across multiple Merchant brands and site’s product codes|
|ProductCode|50|A/N|The fuel code. It is associated with the site|
|TankNumber|50|A/N|The tank number|
|CreatedDateTime|19|A/N|The creation date time ("yyyy/MM/dd hh:mm:ss")|
|StartingDateTime|19|A/N|The starting date time ("yyyy/MM/dd hh:mm:ss")|
|EndingDateTime|19|A/N|the ending date time ("yyyy/MM/dd hh:mm:ss")|
|StartingVolume|10|N|The starting volume|
|StartingVolumeTC|10|N|The starting volume TC|
|StartingWaterVolume|10|N|The starting water volume|
|StartingTemperature|10|N|The starting temperature|
|StartingFuelHeight|10|N|The starting fuel height|
|EndingVolume|10|N|The ending volume|
|EndingVolumeTC|10|N|The ending volume TC|
|EndingWaterVolume|10|N|The ending water volume|
|EndingTemperature|10|N|the ending temperature|
|EndingFuelHeight|10|N|The ending fuel height|
|TotalVolume|10|N|The total volume|
|TotalVolumeTC|10|N|The total volume TC|
|DeliveryNotesData|X|X|Delivery receipt values - see below - see below|
|GPSData|X|X|GPS Values - see below|

### 11.4 Delivery GPS Download – DeliveryNotesData Body Section Format *Response*
|Field Name|Size|Type|Descriptions/Field Value(s)|
|--- |--- |--- |--- |
|InvoiceNumber|50|A/N|Delivery invoice Number|
|InvoiceItem|50|A/N|Invoice description|
|InvoiceDate|19|A/N|Invoice date time ("yyyy/MM/dd hh:mm:ss")|
|PhysicalAmountRemitted|10|N|Physical amount remitted on invoice|
|CompensatedAmountRemitted|10|N|Compensated amount remitted on invoice|
|RealTemperature|10|N|The actual and exact temperature of the product when it is loaded into the truck|
|ReferenceTemperature|10|N|It is for a calendar month and the average temperature of the place of delivery is taken. It is obtained from the national meteorological services of each country and it is with which the amount of the invoice is corrected|
|Density|10|N|The density of the product at the time of being loaded into the truck|

### 11.5 Delivery GPS Download – GPS Body Section Format *Response*

|Field Name|Size|Type|Descriptions/Field Value(s)|
|--- |--- |--- |---
|StartingGPSDate|19|A/N|The starting delivery GPS date ("yyyy/MM/dd hh:mm:ss")|
|EndingGPSDate|19|A/N|The ending delivery GPS date ("yyyy/MM/dd hh:mm:ss")|
|LatitudeStart|10|N|Start location: Latitude|
|LongitudeStart|10|N|Start location: Longitude|
|AltitudeStart|10|N|Start location: Altitude|
|LatitudeEnd|10|N|End location: Latitude|
|LongitudeEnd|10|N|End location: Longitude|
|AltitudeEnd|10|N|End location: Altitude|

### 11.6 Inventories Download (POST) – Body Section Format *Request*

|Field Name|Size|Type|Condition|Descriptions/Field Value(s)|
|--- |--- |--- |--- |--- |
|SubscriberCode|3|A/N|Required|Fixed. To be assigned by ATIONet|
|ActionCode|3|A/N|Required|See Action Codes section above|
|CompanyCode|30|A/N|Conditional|See Action Codes section above|
|DateFrom|19|A/N|Required|From date to filter movements ("yyyy/MM/dd hh:mm:ss")|
|DateTo|19|A/N|Optional|To date to filter movements ("yyyy/MM/dd hh:mm:ss")|

### 11.7 Inventories Download (POST) – Body Section Format *Response*

|Field Name|Size|Type|Descriptions/Field Value(s)|
|--- |--- |--- |--- |
|InventoryId|36|A/N|Delivery UID|
|MerchantName|250|A/N|Name of the company who owns the site|
|SiteCode|50|A/N|Site Code|
|SiteShortName|50|A/N|The short name of the site|
|TerminalCode|50|A/N|Site’s Terminal identification code.|
|TerminalDescription|50|A/N|Terminal description.|
|FuelMasterCode|50|A/N|Standardized product code. Helps to identify a fuel product category across multiple Merchant brands and site’s product codes|
|FuelMasterDescription|100|A/N|Standardized product description. Helps to identify a fuel product category across multiple Merchant brands and site’s product codes|
|ProductCode|50|A/N|The fuel code. It is associated with the site|
|TankNumber|50|A/N|The tank number|
|DateTime|19|A/N|Date time of the Inventory ("yyyy/MM/dd hh:mm:ss")|
|Volume|10|N|The volume|
|VolumeTC|10|N|The volume TC|
|Ullage|10|N|The ullage|
|WaterVolume|10|N|The water Volume|
|Temperature|10|N|The temperature|
|FuelHeight|10|N|The fuel height|
|WaterHeight|10|N|The water height|
|GPSDateTime|19|A/N|The inventory GPS date time ("yyyy/MM/dd hh:mm:ss")|
|Longitude|10|N|Location: Longitude|
|Latitude|10|N|Location: Latitude|
|Altitude|10|N|Location: Altitude|

## 12 Examples

### 12.1 C# example

```C#
using System.IO;
using System.IO.Compression;
using System.Net;
using System.Text;

using Newtonsoft.Json;
```

```C#
// Create Json object
object requestObject = new { ActionCode = "941", SubscriberCode = "{YourSubscriberCode}", Identifier = "{YourIdentifier}" };

// Serialize Json object
string request = JsonConvert.SerializeObject(requestObject);

// Get total bytes to send
int length = Encoding.ASCII.GetByteCount(request);

WebRequest webRequest = WebRequest.Create("https://native.ationet.com/v1/interface");

// Set gzip encoding (optional), user and password in the headers
webRequest.Headers = new WebHeaderCollection { "Accept-Encoding: gzip", "Authorization: Basic {User}:{Password}" };
webRequest.Method = "POST";
webRequest.ContentLength = length;

// Send request
using (Stream requestStream = webRequest.GetRequestStream())
{
	requestStream.Write(Encoding.ASCII.GetBytes(request), 0, length);
	requestStream.Close();
}

// Receive and analize response
using (WebResponse webResponse = webRequest.GetResponse())
{
	using (Stream stream = webResponse.GetResponseStream())
	{
		if (((HttpWebResponse)webResponse).StatusCode == HttpStatusCode.OK && stream != null)
		{
			// Handle response
			StreamReader reader = webResponse.Headers["Content-Encoding"] == "gzip"
			  ? new StreamReader(new GZipStream(stream, CompressionMode.Decompress))
			  : new StreamReader(stream);

			// Read response
			string response = reader.ReadToEnd();
		}
		else
		{
			// Handle error
		}
	}
}
```
