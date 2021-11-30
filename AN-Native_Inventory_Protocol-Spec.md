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
			<p>FMSAPI</p>
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
			<p>FMSAPI</p>
		</td>
	</tr>
</table>

## 3 Deliveries Insert (POST) – Body Section Format *Request*
|Field Name|Size|Type|Condition|Descriptions/Field Value(s)|
|--- |--- |--- |--- |---
|ActionCode|3|A/N|Required|See Action Codes section above|
|TerminalCode|50|A/N|Required|Site’s Terminal identification code.|
|Trama|X|X|Required|Delivery values|


### 3.1 Trama Body Format 
|Field Name|Size|Type|Condition|Descriptions/Field Value(s)|
|--- |--- |--- |--- |---
|TankNumber|X|A/N|Required|The tank number|
|ProductCode|X|A/N|Required|The fuel code. It is associated with the site|
|CreatedDateTime|X|A/N|Required|Delivery creation date time ("yyyy/MM/dd hh:mm:ss")|
|StartingDateTime|X|A/N|Optional|Delivery start date time ("yyyy/MM/dd hh:mm:ss")|
|EndingDateTime|X|A/N|Optional|Delivery end date time ("yyyy/MM/dd hh:mm:ss")|
|StartingVolume|X|N|Optional|The starting volume|
|StartingVolumeTC|X|N|Optional|The starting volume TC|
|StartingWaterVolume|X|N|Optional|The starting water volume|
|StartingTemperature|X|N|Optional|The starting temperature|
|EndingVolumeTC|X|N|Optional|The ending volume TC|
|EndingWaterVolume|X|N|Optional|The ending water volume|
|EndingTemperature|X|N|Optional|The ending temperature|
|StartingFuelHeight|X|N|Optional|The starting fuel height|
|EndingFuelHeight|X|N|Optional|The ending fuel height|
|TotalVolume|X|N|Required|The total volume|
|TotalVolumeTC|X|N|Optional|The total volume TC|
|InvoiceNumber|X|N|Optional|The invoice number|
|InvoiceItem|X|A/N|Optional|Invoice description|
|InvoiceDate|X|A/N|Optional|Invoice date ("yyyy/MM/dd hh:mm:ss")|
|PhysicalAmountRemitted|X|N|Optional|Physical amount remitted on invoice|
|CompensatedAmountRemitted|X|N|Optional|Compensated amount remitted on invoice|
|RealTemperature|X|N|Optional|The actual and exact temperature of the product when it is loaded into the truck|
|ReferenceTemperature|X|N|Optional|It is for a calendar month and the average temperature of the place of delivery is taken. It is obtained from the national meteorological services of each country and it is with which the amount of the invoice is corrected|
|Density|X|N|Optional|The density of the product at the time of being loaded into the truck|
|Comments|X|A/N|Optional|Delivery Comments|
|GPSData|X|X|Optional|GPS Values - see below|

### 3.2 GPS Body Format 
|Field Name|Size|Type|Condition|Descriptions/Field Value(s)|
|--- |--- |--- |--- |---
|LatitudeStart|X|N|Conditional|Start location: Latitude|
|LongitudeStart|X|N|Conditional|Start location: Longitude|
|AltitudeStart|X|N|Conditional|Start location: Altitude|
|StartingGPSDate|X|A/N|Conditional to Location Start|Start date of delivery location ("yyyy/MM/dd hh:mm:ss")|
|LatitudeEnd|X|N|Conditional|End location: Latitude|
|LongitudeEnd|X|N|Conditional|End location: Longitude|
|AltitudeEnd|X|N|Conditional|End location: Altitude|
|EndingGPSDate|X|A/N|Conditional to Location End|End date of delivery location ("yyyy/MM/dd hh:mm:ss")|

``` 
Note: The values aare conditioned to whether there is a value associated with it. For example, if you have a value for 
the initial latitude, the values for the end and the date must be present.
``` 

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
