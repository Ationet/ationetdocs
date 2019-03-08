![ationetlogo](Content/Images/ATIOnetLogo_250x70.png)
# ATIONet - Accumulation Transaction Logic

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
			AN-LTY-Accumulation_Logic
		</td>
	</tr>
	<tr>
		<td>
			Doc Version:
		</td>
		<td>
			1.0
		</td>
	</tr>
	<tr>
		<td>
			Release Date:
		</td>
		<td>
			04, Nov 2014
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
			<p>04/Nov/2014</p>
		</td>
		<td>
			<p>Initial version.</p>
		</td>
	</tr>
</table>

## Contents

<!-- MarkdownTOC depth=4 -->

- Overview
	- Introduction
	- Definitions
- Accumulation process
	- Accumulation methods
		- Locally-assigned
		- Program Rules - Transaction Amount
		- Program Rules - Ticket Data
	- Evaluation Order
- Rules Configuration
	- Transaction Amount
	- Products Catalog
	- Products Categories
	- Method of Payments
	- Allowed combinations
		- Configuration examples
	- Force and Time configurations

<!-- /MarkdownTOC -->

## Overview

### Introduction

This document explains how Points are calculated during the processing of Accumulation Transaction by the ATIOnet Loyalty Sub-system.

### Definitions

###### Points
The value unit of a Loyalty Program, it can be Points, Miles, Kilometers or even a money value.

###### Accumulation Transaction
An Accumulation transaction adds Points to the Member's Loyalty Account. Points can also be added by the Adjustment and Transfer transactions. ATIOnet does not implement any kind of manual entry or override of the balance of a Loyalty account.

###### Capture System
A system or device that handles the interaction with the Attendant and/or the Customer, and also process the Requests and Responses to and from ATIOnet Loyalty Service.  

###### Loyalty Programs
Loyalty Programs (or just Programs in this document) are a set of definitions that govern how the ATIOnet Loyalty system will behave for a given Loyalty Member. Each Member belongs to one and only one Program.

###### Expiration
Loyalty Programs may specify a business rule forcing the cancellation of a part or the total of the Points accumulated on a Member's account based on the aging of the Points or other criteria. 

## Accumulation process
ATIOnet Loyalty keeps a separate Loyalty Account for each Loyalty Member. The account balance is incremented by Accumulation Transactions and decremented by Redemption Transactions and Program's Expiration Rules. Adjustment and Transfer transactions may also add to or reduce the balance of the account, depending on the sign of the operation.

At the Service Point (Store, Kiosk, Web market, etc.), the Accumulation process is usually related to a purchase or payment operation, where the customers earn Points in exchange to their business.

A given Loyalty Program may have none, one or several Accumulation Rules. Accumulation Rules are processed on real-time when an Accumulation Transaction Request is received and tell ATIOnet Loyalty how many Points must be add to the Member's account. But also the Capture may specify a certain amount of Points to be awarded to the account, overriding Program's rules.

### Accumulation methods
Depending on the Request format and the Program's rules, ATIOnet Loyalty can process the accumulation in three different ways:

#### Locally-assigned
The Capture System sends a Points value on the Accumulation Request message. In this case ATIOnet Loyalty takes the informed value, assuming that there is a local calculation or manual assignment at the Capture system and stops processing any Program rules. 

#### Program Rules - Transaction Amount
An Accumulation Rule may specify a _Points-per-amount_ value. No matter the items purchased or the method of payments informed on the transaction request, Points will be credited according to the quotient between the transaction amount and the points-per-amount informed as the TargetAmount parameter on the rule.

#### Program Rules - Ticket Data
ATIOnet Loyalty will analize the list of Product Items and the list of Method-of-Payment informed on the TransactionData structure on the request and process all matching accumulation rule.

### Evaluation Order
The Accumulation process will first check and try to use any _Locally-assigned_ Points informed on the transaction. If this is the case, Host's rules processing will be aborted.
Then, the process will evaluate any applicable Program rules and choose the combination resulting in the __highest accumulation value__. Transaction Amount and Ticket-data rules are processed at this same step.

## Rules Configuration
Accumulation Rules can be set-up around the following items:

#### Transaction Amount
Requires setting the _Target-Amount_ and the _Points_ variables. Points will be credited as:
``` Accumulation = Transaction Amount / Target Amount * Points ```

#### Products Catalog
Requires setting the _Target-Product_, the _Points_, and _Units/Amount_ variables and optionally the _Target-Item-Amount_ variable. Points will be credited as:

If _Units/Amount_ is "Whole Quantity", 

``` Accumulation = Ticket-data.Product.Quantity * Points ```

If _Units/Amount_  is "Exact Quantity"

``` Accumulation = Ticket-data.Product.Quantity (rounded down to integer) * Points ```

If _Units/Amount_  is "Amount"

``` Accumulation = Ticket-data.Product.Amount / Target-Item-Amount * Points ```

#### Products Categories
Same as _Products catalog_ settings but uses a _Target-Category_ instead of a _Target-Product_. Calculation are equivalent but computes any product on the Ticket data that belongs to the target category. For example 100 Points each $100 on Lubes.

#### Method of Payments
Requires setting the _Target-Method-of-Payment_, the _Points_, and the _Target-MoP-Amount_ variables. Points will be credited as:

``` Accumulation = Ticket-data.Method-of-Payment.Amount / Target-MoP-Amount * Points ```

The Method of Payment rule applies always to the amount informed for the particular MoP in the Ticket data (as opposed to the Transaction Amount). An additional parameter (_Target-MoP-Exclusive_) on MoP rules controls when the MoP has to be exclusive to be considered. By default, the Points will be awarded considering the partial value informed on the Ticket data.

### Allowed combinations
- __Transaction-Amount + Method-of-Payment__. Process the amount rule only when the MoP is present in the Ticket Data
- __Target-Product + Method-of-Payment__. Process the product rule, related to Units or Amount, only when the MoP is present in the Ticket Data
- __Target-Category + Method-of-Payment__. Process the product category rule, related to Units or Amount, only when the MoP is present in the Ticket Data   

> Target-Product and Target-Categories are mutually exclusive. A rule cannot be configured targeting both.

#### Configuration examples

<table>
	<tr>
		<td width="30%"> Description </td>
		<td width="20%">Type</td>
		<td width="40%">Parameters</td>
	</tr>
	<tr>
		<td>1 Point per Diesel Gallon</td>
		<td>Product</td>
		<td>Target-Product = "Diesel" </br>Points=1</br>Units/Amount="Whole Quantity"</td>
	</tr>
	<tr>
		<td>1 Point per full gallon</td>
		<td>Category</td>
		<td>Target-Category = "Fuels" </br>Points=1</br>Units/Amount="Exact Quantity"</td>
	</tr>
	<tr>
		<td>10 Point each $100 in Services</td>
		<td>Category</td>
		<td>Target-Category = "Services" </br>Points=10</br>Units/Amount="Amount"</br>Target-Item-Amount=100</td>
	</tr>
	<tr>
		<td>10 Point each $100 paying in Visa</td>
		<td>Method-of-Payment</td>
		<td>Target-MoP = "Visa" </br>Points=10</br>Target-Mop-Amount=100</td>
	</tr>
	<tr>
		<td>10 Point each $100 in Services when paid with Visa</td>
		<td>Combined</td>
		<td>Target-Category = "Services" </br>Points=10</br>Units/Amount="Amount"</br>Target-Item-Amount=100</br>Target-MoP = "Visa"</td>
</table>

### Force and Time configurations
ATIOnet Loyalty Accumulation rules also implements a set of time parameters that controls, the validity period of the rule and the time and days of the week when the rule applies. This allows to configure juxtaposed rules that will apply depending on the moment of the day or week. 

For example: 
- 10 Points per Carwash, valid from November to January.  
- 15 Points per Carwash, paying with Mastercard on Sundays, valid from November to January.
On a Wednesday, ATIOnet Loyalty will find both rules and discard the Sunday rule, because of the Time/Days restriction.
On a Sunday, if the Ticket data includes Mastercard, both rules will be processed and the _highest accumulation_ criteria will define the accumulation value. (15 points).


