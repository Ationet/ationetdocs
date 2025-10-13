![ationetlogo](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/ATIOnetLogo_250x70.png)

# Contents
 
- [Consumer Card](#Consumer-Card)
  - [Billed Items](#Billed-Items)
  - [Billing Documents](#Billing-Documents)
  - [Billing Processes](#Billing-Processes)
  - [Cards](#Cards)
  - [Charges Documents](#Charges-Documents)
  - [Contingencies](#Contingencies)
  - [Declined Transactions](#Declined-Transactions)
  - [Errors](#Errors)
  - [Movements](#Movements)
  - [Outstanding Authorizations](#Outstanding-Authorizations)
  - [Programs](#Programs)
  - [Recharges](#Recharges)
  - [Requested Cards](#Requested-Cards)
  - [Statements](#Statements)
  - [Transactions](#Transactions)

##  Billed Items

In this section, you can view the items applied to each account statement.

In the upper section, there is a filter system that allows you to filter by process code, as well as by billing number, customer, and date/time.
By interacting with the date column, you can reorder the list of billed items by date.

INSERT IMAGE


  </br>
  
##  Billing Documents

In this section, you can see all the registration statuses of the requested billing documents. The possible statuses are: Pending, Processing, Completed, or Completed with errors.

INSERT IMAGE

  </br>
  
##  Billing Processes

In this section, you can manually execute a billing process or view the status of all billing processes. The possible process statuses are: Pending, Confirmed, Error, or Confirmed with errors.

INSERT IMAGE

Additionally, in the details column, you can view four options that facilitate access to sections related to this process.
From left to right, the processes are as follows:

* **Settlements:** When you interact with this option, you will be redirected to the "Charge Documents" section, where the "Processes" filter will have been automatically applied, highlighting the results related to the settlement process. 

* **Settled items:** When you select this option, you will be redirected to the "Settled items" section, where the "Processes" filter will have been automatically applied, highlighting the results related to the settlement process.

* **Account statements:** When you select this option, you will be redirected to the "Account statements" section, where the "Processes" filter will have been automatically applied, highlighting the results related to the settlement process.

* **Error:** When you select this option, you will be redirected to the "Errors" section.


  </br>
  
##  Cards

In this section, you can view the cards that have been created, as well as edit them and enable/disable cards.

INSERT IMAGE

In the ***"Bulk Cards"*** option, you can create multiple cards by simply selecting the program to which they will belong and the desired quantity.

INSERT IMAGE

To create a new card, click on the "New" button and fill in the following fields:

INSERT IMAGE 

* **Program:** Enter the program to which the card will be associated.
* **Last name:** Enter the last name of the cardholder.
* **First name:** Enter the first name of the cardholder
* **Email:** Enter the cardholder's email address
* **Date of Birth:** Enter the cardholder's date of birth
* **Country:** Enter the country associated with the card user
* **State:** Enter the state associated with the cardholder
* **City:** Enter the city associated with the cardholder
* **Zip Code:** Enter the zip code corresponding to the cardholder
* **Street:** Enter the main street associated with the cardholder
* **Street 2:** Enter the secondary street associated with the card user
* **Phone 1:** Enter the primary phone number associated with the card user
* **Phone 2:** Enter the secondary phone number associated with the card user


  </br>
  
##  Charges Documents

In this section, you can view a summary of the items applied.
By clicking on the **Number**, you can view the details of which items were applied, as well as the number of transactions to which that item was applied.

INSERT IMAGE

For more details about its configuration, go to the [#Programs](#Programs) section.


  </br>

##  Contingencies

In ATIONet, a contingency is a manually entered transaction. In this section, you can view and create contingencies. Please note that contingencies are transactions without prior authorization.

IMAGE

To create a contingency, click on the New button.

IMAGE

* **Reason:** Enter the reason for the contingency.
* **Date:** Enter the date of the contingency.
* **Time:** Enter the time of the contingency.
* **Program:** Enter the program associated with the corresponding card
* **Card:** Enter the card corresponding to the contingency
* **Site:** Select the site associated with the contingency.
* **Terminal/Controller:** Select the terminal/controller associated with the contingency.
* **Fuel:** Select the fuel associated with the contingency.
* **Dispensed Volume:** Enter the volume associated with the contingency.
* **Unit Price:** Enter the unit price associated with the contingency.
* **Dispensed Amount:** Enter the amount associated with the contingency.
* **Shift Number:** Enter the shift associated with the contingency.
* **Pump Number:** Enter the pump associated with the contingency.
* **Odometer:** Enter the odometer of the vehicle associated with the contingency.
* **Engine Hours:** Enter the engine hours of the vehicle associated with the contingency.
* **Driver ID:** Enter the ID of the driver associated with the incident.
* **Vehicle ID:** Enter the identifier of the vehicle associated with the incident.
* **Attendant Code:** Enter the code associated with the contingency.
* **Miscellaneous:** Enter the miscellaneous information for the vehicle associated with the incident.
When you have finished filling in the fields, press the Save button.


  </br>

##  Declined Transactions

Rejected Transactions are those that passed ATIONET's hard authentications but were rejected by other validations, such as an unsatisfied rule or a balance validation. 
In the **Dispatched Volume**, **Dispatched Unit Price**, **Dispatched Amount**, **Contract Unit Price**, and **Contract Amount** columns, you can see the currency in which the rejected transaction was made.

INSERT IMAGE

  </br>
  
##  Errors

In this section, you can view errors resulting from billing processes that ended in errors.

INSERT IMAGE


  </br>

##  Movements

In the **Movements** section, you can view all interactions related to the card balance.
To facilitate queries, a filter panel is available:

INSERT IMAGE

To register a new transaction, press the **New** button, then prioritize the following information:

* **Type:** Select the type of transaction you wish to perform, which can range from a transfer of funds between two cards to the withdrawal of funds to a subaccount.
    * **If you select *“Money transfer between cards”***:

  *  INSERT IMAGE
    
        - **Description:** Enter a description for the specific transaction.
        - **Client:** Enter the client to whom the transaction corresponds.
        - **Origin Card:** Enter the card from which the funds will be withdrawn.
        - **Destination Card:** Enter the card to which the funds will be transferred.
        - **Amount:** Enter the desired amount for the transaction.

    * **If you select *“Money Withdrawal from subaccount”***:

  *  INSERT IMAGE

        - **Program:** Enter the corresponding program for the card. 
        - **Card:** Enter the card from which the funds will be withdrawn.
        - **Amount:** Enter the desired amount for the transaction.

Once you have finished configuring this transaction, press **Create.**

  </br>
  
##  Outstanding Authorizations

In ATIONet, outstanding authorizations are transactions that have not yet received the completion transaction but have been preauthorized. The information shown in this view is for shipments that are currently in progress. If for some reason there are old preauthorization, it is likely that the POS terminal has not sent the completion transaction or the cancellation transaction if the shipment has not been completed.
Please note that at the time of preauthorization, ATIONet froze the authorization amount from the checking account for the associated subaccount. This view displays all the fields necessary to identify the transaction and the subaccount. If you need to see more details, clicking on the authorization code will take you to the transaction details view.

-Insert Image

If old pending transactions appear and you are sure that they are not a shipment in progress, you can cancel them and return the balance to the checking account. There are two ways to do this: individually, by clicking on the X icon on the right, or in bulk, by selecting the transactions, opening the Batch Actions menu, and selecting Cancel. This will cancel the transactions and return the reserved balance to each of the current accounts. (For more details on the transaction flow, see this document).


  </br>
  
##  Programs

In this section, you can view, create, and edit consumer card programs.

INSERT IMAGE

To create a new program, press the **NEW** button.

INSERT IMAGE

Then you must fill in the following information:

* **Name:** Enter the desired name for the program
* **Description:** Enter a description of the program
* **BIN Range:** Enter a BIN range with a maximum of 7 alphanumeric characters. 
* **Start Date:** Enter the start date of the program
* **Duration:** Enter the desired duration of the program
* **Site Validation:** By enabling this option, the program will only operate on the configured sites
* **Discount Requires Registration:** By checking this box, only end users who are registered on the Consumer Card Portal will be able to use the discounts configured in the program. 
* **Validate Expiration Date:** Enabling this option allows you to configure an expiration date for cards created with this program
* **Contact Name:** Enter a contact name for the program
* **Contact Email:** Enter the email address of the program contact.
* **Rack Prices List:** Select the distribution price list that will be applied to the program.
* **Currency:** Select the currency in which the cards for this program will operate.

Then, you can configure the following sections:

* **Fuels:** In this section, you can configure which fuels the cards related to this program will be able to operate with

INSERT IMAGE

* **Sites:** In this section, you can configure the sites and fuels that will be used at the corresponding locations.

INSERT IMAGE

* **Discounts:** In this section, you can configure the discounts. 

INSERT IMAGE

* **Biliing:** In this section, you can configure the frequency of billing for the cards associated with this program.

INSERT IMAGE

* **Concepts:** In this section, you can configure the concepts applicable to the cards associated with this program

INSERT IMAGE

* **Identifier Models:** In this section, you can configure the characteristics of the card as an identifier.

INSERT IMAGE

* **Rule:** In this section, you can configure the rules corresponding to this program.

INSERT IMAGE

* **Merchant:** In this section, you can configure the merchants associated with the program.

INSERT IMAGE

Once you have finished configuring the program as desired, press **Save**

  </br>
  
##  Recharges

In this section, you can view the recharges made to the respective cards.

INSERT IMAGE

To make a top-up, click on the **NEW** button.
Once in this view, you must complete the requested information:

INSERT IMAGE

* **Program:** Enter the program to which the card is associated.
* **Card:** Enter the number of the card you wish to recharge.
* **Amount:** Enter the amount corresponding to the recharge.
* **Attendant:** Enter the attendant associated with the card.

To finish, press **Create** to complete the recharge process.


  </br>
  
##  Requested Cards

In this section, you can view the processes for requested cards. They are sorted by order number by default, but when you interact with the column title **"Order Request"** or **"Order Date",** the results will be reorganized from lowest to highest depending on which title you interacted with.

INSERT IMAGE

To create a new request, click on the **"New Request"** button.

Select the program associated with these cards and the desired number of cards, click on the **"Create"** button, and the request will be processed.

INSERT IMAGE 


  </br>
  
##  Statements

In this section, you can view and download your Network account statements. You can also generate account statements in .pdf format one by one, or generate a package within the Batch Action.

In turn, by interacting with the **Statements Number**, you can view the details of the corresponding account statement.

INSERT IMAGE

  </br>
  
##  Transactions

In this view, you can see all the transactions corresponding to this section.
The filter panel has all of these fields available:

INSERT IMAGE

* **Authorization Code:** Enter the authorization code associated with the transaction.
* **Customer:** Enter the name of the customer associated with the transaction.
* **Program:** Select the consumer card program associated with the transaction.
* **Site:** Select the site associated with the transaction.
* **Terminal/Controller:** Select the terminal associated with the transaction.
* **Date from/to:** Enter the start and end dates associated with the transaction.
* **Time from/to:** Enter the start and end times associated with the transaction.

Once you have filtered, click Search and the transactions that match the filter will be listed.

INSERT IMAGE

If you want to see the transaction details, click on the Authorization Code and this will take you to a detailed view of the transaction.

INSERT IMAGE

  </br>

[Back to top](#contents) 	:arrow_up:
