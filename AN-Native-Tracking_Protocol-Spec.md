![ationetlogo](Content/Images/ATIOnetLogo_250x70.png)
# ATIONet Tracking Interface API Protocol Specification

|Document Information|.|
|--- |--- |
|File:|AN-Native-Tracking_Protocol-Spec|
|Doc Version:|1.0|
|Release Date:|29, November 2021|
|Author:|ATIONet LLC|

|Change Log|||
|--- |--- |--- |
|Ver.|Date|Change Summary|
|1.0|29/Nov/2021|- Initial version. <br> - General information <br> - Tracking Insert (POST) – Body Section Format Request|

## Contents

- [1 Scope](#1-scope)
	- [1.1 Scope details](#11-scope-details)
- [2 Actin Codes](#2-Action-Codes)
- [3 Event Types Codes](#3-Event-Types-Codes)
- [4 Tracking Insert (POST) – Body Section Format Request](#4-Tracking-Insert-POST--Body-Section-Format-Request)

## Overview

### Introduction

This specification is intended to document ATIONet’s Tracking Interface
API messaging format and related features required for the systems
applying for integration with ATIONet.

The Tracking API allows the The following sections provide descriptions
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

Version 1.0 of this document covers a particular version of ATIONet’s
Host protocol. Although feature’s descriptions are generally not related
to a particular version of the protocol, some changes may apply which
would be specifically commented and identified on each feature’s
description paragraph.

### 1.1 Scope details

Protocol: ATIONet Tracking Interface API

Version: Version 1.0

API URI: native.ationet.com/v1/tracking

## 2 Action Codes

The action code specifies what type of action will be executed when you enter a new request in the Tracking Native API.

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
			<p>1001</p>
		</td>
		<td>
			<p>Title:</p>
		</td>
		<td>
			<p>Tracking</p>
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>Function:</p>
		</td>
		<td>
			<p>Insert Tracking data request code</p>
		</td>
	</tr>
	
</table>

## 3 Event Types Codes

The event type specifies what type of tracking event will be associated with the tracking report send in the request.

|Event Type|Description|
|--- |--- 
|2|Report|
|3|No position|
|4|Detention|
|14|Detour|

## 4 Tracking Insert (POST) – Body Section Format *Request*

|Field Name|Condition|Descriptions/Field Value(s)|
|--- |--- |---
|ActionCode|Required|See Action Codes section above|
|SystemModel|Required|Internal value. Must be set to 1|
|SystemVersion|Required|Internal value. Must be set to 1.3|
|DeviceVolts|Required|Internal value. Must be set to 12.4|
|MessageFormatVersion|Required|Internal value. Must be set to 1|
|DeviceId|Required|This field will contain the identification number of the device linked to this service|
|EventType|Required|Event Type's Codes section above|
|HostDateTime|Required|The host date time ("yyyy/MM/dd HH:mm:ss")|
|DeviceDateTime|Required|The device date time ("yyyy/MM/dd HH:mm:ss")|
|Speed|Required|Vehicle speed|
|Odometer|Required|Vehicle odometer|
|Orientation|Required|Location: Orientation|
|Latitude|Required|Location: Latitude|
|Longitude|Required|Location: Longitude|