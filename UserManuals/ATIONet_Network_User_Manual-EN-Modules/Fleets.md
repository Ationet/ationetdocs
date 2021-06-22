![ationetlogo](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/ATIOnetLogo_250x70.png)

# Contents

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
	- [Uncontrolled Transactions](#uncontrolled-transactions)

# Fleets
Inside this module you can manage Company and Merchant Contracts, Concepts, Contingencies and Transactions among other things.

## Attendants
In ATIONet the term attendant refers to the person responsible to make the dispatch, that operates the pumps. In this section you can view, create and edit all attendants. To make queries easier, there is a panel of filters at the top.

![Attendants](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Attendant.PNG)

To create an attendant, click the **New** button.

![Attendants New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Attendant%20New.PNG)

When you have finished filling in the fields, click the **Save** button.

## Company Contracts
In ATIONet the term company refers to the entity that manages the fleet. In this section you can create, edit or consult all company contracts. To make queries easier, there is a panel of filters at the top.

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

Declined Transactions are those that managed to pass ATIONet's hard authentications, but were rejected by other validations such as an unsatisfied rule or balance validation.

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

## Fraud Alerts
Inside this section you can see a list of all frauds performed by the Network. To configure how/when to alert of fraud, go to [Fraud Alerts Configuration](#fraud-alerts-configuration).

![Fraud Alerts](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Fraud%20Alerts.PNG)

## Fraud Alerts Configuration
In this section you can consult and configure how and when are fraud alerts triggered for the Network.

![Fraud Alerts Configuration](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Fraud%20Alerts%20Configuration.PNG)

To create a configuration, click the **New** button.

![Fraud Alerts Configuration New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Fraud%20Alerts%20Configuration%20New.PNG)

When you have finished filling in the fields, click the **Save** button.

## Merchants Contracts
In ATIONet the term merchant refers to the entity that owns the sites. In this section you can consult, edit and create merchant contracts. To make queries easier, there is a panel of filters at the top.

![Merchant Contracts](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Merchant%20Contracts.PNG)

To create a merchant contract, click the **New** button.

![Merchant Contract New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Merchant%20Contracts%20New.PNG)

The fields to be completed are as follows:

* **Code:** Input the code of the contract.
* **Automatically Generated:** Checkmark this option to have ATIONet automatically generate the contract code.
* **Description:** Input the description of the contract.
* **Merchant:** Select the merchant assocciated to the contract.
* **Merchant User:** Input the merchant contact user.
* **Start Date:** Input the starting date of the contract.
* **Duration:** Input the duration of the contract.
* **Current Account Mode:** Select the current account mode (Product or Money).

After completing these fields, you must enter the fuel assigned to the contract and fill in the Volume, Security Limit, Over Limit, Over Limit Start and End Dates fields, Currency in which the Fuel Value is located, and the Fuel Price.

When you have finished filling in the fields, click the **Save** button.

## Merchant Current Accounts
The merchant current accounts view is where the balances and movements of all merchant are consulted.

For easier quieries there is a filter panel available and the first option in the panel is the type of report to see (Contracts List, Contracts Movements, Sites List and Sites Movements).

![Merchant Current Accounts](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Merchant%20Current%20Accounts.PNG)

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
Inside this section you can consult, edit or create fleet programs. For every Network, ATIONet already has a CLASSIC program created by default. A fleet progam in ATIONet allows identifications to override some of their behaviors, like for example: Balance Mode, Contingency Support, Offline Support, etc.

![Programs](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Programs.PNG)

To create a program, click the **New** button.

![Programs New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Programs%20New.PNG)

The fields to complete are the following:

* **Description:** Input the program description.
* **BIN Range:** Input the BIN Range associated to the program.
* **Apply Contract Sites:** Select if the site validation is enforced or not on the program.
* **Balance Mode:** Select the balance mode for the program (Contract, Disperse, Do Not Disperse or Auto Fill).
* **Contingency Support:** Select if contingency creation is enforced or not on the program.
* **Offline Support:** Select if the offline module is enforced or not on the program.
* **Type:** Select the type of program (Fleet or Voucher).
* **Support Dry Products:** Checkmark this option if the program supports SKUs.
* **Validates Expiration Date:** Checkmark this option if the program validates identification expiration dates.
* **Identifier Expiration:** Input the identification duration.

Once the general information was completed, you can also configure prompt and location rules for the program:

![Programs New - Rules](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Programs%20New%20-%20Rules.PNG)

For more information about rules go [here](#rules).

When you have finished filling in the fields, click the **Save** button.

## Requested Identifications
In this section you can consult the requested identifications by the company and request fleet and/or loyalty identification. You can also perform actions such as establishing the identifications as in production or as delivered.

It also has a panel to filter the requested identifications and thus make the search easier.

![Requested Identifications](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Requested%20Identifications.PNG)

To request a fleet identification, click the **New Request** button and select **Request Fleet Identifications**. When you do, a form will open up.

![Requested Identifications - New Fleet](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Requested%20Identifications%20-%20New%20Fleet.PNG)

* **Type:** Select the identifications type (Card, TAG, Chipkey, ATIOnet Card, ATIOnet TAG, Barcode and QR).
* **Model:** Select the identifications model.
* **Company:** Select the company associated to the identifications.
* **Contract:** Select the company contract associated to the identifications.
* **Program:** Select the program associated to the identifications.
* **Quantity:** Input the quantity of identifications to be requested.

When you have finished filling in the fields, click the **Request identifications** button.

In order to change the requested identification status, click the **Bulk Action** button and select either **Set in production** or **Set as delivered** option. You can either have **All** requests change the status or only the **Selected** ones.

## Rules
In ATIONet rules refer to limits that can be configured by the company and associated to different entities. Inside this view you can consult, create or edit rules. There are different type of rules: Quota, Date Range, Location, Fuel, Limit Per Transactions, DaysTime, Prompting, Dry Transaction Limit and Dry Quota Limit.

Take into consideration that all rules can be **Non Blocking**, which it means that ATIONet will not reject the transaction even when the parameters are met.

![Rules](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Rules.PNG)

1. **Quota:** In this rule you can limit transactions quantity, volume and/or money on an specific frequency.

![Rules - Quota](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Rules%20-%20Quota.PNG)

2. **Date Range:** In this rule you can limit transactions to be made on specific date and time ranges.

![Rules - Date Range](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Rules%20-%20Date%20Range.PNG)

3. **Location:** In this rule you can limit transactions to be made on specific sites and zones.

![Rules - Location](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Rules%20-%20Location.PNG)

4. **Fuel:** In this rule you can limit transactions to be made for specific fuels and fuels masters groups.

![Rules - Fuel](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Rules%20-%20Fuel.PNG)

5. **Limit Per Transactions:** In this rule you can limit each transaction volume and/or money.

![Rules - Limit Per Transactions](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Rules%20-%20Limit%20Per%20Transaction.PNG)

6. **DaysTime:** In this rule you can limit transactions to be made on specific days and times of the week.

![Rules - DaysTime](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Rules%20-%20DaysTime.PNG)

7. **Prompting:** In this rule you can configure prompts to be requested for transactions, such as Driver/Vehicle ID, Driver/Vehicle PIN, etc.

![Rules - Prompting](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Rules%20-%20Prompting.PNG)

8. **Dry Transaction Limit:** In this rule you can limit each SKUs transactions money.

![Rules - Dry Transaction Limit](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Rules%20-%20Dry%20Transaction%20Limit.PNG)

9. **Dry Quota Limit:** In this rule you can limit transactions money on an specific frequency.

![Rules - Dry Quota Limit](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Rules%20-%20Dry%20Quota%20Limit.PNG)

After configuring any type of rule, the last step is to associate the rule to an entity. You can apply rules to: Fleets, Vehicles, Drivers, Sites and Fuels.

![Rules - Association](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Rules%20-%20Association.PNG)

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

The filter panel has the following possibilities:

## Uncontrolled Transactions
Uncontrolled transactions are those that are generated because the controller detects a difference in gauges and sends a transaction for the difference. These transactions do not contain data about the identification, since they were generated automatically and were not initiated with the presentation of an identification. As they do not have an identification assigned, they are not impacted in any current account nor do they count for the calculation of rules.

![Uncontrolled Transactions](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Fleets/Uncontrolled%20Transactions.PNG)
