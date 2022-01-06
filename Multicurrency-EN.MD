![ationetlogo](Content/Images/ATIOnetLogo_250x70.png)

|**Document Information**|.|
|--- |--- |
|**File:**|Multicurrency-EN.MD|
|**Doc Version:**|1.0|
|**Release Date:**|05, Jan 2022|
|**Author:**|ATIONet LLC|


|**Change Log**|||
|--- |--- |--- |
|**Ver.**|**Date**|**Change Summary**|
|1.0|05/Jan/2022|- Initial version


# Contents

- [Multicurrency](#multicurrency) 	
    - [Configurations](#configurations) 

<br>

# Multicurrency

### Objetive
The purpose of the document is to detail how the Multicurrency functionality helps in the daily management of fuel in ATIONET when transactions are generated in different currencies, seeking to reduce manual processes that our users may carry out.

<br>

### Introduction
In countries or regions in which several currencies circulate, the multi-currency functionality is strategic and essential. Provides the possibility that your customers can pay with different currencies according to the site or region where they are.

<br>

### Description
The Multicurrency functionality allows you to operate with different currencies within the portal. In order to use this functionality, it is necessary to make some configurations on the platform that will allow the required conversions to be made in each operation.

Four different types of currencies are involved:
- Operation currency: it is the currency of occurrence, in a transaction it is the currency configured on the site, in a current account movement it is the currency chosen for payment.
- Conversion currency: it is the pivot currency, used for any conversion from the currency of operation to any other currency.
- Current account currency: it is the currency in which the contracts are administered, and therefore the current account.
- Reconciliation currency: it is the currency used to reconcile all current accounts, if the Network wants to reconcile all its contracts. Although these conversions are being made today, this value is not shown anywhere, in any report.

<br>


### Initial setup flow required

![Flujomultimoneda](ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/flujomultimoneda.PNG)

* In the section Configuration you can find the details of the settings necessary to enable Multicurrency functionality.

<br>


### Impacted views
The views that are impacted by the Multicurrency functionality are detailed below:
- Transactions
- Current Account Movements
- Account status
- Billing Process Configuration
- Merchant Contract.
- Network Configuration
- Site and Settings

<br>


#### Transaction views
The currencies that interact in the authorization circuit of a transaction can be identified as complementary data in the fields that represent the monetary value of the same.
Within the transaction views, the following are affected by the multi-currency functionality:

- Transactions
- Details of Transactions
- Detail of Exceptions
- Dispatched Transactions
- ERP transactions
- Declined Transactions

<br>


##### Transaction views


##### Detail View (This section is the same in all Transactions and Exceptions)


##### Dispensed Transactions View


##### ERP Transactions view


##### Declined Transactions View


<br>

### Grouped transaction views

Se pueden visualizar las monedas que interactúan en el circuito de autorización de una transacción como dato complementario en los campos que representan valor monetario de la misma. Las vistas en las que se ven reflejadas son las siguientes:



##### Transactions by Driver views

##### Transactions by Vehicle views

##### Transactions by Fleet views

##### Transactions by Site viewss

<br>


### Quote in transaction
The authorization engine has the logic to consider the calculation of current configured quotes in the authorized amounts, and in the validation of customers' availability to transact, as well as the impact of the corresponding amounts in the currency of the contract on the current account of the same.

<br>

### Current Account Quote
Allows you to carry out Current Account movements (deposits) in Company and / or Commerce Contracts and in subaccounts, in currencies other than those of the referred contract.

<br>

### Company Checking Account View
The Currency column can be viewed in the Company Current Account grid, as well as in the export of movements and printing of them to Excel. The currency will be displayed as long as the contract is in amount.

<br>


##### Excel file of movement Company Current Account


##### New movement of Company Current Account

<br>


### View of Trade Current Accounts
The Currency column can be viewed in the Commercial Current Accounts grid, as well as in the export of movements to Excel. The currency will be displayed as long as the contract is in amount.


##### Excel file of movement Merchant Current Accounts


##### New movement of Merchant Current Account


<br>


### Values in account statements
The Multicurrency functionality impacts on the account statement generation process, which makes it consider the recorded values of the transactions based on the currencies involved to perform the corresponding calculations and reflect them in the account statement.

<br>


### Site view and configuration
The currency configuration at the Site level is used in the calculation of currency conversions in case there is a currency of the Site, and a currency of a Company / Merchant Agreement. It is part of the multi-currency functionality for international transactions or contract operations in different currencies.

It should be clarified that the Currency field is mandatory in the configuration of a Site, a Currency column was also incorporated in the Excel document that is downloaded when the sites are exported from the ATIONET portal.

<br>



### Currency in contingency
The site currency field can be found in Contingency listing, details, creation and editing view. In the creation and edition view, the currency is automatically loaded when choosing the place of occurrence of the transaction.

<br>


### Currency in manual pre-authorization widget
When you want to generate a pre-authorization through the widget, the currency will be indicated automatically once the site where you want to pre-authorize a transaction is loaded.

<br>


### Currency in pending pre authorization widget
In the widget view of pending pre-authorizations you can see the currency code of the Site.

<br>


## Configurations

The necessary settings to enable Multicurrency functionality are the following:


<br>


### Currency configuration in Network

In this section, within the network configuration, three types of currencies can be configured (Accounting, Conversion, Reconciliation), as part of the multi-currency functionality for international transactions.

##### Add Image

In the three options select the currency with which you are going to manage the Network.


<br>


### Create and configure Quote

This step is very important to be able to operate with different currencies:

In Administration / Create quote of the selected currency in configurations with the other currency with which it will be managed:

##### Add Image

Any currency other than accounting has to be added as a quote.

Take into account that in the default grid you see the current prices, in case you need to view quotes with Future or Past validities, you can use the Validity filter.

##### Add Image

<br>


### Currency Settings on Site

<br>


In this view, when creating or editing a Site, the currency of operation can be configured.
##### Add Image

<br>

#### Edit Site

By selecting the Edit option, the currency can be configured in a place where it is required:
##### Add Image

The detail is enabled and in the Currency field select the one that corresponds:
##### Add Image

<br>


#### New Site
When creating a new Site, in the Currency field you must select the currency that will be used in it.

##### Add Image

The incorporation of currency configuration at the Site level is intended to be used in the calculation of currency conversions if it were the case between the site currency and the currency of a company / trade contract. Part of the multi-currency operation functionality for international transactions or contract operations in different currencies.