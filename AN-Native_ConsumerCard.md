![ationetlogo](Content/Images/ATIOnetLogo_250x70.png)
# ATIONet Native Consumer Card API Protocol Specification

|Document Information|.|
|--- |--- |
|File:|AN-Native_ConsumerCard.md|
|Doc Version:|1.0|
|Release Date:|29, March 2023|
|Author:|ATIONet LLC|


|Change Log|||
|--- |--- |--- |
|Ver.|Date|Change Summary|
|1.0|04/Jan/2013|- Initial version.|

## Contents

- [1 Scope](#1-scope)
	- [1.1 Scope details](#11-scope-details)


## Overview

### Introduction

This specification is intended to document ATIONet’s Native Consumer Card
API messaging format and related features required for the systems
applying for integration with ATIONet.

The Interface API allows the The following sections provide descriptions
of the messages themselves, the expected behaviour for each supported
action type and a common ground for the functionality of each relevant
item.

## 1 Scope

Version 1.4 of this document covers a particular version of ATIONet’s
Host protocol. Although feature’s descriptions are generally not related
to a particular version of the protocol, some changes may apply which
would be specifically commented and identified on each feature’s
description paragraph.

### 1.1 Scope details

Protocol: ATIONet Native Interface API

Version: Version 1.4

API URI: native.ationet.com/v1/ConsumerCard

## 2 Consumer Card Client Recharge

The Consumer Card Client Recharge message sends an instruction to ATIONet to apply a
well-defined action on the consumer card subsystem. The subject of the action will be
a consumer card identification.

### 2.1 Action Codes

The Action Code specifies the type of recharge requested
The submitted code must match one of the pre-defined 
operation types. 

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
			<p>820</p>
		</td>
		<td>
			<p>Title:</p>
		</td>
		<td>
			<p>Consumer Card Client Recharge</p>
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>Function:</p>
		</td>
		<td>
			<p>Perform a balance recharge to a consumer card type identifier</p>
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>Allowed for:</p>
		</td>
		<td>
			<p>ConsumerCardAPI</p>
		</td>
	</tr>
	<tr valign="top">
		<td rowspan="3">
			<p>821</p>
		</td>
		<td>
			<p>Title:</p>
		</td>
		<td>
			<p>Consumer Card Client Recharge Void</p>
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>Function:</p>
		</td>
		<td>
			<p>Perform a reverse on the last balance recharge to a consumer card type identifier. The last movement made by the card must have been the balance recharge.</p>
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>Allowed for:</p>
		</td>
		<td>
			<p>ConsumerCardAPI</p>
		</td>
	</tr>
</table>

### 2.2 Consumer Card Client Recharge – Body Section Format *Request*

|Field Name|Size|Type|Condition|Descriptions/Field Value(s)|
|--- |--- |--- |--- |--- |
|ActionCode|3|A/N|Required|See Action Codes section above|
|SubscriberCode|3|A/N|Required|Fixed. To be assigned by ATIONet|
|TerminalCode|50|A/N|Required|Site’s Terminal identification code.|
|SystemModel|50|A/N|Required|System Model|
|SystemVersion|50|A/N|Required|System Version|
|MessageFormatVersion|50|A/N|Required|Message Format Version|
|TrackNumber|50|A/N|Required|The track number to identify the consumer card identification|
|Amount|18|N|Required|The amount of the operation to perform.|

### 2.3 Consumer Card Client Recharge – Body Section Format *Response*
|Field Name|Size|Type|Descriptions/Field Value(s)|
|--- |--- |--- |--- |
|Balance|18|N|The current balance of the card before the recharge.|
|ReceiptData|50|json|The information of the receipt related to the related recharge.|
|ResponseCode|50|A/N|The code representing the status of the operation.|
|ResponseMessage|50|A/N|The response message after the request has been processed. Here it could be indicated that the recharge was carried out successfully or the error message if it could not be carried out.|

### 2.4 Consumer Card Client Void Recharge – Body Section Format *Request*

|Field Name|Size|Type|Condition|Descriptions/Field Value(s)|
|--- |--- |--- |--- |--- |
|ActionCode|3|A/N|Required|See Action Codes section above|
|SubscriberCode|3|A/N|Required|Fixed. To be assigned by ATIONet|
|TerminalCode|50|A/N|Required|Site’s Terminal identification code.|
|SystemModel|50|A/N|Required|System Model|
|SystemVersion|50|A/N|Required|System Version|
|MessageFormatVersion|50|A/N|Required|Message Format Version|
|TrackNumber|50|A/N|Required|The track number to identify the consumer card identification|

### 2.5 Consumer Card Client Void Recharge – Body Section Format *Response*
Field Name|Size|Type|Descriptions/Field Value(s)|
|--- |--- |--- |--- |
|Balance|18|N|The current balance of the card before the recharge.|
|ReceiptData|50|json|The information of the receipt related to the related recharge.|
|ResponseCode|50|A/N|The code representing the status of the operation.|
|ResponseMessage|50|A/N|The response message after the request has been processed. Here it could be indicated that the recharge was carried out successfully or the error message if it could not be carried out.|



