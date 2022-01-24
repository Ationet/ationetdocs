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


# Administration
Within this module you will be able to manage Fuels, Notifications, Sites and Terminals among other things.

## External Documentation
This view lists all the external documents uploaded by the Company (through APIs) and the possibility of downloading them. An external document is a document associated with an operation performed externally to ATIONET.

![External Documentation](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20Company%20ATIONet/Administraci%C3%B3n/Documentos%20Externos%20Lista.PNG)

## Fuels
This view lists the fuel allocations and their respective code for all sites that have the **Fuel Required Mapping** option enabled (this option is used if specific fuel codes are required to be used, otherwise ATIONET will validate against the [Fuel Codes Master Fuel](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/C%C3%B3digos%20Maestros%20de%20Fuel.PNG)). To facilitate queries, there is a filter panel at the top.


## Notifications
In this section each user can select their own notifications to be received either by email or sms.

## Sites
In ATIONET the site represents the service station. This section lists the sites already created, edit them and also create new ones. You can also add taxes to sites directly from the **Options** column. To make queries easier, there is a panel of filters at the top.

![Sites](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Sites.PNG)

## Terminals / Controllers
This section lists all the terminals/controllers created by the Network. The terminal is the site's point of sale and the controller manages the dispensers. To facilitate queries, there is a filter panel at the top.

![Terminales](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20Merchant%20ATIONet/Administraci%C3%B3n/Terminales-Controladores.PNG)


## Users
In this section you can view, create or edit users for the Network. You can edit them by clicking on the pencil icon in the options column, enable/disable a user by clicking on the padlock icon and reset the password with the star icon.

![Users](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Users.PNG)

To create a User, click the **New** button.

![Users New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Users%20New.PNG)

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

<br>

* **Role:** The role that the new user will assume.
* **Entity:** The entity assigned to the user.

When you have finished filling in the fields, press the **Save** button.

# Fleets
Within this module you can manage Contingencies, Transactions, Exceptions and Rejections among other things.

## Contingency
In ATIONet a contingency is a manually entered transaction. In this section you can consult and create contingencies. Take into account that contingencies are transactions without a pre-authorization.

![Contingency](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Contingencies.PNG)

To create a contingency, click the **New** button.

![Contingencies New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Contingencies%20New.PNG)

The fields to complete are the following:

* **Date:** Input the date of the contingency.
* **Time:** Input the time of the contingency.
* **Site:** Select the site associated to the contingency.
* **Terminal/Controller:** Select the terminal/controller associated to the contingency.
* **Primary Account:** Select the primary sub-account associated to the contingency.
* **Secondary Account:** Select the secondary sub-account associated to the contingency.
* **Fuel:** Select the fuel associated to the contingency.
* **Dispensed Volume:** Input the volume associated to the contingency.
* **Unit Price:** Input the unit price associated to the contingency.
* **Dispensed Amount:** Input the amount associated to the contingency.
* **Shift Number:** Input the shift associated to the contingency.
* **Pump Number:** Input the pump associated to the contingency.
* **Odometer:** Input the vehicle's odometer associated to the contingency.
* **Engine Hours:** Input the vehicle's engine hours associated to the contingency.
* **Driver Id:** Input the the driver's identifier associated to the contingency.
* **Vehicle Id:** Input the vehicle's identifier associated to the contingency.
* **Attendant:** Input the attendant associated to the contingency.
* **Pump Side:** Input the pump side associated to the contingency.
* **Miscellaneous:** Input the vehicle's miscellaneous associated to the contingency.
* **Invoice Number:** Input the invoice number associated to the contingency.
* **Purchase Order Number:** Input the purchase orden number associated to the contingency.

When you have finished filling in the fields, click the **Save** button.


## Declined Transactions
ATIONet separates unauthorized transactions into 2 sections: [Exceptions](#exceptions) and **Declined Transactions**.

Declined Transactions are those that managed to pass ATIONET's hard authentications, but were rejected by other validations such as an unsatisfied rule or balance validation.

![Declined Transactions](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Declined%20Transactions.PNG)

In this view, at the start you can filter by the type of rejection. The types of rejections available are as follows:

![Declined Transactions Filters](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Declined%20Transactions%20Filters.PNG)

## Disputed Transactions
Disputed transactions are those that either party (Merchant or Company) claims to be unaware of.

In this section you can consult the disputed transactions, listed by code, date, reason, state, transaction number, company, site. There is also the commentary of the company, the merchant and the network.

![Disputed Transactions](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Disputed%20Transactions.PNG)

## Exceptions
ATIONet separates unauthorized transactions into 2 sections: **Exceptions** and [Declined transactions](#declined-transactions). Exceptions are those transactions that did not pass the hard validations of the system or those that are detected as possible frauds.

![Exceptions](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Exceptions.PNG)

In this view, at the start you can filter by the type of exception. The types of exceptions available are as follows:

![Exceptions Filters](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Exceptions%20Filters.PNG)

Some transactions remain in **Review** status in some situations, such as when more than authorized is sent (due to a controller or POS error). In these cases it is necessary to approve or reject the transaction using one of the two icons to the right of each record.

## Outstanding Authorizations
In ATIONET outstanding authorizations are those transactions that have not yet received the completion transaction, but have been pre-authorized. The information seen in this view are dispatches that are currently underway. If for some reason there are old pre-authorizations, it is likely that the POS did not send the completion transaction or the cancellation transaction if the dispatch was not completed.

Please note that at the time of pre-authorization, ATIONET froze the amount of the authorization of the current account for the sub-account associated. This view presents all the fields necessary to identify the transaction and the sub-account. If you need to see more details, clicking on the authorization code will take you to the transaction details view.

![Outstanding Authorization](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Outstanding%20Authorization.PNG)

## Transactions
The transaction view is one of the most important in ATIONet. In this view you can see all successful transactions.

The filter panel has all these fields available:

![Trasactions - Filter](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Transactions%20-%20Filter.PNG)

* **Site:** Select the site associated to the transaction.
* **Terminal/Controller:** Select the terminal associated to the transaction.
* **Fuel:** Select the fuel associated to the transaction.
* 
* **Date Type:** Select the date type associated to the transaction (Controller, Host, Subscription or Site).
* **Date From / Date To:** Input the starting and ending dates associated to the transaction.
* **Time From / Time To:** Input the starting and ending times associated to the transaction.
* **Mode:** Select the transaction mode (Contingency, Offline or Standard).

Once you have filtered, press ***Search*** and it will list the transactions that comply with the filter.

![Transactions](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Transactions.PNG)

If you want to see the transaction detail, click on the **Authorization Code** and this will take you to a detail view of the transaction.

![Transaction Details](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Transaction%20Details.PNG)

With the incorporation of Multicurrency, within Transaction Details you will find three new sections: Site Currency, Company Currency and Merchant Currency, which are configurable as explained in the transaction document. [Multicurrency](https://github.com/nuchavez/ationetdocs/blob/master/Multicurrency-EN.MD). 
 

## Transactions by Site
In this view you can see the transactions grouped by the site where they were made. The buttons at the top left are for printing the table or creating an Excel file from the table, respectively.
Within the grid in the Currency column you can see in which currency each transaction is made. If the Multicurrency functionality is enabled, the different currencies will be indicated in the list of transactions according to each one of them.

![Transactions by Site](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Transactions%20by%20Site.PNG)

# Billing

## Billed Items
In this section you can view concepts applied for each statement.

![Billed Items](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Billing/Billed%20Items.PNG)

## Billing Documents
In this section you can view all register status for billing documents requested. Possible status are: Pending, Processing, Finished or Finished with errors.

![Billing Documents](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Billing/Billing%20Documents.PNG)


## Charges Documents
In this section you can view all concepts applied grouped up by statement. If you click on the statement code, it will redirect you to the statement details.

![Charges Documents](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Billing/Charges%20Documents.PNG)

## External Charges
In this section you can upload a receipt associated with an external document. The receipt takes the amount informed in the document and a file/receipt must be attached that supports the information uploaded.

![Cargos Externos](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20Company%20ATIONet/Liquidaci%C3%B3n/Cargos%20Externos.PNG)

To create an external charge, click the **New** button.

![Cargos Externos Nuevo](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Manual%20Usuario%20Company%20ATIONet/Liquidaci%C3%B3n/Cargos%20Externos%20Nuevo.PNG)

The fields to complete are the following:

* **Date:** Enter the date of the external position.
* **External Document:** Select the external document associated with the position.
* **Description:** Enter the description of the external position.
* **Type of Invoice:** Select the type of receipt associated with the charge.
* **Invoice Number:** Enter the receipt number associated with the charge.
* **Electronic Authorization Code:** Enter the electronic authorization code associated with the charge.
* **Expiration date:** Enter the expiration date of the external charge.
* **Currency:** Select the currency of the external charge.
* **Net Amount:** Enter the net amount of the external charge.
* **Tax Exempt:** Check this option if the charge is tax free.

<br>

**Taxes**

* **Tax:** Enter the code or name of the corresponding tax.
* **Type** Enter the corresponding tax type.
* **Amount:** Enter the amouth of the corresponding tax.
* **Mode:** Enter the mode of the corresponding tax.
* **Value:** Enter the value of the corresponding tax.

This view has an approval flow associated with it, where:
* The Company enters the external position and it remains in **New** status (it is allowed to edit or delete it).
* The same Company can change the status to **Approved by the Company** or **Rejected by the Company**.

If the charge is rejected, the flow ends. Instead, if approved, the Network is responsible for reviewing the **external charge** and may likewise approve or reject it.


## Statements
In this section you can view and download statements from your Network. You can also generate the .pdf statements one by one, or inside the **Bulk Action** generate a .pdf package.

![Statements](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Billing/Statements.PNG)


<br>

[Back to top](#contents)  :arrow_up:
