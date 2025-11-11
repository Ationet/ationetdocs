![ationetlogo](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/ATIOnetLogo_250x70.png)

# Contents
 
- [Gift Cards](#Gift-Cards)
  - [Cards](#Cards)
  - [Contingencies](#Contingencies)
  - [Declined Transactions](#Declined-Transactions)
  - [Movements](#Movements)
  - [Outstanding Authorizations](#Outstanding-Authorizations)
  - [Programs](#Programs)
  - [Requested Cards](#Requested-Cards)
  - [Transactions](#Transactions)


# Cards

In this section, you can view the cards that have been created, as well as enable/disable cards and, if necessary, mark them as lost.

In turn, in the "Batch Actions" option, you can activate or deactivate multiple cards simply by selecting the cards using the box on the left. Finally, the "Update" button allows you to download a template from which you can perform a mass update of cards, which, unlike "Batch Actions," is not limited by Ationet's limit of 50 results.

 </br>
 
# Contingencies

In ATIONet, a contingency is a manually entered transaction. In this section, you can view and create contingencies. Please note that contingencies are transactions without prior authorization.

To create a contingency, click on the **New** button.

The fields to be completed are as follows:
* **Reason:** Enter the reason for the contingency.
* **Date:** Enter the date of the contingency.
* **Time:** Enter the time of the contingency.
* **Authorization code:** When you enter the authorization code in the contingency, the contingency data can be loaded.
* **Program:** Enter the program associated with the contingency.
* **Card:** Enter the card associated with the contingency.
* **Site:** Select the site associated with the contingency.
* **Terminal/Controller:** Select the terminal/controller associated with the contingency.
* **Fuel:** Select the fuel associated with the contingency.
* **Dispensed Volume:** Enter the volume associated with the contingency.
* **Unit Price:** Enter the unit price associated with the contingency.
* **Dispensed Amount:** Enter the amount associated with the contingency.
* **Shif Numbert:** Enter the shift number associated with the contingency.
* **Pump Number:** Enter the pump associated with the contingency.
* **Odometer:** Enter the odometer of the vehicle associated with the contingency.
* **Engine Hours:** Enter the engine hours of the vehicle associated with the contingency.
* **Driver ID:** Enter the driver ID associated with the incident.
* **Vehicle ID:** Enter the identifier of the vehicle associated with the incident.
* **Attendant Code:** Enter the manager associated with the contingency.
* **Miscellaneous:** Enter the miscellaneous information for the vehicle associated with the incident. 
When you have finished filling in the fields, press the **Save** button.

 </br>
 
# Declined Transactions

Declined Transactions are those that passed ATIONET's hard authentications but were rejected by other validations such as an unsatisfied rule or a balance validation.

INSERT IMAGE

 </br>
 
# Movements

The Movements section displays all interactions related to the card balance. To facilitate queries, a filter panel is available.

 </br>
 
# Outstanding Authorizations

At ATIONet, outstanding authorizations are transactions that have not yet been finalized but have been preauthorized. The information displayed in this view shows shipments that are currently in progress.

 </br>
 
# Programs

In this section, you can view, edit, or create gift card programs.

To create a program, click the **New** button.

The fields to be completed are as follows:
* **Name:** Enter the desired name for the program.
* **Description:** Enter the description of the program.
* **BIN range:** Enter the BIN range associated with the program.
* **Currency:** Enter the currency corresponding to the program.
* **Activate Cards:** Enabling this option will activate the cards created with this program after they are created.
* **Card Duration:** Enter the duration period for cards created with this program.
* **Validate Sites:** Enabling this option will ensure that the program only operates on the configured sites.
* **Single Use:** Enabling this function will ensure that cards can only be used once, regardless of the remaining balance.
* **Validate Expiration Date:** Enabling this option allows you to set an expiration date on the cards that will be validated for operation. 
* **Use creation date in expiration date of the cards:** Enabling this function means that when the identifiers are activated, the creation date will be used to generate the expiration date. Otherwise, the activation date will be used.

Then, the following sections can be configured:

* **Value:** In this section, you can configure the value of the cards.

* **Fuels:** In this section, you can configure which fuels the cards related to this program can operate with.

* **Sites:** In this section, you can configure the locations and fuels that will be used at the corresponding locations.

* **Discounts:** In this section, you can configure discounts.

* **Identifications Models:** In this section, you can configure the characteristics of the card as an identifier.

* **Rule:** In this section, you can configure the rules corresponding to this program.

When you have finished filling in the fields, press the **Save** button.

 </br>
 
# Requested Cards

In this section, you can view the processes for requested cards. They are sorted by order number by default, but when you interact with the column title "Request Order" or "Order Date," the results will be reorganized from lowest to highest depending on which title you interacted with.

To create a new request, click on the "New Request" button. Select the program associated with these cards and the desired number of cards, click on the "Create" button, and the request will be processed.


 </br>
 
# Transactions

The transaction view is one of the most important in ATIONet. In this view, you can see all successful transactions.

The filter panel has all of these fields available:

* **Authorization Code:** Enter the authorization code associated with the transaction.
* **Program:** Select the fleet program associated with the transaction.
* **Card:** Enter the card corresponding to the transaction.
* **Site:** Select the site associated with the transaction.
* **Terminal/Controller:** Select the terminal associated with the transaction.
* **Date Type:** Select the date type associated with the transaction (Controller, Host, Subscription, or Site).
* **Time Interval Type:** Select the time interval type for the transaction (this can be current, fixed, or previous).
* **Date From/To:** Enter the start and end dates associated with the transaction.
* **Time From/To:** Enter the start and end times associated with the transaction. Once you have filtered, click Search and the transactions that match the filter will be listed.

If you want to see the transaction details, click on the Authorization Code and this will take you to a detailed view of the transaction.


 </br>
 

[Back to top](#contents) 	:arrow_up:
