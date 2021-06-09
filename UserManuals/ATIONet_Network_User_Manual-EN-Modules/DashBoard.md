![ationetlogo](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/ATIOnetLogo_250x70.png)

# Contents

- [DashBoard](#dashboard)
	- [Health Status](#health-status)
	- [Units/Months](#unitsmonths)
	- [Today’s Transactions](#todays-transactions)
	- [List of Outstanding Pre-Authorizations](#list-of-outstanding-pre-authorizations)
	- [Flagged Transactions Current Month](#flagged-transactions-current-month)
	- [Contracts Without Activity](#list-of-outstanding-pre-authorizations)
	- [Sub-Accounts with Exceptions](#sub-accounts-with-exceptions)
	- [Recent Transactions](#recent-transactions)
	- [Contract Low Balance Listing](#contract-low-balance-listing)
	- [Sub-Account Low Balance Listing](#sub-account-low-balance-listing)
	- [Last Month Identification Updates](#last-month-identification-updates)
	- [Terminal status](#terminal-status)

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

The following shows all transactions that were rejected by any of the validations made by ATIONet in the authorization process. Either due to lack of balance or rules among other validations.

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

For more details about sub-accounts please consult [this section](#sub-account)

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

All terminals that are natively connected to ATIONet send a regular message indicating that they are active. If the terminal reported the status in the last 5 hours, the terminal will be shown with the green icon, if not reported in the last 5 hours the icon will be red.
The column **Age** shows the number of minutes since the last time the terminal was reported. 

![Terminal Status](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Dashboard/Terminal%20Status.PNG)
