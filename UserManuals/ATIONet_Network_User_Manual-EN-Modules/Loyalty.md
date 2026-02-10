![ationetlogo](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/ATIOnetLogo_250x70.png)

# Contents
- [Loyalty](#Loyalty)
  - [Adjustments](#Adjustments)
  - [Clients](#Clients)
  - [Communities](#Communities)
  - [Contingencies](#Contingencies)
  - [Contingencies Processes](#Contingencies-Processes)
  - [Current Account](#Current-Account)
  - [Discount Rules](#Discount-Rules)
  - [Exceptions](#Exceptions)
  - [Identities](#Identities)
  - [Loyalty Coupons](#Loyalty-Coupons)
  - [Loyalty Coupons Processes](#Loyalty-Coupons-Processes)
  - [Points Rules](#Points-Rules)
  - [Redemptions](#Redemptions)
  - [Service Entry Classes](#Service-Entry-Classes)
  - [Service Entry Types](#Service-Entry-Types)
  - [Service Entry Types Groups](#Service-Entry-Types-Groups)
  - [Service Files](#Service-Files)
  - [Transactions](#Transactions)
  - [Transfers](#Transfers)
  - [Units](#Units)

 
# Adjustments

In this section, you can schedule credit top-ups for loyalty accounts.

To schedule a new setting, click ***New***, then complete the following sections:

* **Description:** Enter a description for the desired Setting
* **Date:** Enter the date on which the setting is made
* **Time:** Enter the time at which the setting is made
* **Location:** Enter the location corresponding to the adjustment
* **Terminal/Controller:** Enter the terminal/controller corresponding to the setting
* **Community:** Add the community associated with the adjustment 
* **Loyalty Account:** Add the loyalty account associated with the adjustment 
* **Amount:** Enter the corresponding amount of the change

Once you have completed the desired configuration, click ***Save***.

</br>

# Clients

In this section, you can create clients who operate with the loyalty module.

To create a clients, you must complete the following information:

* **Community:** Add the community associated with the clients
* **Site:** Enter the site corresponding to the clients

  > In the ***"Drivers"*** section:

* **License:** Enter the driver's license 
* **Code:** Enter a code that will identify the driver
* **Last name(s):** Enter the driver's last name(s)
* **First name(s):** Enter the driver's first name(s)
* **Email:** Enter an email address associated with the driver
* **Phone 1:** Enter a phone number associated with the driver

  > In the ***"Vehicle"*** section:

* **License plate:** Enter the license plate number corresponding to the vehicle
* **Code:** Enter a code that will identify the vehicle
* **Make:** Enter the make of the vehicle
* **Model:** Enter the vehicle model
* **Color:** Enter the color of the vehicle
* **Year:** Enter the year corresponding to the vehicle model.

  > In the ***"Identifiers"*** section:

* **Label:** Enter the identifier label
* **PAN:** Enter the identifier's PAN
* **Track:** Enter the track of the identifier
* **Type:** Select the identifier type
* **Model:** Select the identifier model

  > In the ***"Service Entry"*** section:

* **Service Sheet Code:** Enter the service sheet code
* **Service Entry Type Group:** Enter the service entry group code
* **Service Entry Type:** Select the type of service entry
* **Entry:** Indicate the date of entry of the service
* **Expiration Date:** Indicate the service expiration date
* **Odometer:** Enter the most recent odometer readings corresponding to the service
* **Engine hours:** Enter the engine hours corresponding to the service

Once these parameters have been completed, click ***Save*** to successfully register the client.

</br>

# Communities

In this section, you can view, edit, and create communities 

To create a new Community, press the **"New"** button and fill in the following information:

* **Code:** Enter the code corresponding to the community
* **Active:** Check this box to mark the community as active
* **Description:** Enter a description for the community
* **Process External Host:** Check this option to indicate that the community is capable of processing an external host
* **Member Type:** Select the type of members belonging to the community
* **Supports Dual Identification:** Check this option to show that the community supports dual identification 
* **Start Date:** Enter the start date of the community
* **Duration:** Enter the duration of the community
* **BIN Range:** Enter the BIN range corresponding to the community (which is a numeric code of up to 6 characters)
* **Company:** Enter the company associated with the community
* **Service Entry Type Group:** Select the service entry type group associated with the community
* **Units:** Select the units associated with the community 
* **Initial Amount:** Enter the initial amount of the community
* **Point Alert Notification:**	Enter the minimum number of points for an alert notification to be applied 
* **Type:** Select the type of community. (This can be points, discounts, or promotions)
* **Allow multiple identities per identifier:** Enabling this option will allow multiple entities to use a common identifier.
* **Support phone number:** Enter a phone number in case you need assistance with community issues
* **Supports inventory management:** This option is only enabled for points communities and if the "External Host" option is not enabled. 

  > Enabling this option will enable inventory management so that items redeemable for points can be tracked.
* **Email notifications:** When this option is enabled, notifications corresponding to the community will be sent by email. 
* **Allow anonymous IDs:** When this option is enabled, the community will allow anonymous IDs corresponding to the associated company (the "Company" field becomes mandatory).

    > **Reconciliations:**
* **Reconciliation email:** Enter the email address associated with reconciliations 
* **Reconciliation Email Name:** Enter the name of the entity associated with the email address used

    > **Zones:**
* **Zone:** Indicate a zone associated with the community

    > **Locations:**
* **Site:** Indicate sites associated with the community

    > **Elite Status:**
* **Code:** Specify the code corresponding to the status to be created
* **Name:** Specify the name of the status associated with the corresponding code

    > **Expiration Information**
* **Expiration Type:** Select the expiration type for the community
* **Frequency:** Indicate the periodicity until expiration
* **Grace Days:** Set the grace days after the community expires

Once you have finished configuring the settings, click on the ***"Save"*** button.

</br>

# Contingencies

In ATIONet, a contingency is a manually entered transaction. In this section, you can view and create contingencies. Please note that contingencies are transactions without prior authorization.

The fields to be completed are as follows:
* **Description:** Enter the reason for the contingency.
* **Date:** Enter the date of the contingency.
* **Time:** Enter the time of the contingency.
* **Location:** Select the location associated with the contingency.
* **Terminal/Controller:** Select the terminal/controller associated with the contingency.
* **Community:** Enter the community associated with the contingency. 
* **Receipt number:** Enter the receipt number for the original transaction.
* **Loyalty account:** Enter the loyalty account corresponding to the contingency (only accounts with assigned identifiers will be selectable).

    >  ***PRODUCTS***

* **Product:** Enter the product associated with the contingency. 
* **Quantity:** Enter the quantity corresponding to the product.
* **Amount:** Enter the corresponding amount per unit.

When you have finished filling in the fields, press the ***Save*** button.

</br>

# Contingencies Processes

In this section, you can view the processes corresponding to contingencies related to loyalty accounts.
(For more details regarding the configuration of this section, please ***contactsupport@atioinc.com***).

</br>

# Current Account

The Loyalty Current Accounts section shows the available balance of the accounts, as well as all account movements. 

</br>

# Discount Rules

In this section, you can view, edit, and create/delete discount rules.
To create a new discount rule, click the ***New*** button and fill in the following information:

* **Code:** Enter the code for the rule in question

* **Description:** Enter a description to facilitate identification of the rule

* **Community:** Indicate the community to which the rule will be linked

* **Type:** Indicate the type of discount (it can be a percentage or a fixed amount per transaction/unit)

* **Date from/to:** Enter the duration of the discount rule

* **Limits:** Set the allowed limit for the discount in question.

     > ***These limits are divided as follows:***
  - Daily Transaction Limit
  - Monthly Transaction Limit
  - Discount Amount Limit
  - Discount Limit by Quantity
  - Monthly Amount Limit
  - Monthly Quantity Limit

* **SKU:** Enter the SKU(s) associated with the rule and its specific parameters

* **Elite Status:** Enter the status to which this rule will apply

Once you have entered all the necessary information, click ***Save*** to complete the configuration.

</br>

# Exceptions

ATIONet separates unauthorized transactions into two sections: ***Exceptions*** and ***[Rejected Transactions](#rejected-transactions)***. Exceptions are transactions that did not pass the system's strict validations or those that are detected as possible fraud.

</br>

# Identities

In this section, you can filter and view the entities previously created in the ***"Customers"*** section

In turn, by clicking on the ***"Document number"*** in that view, you can access the details of that entity

</br>

# Loyalty Coupons

In this section, you can view the Coupons applied to the respective transactions related to the loyalty accounts.
(For more details regarding the configuration of this section, please ***contactsupport@atioinc.com***)

</br>

# Loyalty Coupons Processes

In this section, you can view the processes corresponding to the coupons applied in the respective operations related to loyalty accounts.
(For more details regarding the configuration of this section, please ***contactsupport@atioinc.com***)

</br>

# Points Rules

In this section, you can view, edit, and create points rules.
To create a new points rule, press the ***New*** button and fill in the following information:

* **Code:** Enter the code for the rule in question.

* **Description:** Enter a description to make it easier to identify the rule.

* **Type:** Indicate the type of discount (it can be a percentage or a fixed amount per transaction/unit).

* **Points:** Set the number of points corresponding to the rule

* **Units/Amount:** Set the quantity/amount required for points to be awarded.

* **Amount:** Set the total amount of points to be awarded.

* **Date from/to:** Enter the dates corresponding to the duration of this points rule.

* **Time from/to:** Enter the time corresponding to the duration of this points rule.

* **Enabled days of the week:** Enter the days of the week for which this rule applies.

* **Community:** Indicate the community to which the rule will be linked.

Once you have entered all the necessary information, click ***Save*** to complete the configuration.

</br>

# Redemptions

In this section, you can view the redemptions made, as well as make new redemptions.
To make a new redemption, press the ***New*** button:

* **Description:** Enter a description for the desired redemption
* **Date/time:** Enter the date on which the redemption is made
* **Location:** Enter the location corresponding to the redemption
* **Terminal/controller:** Enter the terminal/controller corresponding to the redemption
* **Community:** Add the community associated with the redemption 
* **Loyalty account:** Add the loyalty account associated with the adjustment

    > Then, select the products you want to redeem and the quantity of each:
* **Product:*** Select the product you wish to redeem.
* **Quantity:*** Select the quantity to be exchanged.

    > Once you have selected these, select ***Register*** to confirm the desired exchange.

Once you have finished your selection, press ***Save***.

</br>

# Service Entry Classes

In this section, you can configure up to 3 types of service entries.
Once a type has been created, it can be accessed and viewed as an additional section, within which you can view and create codes corresponding to the type of service entry.

</br>

# Service Entry Types

In this section, you can view, edit, and create service entry types.
To create a service entry type, press the ***New*** button and complete the following information:

* **Code:** Enter the code for the service entry in question.

* **Description:** Enter a description to facilitate identification of the service entry type.

* **Active:** Check this box to determine whether this type of service entry is active or inactive.

* **Accept manual entry:** Check this box to determine whether or not this service entry type accepts manual entry.

* **Available from/to:** Enter the dates corresponding to the duration of the service entry type.

</br>

# Service Entry Types Groups

In this section, you can edit and view the status of service entry type groups.

To create a new service entry type group, press the ***New*** button and fill in the following information:

   > **Information:**
* **Code:** Enter the desired code for the group
* **Active:** Check this option if you want the group to be created 

	> **Items:**
* **Service entry type:** Enter the service entry type code you want to assign 

Once you have finished the corresponding configuration, press the ***Save*** button to successfully create the group.

</br>

# Service Files

This section is divided into two views.
The ***"Lists"*** view and the ***"Entries"*** view, both of which can be selected using filters.
The ***"Lists"*** section is mainly organized based on the subaccount, i.e., a subaccount can have multiple service entries, but only one code. If you interact with the code in that view, you will automatically be taken to the service entries filtered by the selected code. This is the section referred to as ***"Entries"*** in the filters.

By clicking on the ***New*** button, you can create a new service entry.

   > ***Information:***

* **Vehicle/Driver:** Enter the vehicle/driver corresponding to the service entry (if the vehicle/driver already has a code, it will be applied automatically).

* **Service Sheet Code:** Enter the code corresponding to the service entry. 

* **Service Entry Type Group:** Enter the group code for the service entry type

* **Service Entry Type:** Select the type of service entry

* **Entry:** Set the entry date for the service entry

* **Expiration date:** Select the expiration date

* **Odometer:** Indicate the odometer corresponding to the subaccount

* **Engine hours:** Indicate the engine hours corresponding to the subaccount

(If you have established a ***"Service entry class"***, a section will appear with the class created so that you can enter a class code)

</br>

# Transactions

The transactions view is one of the most important views in ATIONet. In this view, you can see all successful transactions.
The filter panel has all of these fields available:

* **Authorization code:** Enter the authorization code associated with the transaction.
* **Type:** Select the transaction type corresponding to the operation.
* **Company:** Select the company associated with the transaction.
* **Merchant:** Select the merchant associated with the transaction.
* **Site:** Select the site associated with the transaction.
* **Terminal/Controller:** Select the terminal associated with the transaction.
* **Community:** Enter the name of the community associated with the transaction.
* **Loyalty Account:** Enter the name of the loyalty account.
* **Receipt Number:** Enter the receipt number associated with the transaction.
* **Identity:** Enter the number or name of the identity associated with the transaction.
* **SKU:** Select the SKU corresponding to the transaction.
* **Identity Options:** Select the corresponding characteristics of the identity associated with the transaction 
* **Batch Number From/To:** Enter the batch numbers between which the transaction took place.
* **Date From/To:** Enter the start and end dates associated with the transaction.
* **Time From/To:** Enter the start and end times associated with the transaction.

Once you have filtered, click Search and the transactions that meet the filter criteria will be listed.

If you want to see the transaction details, click on the ***"Authorization Code"*** and this will take you to a detailed view of the transaction.

</br>

# Transfers

In this section, you can view the transfers made between loyalty accounts.
To make a new transfer, click on the ***New*** button:
* **Description:** Enter a description for the transaction 
* **Date:** Enter the date on which the transfer is made
* **Time:** Enter the time the transfer was made
* **Location:** Enter the location corresponding to the transaction 
* **Terminal/Controller:** Enter the terminal corresponding to the transfer
* **Community:** Enter the community associated with the account
* **Loyalty Account:** Enter the loyalty account from which the amount will be withdrawn
* **Secondary Account:** Enter the account to which the amount will be transferred 
* **Amount:** Enter the amount to be sent in the transfer

Once you have completed the relevant information, press the ***Save*** button:

</br>

# Units

In this section, you can create units that will be applied to discounts and other operations.
To create a new unit, press the ***New*** button:

* **Code:** Enter the code that will identify the unit
* **Name:** Enter the name of the unit
* **Currency:** Select the currency for that unit


</br>


[Volver al inicio](#contenido) 	:arrow_up:
