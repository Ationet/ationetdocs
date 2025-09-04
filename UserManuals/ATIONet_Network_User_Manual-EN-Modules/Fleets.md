![ationetlogo](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/ATIOnetLogo_250x70.png)

# Contents

- [Fleets](#fleets)
	- [Attendants](#attendants)
	- [Company Contracts](#company-contracts)
	- [Company Current Accounts](#company-current-accounts)
	- [Concepts](#concepts)
	- [Concept Families](#concept-families)
	- [Contingencies](#contingencies)
	- [Declined Transactions](#declined-transactions)
	- [Dispensed Transactions](#dispensed-transactions)
	- [Disputed Transactions](#disputed-transactions)
	- [Exceptions](#exceptions)
	- [Fast Track Configuration](#fast-track-configuration)
 	- [Fast Track](#Fast-Tracks)
    - [Fleet Workflow Approvals](#Fleet-Workflow-Approvals)
	- [Fraud Alerts](#fraud-alerts)
	- [Fraud Alerts Configuration](#fraud-alerts-configuration)
 	- [Identifications Scheduler](#Identifications-Scheduler)
  	- [Invoice Type](#Invoice-Type)
	- [Merchants Contracts](#merchants-contracts)
	- [Merchant Current Accounts](#merchant-current-accounts)
	- [Outstanding Authorizations](#outstanding-authorizations)
	- [Over Limit](#over-limit)
	- [Programs](#programs)
	- [Requested Identifications](#requested-identifications)
	- [Rules](#rules)
	- [Transactions](#transactions)
	- [Transactions by Driver](#transactions-by-driver)
	- [Transactions by Fleet](#transactions-by-fleet)
	- [Transactions by Site](#transactions-by-site)
	- [Transactions by Vehicle](#transactions-by-vehicle)
 	- [Transactions ERP](#Transactions-ERP)
	- [Uncontrolled Transactions](#uncontrolled-transactions)
 	- [Vouchers](#Vouchers)
  	- [Vouchers - Administration](#Vouchers---Administration)

# Fleets
Inside this module you can manage Company and Merchant Contracts, Concepts, Contingencies and Transactions among other things.

## Attendants

In ATIONet the term attendant refers to the person responsible for dispatching, the one who operates the pumps. In this section you can view, create and edit all the attendants. To facilitate queries, there is a filter panel at the top.

INSERTAR IMAGEN

To create a attendant, click on the **New** button.

INSERTAR IMAGEN

When you have finished filling in the fields, press the **Save** button.

## Company Contracts

In ATIONet the term company refers to the entity that manages the fleet. In this section you can create, edit or consult all the company contracts. To facilitate queries, there is a filter panel at the top.

INSERTAR IMAGEN

To create a company contract, click on the **New** button.

INSERTAR IMAGEN

The first step to create a new contract is to complete the general information:
* **Active:** Check this option to activate/deactivate the contract.
* **Code:** Enter the code associated with the contract.
* **Company:** Select the company associated to the contract.
* **Reactivation Amount:** Enter the minimum amount required for automatic reactivation (if the contract is deactivated and a deposit of that amount or more has been made).
* **Description:** Enter the description of the contract.
* **Start date:** Enter the start date of the contract.
* **Duration:** Enter the desired duration of the contract.
* **Current Account Mode:** Select the current account mode associated with the contract (Product or Amount).
* **Currency:** Select the currency associated to the contract (this option is only enabled if the current account mode is Amount).
* **Mode:** Select the contract mode (Credit, Debit or Cash).
	o If "Credit" is selected, the option to set a limit for the contract in question will be enabled.
* **Balance Mode:** Select the balance mode associated with the contract: - Disperse: The balance is managed at sub-account level.
	o **Non-disperse:** The balance is managed at the contract level.
	o **Auto Fill:** No balance.
* **Distribution Price List:** Select the distribution prices that will be used as long as there are no prices configured in the contract.
* **Apply lower price on Authorization:** When applying this setting the contract will apply the lowest amount of the product involved in the authorized transaction, whether it is in the distribution price list, in the contract, etc.
* **Validate Sites:** Check this option to enable/disable site validation (the contract can only operate within the assigned sites).
* **Validate Fuels:** Check this option to enable/disable fuel validation (the contract can only operate with the assigned fuels).
* **Validate Programs:** By activating this function the contract will validate the programs in the request for identifiers (by checking this option it becomes mandatory to incorporate at least one program).
* **Subsidized Values:** Check this option to indicate that the contract is generated with Subsidy.
* **Use of Locations:** Checking this option will establish that the contract makes use of the previously configured locations (Administration>Locations).
* **Validate Shops:** Check this option to enable/disable store validation (the contract can only operate within the assigned stores).
* **Allow company address editing:** Checking this option will allow the modification of company delivery addresses.

Once the general information is completed, you have different tabs to configure:

1. **Fuels:** Select the fuels associated to the contract.

INSERTAR IMAGEN

2. **Sites:** Select the sites associated to the contract.

INSERTAR IMAGEN

3. **Prices:** Configure the prices associated to the contract.

INSERTAR IMAGEN

In the "Current Prices" section you can see the current prices for the fuels in the corresponding sites, as well as the modifiers applied to them.

* **Fuel:** Select the fuel associated to the price.
* **Value:** Enter the value of the price.
* **Site:** Select the site associated with the price.
* **Date From:** Enter the start date of the price.
* **Time From:** Enter the start time of the price.
* **Date To:** Enter the end date of the price.
* **Date To:** Enter the end time of the price.

4. **Modifiers:** Configure the modifiers associated to the contract.

INSERTAR IMAGEN

* **Description:** Enter the description of the modifier.
* **Class:** Select the type of modifier (Discount or Recharge).
* **Type:** Select the type of modifier (Percentage, Fixed per Transaction or Fixed per Unit).
* **Value:** Enter the value of the modifier.
* **Fuel:** Select the fuel associated with the modifier.
* **Site:** Select the site associated with the modifier.
* **Date From:** Enter the start date of the modifier.
* **Time From:** Enter the start time of the modifier.
* **Date To:** Enter the end date of the modifier.
* **Time To:** Enter the end time of the modifier.

5. **Billing:** Configure the billing process associated to the contract.

INSERTAR IMAGEN

* **Billing Process Type:** Select the type of settlement process associated to the contract (EdiFactMx is only for Mexico customer).
* **Active:** Check this option to activate/deactivate the settlement process.
* **Due days:** Enter the number of due days associated with the statement.
* **Periodicity:** Enter the frequency with which statements are generated.
* **Manual:** Check this option to activate/deactivate the manual process of the settlement process.
* **Settlement Start Date:** Set the date for which the contract settlements will be scheduled to start. If this section is left blank, the default date will be the same as the contract creation date.
* **Charges Deduct Account Balance:** Check this option to enable/disable ATIONet to automatically subtract items from account balances.
* **Separate Document Charges:** Check this option to enable/disable ATIONet to separate each item associated to the account statement.
* **Recipient Emails:** Enter the email addresses that will receive the statements.
* **Contributor ID:** Enter the ID of the contributor associated with the statement.
* **Name:** Enter the name associated with the statement.
* **Street 1:** Enter the primary street associated with the statement.
* **Street 2:** Enter the secondary street associated with the statement.
* **Zip Code:** Enter the zip code associated with the billing statement.
* **City:** Enter the city associated with the billing statement.
* **Country:** Enter the country associated with the billing statement.
* **State:** Enter the state associated with the statement.

6. **Concepts:** Select the concept associated to the contract. For more information about the concepts click here.

INSERTAR IMAGEN

7. **Documents:** Upload any document associated to the contract (for example: a pdf of the physical contract itself).

INSERTAR IMAGEN

8. **Locks:** Configure the locks associated to the contract.

INSERTAR IMAGEN

* **Type:** Select Fixed to block the transaction on specific dates, or select Fixed to block the transaction on specific days of each month.
* **Date from:** Enter the start date of the block.
* **Date To:** Enter the end date of the block.
* **Day From:** Enter the start day of each month for the block.
* **Day To:** Enter the end day of each month for the block.

9. **Overdraft:** Configure the overdrafts associated with the contract.

INSERTAR IMAGEN

* **Type:** Select the type of overdraft (Percentage or Amount).
* **Value:** Enter the value associated to the overdraft.
* **Date From:** Enter the start date of the overdraft.
* **Date To:** Enter the end date of the overdraft.

10. **Programs:** Add the programs enabled to operate with the contract (If the "Validate Programs" option is checked, this field is mandatory).

INSERTAR IMAGEN

11. **Subsidies:** Add the temporary subsidies that will be implemented for the desired fuels.

INSERTAR IMAGEN

12. **Merchants:** Add the merchants enabled to operate with the contract (In case of having checked the "Validate Merchants" option, this field is mandatory).

INSERTAR IMAGEN

13. **Identifier Model:** Select the identifier models associated to the contract.

INSERTAR IMAGEN

When you have finished filling in the fields, press the **Save** button.

## Company Current Accounts

The Company Current Accounts section is the view of the available balance of the subaccounts and/or contracts, and also the view of all movements of the subaccounts and/or contracts. In the Currency column of the grid you can see in which currency each movement is made. If you have the Multi-Currency functionality configured, you can see the different currencies in each transaction.

To facilitate the queries, there is a filter panel available. The first option in the filter panel is the report type:

INSERTAR IMAGEN

1. **Contracts List:** This option lists all contracts with their respective balances, but does not give details of the movements.

INSERTAR IMAGEN

2. **Contract Movements:** This option shows all contract movements.

INSERTAR IMAGEN

3. **List of Subaccounts:** This option lists all subaccounts with their respective balances, but does not give details of the movements.

INSERTAR IMAGEN

4. **Sub-Account Movements:** This view lists all the movements of the subaccounts.

INSERTAR IMAGEN

5. **Subaccount Recharges:** This view lists all subaccount reloads.

INSERTAR IMAGEN


## Concepts
Concepts in ATIONet refer to taxes or commission fees that can be added to company or merchant contracts. In this section you can consult, create and edit concepts.

![Concepts](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Concepts.PNG)

To create a concept, click the **New** button.

![Concepts New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Concepts%20New.PNG)

The fields to complete are the following:

* **Concept Type:** Select the concept type (Product, Discount or Fee).
* **Code:** Input the concept unique code.
* **Name:** Input the concept name.
* **Concept Family:** Select the family associated to the concept.
* **Class:** Select the cllassL associated to the concept.
* **Type:** Input the concept type.
* **Model:** Input the concept model.
* **Taxes Included:** Checkmark this option if the taxes are included in the amount of the transaction.

In the pricebook section fill in the following fields:

* **Date From:** Input the starting date of the concept.
* **Currency:** Input the currency of the concept.
* **Price:** Input the price of the concept.

When you have finished filling in the fields, click the **Save** button.

## Concept Families
Concept Families in ATIONet is just a way to group up several concepts. In this section you can consult, create or edit family concepts.

![Concept Families](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Family%20Concepts.PNG)

To create a concept family, click  the **New** button.

![Concept Families New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Family%20Concepts%20New.PNG)

When you have finished filling in the fields, click the **Save** button.

## Contingencies

In ATIONet a contingency is a manually entered transaction. In this section you can query and create contingencies. Note that contingencies are transactions without prior authorization.

INSERTAR IMAGEN

To create a contingency, click on the **New** button.

INSERTAR IMAGEN

The fields to be completed are as follows:
* **Reason:** Enter the reason for which the contingency is being made.
* **Authorization code:** By entering the authorization code in the contingency, the contingency data can be loaded.
* **Site:** Select the site associated to the contingency.
* **Terminal/Controller:** Select the terminal/controller associated with the contingency.
* **Date:** Enter the date of the contingency.
* **Time:** Enter the time of the contingency.
* **Primary Account:** Select the primary sub-account associated with the contingency.
* **Sub Account:** Select the sub account associated to the contingency.
* **Fuel:** Select the fuel associated with the contingency.
* **Volume Dispatched:** Enter the volume associated with the contingency.
* **Currency:** Enter the currency of the contingency.
* **Apply Contingency Price:** By activating this option, the contingency price will ignore any type of modifier related to the corresponding price.
* **Contingency with SKU:** By activating this option, SKUs can be added to the contingency (To enable this option it is necessary to have the "Date", "Time" and "Site" fields completed).

INSERTAR IMAGEN

* **Unit Price:** Enter the unit price associated to the contingency.
* **Amount Dispatched:** Enter the amount associated to the contingency.
* **Shift:** Enter the shift associated to the contingency.
* **Pump:** Enter the pump associated to the contingency.
* **Odometer:** Enter the odometer of the vehicle associated to the contingency.
* **Engine Hours:** Enter the engine hours of the vehicle associated to the contingency.
* **Driver ID:** Enter the identifier of the driver associated to the contingency.
* **Vehicle ID:** Enter the identifier of the vehicle associated to the contingency.
* **Foreman:** Enter the foreman associated to the contingency.
* **Pump Side:** Enter the pump side associated to the contingency.
* **Miscellaneous:** Enter the vehicle miscellaneous associated with the contingency.
* **Voucher Number:** Enter the voucher number associated with the contingency.
* **Purchase Order Number:** Enter the purchase order number associated with the contingency.

When you have finished filling in the fields, press the **Save** button.

## Declined Transactions

ATIONet separates unauthorized transactions into 2 sections: [Exceptions](#exceptions) and **Declined Transactions**.

Rejected Transactions are those that managed to pass ATIONet's hard authentications, but were rejected by other validations such as an unsatisfied rule or a balance validation. In the columns Volume Dispatched, Unit Price Dispatched, Amount Dispatched, Contract Unit Price, Contract Amount you can see in which currency the rejected transaction was made.

INSERTAR IMAGEN

In this view, at first you can filter by scrap type. The available scrap types are as follows:

INSERTAR IMAGEN


## Dispensed Transactions
In this section you can view all transactions that had fuel dispensed. With the incorporation of the Multicurrency functionality, in the Amount Dispensed column it will be possible to view the currency with which each transaction was made.

![Dispensed Transactions](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Dispensed%20Transactions.PNG)

## Disputed Transactions
Disputed transactions are those that either party (Merchant or Company) claims to be unaware of.

In this section you can consult the disputed transactions, listed by code, date, reason, state, transaction number, company, site. There is also the commentary of the company, the merchant and the network.

![Disputed Transactions](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Disputed%20Transactions.PNG)

## Exceptions

ATIONet separates unauthorized transactions into 2 sections: Exceptions and [Rejected Transactions](#rejected-transactions). Exceptions are those transactions that did not pass the hard validations of the system or those that are detected as possible frauds.

INSERTAR IMAGEN

In this view, at first you can filter by the type of exception. The types of exceptions available are as follows:

INSERTAR IMAGEN

Some transactions remain in Review status in some situations, such as when more than authorized is sent (due to a controller or POS error). In these cases it is necessary to approve or reject the transaction using one of the two icons to the right of each record.


## Fast Track Configuration
A Fast Track in ATIONet is a way to configure a one-use-only authorization for an specific amount to an already existing fleet sub-account. In this sections you can configure up to 10 Custom Fields for Fast Tracks.

![Fast Track Configuration](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Fast%20Track%20Configuration.PNG)

When you have finished filling in the fields, click the **Save** button.

## Fast Tracks

In this section you can view the FasTracks created. In this view, you can visualize both the amount and its period of availability. You can also view the amount of FastTrack used and the volume transacted with it.

INSERTAR IMAGEN


## Fleet Workflow Approvals

In this section you can view the different operations pending approval. These are determined in [Fleet Workflows Settings](#Fleet-Workflows-Settings).

INSERTAR IMAGEN

## Fraud Alerts
Inside this section you can see a list of all frauds performed by the Network. To configure how/when to alert of fraud, go to [Fraud Alerts Configuration](#fraud-alerts-configuration).

![Fraud Alerts](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Fraud%20Alerts.PNG)

## Fraud Alerts Configuration

In this section you can view and configure how and when fraud alerts are triggered for the Network.

INSERTAR IMAGEN

To create a configuration, click on the **New** button.

INSERTAR IMAGEN

* **Type:** Select the item to which the alert will be applied (this can be applied to transactions, amount, volume and KM/MI).
* **Mode:** (This option is only enabled in case of selecting "Transactions" as an element) Choose for which type of transactions the alert will be applied. It is divided into 3 groups; standard, offline and contingency.
* **Amount:** Enter the amount from which the alert will be executed.
* **Value:** (This option is only enabled if "Amount" is selected as an element) Enter the value from which the alert will be executed.
* **Active:** Check/Uncheck this box to keep this alert active/deactive.
* **Sub-account owner:** (This option is only enabled if "Transactions" is selected as an element).
* **Periodicity:** Enter the time unit for which you want this alert to remain in effect.

When you have finished filling in the fields, press the **Save** button.

## Identifications Scheduler

In this section you can view the Identifier Scheduler excecuted processes.

For more details about its configuration refer to the section [Identifier Scheduler Settings](Identifier-Scheduler-Settings).

INSERTAR IMAGEN

## Invoice Type

In this section, you can CREATE, EDIT and DELETE various types of invoices.

INSERTAR IMAGEN

To create a new invoices type, press the **NEW** button and fill in the required fields.

INSERTAR IMAGEN

When you have finished filling in these fields, click the **Save** button.

## Merchants Contracts

In ATIONet the term trade refers to the entity that owns the sites. In this section you can consult, edit and create trade contracts. To facilitate queries, there is a filter panel at the top.

INSERTAR IMAGEN

To create a merchant contract, click on the **New** button.

INSERTAR IMAGEN

The fields to fill in are as follows:

* **Active:** Check/Uncheck this box to keep this contract active/deactive.
* **Trade:** Select the merchant associated to the contract.
* **Trade User:** Enter the contact user of the trade.
* **Code:** Enter the code of the contract.
* **Automatically generated:** Check this option to have ATIONet automatically generate the contract code.
* **Description:** Enter the description of the contract.
* **Start date:** Enter the start date of the contract.
* **Duration:** Enter the duration of the contract.
* **Current Account Mode:** Select the current account mode (Product or Money).
* **Distribution Price List:** Select the price list of the contract.

After filling in these fields, you must configure the Site, Fuel, Prices and Modifiers tabs.

1. **Sites:** Select the sites associated to the contract.

INSERTAR IMAGEN

2. **Fuels:** Select the fuels associated to the contract.

INSERTAR IMAGEN

3. **Prices:** Select the prices associated to the contract.

INSERTAR IMAGEN

4. **Modifiers:** Select the modifiers associated to the contract.

INSERTAR IMAGEN

When you have finished filling in the fields, press the **Save** button.

## Merchant Current Accounts

The Merchant Current Accounts view is where the balances and movements of all merchants are consulted.

To make queries easier, a filter panel is available and the first option in the panel is the type of report you want to view (List of Contracts, Contract Movements, List of Sites and Site Movements). In the Currency column of the grid you can see in which currency each movement is made. If you have Multi-Currency functionality configured, you can see the different currencies in each movement.

INSERTAR IMAGEN

**List of contracts:** This option lists all contracts with their respective balances, but does not give details of the movements.

INSERTAR IMAGEN

**Contract movements:** This option shows all contract movements.

INSERTAR IMAGEN

**Sites List:** This option lists all Sites with their respective balances, but does not give details of the movements.

INSERTAR IMAGEN

**Site Movements:** This view lists all the movements of the Sites.

INSERTAR IMAGEN

## Outstanding Authorizations
In ATIONet outstanding authorizations are those transactions that have not yet received the completion transaction, but have been pre-authorized. The information seen in this view are dispatches that are currently underway. If for some reason there are old pre-authorizations, it is likely that the POS did not send the completion transaction or the cancellation transaction if the dispatch was not completed.

Please note that at the time of pre-authorization, ATIONet froze the amount of the authorization of the current account for the sub-account associated. This view presents all the fields necessary to identify the transaction and the sub-account. If you need to see more details, clicking on the authorization code will take you to the transaction details view.

![Outstanding Authorization](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Outstanding%20Authorization.PNG)

If old pending transactions appear and you are sure it is not an ongoing dispatch, you may cancel them and return the balance to the current account.
To do so there are 2 ways: individually, by clicking on the **X** icon to the right side of the grid, or massively by selecting the transactions, displaying the **Batch Actions** menu and selecting **Cancel**. This will cancel the transactions and return the balance reserved to each of the current accounts. (for more details on the transaction flow refer to this [document](AN-Transaction_Flows-TechGuide.md))

## Over Limit
In this section you can consult or create over limits for company contracts. Over limit in ATIONet refers to an amount that sub-accounts can overextend from their balances.

![Over Limit](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Over%20Limit.PNG)

To create an over limit, click the **New** button.

![Over Limit New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Over%20Limit%20New.PNG)

The fields to be completed are as follows:

* **Company:** Select the company associated to the over limit.
* **Contract:** Select the company contract associated to the over limit.
* **Date From:** Input the starting date of the over limit.
* **Date To:** Input the ending date of the over limit.
* **Type:** Select the over limit type (Percent or Amount).
* **Value:** Input the value of the over limit.

When you have finished filling in the fields, click the **Save** button.

## Programs

In this section you can consult, edit or create fleet programs. For each Network ATIONet already has a CLASSIC program created by default. A fleet program in ATIONet allows identifiers to ignore some of their behaviors, such as Balance Mode, Contingency Support, Offline Support, etc.

INSERTAR IMAGEN

To create a program, click on the **New** button.

INSERTAR IMAGEN

The fields to be completed are as follows:
* **Code:** Enter the desired code for the program
* **Description:** Enter the description of the program.
* **BIN Range:** Enter the BIN range associated with the program.
* **Application of Contractual Sites:** Select whether or not site validation is applied to the program.
* **Balance Mode:** Select the balance mode for the program (Contract, Dispersed, Non-Dispersed or Auto Fill).
* **Contingency Support:** Select whether or not contingency creation is applied in the program.
* **Offline Support:** Select whether or not the offline module is applied in the program.
* **Type:** Select the type of program (Fleet or Vouchers).
* **Dry Goods Support:** Check this option if the program supports SKUs. Validate Expiration Date: Check this option if the program validates the expiration dates of the identifiers.
* **ID Expiration:** Enter the duration of the ID.
* **Driver ID Usage:** Select the type of ID to be requested from the driver.
* **Vehicle ID Usage:** Select the type of identifier that will be requested for the vehicle.

Once you have completed the general information, you can also configure the request and location rules for the program:

INSERTAR IMAGEN

For more information on the rules go [here](#rules).

When you have finished filling in the fields, press the **Save** button.


## Requested Identifications

In this section you can consult the IDs requested by the company and request the identification of the fleet and/or loyalty. You can also perform actions such as setting the IDs as in production or as delivered.

You also have a panel to filter the requested IDs to facilitate the search.

INSERTAR IMAGEN

In the detail view you can see the delivery address that has been configured for the company, as well as the type and model of the badge, and the requestor of the badge.

INSERTAR IMAGEN

To request a fleet ID, click on the **New Request** button and select Request Fleet IDs. This will open a form.

INSERTAR IMAGEN

* **Type:** Select the type of identifiers (Card, TAG, Chipkey, ATIOnet Card, ATIOnet TAG, Barcode and QR).
* **Model:** Select the identifier model.
* **Company:** Select the company associated to the identifiers.
* **Contract:** Select the company contract associated to the identifiers.
* **Program:** Select the program associated to the identifiers.
* **Quantity:** Enter the quantity of identifiers to request.

When you have finished filling in the fields, press the **Request Identifiers** button.

To change the status of the requested identifiers, click on the **Action** button in Batch and select the Put into Production or Put as Delivered option. You can have **All** requests change the status or only the selected ones.

## Rules

In ATIONet rules refer to limits that can be configured by the company and associated to different entities. Within this view you can consult, create or edit rules. There are different types of rules: Quota, Date Range, Location, Fuel, Transaction Limit, DaysTime, Request, Dry Transaction Limit and Dry Quota Limit.

Note that all rules can be Non-Blocking, which means that ATIONet will not reject the transaction even if the parameters are met.

INSERTAR IMAGEN

1. **Quota:** In this rule you can limit the amount of transactions, volume and/or money at a specific frequency.

INSERTAR IMAGEN

2. **Date Range:** In this rule you can limit the transactions to be made in specific date and time ranges.

INSERTAR IMAGEN

3. **Location:** In this rule you can limit transactions to be made in specific locations, zones and trades.

INSERTAR IMAGEN

4. **Fuel:** In this rule you can limit transactions to be made for specific fuels and fuel master groups.

INSERTAR IMAGEN

5. **Limit per Transaction:** In this rule you can limit the volume of each transaction and/or money.

INSERTAR IMAGEN

6. **Days/Time:** In this rule you can limit the transactions to be performed on specific days and times of the week.

INSERTAR IMAGEN

7. **Request:** In this rule you can configure the information request for transactions, such as driver/vehicle ID, driver/vehicle PIN, etc.

INSERTAR IMAGEN

8. **Product Limit per Transaction:** In this rule you can limit the transaction money for each SKU.

INSERTAR IMAGEN

9. **Per Product Quota:** Per Product Quota rules, limit to those to whom this rule applies, the amount of money in which dry goods will be allowed to be bought/sold, every certain number of days, weeks, months or years. Once this time interval ends, the amount used so far is reset (i.e. returns to zero). In turn, this rule is not available in offline mode.

INSERTAR IMAGEN

10. **Fuel Quota:** The Fuel Quota rules specify the types of fuels that can be sold by the company within a certain period of time. Once this interval ends, the sales counter will be reset (i.e. reset to zero). The amount that can be transacted can be specified in number of transactions, volume of fuel, or amount of money, but only one of these can be selected.

INSERTAR IMAGEN

11. **Quota per day:** The rules of type Quota per day specify the amount of fuel that can be bought/sold by the company during each day of the week. The value set for a given day implies the consumption available for that specific day and are not cumulative under any criteria. The quantity counter resets to zero when the day ends and will only come into operation when a new day with configured values starts. Days that are left inactive or disabled do NOT represent any limit or restriction on the purchase/sale of fuel for that day. The amount of available quota can be specified in number of transactions, volume of fuel or amount of money. Also, this rule is not available in offline mode.

INSERTAR IMAGEN

12. **Full Quota:** Full Quota type rules specify an overall limit on the company's consumption considering both fuels and SKUs every certain period of time. Once this interval ends, the consumption counter is reset (i.e., reset to zero). The amount that can be transacted can be set in number of transactions or amount of money. At the same time, this rule is not available in offline mode.

INSERTAR IMAGEN

After setting up any type of rule, the last step is to associate the rule to an entity. Rules can be applied to: Fleets, Vehicles, Drivers, Sites and Fuels.

INSERTAR IMAGEN


## Transactions

The transactions view is one of the most important views in ATIONet. In this view you can see all successful transactions.

The filter panel has all these fields available:

INSERTAR IMAGEN

* **Authorization Code:** Enter the authorization code associated with the transaction.
* **Shift:** Enter the shift number associated with the transaction.
* **Company:** Select the company associated to the transaction.
* **Fleet:** Select the fleet associated to the transaction.
* **Vehicle:** Select the vehicle associated with the transaction.
* **Driver:** Select the driver associated to the transaction.
* **Trade:** Select the trade associated to the transaction.
* **Site:** Select the site associated to the transaction.
* **Terminal/Controller Type:** Select the terminal type associated with the transaction.
* **Terminal/Controller:** Select the terminal associated with the transaction.
* **Fuel:** Select the fuel associated to the transaction.
* **ERP Voucher Number:** Enter the ERP voucher number associated with the transaction.
* **Program:** Select the fleet program associated with the transaction.
* **Contract:** Select the company contract associated with the transaction.
* **Industry:** Select whether or not to filter by sites that are considered industries and are related to the corresponding transaction.
* **Invoice Number:** Enter the invoice number associated with the transaction.
* **Billing Number:** Enter the billing number associated with the transaction.
* **Date Type:** Select the date type associated with the transaction (Controller, Host, Subscription or Site).
* **Time Range Type:** Select the time range type of the transaction (this can be current, fixed or previous).
* **From/To Date:** Enter the start and end dates associated with the transaction.
* **From/To Time:** Enter the start and end times associated with the transaction.
* **Yield by Period:** Check this option to filter among the transactions which submitted yields within a particular period. (Checking this option makes the date a required field).
* **Show Transactions Completed on Zero:** Check this option to view transactions in which no fuel was dispensed.
* **Mode:** Select the transaction mode (Contingency, Offline or Standard).
* **Transactions with Products:** Check this option to view transactions with embedded SKUs.
* **Subsidized Values:** Select the option corresponding to the transaction (Yes/No).
* **Transaction Type:** Select the type of transaction (Transaction can be a sale completion, sale, return or reversal).
* **SKU Categories:** Select the SKU category associated to the transaction.
* **SKU:** Select the SKU associated with the transaction.
* **ID:** Select an ID associated with the transaction.
* **Fast Track Order Number:** Enter the Fast Track Order Number associated with the transaction.
* **Transactions with Fast Tracks:** Check this option to view transactions which contain Fast Tracks.

Once you have filtered, click **Search** and the transactions that match the filter will be listed.

INSERTAR IMAGEN

If you want to see the detail of the transaction, click on the **Authorization Code** and this will take you to a detailed view of the transaction.

INSERTAR IMAGEN

With the addition of Multicurrency, within Transaction Details you will find three new sections: Site Currency, Company Currency and Trade Currency, which are configurable as explained in the Multicurrency document.

 
## Transactions by Driver
In this view you can see the transactions grouped by the driver who made them. The buttons at the top left are for printing the table or creating an Excel file from the table, respectively. 
Within the grid in the Currency column you can see in which currency each transaction is made. If the Multicurrency functionality is enabled, the different currencies will be indicated in the list of transactions according to each one of them.

![Transactions by Driver](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Transactions%20by%20Driver.PNG)

## Transactions by Fleet
In this view you can see the transactions grouped by the fleet who made them. The buttons at the top left are for printing the table or creating an Excel file from the table, respectively.
Within the grid in the Currency column you can see in which currency each transaction is made. If the Multicurrency functionality is enabled, the different currencies will be indicated in the list of transactions according to each one of them.

![Transactions by Fleet](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Transactions%20by%20Fleet.PNG)

## Transactions by Site
In this view you can see the transactions grouped by the site where they were made. The buttons at the top left are for printing the table or creating an Excel file from the table, respectively.
Within the grid in the Currency column you can see in which currency each transaction is made. If the Multicurrency functionality is enabled, the different currencies will be indicated in the list of transactions according to each one of them.

![Transactions by Site](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Transactions%20by%20Site.PNG)

## Transactions by Vehicle
In this view you can see the transactions grouped by the vehicle who made them. The buttons at the top left are for printing the table or creating an Excel file from the table, respectively.
Within the grid in the Currency column you can see in which currency each transaction is made. If the Multicurrency functionality is enabled, the different currencies will be indicated in the list of transactions according to each one of them.

![Transactions by Vehicle](https://github.com/nuchavez/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Transactions%20by%20Vehicle.PNG)

## Transactions ERP

In this view you can see the transactions grouped by corresponding ERP. The buttons on the top left are used to print the table or to create an Excel file from the table, respectively.

INSERTAR IMAGEN

## Uncontrolled Transactions
Uncontrolled transactions are those that are generated because the controller detects a difference in gauges and sends a transaction for the difference. These transactions do not contain data about the identification, since they were generated automatically and were not initiated with the presentation of an identification. As they do not have an identification assigned, they are not impacted in any current account nor do they count for the calculation of rules.

![Uncontrolled Transactions](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Uncontrolled%20Transactions.PNG)


## Vouchers

In this section you can view the vouchers created, as well as filter between those that are active and inactive, and between those that have or do not have a balance. With the buttons at the top you can modify the views between detailed and simplified, as well as download an Excel file with the corresponding information of the vouchers.

INSERTAR IMAGEN

## Vouchers - Administration

In this section you can view the vouchers created, which are organized by period of creation. These columns show the detail of how many vouchers were generated on the corresponding date and how much their individual amount corresponds to, as well as the total amount of the operation.

INSERTAR IMAGEN

<br>

[Back to top](#contents) 	:arrow_up:

