![ationetlogo](Content/Images/ATIOnetLogo_250x70.png)

##ATIONet Native Interface API Protocol Specification##

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
			ATIONet-Native_Interface_Protocol_Spec-v1.3
		</td>
	</tr>
	<tr>
		<td>
		 Doc Version:
		</td>
		<td>
		 1.3
		</td>
	</tr>
	<tr>
		<td>
		 Release Date:
		</td>
		<td>
		 05, July 2014
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
			<p>Initial version.</p>
			<p>General information
			<br> Actions: Statement Charges (partial)
			<br> Transactions Download</p>
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>1.1</p>
		</td>
		<td>
			<p>07/Jan/2013</p>
		</td>
		<td>
			<p>Statement Charges
			<br> - Added Action 902 Negative Balance transfer to a sub-account</p>
			<p>New group of actions: 941 &ndash; 950 Account Inquiries (partial)
			<br> Actions: 941 Sub-account Balance Enquiry
			<br> 942 Sub-account Limit Enquiry</p>
			<p>Transactions Downloads
			<br> - Consolidated Classification Fields for Vehicles and Drivers
			<br> - Reorganized Response record, moved Classification fields after Driver Fields.</p>
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>1.2</p>
		</td>
		<td>
			<p>30/10/2013</p>
		</td>
		<td>
			<p>Account Inquiries
			<br> - Added Action 943 Contract Balance Enquiry</p>
			<p>New group of actions: 951 &ndash; 959 Account Download (partial)
			<br> Actions: 951 Sub-Account Movements Download
			<br> 952 Contract Movements Download</p>
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>1.3</p>
		</td>
		<td>
			<p>05/07/2014</p>
		</td>
		<td>
			<p><b>Statement Charges</b>
			<br> - Added Action 903 Transfer balance from sub-account to a sub-account</p>
			<p>- Added Action 904 Transfer balance from contract to a sub-account</p>
			<p>- Added Action 905 Transfer balance from sub-account to a contract</p>
			<p>- Change and reorganize request and response records</p>
			<p><b>Transactions Downloads</b>
			<br> - Change and reorganize request and response records</p>
			<p><b>Account Inquiries</b>
			<br> - Remove Action 943 Contract Balance Enquiry</p>
			<p>- Change and reorganize request and response records</p>
			<p><b>Account Downloads</b>
			<br> - Remove Action 952 Contract Movements Download</p>
			<p>- Change Action 951 Sub-Account Movements Download to 951 Movements Download</p>
			<p>- Change and reorganize request and response records</p>
			<p><b>Error Handling</b></p>
			<p>- Include &ldquo;ResponseError&rdquo; in response record for actions intended to post a command</p>
		</td>
	</tr>
</table>

**Contents**

[1 Scope](#1-scope)

>[1.1 Scope details](#11-scope-details)

[2 System Interface API](#2-system-interface-api)

>[2.1 Interface API Messages](#21-interface-api-messages)

[3 Data security](#3-data-security)

[4 Message Structure](#4-message-structure)

[5 Error handling](#5-error-handling)

[6 Statement Charges Interface](#6-statement-charges-interface)

>[6.1 Action Codes](#61-action-codes)

>[6.2 Identification](#62-identification)

>[6.3 Statement Charge (POST) – Body Section Record Format](#63-statement-charge-post--body-section-record-format)

[7 Transactions Download Interface](#7-transactions-download-interface)

>[7.1 Action Codes](#71-action-codes)

>[7.2 Transactions Download (POST) – Body Section Format Request](#72-transactions-download-post--body-section-format-request)

>[7.3 Transactions Download (POST) – Body Section Format Response](#73-transactions-download-post--body-section-format-response)

[8 Account Enquiries](#8-account-enquiries)

>[8.1 Action Codes](#81-action-codes)

>[8.2 Identification](#82-identification)

>[8.3 Account Enquiry (POST) – Body Section Record Format Request](#83-account-enquiry-post--body-section-record-format-request)

>[8.4 Account Enquiry (POST) – Body Section Record Format Response](#84-account-enquiry-post--body-section-record-format-response)

[9 Account Downloads](#9-account-downloads)

>[9.1 Action Codes](#91-action-codes)

>[9.2 Account Download (POST) – Body Section Format Request](#92-account-download-post--body-section-format-request)

>[9.3 Account Download (POST) – Body Section Format Response](#93-account-download-post--body-section-format-response)

####Overview####

#####Introduction#####

This specification is intended to document ATIONet’s Native Interface
API messaging format and related features required for the systems
applying for integration with ATIONet.

The Interface API allows the The following sections provide descriptions
of the messages themselves, the expected behaviour for each supported
action type and a common ground for the functionality of each relevant
item.

#####Definitions#####

######Subscriber.######
ATIONet’s subscription owner. The person or company who
runs the service.

######Homebase.######
A type of ATIONet subscription where the subscriber owns
the site(s) but also the fleet(s) of vehicles.

######Network.######
A type of ATIONet subscription where the subscriber enrolls
Fleet Companies and retail or commercial sites to operate with its own
method-of-payment. The Network company doesn’t own the site(s) or the
vehicles.

######Retail.######
A type of ATIONet subscription where the subscriber owns the
sites and enrolls Fleet Companies to operate with its own
method-of-payment.

######Merchant.######
On a Network type subscription, the Merchant is the
company who own the sites.

######Company.######
On a Network or Retail type subscription, the Company is
the company who own the fleet.

######Terminal.######
Transaction capture device at the site.

####1 Scope####

Version 1.3 of this document covers a particular version of ATIONet’s
Host protocol. Although feature’s descriptions are generally not related
to a particular version of the protocol, some changes may apply which
would be specifically commented and identified on each feature’s
description paragraph.

#####1.1 Scope details:#####

Protocol: ATIONet Native Interface API

Version: Version 1.3

API URI: native.ationet.com/v1/interface\

####2 System Interface API####

The Interface API provide system-to-system access to certain features of
ATIONet otherwise only available via the ATIONet Console, and it’s
intended to allow direct interaction of third-party systems on
Subscribers, Merchants and fleet Companies with ATIONet.

Availability of part or all the functionality of the Interface API is
subject to the business type and contract terms of the ATIONet
subscriber.

#####2.1 Interface API Messages#####

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
			<td rowspan="3">
				<p align="left">Statement charges
				<br> [HTTP POST]</p>
				<p align="left">901 to 920</p>
			</td>
			<td>
				<p align="center">1.0</p>
			</td>
			<td></td>
			<td>
				<p align="left">Commands ATIONet to process a movement on the account of a driver or vehicle, given an action type indicated on the message body.</p>
				<p align="left">Availability of this message and the type of actions allowed depend on the subscriber type and its contracting terms.</p>
				<p align="left">901 - Balance transfer to a sub-account</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="center">1.1</p>
			</td>
			<td></td>
			<td>
				<p align="left">902 - Balance withdrawal from a sub-account</p>
			</td>
		</tr>
		<tr valign="top">
			<td></td>
			<td>
				<p align="center">1.3</p>
			</td>
			<td>
				<p align="left">901 - Balance transfer to a sub-account</p>
				<p align="left">902 - Balance withdrawal from a sub-account</p>
				<p align="left">903 - Transfer balance from sub-account to a sub-account</p>
				<p align="left">904 - Transfer balance from contract to a sub-account</p>
				<p align="left">905 - Transfer balance from sub-account to a contract</p>
			</td>
		</tr>
		<tr valign="top">
			<td rowspan="3">
				<p align="left">Transactions Download
				<br> [HTTP POST]</p>
				<p align="left">931 to 940</p>
			</td>
			<td rowspan="2">
				<p align="center">1.0</p>
			</td>
			<td></td>
			<td>
				<p align="left">Returns a list of completed transactions from ATIONet host, between two dates, for a given Subscriber, Merchant or fleet Company</p>
				<p align="left">931 - Transactions Download</p>
				<p align="left">932 - Transactions Download for Merchants</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="center">1.1</p>
			</td>
			<td>
				<p align="left">931 - Transactions Download</p>
				<p align="left">932 - Transactions Download for Merchants</p>
			</td>
		</tr>
		<tr valign="top">
			<td></td>
			<td>
				<p align="center">1.3</p>
			</td>
			<td>
				<p align="left">931 - Transactions Download</p>
				<p align="left">932 - Transactions Download for Merchants</p>
			</td>
		</tr>
		<tr valign="top">
			<td rowspan="3">
				<p align="left">Account Enquiries
				<br>[HTTP POST]</p>
				<p align="left">941 to 950</p>
			</td>
			<td>
				<p align="center">1.1</p>
			</td>
			<td></td>
			<td>
				<p align="left">Returns specific values of a Contract or Sub-account.</p>
				<p align="left">941 - Sub-account Balance Enquiry</p>
				<p align="left">942 - Sub-Account Limit Enquiry</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="center">1.2</p>
			</td>
			<td></td>
			<td>
				<p align="left">943 - Contract Balance Enquiry</p>
			</td>
		</tr>
		<tr valign="top">
			<td></td>
			<td>
				<p align="center">1.3</p>
			</td>
			<td>
				<p align="left">941 - Sub-account Balance Enquiry</p>
				<p align="left">942 - Sub-Account Limit Enquiry</p>
				<p align="left"><strike>943 - Contract Balance Enquiry</strike></p>
			</td>
		</tr>
		<tr valign="top">
			<td rowspan="2">
				<p align="left">Account Downloads
				<br>[HTTP POST]</p>
				<p align="left">951 to 960</p>
			</td>
			<td>
				<p align="center">1.2</p>
			</td>
			<td></td>
			<td>
				<p align="left">951 - Sub-Account Movements Download</p>
				<p align="left">952 - Contract Movements Download</p>
			</td>
		</tr>
		<tr valign="top">
			<td></td>
			<td>
				<p align="center">1.3</p>
			</td>
			<td>
				<p align="left">951 - Movements Download</p>
				<p align="left"><strike>951 - Sub-Account Movements Download</strike></p>
				<p align="left"><strike>952	- Contract Movements Download</strike></p>
			</td>
		</tr>
	</tbody>
</table>

####3 Data security####

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

####4 Message Structure####

All Interface API messages share the same structure, what change from
message to message are the Action Code, which indicates the actual
interface function, the value fields sent and received, and the HTTP
action (POST, GET, REQUEST) which changes depending on the Action Code.

Both, requests and responses use a JSON format.

Only one request is accepted on each message, although some requests and
many responses will contain multiple records.

#####Request Format#####

*Header:*

	Accept-Encoding: gzip

	Authorization: Basic user:password

*Body:*

	{“ActionCode”:”nnn”,”FieldName”:”StringValue”,”FieldName”:Value}

#####Response#####

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

####5 Error handling#####

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

####6 Statement Charges Interface####

The Statement Charge message sends an instruction to ATIONet to apply a
well-defined action on the current account subsystem, the subject of the
action will be a sub-account of a contract, lets say a Vehicle or a
Driver account.

Depending on the type of charge, this message might be used by one or
the other party of the contract (the subscriber or the fleet company).

#####6.1 Action Codes#####

The Action Code specifies the type of accounting transactions requested
by a Statement Charge Message. The submitted code must match one of the
pre-defined operation types. Not all operation types are available for
all subscribers and/or fleet companies, availability depends on
subscription types but also on contract terms with ATIONet.

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
		<td rowspan="3">
			<p>901</p>
		</td>
		<td>
			<p>Title:</p>
		</td>
		<td>
			<p>Balance transfer to a sub-account</p>
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>Function:</p>
		</td>
		<td>
			<p>Transfers a given value from the global balance of the Contract to the sub-account related to the Vehicle or Driver.</p>
			<p>Contract Balance must have enough funds (or product volume) to allow the transfer; otherwise the action will be rejected by the current accounts subsystem.</p>
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>Observations</p>
		</td>
		<td>
			<p>The action will first trigger a Deposit action on the Contract and the Contract to sub-account transfer.</p>
		</td>
	</tr>
	<tr valign="top">
		<td rowspan="2">
			<p>902</p>
		</td>
		<td>
			<p>Title:</p>
		</td>
		<td>
			<p>Balance withdrawal from a sub-account</p>
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>Function:</p>
		</td>
		<td>
			<p>Withdraws a given value from the sub-account related to the Vehicle or Driver.</p>
			<p>Sub-account Balance must have enough funds (or product volume) to allow the withdrawal; otherwise the action will be rejected by the current accounts subsystem.</p>
		</td>
	</tr>
	<tr valign="top">
		<td rowspan="2">
			<p>903</p>
		</td>
		<td>
			<p>Title:</p>
		</td>
		<td>
			<p>Balance transfer from sub-account to sub-account</p>
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>Function:</p>
		</td>
		<td>
			<p>Transfers a given value from the original sub-account (related to the Original Vehicle or Driver) to the sub-account related to the Vehicle or Driver.</p>
			<p>Original sub-account balance must have enough funds (or product volume) to allow the transfer; otherwise the action will be rejected by the current accounts subsystem.</p>
		</td>
	</tr>
	<tr valign="top">
		<td rowspan="2">
			<p>904</p>
		</td>
		<td>
			<p>Title:</p>
		</td>
		<td>
			<p>Balance transfer from contract to sub-account</p>
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>Function:</p>
		</td>
		<td>
			<p>Transfers a given value from the contract to the sub-account related to the Vehicle or Driver.</p>
			<p>Contract balance must have enough funds (or product volume) to allow the transfer; otherwise the action will be rejected by the current accounts subsystem.</p>
		</td>
	</tr>
	<tr valign="top">
		<td rowspan="2">
			<p>905</p>
		</td>
		<td>
			<p>Title:</p>
		</td>
		<td>
			<p>Balance transfer from sub-account to contract</p>
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>Function:</p>
		</td>
		<td>
			<p>Transfers a given value from the sub-account related to the Vehicle or Driver to the contract.</p>
			<p>Sub-account Balance must have enough funds (or product volume) to allow the withdrawal; otherwise the action will be rejected by the current accounts subsystem.</p>
		</td>
	</tr>
</table>

#####6.2 Identification#####

When a Statement Charge is received, ATIONet will try to identify the
Subscriber, the Species (Currency Code or Master Fuel Code) and the
Identifier of the sub-account (Vehicle or Driver), this can be performed
thru several combinations of the Identification Fields on the body of
the message:

1.  Any Identifier field (Identifier, Driver Code, Vehicle Code, Vehicle
    Plate, SubAccount External Code and SubAccount Id) only. Only
    accepted for Home-base subscriptions.

2.  Company Code + Identifier.

3.  Company Code + Contract Code + (Driver Code or Vehicle Code or
    Vehicle Plate)

#####6.3 Statement Charge (POST) – Body Section Record Format#####

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

####7 Transactions Download Interface####

The Transactions Download Interface are POST actions to recover all the
payment transactions processed by ATIONet for a given Terminal, Contract
Code or Company Code depending on the particular Action Code.

The Action Code is validated against the type of company of the
authenticated user. Request not passing this validation will be
rejected.

The download will be limited by dates (from and to), which must be
included in the request

#####7.1 Action Codes#####

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

#####7.2 Transactions Download (POST) – Body Section Format *Request*#####

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

#####7.3 Transactions Download (POST) – Body Section Format *Response*#####

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
				<p>ProductUnitPrice</p>
			</td>
			<td>
				<p>10</p>
			</td>
			<td>
				<p>N</p>
			</td>
			<td>
				<p>PUP on a single-product transaction.</p>
				<p>xxx.xxx</p>
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
				<p>DriverLicenceState</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Driver licence jurisdiction</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>DriverLicenceNumber</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Driver licence</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>DriverID</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>N</p>
			</td>
			<td>
				<p>DriverID prompt result</p>
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
				<p>EngineHours</p>
			</td>
			<td>
				<p>10</p>
			</td>
			<td>
				<p>N</p>
			</td>
			<td>
				<p>Engine hours prompt result</p>
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
				<p>LastOdometer</p>
			</td>
			<td>
				<p>10</p>
			</td>
			<td>
				<p>N</p>
			</td>
			<td>
				<p>Previous odometer value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>LastEngineHours</p>
			</td>
			<td>
				<p>10</p>
			</td>
			<td>
				<p>N</p>
			</td>
			<td>
				<p>Previous engine hours value</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>TrailerHourMeterReading</p>
			</td>
			<td>
				<p>10</p>
			</td>
			<td>
				<p>N</p>
			</td>
			<td>
				<p>Trailer hours prompt result</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>TruckUnitNumber</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Truck Unit ID prompt result</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>TrailerNumber</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Trailer ID prompt result</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>TripNumber</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Trip/Guide/Route prompt result</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>PurchaseOrderNumber</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>PO prompt result</p>
			</td>
		</tr>
	</tbody>
</table>

####8 Account Enquiries####

The Account Enquiries messages retrieve data from ATIONet, specific to a
Contract or Sub-Account (Vehicle or Driver types).

Depending on the type of enquiry, this message might be used by one or
the other party of the contract (the subscriber or the fleet company).

#####8.1 Action Codes#####

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

#####8.2 Identification#####

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

#####8.3 Account Enquiry (POST) – Body Section Record Format *Request*#####

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

#####8.4 Account Enquiry (POST) – Body Section Record Format *Response*#####

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

####9 Account Downloads####

The Account Download messages are POST actions to recover all the
currents accounts movements processed by ATIONet for a given Company
Code depending on the particular Action Code.

The Action Code is validated against the type of company of the
authenticated user. Request not passing this validation will be
rejected.

The download will be limited by dates (from and to), which must be
included in the request

#####9.1 Action Codes#####

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

#####9.2 Account Download (POST) – Body Section Format *Request*#####

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
				<p align="left">From date to filter movements</p>
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
				<p align="left">To date to filter movements</p>
				<p align="left">&ldquo;yyyy/MM/dd hh:mm:ss&rdquo;</p>
			</td>
		</tr>
	</tbody>
</table>

#####9.3 Account Download (POST) – Body Section Format *Response*#####

<table>
	<thead>
		<tr valign="top">
			<th align="left">Field Name
			</th>
			<th align="left">Size
			</th>
			<th align="left">Type
			</th>
			<th align="left">Descriptions/Field Value(s)
			</th>
		</tr>
	</thead>
	<tbody>
		<tr valign="top">
			<td>
				<p>Id</p>
			</td>
			<td>
				<p>36</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Current account&rsquo;s UID</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>MovementId</p>
			</td>
			<td>
				<p>36</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Movements&rsquo;s UID</p>
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
				<p>HostDateTime</p>
			</td>
			<td>
				<p>19</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>ATIONet&rsquo;s transaction date time &ldquo;yyyy/mm/dd hh:mm:ss&rdquo;.</p>
				<p>ATIONet Host date time is UCT</p>
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
				<p>movement date expressed in subscriber time zone</p>
				<p>&ldquo;yyyy/mm/dd hh:mm:ss&rdquo;.</p>
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
				<p>Type</p>
			</td>
			<td>
				<p>1</p>
			</td>
			<td>
				<p>N</p>
			</td>
			<td>
				<p align="left">Internal ATIOnet movement type code</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>TypeDescription</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p align="left">Movement type description</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>Origin</p>
			</td>
			<td>
				<p>1</p>
			</td>
			<td>
				<p>N</p>
			</td>
			<td>
				<p>Internal ATIOnet code for the origin of the movement</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>OriginDescription</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Description for the origin of the movement</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p>Description</p>
			</td>
			<td>
				<p>1000</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Movement description</p>
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
				<p>IsDebit</p>
			</td>
			<td>
				<p>1</p>
			</td>
			<td>
				<p>N</p>
			</td>
			<td>
				<p>Indicates that&rsquo;s a debit or credit movement</p>
				<p>1 = &ldquo;True&rdquo;, 2= &ldquo;False&rdquo;</p>
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
				<p>CurrencyCode</p>
			</td>
			<td>
				<p>50</p>
			</td>
			<td>
				<p>A/N</p>
			</td>
			<td>
				<p>Currency of the amount fields</p>
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
