![ationetlogo](Content/Images/ATIOnetLogo_250x70.png)

|**Document Information**|.|
|--- |--- |
|**File:**|ATIONet_Network_User_Manual-EN.md|
|**Doc Version:**|2.0|
|**Release Date:**|14, May 2021|
|**Author:**|ATIONet LLC|


|**Change Log**|||
|--- |--- |--- |
|**Ver.**|**Date**|**Change Summary**|
|1.0|02/Aug/2017|- Initial version
|2.0|14/May/2021|- Manual update

# Contents

- [Overview](#overview)
- [Definitions](#definitions)
	- [Contract](#contract) 
	- [Sub-account](#sub-account)
	- [Company](#company)
	- [Identification](#identification)
	- [Site](#site)
	- [Vehicle](#vehicle)
	- [Driver](#driver)
	- [Offline module](#offline-module)
	- [Terminal](#terminal)
- [Navigation Menu](#navigation-menu)
	- [DashBoard](#dashboard)
		- [Health Status](#health-status)
		- [Units/Months](#unitsmonths)
		- [Today’s Transactions](#todays-transactions)
		- [List of Outstanding Pre-Authorizations](#list-of-outstanding-pre-authorizations)
		- [Flagged Transactions Current Month](#flagged-transactions-current-month)
		- [Contracts Without Activity](list-of-outstanding-pre-authorizations)
		- [Sub-Accounts with Exceptions](#sub-accounts-with-exceptions)
		- [Recent Transactions](#recent-transactions)
		- [Contract Low Balance Listing](#contract-low-balance-listing)
		- [Sub-Account Low Balance Listing](#sub-account-low-balance-listing)
		- [Last Month Identification Updates](#last-month-identification-updates)
		- [Terminal status](#terminal-status)
	- [Favorites](#favorites)
	- [Reports](#reports)
		- [Driver](#driver-1)
		- [Transactions](#transactions)
		- [Vehicle](#vehicle-1)
	- [Administration](#administration)
		- [Brands](#brands)
		- [Companies](#companies)
		- [Companies Groups](#companies-groups)
		- [Companies Groups – Movements](#companies-groups--movements)
		- [Drivers](#drivers)
		- [Fuels](#fuels)
		- [Fuels Masters Groups](#fuels-masters-groups)
		- [Gift Card](#gift-card)
		- [Gift Cards Request](#gift-cards-request)
		- [Identifications](#identifications)
		- [Identifications Models](#identifications-models)
		- [Identifications Providers](#identifications-providers)
		- [Installations](#installations)
		- [Merchants](#merchants)
		- [Notifications](#notifications)
		- [Payment Methods](#payment-methods)
		- [Rack Prices](#rack-prices)
		- [Sites](#sites)
		- [SKUs](#skus)
		- [SKUs categories](#skus-categories)
		- [Taxes](#taxes)
		- [Terminals / Controllers](#terminals--controllers)
		- [Users](#users)
		- [Vehicle](#vehicle-2)
		- [Vouchers](#vouchers)
		- [Warehouses](#warehouses)
		- [Zones](#zones)
	- [Fleets](#fleets)
		- [Attendants](#attendants)
		- [Company Contracts](#company-contracts)
		- [Company Current Accounts](#company-current-accounts)
		- [Concepts](#concepts)
		- [Concept Families](#concept-families)
		- [Contingency](#contingency)
		- [Declined Transactions](#declined-transactions)
		- [Dispensed Transactions](#dispensed-transactions)
		- [Disputed Transactions](#disputed-transactions)
		- [Exceptions](#exceptions)
		- [Fast Track Configuration](#fast-track-configuration)
		- [Fraud Alerts](#fraud-alerts)
		- [Fraud Alerts Configuration](#fraud-alerts-configuration)
		- [Generation of Vouchers](#generation-of-vouchers)
		- [Invoice Type](#invoice-type)
		- [Invoices](#invoices)
		- [Merchants Contracts](#merchants-contracts)
		- [Merchant Current Accounts](#merchant-current-accounts)
		- [Outstanding Authorizations](#outstanding-authorizations)
		- [Over Limit](#over-limit)
		- [Programs](#programs)
		- [Requested Identifications](#requested-identifications)
		- [Rules](#rules)
		- [Transactions](#transactions-1)
		- [Transactions by Driver](#transactions-by-driver)
		- [Transactions by Fleet](#transactions-by-fleet)
		- [Transactions by Site](#transactions-by-site)
		- [Transactions by Vehicle](#transactions-by-vehicle)
		- [Uncontrolled Transactions](#uncontrolled-transactions)
	- [Billing](#billing)
		- [Billed Items](#billed-items)
		- [Billing Documents](#billing-documents)
		- [Billing Processes](#billing-processes)
		- [Billing Types Configuration](#billing-types-configuration)
		- [Charges Documents](#charges-documents)
		- [Statements](#statements)
	- [Notifications](#notifications-1)
		- [Alert Rules](#alert-rules)
		- [Notification Formats](#notification-formats)
		- [Notifications](#notifications-2)
	- [Configuration](#configuration)
		- [Company Contracts Classifications](#company-contracts-classifications)
		- [Contingencies Reasons](#contingencies-reasons)
		- [Network](#network)
		- [Process Configuration](#process-configuration)
		- [Sites Classification](#sites-classification)
	- [Logs](#logs)
		- [Audit Log](#audit-log)
		- [Process History](#process-history)
- [My Filters](#my-filters)
- [My Preferences](#my-preferences)
- [Inventory](#inventory)
  - [Inventory Chart](#inventory-chart)
  - [Inventory](#inventory-1)
  - [Deliveries](#deliveries)
  - [Inventory Reconciliation](#inventory-reconciliation)

# Overview

ATIONet is based on the premise that online communications between sites and the web portal are possible, however, it provides solid contingency procedures in the event of a communication error.

The ATIONet platform is a fleet management service with an innovative and unique market offer. Cloud processing, 100% web-based, multi-user access, data availability and sharing, instant updates, security, automatic back-up and paperwork reduction.

ATIONet is a web portal for fleet service companies that allows the processing of transactions from any point of sale application through a simple and reliable interface. 

ATIONet can be installed at any service station with one or multiple fleet service programs. The web portal allows fleet managers full access to their vehicle information.

ATIONet makes it possible for the fleet manager to operate, monitor, change and edit fleet information in real time.


# Definitions

## Contract 

The contract is the relationship that exists between the network and the client, in which it is guided, for example, if it will be of amount or volume, the price at which the fuel is going to be sold, in which sites it can load, among others.

## Sub-account 

Each time an identification is associated with a vehicle or driver, a sub-account is created. The sub-account is definitely who is going to have a current account, the sub-account is going to be able to receive deposits of money or product. The rules also impact the sub-account.

The sub-accounts are hierarchically dependent on the contract.

## Company

In ATIONet the company refers to the entity that owns the fleet. It is the one that manages the vehicles, drivers and fleet rules.

## Identification

The identification is the physical means used by ATIONet to identify a vehicle or driver. ATIONet supports various types of identifications, such as card, TAG, chip, ATIONet card, manual entry, barcode and iButton. When an identification is associated to a Vehicle or Driver, a sub-account is created.

## Site 

The Site represents the service station. A site is assigned a terminal/controller and may also have associated Location rules.

## Vehicle 

The vehicles can be associated or grouped by a fleet, they can have associated rules and at the moment of being related with an identification a sub-account is created. They may also have an associated driver.

## Driver 

The driver in ATIONet is the person who is identified as a chauffeur. If this driver is assigned an identification, a sub-account is created. Drivers may also have associated rules.

## Offline module 

ATIONet's offline module is automatically activated when the service station has no Internet connection and the authorizations cannot be processed online. At this point the offline module comes into play. For the terminal/controller it is completely transparent. When the offline module recovers the connectivity it sends all the information processed locally and also downloads any updates. As long as there is connectivity, the offline module is continuously downloading ATIONet updates (balances, identifications, rules, etc).

## Terminal

The terminal (or controller) is the representation of the dispenser controller, which needs to be parameterized in a particular way according to the type of terminal. The terminals handled by ATIONet are ATIO-NanoCPI, ATIO-Standalone, ATIO-CG, VF-Sapphire, VF-Commander, VF-Ruby, ControlGas, among others. 

# Navigation Menu

ATIONet has a quick access menu located on the left side of the website. From this menu you can access different options. The menu is divided into 9 sections. (Dashboard, Favorites, Reports, Administration, Fleets, Billing, Notifications, Configuration and Logbook).

## Dashboard

The Board is a page where you will have a global vision of the operation of your network. The dashboard has specific widgets that will help you make preventive or corrective decisions according to the information and data they show. The data shown in the Dashboard is real time data and some of the widgets are automatically refreshed.
These can be removed or added according to the user's needs in the **My Preferences** option. They can also be placed on the board according to the level of visibility you want to give each one.
The complete list of widgets available for Network subscriptions is as follows:

### Health Status

This widget is very important when starting up the network. This widget gives us information of which parameters we need to configure to be operative. It warns us when, for example, we don't have vehicles or identifications created among other parameters.
This widget can show **Warnings** (yellow icon) when the operation of the network is not in play, but if it shows a red cross indicates that the network is not operational.

![Health Status](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Dashboard/Health%20Status.PNG)

### Units/Months

The "Units/Month" indicates the amount of each fuel dispensed in the last month. The last month is the last 30 days from the day of the date. This widget has the ability to filter by Site, City and Fleet. You must select the filter and then enter the value by which it should be filtered. This last field is of the "auto complete" type.

![Units/Months](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Dashboard/Units-Months.PNG)

### Today’s Transactions

This widget contains a pie chart that shows very quickly how many transactions were approved and how many were rejected during the day.

![Today’s Transactions](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Dashboard/Today%E2%80%99s%20Transactions.PNG)

### List of Outstanding Pre-Authorizations

This list widget displays all pre-authorizations that have not yet received the completion transaction. (For more details on the transaction flow refer to this one [document]( https://github.com/Ationet/ationetdocs/blob/master/AN-Transaction_Flows-TechGuide.md)).

This shows 7 columns:

1. **Authorization Code:** The authorization code assigned to the transaction.
2. **Company:** The company to which the vehicle in question belongs.
3. **SubAccount:** The subaccount that requested the pre-authorization.
4. **Site:** The site where the transaction took place.
5. **Authorized:** The amount that was authorized in the pre-authorization.
6. **Pos:** Position or pump informed by the point of sale or controller.
7. **Age:** The time in minutes that this pre-authorization has been in effect.

The pending pre-authorizations should be dispatches in progress, if there are records in this widget with a high Age, means that the point of sale or controller did not send the completion transaction or the cancellation transaction in the case that fuel has not been dispatched.

![Outstanding Authorization List](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Dashboard/Outstanding%20Authorization%20List.PNG)

### Flagged Transactions Current Month

The following shows all transactions that were rejected by any of the validations made by ATIONet in the authorization process. Either due to lack of balance or rules among other validations.

![Flagged Transactions](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Dashboard/Flagged%20Transactions.PNG)

### Contracts Without Activity

Displays the list of contracts that were never active.

![Contracts Without Activity](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Dashboard/Contracts%20Without%20Activity.PNG)

### Sub-Accounts with Exceptions

This shows all sub-accounts that have something to pay attention to, such as:

1. **Without Identifications:** These are vehicles or drivers that do not have an associated identifier.
2. **With inactive Identification:** Are sub-accounts that have an associated identification that has been deactivated from the portal.
3. **With Suspended Identification:** Sub-accounts that have an identification that has been suspended. **Only ATIONet can suspend an identification**.
4. **With inactive Vehicle/Driver:** These are sub-accounts that have a vehicle or driver that has not been deactivated from the portal.

For more details about sub-accounts please consult [this section](#sub-account)

![Sub-Accounts with Exceptions](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Dashboard/Sub-Accounts%20with%20Exceptions.PNG)

### Recent Transactions

The following shows the last 20 completed transactions. It shows the most relevant data to be able to identify it, in case you need more information about the transaction you can click on the authorization code, that will take you to the view of details of the transaction.

![Recent Transactions](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Dashboard/Recent%20Transactions.PNG)

### Contract Low Balance Listing

Shows the list of contracts with low balance to trade 4 more days. This calculation is based on usage. The "Days Left" column shows the number of days remaining in the contract based on usage analysis. This number is not exact and may vary if the usage pattern changes.

![Contract Low Balance Listing](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Dashboard/Contract%20Low%20Balance%20Listing.PNG)

### Sub-Account Low Balance Listing

Shows the list of sub-accounts containing low balance to trade 4 more days. This calculation is made based on the use of each sub account. The "Days Left" column shows the number of days left in the sub-account based on the usage analysis. This number is not exact and may vary if the usage pattern changes.

![Sub-Account Low Balance Listing](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Dashboard/Sub-Account%20Low%20Balance%20Listing.PNG)

### Last Month Identification Updates

This widget shows the activity of the administration of identifications, shows the number of identifications that were modified grouped by state.

1. **Assigned:** The number of identifications that changed to the "Assigned" state.
2. **Available:** The number of identifications that changed to the "Available" state.
3. **Cancelled:** The number of identifications that changed to "Cancelled" status.
4. **Reported:** The number of identifications that changed to "Reported" status.
5. **Suspended:** The number of identifications that changed to "Suspended" status.

![Last Month Identification Updates](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Dashboard/Last%20Month%20Identification%20Updates.PNG)

### Terminal status

All terminals that are natively connected to ATIONet send a regular message indicating that they are active. If the terminal reported the status in the last 5 hours, the terminal will be shown with the green icon, if not reported in the last 5 hours the icon will be red.
The column **Age** shows the number of minutes since the last time the terminal was reported. 

![Terminal Status](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Dashboard/Terminal%20Status.PNG)

## Favorites

Vehicles, Drivers, Sites and Fleets are entities that may require daily monitoring by certain users. To facilitate this task you can add some of these sections to the list of **Favorites**. Once entered a section to this list, the access is faster and direct, without the need to enter filters each time you want to search.

Once inside the Favorites page, by clicking on the link in the **Type** column, you will be redirected to the detailed view of that section.

If you want to remove a section from the list of Favorites, click on the icon on the right side with the shape of a cross.

![Favorites](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Favorites.PNG)

## Reports
In ATIONet the reports are considered those lists of information that if or if they are going to be printed and filed in physical format. When they are printed, ATIONet adds a header with the logo of the subscription automatically.

### Driver
The Driver report can be filtered by driver name/code or by identification.
Once the filter is selected press the ***Print*** button, this will display a popup with the selected information.
The information is displayed in a print-ready format, including the subscription logo and the date and time of report generation.

This popup has a print button that when pressed opens the default print window of the Internet browser.

![Drivers](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Reports/Driver.PNG)

### Transactions
This report shows the list of transactions made, sorted by date. This report has several filters to adjust the search. The first field of the filter panel indicates why the field will sort the list, the field selected in this list will be shown in the first column.

![Transactions](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Reports/Transaction%20Filter.PNG)

Once the filter is selected press the ***Print*** button, this will display a popup with the selected information.
The information is displayed in a print-ready format, including the subscription logo and the date and time of report generation.

This popup has a print button that when pressed opens the default print window of the Internet browser.

![Transactions](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Reports/Transaction.PNG)

### Vehicle
This report shows the list of vehicles. This report has several filters to adjust the search. The first field of the filter panel indicates why the field will sort the list, the field selected in this list will be shown in the first column.

![Vehicles](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Reports/Vehicle%20Filter.PNG)

Once the filter is selected press the ***Print*** button, this will display a popup with the selected information.
The information is displayed in a print-ready format, including the subscription logo and the date and time the report was generated.

This popup has a print button that when pressed opens the default print window of the Internet browser.

![Vehicles](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Reports/Vehicle.PNG)

## Administration

### Brands
In ATIONet the term brand refers to the name for each master fuel available in ATIONet. This section lists all brands created in the Network.

![Brands](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Brands.PNG)

For every Network ATIONet already has a **DEFAULT** brand created with the following fuels:

![Brand DEFAULT](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Brand%20DEFAULT.PNG)

To create a new Brand, click the **New** button:

![Brands New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Brands%20New.PNG)

The fields to complete are the following:

* **Name:** The name of the new brand.
* **Fuel:** Select the ATIONet Master Fuel you wish to rename.
* **Fuel Name:** Input the new name for your fuel.

### Companies
In ATIONet the term company refers to the entity that owns the fleet. In this section you can see the existing companies with their details and edit them if you want. You can also filter them by name and/or code.

![Companies](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Companies.PNG)

### Companies Groups
This section lists all company groups created on the Network. This feature will allow you to group up companies into one.

![Companies Groups](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Companies%20Groups.PNG)

To create a new Company Group, click on the **New** button.

![Companies Groups New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Companies%20Groups%20New.PNG)

The fields to complete are the following:

* **Tax Payer Id:** Input the Company Group Taxpayer identification.
* **Active:** Checkmark to enable/disable the group company.
* **Code:** Input the Company Group unique code.
* **Name:** Input the Company Group name.
* **Industry:** Select the Company Group industry from the drop down menu.
* **Type:** Select the Company Group Type (Fleet, GiftCard or Retail).
* **Street 1:** Input the Company Group primary street.
* **Street 2:** Input the Company Group secondary street (if applicable).
* **Zip Code:** Input the Company Group zip code.
* **City:** Input the Company Group city.
* **Country:** Input the Company Group country.
* **State:** Input the Company Group state.
* **Taxpayer Category:** Select the Company Group taxpayer category (if applicable).
* **Contact Name:** Input the Company Group contact name.
* **Contact Email:** Input the Company Group contact email.
* **Phone Number 1:** Input the Company Group primary phone number.
* **Phone Number 2:** Input the Company Group secondary phone number (if applicable).
* **Current Account Mode:** Select the Company Group current account mode.
* **Currency:** Select the Company Group currency.
* **Mode:** Select the Company Group Mode (credit or debit).
* **Limit:** Input the Company Group limit.

<br>

* **Company:** Select the company or companies that are included in the Company Group.

### Companies Groups – Movements
This sections lists all movements (deposits, withrawals, completions, etc.) for all the Company Groups of the Network.

![Companies Groups Movements](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Companies%20Groups%20Movements.PNG)

Note that you must first complete the field **Companies Group** and then click on the **Search** button in order to see all their movements.

To create a new movement, click on the **New** button:

![Companies Groups Movements New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Companies%20Groups%20Movements%20New.PNG)

The fields to complete are the following:

* **Description:** Input a short description of the movement.
* **Companies Group:** Select the Companies Group associated to the movement.
* **Type:** Select the type of movement (deposit or withrawal).
* **Ammount:** Input the amount associated to the movement.

### Drivers
This view lists drivers who have been discharged. You can filter them by name, ID, company, etc. Also, in the options column to the right, you can choose to assign an ID, edit it, or mark the driver as a favorite.

![Drivers](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Drivers.PNG)

### Fuels
### Fuels Masters Groups
### Gift Card
In this section you can consult the created gift cards. You can perform batch actions such as activating or deactivating them. To make queries easier there is a panel of filters at the top.

To create a new Gift Card, click the **New** button.

![Gift Card](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Gift%20Card.PNG)

The fields to fill in to create a new gift card are the following:

![Gift Card New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Gift%20Card%20New.PNG)

* **Program**: The program to which the gift card will be associated.
* **Contract**: The contract to which the gift card will be associated.
* **Label**: The label is the inscription on the back of the card.
* **PAN**: The PAN is the number between 1 and 19 characters found on the gift card.
* **Track**: The Track is the information contained in the card, which is divided into three parts. In this field, you can customize what the second field of the track contains.
* **Type**: Select whether the gift card is a Card, TAG, Chipkey, Manual Entry, ATIONet Card or ATIONet TAG.
* **Model**: The model of the gift card.
* **Expiration Date**: The expiration date of the gift card.

When you have finished filling in the fields, click the **Save** button.

### Gift Cards Request
In this section, you can consult and request lots of gift cards.

![Gift Cards Request](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Gift%20Card%20Request.PNG)

To order a new set of gift cards, click the **New Request** button.

![Gift Cards Request New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Gift%20Card%20Request%20New.PNG)

The fields to complete are the following:

* **Program**: Select the program assigned to the batch of cards you are requesting.
* **Contract**: Select the contract of the program assigned to the batch of cards you are requesting.
* **Quantity**: Enter the number of cards you want to apply.
* **Expiration Date**: Enter the date the gift cards expire.
* **Type**: Select the type. It can be Card, TAG, Chipkey, Manual Entry, ATIONet Card or ATIONet TAG.
* **Model**: Select the model. It can be ATIONet CG, Card or Gift Card.

### Identifications
The identification is the physical means used by ATIONet to identify a vehicle or driver. ATIONet supports various types of identification, such as card, TAG, chip, ATIONet card, manual entry, barcode and iButton. When an identification is associated to a Vehicle or Driver, a sub-account is created. In this section, the identification already created will be shown. In the options column you can edit the identification, enable or disable it, release it.

![Identifications](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Identifications.PNG)

#### Create a new identification

To create a new identification click on the **New** button in the upper left side.

The form to create a new identification receives the following parameters:

![New Identification](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Identifications%20New.PNG)

* **Type:** Can be Card, TAG, Chipkey, Manual Entry, ATIOnet Card or ATIOnet TAG.
* **Model:** The model of the type of identification selected in **Type**.
* **Type of use:** Can be fleet, loyalty or dual.
* **Program:** The program to which this identification will be assigned.
* **Loyalty program:** The loyalty program to which this identifier will be assigned.
* **Label:** The name on the card (e.g. Pablo Pérez)
* **Track:** The track is the information that has the identification engraved inside it. It is divided into three parts. In this field you can edit what the second field of the track contains. 
* **PAN:** Number of between 1 and 19 characters found in the identification. 
* **PIN:** The PIN of the identification.

Note that depending on the type of identification, it will ask for certain items. For example, the TAG does not need a PIN. Also, if you select "Fleet" in the program type, it will not ask you to enter a loyalty program.

### Identifications Models
The models of identification vary according to the necessity of the client. They can be a Card type (a magnetic card), TAG, Chipkey or Manual Entry (A code entered by hand).

![Identification Models](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Identifications%20Model.PNG)

#### Create a new identification model

To create a new identificaiton model click on the **New** button located on the upper left side.

The form to create a new identification model receives the following parameters:

![New Identification Model](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Identifications%20Model%20New.PNG)

* **Type:** Can be Card, TAG, Chipkey or Manual Entry type.
* **Description:** The description of the new identification model.
* **Installable:** Whether it is installable or not.
* **Personalized:** Whether it is personalized or not.
* **Reusable:** Whether it is reusable or not.
* **Supports multiple assignments:** Whether it supports multiple assignments or not.
* **Valid expiration date:** Whether it validates the expiration date or not.
* **Ignore behavior of vehicle id in terminal:** Ignore the behavior of vehicle id in terminal or not.
* **Requires PIN** If it requires PIN or not.

When you have finished making the changes click the **Save** button.

### Identifications Providers
### Installations
In ATIONet, the fact that identifier needs to be placed by a technician is known as **Installations**. 

In this section you can consult all the installations carried out, listed by Date, Work Order, the identifications installed, the vehicle in which the identification was installed, the deposit from which the identification was removed and the technician who installed it.

![Installations](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Installation.PNG)

To create a new installation, click on the **New** button.

![Installation New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Installation%20New.PNG)

The fields you have to fill in are the following:

* **Work Order**: The unique number related to the work order document.
* **Technician**: The technician who carried out the installation.
* **Company**: The company of which the vehicle to which the installation was made was a part.
* **Date**: The date on which the installation was carried out.
* **Contract**: The contract to which the vehicle is linked.
* **Vehicle**: The vehicle to which the installation was made.
* **Deposit**: The deposit is the physical place where the identifier was removed to place it.
* **Has OBD**: Mark this option if the vehicle has an On-Board Diagnostics.

If you have OBD, more fields will be displayed:

* **ID**: Enter the OBD ID.
* **Model**: Select the OBD model.
* **Sensor**: Tilde this option if the OBD has a sensor.
* **Initial Odometer**: Enter the initial odometer.
* **Proportion**: Enter the OBD proportions.

Then, in the Identification section, enter the Identification. When finished, click the **Save** button.

### Merchants
In ATIONet the term merchant refers to the company that owns the sites. In this section you can see the existing shops with their details and edit them if you want.

![Merhcants](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Merchants.PNG)

### Notifications
### Payment Methods
Payment methods are the different ways in which you can pay for a transaction: cash, credit card, debit card, gift cards, etc. ATIONet is a tool for a merchant to create their own means of payment: a fuel payment card.

![Payment Methods](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Payment%20Methods.PNG)

#### Create a new payment method

To create a new payment method, click on the **New** button in the upper left hand corner.

The form to create a new payment method receives the following parameters:

![Payment Method New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Payment%20Methods%20New.PNG)

* **Code:** The code of the new payment method.
* **Description:** The description of the new payment method.

When finished completing all fields, click the **Save** button.

### Quotations
### Rack Prices

### Sites
The Site represents the service station. You assing terminals to a site and also it may have associated a location rules. This section lists the sites already entered in the system and their characteristics and you can also create new ones. You can also add taxes to sites directly from the **Options** column

![Sites](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Sites.PNG)

### SKUs
Stock Keeping Units (SKUs) are non-fuel products. In this section you can consult the created SKUs and edit them by clicking on the pencil icon in the options column.

![SKUs](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/SKUs.PNG)

To create a new SKU, click on the **New** button.

![SKUs New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/SKUs%20New.PNG)

The fields to complete are the following:

* **Code**: The SKU code.
* **Description**: The description of the SKU.
* **Short Description**: A short description of the SKU.
* **Ultra Short Description**: A very short description of the SKU.
* **POS Product Type**: Select what type of product it is.
* **Fuel Product**: Checkmark this option if the SKU is a fuel product.
* **SKU Category**: Enter the category to which the SKU belongs.
* **Measurement Unit**: Enter the unit in which the SKU is measured.
* **Sellable**: Checkmark this option if the SKU is sellable.
* **Weightable**: Checkmark this option if the SKU is weighable.
* **Fractional**: Checkmark this option if the SKU is fractional.
* **Stockable**: Checkmark this option if the SKU is storable.
* **Consignment**: Checkmark this option if the SKU is in consignment.
* **Availability From/To**: Select the dates among which the SKU is available.
* **Is POS**: Checkmark this option if the SKU is sold at the point of sale.
* **Dry Fleet**: Checkmark this option if the SKU is a dry product.
* **Reward**: Checkmark this option if the SKU can be redeemed for reward points.
* **Service**: Checkmark this option if the SKU is a service.
* **Loyalty**: Checkmark this option if the SKU accumulates points.
* **Stock Volume Min/Max Default**: ?
* **Days of Restock Default**: ?
* **Restock Default Volume**: ?

Pricebook:

* **Site**: Select the site to which you will charge the SKU price.
* **Date From**: Select the date on which the SKU goes into effect.
* **Price**: Indicate the price of the SKU.
* **Currency**: Select the currency in which the SKU is priced.

Items:

* **POS Code Format**: Select the point-of-sale code format.
* **POS Code**: Enter a point-of-sale code.

When you have finished filling those two fields, click the **Add** button.

* **Taxes**: Enter the SKU tax code.

### SKUs categories
In this section you can consult the categories of SKUs (Stock Keeping Units) already created and, if you want, edit them by clicking on the pencil icon in the options column.

![SKUs Categories](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/SKUs%20Category.PNG)

To create a new SKU, click on the **New** button.

![SKUs Categories New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/SKUs%20Category%20New.PNG)

The fields to complete are the following:

* **Code**: The SKU category code.
* **Name**: The name of the SKU category.
* **Short Description**: A short description of the SKU category.
* **First/Second Parent Category**: For example, if the SKU category was "Camel Cigarettes", the first parent category would be "Tobacco" and the second would be "Cigarettes".
* **Is POS**: Checkmark this option if the SKU category can be purchased at the point of sale.
* **Dry Fleet**: Checkmark this option if the SKU category is dry fleet.
* **Reward**: Checkmark this option if it can be redeemed for loyalty points.
* **Service**: Checkmark this option if it is a service.
* **Loyalty**: Checkmark this option if the purchase of the product accumulates loyalty points. 

### Taxes
The tax table displays:
* **Code:** Tax Code.
* **Description:** Tax description.
* **Type:** Type of tax (It can be a fixed tax, a percentage tax or a fixed tax per unit).
* **Amount:** The amount of tax (In the case of percentage tax, the percentage).
* **Date From / Date To:** Range of dates.
* **Options:** Edit the tax.

![Taxes](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Taxes.PNG)

To create a new tax, click on the **New** button in the upper left corner.

![Taxes New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Taxes%20New.PNG) 

The form to create a new tax receives the following parameters:

* **Code:** The code of the new tax.
* **Description:** The description of the new tax.
* **Type:** Type of tax (Can be a fixed tax, a percentual tax or a fixed tax per unit).
* **Date from:** The date on which the tax takes effect.
* **Amount:** The amount of the tax (In the case of percentual tax, the percentage).

After filling in the fields **Date from** and **Amount** click the **Add** button. 
When you have finished making the changes, click the **Save** button.

### Terminals / Controllers
### Users
In this view you can consult the users of the Network. You can edit them by clicking on the pencil icon in the options column, enable/disable a user by clicking on the padlock icon and reset the password with the star icon.

![Users](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Users.PNG)

To create a new User, click on the **New** button.

![Users New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Users%20New.PNG)

The fields to complete are the following:

* **User Mail**: The user's email address.
* **Name**: The user's name.
* **Social Security**: The user's document.
* **Street 1**: The street where the user resides.
* **Street 2**: Another street of reference, as it can be the one of the corner.
* **Country**: The user's country.
* **State**: The state of the user's country.
* **Zip Code**: The postal code of the locality where the user resides.
* **Phone Number 1**: The user's phone.
* **Phone Number 2**: The user's other phone if available.

<br>

* **Role**: The role that the new user will assume.
* **Entity**: The entity assigned to the user.

### Vehicle
This view lists all vehicles that have been created for the Network. Remember that it is not mandatory to load vehicles in order to operate, it is only necessary if you decide to associate the identifications to vehicles.

![Vehicles](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Vehicles.PNG)

### Vouchers
### Warehouses
### Zones

## Fleets

### Attendants
### Company Contracts
In ATIONet the term company refers to the company that owns the fleet. In this section you can consult the contracts. 

![Contratos de Compañía](Content/Includes/AN-HomeBase-UserManal-SP/contratosDeCompaniaAdministracion.png)

To make queries easier there is a window of applicable filters. You can filter by code, company, mode (credit or debit), description or species.

![Contratos de Compañía](Content/Includes/AN-Network-UserManal-SP/filtrosContratosDeCompañia.png)

To create a new Company contract, click on the New button.

The fields to be completed are as follows:

![Contratos de Compañía](Content/Includes/AN-Network-UserManal-SP/nuevoContratoCompañia.png)

* **Code**: The code you want to assign to the contract.
* **Mode**: You can choose whether the contract is credit or debit.
* **Description**: Enter a description of the contract.
* **Company**: Select a company.
* **Company User**: Enter a Company User.
* **Start Date**: Enter the effective date of the contract.
* **Duration** Enter the duration of the opposite.
* **Checking Account Mode**: You can select between Products or Amount.
* **Balance Mode**: You can choose between Scatter, No Scatter and Auto Fill.
* **Maximum Amount of Accounts**: Enter the maximum amount of account you will allow.
* **Validate Sites**: Check this option if you want to validate the sites.
* **Gift Card**: Tilde this option if ?

After filling these fields, you must enter the fuel assigned to the contract, and fill the fields Volume, Safety Limit, Overdraft, Start and End Dates of Overdraft, the currency in which the Fuel Value is and the fuel price.

![Contratos de Compañia](Content/Includes/AN-Network-UserManal-SP/nuevoContratoCompañia2.png)

The next thing is to register different items.

The first thing is the Registration of Sites. Enter the site and it will load below, asking you to provide the price of the fuels, and the currency in which they are.

Then, in the section "High identifiers" enter the identifiers that you want to relate to the contract.

![Contratos de Compañía](Content/Includes/AN-Network-UserManal-SP/nuevoContratoCompañia3.png)

After that, you will need to fill out the Settlement Configuration form.

The fields to complete are the following:

![Contratos de Compañia](Content/Includes/AN-Network-UserManal-SP/nuevoContratoCompañia4.png)

* **Type of Billing Process**: Select the type of Billing process you want.
* **Periodicity**: ?
* **Manual**: Tilde this option if ?
* **Cutting time**: ?
* **Charges Deducted from Contract Balance**: Tilde this option if the charges are deducted from the contract balance.
* **Separate Charge Document**: ?
* **Taxpayer ID**: ?
* **Street**: ?
* **Street 2**: ?
* **Zip Code**: ?
* **City**: ?
* **Country**: ?
* **State**: ?
* **Currency**: ?

Finally, you must fill out the Concept Registration form.

![Contratos de Compañia](Content/Includes/AN-Network-UserManal-SP/nuevoContratoCompañia5.png)

Enter a concept and then another form will be displayed.

![Contratos de Compañia](Content/Includes/AN-Network-UserManal-SP/nuevoContratoCompañia6.png)

* **Real price **: ?
* **Currency**: Select the currency in which the price is located.
* **Quantity**: ?
* **Liquid Event**: Select between Contract Period, Next Run of the Liquidation Process or Summary Period. ?
* **Application**: ?

Then, in the second tab, Discounts/Increases, you must fill in the following fields.

![Contratos de Compañia](Content/Includes/AN-Network-UserManal-SP/nuevoContratoCompañia7.png)

* **Class**: Select whether the concept is Discount or Increment.
* **Included**: Tilde this option if ?
* **Type**: Select if the concept is for Amount, Units, Percentage or if it is for Amount per unit.
* **Type of Rank**: Select if the type of rank is by amount or by units.
* **Staggered**: Tilde this option if ?
* **Roof Type**: Select if the roof type is by amount or by units.
* **Roof**: Enter the value of the roof.

In the Steps section you must fill in the following fields.

* **Range from**: ?
* **Range to**: ?
* **Value**: ?

When you have finished filling these fields, click on the "Add" button to register it.
### Company Current Accounts
The Company Checking Accounts view is the view where the available sub account balances are consulted (Remember that the sub account is the union between a vehicle/driver and an identifier. For more details on sub-a Conceptsccounts consult: [Esta sección](#sub-cuenta)).

In ATIONet the term company refers to the company that owns the fleet. For more details about companies consult: [Esta sección](#compañía)

This view has, like the rest of the views, a panel of filters.
The first option in the filter panel is the type of report we want to see:

![Cuentas Corrientes](Content/Includes/AN-Network-UserManal-SP/tiposDeCuentasCorrientesDeCompañia.PNG)

1. ***List of Contracts:*** This option lists the contracts with their respective balance, but does not give details of the movements, it is a view that summarizes the data of each of the sub-accounts.

	![Cuentas Corrientes](Content/Includes/AN-Network-UserManal-SP/listaDeContratos.png)

2. ***Contract Movements:*** This option lists the sub-accounts with their respective balance, but does not give details of the movements, it is a view that summarizes the data of each of the sub-accounts.

	![Cuentas Corrientes](Content/Includes/AN-Network-UserManal-SP/movimientosDeContratos.png)

3. ***List of Sub-accounts:*** This option lists the sub-accounts with their respective balance, but does not give details of the movements, it is a view that summarizes the data of each of the sub-accounts.

	![Cuentas Corrientes](Content/Includes/AN-Network-UserManal-SP/listaDeSubCuentas.png)

4. ***Sub-accounts Movements:*** This view option shows in detail each of the movements of the sub-account, both credits and debits.   

	![Cuentas Corrientes](Content/Includes/AN-HomeBase-UserManal-SP/cuentasCorrientes3.png)

Selecting this second option enables several more filters:

* ***Account Statement:*** Account Statement Number.
* If you enter one or more sub-account names, only the movements of those sub-accounts will be listed. Note that this field is "autocomplete", will be completed as you type, if you press the space bar will show all subaccounts.
* ***Date From / Date To:*** Entering these values will filter the movements between the two dates.
* ***Time From / Time To:*** Entering these values will filter the movements between the two hours.
* ***Amount From / Amount To:*** Entering these values will filter the movements whose amount is between both values.
* ***Species:*** You can filter by species (Product).
* ***Debit / Credit:*** You can select which type of movements you want to see, whether debit or credit.
* ***Type:*** What type of movement generated the movement in the current account
***Origin:***Origin of the movement, whether it is the ATIONet console, a mobile application or a call to the API from a third party application.
* ***Transient Movements:*** Checking this option will show the internal movements generated by ATIONet. For example, each time a balance is frozen after a pre-authorization and a termination transaction is received, ATIONet returns the frozen balance and subsequently debits the final amount reported. The return of the frozen balance is considered a transitory movement and is not shown if this option is not selected.

### Concepts
In this section you can consult the Concepts already created, listed by Code, Name, Type of Concept, Family of Concepts, Class, Type, Model and State. If you want to edit them, you can do so by clicking on the pencil icon in the options column.

To create a new concept, click on the "New" button.

![Conceptos](Content/Includes/AN-Network-UserManal-SP/conceptos.png)

###### Create a new concept

To create a new concept, you must fill out the following form:

![Conceptos](Content/Includes/AN-Network-UserManal-SP/nuevoConcepto.png)

In the information section, you must fill in the following fields:

* **Concept Type**: Select if it is a Product, Discount or Commission type.
* **Code**: The concept code.
* **Name**: The name of the concept.
* **Concept Family**: Select which concept family it belongs to.
* **Class**: Select which class of concept it belongs to.
* **Type**: The type of concept.
* **Model** The concept model.
* **Taxes Included**: Tilde this option if included in the amount of the transaction.

In the price list section, you must fill in the following fields:

* **Date from**: The date on which the concept comes into effect.
* **Currency**: In what currency is the concept.
* **Price**: The price of the concept.

When you have finished filling these fields, click on "Register".

In the tax section, you must fill the Tax field with the tax code to apply to the concept.

When you have finished filling out the form, click on "Save".

### Concept Families

In this section, you can consult the families of concepts created, listed by Code and Description. If you want to edit it, you can click on the pencil icon on the right.

In ATIOnet, the families of concepts are ?

![Depósitos](Content/Includes/AN-Network-UserManal-SP/familiaDeConceptos.png)

To create a new concept family, click on the "New" button and fill in the Code and Description fields.

![Depósitos](Content/Includes/AN-Network-UserManal-SP/nuevoFamiliaDeConceptos.png)

### Contingency
In this section, you can consult the contingencies of the Network. To make the queries easier, you have a panel of filters.

The contingencies are the transactions that were made without a pre-authorization, either because the terminal was off-line or because it did not have one.

![Contingencia](Content/Includes/AN-Network-UserManal-SP/contingencias.png)

To create a new contingency, click on the "New" button.

![Contigencia](Content/Includes/AN-Network-UserManal-SP/nuevaContingencia.png)

The fields to complete are the following:

* **Authorization Code**: The authorization code for the contingency.
* **Date**: The date of the contingency.
* **Time**: The time of the contingency.
* **Site**: The place where the contingency occurs.
* **Terminal/Controller**: The terminal/controller where the contingency occurs.
* **Primary Account**: ?
* **Secondary Account**: ?
* **Fuel**: The fuel being shipped.
* **Volume Dispatched**: The amount of fuel dispatched.
* **Unit Price**: The unit price of the shipment.
* **Dispatched Amount**: ?
* **Shift**: ?
* **Jet**: The jet from which the fuel is dispatched.
* **Odometer**: The amount of kilometers marked on the odometer of the vehicle.
* **Engine Hours**: The amount of engine hours the vehicle has.
* **Driver's Identifier**: The driver's identifier.
* **Vehicle ID**: The identifier of the vehicle.
* **Miscellaneous**: ?

### Declined Transactions
ATIONet separates unauthorized transactions into 2 sections, [Excepciones](#excepciones)and Rejected Transactions.
Rejected Transactions are those transactions that managed to pass ATIONet's hard validations but were rejected by other validations such as an unsatisfied rule or balance validation.

In the Rejected Transactions view we can filter by the type of rejection first. The types of rejections available are as follows:

![Transacciones Rechazadas](Content/Includes/AN-HomeBase-UserManal-SP/transaccionesRechazadas.png)

This view also has the filter panel mentioned above. It is worth highlighting the ***"Offline Transactions "*** filter, by checking this option, it will also show those transactions that were marked as rejected in the Offline module. 
(for more details about the Offline module see this [sección](#modulo-offline))

![Cuentas Corrientes](Content/Includes/AN-HomeBase-UserManal-SP/excepciones4.png)

Once you select the filters, press ***"Search "*** and all transactions marked as rejected will be listed.

![Transacciones Rechazadas](Content/Includes/AN-HomeBase-UserManal-SP/transaccionesRechazadas2.png)

It should be clarified that there is a possibility that a transaction may be rejected but that the fuel has been delivered. This occurs when the rejection occurs in the termination transaction.
Some of the most common reasons for this situation are the following:

* The pre authorization is expired (more than 3hs between the date of creation of the pre authorization and the date of creation of the termination. This is not related to the time it may take for the termination to arrive in offline mode).
* There is no existing pre-authorization for that transaction.
* The pre-authorization was cancelled manually.
* The termination transaction contains invalid information (errors in the terminal or controller).
* The termination transaction was executed with errors on the host.
* The termination transaction contains different information than the pre-authorization information, such as for example.
* The termination transaction reports more volume or amount than was authorized. In this case the authorization can be approved.

### Dispensed Transactions
### Disputed Transactions
Disputed transactions are those that either party (Commerce or Company) claims to be unaware of.

In this section you can consult the disputed transactions, listed by code, date, reason, state, transaction number, company, trade, site. There is also the commentary of the company, the trade and the network.

To make queries easier, this section has a panel of filters at the top.

![Transacciones Desconocidas](Content/Includes/AN-Network-UserManal-SP/transaccionesDesconocidas.png)

### Exceptions
ATIONet separates unauthorized transactions into 2 sections, Exceptions and [Transacciones Rechazadas](#transacciones-rechazadas).
Exceptions are those transactions that did not pass the hard validations of the system or those that are detected as possible frauds.

In the Exceptions view we can filter by Exception type first. The types of Exceptions available are as follows:

![Cuentas Corrientes](Content/Includes/AN-HomeBase-UserManal-SP/excepciones2.png)

This view also has the filter panel mentioned above. It is worth highlighting the ***"Offline Transactions "*** filter, by checking this option, it will also show those transactions that were marked as Exceptions in the Offline module. 
(for more details about the Offline module see this [sección](#modulo-offline))

![Cuentas Corrientes](Content/Includes/AN-HomeBase-UserManal-SP/excepciones4.png)

Once you have selected the filters, press ***"Search "***" and all transactions marked as Exceptions will appear in the list.

Some transactions remain in "Review" status in some situations, such as when more than authorized is sent (due to a controller or POS error). In these cases it is necessary to approve or reject the transaction using one of the two icons to the right of each record.

![Cuentas Corrientes](Content/Includes/AN-HomeBase-UserManal-SP/excepciones.png)


### Fast Track Configuration
?

![Configuración de Fast Track Administración](Content/Includes/AN-HomeBase-UserManal-SP/configuracionFastTrackAdministracion.png)
### Fraud Alerts
### Fraud Alerts Configuration
### Generation of Vouchers
### Invoice Type
### Invoices
### Merchants Contracts
In ATIONet the term commerce refers to the company that owns the sites. In this section you can consult the contracts.

![Contratos de Comercio](Content/Includes/AN-Network-UserManal-SP/contratosDeComercio.png)

To create a new Company contract, click on the New button.

The fields to be completed are as follows:

![Contratos de Compañia](Content/Includes/AN-Network-UserManal-SP/nuevoContratoDeComercio.png)

* **Code**: The code you want to assign to the contract.
* **Description**: Enter a description of the contract.
* **Trade**: Select a trade.
* **Commerce User**: Enter a Commerce User.
* **Start Date**: Enter the effective date of the contract.
* **Duration** Enter the duration of the opposite.
* **Checking Account Mode**: You can select between Products or Amount.

After completing these fields, you must enter the fuel assigned to the contract, and fill in the Volume, Safety Limit, Overdraft, Overdraft Start and End Dates fields, the currency in which the Fuel Value is located, and the fuel price.

![Contratos de Compañía](Content/Includes/AN-Network-UserManal-SP/nuevoContratoDeComercio2.png)

The next thing is to register different items.

The first thing is the Registration of Sites. Enter the site and it will load below, asking you to provide the price of the fuels, and the currency in which they are.

After that, you will have to fill out the Settlement Configuration form.

The fields to complete are the following:

![Contratos de Compañia](Content/Includes/AN-Network-UserManal-SP/nuevoContratoDeComercio3.png)

* **Type of Billing Process**: Select the type of Billing process you want.
* **Periodicity**: ?
* **Manual**: Tilde this option if ?
* **Cutting time**: ?
* **Charges Deducted from Contract Balance**: Tilde this option if the charges are deducted from the contract balance.
* **Separate Charges Document**: ?
* **Taxpayer ID**: ?
* **Name**: ?
* **Street**: ?
* **Street 2**: ?
* **Postal Code**: ?
* **City**: ?
* **Country**: ?
* **State**: ?
* **Currency**: ?

Finally, you must fill out the Concept Registration form.

![Contratos de Compañía](Content/Includes/AN-Network-UserManal-SP/nuevoContratoCompañia5.png)

Enter a concept and then another form will be displayed.

![Contratos de Compañía](Content/Includes/AN-Network-UserManal-SP/nuevoContratoCompañia6.png)

* **Real price **: ?
* **Currency**: Select the currency in which the price is located.
* **Quantity**: ?
* **Clearing**: Tilde this option if ?
* **Liquid Event **: Select between Contract Period, Next Run of the Liquidation Process or Summary Period. ?
* **Application**: ?

Then, in the second tab, Discounts/Increases, you must fill in the following fields.

![Contratos de Compañía](Content/Includes/AN-Network-UserManal-SP/nuevoContratoCompañia7.png)

* **Class**: Select whether the concept is Discount or Increment.
* **Included**: Tilde this option if ?
* **Type**: Select if the concept is for Amount, Units, Percentage or if it is for Amount per unit.
* **Type of Rank**: Select if the type of rank is by amount or by units.
* **Staggered**: Tilde this option if ?
* **Roof Type**: Select if the roof type is by amount or by units.
* **Roof**: Enter the value of the roof.

In the Steps section you must fill in the following fields.

* **Range from**: ?
* **Range to**: ?
* **Value**: ?

When you have finished filling these fields, click on the "Add" button to register it.

### Merchant Current Accounts
The trade current accounts view is the view where the balances and movements of the trades are consulted.
In ATIONet the term trade refers to the company that owns the sites.

This view has, like the rest of the views, a panel of filters.
The first option in the panel is the type of report we want to see.

![Cuentas Corrientes de Comercio](Content/Includes/AN-Network-UserManal-SP/cuentasCorrientesDeComercio.png)

### Outstanding Authorizations
Pending authorizations are those transactions that have not yet received the completion transaction. The records seen in this view are dispatched that are currently underway. If for some reason there are old pre-authorizations, it is likely that the POS did not send the completion transaction or the cancellation transaction if the dispatch was not completed.

Please note that at the time of pre-authorization, ATIONet froze the amount of the authorization of the current account of the sub-account.
This view presents all the fields necessary to identify the transaction and the vehicle. If you need to see more details, clicking on the authorization code will take you to the transaction details view.

![Autorizaciones Pendientes](Content/Includes/AN-Network-UserManal-SP/autorizacionesPendientes.png)

If old pending transactions appear and you are sure it is not an ongoing dispatch, you may cancel them and return the balance to the current account.
To do this you have 2 ways, individually, by clicking on the **X** icon to the right side of the grid, or massively by selecting the transactions, displaying the **Batch Actions** menu and selecting "Cancel". This will cancel the transactions and return the balance to each of the current accounts.

![Autorizaciones Pendientes](Content/Includes/AN-Network-UserManal-SP/autorizacionesPendientes2.png)

(for more details on the transaction flow refer to this [documento](AN-Transaction_Flows-TechGuide.md))

### Over Limit
### Programs
The programs in ATIOnet are ?

![Programas Administración](Content/Includes/AN-HomeBase-UserManal-SP/programasAdministracion.png)

To create a new program click on the "New" button.

![Programas Administración](Content/Includes/AN-Network-UserManal-SP/nuevoPrograma.png)

The fields to complete are the following:

* **Description**: The description of the program.
* **Apply Contract Sites**:
* **Balance Mode**:
* **Supports contigencies**:
* **Off-line support**:
* **Gift Card**: Tilde this option if ?

#### Create a new program

To create a new program, click on the "New" button in the upper left corner.

The form to create a new program receives the following parameters:

![Nuevo Programa Administración](Content/Includes/AN-HomeBase-UserManal-SP/crearNuevoProgramaAdministracion.png)

* ***Description:*** The description of the new program.
* ***Apply Contract Sites:*** May be unaffected, forced or unforced.
* ***Balance mode:*** Can be unaffected, dispersed, undispersed, unlimited or automatic filling.
* ***Supports contingencies:*** Can be unaffected, forced or unforced.
* ***Supports offline:*** Can be unaffected, forced or unforced.
* ***Gift card:*** Whether it includes a gift card or not. If this option is checked, three more parameters will appear:
* ***Gift Card Amount:*** The amount of the gift card.
* ***Rechargeable:*** If it is rechargeable.
* ***Company:***The company to which it is assigned.

When you have finished making the changes, click the "Save" button.

### Requested Identifications
In this section you can consult the requested identifications, request fleet identification and/or loyalty. You can also perform actions such as establishing the identifications as in production or as delivered.

It also has a panel to filter the requested identifications and thus make the search easier. You can filter by company name, order number, program, contract, state and/or loyalty program.

![Requested Identifications]()

To request a fleet identification click on the *Request Fleet Identifiers** button. When you do, a form will open. The fields to complete are:

* **Type**: Can be Card, TAG, Chipkey, Manual Entry, ATIOnet Card or ATIOnet TAG.
* **Model**: The model. Only those with a custom track will be shown.
* **Company**: The name of the company.
* **Contract**: The contract.
* **Program**: Select the program for the identifier.
* **Quantity**: The number of identifiers.

When you have finished filling in the fields, click on the **Request IDs** button.

![Fleet Requested Identification]()

To request a loyalty ID, click on the **Request Loyalty IDs** button. When you do, a form will open. The fields to complete are:

* **Model**: The model of the ATIOnet Card.
* **Loyalty Program**: The loyalty program to which the requested identifier belongs.
* **Number**: The number of identifiers you want to request.

When you have finished filling in the fields, click on the "Request IDs" button.

![Loyalty Requested Identification]()

### Rules
### Transactions

The transaction view is one of the most important in ATIONet. In this view you can see the transactions that were made and approved.

The Filter panel has all these possibilities:

![Transacciones](Content/Includes/AN-HomeBase-UserManal-SP/transactions.png)

* ***Authorization Code:*** Authorization Code delivered by ATIONet.
* ***Vehicle:*** Vehicle or Vehicles (autocomplete field and multiple selection, pressing the space bar will list the first 20 vehicles).
* ***Fleet:***The name of the fleet. (autocomplete and multiple selection field)
* ***Site:*** The name of the site. (autocomplete and multiple selection field)
* ***Date From / Date To:*** Range of dates.
* ***Time From / Time To:*** Range of hours.
* ***Period Performance:*** ?
* ***Offline Transactions:*** Checking this option will also list the approved transactions in Offline mode. (for more details on the Offline module please see this [sección](#modulo-offline))
* ***Shift:*** The turn in which the transaction occurred. (as long as the terminal or POS informs you)
* ***Driver:***The name of the driver. (autocomplete and multiple selection field).
* ***Terminal / Controller:*** Name of the terminal that recorded the transaction. (Autocomplete and multiple selection field).
* ***Fuel:*** The product involved in the transaction. (autocomplete and multiple selection field)
* ***Show Complete Transactions at Zero:*** Checking this option will also show transactions that have been sent with amount or volume at 0.
* ***Product Transactions:*** Checking this option will also show transactions that contain dry products.

Once you have selected the desired filter, press ***"Search "*** and it will list the transactions that comply with the filter.

![Transacciones](Content/Includes/AN-HomeBase-UserManal-SP/transactions2.png)

The grid shows the main data of the transaction, in the actions column you can ignore a transaction and enter the process of ignorance. (for more details on the ignorance of transactions see this [sección](#transacciones-desconocidas)).

If you want to see the transaction detail, click on the Authorization Code, this will take you to a detail view of the transaction.

![Transacciones](Content/Includes/AN-HomeBase-UserManal-SP/transactions3.png)
 
### Transactions by Driver

In this view you can see the transactions, grouped by the driver who made them. The buttons at the top left are for printing the table or creating an Excel file from the table, respectively.

![Transacciones por Sitio](Content/Includes/AN-HomeBase-UserManal-SP/transaccionesPorConductor.png)

The filter panel has the following possibilities:

![Transacciones por Sitio](Content/Includes/AN-HomeBase-UserManal-SP/filtrosTransaccionesPorConductor.png)

* ***Group by:***Site, Fleet, Program, Vehicle ID and/or Date.
* ***Driver:***Filter by driver who dispatched.
* ***Fleet:*** Filter by fleet to which the vehicle that made the dispatch belongs.
* ***Vehicle ID:***Filter by the ID of the vehicle that made the dispatch.
* ***Site:***Filter by the place where the dispatch took place.
* ***Terminal/Controller:*** Filter by terminal/controller that dispatched.
* ***Fuel:***Filter by the fuel that was dispatched.
* ***Date from/Date to:*** Range of dates to filter.
* ***Time from/to:*** Range of hours to filter.

When you have finished filling out the form, click "Search" to apply the filter, or "Create filter" to save the filter done.

### Transactions by Fleet
In this view you can see the transactions that were made, grouped by fleet. The buttons at the top left are for printing the table or creating an Excel file from the table, respectively.

![Transacciones por Sitio](Content/Includes/AN-HomeBase-UserManal-SP/transaccionesPorFlota.png)

The filter panel has the following possibilities:

![Transacciones por Sitio](Content/Includes/AN-HomeBase-UserManal-SP/filtrosTransaccionesPorFlota.png)

* ***Group by:***Site, Vehicle, Driver ID and/or Date.
* ***Fleet:*** Filter by fleet to which the vehicle that made the dispatch belongs.
* ***Vehicle:*** Filter by the vehicle that made the dispatch.
* ***Driver:***Filter by the ID of the driver who made the dispatch.
* ***Site:*** Filter by the place where the dispatch took place.
* ***Fuel:***Filter by the fuel that was dispatched.
* ***Terminal/Controller:*** Filter by terminal/controller that dispatched.
* ***Date from/Date to:*** Range of dates to filter.
* ***Time from/time to:*** Range of hours to filter.

When you finish filling the form, click "Search" to apply the filter, or "Create filter" to save the filter done.

### Transactions by Site

In this view you can see the transactions that took place, grouped by the place where they took place. The buttons at the top left are for printing the table or creating an Excel file from the table, respectively.

![Transacciones por Sitio](Content/Includes/AN-HomeBase-UserManal-SP/transaccionesPorSitio.png)

The filter panel has the following possibilities:

![Transacciones por Sitio](Content/Includes/AN-HomeBase-UserManal-SP/filtrosTransaccionesPorSitio.png)

* ***Group by:***Fuel, Fleet, Program, Shift and/or Date.
* ***Site:***Filter by the place where the dispatch took place.
* ***Fuel:***Filter by the fuel that was dispatched.
* ***Fleet:*** Filter by fleet to which the vehicle that made the dispatch belongs.
* ***Terminal/Controller:*** Filter by terminal/controller that dispatched.
* ***Date from/Date to:*** Range of dates to filter.
* ***Time from/to:*** Range of hours to filter.

When you finish filling the form, click "Search" to apply the filter, or "Create filter" to save the filter done.

### Transactions by Vehicle

In this view you can see the transactions, grouped by the vehicle that made them. The buttons at the top left are for printing the table or creating an Excel file from the table, respectively.

![Transacciones por Vehículo](Content/Includes/AN-HomeBase-UserManal-SP/transaccionesPorVehiculo.png)

The filter panel has the following possibilities:

![Transacciones por Sitio](Content/Includes/AN-HomeBase-UserManal-SP/filtrosTransaccionesPorVehiculo.png)

* ***Group by:***Site, Fleet, Program, Driver ID and/or Date.
* ***Vehicle:*** Filter by vehicle that made the dispatch.
* ***Fleet:*** Filter by fleet to which the vehicle that made the dispatch belongs.
* ***Driver:***Filter by the ID of the driver who made the dispatch.
* ***Site:*** Filter by the place where the dispatch took place.
* ***Terminal/Controller:*** Filter by terminal/controller that dispatched.
* ***Fuel:***Filter by the fuel that was dispatched.
* ***Date from/Date to:*** Range of dates to filter.
* ***Time from/to:*** Range of hours to filter.

When you have finished filling out the form, click "Search" to apply the filter, or "Create filter" to save the filter done.

### Uncontrolled Transactions

Uncontrolled transactions are those transactions that are generated because the controller detects a difference in gauges and sends a transaction for the difference. These transactions do not contain data about the identifier since they were generated automatically and were not initiated with the presentation of an identifier. As they do not have an identifier assigned, they are not impacted in any current account nor do they count for the calculation of rules.
This view also filters panel to make more specific searches.

![Transacciones sin Control](Content/Includes/AN-HomeBase-UserManal-SP/transaccionesFueraDeControl.png)

## Billing

### Billed Items
### Billing Documents
### Billing Processes
### Billing Types Configuration
### Charges Documents
### Statements

## Notifications

### Alert Rules
### Notification Formats
### Notifications

## Configuration

### Company Contracts Classifications
### Contingencies Reasons
### Network
### Process Configuration
### Sites Classification

## Logs

### Audit Log
### Process History

# My Filters

# My Preferences

# Inventory

## Inventory Chart

![Grafico de Inventarios](Content/Includes/AN-Network-UserManal-SP/graficoDeInventarios.png)

## Inventory

![Inventarios](Content/Includes/AN-Network-UserManal-SP/inventarios.png)

![Inventarios](Content/Includes/AN-Network-UserManal-SP/nuevoInventario.png)

## Deliveries

![Recepciones](Content/Includes/AN-Network-UserManal-SP/recepciones.png)

![Recepciones](Content/Includes/AN-Network-UserManal-SP/nuevoRecepciones.png)

## Inventory Reconciliation
![Reconciliacion Inventario](Content/Includes/AN-Network-UserManal-SP/reconciliacionInventario.png)

