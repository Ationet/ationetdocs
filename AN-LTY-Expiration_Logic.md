![ationetlogo](Content/Images/ATIOnetLogo_250x70.png)
# ATIONet - Logic of Expiration of Points

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
			AN-LTY-Expiration_Logic
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
- Expiration Configuration
- Expiration Process
- Expiration Profiles
	- Single points expiration after retention period. Non-renewable.
	- Single points expiration. Renewable.
	- Batch expiration of period's points. Program's period
	- Batch expiration of all points. Program's period
	- Batch expiration of period's points. Members's period
	- Batch expiration of all points. Members's period

<!-- /MarkdownTOC -->

## Overview

### Introduction

This document describes the Points expiration profiles available in ATIOnet Loyalty.

### Definitions

###### Points
The value unit of a Loyalty Program, it can be Points, Miles, Kilometers or even a money value.

###### Loyalty Programs
Loyalty Programs (or just Programs in this document) are a set of definitions that govern how the ATIOnet Loyalty system will behave for a given Loyalty Member. Each Member belongs to one and only one Program.

###### Expiration
Loyalty Programs may specify a business rule forcing the cancellation of a part or the total of the Points accumulated on a Member's account based on the aging of the Points or other criteria. 

## Expiration Configuration
Each Loyalty Program may have none or one Expiration Profile. Programs that do not specify a profile will keep accumulated points indefinitely as long as the Loyalty Account is active. 

Profiles go from basic behavior, like "points are good for 6 months", to more complex rules like "each purchase renew previous balance", or "expiration cancels all points up to date". To simplify expiration configuration, typical behaviours are pre-defined on the ATIOnet Loyalty system. The user only has to select the preferred one.  

Expiration also requires a time lapse parameter, that can specified in Years, Months, or Days. Time lapse parameter specifies the _Retention_ period for the points.

Program Period Parameters: Period Start Date and Duration (Days, Months, Years)	
Some profiles that work with batch expiration require a cut date to evaluate the expiration. The process will cut the period automatically for each multiply of the _Duration_ parameter, since the _Period Start Date_

## Expiration Process

The ATIOnet Loyalty system runs a batch process that enforces the Expiration Profiles on a daily basis, at a configurable time of the day. The process always uses the date of the previous day as the Process Date. 
>Example: At 04:00AM of November/01. the process will run with Process Date = October/31. _Retention calculation includes the Process Date_, Points with single expiration whose retention period end on October/31 (up to 24:00) will be removed on the November/01's run.
>Note: When a Program has a Program Period parametrization, the process will effectively evaluate the Program on each cut date, although it will wake-up every day.

The result of an Expiration Process Run is one or more system-internal Expiration transactions. This transaction will be posted against the balance of each Loyalty account.

## Expiration Profiles

#### Single points expiration after retention period. Non-renewable.
Points will be cancelled the day after the retention period ends.

#### Single points expiration. Renewable.
Points will be cancelled the day after the retention period ends. New accumulations reset the retention elapsed time to zero (postpone the effective expiration for the a new period starting on the day of the new accumulation event).

#### Batch expiration of period's points. Program's period
All existing points that exceeded their retention period during the Period of the Program evaluated will be cancelled.

#### Batch expiration of all points. Program's period
All existing points will be cancelled. This profile does not check the Retention parameter.

#### Batch expiration of period's points. Members's period
The Member's Period is defined by a multiply of the _Duration_ parameters, since the date of affiliation of the Member.
>For example: A Member who joined a Program with Duration = 6 months, on March/15, will have period cuts on each March/15 and September/15.

Expiration Process runs following the Program Period Parameters, but only to define when it must process the Program. 
All existing points that exceeded their retention period during the Period of the Member evaluated will be cancelled.

#### Batch expiration of all points. Members's period
Same as previous but all existing points will be cancelled. This profile does not check the Retention parameter.



