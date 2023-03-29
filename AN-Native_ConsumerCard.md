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
