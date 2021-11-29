![ationetlogo](Content/Images/ATIOnetLogo_250x70.png)
# ATIONET - FMS Protocol Specification v1.0 #

|Document Information||
|--- |--- |
|File:|ATIONET-Native_Inventory_Protocol-Spec|
|Doc Version:|1.2|
|Release Date:|31, August 2020|
|Author:|ATIONET LLC|

|Change Log|||
|--- |--- |--- |
|Ver.|Date|Change Summary|
|1.0|31/Aug/2020|Initial version. Covers inventory and delivery messages.|
|1.1|26/Nov/2021|Update document <br> - Response Code's <br> - Deliveries insert request <br> - Inventories insert request|

## Contents ##

- [1 ATIOnet Integration Documentation Scope](#1-ationet-integration-documentation-scope)
- [2 Action Codes](#2-Action-Codes)
- [3 Deliveries Insert (POST) - Body Section Format Request](#3-Deliveries-Insert-POST--Body-Section-Format-Request)
	- [3.1 Trama Body Format](#31-Trama-Body-Format)
		- [3.2 GPS Body Format](#32-GPS-Body-Format)
- [4 Inventories Insert (POST) - Body Section Format Request](#4-Inventories-Insert-POST--Body-Section-Format-Request)
	- [4.1 Trama Body Format](#41-Trama-Body-Format)

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

## 1 ATIOnet Integration Documentation Scope

Third-party systems integrate with ATIOnet via a set of APIs (Application Programming Interfaces). Each ATIOnet’s API is described on a separate Protocol Specification. The complete documentation of ATIOnet API’s is comprised of:

#### ATIOnet Native Transactions Protocol Specification: 
Covers financial transactions for transaction capture systems (payment terminals, site controllers and point of sale systems), including sales and refunds.

#### ATIOnet Administrative Transactions Protocol Specification: 
Describes a set of functions complementing the transaction-capture business, for example Batch or Shift Close. These functions enhance the capabilities of the integration but their implementation is not mandatory.

## 2 Action Codes

The action code specifies what type of action will be executed when you enter a new request in the FMS.

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
			<p>701</p>
		</td>
		<td>
			<p>Title:</p>
		</td>
		<td>
			<p>Deliveries</p>
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>Function:</p>
		</td>
		<td>
			<p>Insert Deliveries request code</p>
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>Allowed for:</p>
		</td>
		<td>
			<p>FILL</p>
		</td>
	</tr>
	<tr valign="top">
		<td rowspan="3">
			<p>702</p>
		</td>
		<td>
			<p>Title:</p>
		</td>
		<td>
			<p>Inventories</p>
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>Function:</p>
		</td>
		<td>
			<p>Insert Inventories request code</p>
		</td>
	</tr>
	<tr valign="top">
		<td>
			<p>Allowed for:</p>
		</td>
		<td>
			<p>FILL</p>
		</td>
	</tr>
</table>

## 3 Deliveries Insert (POST) – Body Section Format *Request*
|Field Name|Condition|Descriptions/Field Value(s)|
|--- |--- |---
|ActionCode|Required|See Action Codes section above|
|TerminalCode|Required|Site’s Terminal identification code.|
|Trama|Required|Delivery values|


### 3.1 Trama Body Format 
|Field Name|Descriptions/Field Value(s)|
|--- |---
|TankNumber|The tank number|
|ProductCode|The fuel code. It is associated with the site|
|CreatedDateTime|Delivery creation date time ("yyyy/MM/dd hh:mm:ss")|
|StartingDateTime|Delivery start date time ("yyyy/MM/dd hh:mm:ss")|
|EndingDateTime|Delivery end date time ("yyyy/MM/dd hh:mm:ss")|
|StartingVolume|The starting volume|
|StartingVolumeTC|The starting volume TC|
|StartingWaterVolume|The starting water volume|
|StartingTemperature|The starting temperature|
|EndingVolumeTC|The ending volume TC|
|EndingWaterVolume|The ending water volume|
|EndingTemperature|The ending temperature|
|StartingFuelHeight|The starting fuel height|
|EndingFuelHeight|The ending fuel height|
|TotalVolumeTC|The total volume TC|
|InvoiceNumber|The invoice number|
|InvoiceItem|Invoice description|
|InvoiceDate|Invoice date ("yyyy/MM/dd hh:mm:ss")|
|CompensatedAmountRemitted|Compensated amount remitted|
|RealTemperature|The actual and exact temperature of the product when it is loaded into the truck|
|ReferenceTemperature|It is for a calendar month and the average temperature of the place of delivery is taken. It is obtained from the national meteorological services of each country and it is with which the amount of the invoice is corrected|
|Density|The density of the product at the time of being loaded into the truck|
|Comments|Delivery Comments|
|GPSData|GPS Values - see below|

### 3.2 GPS Body Format 
|Field Name|Descriptions/Field Value(s)|
|--- |---
|LatitudeStart|Start location: Latitude|
|LongitudeStart|Start location: Longitude|
|AltitudeStart|Start location: Altitude|
|StartingGPSDate|Start date of delivery location ("yyyy/MM/dd hh:mm:ss")|
|LatitudeEnd|End location: Latitude|
|LongitudeEnd|End location: Longitude|
|AltitudeEnd|End location: Altitude|
|EndingGPSDate|End date of delivery location ("yyyy/MM/dd hh:mm:ss")|

## 4 Inventories Insert (POST) – Body Section Format *Request*
|Field Name|Condition|Descriptions/Field Value(s)|
|--- |--- |--- |
|ActionCode|Required|See Action Codes section above|
|TerminalCode|Required|Site’s Terminal identification code.|
|Trama|Required|Inventory values|


### 4.1 Trama Body Format 
|Field Name|Descriptions/Field Value(s)|
|--- |---
|TankNumber|The tank number|
|ProductCode|The fuel code. It is associated with the site|
|DateTime|Inventory date time ("yyyy/MM/dd hh:mm:ss")|
|Volume|The volume|
|VolumeTC|The volume TC|
|Ullage|The ullage|
|WaterVolume|The water volume|
|FuelHeight|the fuel height|
|Temperature|The temperature|
|WaterHeight|The water height|
|Latitude|Location: Latitude|
|Longitude|Location: Longitude|
|Altitude|Location: Altitude|
|Date|Location date ("yyyy/MM/dd hh:mm:ss")|
