![ationetlogo](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/ATIOnetLogo_250x70.png)

|**Document Information**|.|
|--- |--- |
|**File:**|ATIONET_Merchant_User_Manual-EN.MD|
|**Doc Version:**|1.0|
|**Release Date:**|24, Jan 2022|
|**Author:**|ATIONET LLC|


|**Change Log**|||
|--- |--- |--- |
|**Ver.**|**Date**|**Change Summary**|
|1.0|24/Jan/2022|- Initial version


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
	- [Terminal](#terminal)
- [My Preferences](#my-preferences) 
- [Navigation Menu](#navigation-menu)
	- [DashBoard](#dashboard)
	  - [Health Status](#dashboard)
	  - [Units/Months](#unitsmonths)
	  - [Today’s Transactions](#todays-transactions)
	  - [List of Outstanding Pre-Authorizations](#list-of-outstanding-pre-authorizations)
	  - [Flagged Transactions Current Month](#flagged-transactions-current-month)
	  - [Recent Transactions](#recent-transactions)
	  - [Contract Low Balance Listing](#contract-low-balance-listing)
	  - [Sub-Account Low Balance Listing](#sub-account-low-balance-listing)
	  - [Last Month Identification Updates](#last-month-identification-updates)
	  - [Terminal status](#terminal-status)
	- [Favorites](#favorites)
	- [Reports](#reports)
	  - [Sites](#sites)	
	  - [Transactions](#transactions)
	- [Administration](#administration)
	  - [External Documentation](#external-documentation))	
	  - [Fuel](#fuel)
	  - [Notifications](#notifications)
	  - [Sites](#sites)
	  - [Terminal](#terminal)
	  - [Users](#users)
	- [Fleets](#fleets)
	  - [Contingency](#contingency)
	  - [Declined Transactions](#declined-transactions)
	  - [Dispensed Transactions](#dispensed-transactions)
	  - [Exceptions](#exceptions)
	  - [Outstanding Authorizations](#outstanding-authorizations)
	  - [Transactions](#transactions)
	  - [Transactions by Site](#transactions-by-site)	  - 
	- [Billing](#billing)
		- [Billed Items](#billing-items)
		- [Billing Documents](#billing-documents)
		- [Charges Documents](#changes-documents)
		- [External Charge](#external-charge)
		- [Merchant Charge](#merchant-charge)
		- [Statements](#statements)
- [Inventory](#inventory)
	- [Inventory-Charts](#inventory-charts)
	- [Inventories](#inventories)
	- [Deliveries](#deliveries)
	- [Physical Reconciliations](#physical-reconciliations)



# Overview

ATIONet is based on the premise that online communications between sites and the web portal are possible, however, it provides solid contingency procedures in the event of a communication error.

The ATIONet platform is a fleet management service with an innovative and unique market offer. Cloud processing, 100% web-based, multi-user access, data availability and sharing, instant updates, security, automatic back-up and paperwork reduction.

ATIONet is a web portal for fleet service companies that allows the processing of transactions from any point of sale application through a simple and reliable interface. 

ATIONet can be installed at any service station with one or multiple fleet service programs. The web portal allows fleet managers full access to their vehicle information.

ATIONet makes it possible for the fleet manager to operate, monitor, change and edit fleet information in real time.



# Definitions

## Contract
The contract is the relationship that exists between the Network and the client, in which it is oriented, for example, if it will be of quantity or volume, the price at which the fuel is going to be sold, in which places it can be loaded, among others. .

## Subaccount
Each time an identifier is associated with a vehicle or driver, a sub-account is created. The subaccount is ultimately who is going to have a current account, the subaccount is going to be able to receive deposits of money or product. The rules also affect the subaccount.
The subaccounts depend hierarchically on the contract.

## Company
In ATIONET the company refers to the entity that owns the fleet. It is the one that manages the vehicles, the drivers and the rules of the fleet.

## Identifier
The identifier is the physical means used by ATIONET to identify a vehicle or driver. ATIONET supports various types of identifiers, such as card, TAG, chip, ATIONET card, manual input, barcode and iButton. When an identifier is associated with a vehicle or driver, a subaccount is created.

## Site
The Site represents the service station. A site is assigned a terminal/controller and can also have location rules associated with it.

## Vehicle
The vehicles can be associated or grouped by a fleet, they can have associated rules and when they are related to an identifier, a subaccount is created. They may also have an associated driver.

## Driver
The driver in ATIONET is the person who identifies himself as the driver. If this driver is assigned an identifier, a subaccount is created. Drivers can also have rules associated with them.

## Terminal
The terminal (or controller) is the representation of the dispenser controller, which must be parameterized in a particular way depending on the type of terminal. The terminals handled by ATIONET are: ATIO-NanoCPI, ATIO-Standalone, ATIO-CG, VF-Sapphire, VF-Commander, VF-Ruby, ControlGas, among others.

# Navigation Menu

ATIONet has a quick access menu located on the left side of the website. From this menu you can access different options. The menu is divided into 9 sections. (Dashboard, Favorites, Reports, Administration, Fleets, Billing, Notifications, Configuration and Logbook).


# My Preferences
Inside this section each user can customize their portal preferences.



1. **Default Role:** Select the default role when loggin in.

![Default Role](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/My%20Preferences/Default%20Role.PNG)

2. **Profile Picture:** Change the profile picture of your user.

![Profile Picture](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/My%20Preferences/Profile%20Picture.PNG)

3. **Change Password:** Change the password for your user.

![Change Password](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/My%20Preferences/Change%20Password.PNG)

To edit your password, click the ***change password*** link.

![Change Password New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/My%20Preferences/Change%20Password%20New.PNG)

4. **Widgets Configuration:** Select which widgets to show on your dashboard.

![Widget Configuration](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/My%20Preferences/Widget%20Configuration.PNG)

# Board
The Dashboard is a page where you have a global vision of the operation of your Company. The dashboard has specific widgets that will help you make preventive or corrective decisions based on the information and data they display. The data displayed on the Dashboard is real-time data and some of the widgets update automatically.

These can be removed or added according to the user's needs in the **My Preferences** option. They can also be placed on the board according to the level of visibility that you want to give each one.

## Overall status
This widget is very important when starting up the Network. This widget gives us information about the parameters that we need to configure to be operational. It notifies us when, for example, we do not have vehicles or identifications created among other parameters.
This widget can display **Warnings** (yellow icon) when network operation is not in play, but displaying a red cross indicates that the network is not operational.

![General Status](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20User%20ATIONet/Board/Status%20General.PNG)

## Units/Month
The "Units/Month" indicates the amount of each fuel dispensed in the last month. The last month is the last 30 days from the day of the date. This widget has the ability to filter by Site, City and Fleet. You must select the filter and then enter the value to filter by. This last field is of type "autocomplete".

![Units/Months](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20User%20ATIONet/Board/Units-Month.PNG)

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

The following shows all transactions that were rejected by any of the validations made by ATIONet in the authorization process. Either due to lack of balance or rules among other validations.

![Flagged Transactions](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Dashboard/Flagged%20Transactions.PNG)

## Contracts Without Activity

Displays the list of contracts that were never active.

![Contracts Without Activity](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Dashboard/Contracts%20Without%20Activity.PNG)

## Recent Transactions

The following shows the last 20 completed transactions. It shows the most relevant data to be able to identify it, in case you need more information about the transaction you can click on the authorization code, that will take you to the view of details of the transaction.

![Recent Transactions](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Dashboard/Recent%20Transactions.PNG)

## Contract Low Balance Listing

Shows the list of contracts with low balance to trade 4 more days. This calculation is based on usage. The **Days Left** column shows the number of days remaining in the contract based on usage analysis. This number is not exact and may vary if the usage pattern changes.

![Contract Low Balance Listing](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Dashboard/Contract%20Low%20Balance%20Listing.PNG)

## Last Month Identification Updates

This widget shows the activity of the administration of identifications, shows the number of identifications that were modified grouped by state.

1. **Assigned:** The number of identifications that changed to the **Assigned** state.
2. **Available:** The number of identifications that changed to the **Available** state.
3. **Cancelled:** The number of identifications that changed to **Cancelled** status.
4. **Reported:** The number of identifications that changed to **Reported** status.
5. **Suspended:** The number of identifications that changed to **Suspended** status.

![Last Month Identification Updates](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Dashboard/Last%20Month%20Identification%20Updates.PNG)

## Terminal status

All terminals that are natively connected to ATIONet send a regular message indicating that they are active. If the terminal reported the status in the last 5 hours, the terminal will be shown with the green icon, if not reported in the last 5 hours the icon will be red.
The column **Age** shows the number of minutes since the last time the terminal was reported. 

![Terminal Status](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Dashboard/Terminal%20Status.PNG)


# Favorites

Vehicles, Drivers, Sites and Fleets are entities that may require daily monitoring by certain users. To facilitate this task you can add some of these sections to the list of **Favorites**. Once entered a section to this list, the access is faster and direct, without the need to enter filters each time you want to search.

Once inside the Favorites page, by clicking on the link in the **Type** column, you will be redirected to the detailed view of that section.

If you want to remove a section from the list of Favorites, click on the icon on the right side with the shape of a cross.

![Favorites](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Favorites.PNG)

# Reports
In ATIONET the reports are considered those lists of information that are going to be printed and filed in physical format. When they are printed, ATIONET adds a header with the logo of the subscription automatically.

## Sites
This report shows the list of sites created by the Network, sorted by code. At the top you can filter by site, or press the ***Print*** button and get a complete list of all Merchant sites.

![Sites](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20Merchant%20ATIONet/Reportes/Sitios.PNG)

This pop-up window has a print button that when clicked opens the default print window of the Internet browser.

## Transactions report
This report shows the list of transactions made, sorted by date. This report has several filters to adjust the search. The first field of the filter panel indicates why the field will sort the list, the field selected in this list will be shown in the first column.

![Transactions](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Reports/Transaction%20Filter.PNG)

Once the filter is selected press the ***Print*** button, this will display a popup with the selected information.
The information is displayed in a print-ready format, including the subscription logo and the date and time of report generation.

This popup has a print button that when pressed opens the default print window of the Internet browser.

![Transactions](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Reports/Transaction.PNG)

<br>

[Back to top](#contents)  :arrow_up:
