![ationetlogo](Content/Images/ATIOnetLogo_250x70.png) 
# ATIOnet Rules, Restrictions and Balances

> **About:** This document discusses the available rules types and their interaction with sub-account balances and contract balance processing configuration at transaction authorization time. ATIOnet supports different ways to implement restrictions and limits; this information should be useful to plan ahead the best suited alternative for each case. 	

</br>

<table>
	<thead>
		<tr>
			<td colspan="2" class="tablehead">Document Information</td>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td width="20%" class="rowhead" align="right">File:</td>
			<td>AN-Rules_Restrictions_Balances-Concepts</td>
		</tr>
		<tr>
			<td align="right">Doc. Version:</td>
			<td>1.0</td>
		</tr>
		<tr>
			<td align="right">Release Date:</td>
			<td>20/July/2014</td>
		</tr>
		<tr>
			<td align="right">Author:</td>
			<td>ATIO International LLC</td>
		</tr>
	</tbody>
</table>

<table>
     <thead>
          <tr>
          	<td colspan="3">Change Log</td>
          </tr>
     </thead>
     <tbody>
        <tr>
          	<td>Ver.</td>
            <td>Date</td>
            <td>Change summary</td>
        </tr>
        <!-- Insert a table row like this for each version -->
        <tr>
          	<td>1.0</td>
          	<td>20/July/2014</td>
          	<td>Initial Version</td>
        </tr>
        <!-- End of version table row -->
     </tbody>
</table>
</br>

### Contents
<!-- MarkdownTOC depth=3 -->

- Overview
- Restrictions
- Rules
	- Types of Rules
	- Subjects for Rules
- Balances

<!-- /MarkdownTOC -->



<!-- Optional Terms & Definition section -->
        

<!-- Content starts here -->

## Overview
ATIOnet Authorization Engine evaluates authorization requests using a three-step process:

- Validations: First, transaction requests are inspected against formatting defects, attack intents, and data integrity issues.
- Rules processing: Following, the engine checks whether the transaction can happen based on restrictions configured directly to the sub-account or inherited from the location, the contract, the classification or the groups to which the sub-account belongs to. These set of rules might restrict the execution of the transaction but also the amount and product to be served.
- Finally, if the transaction can happen, the amount or volume resulting after rules processing is sent to the current accounts sub-system, to check if it can be approved based on the contract's or the sub-account's balance.

As a result of the evaluation process, a transaction can be _declined_, _approved_, or _partially approved_. Depending on the Terminal's and protocol's capabilities a partial approval could be converted on a decline response. Also, there is a special decline situation called **Re-prompt**. Some Terminals can understand a re-prompt decline and just have the user enter an addtional piece of data, instead of completely rejecting the sale, whith this new prompt the transaction is re-sent to the host to be re-evaluated.

> ATIOnet always approves using the most restricting criteria 

## Restrictions
Let's define _Restriction_ as any system behavior that limits some dimension of a transaction.

The _dimensions_ of the restrictions are:

- Location: **Where** a transaction can be performed
- Temporal: **When**, certain days, days/time, fixed from/to dates.
- Value: **How much** money or product volume can be authorized
- Object: **What** product(s) and services can be charged
- Cualification: complementary **data** included during transaction capture (prompting) plus the operative **condition** (for example: offline or contingency entry method)

Restrictions can be derived from or affected by:

<dl>
	<dt>Rules</dt>
	<dd>Rules are the main way to set restrictions and conditions for the transaction authorization</dd>
	<dt>Vehicle Class</dt>
	<dd>The Vehicle class enforces fuel quantity limit and fuel product restriction to every vehicle belonging to that class without the need to set a quota or product rule.</dd>
	<dt>Program</dt>
	<dd>A Program is a set of attributes that can be selected for a given Identification type. Programs can be used to easly manage a very broad group of Identifications beyond particular sub-account conditions (for example: A Gold Card that has no restrictions) </dd>
	<dt>Site configuration</dt>
	<dd>Site's product configuration may indirectly impose a product restriction due to product availability configuration.</dd>
	<dt>Terminal / Controller configuration</dt>
	<dd>Terminal's configuration affects the authorization in three ways: 
		<br>- Sets the Max Cutoff Amount or Volume
		<br>- Sets the Default product, to be used when a money preauthorization is received but the account is set on product instead of money
		<br>- Flags the site as AVI-installed (automatic vehicle identification). Depending on Program's configuration, a transaction using an identification technology other than AVI (i.e: magnetic cards) might be flagged as a Contingency transaction.</dd>
	<dt>Contracts</dt>
	<dd>The terms of Merchant and Company contracts define the behavior of the current account subsystem, but also product and location restrictions, and both are subjects for rules application by themselves.</dd>
</dl>

## Rules
A Rule in ATIOnet is a user-defined condition that must be met by a transaction to be approved, or a user-value that will be used during the calculation of the amount or volume to be authorized.
Rules are user configured and given a name when created, so they can be reused or modified affected all related subject with a single user action. 

### Types of Rules
1. **Quota**: Restricts the number of transactions or total consumption (volume or amount) on each given period of time. The parameters are the Periodicity (daily, weekly, bi-weekly, etc) and the possible quota values (Transactions count, Money or Volume quota, Contingency quota, Offline quota and Security Limit)
2. **Fixed time**: Limit the operation to a certain period of time, after which the subject is not allowed to operate
3. **Location**: A list of Sites where the subject will be allowed to initiate a transaction
4. **Fuel Product**: Product(s) allowed to be included in the transaction
5. **Transaction Limits**: Maximum value for each transaction
6. **Days/Time**: Restriction to purchase only on certain days of the week and/or at certain times of the day
7. **Prompting**: Additional data required to be included in the authorization request. Options available:
	- Vehicle ID, Driver ID
	- Vehicle PIN, Driver PIN
	- Odometer and Engine hours, both with Min/Max variation from last transaction
	- Trailer Number
	- Miscellaneous prompt

### Subjects for Rules
Rules can be applied to:

- Vehicles
- Drivers
- Fleets
- Classifications (user-defined groups of Vehicles or Drivers)
- Sites

## Balances
The Balance is the available purchase limit of a Contract or sub-account (Vehicle or Driver).
A Company contract can be Credit or Debit, but also may have three possible ways to maintain the balance.

- **Balance Dispersion Mode**: In this mode, the effective balance is maintained at the sub-account level (each Vehicle or each Driver); meaning that no matter the balance of the Contract, the authorization request will be evaluated against the sub-account balance. This implies that after depositing values on the Contract -or renewing the period credit allowance- the Contract balance must be distributed to the sub-accounts by the Company via an automatic or manual Balance Dispersion transaction.
- **Contract Balance**: Is the opposite of the Dispersion Mode. In this mode, the balance is maintained at the Contract level, all sub-accounts consume from the global balance and no dispersion operation is needed.
- **Autofill**: This is a special mode, only available for Homebase subscription. In this mode, the current accounts sub-system is virtually nullified. Each time a transaction authorizaiton is requested the subsystem triggers an automatic deposit to the Contract or sub-account to compensate for the consumption. This mode is not available on Retail and Network subscribers.

Please refer to the document AN-Company_Contract-TechGuide.en for further information on Balances and Contracts.

