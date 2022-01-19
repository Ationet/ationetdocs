![ationetlogo](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/ATIOnetLogo_250x70.png)

|**Document Information**|.|
|--- |--- |
|**File:**|ATIONET_Company_User_Manual-EN.MD|
|**Doc Version:**|1.0|
|**Release Date:**|19, Jan 2022|
|**Author:**|ATIONET LLC|


|**Change Log**|||
|--- |--- |--- |
|**Ver.**|**Date**|**Change Summary**|
|1.0|19/Jan/2022|- Initial version


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
- [My Preferences](#my-preferences) 
- [Navigation Menu](#navigation-menu)
	- [DashBoard](#dashboard)
		- [Health Status](#dashboard)
		- [Units/Months](#unitsmonths)
		- [Today’s Transactions](#todays-transactions)
		- [List of Outstanding Pre-Authorizations](#list-of-outstanding-pre-authorizations)
		- [Flagged Transactions Current Month](#flagged-transactions-current-month)
		- [List of Outstanding Pre-Authorizations](#list-of-outstanding-pre-authorizations)
		- [Recent Transactions](#recent-transactions)
		- [Contract Low Balance Listing](#contract-low-balance-listing)
		- [Sub-Account Low Balance Listing](#sub-account-low-balance-listing)
		- [Last Month Identification Updates](#last-month-identification-updates)
		- [Terminal status](#terminal-status)
	- [Favorites](#favorites)
	- [Reports](#reports)
		- [Driver](#driver)
		- [Transactions](#transactions)
		- [Vehicle](#vehicle)
	- [Administration](#administration)
		- [Companies](#companies)
		- [Dispersion](#dispersion)
		- [Drivers](#drivers)
		- [External Documentation](#external-documentation)
		- [Fleet](#fleet)
		- [Notifications](#notifications)
		- [Sites](#sites)
		- [Users](#users)
		- [Vehicle](#vehicle)
		- [Vehicle classes](#vehicle-classes)
		- [Vouchers](#vouchers)				
	- [Fleets](#fleets)
		- [Company Contracts](#company-contracts)
		- [Company Current Accounts](#company-current-accounts)
		- [Declined Transactions](#declined-transactions)
		- [Dispensed Transactions](#dispensed-transactions)
		- [Disputed Transactions](#disputed-transactions)
		- [Exceptions](#exceptions)
		- [Fast Track Configuration](#fast-track-configuration)
		- [Outstanding Authorizations](#outstanding-authorizations)
		- [Requested Identifications](#requested-identifications)
		- [Rules](#rules)
		- [Transactions](#transactions)
		- [Transactions by Driver](#transactions-by-driver)
		- [Transactions by Fleet](#transactions-by-fleet)
		- [Transactions by Site](#transactions-by-site)
		- [Transactions by Vehicle](#transactions-by-vehicle)
	- [Billing](#billing)
		- [Billed Items](#billing)-items)
		- [Charges Documents](#changes-documents)
		- [Billing Processes](#billing)-processes)
		- [Statements](#statements)
	- [Configuration](#configuration)
		- [Company Contracts Classifications](#company-contracts-classifications)		
	- [Logs](#logs)
		- [Audit Log](#audit-log)
		
# Overview

ATIONET is based on the premise that online communications between sites and the web portal are possible, however, it provides solid contingency procedures in the event of a communication error.

The ATIONET platform is a fleet management service with an innovative and unique market offer. Cloud processing, 100% web-based, multi-user access, data availability and sharing, instant updates, security, automatic back-up and paperwork reduction.

ATIONET is a web portal for fleet service companies that allows the processing of transactions from any point of sale application through a simple and reliable interface. 

ATIONET can be installed at any service station with one or multiple fleet service programs. The web portal allows fleet managers full access to their vehicle information.

ATIONET makes it possible for the fleet manager to operate, monitor, change and edit fleet information in real time.


# Definitions

## Contract 

The contract is the relationship that exists between the network and the client, in which it is guided, for example, if it will be of amount or volume, the price at which the fuel is going to be sold, in which sites it can load, among others.

## Sub-account 

Each time an identification is associated with a vehicle or driver, a sub-account is created. The sub-account is definitely who is going to have a current account, the sub-account is going to be able to receive deposits of money or product. The rules also impact the sub-account.

The sub-accounts are hierarchically dependent on the contract.

## Company

In ATIONET the company refers to the entity that owns the fleet. It is the one that manages the vehicles, drivers and fleet rules.

## Identification

The identification is the physical means used by ATIONET to identify a vehicle or driver. ATIONET supports various types of identifications, such as card, TAG, chip, ATIONET card, manual entry, barcode and iButton. When an identification is associated to a Vehicle or Driver, a sub-account is created.

## Site 

The Site represents the service station. A site is assigned a terminal/controller and may also have associated Location rules.

## Vehicle 

The vehicles can be associated or grouped by a fleet, they can have associated rules and at the moment of being related with an identification a sub-account is created. They may also have an associated driver.

## Driver 

The driver in ATIONET is the person who is identified as a chauffeur. If this driver is assigned an identification, a sub-account is created. Drivers may also have associated rules.

## Offline module 

ATIONET's offline module is automatically activated when the service station has no Internet connection and the authorizations cannot be processed online. At this point the offline module comes into play. For the terminal/controller it is completely transparent. When the offline module recovers the connectivity it sends all the information processed locally and also downloads any updates. As long as there is connectivity, the offline module is continuously downloading ATIONET updates (balances, identifications, rules, etc).

## Terminal

The terminal (or controller) is the representation of the dispenser controller, which needs to be parameterized in a particular way according to the type of terminal. The terminals handled by ATIONET are ATIO-NanoCPI, ATIO-Standalone, ATIO-CG, VF-Sapphire, VF-Commander, VF-Ruby, ControlGas, among others. 

# Navigation Menu

ATIONET has a quick access menu located on the left side of the website. From this menu you can access different options. The menu is divided into 9 sections. (Dashboard, Favorites, Reports, Administration, Fleets, Billing, Notifications, Configuration and Logbook).

# My Preferences
Inside this section each user can customize their portal preferences.

1. **Default Role:** Select the default role when loggin in.

![Default Role](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/My%20Preferences/Default%20Role.PNG)

2. **Profile Picture:** Change the profile picture of your user.

![Profile Picture](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/My%20Preferences/Profile%20Picture.PNG)

3. **Change Password:** Change the password for your user.

![Change Password](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/My%20Preferences/Change%20Password.PNG)

To edit your password, click the ***change password*** link.

![Change Password New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/My%20Preferences/Change%20Password%20New.PNG)

4. **Widgets Configuration:** Select which widgets to show on your dashboard.

![Widget Configuration](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/My%20Preferences/Widget%20Configuration.PNG)


# Dashboard

The Board is a page where you will have a global vision of the operation of your network. The dashboard has specific widgets that will help you make preventive or corrective decisions according to the information and data they show. The data shown in the Dashboard is real time data and some of the widgets are automatically refreshed.
These can be removed or added according to the user's needs in the **My Preferences** option. They can also be placed on the board according to the level of visibility you want to give each one.
The complete list of widgets available for Network subscriptions is as follows:

## Health Status

This widget is very important when starting up the network. This widget gives us information of which parameters we need to configure to be operative. It warns us when, for example, we don't have vehicles or identifications created among other parameters.
This widget can show **Warnings** (yellow icon) when the operation of the network is not in play, but if it shows a red cross indicates that the network is not operational.

![Health Status](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Dashboard/Health%20Status.PNG)

## Units/Months

The "Units/Month" indicates the amount of each fuel dispensed in the last month. The last month is the last 30 days from the day of the date. This widget has the ability to filter by Site, City and Fleet. You must select the filter and then enter the value by which it should be filtered. This last field is of the "auto complete" type.

![Units/Months](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Dashboard/Units-Months.PNG)

## Today’s Transactions

This widget contains a pie chart that shows very quickly how many transactions were approved and how many were rejected during the day.

![Today’s Transactions](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Dashboard/Today%E2%80%99s%20Transactions.PNG)

## List of Outstanding Pre-Authorizations

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

## Flagged Transactions Current Month

The following shows all transactions that were rejected by any of the validations made by ATIONET in the authorization process. Either due to lack of balance or rules among other validations.

![Flagged Transactions](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Dashboard/Flagged%20Transactions.PNG)

## Contracts Without Activity

Displays the list of contracts that were never active.

![Contracts Without Activity](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Dashboard/Contracts%20Without%20Activity.PNG)

## Sub-Accounts with Exceptions

This shows all sub-accounts that have something to pay attention to, such as:

1. **Without Identifications:** These are vehicles or drivers that do not have an associated identifier.
2. **With inactive Identification:** Are sub-accounts that have an associated identification that has been deactivated from the portal.
3. **With Suspended Identification:** Sub-accounts that have an identification that has been suspended. **Only ATIONet can suspend an identification**.
4. **With inactive Vehicle/Driver:** These are sub-accounts that have a vehicle or driver that has not been deactivated from the portal.

![Sub-Accounts with Exceptions](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Dashboard/Sub-Accounts%20with%20Exceptions.PNG)

## Recent Transactions

The following shows the last 20 completed transactions. It shows the most relevant data to be able to identify it, in case you need more information about the transaction you can click on the authorization code, that will take you to the view of details of the transaction.

![Recent Transactions](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Dashboard/Recent%20Transactions.PNG)

## Contract Low Balance Listing

Shows the list of contracts with low balance to trade 4 more days. This calculation is based on usage. The **Days Left** column shows the number of days remaining in the contract based on usage analysis. This number is not exact and may vary if the usage pattern changes.

![Contract Low Balance Listing](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Dashboard/Contract%20Low%20Balance%20Listing.PNG)

## Sub-Account Low Balance Listing

Shows the list of sub-accounts containing low balance to trade 4 more days. This calculation is made based on the use of each sub account. The **Days Left** column shows the number of days left in the sub-account based on the usage analysis. This number is not exact and may vary if the usage pattern changes.

![Sub-Account Low Balance Listing](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Dashboard/Sub-Account%20Low%20Balance%20Listing.PNG)

## Last Month Identification Updates

This widget shows the activity of the administration of identifications, shows the number of identifications that were modified grouped by state.

1. **Assigned:** The number of identifications that changed to the **Assigned** state.
2. **Available:** The number of identifications that changed to the **Available** state.
3. **Cancelled:** The number of identifications that changed to **Cancelled** status.
4. **Reported:** The number of identifications that changed to **Reported** status.
5. **Suspended:** The number of identifications that changed to **Suspended** status.

![Last Month Identification Updates](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Dashboard/Last%20Month%20Identification%20Updates.PNG)

## Terminal status

All terminals that are natively connected to ATIONET send a regular message indicating that they are active. If the terminal reported the status in the last 5 hours, the terminal will be shown with the green icon, if not reported in the last 5 hours the icon will be red.
The column **Age** shows the number of minutes since the last time the terminal was reported. 

![Terminal Status](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Dashboard/Terminal%20Status.PNG)

# Favorites

Vehicles, Drivers, Sites and Fleets are entities that may require daily monitoring by certain users. To facilitate this task you can add some of these sections to the list of **Favorites**. Once entered a section to this list, the access is faster and direct, without the need to enter filters each time you want to search.

Once inside the Favorites page, by clicking on the link in the **Type** column, you will be redirected to the detailed view of that section.

If you want to remove a section from the list of Favorites, click on the icon on the right side with the shape of a cross.

![Favorites](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Favorites.PNG)

# Reports
In ATIONET the reports are considered those lists of information that are going to be printed and filed in physical format. When they are printed, ATIONET adds a header with the logo of the subscription automatically.

## Driver
The Driver report can be filtered by driver name/code or by identification.
Once the filter is selected press the ***Print*** button, this will display a popup with the selected information.
The information is displayed in a print-ready format, including the subscription logo and the date and time of report generation.

This popup has a print button that when pressed opens the default print window of the Internet browser.

![Drivers](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Reports/Driver.PNG)

## Transactions
This report shows the list of transactions made, sorted by date. This report has several filters to adjust the search. The first field of the filter panel indicates why the field will sort the list, the field selected in this list will be shown in the first column.

![Transactions](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Reports/Transaction%20Filter.PNG)

Once the filter is selected press the ***Print*** button, this will display a popup with the selected information.
The information is displayed in a print-ready format, including the subscription logo and the date and time of report generation.

This popup has a print button that when pressed opens the default print window of the Internet browser.

![Transactions](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Reports/Transaction.PNG)

## Vehicle
This report shows the list of vehicles. This report has several filters to adjust the search. The first field of the filter panel indicates why the field will sort the list, the field selected in this list will be shown in the first column.

![Vehicles](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Reports/Vehicle%20Filter.PNG)

Once the filter is selected press the ***Print*** button, this will display a popup with the selected information.
The information is displayed in a print-ready format, including the subscription logo and the date and time the report was generated.

This popup has a print button that when pressed opens the default print window of the Internet browser.

![Vehicles](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Reports/Vehicle.PNG)

# Administration
Inside this module you can manage Companies, Merchants, Sites, Identifications, Payment Methods and Users among other things.

## Companies
In ATIONET the term company refers to the entity that owns the fleet. In this section you can see the existing companies with their details, edit them and/or create new companies. To make queries easier, there is a panel of filters at the top.

![Companies](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Companies.PNG)

To create a Company, click the **New** button.

![Companies New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Companies%20New.PNG)

The fields to complete are the following:

* **Tax Payer Id:** Input the company taxpayer identification.
* **Active:** Checkmark to enable/disable the group company.
* **Code:** Input the company unique code.
* **Name:** Input the company name.
* **Automatically Generated:** Checkmark this option to have the **code** automatically generated.
* **Industry:** Select the industry associated to the company.
* **Street 1:** Input the company primary street.
* **Street 2:** Input the company secondary street (if applicable).
* **Zip Code:** Input the company zip code.
* **City:** Input the company city.
* **Country:** Input the company country.
* **State:** Input the company state.
* **Taxpayer Category:** Select the company taxpayer category (if applicable).
* **Contact Name:** Input the company contact name.
* **Contact Email:** Input the company contact email.
* **Phone Number 1:** Input the company primary phone number.
* **Phone Number 2:** Input the company secondary phone number (if applicable).

When you have finished filling in the fields, click the **Save** button.

## Dispersion
In this section you can make current account movements in bulk. In a first view you can filter by contract (as long as it is **Disperse** mode) and see how much balance it has.

![Dispersion](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20Company%20ATIONet/Administraci%C3%B3n/Dispersion%20Vista.PNG)

Once you have clicked on the **Search** button you will have a list of all the subaccounts to which you can disperse balance. Select the corresponding subaccounts, click on **Bulk Action** and press **Disperse**.

![New Dispersion](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20Company%20ATIONet/Administraci%C3%B3n/Dispersion%20Nuevo.PNG)

There are 3 ways to massively disperse the balance:
* **Equitable:** The total amount is divided equally among all subaccounts.
* **Balance A:** The balance of the subaccount is equal to the amount deposited.
* **By Amount:** The amount entered into each subaccount is dispersed.

## Drivers
This view lists drivers that have been created. To make queries easier, there is a panel of filters at the top.

![Drivers](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Drivers.PNG)

## External Documentation
This view lists all the external documents uploaded by the Company (through APIs) and the possibility of downloading them. An external document is a document associated with an operation performed externally to ATIONET.

![External Documentation](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20Company%20ATIONet/Administraci%C3%B3n/Documentos%20Externos%20Lista.PNG)

## Fleet
At ATIONET, the fleet refers to the group of vehicles within a Company. In this section you can see the existing fleets, edit them and/or create new ones.

![Fleet](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20Company%20ATIONet/Administraci%C3%B3n/Flotas.PNG)

To create a fleet, click the **New** button.

![New Fleet](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20Company%20ATIONet/Administraci%C3%B3n/Flotas%20Nueva.PNG)

The fields to complete are the following:
* **Code:** Enter the unique code of the fleet.
* **Automatically Generated:** Check this option to have the code generated automatically.
* **Name:** Enter the name associated with the fleet.

<br>

## Notifications
In this section each user can select their own notifications to be received either by email or sms.

### Company Notifications
In this section company users can configure their own notifications (inside their company profiles in ATIONet).

![Notification Company](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Notification%20Company.PNG)

1. ***Contract***
   * **Contract balance low notification:** Get a notification when a contract balance is low.
   * **Contract balance empty notification:** Get a notification when a contract has no balance.
   * **Percent Credit Notification:** Get a notification when a percent credit is reached (click on the pencil to configure the percent).
   * **Low amount balance:** Get a notification when a balance amount is reached (click on the pencil to configure the amount).
   * **Company Contract Deposit:** Get a notification when a deposit to a contract is detected.
2. ***Billing***
   * **External Charges:** Get a notification when external charges were detected.
3. ***Transactions***
   * **Transaction Exception:** Get a notification when an exception is detected.
   * **Non-Blocking Rules Authorization:** Get a notification when a non-blocking rule authorization was detected.
   * **Identification Enabled/Disabled:** Get a notification when an identification was enabled/disabled.
   * **Requested Identifications:** Get a notification when an identification request was detected.
   * **Transaction Rejected:** Get a notification when a rejected transaction was detected.
   * **Disputed Transactions:** Get a notification when a disputed transaction was detected.
4. ***Fleet***
   * **Vehicle Odometer Limit:** Get a notification when a vehicle odometer is reached (click the **Vehicle List** button to configure the odometer and select the vehicle associated to the notification).

## Sites
In ATIONET the site represents the service station. This section lists the sites already created, edit them and also create new ones. You can also add taxes to sites directly from the **Options** column. To make queries easier, there is a panel of filters at the top.

![Sites](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Sites.PNG)

To create a site, click the **New** button.

![Sites New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Sites%20New.PNG)

The fields to complete are the following:

* **Merchant:** Select the merchant associated to the site.
* **Code:** Input the unique code associated to the site.
* **Zone:** Select the zone associated to the site.
* **Automatically Generated:** Checkmark this option to have the **code** automatically generated.
* **Brand:** Select the brand associated to the site.
* **Language:** Select the language associated to the site.
* **Short Name:** Input the short name of the site.
* **Full Name:** Input the full name of the site
* **Street 1:** Input the site primary street.
* **Street 2:** Input the site secondary street.
* **Industry:** Select the industry associated to the site.
* **Time Zone:** Select the time zone associated to the site.
* **Zip Code:** Input the site zip code.
* **City:** Input the site city.
* **Country:** Input the site country.
* **State:** Input the site state.
* **Phone Number 1:** Input the site primary phone number.
* **Phone Number 2:** Input the site secondary phone number.
* **Require Fuel Mapping:** Checkmark this option if specific fuel codes need to be configured for the site (if not, [ATIONet Master Fuel Codes](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/C%C3%B3digos%20Maestros%20de%20Combustible.PNG) will be used).
* **Recipient Emails:** Input the email addresses associated to the site (they will receive the billing statements for the site).
* **Latitude:** Input the latitude of the site.
* **Longitude:** Input the longitude of the site.
* **Currency:** Select the currency associated to the site.

<br>

## Users
In this section you can view, create or edit users for the Network. You can edit them by clicking on the pencil icon in the options column, enable/disable a user by clicking on the padlock icon and reset the password with the star icon.

![Users](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Users.PNG)

To create a User, click the **New** button.

![Users New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Users%20New.PNG)

The fields to complete are the following:

* **User Mail:** The user's email address.
* **Name:** The user's name.
* **Social Security:** The user's document.
* **Street 1:** The street where the user resides.
* **Street 2:** Another street of reference, as it can be the one of the corner.
* **Country:** The user's country.
* **State:** The state of the user's country.
* **Zip Code:** The postal code of the locality where the user resides.
* **Phone Number 1:** The user's phone.
* **Phone Number 2:** The user's other phone if available.

## Vehicle
This view lists all vehicles that have been created. Remember that it is not mandatory to load vehicles in order to operate, it is only necessary if you decide to associate the identifications to vehicles. To make queries easier, there is a panel of filters at the top.

![Vehicles](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Vehicles.PNG)

Under the **Options** column you can:

* **Assign Identification:** Assign/Unassign identifications to the vehicle.  
* **Renew Identification:** Renew the identification associated to the vehicle.
* **Favorites:** Add the vehicle to the **favorites** module.

## Vehicle Classes

The fields to complete are the following:
* **Type:** Select the vehicle type associated with the vehicle class.
* **Theoretical consumption (Distance * Volume):** Enter the theoretical consumption associated with the vehicle class.
* **Make:** Enter the make associated with the vehicle class.
* **Model:** Enter the model associated with the vehicle class.
* **Minimum Mileage:** Enter the minimum mileage associated with the vehicle class.
* **Maximum mileage:** Enter the maximum mileage associated with the vehicle class

## Vouchers
Inside this section you can view a list of all vouchers created by companies. To make queries easier, there is a panel of filters at the top.

![Vouchers](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Vouchers.PNG)

# Fleets
Inside this module you can manage Company and Merchant Contracts, Concepts, Contingencies and Transactions among other things.


## Company Contracts
In ATIONET the term company refers to the entity that manages the fleet. In this section you can create, edit or consult all company contracts. To make queries easier, there is a panel of filters at the top.

![Company Contracts](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Company%20Contracts.PNG)

To create a company contract, click the **New** button.

![Company Contracts New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Company%20Contracts%20New.PNG)

The first step to create a new contract is filling out the general information:

* **Active:** Checkmark this option to enable/disable the contract.
* **Code:** Input the code associated to the contract.
* **Company:** Select the company associated to the contract
* **Reactivation amount:** Input the minimum amount required for automatic reactivation (if the contract is disabled and a deposit was made for that amount or higher).
* **Description:** Input the description of the contract.
* **Start Date:** Input the starting date of the contract.
* **Duration:** Input the duration of the contract.
* **Current Account Mode:** Select the current account mode associated to the contract (Product or Money).
* **Currency:** Select the currency associated to the contract (this option is only enabled if the **current account mode** is **Money**).
* **Mode:** Select the contract mode (Credit, Debir or Cash).
* **Limit:** Input the credit limit associated to the contract.
* **Balance Mode:** Select the balance mode associated to the contract:
	* ***Disperse:*** The balance is managed on a sub-account level.
	* ***Do not Disperse:*** The balace is managed on a contract level.
	* ***Auto Fill:*** There is no balance.
* **Site Validation:** Checkmark this option to enable/disable site validation (the contract can only operate within the sites assigned).
* **Validate Fuels:** Checkmark this option to enable/disable fuel validation (the contract can only operate with fuels assigned).
* **Use Rack Prices:** Checkmark this option to enable/disable the usage of rack prices (the contract will only use rack prices when there are no prices configured in the contract).
* **Validate Programs:**
* **Subsidized Values:**

Once the general information is completed, you have different tabs to configure:

1. **Fuels:** Select the fuels associated to the contract.

![Company Contract New - Fuels](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Company%20Contracts%20New%20-%20Fuels.PNG)

2. **Sites:** Select the sites associated to the contract.

![Company Contract New - Sites](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Company%20Contracts%20New%20-%20Sites.PNG)

3. **Prices:** Configure prices associated to the contract.

![Company Contract New - Prices](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Company%20Contracts%20New%20-%20Prices.PNG)

* ***Fuel:*** Select the fuel associated to the price.
* ***Value:*** Input the price value.
* ***Site:*** Select the site associated to the price.
* ***Date From:*** Input the starting date of the price.
* ***Time From:*** Input the starting time of the price.
* ***Date To:***  Input the ending date of the price.
* ***Time To:*** Input the ending time of the price.

4. **Modifiers:** Configure modifiers associated to the contract.

![Company Contract New - Modifiers](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Company%20Contracts%20New%20-%20Modifiers.PNG)

* ***Description:*** Input the modifier description.
* ***Class:*** Select the modifier class (Discount or Recharge).
* ***Type:*** Select the modifier type (Percentual, Fixed per Transaction or Fixed per Unit).
* ***Value:*** Input the modifier value.
* ***Fuel:*** Select the fuel associated to the modifier.
* ***Site:*** Select the site associated to the modifier.
* ***Date From:*** Input the starting date of the modifier.
* ***Time From:*** Input the starting time of the modifier.
* ***Date To:***  Input the ending date of the modifier.
* ***Time To:*** Input the ending time of the modifier.

5. **Billing:** Configure the billing process associated to the contract.

![Company Contract New - Billing](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Company%20Contracts%20New%20-%20Billing.PNG)

* ***Process Billing Type:*** Select the process billing type associated to the contract (EdiFactMx is for Mexico client only)
* ***Active:*** Checkmark this option to enable/disble the billing process.
* ***Due Days:*** Input the amount of expiration days associated to the statement.
* ***Periodicity:*** Input the frequency in which statements are generated.
* ***Manual:*** Checkmarck this option to enable/disable the manual process of the billing process.
* ***Charges Deduct Balance from Accounts:*** Checkmark this option to enable/disable ATIONet from automatically substracting concepts from accounts balances.
* ***Separate Charges Document:*** Checkmark this option to enable/disable ATIONet from separating each concept associated to the statement.
* ***Recipient Emails:*** Input the emails addresses that will receive the statements.
* ***Tax Payer Id:*** Input the tax payer id associated to the statement.
* ***Name:*** Input the name associated to the statement.
* ***Street 1:*** Input the primary street associated to the statement.
* ***Street 2:*** Input the secobndary street associated to the statement.
* ***Zip Code:*** Input the zip code associated to the statement.
* ***City:*** Input the city associated to the statement.
* ***Country:*** Input the country associated to the statement.
* ***State:*** Input the state associated to the statement.

6. **Concepts:** Select the concept associated to the contract. For more information on concepts access [here]().

![Company Contracts New - Concepts](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Company%20Contracts%20New%20-%20Concepts.PNG)
	
7. **Documents:** Upload any document associated to the contract (for example: a pdf of the actual physical contract).

![Company Contracts New - Documents](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Company%20Contracts%20New%20-%20Documents.PNG)

8. **Blocks:** Configure the blocks associated to the contract

![Company Contracts New - Blocks](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Company%20Contracts%20New%20-%20Blocks.PNG)

* ***Type:*** Select **Fixed** to block operation on specific dates, or select **Fixed** to block operation on specific days of every month. 
* ***Date From:*** Input the starting date of the block.
* ***Date To:*** Input the ending date of the block.
* ***Day From:*** Input the starting day of every month for the block.
* ***Day To:*** Input the ending day of every moth for the block.

9. **Over Limit:** Configure the overlimits associated to the contract.

![Company Contracts New - Over Limit](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Company%20Contracts%20New%20-%20Over%20Limit.PNG)

* ***Type:*** Select the over limit type (Percent or Amount).
* ***Value:*** Input the value associated to the over limit.
* ***Date From:*** Input the starting date of the over limit.
* ***Date To:*** Input the ending date of the over limit.

10. **Programs:**
11. **Subsidies:**
12. **Custom Fields:**

When you have finished filling in the fields, click the **Save** button.

## Company Current Accounts
The Company Current Accounts section is the view of available balance of sub-account and/or contracts, and also the view of all movements of sub-accounts and/or contracts.

For easier quieries, there is a filter panel available. The first option in the filter panel is the type of report:

![Company Current Accounts](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Company%20Current%20Accounts.PNG)

1. **Contract List:** This option lists all contracts with their respective balance, but does not give details of the movements.

![Company Current Accounts - Contract List](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Company%20Current%20Accounts%20-%20Contract%20List.PNG)

2. **Contract Movements:** This option lists all contract movements.

![Company Current Accounts - Contract Movements](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Company%20Current%20Accounts%20-%20Contract%20Movements.PNG)

3. **Sub-account List:** This option lists all sub-accounts with their respective balances, but does not give details of the movements.

![Company Current Accounts - Sub-Account List](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Company%20Current%20Accounts%20-%20Sub-Account%20List.PNG)

4. **Sub-account Movements:** This view lists all sub-account movements.  

![Company Current Accounts - Sub-Account Movements](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Company%20Current%20Accounts%20-%20Sub-Account%20Movements.PNG)

## Declined Transactions
ATIONet separates unauthorized transactions into 2 sections: [Exceptions](#exceptions) and **Declined Transactions**.

Declined Transactions are those that managed to pass ATIONET's hard authentications, but were rejected by other validations such as an unsatisfied rule or balance validation.

![Declined Transactions](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Declined%20Transactions.PNG)

In this view, at the start you can filter by the type of rejection. The types of rejections available are as follows:

![Declined Transactions Filters](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Declined%20Transactions%20Filters.PNG)

## Dispensed Transactions
In this section you can view all transactions that had fuel dispensed.

![Dispensed Transactions](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Dispensed%20Transactions.PNG)

## Disputed Transactions
Disputed transactions are those that either party (Merchant or Company) claims to be unaware of.

In this section you can consult the disputed transactions, listed by code, date, reason, state, transaction number, company, site. There is also the commentary of the company, the merchant and the network.

![Disputed Transactions](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Disputed%20Transactions.PNG)

## Exceptions
ATIONet separates unauthorized transactions into 2 sections: **Exceptions** and [Declined transactions](#declined-transactions). Exceptions are those transactions that did not pass the hard validations of the system or those that are detected as possible frauds.

![Exceptions](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Exceptions.PNG)

In this view, at the start you can filter by the type of exception. The types of exceptions available are as follows:

![Exceptions Filters](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Exceptions%20Filters.PNG)

Some transactions remain in **Review** status in some situations, such as when more than authorized is sent (due to a controller or POS error). In these cases it is necessary to approve or reject the transaction using one of the two icons to the right of each record.

## Fast Track Configuration
A Fast Track in ATIONet is a way to configure a one-use-only authorization for an specific amount to an already existing fleet sub-account. In this sections you can configure up to 10 Custom Fields for Fast Tracks.

![Fast Track Configuration](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Fast%20Track%20Configuration.PNG)

When you have finished filling in the fields, click the **Save** button.

## Outstanding Authorizations
In ATIONET outstanding authorizations are those transactions that have not yet received the completion transaction, but have been pre-authorized. The information seen in this view are dispatches that are currently underway. If for some reason there are old pre-authorizations, it is likely that the POS did not send the completion transaction or the cancellation transaction if the dispatch was not completed.

Please note that at the time of pre-authorization, ATIONET froze the amount of the authorization of the current account for the sub-account associated. This view presents all the fields necessary to identify the transaction and the sub-account. If you need to see more details, clicking on the authorization code will take you to the transaction details view.

![Outstanding Authorization](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Outstanding%20Authorization.PNG)

If old pending transactions appear and you are sure it is not an ongoing dispatch, you may cancel them and return the balance to the current account.
To do so there are 2 ways: individually, by clicking on the **X** icon to the right side of the grid, or massively by selecting the transactions, displaying the **Batch Actions** menu and selecting **Cancel**. This will cancel the transactions and return the balance reserved to each of the current accounts. (for more details on the transaction flow refer to this [document](AN-Transaction_Flows-TechGuide.md))


## Requested Identifications

From this section you will be able to confirm receipt of requests for identifiers made, to complete the request process. Please note that the only orders you can confirm are those that have already been marked as **Delivered**.
To change the status of the requested badges, click the **Bulk Action** button and select the option **Confirm badge delivery**.

## Rules
In ATIONET the rules refer to the limits that can be configured. Within this view you can consult, create or edit rules. There are different types of rules: Fee, Date Range, Location, Fuel, Transaction Limit, Days-Hour, Request, Dry Transaction Limit and Dry Fee Limit.

Note that all the rules can be **Non-Blocking**, which means that ATIONET will not reject the transaction, even if the configured parameters are met.

![Rules](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Reglas.PNG)

1. **Quota:** In this rule you can limit the number of transactions, volume and/or money on a specific frequency.

![Rules - Quota](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Rules%20-%20Quota.PNG)

2. **Date Range:** In this rule you can limit the transactions to be made in specific date and time ranges.

![Rules - Date Range](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Rules%20-%20Date%20Range.PNG)

3. **Location:** In this rule you can limit transactions to specific sites and zones.

![Rules - Location](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Rules%20-%20Location.PNG)

4. **Fuel:** In this rule you can limit the transactions to be made for specific fuels and fuel master groups.

![Rules - Fuel](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Rules%20-%20Fuel.PNG)

5. **Limit per Transactions:** In this rule you can limit the volume of each transaction and/or the money.

![Rules - Limit Per Transactions](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Rules%20-%20Limit%20Per%20Transaction.PNG)

6. **DaysTime:** In this rule you can limit transactions to specific days and hours of the week.

![Rules - DaysTime](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Rules%20-%20DaysTime.PNG)

7. **Prompting:** In this rule you can configure the request for information for transactions, such as driver/vehicle ID, driver/vehicle PIN, etc.

![Rules - Prompting](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Rules%20-%20Prompting.PNG)

8. **Dry Transaction Limit:** In this rule you can limit the money of the transactions of each SKU.

![Rules - Dry Transaction Limit](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Rules%20-%20Dry%20Transaction%20Limit.PNG)

9. **Dry Quota Limit:** In this rule you can limit the transaction money in a specific frequency.

![Rules - Dry Quota Limit](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Rules%20-%20Dry%20Quota%20Limit.PNG)

After configuring any type of rule, the last step is to associate the rule with an entity. Rules can be applied to: Fleets, Vehicles, Drivers, Sites and Fuels.

![Reglas - Asociación](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20ATIONet/Flotas/Reglas%20-%20Aplicacion.PNG)

## Transactions
The transaction view is one of the most important in ATIONet. In this view you can see all successful transactions.

The filter panel has all these fields available:

![Trasactions - Filter](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Transactions%20-%20Filter.PNG)

* **Authorization Code:** Input the authorization code associated to the transaction.
* **Shift Number:** Input the shift number associated to the transaction.
* **Vehicle:** Select the vehicle associated to the transaction.
* **Driver:** Select the driver associated to the transaction.
* **Merchant:** Select the merchant associated to the transaction.
* **Site:** Select the site associated to the transaction.
* **Terminal/Controller:** Select the terminal associated to the transaction.
* **Fuel:** Select the fuel associated to the transaction.
* **Program:** Select the fleet program associated to the transaction.
* **Contract:** Select the company contract associated to the transaction.
* **Invoice Number:** Input the invoice number associated to the transaction.
* **Date Type:** Select the date type associated to the transaction (Controller, Host, Subscription or Site).
* **Date From / Date To:** Input the starting and ending dates associated to the transaction.
* **Time From / Time To:** Input the starting and ending times associated to the transaction.
* **Mode:** Select the transaction mode (Contingency, Offline or Standard).
* **Show Zero Completions:** Checkmark this option to view transactions that no fuel was dispatched.

Once you have filtered, press ***Search*** and it will list the transactions that comply with the filter.

![Transactions](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Transactions.PNG)

If you want to see the transaction detail, click on the **Authorization Code** and this will take you to a detail view of the transaction.

![Transaction Details](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Transaction%20Details.PNG)
 
## Transactions by Driver
In this view you can see the transactions grouped by the driver who made them. The buttons at the top left are for printing the table or creating an Excel file from the table, respectively.

![Transactions by Driver](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Transactions%20by%20Driver.PNG)

## Transactions by Fleet
In this view you can see the transactions grouped by the fleet who made them. The buttons at the top left are for printing the table or creating an Excel file from the table, respectively.

![Transactions by Fleet](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Transactions%20by%20Fleet.PNG)

## Transactions by Site
In this view you can see the transactions grouped by the site where they were made. The buttons at the top left are for printing the table or creating an Excel file from the table, respectively.

![Transactions by Site](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Transactions%20by%20Site.PNG)

## Transactions by Vehicle
In this view you can see the transactions grouped by the vehicle who made them. The buttons at the top left are for printing the table or creating an Excel file from the table, respectively.

![Transactions by Vehicle](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Transactions%20by%20Vehicle.PNG)

# Billing

## Billed Items
In this section you can view concepts applied for each statement.

![Billed Items](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Billing/Billed%20Items.PNG)

## Billing Documents
In this section you can view all register status for billing documents requested. Possible status are: Pending, Processing, Finished or Finished with errors.

![Billing Documents](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Billing/Billing%20Documents.PNG)

## Billing Processes
In this section you can manually execute a billing process or view all billing processes status. Possible processing status are: Pending, Confirmed, Error or Confirmed With Errors.

![Billing Processes](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Billing/Billing%20Processes.PNG)

To manually execute a billing process, click the **Run Process** button. This will automatically generate a billing process register. Take into consideration that this will only impact contracts that have the billing process configured as **Manual**.

## Statements
In this section you can view and download statements from your Network. You can also generate the .pdf statements one by one, or inside the **Bulk Action** generate a .pdf package.

![Statements](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Billing/Statements.PNG)

# Configuration

## Company Contracts Classifications
In this section you can configure custom company contract classifications.

![Company Contracts Classifications](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Configuration/Company%20Contracts%20Classifications.PNG)

# Logs

## Audit Log
In this section you can view a list of all actions made by all users. There is a filter panel on the top to make queries easier.

![Audit Log](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Audit%20Log.PNG)
