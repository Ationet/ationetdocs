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

## Contents ##

- [1 ATIOnet Integration Documentation Scope](#1-ationet-integration-documentation-scope)

- [2 Scope](#2-scope)
	- [2.1 Scope Details](#21-scope-details)
	- [2.2 Supported Transactions](#22-supported-transactions)

- [3 Data Security](#3-data-security)

- [4 Message Structure](#4-message-structure)
	- [Request Format](#request-format)
	- [Response Format](#response-format)

- [5 Error Handling](#5-error-handling)

- [6 Field descriptions](#6-field-descriptions)
	- [System Model and System Version](#system-model-and-system-version)
	- [Pump Authorization Values](#pump-authorization-values)
	- [Terminal Identification](#terminal-identification)
	- [Device Type Identifier](#device-type-identifier)
	- [Transaction Sequence Number](#transaction-sequence-number)
	- [Entry Method](#entry-method)
	- [Processing Mode](#processing-mode)
	- [Track Data](#track-data)
	- [Batch Number](#batch-number)
	- [Shift Number](#shift-number)
	- [Product Fields](#product-fields)
	- [Customer Data](#customer-data)
	- [Re-prompting & Dual-Card Identification](#re-prompting--dual-card-identification)
	- [Authorization Code](#authorization-code)
	- [PIN Block](#pin-block)
	- [Original Data](#original-data)

- [7 Transaction Request (TREQ) Message Format](#7-transaction-request-treq-message-format)

- [8 Transaction Response (TRESP) Message Format](#8-transaction-response-tresp-message-format)

- [9 Satellite TAG Validation Request (VREQ) Message Format](#9-satellite-tag-validation-request-vreq-message-format)

- [10 Satellite TAG Validation Response (VRESP) Message Format](#10-satellite-tag-validation-response-vresp-message-format)

- [11 Identification Pin Change Request (PREQ) Message Format](#11-identification-pin-change-request-preq-message-format)

- [12 Identification Pin Change Response (PRESP) Message Format](#12-identification-pin-change-response-presp-message-format)

- [13 Reference Tables](#11-reference-tables)
	- [13.1 Transaction Codes](#111-transaction-codes)
	- [13.2 Response Codes](#112-response-codes)	
	- [13.3 Account Types](#113-account-type)
	- [13.4 Product Data Structure](#114-product-data-structure)
	- [13.5 Customer Data](#115-customer-data)
	- [13.6 Measurement Unit Codes](#116-measurement-unit-codes)
	- [13.7 Currency Codes](#117-currency-codes)
	- [13.8 Original Data](#118-original-data)
- [14 Message Samples](#12-message-samples)
	- [14.1 Pre Authorization Sample](#121-pre-authorization-samples)
	- [14.2 Completion Sample](#122-completion-sample)
- [Appendix A - Native Authorization Protocol Messages](#appendix-a---native-authorization-protocol-messages)

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

