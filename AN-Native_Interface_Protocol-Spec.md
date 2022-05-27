![ationetlogo](Content/Images/ATIOnetLogo_250x70.png)
# ATIONet Native Interface API Protocol Specification

|Document Information|.|
|--- |--- |
|File:|ATIONet-Native_Interface_Protocol-Spec|
|Doc Version:|2.2|
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
|1.7|19/01/2022|**Document Update** <br> - Add CompanyGroups movements download: Request/Response <br> - Add Merchant Charges Comissions Download: Request/Response <br> - Add Sub-Account/Contract Balance Download: Request/Response <br> - Update Transaction Download Response <br> - Update company movements download request parameters <br> - Update Current Account Action Codes <br> - Update Transaction Action Codes <br> - Update Interface API Messages <br> - Update Transaction Currency Response Fields <br> - Add Transaction product format response <br> - Add Transaction Product Taxes Format Response <br> - Add Transaction Modifiers Format Response <br> - Add Transaction Movement ERP Format Response <br> - Add Transaction Fee Format Response|
|1.8|26/01/2022|**Document Update** <br> - Add Transaction custom fields download Request|
|1.9|04/04/2022|**Document Update** <br> - Company inserts addition|
|2.0|11/04/2022|**Document Update** <br> - Company inserts update|
|2.1|28/04/2022|**Document Update** <br> - Company inserts update fuel reference|
|2.2|26/05/2022|**Document Update** <br> - Add Company Contract Offline Balance Update Request|

## Contents

- [1 Scope](#1-scope)
	- [1.1 Scope details](#11-scope-details)

- [2 System Interface API](#2-system-interface-api)
	- [2.1 Interface API Messages](#21-interface-api-messages)
		- [2.1.1 Current Account Messages](#211-current-account-messages)
		- [2.1.2 Transaction Messages](#212-transaction-messages)
		- [2.1.3 FMS Messages](#213-fms-messages)

- [3 Data security](#3-data-security)

- [4 Message Structure](#4-message-structure)

- [5 Error handling](#5-error-handling)

- [6 Current Account Movements Interface](#6-current-account-movements-interface)
	- [6.1 Action Codes](#61-action-codes)
	- [6.2 Identification](#62-identification)
	- [6.3 Current Account Movements (POST) – Body Section Record Format](#63-current-account-movements-post--body-section-record-format)
        - [6.4 Company Contract Offline Balance Update (PUT) – Body Section Record Format](#64-company-contract-offline-balance-update-put--body-section-record-format)
- [7 Transactions Download Interface](#7-transactions-download-interface)
	- [7.1 Action Codes](#71-action-codes)
	- [7.2 Transactions Download (POST) – Body Section Format Request](#72-transactions-download-post--body-section-format-request)
	- [7.3 Transactions Download (POST) – Body Section Format Response](#73-transactions-download-post--body-section-format-response)
		- [7.3.1 Transaction Fee Format Response](#731-transaction-fee-format-response)
		- [7.3.2 Transaction Currency Format Response](#732-transaction-currency-format-response)
		- [7.3.3 Transaction Product Format Response](#733-transaction-product-format-response)
			- [7.3.3.1 Transaction Product Taxes Format Response](#7331-transaction-product-taxes-format-response)
		- [7.3.4 Transaction Modifiers Format Response](#734-transaction-modifiers-format-response)
		- [7.3.5 Transaction Movement ERP Format Response](#735-transaction-movement-erp-format-response)
	- [7.4 Transacionts Custom Fields Download (POST) – Body Section Format Request](#74-transacionts-custom-fields-download-post--body-section-format-request)

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
	- [10.2 Merchant Charges Comissions Download (POST) – Body Section Format Request](#102-merchant-charges-comissions-download-post--body-section-format-request)
	- [10.3 Merchant Charges Comissions Download (POST) – Body Section Format Response](#103-merchant-charges-comissions-download-post--body-section-format-response)
	- [10.4 Company Movements Download (POST) – Body Section Format Request](#104-company-movements-download-post--body-section-format-request)
	- [10.5 Company Movements Download (POST) – Body Section Format Response](#105-company-movements-download-post--body-section-format-response)
	- [10.6 Company Group Movements Download (POST) – Body Section Format Request](#106-company-group-movements-download-post--body-section-format-request)
	- [10.7 Company Group Movements Download (POST) – Body Section Format Response](#107-company-group-movements-download-post--body-section-format-response)
	- [10.8 Sub-Account/Contract Balance Download (POST) – Body Section Format Request](#108-sub-accountcontract-balance-download-post--body-section-format-request)
	- [10.9 Sub-Account/Contract Balance Download (POST) – Body Section Format Response](#109-sub-accountcontract-balance-download-post--body-section-format-response)

- [11 Inventory and deliveries Downloads](#11-Inventory-and-deliveries-Downloads)
	- [11.1 Action Codes](#111-Action-Codes)
	- [11.2 Deliveries Download (POST) – Body Section Format Request](#112-Deliveries-Download-POST--Body-Section-Format-Request)
	- [11.3 Deliveries Download (POST) – Body Section Format *Response*](#113-Deliveries-Download-POST--Body-Section-Format-Response)
	- [11.4 Delivery DeliveryNotesData Download - Body Section Format *Response*](#114-Delivery-DeliveryNotesData-Download--Body-Section-Format-Response)
	- [11.5 Delivery GPS Download - Body Section Format *Response*](#115-Delivery-GPS-Download--Body-Section-Format-Response)
	- [11.6 Inventories Download (POST) – Body Section Format *Request*](#116-Inventories-Download-POST--Body-Section-Format-Request)
	- [11.7 Inventories Download (POST) – Body Section Format *Response*](#117-Inventories-Download-POST--Body-Section-Format-Response)

- [12 Company Inserts](#12-Company-Inserts)
	- [12.1 Native Api Request](#121-nativeapirequest)
	- [12.2 Base Interface Request](#122-baseinterfacerequest)
	- [12.3 Interface Company Request](#123-interfacecompanyrequest)
	- [12.4 Interface Company Contract](#124-interfacecompanycontract)
	- [12.5 Interface Fuel Contract](#125-interfacefuelcontract)
	- [12.6 Interface Site Contract](#126-interfacesitecontract)
	- [12.7 Interface Price Contract](#127-interfacepricecontract)
	- [12.8 Interface Modifier Contract](#128-interfacemodifiercontract)
	- [12.9 Interface Concept Contract](#129-interfaceconceptcontract)
	- [12.10 Interface Block Contract](#1210-interfaceblockcontract)
	- [12.11 Interface Overlimit Contract](#1211-interfaceoverlimitcontract)
	- [12.12 Interface Program Contract](#1212-InterfaceProgramContract)
	- [12.13 Response Messages](#1213-response-messages)

- [13 Examples](#13-Examples)
	- [13.1 C# example](#131-C-example)
	- [13.2 Example](#132-example)

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
    <td class="tg-rjo2" rowspan="24">Current Accounts</td>
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
    <td class="tg-eygw">908</td>
    <td class="tg-eygw">Balance credit transfer to contract</td>
  </tr>
  <tr>
    <td class="tg-eygw">909</td>
    <td class="tg-eygw">Balance credit withdraw from contract</td>
  </tr>
  <tr>
    <td class="tg-eygw">911</td>
    <td class="tg-eygw">Merchant balance transfer to contract</td>
  </tr>
  <tr>
    <td class="tg-eygw">912</td>
    <td class="tg-eygw">Merchant balance withdraw from contract</td>
  </tr>
  <tr>
    <td class="tg-eygw">913</td>
    <td class="tg-eygw">Balance transfer to companies group</td>
  </tr>
  <tr>
    <td class="tg-eygw">914</td>
    <td class="tg-eygw">Balance withdraw from companies group</td>
  </tr>
  <tr>
    <td class="tg-eygw">915</td>
    <td class="tg-eygw">Recharge to sub account</td>
  </tr>
  <tr>
    <td class="tg-eygw">916</td>
    <td class="tg-eygw">Quotation Insert</td>
  </tr>
  <tr>
    <td class="tg-eygw">922</td>
    <td class="tg-eygw">Merchant charges comissions download</td>
  </tr>
  <tr>
    <td class="tg-eygw">925</td>
    <td class="tg-eygw">Company Insert</td>
  </tr>
  <tr>
    <td class="tg-eygw">926</td>
    <td class="tg-eygw">Company contract credit limit update</td>
  </tr>
  <tr>
    <td class="tg-eygw">928</td>
    <td class="tg-eygw">Company contract offline balance update</td>
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
    <td class="tg-eygw">945</td>
    <td class="tg-eygw">Merchant contract balance download</td>
  </tr>
  <tr>
    <td class="tg-eygw">946</td>
    <td class="tg-eygw">Merchant movements download</td>
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
    <td class="tg-rjo2" rowspan="17">Transactions</td>
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
    <td class="tg-eygw">940</td>
    <td class="tg-eygw">ERP Transaction insert</td>
  </tr>
  <tr>
    <td class="tg-gvcd">943</td>
    <td class="tg-gvcd">ConsumerCard transactions download</td>
  </tr>
  <tr>
    <td class="tg-eygw">944</td>
    <td class="tg-eygw">ConsumerCard exceptions download</td>
  </tr>
  <tr>
    <td class="tg-eygw">949</td>
    <td class="tg-eygw">Mobile payment fleet transactions download</td>
  </tr>
  <tr>
    <td class="tg-eygw">961</td>
    <td class="tg-eygw">Retail transactions download</td>
  </tr>
  <tr>
    <td class="tg-eygw">962</td>
    <td class="tg-eygw">Retail barch close download</td>
  </tr>
  <tr>
    <td class="tg-eygw">993</td>
    <td class="tg-eygw">Loyalty transactions download</td>
  </tr>
  <tr>
    <td class="tg-eygw">994</td>
    <td class="tg-eygw">Transaction invoice update</td>
  </tr>
</tbody>
</table>

#### 2.1.3 FMS Messages

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
    <td class="tg-rjo2" rowspan="2">FMS</td>
    <td class="tg-eygw">981</td>
    <td class="tg-eygw">Deliveries download</td>
  </tr>
  <tr>
    <td class="tg-gvcd">982</td>
    <td class="tg-gvcd">Inventories download</td>
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
    <td class="tg-eygw">908</td>
    <td class="tg-dqd0">Balance credit transfer to contract</td>
    <td class="tg-eygw">Transfer a given value from credit balance to a contract</td>
  </tr>
  <tr>
    <td class="tg-eygw">909</td>
    <td class="tg-dqd0">Balance credit withdraw from contract</td>
    <td class="tg-eygw">Withdraws a given value from credit balance to a contract</td>
  </tr>
  <tr>
    <td class="tg-eygw">911</td>
    <td class="tg-dqd0">Merchant balance transfer to contract</td>
    <td class="tg-eygw">Transfer a given value from merchant balance to a contract</td>
  </tr>
  <tr>
    <td class="tg-eygw">912</td>
    <td class="tg-dqd0">Merchant balance withdraw to contract</td>
    <td class="tg-eygw">Withdraws a given value from merchant balance to a contract</td>
  </tr>
  <tr>
    <td class="tg-eygw">913</td>
    <td class="tg-dqd0">Balance transfer to companies group</td>
    <td class="tg-eygw">Transfer a given value to a company group</td>
  </tr>
  <tr>
    <td class="tg-eygw">914</td>
    <td class="tg-dqd0">Balance withdraw to companies group</td>
    <td class="tg-eygw">Withdraws a given value to a company group</td>
  </tr>
  <tr>
    <td class="tg-eygw">915</td>
    <td class="tg-dqd0">Recharge to sub account</td>
    <td class="tg-eygw">Recharge a given value to a sub account</td>
  </tr>
  <tr>
    <td class="tg-eygw">916</td>
    <td class="tg-dqd0">Quotation insert</td>
    <td class="tg-eygw">Adds or update a quote to the network using the configured conversion currency.</td>
  </tr>
	
  <tr>
    <td class="tg-eygw">922</td>
    <td class="tg-dqd0">Merchant charges comissions download</td>
    <td class="tg-eygw">Downloads the merchant charges commissions</td>
  </tr>	
  <tr>
    <td class="tg-eygw">925</td>
    <td class="tg-dqd0">Company insert</td>
    <td class="tg-eygw">Adds or update a company related to the user network</td>
  </tr>	
  <tr>
    <td class="tg-eygw">926</td>
    <td class="tg-dqd0">Company contract credit limit update</td>
    <td class="tg-eygw">Update the credit limit related to the given company</td>
  </tr>
  <tr>
    <td class="tg-eygw">928</td>
    <td class="tg-dqd0">Company contract offline balanc update</td>
    <td class="tg-eygw">Update the offline balance related to the given company contract.</td>
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
    <td class="tg-eygw">945</td>
    <td class="tg-dqd0">Merchant contract balance download</td>
    <td class="tg-eygw">Downloads the the balance of the given merchant contract</td>
  </tr>	
  <tr>
    <td class="tg-eygw">946</td>
    <td class="tg-dqd0">Merchant movements download</td>
    <td class="tg-eygw">Downloads the movements of a determined merchant</td>
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

### 6.4 Company Contract Offline Balance Update (PUT) – Body Section Record Format

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
				<p align="left">SubscriberId</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">Subscriber/Network Id. Use optionally instead of SubscriberCode  
				</p>
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
				<p align="left">nvarchar</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">The Company Contract Code. Use optionally instead of Company Contract Id.  
				</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ContractId</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">The Company Contract Id. Use optionally instead of Company Contract Code.  
				</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">OfflineBalance</p>
			</td>
			<td>
				<p align="left">18.6</p>
			</td>
			<td>
				<p align="left">numeric</p>
			</td>
			<td>
				<p align="left">Required</p>
			</td>
			<td>
				<p align="left">The Company Contract Offline Balance that's going to be updated.  
				</p>
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
	<tr valign="top">
		<td rowspan="4">
			<p>948</p>
		</td>
		<td>
			<p>Title:</p>
		</td>
		<td>
			<p>Transactions Custom Fields Download</p>
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>Function:</p>
		</td>
		<td>
			<p>Download partial information of transactions records</p>
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
			<p>Fields (Required)</p>
			<p>Merchant Code (Optional, if included will act as a filter)</p>
			<p>Company Code (Optional, if included will act as a filter)</p>
			<p>Terminal Code(Optional, if included will act as a filter)</p>
			<p>Contract Code (Optional, if included will act as a filter)</p>
			<p>Identification ID (Optional, if included will act as a filter)</p>
			<p>Track Number (Optional, if included will act as a filter)</p>
			<p>PAN (Optional, if included will act as a filter)</p>
			<p>Company Group ID (Optional, if included will act as a filter)</p>
			<p>Company Group Code (Optional, if included will act as a filter)</p>
			<p>Transaction Modes (Optional, if included will act as a filter)</p>
			<p>Authorization Code (Optional, if included will act as a filter)</p>
			<p>Program Id(Optional, if included will act as a filter)</p>
			<p>Date From (Optional, if included will act as a filter)</p>
			<p>Date To (Optional, if included will act as a filter)</p>
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
				<p>1</p>
			</td>
			<td>
				<p>N</p>
			</td>
			<td>
				<p>Transaction mode <br> 0 = Standard <br> 1 = Offline <br> 2 = Contingecy</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>Type</p>
			</td>
			<td>
				<p>1</p>
			</td>
			<td>
				<p>N</p>
			</td>
			<td>
				<p>Type of transaction <br> 0 = PreAuthorization <br> 1 = Completion <br> 2 = Sale <br> 3 = Refund <br> 4 = Disputed <br> 5 = Cancellation <br> 6 = Voided <br> 7 = BalanceInquiry</p>
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
				<p>30</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>The merchant contract code</p>
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
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Merchat custom field 0</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>MerchantCustomField1</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Merchat custom field 1</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>MerchantCustomField2</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Merchat custom field 2</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>MerchantCustomField3</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Merchat custom field 3</p>
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
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Site short name</p>
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
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Type of terminal</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>TerminalId</p>
			</td>
			<td>
				<p>36</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Termianl&rsquo; UID</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>TerminalTypeId</p>
			</td>
			<td>
				<p>36</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>TerminalType&rsquo; UID</p>
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
				<p>36</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Secondary Sub-Account UID</p>
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
				<p>10</p>
			</td>
			<td>
				<p>N</p>
			</td>
			<td>
				<p>Transaction net amount</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>ProductUnitPriceRequested</p>
			</td>
			<td>
				<p>10</p>
			</td>
			<td>
				<p>N</p>
			</td>
			<td>
				<p>Rquested fuel price</p>
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
				<p>10</p>
			</td>
			<td>
				<p>N</p>
			</td>
			<td>
				<p>Authozized fuel price</p>
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
				<p>10</p>
			</td>
			<td>
				<p>N</p>
			</td>
			<td>
				<p>Dispensed fuel price</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>ProductNetAmountDispensed</p>
			</td>
			<td>
				<p>10</p>
			</td>
			<td>
				<p>N</p>
			</td>
			<td>
				<p>Net amount of fuel dispensed</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>ProductUnitPriceCompany</p>
			</td>
			<td>
				<p>10</p>
			</td>
			<td>
				<p>N</p>
			</td>
			<td>
				<p>Company fuel price</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>ProductUnitPriceMerchant</p>
			</td>
			<td>
				<p>10</p>
			</td>
			<td>
				<p>N</p>
			</td>
			<td>
				<p>Merchant fuel price</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>ProductAmountCompany</p>
			</td>
			<td>
				<p>10</p>
			</td>
			<td>
				<p>N</p>
			</td>
			<td>
				<p>Company fuel amount</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>ProductAmountMerchant</p>
			</td>
			<td>
				<p>10</p>
			</td>
			<td>
				<p>N</p>
			</td>
			<td>
				<p>Merchant fuel amount</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>TransactionAmountCompany</p>
			</td>
			<td>
				<p>10</p>
			</td>
			<td>
				<p>N</p>
			</td>
			<td>
				<p>Company transaction amount</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>TransactionAmountMerchant</p>
			</td>
			<td>
				<p>10</p>
			</td>
			<td>
				<p>N</p>
			</td>
			<td>
				<p>Merchant transaction amount</p>
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
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Company custom field 0</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>CompanyCustomField1</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Company custom field 1</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>CompanyCustomField2</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Company custom field 2</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>CompanyCustomField3</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Company custom field 3</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>CompaniesGroupCode</p>
			</td>
			<td>
				<p>30</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Company group code</p>
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
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Company Contract classification 1</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>CompanyContractClassificationValue2</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Company Contract classification 2</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>CompanyContractClassificationValue3</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Company Contract classification 3</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>CompanyContractClassificationValue4</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Company Contract classification 4</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>CompanyContractCustomField0</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Company contract customizable field 0</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>CompanyContractCustomField1</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Company contract customizable field 1</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>CompanyContractCustomField2</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Company contract customizable field 2</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>CompanyContractCustomField3</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Company contract customizable field 3</p>
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
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Primary track</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>SecondaryIdentificationTrack</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Secondary track</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>PrimaryIdentificationPAN</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Primary PAN</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>SecondaryIdentificationPAN</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Secondary PAN</p>
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
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Primary identifier model</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>SecondaryIdentificationModelDescription</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Secondary identifier model</p>
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
				<p>Vehicle clasiffication value 1<br>
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
				<p>Vehicle clasiffication value 2<br>
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
				<p>Vehicle clasiffication value 3<br>
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
				<p>Vehicle clasiffication value 4<br>
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
				<p>Driver classification value 1<br>
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
				<p>Driver classification value 2<br>
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
				<p>Driver classification value 3<br>
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
				<p>Driver classification value 4<br>
				</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>CustomerData</p>
			</td>
			<td>
				<p></p>
			</td>
			<td>
				<p>M</p>
			</td>
			<td>
				<p>Map of customer data</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>FastTrackData</p>
			</td>
			<td>
				<p></p>
			</td>
			<td>
				<p>M</p>
			</td>
			<td>
				<p>Map of fas track data</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>TaxesData</p>
			</td>
			<td>
				<p></p>
			</td>
			<td>
				<p>M</p>
			</td>
			<td>
				<p>Map of taxes data</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>FeesData</p>
			</td>
			<td>
				<p></p>
			</td>
			<td>
				<p>L</p>
			</td>
			<td>
				<p>List of fees data</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>CompanyTaxpayerId</p>
			</td>
			<td>
				<p>36</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Company taxpayer UID</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>ApplicationCode</p>
			</td>
			<td>
				<p>30</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Application code</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>DisputeDate</p>
			</td>
			<td>
				<p>19</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Duspte date time "yyyy/MM/dd HH:mm:ss"</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>Reason</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Dispute reason</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>State</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Dispute state</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>DisputeCommentCompany</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Company dispute comments</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>ResolvedDate</p>
			</td>
			<td>
				<p>19</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Dispute resolved date "yyyy/MM/dd HH:mm:ss"</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>DisputeResolveNetworkComment</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Network dispute resolved comments</p>
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
				<p>36</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Site country UID</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>SiteCountry</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>The site country</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>SiteAddress</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Site address</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>SiteStateId</p>
			</td>
			<td>
				<p>36</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Site state UID</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>SiteState</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Site state</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>SiteCity</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Site city</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>SiteZipCode</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Site zip code</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>SiteClassificationValue1</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Site classification value 1</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>SiteClassificationValue2</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Site classification value 2</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>SiteClassificationValue3</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Site classification value 3</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>SiteClassificationValue4</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Site classification value 4</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>SiteCustomField0</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Site custom field 0</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>SiteCustomField1</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Site custom field 1</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>SiteCustomField2</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Site custom field 2</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>SiteCustomField3</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Site custom field 3</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>DriverFirstName</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Driver first name</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>DriverLastName</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Driver last name</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>GPSVirtualOdometer</p>
			</td>
			<td>
				<p>10</p>
			</td>
			<td>
				<p>N</p>
			</td>
			<td>
				<p>GPS virtual odometer</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>GPSDistance</p>
			</td>
			<td>
				<p>10</p>
			</td>
			<td>
				<p>N</p>
			</td>
			<td>
				<p>GPS distance</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>GPSAddress</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>GPS address</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>GPSComment</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>GPS comments</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>DriverCustomField0</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Driver custom field 0</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>DriverCustomField1</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Driver custom field 1</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>DriverCustomField2</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Driver custom field 2</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>DriverCustomField3</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Driver custom field 3</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>VehicleCustomField0</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Vehicle custom field 0</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>VehicleCustomField1</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Vehicle custom field 1</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>VehicleCustomField2</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Vehicle custom field 2</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>VehicleCustomField3</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Vehicle custom field 3</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>IdProgram</p>
			</td>
			<td>
				<p>36</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Program UID</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>ProgramDescription</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Program description</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>LatitudeStart</p>
			</td>
			<td>
				<p>10</p>
			</td>
			<td>
				<p>N</p>
			</td>
			<td>
				<p>Location Start: Latitude</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>LongitudeStart</p>
			</td>
			<td>
				<p>10</p>
			</td>
			<td>
				<p>N</p>
			</td>
			<td>
				<p>Location Start: Longitude</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>AltitudeStart</p>
			</td>
			<td>
				<p>10</p>
			</td>
			<td>
				<p>N</p>
			</td>
			<td>
				<p>Location Start: Altitude</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>LatitudeEnd</p>
			</td>
			<td>
				<p>10</p>
			</td>
			<td>
				<p>N</p>
			</td>
			<td>
				<p>Location End: Latitude</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>LongitudeEnd</p>
			</td>
			<td>
				<p>10</p>
			</td>
			<td>
				<p>N</p>
			</td>
			<td>
				<p>Location End: Longitude</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>AltitudeEnd</p>
			</td>
			<td>
				<p>10</p>
			</td>
			<td>
				<p>N</p>
			</td>
			<td>
				<p>Location End: Altitude</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>ContingencyReason</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Contingecy reason</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>AuthorizationType</p>
			</td>
			<td>
				<p>1</p>
			</td>
			<td>
				<p>N</p>
			</td>
			<td>
				<p>Type of Authorization <br> 0 = Fleet (default) <br> 1 = Voucher <br> 2 = FastTrack</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>AttendantCode</p>
			</td>
			<td>
				<p>30</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Attendant code</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>PumpSide</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Pump side</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>VehicleBrand</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Vehicle Brand</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>VehicleModel</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Vehicle model</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>Subsidized</p>
			</td>
			<td>
				<p>1</p>
			</td>
			<td>
				<p>N</p>
			</td>
			<td>
				<p>Subsidized <br> 0 = false <br> 1 = true</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>SiteCountryCode</p>
			</td>
			<td>
				<p>30</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Site country code</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>CompanyContractCustomInterface0</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Company contract custom interface 0</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>CompanyContractCustomInterface1</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Company contract custom interface 1</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>CompanyContractCustomInterface2</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Company contract custom interface 2</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>CompanyContractCustomInterface3</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Company contract custom interface 3</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>CompanyContractCustomInterface4</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Company contract custom interface 4</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>CompanyContractCustomOperation0</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Company contract custom operation 0</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>CompanyContractCustomOperation1</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Company contract custom operation 1</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>CompanyContractCustomOperation2</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Company contract custom operation 2</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>CompanyContractCustomOperation3</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Company contract custom operation 3</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>CompanyContractCustomOperation4</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Company contract custom operation 4</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>ProductsData</p>
			</td>
			<td>
				<p></p>
			</td>
			<td>
				<p>List</p>
			</td>
			<td>
				<p>List of products data</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>ModifiersData</p>
			</td>
			<td>
				<p></p>
			</td>
			<td>
				<p>List</p>
			</td>
			<td>
				<p>List of modifiers data</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>ERPData</p>
			</td>
			<td>
				<p></p>
			</td>
			<td>
				<p>C</p>
			</td>
			<td>
				<p>Transaction movement ERP data</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>FuelERPCode</p>
			</td>
			<td>
				<p>30</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Fuel ERP code</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>TransactionCurrency</p>
			</td>
			<td>
				<p></p>
			</td>
			<td>
				<p>C</p>
			</td>
			<td>
				<p>Transaction currency data</p>
			</td>
		</tr>
	</tbody>
</table>

#### 7.3.1 Transaction Fee Format Response

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
				<p align="left">Name</p>
			</td>
			<td>
				<p align="left">50<p>
			</td>
			<td>
				<p align="left">A/N<p>
			</td>
			<td>
				<p align="left">Fee name</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Value</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Fee value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Id</p>
			</td>
			<td>
				<p align="left">36<p>
			</td>
			<td>
				<p align="left">A/N<p>
			</td>
			<td>
				<p align="left">Fee UID</p>
			</td>
		</tr>
	</tbody>
</table>

#### 7.3.2 Transaction Currency Format Response

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
				<p align="left">IdCurrencySite</p>
			</td>
			<td>
				<p align="left">36<p>
			</td>
			<td>
				<p align="left">A/N<p>
			</td>
			<td>
				<p align="left">Currency site UID</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteCurrencyCode</p>
			</td>
			<td>
				<p align="left">50<p>
			</td>
			<td>
				<p align="left">A/N<p>
			</td>
			<td>
				<p align="left">Site currency code</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteCurrencyFactor</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Site currency factor</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteProductAmountDispensed</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Amout of product dispensed by the site</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteProductAmountAuthorized</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Amount of product authorized by the site</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteProductAmountRequested</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Amount of product requested by the site</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteProductAmountCompany</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Site product amount company</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteProductAmountMerchant</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Site product amount merchant</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteProductUnitPriceDispensed</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Site product unit price dispensed</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteProductUnitPriceAuthorized</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Site product unit price authorized</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteProductUnitPriceRequested</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Site product unit price requested</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteProductUnitPriceMerchant</p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">Site product unit price merchant</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteProductUnitPriceCompany</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Site product unit price company</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteTransactionAmountDispensed</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Site transaction amount dispensed</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteTransactionAmountAuthorized</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Site transaction amount authorized</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteTransactionAmountRequested</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Site transacion amount requested</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteTransactionAmountCompany</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Site transaction amount company</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteTransactionAmountMerchant</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Site transaction amount merchant</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">IdCurrencyConversion</p>
			</td>
			<td>
				<p align="left">36<p>
			</td>
			<td>
				<p align="left">A/N<p>
			</td>
			<td>
				<p align="left">Currency Conversion UID</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConversionCurrencyCode</p>
			</td>
			<td>
				<p align="left">30<p>
			</td>
			<td>
				<p align="left">A/N<p>
			</td>
			<td>
				<p align="left">Currency conversion code</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConversionProductAmountDispensed</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Conversion product amount dispensed</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConversionProductAmountAuthorized</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Conversion product amount authorized</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConversionProductAmountRequested</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Conversion product amount requested</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConversionProductAmountCompany</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Conversion product amount company</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConversionProductAmountMerchant</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Conversion product amount merchant</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConversionProductUnitPriceDispensed</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Conversion product unit price dispensed</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConversionProductUnitPriceAuthorized</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Conversion product unit price authorized</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConversionProductUnitPriceRequested</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Conversion product unit price requested</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConversionProductUnitPriceMerchant</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Conversion product unit price merchant</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConversionProductUnitPriceCompany</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Conversion product unit price company</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConversionTransactionAmountDispensed</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Conversion transaction amount dispensed</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConversionTransactionAmountAuthorized</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Conversion transaction amount authorized</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConversionTransactionAmountRequested</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Conversion transaction amount requested</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConversionTransactionAmountCompany</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Conversion transaction amount company</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConversionTransactionAmountMerchant</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Conversion transaction amount merchant</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">IdCurrencyConciliation</p>
			</td>
			<td>
				<p align="left">36<p>
			</td>
			<td>
				<p align="left">A/N<p>
			</td>
			<td>
				<p align="left">Currency conciliation UID</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConciliationCurrencyCode</p>
			</td>
			<td>
				<p align="left">30<p>
			</td>
			<td>
				<p align="left">A/N<p>
			</td>
			<td>
				<p align="left">Currency Conciliation Code</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConciliationCurrencyFactor</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Conciliation currency factor</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConciliationProductAmountDispensed</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Conciliation product amount dispensed</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConciliationProductAmountAuthorized</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Conciliation product amount authorized</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConciliationProductAmountRequested</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Conciliation product amount requested</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConciliationProductAmountMerchant</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Conciliation product amount merchant</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConciliationProductAmountCompany</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Conciliation product amount company</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConciliationProductUnitPriceDispensed</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Conciliation product unit price dispensed</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConciliationProductUnitPriceAuthorized</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Conciliation product unit price authorized</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConciliationProductUnitPriceRequested</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Conciliation product unit price requested</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConciliationProductUnitPriceMerchant</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Conciliation product unit price merchant</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConciliationProductUnitPriceCompany</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Conciliation product unit price company</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConciliationTransactionAmountDispensed</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Conciliation transaction amount dispensed</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConciliationTransactionAmountAuthorized</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Conciliation transaction amount authorized</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConciliationTransactionAmountRequested</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Conciliation transaction amount requested</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConciliationTransactionAmountCompany</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Conciliation transaction amount company</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ConciliationTransactionAmountMerchant</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Conciliation transaction amount merchant</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">IdCurrencyMerchant</p>
			</td>
			<td>
				<p align="left">36<p>
			</td>
			<td>
				<p align="left">A/N<p>
			</td>
			<td>
				<p align="left">Currency Merchant UID</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">MerchantCurrencyCode</p>
			</td>
			<td>
				<p align="left">30<p>
			</td>
			<td>
				<p align="left">A/N<p>
			</td>
			<td>
				<p align="left">Merchant currency code</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">MerchantCurrencyFactor</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Merchant currency factor</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">MerchantProductAmountDispensed</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Merchant product amount dispensed</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">MerchantProductAmountAuthorized</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Merchant product amount authorized</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">MerchantProductAmountRequested</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Merchant product amount requested</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">MerchantProductAmount</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Merchant product amount</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">MerchantProductUnitPriceDispensed</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Merchant product unit price dispensed</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">MerchantProductUnitPriceAuthorized</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Merchant product unit price authorized</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">MerchantProductUnitPriceRequested</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Merchant product unit price requested</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">MerchantProductUnitPrice</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Merchant product unit price</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">MerchantTransactionAmountDispensed</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Merchant transacion amount dispensed</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">MerchantTransactionAmountAuthorized</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Merchant transacion amount authorized</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">MerchantTransactionAmountRequested</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Merchant transacion amount requested</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">MerchantTransactionAmount</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Merchant transacion amount</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">IdCurrencyCompany</p>
			</td>
			<td>
				<p align="left">36<p>
			</td>
			<td>
				<p align="left">A/N<p>
			</td>
			<td>
				<p align="left">Currency company UID</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyCurrencyCode</p>
			</td>
			<td>
				<p align="left">30<p>
			</td>
			<td>
				<p align="left">A/N<p>
			</td>
			<td>
				<p align="left">Currency company code</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyCurrencyFactor</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Company currency factor</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyProductAmountDispensed</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Company product amount dispensed</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyProductAmountAuthorized</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Company product amount authorized</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyProductAmountRequested</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Company product amount requested</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyProductAmount</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Company product amount</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyProductUnitPriceDispensed</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Company product unit price dispensed</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyProductUnitPriceAuthorized</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Company product unit price authorized</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyProductUnitPriceRequested</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Company product unit price requested</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyProductUnitPrice</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Company product unit price</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyTransactionAmountDispensed</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Company transaction amount dispensed</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyTransactionAmountAuthorized</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Company transaction amount authorized</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyTransactionAmountRequested</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Company transaction amount requested</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyTransactionAmount</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Company transaction amount</p>
			</td>
		</tr>
	</tbody>
</table>

#### 7.3.3 Transaction Product Format Response

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
				<p align="left">Product Code</p>
			</td>
			<td>
				<p align="left">30<p>
			</td>
			<td>
				<p align="left">A/N<p>
			</td>
			<td>
				<p align="left">The fuel code. It is associated with the site</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Product unit price</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">A<p>
			</td>
			<td>
				<p align="left">Fuel unit price</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Product net price</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">A<p>
			</td>
			<td>
				<p align="left">Fuel net price</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ProductNetAmount</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">A<p>
			</td>
			<td>
				<p align="left">Fuel net amountX</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ProductAmount</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">A<p>
			</td>
			<td>
				<p align="left">Fuel amount</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ProductQuantity</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">A<p>
			</td>
			<td>
				<p align="left">Fuel quantity</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">UnitCode</p>
			</td>
			<td>
				<p align="left">30<p>
			</td>
			<td>
				<p align="left">A/N<p>
			</td>
			<td>
				<p align="left">Unit code</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CategoryCode</p>
			</td>
			<td>
				<p align="left">30<p>
			</td>
			<td>
				<p align="left">A/N<p>
			</td>
			<td>
				<p align="left">Category code</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Taxes</p>
			</td>
			<td>
				<p align="left"><p>
			</td>
			<td>
				<p align="left">L<p>
			</td>
			<td>
				<p align="left">List of taxes applied</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ProductPosCode</p>
			</td>
			<td>
				<p align="left">30<p>
			</td>
			<td>
				<p align="left">A/N<p>
			</td>
			<td>
				<p align="left">Fuel post code</p>
			</td>
		</tr>
	</tbody>
</table>

#### 7.3.3.1 Transaction Product Taxes Format Response

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
				<p align="left">Code</p>
			</td>
			<td>
				<p align="left">30<p>
			</td>
			<td>
				<p align="left">A/N<p>
			</td>
			<td>
				<p align="left">Tax code</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Description</p>
			</td>
			<td>
				<p align="left">50<p>
			</td>
			<td>
				<p align="left">A/N<p>
			</td>
			<td>
				<p align="left">Tax description</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Factor</p>
			</td>
			<td>
				<p align="left">50<p>
			</td>
			<td>
				<p align="left">A/N<p>
			</td>
			<td>
				<p align="left">Factor applied to the tax</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Amount</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">A<p>
			</td>
			<td>
				<p align="left">Tax amount</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Value</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">A<p>
			</td>
			<td>
				<p align="left">Tax value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">FactorValue</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">A<p>
			</td>
			<td>
				<p align="left">Factor value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Included</p>
			</td>
			<td>
				<p align="left">1<p>
			</td>
			<td>
				<p align="left">A<p>
			</td>
			<td>
				<p align="left">Included <br> 0 = false <br> 1 = true</p>
			</td>
		</tr>
	</tbody>
</table>

#### 7.3.4 Transaction Modifiers Format Response

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
				<p align="left">ModifierClass</p>
			</td>
			<td>
				<p align="left">1<p>
			</td>
			<td>
				<p align="left">A<p>
			</td>
			<td>
				<p align="left">Modifier class <br> 0 = Discount <br> 1 = Recharge</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ModifierType</p>
			</td>
			<td>
				<p align="left">1<p>
			</td>
			<td>
				<p align="left">A<p>
			</td>
			<td>
				<p align="left">Modifier type <br> 0 = Percentual <br> 1 = FixedPerTransaction <br> 2 = FixedPerUnit</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ModifierValue</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">A<p>
			</td>
			<td>
				<p align="left">Modifier value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ModifierAmount</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">A<p>
			</td>
			<td>
				<p align="left">Modifier amount</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ModifierTotal</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">A<p>
			</td>
			<td>
				<p align="left">Modifier total</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">BaseValue</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">A<p>
			</td>
			<td>
				<p align="left">Base value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Description</p>
			</td>
			<td>
				<p align="left">50<p>
			</td>
			<td>
				<p align="left">A/N<p>
			</td>
			<td>
				<p align="left">Modifier description</p>
			</td>
		</tr>
	</tbody>
</table>

#### 7.3.5 Transaction Movement ERP Format Response

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
				<p align="left">ERPDate</p>
			</td>
			<td>
				<p align="left">19<p>
			</td>
			<td>
				<p align="left">A/N<p>
			</td>
			<td>
				<p align="left">ERP Date "yyyy/MM/dd HH:mm:ss"</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ERPInvoicedDate</p>
			</td>
			<td>
				<p align="left">19<p>
			</td>
			<td>
				<p align="left">A/N<p>
			</td>
			<td>
				<p align="left">ERP invoice Date "yyyy/MM/dd HH:mm:ss"</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">NetPrice</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Net price</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">NetAmount</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Net amount</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">TaxAmount0</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Tax amount 0</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">TaxAmount1</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Tax amount 1</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">TaxAmount2</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Tax amount 2</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">TaxAmount3</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Tax amount 3</p>
		</td>
		<tr valign="top">
			<td>
				<p align="left">TaxAmount4</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Tax amount 4</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">TaxAmount5</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Tax amount 5</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">OrderTotalAmount</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Order total amount</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">InvoiceTotalAmount</p>
			</td>
			<td>
				<p align="left">10<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">Invoice total amount</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ERPState</p>
			</td>
			<td>
				<p align="left">1<p>
			</td>
			<td>
				<p align="left">N<p>
			</td>
			<td>
				<p align="left">The ERP State <br> 0 = DailyOrder <br> 1 = Billed <br> 2 = Settled <br> 3 = VoidedWithAffectation <br> 4 = VoidedWithoutAffectation</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ERPInvoiceNumber</p>
			</td>
			<td>
				<p align="left">50<p>
			</td>
			<td>
				<p align="left">A/N<p>
			</td>
			<td>
				<p align="left">ERP Invoice number</p>
			</td>
		</tr>
	</tbody>
</table>

### 7.4 Transactions Custom Fields Download (POST) – Body Section Format Request

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
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">Merchant code to filter transactions by</p>
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
				<p align="left">Company code to filter transactions by</p>
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
				<p align="left">Company contract code to filter transactions by</p>
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
				<p align="left">Terminal code to filter transactions by</p>
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
		<tr valign="top">
			<td>
				<p align="left">IdentificationId</p>
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
				<p align="left">Identification UID to filter transactions</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">TrackNumber</p>
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
				<p align="left">TrackNumber to filter transactions</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">PAN</p>
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
				<p align="left">PAN to filter transactions</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">AuthorizationCode</p>
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
				<p align="left">Authorization code to filter transactions</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyGroupId</p>
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
				<p align="left">Company group UID to filter transactions</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyGroupCode</p>
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
				<p align="left">Company group code to filter transactions</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ProgramId</p>
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
				<p align="left">Program UID to filter transactions</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ProcessBillingStatementCompanyId</p>
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
				<p align="left">Company process billing statement UID to filter transactions by</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ProcessBillingStatementMerchantId</p>
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
				<p align="left">Merchant process billing statement UID to filter transactions by</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteId</p>
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
				<p align="left">Site UID to filter transactions by</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">TransactionModes</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">L</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">List of transacion modes to filter transactions <br> 0 = Standard <br> 1 = Offline <br> 2 = Contingency</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SubAccountTypes</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">L</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">List of subaccount types to filter transactions by <br> 0 = Fleet <br> 1 = Old Gift Card <br> 2 = Consumer Card <br> 3 = Gift Card</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">TransactionDateType</p>
			</td>
			<td>
				<p align="left">10</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">Transaction date type to filter transactions <br> 0 = RealDate <br> 1 = LocalTransactionDate <br> 2 = NetworkDate <br> 3 = CorrectedDate</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Fields</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">L</p>
			</td>
			<td>
				<p align="left">Required</p>
			</td>
			<td>
				<p align="left">List of transactions fields to be download</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Paginate</p>
			</td>
			<td>
				<p align="left">1</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
			<td>
				<p align="left">Indicates if the query result will be paginated <br> 0 = false <br> 1 = true</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">PageSize</p>
			</td>
			<td>
				<p align="left">10</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Conditional</p>
			</td>
			<td>
				<p align="left">Indicates the number of records to download in case the query is paginated.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Page</p>
			</td>
			<td>
				<p align="left">10</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Conditional</p>
			</td>
			<td>
				<p align="left">Indicates the page to be download</p>
			</td>
		</tr>
	</tbody>
</table>

### 7.4.1 Transactions Custom Fields

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
				<p align="left">State</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Dispute state</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteStateDescription</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">the site state description</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteCountryId</p>
			</td>
			<td>
				<p align="left">36</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Site country UID</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteCountry</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">The site country</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteAddress</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Site address</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteStateId</p>
			</td>
			<td>
				<p align="left">36</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Site state UID</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteCityDescription</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Site city description</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteZipCode</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Site zip code</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteCustomField0</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Site custom field 0</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteCustomField1</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Site custom field 1</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteCustomField2</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Site custom field 2</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteCustomField3</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Site custom field 3</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyTaxpayerId</p>
			</td>
			<td>
				<p align="left">36</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Company taxpayer UID</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">DriverClassificationCode2</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Driver classification code 2</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">DriverClassificationCode4</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Driver classification code 4</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">PrimaryIdentificationPAN</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Primary PAN</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SecondaryIdentificationTrack</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Secondary track</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SecondaryIdentificationPAN</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Secondary PAN</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">PrimaryIdentificationLabel</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Public ID of the primary identification device (chipkey ID, account number on a mag card, RFID serial number, etc.)</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SecondaryIdentificationLabel</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Public ID of the secondary identification device (chipkey ID, account number on a mag card, RFID serial number, etc.)</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">PrimaryIdentificationModelDescription</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Primary identifier model</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SecondaryIdentificationModelDescription</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Secondary identifier model</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">FleetCode</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Fleet code</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">FleetName</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Fleet name</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">PrimaryIdentificationTrack</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Primary identification track</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SecondaryIdentificationTrack</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Secondary track</p>
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
				<p align="left">Vehicle plate</p>
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
				<p align="left">Vehicle code</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">VehicleBrand</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Vehicle brand</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">VehicleModel</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Vehicle model</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">VehicleCustomField0</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Vehicle custom field 0</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">VehicleCustomField1</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Vehicle custom field 1</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">VehicleCustomField2</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Vehicle custom field 2</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">VehicleCustomField3</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Vehicle custom field 3</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">VehicleClassDescription</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Vehicle class</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">VehicleClassificationCode1</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Vehicle classifcation code 1</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">VehicleClassificationCode2</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Vehicle classifcation code 2</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">VehicleClassificationCode3</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Vehicle classifcation code 3</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">VehicleClassificationCode4</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Vehicle classifcation code 4</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">DriverName</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Driver name</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">DriverFirstName</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Driver first name</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">DriverLastName</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Driver last name</p>
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
				<p align="left">Driver code</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">DriverCustomField0</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Driver custom field 0</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">DriverCustomField1</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Driver custom field 1</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">DriverCustomField2</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Driver custom field 2</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">DriverCustomField3</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Driver custom field 3</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">DriverClassificationCode1</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Driver classification code 1</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">DriverClassificationCode3</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Driver classification code 3</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Subsidized</p>
			</td>
			<td>
				<p align="left">1</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Transaction subsidized active status <br> 0 = false <br> 1 = true</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteCountrySatCode</p>
			</td>
			<td>
				<p align="left">3</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Site country SAT Code</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteCountryDescription</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Site country description</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyContractCustomInterface0</p>
			</td>
			<td>
				<p align="left">1</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Company contract custom interface 0 active status <br> 0 = false <br> 1 = true</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyContractCustomInterface1</p>
			</td>
			<td>
				<p align="left">1</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Company contract custom interface 1 active status <br> 0 = false <br> 1 = true</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyContractCustomInterface2</p>
			</td>
			<td>
				<p align="left">1</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Company contract custom interface 2 active status <br> 0 = false <br> 1 = true</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyContractCustomInterface3</p>
			</td>
			<td>
				<p align="left">1</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Company contract custom interface 3 active status <br> 0 = false <br> 1 = true</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyContractCustomInterface4</p>
			</td>
			<td>
				<p align="left">1</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Company contract custom interface 4 active status <br> 0 = false <br> 1 = true</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyContractCustomOperation0</p>
			</td>
			<td>
				<p align="left">1</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Company contract custom operation 0 active status <br> 0 = false <br> 1 = true</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyContractCustomOperation1</p>
			</td>
			<td>
				<p align="left">1</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Company contract custom operation 1 active status <br> 0 = false <br> 1 = true</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyContractCustomOperation2</p>
			</td>
			<td>
				<p align="left">1</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Company contract custom operation 2 active status <br> 0 = false <br> 1 = true</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyContractCustomOperation3</p>
			</td>
			<td>
				<p align="left">1</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Company contract custom operation 3 active status <br> 0 = false <br> 1 = true</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyContractCustomOperation4</p>
			</td>
			<td>
				<p align="left">1</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Company contract custom operation 4 active status <br> 0 = false <br> 1 = true</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Odometer</p>
			</td>
			<td>
				<p align="left">10</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Transaction's customer data odometer value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">FastTrack</p>
			</td>
			<td>
				<p align="left">Varies</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">Transaction's fast track data mapped</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CustomerData</p>
			</td>
			<td>
				<p align="left">Varies</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">Transaction's customer data mapped</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">AuthorizationType</p>
			</td>
			<td>
				<p align="left">1</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Transaction's authorization type <br> 0 = fleet <br> 1 = voucher <br> 2 = fast track</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ProgramId</p>
			</td>
			<td>
				<p align="left">36</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Identification program UID</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ProgramDescription</p>
			</td>
			<td>
				<p align="left">100</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Identification program description</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">GiftCardProgramId</p>
			</td>
			<td>
				<p align="left">36</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Identification gift card program UID</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">GiftCardProgramName</p>
			</td>
			<td>
				<p align="left">100</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Identification program name</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">GiftCardProgramDescription</p>
			</td>
			<td>
				<p align="left">100</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Identification program description</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">GPSVirtualOdometer</p>
			</td>
			<td>
				<p align="left">10</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Transaction's GPS data virtual odometer value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">GPSDistance</p>
			</td>
			<td>
				<p align="left">18</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Transaction's GPS data distance value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">GPSAddress</p>
			</td>
			<td>
				<p align="left">100</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Transaction's GPS data adress</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">GPSComment</p>
			</td>
			<td>
				<p align="left">200</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Transaction's GPS data commentaries</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">GPSLatitudeStart</p>
			</td>
			<td>
				<p align="left">17</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Transaction's GPS data starting latitude</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">GPSLongitudeStart</p>
			</td>
			<td>
				<p align="left">17</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Transaction's GPS data starting longitude</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">GPSAltitudeStart</p>
			</td>
			<td>
				<p align="left">17</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Transaction's GPS data starting altitude</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Modifiers</p>
			</td>
			<td>
				<p align="left">Varies</p>
			</td>
			<td>
				<p align="left">L</p>
			</td>
			<td>
				<p align="left">A list of transaction's modifiers data</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyContractCustomField0</p>
			</td>
			<td>
				<p align="left">200</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Company contract custom field 0 value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyContractCustomField1</p>
			</td>
			<td>
				<p align="left">200</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Company contract custom field 1 value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyContractCustomField2</p>
			</td>
			<td>
				<p align="left">200</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Company contract custom field 2 value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyContractCustomField3</p>
			</td>
			<td>
				<p align="left">200</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Company contract custom field 3 value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">MerchantCustomField0</p>
			</td>
			<td>
				<p align="left">200</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Merchant custom field 0 value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">MerchantCustomField1</p>
			</td>
			<td>
				<p align="left">200</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Merchant custom field 1 value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">MerchantCustomField2</p>
			</td>
			<td>
				<p align="left">200</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Merchant custom field 2 value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">MerchantCustomField3</p>
			</td>
			<td>
				<p align="left">200</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Merchant custom field 3 value</p>
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
				<p align="left">Transaction's site code</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteName</p>
			</td>
			<td>
				<p align="left">100</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Transaction's site full name</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteShortName</p>
			</td>
			<td>
				<p align="left">100</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Transaction's site short name</p>
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
				<p align="left">Transaction's terminal code</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">TerminalId</p>
			</td>
			<td>
				<p align="left">36</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Transaction's terminal UID</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">TerminalType</p>
			</td>
			<td>
				<p align="left">100</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Transaction's terminal type description</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">TerminalTypeId</p>
			</td>
			<td>
				<p align="left">36</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Transaction's terminal type UID</p>
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
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Transaction's primary subaccount UID</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SecondarySubAccountId</p>
			</td>
			<td>
				<p align="left">36</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Transaction's secondary subaccount UID</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">AccountTypeDescription</p>
			</td>
			<td>
				<p align="left">7</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Transaction's account type description:<br> - Vehicle <br> - Driver <br></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">TransactionNetAmount</p>
			</td>
			<td>
				<p align="left">18</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Transaction's net amount value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ProductUnitPriceRequested</p>
			</td>
			<td>
				<p align="left">18</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Transaction's requested unit price value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">MerchantName</p>
			</td>
			<td>
				<p align="left">250</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Merchant name</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">MerchantContractCode</p>
			</td>
			<td>
				<p align="left">20</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Merchant contract code</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">DateTime</p>
			</td>
			<td>
				<p align="left">19</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Local transaction date and time value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">TransactionId</p>
			</td>
			<td>
				<p align="left">36</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Transaction's UID</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SubscriberId</p>
			</td>
			<td>
				<p align="left">36</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Subscriber's UID</p>
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
				<p align="left">Subscriber's code</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SubscriberName</p>
			</td>
			<td>
				<p align="left">250</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Subscriber's name</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">TransactionSequenceNumber</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Transaction's sequence number value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">AuthorizationCode</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Transaction's authorization code value</p>
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
				<p align="left">Transaction's response code value</p>
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
				<p align="left">Transaction's response message value</p>
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
				<p align="left">Transaction status value:<br> 0 = Ok <br> 1 = Processing <br>2 = PendingRetry <br>3 = PendingReprompt <br>4 = Dirty <br>5 = Error</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">StatusDescription</p>
			</td>
			<td>
				<p align="left">11</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Transaction status description</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Mode</p>
			</td>
			<td>
				<p align="left">1</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Transaction mode value:<br> 0 = Standard <br> 1 = Offline <br>2 = Contingency</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">HostDateTime</p>
			</td>
			<td>
				<p align="left">19</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">UTC transaction date and time value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SubscriberDateTime</p>
			</td>
			<td>
				<p align="left">19</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Subscriber date and time value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SubscriberTimeZone</p>
			</td>
			<td>
				<p align="left">150</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Subscriber time zone</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteDateTime</p>
			</td>
			<td>
				<p align="left">19</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Site date and time value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteTimeZone</p>
			</td>
			<td>
				<p align="left">150</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Site time zone</p>
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
				<p align="left">Merchant code</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ProductVolumeRequested</p>
			</td>
			<td>
				<p align="left">18</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Transaction's product volume requested</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">TransactionAmountRequested</p>
			</td>
			<td>
				<p align="left">18</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Transaction's amount requested</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">BatchNumber</p>
			</td>
			<td>
				<p align="left">10</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Transaction's batch number</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ShiftNumber</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Transaction's shift number</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">PumpNumber</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Transaction's pump number</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">EntryMethod</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Transaction's entry method</p>
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
				<p align="left">Company code</p>
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
				<p align="left">Company name</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyCustomField0</p>
			</td>
			<td>
				<p align="left">200</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Company custom field 0 value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyCustomField1</p>
			</td>
			<td>
				<p align="left">200</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Company custom field 1 value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyCustomField2</p>
			</td>
			<td>
				<p align="left">200</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Company custom field 2 value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyCustomField3</p>
			</td>
			<td>
				<p align="left">200</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Company custom field 3 value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompaniesGroupCode</p>
			</td>
			<td>
				<p align="left">30</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Companies group code</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ClassificationLabel1</p>
			</td>
			<td>
				<p align="left">200</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Company's classification 1 value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ClassificationLabel2</p>
			</td>
			<td>
				<p align="left">200</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Company's classification 2 value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ClassificationLabel3</p>
			</td>
			<td>
				<p align="left">200</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Company's classification 3 value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ClassificationLabel4</p>
			</td>
			<td>
				<p align="left">200</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Company's classification 4 value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyContractCode</p>
			</td>
			<td>
				<p align="left">20</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Company contract's code</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyContractCustomField0</p>
			</td>
			<td>
				<p align="left">200</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Company contract's custom field 0 value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyContractCustomField1</p>
			</td>
			<td>
				<p align="left">200</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Company contract's custom field 1 value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyContractCustomField2</p>
			</td>
			<td>
				<p align="left">200</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Company contract's custom field 2 value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CompanyContractCustomField3</p>
			</td>
			<td>
				<p align="left">200</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Company contract's custom field 3 value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">InvoiceNumber</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Transaction's invoice number value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ProductAmountRequested</p>
			</td>
			<td>
				<p align="left">18</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Transaction's product amount requested value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">FuelMasterDescription</p>
			</td>
			<td>
				<p align="left">100</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Transaction's fuel master description</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">FuelCode</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Transaction's fuel master code</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ProductUnitPriceAuthorized</p>
			</td>
			<td>
				<p align="left">18</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Transaction's product unit prize authorized value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ProductVolumeAuthorized</p>
			</td>
			<td>
				<p align="left">18</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Transaction's product volume authorized value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ProductAmountAuthorized</p>
			</td>
			<td>
				<p align="left">18</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Transaction's product amount authorized value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">TransactionAmountAuthorized</p>
			</td>
			<td>
				<p align="left">18</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Transaction's amount authorized value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ProductUnitPriceDispensed</p>
			</td>
			<td>
				<p align="left">18</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Transaction's product unit price dispensed value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ProductVolumeDispensed</p>
			</td>
			<td>
				<p align="left">18</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Transaction's product volume dispensed value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ProductAmountDispensed</p>
			</td>
			<td>
				<p align="left">18</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Transaction's product amount dispensed value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ProductNetAmountDispensed</p>
			</td>
			<td>
				<p align="left">18</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Transaction's product net amount dispensed value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">TransactionAmountDispensed</p>
			</td>
			<td>
				<p align="left">18</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Transaction's amount dispensed value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ProductUnitPriceCompany</p>
			</td>
			<td>
				<p align="left">18</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Transaction's company product unit price value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ProductUnitPriceMerchant</p>
			</td>
			<td>
				<p align="left">18</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Transaction's merchant product unit price value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ProductAmountCompany</p>
			</td>
			<td>
				<p align="left">18</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Transaction's company product amount value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ProductAmountMerchant</p>
			</td>
			<td>
				<p align="left">18</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Transaction's merchant product amount value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">TransactionAmountCompany</p>
			</td>
			<td>
				<p align="left">18</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Transaction's company amount value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">TransactionAmountMerchant</p>
			</td>
			<td>
				<p align="left">18</p>
			</td>
			<td>
				<p align="left">N</p>
			</td>
			<td>
				<p align="left">Transaction's merchant amount value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">UnitOfMeasurementCode</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">A/N</p>
			</td>
			<td>
				<p align="left">Transaction's unit of measurement code value</p>
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
				<p align="left">Transaction's currency code value</p>
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
				<p align="left">Transaction's fuel master code value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">BillingChargesItems</p>
			</td>
			<td>
				<p align="left">Varies</p>
			</td>
			<td>
				<p align="left">L</p>
			</td>
			<td>
				<p align="left">A list of the transaction's realted billing charges items</p>
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
			<p>922</p>
		</td>
		<td>
			<p>Title:</p>
		</td>
		<td>
			<p>Merchant charges commissions download</p>
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>Function:</p>
		</td>
		<td>
			<p>Download merchant charges comissions</p>
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>Allowed for:</p>
		</td>
		<td>
			<p></p>
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
	<tr valign="top">
		<td rowspan="4">
			<p>941/942</p>
		</td>
		<td>
			<p>Title:</p>
		</td>
		<td>
			<p>Balance download of Sub-account (941) / Contract (942)</p>
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>Function:</p>
		</td>
		<td>
			<p>Download balance for sub-account/contract</p>
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
			<p>Company Code</p>
			<p>Contract Code</p>
		</td>
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
			<p>Download complete current account movements records from a company</p>
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
	<tr valign="top">
		<td rowspan="4">
			<p>952</p>
		</td>
		<td>
			<p>Title:</p>
		</td>
		<td>
			<p>Company Group Movements Download</p>
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>Function:</p>
		</td>
		<td>
			<p>Download complete current account movements records from a company group</p>
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>Allowed for:</p>
		</td>
		<td>
			<p>NWInterfaceApi and CGInterfaceAPI </p>
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>Identification:</p>
		</td>
		<td>
			<p>Subscriber Code</p>
			<p>Companies Group Id (Optional, if included will act as a filter)</p>
		</td>
	</tr>
</table>

### 10.2 Merchant Charges Comissions Download (POST) – Body Section Format *Request*
|Field Name|Size|Type|Condition|Descriptions/Field Value(s)|
|--- |--- |--- |--- |--- |
|SubscriberCode|3|A/N|Required|Fixed. To be assigned by ATIONet|
|ActionCode|3|N|Required|See Action Codes section above|
|CompanyCode|30|A/N|Conditional|See Action Codes section above|
|State|1|N|Optional|The state of the charge <br> 0 = New <br> 1 = Cancelled by merchant <br> 2 = Confirmed by merchant <br> 3 = Rejected by network <br> 4 = Aproved by network|
|DateType|1|N|Optional|The type of the date time of comission charge <br> 0 = Creation date <br> 1 = Aproved by network <br> 2 = Rejected by network <br> 3 = Invoice date|
|DateFrom|19|A/N|Optional|From date to filter charges comissions "yyyy/MM/dd hh:mm:ss"|
|DateTo|19|A/N|Optional|To date to filter charges comissions "yyyy/MM/dd hh:mm:ss"|
|InvoiceNumber|50|A/N|Optional|Invoice number to filter charges comissions|

### 10.3 Merchant Charges Comissions Download (POST) – Body Section Format *Response*
|Field Name|Size|Type|Descriptions/Field Value(s)|
|--- |--- |--- |--- |
|IdProcessBillingStatement|36|A/N|Process billing statement UID|
|IdProcessBillingCharge|36|A/N|Process billing charge UID|
|IdMerchant|36|A/N|Merchant UID|
|MerchantCode|50|A/N|Code of the merchant|
|MerchantName|50|A/N|Name of the merchant|
|TypeCode|50|A/N|Invoice code|
|TypeName|50|A/N|Invoice name|
|TypeDescription|50|A/N|Invoice description|
|InvoiceDate|19|A/N|Invoice date time "yyyy/mm/dd|
|InvoiceNumber|50|A/N|Invoice number|
|Description|50|A/N|The charge comission description|
|ElectronicAuthorizationCode|50|A/N|Electronic authorization code|
|ElectronicAuthorizationCodeExpirationDate|19|A/N|Electronic authorization code expiration date "yyyy/mm/dd"|
|IdCurrency|36|A/N|Currency UID|
|CurrencyCode|50|A/N|Currency of the amount fields|
|MerchantCustomField0|50|A/N|Merchant custom field 0|
|MerchantCustomField1|50|A/N|Merchant custom field 1|
|MerchantCustomField2|50|A/N|Merchant custom field 2|
|MerchantCustomField3|50|A/N|Merchant custom field 3|
|ContractCode|20|A/N|Contract identification|
|NetAmount|10|N|Charge amount|
|TotalAmount|10|N|The total amount of the charge|
|TaxExempt|1|N|Tax Exempt <br> 0 = false <br> 1 = true|
|State|1|N|State of the charge <br> 0 = New <br> 1 = Cancelled by Merchant <br> 2 = Confirmed by merchant <br> 3 = Rejected by network <br> 4 = Aproved by network|
|Taxes||A/N|List of taxes applied to the charge|
|CreationDate|19|A/N|Creation date "yyyy/mm/dd|
|CreationRealDate|19|A/N|Creation real date "yyyy/mm/dd|
|UpdateDate|19|A/N|Update date "yyyy/mm/dd|
|AprovedDate|19|A/N|Aproved date "yyyy/mm/dd|
|AprovedRealDate|19|A/N|Aproved real date "yyyy/mm/dd|
|RejectDate|19|A/N|Reject date "yyyy/mm/dd|
|RejectRealDate|19|A/N|Reject real date "yyyy/mm/dd|
|NetworkTimeZone|19|A/N|TimeZone code of the network (abbreviation)|
|FileId|36|A/N|File UID|
|FileEntityId|1|N|File entity id|

### 10.4 Company Movements Download (POST) – Body Section Format *Request*
|Field Name|Size|Type|Condition|Descriptions/Field Value(s)|
|--- |--- |--- |--- |--- |
|SubscriberCode|3|A/N|Required|Fixed. To be assigned by ATIONet|
|ActionCode|3|N|Required|See Action Codes section above|
|CompanyCode|30|A/N|Conditional|See Action Codes section above|
|DateFrom|19|A/N|Required|From date to filter movements "yyyy/MM/dd hh:mm:ss"|
|DateTo|19|A/N|Optional|To date to filter movements "yyyy/MM/dd hh:mm:ss"|
|Types||N|Optional|List of types to filter movements|
|Origins||N|Optional|List of origin to filter movements|

### 10.5 Company Movements Download (POST) – Body Section Format *Response*
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

### 10.6 Company Group Movements Download (POST) – Body Section Format *Request*
|Field Name|Size|Type|Condition|Descriptions/Field Value(s)|
|--- |--- |--- |--- |--- |
|SubscriberCode|3|A/N|Required|Fixed. To be assigned by ATIONet|
|ActionCode|3|N|Required|See Action Codes section above|
|CompanyCode|30|A/N|Conditional|See Action Codes section above|
|CompaniesGroupCode|30|A/N|Optional|Use to filter for company group|
|DateFrom|19|A/N|Required|From date to filter movements "yyyy/MM/dd hh:mm:ss"|
|DateTo|19|A/N|Optional|To date to filter movements "yyyy/MM/dd hh:mm:ss"|
|AmountFrom|10|N|Optional|To filter movements from an amount|
|AmountTo|10|N|Optional|To filter movements up to an amount|
|Types|1|N|Optional|Types to filter movements|
|Origins|1|N|Optional|Origin to filter movements|

### 10.7 Company Group Movements Download (POST) – Body Section Format *Response*
|Field Name|Size|Type|Descriptions/Field Value(s)|
|--- |--- |--- |--- |
|MovementId|36|A/N|Movements’s UID|
|CompaniesGroupId|36|A/N|Company group UID|
|CompaniesGoupName|250|A/N|Company group name|
|HostDateTime|19|A/N|ATIONet’s transaction date time "yyyy/mm/dd hh:mm:ss" (ATIONet Host date time is UCT)|
|SubscriberDateTime|19|A/N|Movement date expressed in subscriber time zone (yyyy/mm/dd hh:mm:ss)|
|Amount|10|N|Amount of the movement|
|Type|1|N|Internal ATIOnet movement type code|
|TypeDescription|50|A/N|Movement type description|
|MovementDescription|50|A/N|Movement description|
|IsDebit|1|N|Indicates that’s a debit or credit movement (1 = "True", 2= "False")|
|Origin|1|N|Internal ATIOnet code for the origin of the movement|
|OriginDescription|50|A/N|Description for the origin of the movement|

### 10.8 Sub-Account/Contract Balance Download (POST) – Body Section Format *Request*
|Field Name|Size|Type|Condition|Descriptions/Field Value(s)|
|--- |--- |--- |--- |--- |
|SubscriberCode|3|A/N|Required|Fixed. To be assigned by ATIONet|
|ActionCode|3|N|Required|See Action Codes section above|
|CompanyCode|50|A/N|Conditional|See Action Codes section above|
|ContractCode|50|A/N|Relative to any other code|See identification section|
|DriverCode|50|A/N|Relative to any other code|See identification section|
|VehicleCode|50|A/N|Relative to any other code|See identification section|
|VehiclePlate|50|A/N|Relative to any other code|See identification section|
|Identifier|50|A/N|Relative to any other code|Public ID of the identification device (chipkey ID, account number on a mag card, RFID serial number, etc) <br> See identification section|
|SubAccountId|36|A/N|Relative to any other code|SubAccount UID|

### 10.9 Sub-Account/Contract Balance Download (POST) – Body Section Format *Response*
|Field Name|Size|Type|Descriptions/Field Value(s)|
|--- |--- |--- |--- |
|SubscriberCode|3|A/N|Fixed. To be assigned by ATIONet|
|CompanyCode|50|A/N|See Action Codes section above|
|CompanyName|50|A/N|Company name|
|ContractCode|50|A/N|See identification section|
|SubContractCode|50|A/N|See identification section|
|SubAccountId|36|A/N|SubAccount UID|
|DriverCode|50|A/N|See identification section|
|VehicleCode|50|A/N|See identification section|
|VehiclePlate|50|A/N|See identification section|
|Identifier|50|A/N|Public ID of the identification device (chipkey ID, account number on a mag card, RFID serial number, etc) <br> See identification section|
|FuelMasterCode|50|A/N|See identification section|
|FuelMasterDescription|50|A/N|Fuel master description|
|CurrencyCode|50|A/N|See identification section|
|Amount|10|N|The balance of the sub-account|

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
|InvoiceNumber|50|A/N|Delivery invoice Number|
|DeliveryNotesData|X|X|Delivery receipt values - see below - see below|
|GPSData|X|X|GPS Values - see below|

### 11.4 Delivery DeliveryNotesData Download – Body Section Format *Response*
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

### 11.5 Delivery GPS Download – Body Section Format *Response*
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

## 12 Company Inserts
The Company Inserts messages are POST actions to create or edit a company, a company contract or both.

To edit a company there's no need to send the contract information. However, when editing a company contract, the information of the company that the contract belongs to is required.

### 12.1 NativeApiRequest

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
				Required
			</th>
			<th align="left">
				Descriptions/Field Value(s)
			</th>
		</tr>
	</thead>
	<tbody>
		<tr valign="top">
			<td>
				<p align="left">SystemModel</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">nvarchar</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">System Model</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SystemVersion</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">nvarchar</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">System Version</p>
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
				<p align="left">nvarchar</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">MessageFormatVersion</p>
			</td>
		</tr>
	</tbody>
</table>

### 12.2 BaseInterfaceRequest

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
				Required
			</th>
			<th align="left">
				Descriptions/Field Value(s)
			</th>
		</tr>
	</thead>
	<tbody>
		<tr valign="top">
			<td>
				<p align="left">ActionCode</p>
			</td>
			<td>
				<p align="left">4</p>
			</td>
			<td>
				<p align="left">nvarchar</p>
			</td>
			<td>
				<p align="left">Yes</p>
			</td>
			<td>
				<p align="left">Action Code</p>
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
				<p align="left">nvarchar</p>
			</td>
			<td>
				<p align="left">Yes</p>
			</td>
			<td>
				<p align="left">Subscriber Code. To be assigned by ATIONet.</p>
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
				<p align="left">nvarchar</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Company Code</p>
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
				<p align="left">nvarchar</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Merchant Code</p>
			</td>
		</tr>
	</tbody>
</table>


### 12.3 InterfaceCompanyRequest

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
				Required
			</th>
			<th align="left">
				Descriptions/Field Value(s)
			</th>
		</tr>
	</thead>
    <tbody>
      <tr valign="top">
         <td>
            <p align="left">TaxPayerId</p>
         </td>
         <td>
            <p align="left">50</p>
         </td>
         <td>
            <p align="left">nvarchar</p>
         </td>
         <td>
            <p align="left">Yes</p>
         </td>
         <td>
            <p align="left">Taxpayer Id</p>
         </td>
      </tr>
      <tr valign="top">
         <td>
            <p align="left">Type</p>
         </td>
         <td>
            <p align="left">-</p>
         </td>
         <td>
            <p align="left">tinyint</p>
         </td>
         <td>
            <p align="left">Yes</p>
         </td>
         <td>
            <p align="left">Company type</p>
         </td>
      </tr>
      <tr valign="top">
         <td>
            <p align="left">Active</p>
         </td>
         <td>
            <p align="left">-</p>
         </td>
         <td>
            <p align="left">bool</p>
         </td>
         <td>
            <p align="left">Yes</p>
         </td>
         <td>
            <p align="left">Indicates if the company can operate</p>
         </td>
      </tr>
      <tr valign="top">
         <td>
            <p align="left">DesactivationType</p>
         </td>
         <td>
            <p align="left">-</p>
         </td>
         <td>
            <p align="left">byte</p>
         </td>
         <td>
            <p align="left">No</p>
         </td>
         <td>
            <p align="left">Company deactivation type<br/>
               0: Cancellation by the client<br/>
               1: Cancellation by the user<br/>
               2: Cancellation by the ERP
            </p>
         </td>
      </tr>
      <tr valign="top">
         <td>
            <p align="left">Code</p>
         </td>
         <td>
            <p align="left">30</p>
         </td>
         <td>
            <p align="left">varchar</p>
         </td>
         <td>
            <p align="left">Yes</p>
         </td>
         <td>
            <p align="left">Company code</p>
         </td>
      </tr>
      <tr valign="top">
         <td>
            <p align="left">Name</p>
         </td>
         <td>
            <p align="left">250</p>
         </td>
         <td>
            <p align="left">nvarchar</p>
         </td>
         <td>
            <p align="left">Yes</p>
         </td>
         <td>
            <p align="left">Company name</p>
         </td>
      </tr>
      <tr valign="top">
         <td>
            <p align="left">IndustryId</p>
         </td>
         <td>
            <p align="left">-</p>
         </td>
         <td>
            <p align="left">Guid</p>
         </td>
         <td>
            <p align="left">Yes</p>
         </td>
         <td>
            <p align="left">Industry type Id. To be assigned by ATIONet.</p>
         </td>
      </tr>
      <tr valign="top">
         <td>
            <p align="left">Plan</p>
         </td>
         <td>
            <p align="left">-</p>
         </td>
         <td>
            <p align="left">byte</p>
         </td>
         <td>
            <p align="left">No</p>
         </td>
         <td>
            <p align="left">Plan to which the company belongs.<br/>
               0: Silver<br/>
               1: Gold<br/>
               2: Platinum
            </p>
         </td>
      </tr>
      <tr valign="top">
         <td>
            <p align="left">Street1</p>
         </td>
         <td>
            <p align="left">200</p>
         </td>
         <td>
            <p align="left">nvarchar</p>
         </td>
         <td>
            <p align="left">Yes</p>
         </td>
         <td>
            <p align="left">Address</p>
         </td>
      </tr>
      <tr valign="top">
         <td>
            <p align="left">Street2</p>
         </td>
         <td>
            <p align="left">200</p>
         </td>
         <td>
            <p align="left">nvarchar</p>
         </td>
         <td>
            <p align="left">No</p>
         </td>
         <td>
            <p align="left">Additional address infromation</p>
         </td>
      </tr>
      <tr valign="top">
         <td>
            <p align="left">ZipCode</p>
         </td>
         <td>
            <p align="left">50</p>
         </td>
         <td>
            <p align="left">nvarchar</p>
         </td>
         <td>
            <p align="left">No</p>
         </td>
         <td>
            <p align="left">ZIP code</p>
         </td>
      </tr>
      <tr valign="top">
         <td>
            <p align="left">City</p>
         </td>
         <td>
            <p align="left">100</p>
         </td>
         <td>
            <p align="left">nvarchar</p>
         </td>
         <td>
            <p align="left">Yes</p>
         </td>
         <td>
            <p align="left">City</p>
         </td>
      </tr>
      <tr valign="top">
         <td>
            <p align="left">CountryId</p>
         </td>
         <td>
            <p align="left">-</p>
         </td>
         <td>
            <p align="left">Guid</p>
         </td>
         <td>
            <p align="left">Yes</p>
         </td>
         <td>
            <p align="left">Country Id. To be assigned by ATIONet.</p>
         </td>
      </tr>
      <tr valign="top">
         <td>
            <p align="left">StateId</p>
         </td>
         <td>
            <p align="left">-</p>
         </td>
         <td>
            <p align="left">Guid</p>
         </td>
         <td>
            <p align="left">Yes</p>
         </td>
         <td>
            <p align="left">State/Province Id. To be assigned by ATIONet.</p>
         </td>
      </tr>
      <tr valign="top">
         <td>
            <p align="left">Street1Delivery</p>
         </td>
         <td>
            <p align="left">200</p>
         </td>
         <td>
            <p align="left">nvarchar</p>
         </td>
         <td>
            <p align="left">Yes</p>
         </td>
         <td>
            <p align="left">Delivery address</p>
         </td>
      </tr>
      <tr valign="top">
         <td>
            <p align="left">Street2Delivery</p>
         </td>
         <td>
            <p align="left">200</p>
         </td>
         <td>
            <p align="left">nvarchar</p>
         </td>
         <td>
            <p align="left">No</p>
         </td>
         <td>
            <p align="left">Additional delivery address infromation</p>
         </td>
      </tr>
      <tr valign="top">
         <td>
            <p align="left">ZipCodeDelivery</p>
         </td>
         <td>
            <p align="left">50</p>
         </td>
         <td>
            <p align="left">nvarchar</p>
         </td>
         <td>
            <p align="left">No</p>
         </td>
         <td>
            <p align="left">Delivery ZIP code</p>
         </td>
      </tr>
      <tr valign="top">
         <td>
            <p align="left">CityDelivery</p>
         </td>
         <td>
            <p align="left">100</p>
         </td>
         <td>
            <p align="left">nvarchar</p>
         </td>
         <td>
            <p align="left">Yes</p>
         </td>
         <td>
            <p align="left">Delivery city</p>
         </td>
      </tr>
      <tr valign="top">
         <td>
            <p align="left">CountryDeliveryId</p>
         </td>
         <td>
            <p align="left">-</p>
         </td>
         <td>
            <p align="left">Guid</p>
         </td>
         <td>
            <p align="left">Yes</p>
         </td>
         <td>
            <p align="left">Delivery country Id. To be assigned by ATIONet.</p>
         </td>
      </tr>
      <tr valign="top">
         <td>
            <p align="left">StateDeliveryId</p>
         </td>
         <td>
            <p align="left">-</p>
         </td>
         <td>
            <p align="left">Guid</p>
         </td>
         <td>
            <p align="left">Yes</p>
         </td>
         <td>
            <p align="left">Delivery state/province Id. To be assigned by ATIONet.</p>
         </td>
      </tr>
      <tr valign="top">
         <td>
            <p align="left">TaxPayerCategoryId</p>
         </td>
         <td>
            <p align="left">-</p>
         </td>
         <td>
            <p align="left">Guid</p>
         </td>
         <td>
            <p align="left">No</p>
         </td>
         <td>
            <p align="left">Taxpayer Category Id. To be assigned by ATIONet.</p>
         </td>
      </tr>
      <tr valign="top">
         <td>
            <p align="left">ContactName</p>
         </td>
         <td>
            <p align="left">250</p>
         </td>
         <td>
            <p align="left">nvarchar</p>
         </td>
         <td>
            <p align="left">Yes</p>
         </td>
         <td>
            <p align="left">Contact name</p>
         </td>
      </tr>
      <tr valign="top">
         <td>
            <p align="left">ContactEmail</p>
         </td>
         <td>
            <p align="left">50</p>
         </td>
         <td>
            <p align="left">nvarchar</p>
         </td>
         <td>
            <p align="left">Yes</p>
         </td>
         <td>
            <p align="left">Contact E-mail<br/>
               Used for creating the admin user and it is where the access credentials will be sent during the company creation.
            </p>
         </td>
      </tr>
      <tr valign="top">
         <td>
            <p align="left">Phone1</p>
         </td>
         <td>
            <p align="left">50</p>
         </td>
         <td>
            <p align="left">nvarchar</p>
         </td>
         <td>
            <p align="left">Yes</p>
         </td>
         <td>
            <p align="left">Contact main phone number</p>
         </td>
      </tr>
      <tr valign="top">
         <td>
            <p align="left">Phone2</p>
         </td>
         <td>
            <p align="left">50</p>
         </td>
         <td>
            <p align="left">nvarchar</p>
         </td>
         <td>
            <p align="left">No</p>
         </td>
         <td>
            <p align="left">Contact secondary phone number</p>
         </td>
      </tr>
      <tr valign="top">
         <td>
            <p align="left">Custom0</p>
         </td>
         <td>
            <p align="left">200</p>
         </td>
         <td>
            <p align="left">nvarchar</p>
         </td>
         <td>
            <p align="left">No</p>
         </td>
         <td>
            <p align="left">Custom field number 1 value</p>
         </td>
      </tr>
      <tr valign="top">
         <td>
            <p align="left">Custom1</p>
         </td>
         <td>
            <p align="left">200</p>
         </td>
         <td>
            <p align="left">nvarchar</p>
         </td>
         <td>
            <p align="left">No</p>
         </td>
         <td>
            <p align="left">Custom field number 2 value</p>
         </td>
      </tr>
      <tr valign="top">
         <td>
            <p align="left">Custom2</p>
         </td>
         <td>
            <p align="left">200</p>
         </td>
         <td>
            <p align="left">nvarchar</p>
         </td>
         <td>
            <p align="left">No</p>
         </td>
         <td>
            <p align="left">Custom field number 3 value</p>
         </td>
      </tr>
      <tr valign="top">
         <td>
            <p align="left">Custom3</p>
         </td>
         <td>
            <p align="left">200</p>
         </td>
         <td>
            <p align="left">nvarchar</p>
         </td>
         <td>
            <p align="left">No</p>
         </td>
         <td>
            <p align="left">Custom field number 4 value</p>
         </td>
      </tr>
      <tr valign="top">
         <td>
            <p align="left">CompanyGroupId</p>
         </td>
         <td>
            <p align="left">-</p>
         </td>
         <td>
            <p align="left">Guid</p>
         </td>
         <td>
            <p align="left">No</p>
         </td>
         <td>
            <p align="left">Company Group Id.<br/>Relevant only if the company belongs to a group.
            </p>
         </td>
      </tr>
      <tr valign="top">
         <td>
            <p align="left">PermissionsType</p>
         </td>
         <td>
            <p align="left">-</p>
         </td>
         <td>
            <p align="left">smallint</p>
         </td>
         <td>
            <p align="left">No</p>
         </td>
         <td>
            <p align="left">Data edition permissions type.<br/>Used for locking the company's data edition through the ATIONet portal.<br/>
               1: Data edition unlocked.<br/>
               2: Data edition permitted only through the API.
            </p>
         </td>
      </tr>
      <tr valign="top">
         <td>
            <p align="left">Contracts</p>
         </td>
         <td>
            <p align="left">-</p>
         </td>
         <td>
            <p align="left">
               List
               <InterfaceCompanyContract>
            </p>
         </td>
         <td>
            <p align="left">No</p>
         </td>
         <td>
            <p align="left">Company contracts list</p>
         </td>
      </tr>
    </tbody>
</table>

### 12.4 InterfaceCompanyContract

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
				Required
			</th>
			<th align="left">
				Descriptions/Field Value(s)
			</th>
		</tr>
	</thead>
    <tbody>		
		<tr valign="top">
			<td>
				<p align="left">Id</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">Guid</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Contract Id.<br/>Used for updating contracts.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Active</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">bool</p>
			</td>
			<td>
				<p align="left">Yes</p>
			</td>
			<td>
				<p align="left">Indicates if the contract is able to operate</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ReactivationAmount</p>
			</td>
			<td>
				<p align="left">28</p>
			</td>
			<td>
				<p align="left">decimal</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Reactivation amount.<br/>
								When money is credited to the contract, if that amount is greater than or equal to this reference value, the contract will be reactivated if it wasn't active</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">DesactivationType</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">byte</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Contract deactivation type<br/>
								0: Cancellation by the client<br/>
								1: Cancellation by the user<br/>
								2: Cancellation by the ERP</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Code</p>
			</td>
			<td>
				<p align="left">20</p>
			</td>
			<td>
				<p align="left">nvarchar</p>
			</td>
			<td>
				<p align="left">Yes</p>
			</td>
			<td>
				<p align="left">Contract code</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Description</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">nvarchar</p>
			</td>
			<td>
				<p align="left">Yes</p>
			</td>
			<td>
				<p align="left">Contract description</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">StartDate</p>
			</td>
			<td>
				<p align="left">10</p>
			</td>
			<td>
				<p align="left">nvarchar</p>
			</td>
			<td>
				<p align="left">Yes</p>
			</td>
			<td>
				<p align="left">Initial operations date.<br/>
								yyyy/MM/dd format</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Duration</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">short</p>
			</td>
			<td>
				<p align="left">Yes</p>
			</td>
			<td>
				<p align="left">Contract length.<br/>
					Represents an amount of days, weeks, months or years</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Periodicity</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">byte</p>
			</td>
			<td>
				<p align="left">Yes</p>
			</td>
			<td>
				<p align="left">Contract length periodicity<br/>
								0: Days<br/>
								1: Weeks<br/>
								2: Months<br/>
								3: Years</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CurrentAccountMode</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">byte</p>
			</td>
			<td>
				<p align="left">Yes</p>
			</td>
			<td>
				<p align="left">Current acount mode<br/>
								0: Product<br/>
								1: Money</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CurrencyId</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">Guid</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Currency Id.<br/>
								To be assigned by ATIONet.<br/>
								If the selected CurrentAccountMode is ""Money"", either this value or the currency code value must be sent.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CurrenyCode</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">nvarchar</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Currency code.<br/>
								To be assigned by ATIONet.<br/>
								If the selected CurrentAccountMode is ""Money"", either this value or the currency Id value must be sent.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Mode</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">byte</p>
			</td>
			<td>
				<p align="left">Yes</p>
			</td>
			<td>
				<p align="left">Contract mode<br/>
								0: Credit<br/>
								1: Debit<br/>
								2: Cash</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CreditLimit</p>
			</td>
			<td>
				<p align="left">18</p>
			</td>
			<td>
				<p align="left">numeric</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Credit limit.<br/>
								Only relevant if the selected ContractMode is "Credit".</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">BalanceMode</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">byte</p>
			</td>
			<td>
				<p align="left">Yes</p>
			</td>
			<td>
				<p align="left">Balance mode.<br/>
								1: Disperse<br/>
								2: Not Disperse<br/>
								4: Autofill</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ValidateSites</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">bool</p>
			</td>
			<td>
				<p align="left">Yes</p>
			</td>
			<td>
				<p align="left">Indicates if the contract must validate sites</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ValidateFuels</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">bool</p>
			</td>
			<td>
				<p align="left">Yes</p>
			</td>
			<td>
				<p align="left">Indicates if the contract must validate fuels</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">IdRackPricesList</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">Guid</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Rack prices list Id.<br/>
								This value should only be sent if the contract will operate with a rack prices list. If the current account mode is set as ""Money"" both the contract currency and the rack prices list currency must be the same.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">RackPricesListCode</p>
			</td>
			<td>
				<p align="left">20</p>
			</td>
			<td>
				<p align="left">nvarchar</p>
			</td>
			<td>
				<p align="left">Yes</p>
			</td>
			<td>
				<p align="left">Like IdRackPricesList, this value it's used to identify the RackPricesList. If IdRackPricesList and RackPricesListCode are present, IdRackPricesList take priority.</p>
			</td>
		</tr>
	        <tr valign="top">
			<td>
				<p align="left">ValidatePrograms</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">bool</p>
			</td>
			<td>
				<p align="left">Yes</p>
			</td>
			<td>
				<p align="left">Indicates if the contract must validate programs</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Type</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">tinyint</p>
			</td>
			<td>
				<p align="left">Yes</p>
			</td>
			<td>
				<p align="left">Contract type.<br/>
								0: Fleet<br/>
								1: Gift Card (legacy version)<br/>
								2: Consumer Card<br/>
								3: Gift Card</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Subsidized</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">bool</p>
			</td>
			<td>
				<p align="left">Yes</p>
			</td>
			<td>
				<p align="left">Indicates if the contract handles subsidized amounts</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Classification1Id</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">Guid</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Contract classification 1 configured Id.<br/>
								To add this classification to the contract, either the classification Id or the classification code should be sent, but not both.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Classification1Code</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">nvarchar</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Contract classification 1 configured code.<br/>
								To add this classification to the contract, either the classification Id or the classification code should be sent, but not both.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Classification2Id</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">Guid</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Contract classification 2 configured Id.<br/>
								To add this classification to the contract, either the classification Id or the classification code should be sent, but not both.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Classification2Code</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">nvarchar</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Contract classification 2 configured code.<br/>
								To add this classification to the contract, either the classification Id or the classification code should be sent, but not both.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Classification3Id</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">Guid</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Contract classification 3 configured Id.<br/>
								To add this classification to the contract, either the classification Id or the classification code should be sent, but not both.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Classification3Code</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">nvarchar</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Contract classification 3 configured code.<br/>
								To add this classification to the contract, either the classification Id or the classification code should be sent, but not both.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Classification4Id</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">Guid</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Contract classification 4 configured Id.<br/>
								To add this classification to the contract, either the classification Id or the classification code should be sent, but not both.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Classification4Code</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">nvarchar</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Contract classification 4 configured code.<br/>
								To add this classification to the contract, either the classification Id or the classification code should be sent, but not both.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Custom0</p>
			</td>
			<td>
				<p align="left">200</p>
			</td>
			<td>
				<p align="left">nvarchar</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Custom text field used for identifying a required contract value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Custom1</p>
			</td>
			<td>
				<p align="left">200</p>
			</td>
			<td>
				<p align="left">nvarchar</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Custom text field used for identifying a required contract value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Custom2</p>
			</td>
			<td>
				<p align="left">200</p>
			</td>
			<td>
				<p align="left">nvarchar</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Custom text field used for identifying a required contract value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Custom3</p>
			</td>
			<td>
				<p align="left">200</p>
			</td>
			<td>
				<p align="left">nvarchar</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Custom text field used for identifying a required contract value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CustomInterface0</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">bool</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Custom parameter configured by the network to be used in the interface operations.<br/>
								Only relevant for ERPs interfaces integrations.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CustomInterface1</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">bool</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Custom parameter configured by the network to be used in the interface operations.<br/>
								Only relevant for ERPs interfaces integrations.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CustomInterface2</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">bool</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Custom parameter configured by the network to be used in the interface operations.<br/>
								Only relevant for ERPs interfaces integrations.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CustomInterface3</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">bool</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Custom parameter configured by the network to be used in the interface operations.<br/>
								Only relevant for ERPs interfaces integrations.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CustomInterface4</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">bool</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Custom parameter configured by the network to be used in the interface operations.<br/>
								Only relevant for ERPs interfaces integrations.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CustomOperation0</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">bool</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Custom parameter configured by the network to be used in external operations.<br/>
								Only relevant for ERPs interfaces integrations.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CustomOperation1</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">bool</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Custom parameter configured by the network to be used in external operations.<br/>
								Only relevant for ERPs interfaces integrations.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CustomOperation2</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">bool</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Custom parameter configured by the network to be used in external operations.<br/>
								Only relevant for ERPs interfaces integrations.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CustomOperation3</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">bool</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Custom parameter configured by the network to be used in external operations.<br/>
								Only relevant for ERPs interfaces integrations.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CustomOperation4</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">bool</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Custom parameter configured by the network to be used in external operations.<br/>
								Only relevant for ERPs interfaces integrations.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">PermissionsType</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">smallint</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Data edition permissions type.<br/>
								Used for locking the contract's data edition through the ATIONet portal.<br/>
								1: Data edition unlocked.<br/>
								2: Data edition permitted only through the API.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">BillingActive</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">bool</p>
			</td>
			<td>
				<p align="left">Yes</p>
			</td>
			<td>
				<p align="left">Indicates if the contract movements will be billed, activating the billing process.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">BillingDueDays</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">short</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Billing due days.<br/>
								Relevant only if the billing process is activated.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">BillingPeriodicity</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">Byte</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Billing periodicity.<br/>
								Relevant only if the billing process is activated.<br/>
								0: Days<br/>
								1: Weeks<br/>
								2: Months<br/>
								3: Years</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">BillingPeriodicityValue</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">short</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Billing Periodicity Value.<br/>
								Relevant only if the billing process is activated.
								Represents the amount of days, weeks, months or years.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">BillingManual</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">bool</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Indicates if the billing process will be runned manually instead of automatically.<br/>
								Relevant only if the billing process is activated.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">BillingCutTime</p>
			</td>
			<td>
				<p align="left">5</p>
			</td>
			<td>
				<p align="left">varchar</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Billing Cut Time.<br/>
								Relevant only if the billing process is activated.
								Must be established if the billing periodicity is set to ""Days"", using HH:mm format.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">BillingCutDay</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">byte</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Billing Cut Day.<br/>
								Relevant only if the billing process is activated.
								Must be established with a value from 0 to 7 if the billing periodicity is set to ""Weeks"", or from 1 to 31 if the billing periodicity is set to ""Months"" or ""Years"".</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">BillingCutMonth</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">byte</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Billing Cut Month.<br/>
								Relevant only if the billing process is activated.
								Must be established with a value from 1 to 12 if the billing periodicity is set to ""Years"".</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">DocumentChargesFromBalance</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">bool</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Indicates if the charges are deducted from the account balance</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SeparateChargesDocument</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">bool</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Indicates if the charges are reflected in a separate document</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">RecepientEmails</p>
			</td>
			<td>
				<p align="left">max</p>
			</td>
			<td>
				<p align="left">nvarchar</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">The E-mail addresses to where the statements generated by the billing process will be sent.<br/>
								Relevant only if the billing process is activated.
								Multiple emails addresses can be sent separated by a semicolon "";""</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">BillingTaxPayerId</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">nvarchar</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Taxpayer Id that will appear on the statement</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">BillingCompanyName</p>
			</td>
			<td>
				<p align="left">250</p>
			</td>
			<td>
				<p align="left">nvarchar</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Company name that will appear on the statement</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">BillingCompanyStreet1</p>
			</td>
			<td>
				<p align="left">200</p>
			</td>
			<td>
				<p align="left">nvarchar</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Company address that will appear on the statement</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">BillingCompanyStreet2</p>
			</td>
			<td>
				<p align="left">200</p>
			</td>
			<td>
				<p align="left">nvarchar</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Additional company address information that will appear on the statement</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">BillingCompanyZipCode</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">nvarchar</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">ZIP code that will appear on the statement</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">BillingCompanyCity</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">nvarchar</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">City name that will appear on the statement</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">BillingCompanyCountryId</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">Guid</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Country name that will appear on the statement</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">BillingCompanyStateId</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">Guid</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">State/province name that will appear on the statement</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Fuels</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">List<InterfaceFuelContract>
				</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Fuels list available to the contract.<br/>
				If no list is sent, all the fuels will be available for the contract.<br/>The FuelMasterID/FuelMasterCode corresponds always to FuelMaster reference.<br/>The request accepts that only one of the fields that identify the fuel (FuelMasterID/FuelMasterCode) is present. If both are present, the FuelMasterID field will take priority.<br/><br/>
				"Fuels": [<br/>{<br/>"FuelMasterID": "389dee96-c6af-4161-8e3a-fa7835994102",<br/>"FuelMasterCode": "002",<br/>"VolumeLimit": 0.00,				  <br/>"MoneyLimit": 0.00<br/>}<br/></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Sites</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">List<InterfaceSiteContract>
				</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Sites list where the contract sub accounts can operate.<br/>
				If no list is sent, the sub accounts will be allowed to operate in all the sites.The request accepts that only one of the fields that identify the site (SiteId/Code) is present. If both are present, the SiteId field will take priority.<br/><br/><b>Fuels</b><br/>If 'require fuel mapping' is enabled on the site, the FuelMasterID/FuelMasterCode sent corresponds to a Fuel, otherwise the values corresponds to a Fuel Master.<br/>The request accepts that only one of the fields that identify the fuel (FuelMasterID/FuelMasterCode) is present. If both are present, the FuelMasterID field will take priority.<br/><br/>"Sites": [<br/>{<br/>"SiteId":"16431f38-c140-41be-8235-b6fdfed5739d",<br/>"Code":"ABC",<br/>"Fuels":[<br/>{<br/>"FuelMasterId": "389dee96-c6af-4161-8e3a-fa7835994102",<br/>"FuelMasterCode": "002",<br/>"VolumeLimit": 0.00,<br/>"MoneyLimit": 0.00<br/>}<br/>]<br/>}<br/>]<br/></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Prices</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">List<InterfacePriceContract>
				</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Price list that will be applied to the contract.<br/>
								If no list is sent, the contract will operate with the controller prices.
					It is possible to set prices for specific sites and dates.<br/>The request accepts that only one of the fields that identify the site (SiteId/Code) is present. If both are present, the SiteId field will take priority.<br/><br/><b>Fuels</b><br/>If site is sent on the price and has 'require fuel mapping' enabled, the FuelMasterID/FuelMasterCode sent corresponds to a Fuel, otherwise the values corresponds to a Fuel Master.<br/>The request accepts that only one of the fields that identify the fuel (FuelMasterID/FuelMasterCode) is present. If both are present, the FuelMasterID field will take priority.
<br/><br/>"Prices": [<br/>{<br/>"FuelMasterId": "577a92fa-cbb3-43d1-bb31-d54d8ff4a74a",<br/>"FuelMasterCode":"BCA",<br/>"Value": 5,<br/>"SiteId":"16431f38-c140-41be-8235-b6fdfed5739d",<br/>"SiteCode":"ABC",<br/>"DateFrom":"2022/04/07",<br/>"DateTo":"2023/04/01",<br/>"TimeFrom":"00:00",<br/>"TimeTo":"23:59"<br/>}<br/>]</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Modifiers</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">List<InterfaceModifierContract>
				</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Modifiers list that will be applied to the contract (discounts/markups)<br/>The request accepts that only one of the fields that identify the site (SiteId/Code) is present. If both are present, the SiteId field will take priority.<br/><br/><b>Fuels</b><br/>If site is sent on the modifier and has 'require fuel mapping' enabled, the FuelMasterID/FuelMasterCode sent corresponds to a Fuel, otherwise the values corresponds to a Fuel Master.<br/>The request accepts that only one of the fields that identify the fuel (FuelMasterID/FuelMasterCode) is present. If both are present, the FuelMasterID field will take priority.<br/><br/>
"Modifiers": [<br/>{<br/>"Class": 0,<br/>"Type":1,<br/>"Value":0.15,<br/>"FuelMasterId": "577a92fa-cbb3-43d1-bb31-d54d8ff4a74a",<br/>"SiteId": "16431f38-c140-41be-8235-b6fdfed5739d",<br/>"SiteCode": "ABC",<br/>"DateFrom":"2022/04/07",<br/>"TimeFrom":"2023/04/01",<br/>"DateTo":"00:00",<br/>"TimeTo":"23:59"<br/>}<br/>]</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Concepts</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">List<InterfaceConceptContract>
				</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Concepts list. Used to links concepts with the contract<br/>
"Concepts": [<br/>{<br/>"ConceptId":"ca0adaf6-3325-4886-ae2d-eb9d187e6c7b",<br/>"Quantity": 12,<br/>"BillingEvent":0,<br/>"BillingEventPeriodicity":1,<br/>"BillingEventDuration":2,<br/>"BillingEventCutTime":2,<br/>"BillingEventCutDay":7,<br/>"BillingEventCutMonth":1,<br/>"Application":0,<br/>"ApplicationThreshold":0,<br/>"ApplicationCeiling":0,<br/>"IdentificationType":0,<br/>"Enabled":true,<br/>"RollUp":true<br/>}<br/>]<br/></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Blocks</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">List<InterfaceBlockContract>
				</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Blocks list.<br/>
								If no list is sent, no blocks will be applied to the contract. Contract blocks can be applied continuously or intermittently by dates.<br/>
"Blocks": [<br/>{<br/>"Type": 0,<br/>"DateFrom": "2022/04/07",<br/>"DateTo": "2023/04/01",<br/>"DayFrom": 7,<br/>"DayTo": 1<br/>}<br/></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">OverLimits</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">List<InterfaceOverLimitContract>
				</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Overlimits list.<br/>
								Used for establishing overlimits. If not list is sent, no overlimits will be applied.<br/>
				"OverLimits": [<br/>{<br/>"Type": 1,<br/>"Value": 0.00,<br/>"DateFrom": "2022/04/07",<br/>"DateTo": "2023/04/07"<br/>}<br/>
				</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Programs</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">List<Guid>
				</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left"> Used for establishing which programs can be used with the contract.<br/>
						 It's composed by Id and Code. Only one of the values is needed to identify the program. If both values are present, the Id field take the priority.<br/> "Programs":[<br/>{<br/>"Id": "06df1b02-4de2-40d3-ba2f-af03f622c73d"<br/>}<br/> Or<br/>"Programs":[<br/>{<br/>"Code": "PRG001"<br/>}</p>
			</td>
		</tr>
    </tbody>
</table>

### 12.5 InterfaceFuelContract

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
				Required
			</th>
			<th align="left">
				Descriptions/Field Value(s)
			</th>
		</tr>
	</thead>
    <tbody>
		<tr valign="top">
			<td>
				<p align="left">FuelMasterId</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">Guid</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Mandatory if no fuel master code is sent.</p>
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
				<p align="left">nvarchar</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Mandatory if no fuel master id is sent.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">VolumeLimit</p>
			</td>
			<td>
				<p align="left">18</p>
			</td>
			<td>
				<p align="left">numeric</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Used for establishing a consumption limit to the contract.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">MoneyLimit</p>
			</td>
			<td>
				<p align="left">18</p>
			</td>
			<td>
				<p align="left">numeric</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Used for establishing a consumption limit to the contract.</p>
			</td>
		</tr>
    </tbody>
</table>

### 12.6 InterfaceSiteContract

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
				Required
			</th>
			<th align="left">
				Descriptions/Field Value(s)
			</th>
		</tr>
	</thead>
    <tbody>
			<tr valign="top">
			<td>
				<p align="left">SiteId</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">Guid</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">"Site Id.<br/>
								Required if no site code is sent."	</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Code</p>
			</td>
			<td>
				<p align="left">50</p>
			</td>
			<td>
				<p align="left">Nvarchar(50)</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Site code.<br/>
								Required if no site Id is sent.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Fuels</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">List<InterfaceFuelContractRequest></p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Fuels list.<br/>
								If is it sent, only the fuel master codes or Ids should be sent. If no list is setn, only the site will be identified.</p>
			</td>
		</tr>
    </tbody>
</table>

### 12.7 InterfacePriceContract

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
				Required
			</th>
			<th align="left">
				Descriptions/Field Value(s)
			</th>
		</tr>
	</thead>	
	<tbody>		
		<tr valign="top">
			<td>
				<p align="left">FuelMasterId</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">Guid</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Required if no fuel master code is sent.</p>
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
				<p align="left">nvarchar</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Required if no fuel master id is sent.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Value</p>
			</td>
			<td>
				<p align="left">18</p>
			</td>
			<td>
				<p align="left">numeric</p>
			</td>
			<td>
				<p align="left">Yes</p>
			</td>
			<td>
				<p align="left">
				</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteId</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">Guid</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Required if the price should be applied to a specific site.</p>
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
				<p align="left">nvarchar</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Required if the price should be applied to a specific site.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">DateFrom</p>
			</td>
			<td>
				<p align="left">10</p>
			</td>
			<td>
				<p align="left">nvarchar</p>
			</td>
			<td>
				<p align="left">Yes</p>
			</td>
			<td>
				<p align="left">yyyy/MM/dd format</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">TimeFrom</p>
			</td>
			<td>
				<p align="left">5</p>
			</td>
			<td>
				<p align="left">nvarchar</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Relevant only if a time from is defined. HH:mm format.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">DateTo</p>
			</td>
			<td>
				<p align="left">10</p>
			</td>
			<td>
				<p align="left">nvarchar</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">yyyy/MM/dd format.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">TimeTo</p>
			</td>
			<td>
				<p align="left">5</p>
			</td>
			<td>
				<p align="left">nvarchar</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Relevant only if a time to is defined. HH:mm format.</p>
			</td>
		</tr>
	</tbody>
</table>

### 12.8 InterfaceModifierContract

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
				Required
			</th>
			<th align="left">
				Descriptions/Field Value(s)
			</th>
		</tr>
	</thead>
	<tbody>			
		<tr valign="top">
			<td>
				<p align="left">Description</p>
			</td>
			<td>
				<p align="left">30</p>
			</td>
			<td>
				<p align="left">nvarchar</p>
			</td>
			<td>
				<p align="left">Yes</p>
			</td>
			<td>
				<p align="left">Modifier description.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Class</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">byte</p>
			</td>
			<td>
				<p align="left">Yes</p>
			</td>
			<td>
				<p align="left">Modifier class.<br/>
								0: Discount<br/>
								1: Increase</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Type</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">byte</p>
			</td>
			<td>
				<p align="left">Yes</p>
			</td>
			<td>
				<p align="left">Tipo de modificador.<br/>
								0: Percentual<br/>
								1: Fixed per transaction<br/>
								2: Fixed per unit</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Value</p>
			</td>
			<td>
				<p align="left">18</p>
			</td>
			<td>
				<p align="left">numeric</p>
			</td>
			<td>
				<p align="left">Yes</p>
			</td>
			<td>
				<p align="left">Modifier value.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">FuelMasterId</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">Guid</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Fuel master Id.<br/>
								Required if a modifier should be applied to a fuel's price and the associated fuel master code wasn't sent.</p>
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
				<p align="left">nvarchar</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Fuel master code.<br/>
								Required if a modifier should be applied to a fuel's price and the associated fuel master Id wasn't sent.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SiteId</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">Guid</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Site Id.<br/>
								Required if a modifier should be applied to a site and the associated site code wasn't sent.</p>
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
				<p align="left">nvarchar</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Site code.<br/>
								Required if a modifier should be applied to a site and the associated site Id wasn't sent.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">DateFrom</p>
			</td>
			<td>
				<p align="left">10</p>
			</td>
			<td>
				<p align="left">nvarchar</p>
			</td>
			<td>
				<p align="left">Yes</p>
			</td>
			<td>
				<p align="left">Date from which the modifier will be applied.
								yyyy/MM/dd format.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">TimeFrom</p>
			</td>
			<td>
				<p align="left">5</p>
			</td>
			<td>
				<p align="left">nvarchar</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Time from which the modifier will be applied.<br/>
								Relevant only if a dete from is defined. HH:mm format.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">DateTo</p>
			</td>
			<td>
				<p align="left">10</p>
			</td>
			<td>
				<p align="left">nvarchar</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Date until the modifier will be applied.<br/>
								yyyy/MM/dd format.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">TimeTo</p>
			</td>
			<td>
				<p align="left">5</p>
			</td>
			<td>
				<p align="left">nvarchar</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Time until the modifier will be applied.<br/>
								Relevant only if a dete to is defined. HH:mm format.</p>
			</td>
		</tr>
	</tbody>
</table>

### 12.9 InterfaceConceptContract

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
				Required
			</th>
			<th align="left">
				Descriptions/Field Value(s)
			</th>
		</tr>
	</thead>
	<tbody>			
		<tr valign="top">
			<td>
				<p align="left">ConceptId</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">Guid</p>
			</td>
			<td>
				<p align="left">Yes</p>
			</td>
			<td>
				<p align="left">Concept Id</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Quantity</p>
			</td>
			<td>
				<p align="left">18</p>
			</td>
			<td>
				<p align="left">Numeric</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Applied concept amount.<br/>
								Depends on the concept type selected.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">BillingEvent</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">smallint</p>
			</td>
			<td>
				<p align="left">Yes</p>
			</td>
			<td>
				<p align="left">Billing event.<br/>
								0: Contract period<br/>
								1: Next billing process run<br/>
								2: Summary period</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">BillingEventPeriodicity</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">tinyint</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Billing event periodicity.<br/>
								Depends on that the selected billing event is "Summary period" (2).<br/>
								0: Daily<br/>
								1: Weekly<br/>
								2: Monthly<br/>
								3: Yearly</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">BillingEventDuration</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">smallint</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Value of the selected periodicity.<br/>
								Depends on that the selected billing event is "Summary period" (2).</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">BillingEventCutTime</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">smallint</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Limit time of the billing event.<br/>
								Depends on that the selected billing event is "Summary period" (2). 'HHmm' format.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">BillingEventCutDay</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">tinyint</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Limit date.<br/>
								Depends on that the selected billing event is "Summary period" (2) and on that the selected periodicity is "Weekly" (1), "Monthly" (2) or "Yearly" (3).<br/>
								If "Weekly" is selected, the value must be between 0 and 7 reflecting the day of the week; if  "Monthly" or "Yearly" is selected, the value must be between 1 and 31 reflecting the day of the month.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">BillingEventCutMonth</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">tinyint</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Limit month.<br/>
								Depends on that the selected billing event is "Summary period" (2) and on that the selected periodicity is "Yearly" (3). Admits values between 1 y 12.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Application</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">smallint</p>
			</td>
			<td>
				<p align="left">Yes</p>
			</td>
			<td>
				<p align="left">Application type.<br/>
								To be assigned by ATIONet.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ApplicationThreshold</p>
			</td>
			<td>
				<p align="left">18</p>
			</td>
			<td>
				<p align="left">Numeric</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Application threshold.<br/>
								Depends on the application type.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ApplicationCeiling</p>
			</td>
			<td>
				<p align="left">18</p>
			</td>
			<td>
				<p align="left">Numeric</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Application ceiling.<br/>
								Depends on the application type.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">IdentificationType</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">smallint</p>
			</td>
			<td>
				<p align="left">No</p>
			</td>
			<td>
				<p align="left">Identification type.<br/>
								Depends on the application type.</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">Enabled</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">bool</p>
			</td>
			<td>
				<p align="left">Yes</p>
			</td>
			<td>
				<p align="left">
				</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">RollUp</p>
			</td>
			<td>
				<p align="left">-</p>
			</td>
			<td>
				<p align="left">bool</p>
			</td>
			<td>
				<p align="left">Yes</p>
			</td>
			<td>
				<p align="left">
				</p>
			</td>
		</tr>
	</tbody>
</table>

### 12.10 InterfaceBlockContract

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
            Required
         </th>
         <th align="left">
            Descriptions/Field Value(s)
         </th>
      </tr>
    </thead>
    <tbody>
      <tr valign="top">
         <td>
            <p align="left">Type</p>
         </td>
         <td>
            <p align="left">-</p>
         </td>
         <td>
            <p align="left">byte</p>
         </td>
         <td>
            <p align="left">Yes</p>
         </td>
         <td>
            <p align="left">Contract block type.<br/>
               0: Fixed<br/>
               1: Recurrent
            </p>
         </td>
      </tr>
      <tr valign="top">
         <td>
            <p align="left">DateFrom</p>
         </td>
         <td>
            <p align="left">10</p>
         </td>
         <td>
            <p align="left">nvarchar</p>
         </td>
         <td>
            <p align="left">No</p>
         </td>
         <td>
            <p align="left">Contract block starting date.<br/>
               Required if the selected contract block type is "Fixed". yyyy/MM/dd format.
            </p>
         </td>
      </tr>
      <tr valign="top">
         <td>
            <p align="left">DateTo</p>
         </td>
         <td>
            <p align="left">10</p>
         </td>
         <td>
            <p align="left">nvarchar</p>
         </td>
         <td>
            <p align="left">No</p>
         </td>
         <td>
            <p align="left">Contract block finishing date.<br/>
               Required if the selected contract block type is "Fixed". yyyy/MM/dd format.
            </p>
         </td>
      </tr>
      <tr valign="top">
         <td>
            <p align="left">DayFrom</p>
         </td>
         <td>
            <p align="left">-</p>
         </td>
         <td>
            <p align="left">int</p>
         </td>
         <td>
            <p align="left">No</p>
         </td>
         <td>
            <p align="left">Contract block starting day of the month.<br/>
               Required if the selected contract block type is "Recurrent".
            </p>
         </td>
      </tr>
      <tr valign="top">
         <td>
            <p align="left">DayTo</p>
         </td>
         <td>
            <p align="left">-</p>
         </td>
         <td>
            <p align="left">int</p>
         </td>
         <td>
            <p align="left">No</p>
         </td>
         <td>
            <p align="left">Contract block finishing day of the month.<br/>
               Required if the selected contract block type is "Recurrent".
            </p>
         </td>
      </tr>
    </tbody>
</table>

### 12.11 InterfaceOverlimitContract

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
            Required
         </th>
         <th align="left">
            Descriptions/Field Value(s)
         </th>
      </tr>
    </thead>
    <tbody>
      <tr valign="top">
         <td>
            <p align="left">Type</p>
         </td>
         <td>
            <p align="left">-</p>
         </td>
         <td>
            <p align="left">byte</p>
         </td>
         <td>
            <p align="left">Yes</p>
         </td>
         <td>
            <p align="left">"Overlimit type.<br/>
               1: Percent<br/>
               2: Amount
            </p>
         </td>
      </tr>
      <tr valign="top">
         <td>
            <p align="left">Value</p>
         </td>
         <td>
            <p align="left">18</p>
         </td>
         <td>
            <p align="left">numeric</p>
         </td>
         <td>
            <p align="left">Yes</p>
         </td>
         <td>
            <p align="left">Overlimit value.</p>
         </td>
      </tr>
      <tr valign="top">
         <td>
            <p align="left">DateFrom</p>
         </td>
         <td>
            <p align="left">10</p>
         </td>
         <td>
            <p align="left">nvarchar</p>
         </td>
         <td>
            <p align="left">Yes</p>
         </td>
         <td>
            <p align="left">Starting date of the overlimit application.</p>
         </td>
      </tr>
      <tr valign="top">
         <td>
            <p align="left">DateTo</p>
         </td>
         <td>
            <p align="left">10</p>
         </td>
         <td>
            <p align="left">nvarchar</p>
         </td>
         <td>
            <p align="left">Yes</p>
         </td>
         <td>
            <p align="left">Finishing date of the overlimit application.</p>
         </td>
      </tr>
    </tbody>
</table>

### 12.12 InterfaceProgramContract

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
            Required
         </th>
         <th align="left">
            Descriptions/Field Value(s)
         </th>
      </tr>
    </thead>
    <tbody>
      <tr valign="top">
         <td>
            <p align="left">Id</p>
         </td>
         <td>
            <p align="left">36</p>
         </td>
         <td>
            <p align="left">Guid</p>
         </td>
         <td>
            <p align="left">No</p>
         </td>
         <td>
            <p align="left">Unique identifier of the program. If this value is not sent, the identification of the program will be through the code</p>
         </td>
      </tr>
      <tr valign="top">
         <td>
            <p align="left">Code</p>
         </td>
         <td>
            <p align="left">20</p>
         </td>
         <td>
            <p align="left">nvarchar</p>
         </td>
         <td>
            <p align="left">No</p>
         </td>
         <td>
            <p align="left">Code identification of the program. If this value is not sent, the identification of the program will be through by the Id</p>
         </td>
      </tr>
    </tbody>
</table>

### 12.13 Response messages

<table class="tg">
<thead>
  <tr>
    <th class="tg-gvcd"><span style="font-weight:bold"></span></th>
    <th class="tg-gvcd"><span style="font-weight:bold">HttpStatusCode</span></th>
    <th class="tg-gvcd"><span style="font-weight:bold">ATIONet Response</span></th>
    <th class="tg-gvcd"><span style="font-weight:bold">Description</span></th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-rjo2" rowspan="3">Response's</td>
    <td class="tg-eygw">200</td>
    <td class="tg-eygw">"ResponseCode": "00000",<br/>"ResponseMessage": "Ok",<br/>"ResponseError": null<br/></td>
    <td class="tg-eygw">Operation success.</td>
  </tr>
  <tr>
    <td class="tg-eygw">400</td>
    <td class="tg-eygw">"ResponseCode": "51007",<br/>"ResponseMessage": "Invalid Contract Code",<br/>"ResponseError": null<br/></td>
	<td class="tg-eygw">In the case of a validation error, the response message indicate the wrong field.</td>
  </tr>
  <tr>
    <td class="tg-eygw">401</td>
    <td class="tg-eygw">"ResponseCode": "52501",<br/>"ResponseMessage": "User Not Allowed",<br/>"ResponseError": null<br/></td>
	<td class="tg-eygw">In the case of an authentication error</td>
  </tr>
</tbody>
</table>



## 13 Examples

### 13.1 C# example

```C#
using System.IO;
using System.IO.Compression;
using System.Net;
using System.Text;

using Newtonsoft.Json;
```

```C#
// Create Json object
object requestObject = new { ActionCode = "925", SubscriberCode = "{YourSubscriberCode}", Identifier = "{YourIdentifier}" };

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
### 13.2 Example

```
{
    "TaxPayerId": "0000040",
    "Type": 0,
    "Active": true,
    "DesactivationType": null,
    "Code": "YourCode",
    "Name": "Name",
    "IndustryId": "08e9a648-606d-413d-be33-81a5ff380678",
    "Plan": null,
    "Street1": "Av. Street",
    "Street2": "Villa Street",
    "ZipCode": null,
    "City": "Cochabamba",
    "CountryId": "876cc6d9-485f-46f8-8bae-d7d5fdb52077",
    "StateId": "aa46446a-3796-43fe-af44-76071c913b3d",
    "Street1Delivery": "Av. Street",
    "Street2Delivery": "Villa Street",
    "ZipCodeDelivery": null,
    "CityDelivery": "Cochabamba",
    "StateDeliveryId": "aa46446a-3796-43fe-af44-76071c913b3d",
    "CountryDeliveryId": "876cc6d9-485f-46f8-8bae-d7d5fdb52077",
    "TaxPayerCategoryId": null,
    "ContactName": "ConcatName",
    "ContactEmail": "corporatemail@company.com",
    "Phone1": "11111111111",
    "Phone2": null,
    "Custom0": null,
    "Custom1": null,
    "Custom2": null,
    "Custom3": null,
    "CompanyGroupID": null,
    "PermissionsType": null,
    "Contracts": [
        {
            "Active": true,
            "ReactivationAmount": null,
            "DesactivationType": null,
            "Code": " ContractCode",
            "Description": "ContractDescription",
            "StartDate": "2022/04/07",
            "Duration": 99,
            "Periodicity": 3,
            "CurrentAccountMode": 1,
            "CurrencyID": null,
            "CurrencyCode": "USD",
            "Mode": 0,
            "CreditLimit": 100000,
            "BalanceMode": 2,
            "ValidateSites": false,
            "ValidateFuels": false,
            "ValidatePrograms": false,
            "Type": 0,
            "Subsidized": false,
            "Classification1Id": null,
            "Classification1Code": null,
            "Classification2Id": null,
            "Classification2Code": null,
            "Classification3Id": null,
            "Classification3Code": null,
            "Classification4Id": null,
            "Classification4Code": null,
            "Custom0": null,
            "Custom1": null,
            "Custom2": null,
            "Custom3": null,
            "CustomInterface0": null,
            "CustomInterface1": null,
            "CustomInterface2": null,
            "CustomInterface3": null,
            "CustomInterface4": null,
            "CustomOperation0": null,
            "CustomOperation1": null,
            "CustomOperation2": null,
            "CustomOperation3": null,
            "CustomOperation4": null,
            "PermissionsType": null,
            "BillingActive": false,
            "BillingDueDays": null,
            "BillingPeriodicity": null,
            "BillingPeriodicityValue": null,
            "BillingManual": null,
            "BillingCutTime": null,
            "BillingCutDay": null,
            "BillingCutMonth": null,
            "DocumentChargesFromBalance": null,
            "SeparateChargesDocument": null,
            "RecepientEmails": null,
            "BillingTaxPayerId": null,
            "BillingCompanyName": null,
            "BillingCompanyStreet1": null,
            "BillingCompanyStreet2": null,
            "BillingCompanyZipCode": null,
            "BillingCompanyCity": null,
            "BillingCompanyCountryId": null,
            "BillingCompanyStateId": null,
            "IdRackPricesList": null,
            "RackPricesListCode": null,
            "Fuels": [
                {
                    "FuelMasterId": "389dee96-c6af-4161-8e3a-fa7835994102",
                    "FuelMasterCode": "002",
                    "VolumeLimit": 0.00,
                    "MoneyLimit": 0.00
                }
            ],
            "Concepts": [],
            "Sites": [
                {
                    "SiteId":"16431f38-c140-41be-8235-b6fdfed5739d",
                    "Code":"ABC",
                    "Fuels":[
                        {
                            "FuelMasterId": "389dee96-c6af-4161-8e3a-fa7835994102",
                            "FuelMasterCode": "002",
                            "VolumeLimit": 0.00,
                            "MoneyLimit": 0.00
                        }
                    ]
                }
            ],
            "Prices": [
                {
                    "FuelMasterId": "577a92fa-cbb3-43d1-bb31-d54d8ff4a74a",
                    "FuelMasterCode":"002",
                    "Value": 5,
                    "SiteId":"16431f38-c140-41be-8235-b6fdfed5739d",
                    "SiteCode":"ABC",
                    "DateFrom":"2022/04/07",
                    "DateTo":"2023/04/01",
                    "TimeFrom":"00:00",
                    "TimeTo":"23:59"
                }
            ],
            "Modifiers": [
                {
                    "Class": 0,
                    "Type":1,
                    "Value":0.15,
                    "FuelMasterId": "577a92fa-cbb3-43d1-bb31-d54d8ff4a74a",
                    "SiteId": "16431f38-c140-41be-8235-b6fdfed5739d",
                    "SiteCode": "ABC",
                    "DateFrom":"2022/04/07",
                    "TimeFrom":"2023/04/01",
                    "DateTo":"00:00",
                    "TimeTo":"23:59"
                }
            ],
            "Blocks": [],
            "OverLimits": [],
            "Programs": [
                {
                    "Id": "8E5E3376-50BC-462C-BC21-666596220663",
                    "Code": "S2G1014"
                },
                {
                    "Code": "S2G1014"
                },
                {
                    "Id": "48A77FE4-FE48-4D13-BA4D-ACD3E38214D2"
                }
            ]
        }
    ],
    "ActionCode": "925",
    "SubscriberCode": "S2G",
    "SystemModel": "AtionetStandAloneTerminal"
}
```

