![ationetlogo](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/ATIOnetLogo_250x70.png)

# Contents

- [Administration](#administration)
	- [Brands](#brands)
	- [Companies](#companies)
	- [Companies Groups](#companies-groups)
	- [Companies Groups – Movements](#companies-groups--movements)
	- [Drivers](#drivers)
 	- [External Documents](#External-Documents)
	- [Fuels](#fuels)
	- [Fuels Masters Groups](#fuels-masters-groups)
	- [Identifications](#identifications)
	- [Identifications Models](#identifications-models)
	- [Identifications Providers](#identifications-providers)
	- [Identification Renewal Processes](#Identification-Renewal-Processes)
	- [Installations](#installations)
	- [Locations](#Locations)
	- [Merchants](#merchants)
	- [Notifications](#notifications)
	- [Payment Methods](#payment-methods)
	- [Quotations](#Quotations)
	- [Rack Prices](#rack-prices)
	- [Sites](#sites)
	- [SKUs](#skus)
	- [SKUs categories](#skus-categories)
	- [Taxes](#taxes)
	- [Terminals / Controllers](#terminals--controllers)
	- [Vehicle](#vehicle)
	- [Warehouses](#warehouses)
	- [Workflow Instances](#Workflow-Instances)
	- [Zones](#zones)

# Administration
Inside this module you can manage Companies, Merchants, Sites, Identifications, Payment Methods and Users among other things.

## Brands
In ATIONet the term brand refers to the name for each master fuel available in ATIONet. In this section you can consult and create brands.

![Brands](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Brands.PNG)

For every Network ATIONet already has a **DEFAULT** brand created with the following fuels:

![Brand DEFAULT](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Brand%20DEFAULT.PNG)

To create a Brand, click the **New** button:

![Brands New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Brands%20New.PNG)

The fields to complete are the following:

* **Name:** The name of the new brand.
* **Fuel:** Select the ATIONet Master Fuel you wish to rename.
* **Fuel Name:** Input the new name for your fuel.

When you have finished filling in the fields, click the **Save** button.

## Companies
In ATIONet the term company refers to the entity that owns the fleet. In this section you can see the existing companies with their details, edit them and/or create new companies. To make queries easier, there is a panel of filters at the top.

![Company Menu](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Company%20Menu.PNG)

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

## Companies Groups
This section lists all company groups created. This feature will allow you to group up companies into one. To make queries easier, there is a panel of filters at the top.

![Companies Groups](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Companies%20Groups.PNG)

To create a Company Group, click on the **New** button.

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

When you have finished filling in the fields, click the **Save** button.

## Companies Groups – Movements
This sections lists all movements (deposits, withrawals, completions, etc.) for all the Company Groups.

![Companies Groups Movements](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Companies%20Groups%20Movements.PNG)

Note that you must first complete the field **Companies Group** and then click on the **Search** button in order to see all their movements.

To create a movement, click on the **New** button:

![Companies Groups Movements New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Companies%20Groups%20Movements%20New.PNG)

The fields to complete are the following:

* **Description:** Input a short description of the movement.
* **Companies Group:** Select the Companies Group associated to the movement.
* **Type:** Select the type of movement (deposit or withrawal).
* **Amount:** Input the amount associated to the movement.

When you have finished filling in the fields, click the **Create** button.

## Drivers
This view lists drivers that have been created. To make queries easier, there is a panel of filters at the top.

![Drivers](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Drivers.PNG)

## External Documents

The **External Documents** view will allow the Network to host any documentation or report whose origin is outside the ATIONET portal processes. On the other hand, companies or businesses will be able to view and download these files.

To make use of this feature, an integration will be required to consume the corresponding API.

![External Documents](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/External%20Documents.PNG)

## Fuels
This view lists fuel mappings and their respected code for all sites that have **Required Fuel Mapping** option enabled (for more info on fuel mapping click [here](#sites)). To make queries easier, there is a panel of filters at the top.

![Fuel Menu](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Fuel%20Menu.PNG)

To create a fuel mapping, click the **New** button.

![Fuels New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Fuels%20New.PNG)

The fields to complete are the following:

* **Site:** Select the site associated to the fuel mapping.
* **Fuels Masters:** Select the master fuel associated to the fuel mapping.
* **Code:** Input the code associated to the fuel mapping.

When you have finished filling in the fields, click the **Save** button.

## Fuels Masters Groups
This view lists all fuel groups created. This option enables the possibility to group up several master fuels into one. To make queries easier, there is a panel of filters at the top.

![Fuel Masters Groups](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Fuels%20Masters%20Groups.PNG)

To create a new group, click the **New** button.

![Fuels Masters Groups New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Fuels%20Masters%20Groups%20New.PNG)

The fields to complete are the following:

* **Code:** Input the fuels masters group code.
* **Name:** Input the name of the fuels masters group.
* **Description:** Input a description for the fuels masters group.
* **Fuel:** Select all fuels associated to the fuels masters group.
* **CO2 Emission Coefficient:** Input the coefficient for the CO2 emission of all fuels in the group.

When you have finished filling in the fields, click the **Save** button.

## Identifications
The identification is the physical means used by ATIONet to identify a vehicle or driver. ATIONet supports various types of identification, such as card, TAG, chip, ATIONet card, manual entry, barcode and iButton. When an identification is associated to a Vehicle or Driver, a sub-account is created.

In this section the identification already created will be listed. In the options column you can edit the identification, enable or disable it and release it. To facilitate queries, there is a panel of filters at the top.


![Identifications](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Identifications.PNG)

To create an identification, click the **New** button.

![New Identification](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Identifications%20New.PNG)

The fields to complete are the following:

* **Type:** Can be Card, TAG, Chipkey, Manual Entry, ATIOnet Card or ATIOnet TAG.
* **Model:** The model of the type of identification selected in Type.
* **Type of use:** This is divided between fleet, loyalty or dual.
* **Program:** The program to which this identification will be assigned in case you have chosen "Type of use: fleet/dual".
* **Community:** The community to which this identification will be assigned in case you have chosen "Type of use: Loyalty/dual".
* **Label:** The name on the card (for example Pablo Pérez)
* **Track:** The track is the information that has the identification engraved inside it. It is divided into three parts. In this field you can edit what the second field of the track contains.
* **PAN:** A number between 1 and 19 characters found in the identification.
* **Automatically Generated:** By checking this option, the label, track and PAN fields will be generated automatically.
* **PIN:** The PIN of the identification (this option will only be available if the identification model has the PIN option enabled).

When you have finished filling in the fields, click the **Save** button.

## Identifications Models

The identifications models vary according to the customer's needs. They can be of the following types:

* **Card:** Card type identifications. It can be of magnetic stripe or reading by approximation.
* **TAG:** Image type identifications (usually in QR format). It is generally used as a sticker attached to the windshield of the vehicle.
* **Chipkey:** Key type identifications, used by a specific terminal system.

![Identification Models](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Identifications%20Model.PNG)

To create an identificaiton model, click the **New** button.

![New Identification Model](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Identifications%20Model%20New.PNG)

The fields to complete are the following:

* **Type:** Can be Card, TAG, Chipkey or Manual entry type.
* **Description:** The description of the new identification model.
* **Installable:** Identifications with this feature can only be assigned by means of installation.
* **Personalized:** If it is personalized or not.
* **Reusable:** Identifications with this function active can be reused if they are unassigned (otherwise they would be disabled).
* **Supports multiple assignments:** This option allows the driver/vehicle to have multiple identifications of this model.
* **Valid expiration date:** Whether the expiration date is valid or not.
* **Ignore the behavior of the vehicle ID in the terminal:** When this option is activated, the behavior of the related vehicle ID in the terminal will be ignored. In other words, if a request were to be made for a transaction, it will be skipped. A situation where this function can be applied is for a "Gift Card". These do not have any vehicle ID, so if you wish to operate on a site that requests a vehicle ID, without this feature, the Gift Card will be rejected.
* **Custom Track:** If this option is activated, a track number can be determined at will instead of being generated automatically.
* **Single use:** If this option is activated, this identification's model cannot be used multiple times.
* **Notify assignment:** When this function is activated, an e-mail will be sent to the entity to which this identification is assigned.
	* Enabling this feature will enable the "File attachment in notification" option, which allows the QR to be attached to a PDF file.
		* Finally, in case the previous function is enabled, a third function will be enabled called, "Encrypted attachment". This will allow that when the file arrives, a password will be requested, being the vehicle code.

-INSERTAR IMAGEN-

* **No Offline support:** This function allows you to operate only when the system is in the Online state.
* **Require PIN:** This function allows us to determine whether a PIN is required, and also requires us to set the number of numbers requested for the PIN.
	* Activating this function will enable a new function called "Require PIN change" which is a one-time option for terminals that allow a PIN to be set directly from the station.

-INSERTAR IMAGEN-

* **Validate inactivity period:** This function allows us to evaluate the automatic inactivation of an identification corresponding to this model according to the established period.

-INSERTAR IMAGEN-

* When this function is activated, a box will be enabled in which the period in question can be set.

* **Custom Track Type:** Enabling this function allows you to set a Prefix and a Suffix to the Track.
* **Track Encryption:** This function gives the identifiers of this model the capacity to be verified with an encrypted track, which will be recognized by ATIONET and validated if it exists. For the reading of the encrypted track to be applied, the corresponding property must be configured in the terminal.

-INSERTAR IMAGEN-

When you have finished filling in the fields, click the **Save** button.

## Identifications Providers
In this section you can consult and create any supplier you wish to send your identifications to production. To facilitate the queries, there is a filter panel at the top. 

![Identification Providers](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Identification%20Provider.PNG)

To create a provider, click the **New** button.

![Identification Providers New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Identification%20Provider%20New.PNG)

The fields to complete are the following:

* **Name:** Enter the name corresponding to the supplier.
* **E-mail:** Enter the supplier's contact e-mail address.
* **Email Template:** Enter the body of the email you wish to send to your supplier.
* **Delivery label:** This field is optional. When marked as active, an option will appear to upload a file to be used as a template.
* **Notify grouping:** By marking this field as active, a summary of the grouping configurations that were executed in the identification scheduler process will be appended to the beginning of the mail body.
* **Export file configuration:** Select the format in which you want to send the identification information to your supplier. You can send it as Excel, CSV or Text. You can also select what information to send in the file (First Name, Last Name, Card Number, Track Number, etc.).

When you have finished filling in the fields, click the **Save** button.

## Identification Renewal Processes

In this section you can view and renew identifications. In the filters option, you can filter by execution statuses, process statuses and the corresponding schedules in which the process was executed. 

-INSERTAR IMAGEN-

* ***Launch Process:*** When this process is confirmed, existing identifications will be massively renewed.


## Installations
In ATIONet the fact that identifications need to be placed by a technician is known as **Installations**.

In this section you can consult all the installations carried out, listed by Date, Work Order, the identifications installed, the vehicle in which the identification was installed, the deposit from which the identification was removed and the technician who installed it.

![Installations](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Installation.PNG)

To create an installation, click the **New** button.

![Installation New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Installation%20New.PNG)

The fields to complete are the following:

* **Work Order:** The unique number related to the work order document.
* **Technician:** The technician who carried out the installation.
* **Company:** The company of which the vehicle to which the installation was made was a part.
* **Date:** The date on which the installation was carried out.
* **Contract:** The contract to which the vehicle is linked.
* **Vehicle:** The vehicle to which the installation was made.
* **Deposit:** The deposit is the physical place where the identifier was removed to place it.
* **Has OBD:** Mark this option if the vehicle has an On-Board Diagnostics.

If you have OBD, more fields will be displayed:

* **ID:** Enter the OBD ID.
* **Model:** Select the OBD model.
* **Sensor:** Tilde this option if the OBD has a sensor.
* **Initial Odometer:** Enter the initial odometer.
* **Proportion:** Enter the OBD proportions.

Then, in the Identification section select the Identification. When finished, click the **Save** button.

## Locations

In this section users can add specific locations for which a specific type of identification is enabled.

-INSERTAR IMAGEN-

In the **New** option, locations are added, for which a minimum of information is required:

-INSERTAR IMAGEN-

* **Code:** An alphanumeric pattern is required.
* **Country/ State/ City/ Street:** The semi-exact location of the place you wish to enter is specified.
* **Contact Telephone:** The telephone/mobile number of a contact person at the location is required.
* **Type of Identification:** The type of Identification desired for this location is specified.
* **Identification Model:** The desired Identification model for that location is specified.

## Merchants
In ATIONet the term merchant refers to the company that owns the sites. In this section you can view, create and edit all merchants. To make queries easier, there is a panel of filters at the top.

![Merhcants](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Merchants.PNG)

To create a merchant, click the **New** button.

![Merchants New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Merchants%20New.PNG)

The fields to complete are the following:

* **Tax Payer Id:** Input the merchant taxpayer identification.
* **Active:** Checkmark to enable/disable the merchant.
* **Code:** Input the merchant unique code.
* **Name:** Input the merchant name.
* **Automatically Generated:** Checkmark this option to have the **code** automatically generated.
* **Street 1:** Input the merchant primary street.
* **Street 2:** Input the merchant secondary street (if applicable).
* **Zip Code:** Input the merchant zip code.
* **City:** Input the merchant city.
* **Country:** Input the merchant country.
* **State:** Input the merchant state.
* **Contact Name:** Input the merchant contact name.
* **Contact Email:** Input the merchant contact email.
* **Phone Number 1:** Input the merchant primary phone number.
* **Phone Number 2:** Input the merchant secondary phone number (if applicable).

When you have finished filling in the fields, click the **Save** button.

## Notifications
In this section each user can select their own notifications to be received either by email or sms.

![Notifications](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Notification.PNG)

1. ***Inventory***

-INSERTAR IMAGEN-

* **New Delivery notification:** Receive a notification for each delivery detected.
* **Low inventory notification:** Receive a notification when the inventory is low.
* **Water volume notification alert:** Receive a notification when water is low.

2. ***Contract***

  -INSERTAR IMAGEN-
   
* **Low contract balance notification:** Receive a notification when the balance of a contract is low.
* **Notification of empty contract balance:** Receive a notification when a contract has no balance.
* **Credit percentage notification:** Receive a notification when a credit percentage is reached (click on the pencil to set the percentage).
* **Low balance notification:** Receive a notification when an amount is reached (click on the pencil to set the amount).
* **Company contract deposit:** Receive a notification when a deposit to a contract is detected.

3. ***Identification***

-INSERTAR IMAGEN-

* **Notification of Idsentifications at risk of expiration:** Receive a notification when an identification is about to expire.

4. ***Loyalty***

* -INSERTAR IMAGEN-

* **New Loyalty Account Notification:** Receive a notification when a new loyalty program is detected.
* **Loyalty point accumulation notification:** Receive a notification when an accumulation is detected.
* **Loyalty exception notification:** You receive a notification when an exception is detected.

5. ***Billing***

-INSERTAR IMAGEN-

* **Notification of Billing process:** You receive a notification when a billing process is detected.
* **Merchant Charges:** Receive a notification when merchant charges are detected.
* **External charges:** Receive a notification when external charges are detected.

6. ***Transactions***

-INSERTAR IMAGEN-

* **Notification of new contingency transactions:** Receive a notification when a new contingency is detected.
* **Notification of transaction to be reviewed:** Receive a notification when an exception marked for review was detected.
* **Fuel Exit Exception:** Receive a notification when a fuel exit exception was detected.
* **Transaction exception:** Receives a notification when an exception is detected.
* **Incorrect PIN:** Receive a notification when a rejected transaction is detected due to an incorrect PIN.
* **Rejected transaction:** Receive a notification when a rejected transaction is detected.
* **Disputed transactions:** Receive a notification when a disputed transaction is detected.

7. ***Company***

-INSERTAR IMAGEN-

* **Company Activation/Deactivation:** Receive a notification when a change in the status of a company is detected.

8. ***Trade***

-INSERTAR IMAGEN-

* **Trade Activation/Deactivation:** Receive a notification when a change in the status of a trade is detected.
* **Site Offline Transaction Maximum Reached:** Receive a notification when it is detected that the site has reached the maximum possible Offline transactions.

9. ***Fleet Workflow***

-INSERTAR IMAGEN-

* **Fleet workflow created:** Receive a notification when it is detected that a fleet workflow has been created.

### Company Notifications
In this section company users can configure their own notifications (inside their company profiles in ATIONet).

![Notification Company](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Notification%20Company.PNG)

1. ***Contract***
* **Low contract balance notification:** Receive a notification when the balance of a contract is low.
* **Notification of empty contract balance:** Receive a notification when a contract has no balance.
* **Credit percentage notification:** Receive a notification when a credit percentage is reached (click on the pencil to set the percentage).
* **Low balance notification:** Receive a notification when an amount is reached (click on the pencil to set the amount).
* **Company contract deposit:** Receive a notification when a deposit to a contract is detected.

2. ***Liquidation***
* **External charges:** Receive a notification when external charges are detected.

3. ***Transactions***
* **Transaction exception:** Receives a notification when an exception is detected.
* **Non-blocking rule authorization:** Receives a notification when a non-blocking rule authorization is detected.
* **Identification enabled/disabled:** Receive a notification when an identifier was enabled/disabled.
* **Requested identifiers:** Receive a notification when a request for identification is detected.
* **Rejected transaction:** Receive a notification when a rejected transaction is detected.
* **Disputed Transactions:** Receive a notification when a disputed transaction is detected.

4. ***Vehicle fleet***
* **Vehicle Odometer Limit:** Receive a notification when a vehicle's odometer is reached (click on the Vehicle List button to set the odometer and select the vehicle associated with the notification).

5. ***Company***
* **Company Activation/Deactivation:** Receive a notification when a change in the status of a company is detected.
 

## Payment Methods
Payment methods are the different ways in which you can pay for a transaction: cash, credit card, debit card, gift cards, etc. To make queries easier, there is a panel of filters at the top.

![Payment Methods](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Payment%20Methods.PNG)

To create a payment method, click the **New** button.

![Payment Method New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Payment%20Methods%20New.PNG)

The fields to complete are the following:

* **Code:** The code of the new payment method.
* **Description:** The description of the new payment method.

When you have finished filling in the fields, click the **Save** button.

## Quotations

In this section you can configure the quotation of multiple currencies. 

-INSERTAR IMAGEN-

-INSERTAR IMAGEN-

The sections to be configured are as follows:
* **Currency of Origin:** Select the currency of the country of origin.
* **Destination Currency:** Select the currency of the destination country.
* **Conversion Value:** Enter the currency conversion value.
* **Start Date:** Enter the date on which this process will begin.
* **Time from:** Enter the time at which this process will start.


## Rack Prices
In this section you can view all the rack prices generated. These prices are the ones used when a company contract has no prices configured (if the rack prices option is enabled within the company contract configuration). 

1. ***New price:*** 

-INSERTAR IMAGEN-

* **Name:** Enter a name to identify the price
* **Code:** Enter a code to identify the price
* **Currency:** Enter the desired currency
* **Grouping type:** This option enables the possibility of also configuring the fuel by zones (these are created in the **Administration>Zones** section).

2. ***Fuel prices:***

-INSERTAR IMAGEN-

* **Fuel:** Enter the fuels for which these prices are to be applied
* **Value:** Enter the value of the prices
* **Date and Time:** Enter the date and time from which this price will start to apply (It is optional to set a date and time for which this price will stop applying).

3. ***Prices per fuel and site:***

-INSERTAR IMAGEN-

* **Fuel:** Enter the fuels for which these prices are to be applied
* **Value:** Enter the value of the prices
* **Site:** Enter a site for which these prices apply.
* **Date and Time:** Enter the date and time from which this price will start to apply (It is optional to set a date and time for which this price will stop applying).


When you have finished filling in the fields, click the **Save** button.

## Sites
In ATIONET the site represents the service station. This section shows the sites already created, as well as the possibility to edit and create new ones. Taxes can be added to the sites directly from the **Options** column. To facilitate queries, there is a filter panel at the top.

![Sites](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Sites.PNG)

To create a site, click the **New** button.

![Sites New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Sites%20New.PNG)

The fields to complete are the following:
To create a site, click on the New button.
 The fields to be completed are the following: Information
* **Merchant:** Select the merchant associated with the site.
* **Code:** Enter an alphanumeric code (limited to 50 characters) which will be associated with the site.
* **Zone:** Select the zone associated with the site.
* **Automatically generated:** Check this option to have the code generated automatically.
* **Brand:** Select the brand associated with the site.
* **Language:** Select the language associated with the site.
* **Short name:** Enter the short name of the site.
* **Full name:** Enter the full name of the site.
* **Street 1:** Enter the main street of the site.
* **Street 2:** Enter the secondary street of the site.
* **Industry:** Select the industry associated with the site.
* **Time zone:** Select the time zone corresponding to the site.
* **Zip Code:** Enter the zip code of the site.
* **City:** Enter the city of the site.
* **Country:** Enter the country of the site.
* **State:** Enter the state of the site.
* **Phone number 1:** Enter the main phone number of the site.
* **Phone number 2:** Enter the secondary phone number of the site.
* **Require Fuel Mapping:** Checkmark this option if specific fuel codes need to be configured for the site (if not, [ATIONet Master Fuel Codes](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/C%C3%B3digos%20Maestros%20de%20Combustible.PNG) will be used).
* **Recipient Emails:** Enter the email addresses associated with the site (they will receive site statements).
* **Latitude:** Enter the latitude of the site.
* **Longitude:** Enter the length of the site.
* **Currency:** Select the currency associated with the site.
Notification - Alert Rule
* **Low Inventory Notification:** Enter the low inventory quantity. When it is reached, the recipient's email contacts will receive a notification.
* **Water volume notification alert:** Enter the low water volume. When it is reached, contacts in the recipient emails will receive a notification.

***Services***

-INSERTAR IMAGEN-

Select a site to register. After this, the list of services that this site has will be assigned and the current one will be deleted. In the "Services" tab you can select one of the services enabled for that site.

When you have finished filling in the fields, click the **Save** button.

## SKUs
Stock Keeping Units (SKUs) are non-fuel products. In this section you can consult the created SKUs, edit them and create new ones. To facilitate queries, there is a filter panel at the top. 

-INSERTAR IMAGEN-

To create a SKU, click on the **New** button.

-INSERTAR IMAGEN-

The fields to be completed are as follows:
* **Code:** Enter an alphanumeric code (maximum 20 characters) for the SKU.
* **Description:** SKU description.
* **Short Description:** A shortened version of the SKU description.
* **Extra Short Description:** An even shorter description of the SKU.
* **SKU Product Type:** Select the type of product.
* **Fuel Product:** Check this option if the SKU is a fuel product.
* **SKU Category:** Enter the category to which the SKU belongs.
* **Unit of measure:** Enter the unit in which the SKU is measured (Liters, Gallons, etc.).
* **Reference value per unit:** Indicate the value and currency per unit of the product.
* **Saleable:** Check this option if the SKU is saleable.
* **Weighable:** Check this option if the SKU is weighable.
* **Fractionable:** Check this option if the SKU is fractionable.
* **Storable:** Check this option if the SKU is storable.
* **Consignment:** Check this option if the SKU is on consignment.
* **Availability From/To:** Select the dates between which the SKU is available.
* **Is POS:** Check this option if the SKU is sold at the point of sale.
* **Dry Fleet:** Check this option if the SKU is a dry product.
* **Reward:** Check this option if the SKU can be redeemed for reward points.
* **Service:** Check this option if the SKU is a service.
* **Loyalty:** Check this option if the SKU accumulates points.

***Items:***

-INSERTAR IMAGEN-

* **POS code format:** Select the POS code format.
* **POS Code:** Enter a point-of-sale code.

When you have finished filling in these two fields, press the Add button.

* **Taxes:** Enter the tax code of the SKU.

When you have finished filling in the fields, click the **Save** button.

## SKUs categories
In this section you can consult the categories of SKUs (Stock Keeping Units) already created, edit them or create new ones. To make queries easier, there is a panel of filters at the top.

![SKUs Categories](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/SKUs%20Category.PNG)

To create a SKU Category, click the **New** button.

![SKUs Categories New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/SKUs%20Category%20New.PNG)

The fields to complete are the following:

* **Code:** The SKU category code.
* **Name:** The name of the SKU category.
* **Short Description:** A short description of the SKU category.
* **First/Second Parent Category:** For example, if the SKU category was "Camel Cigarettes", the first parent category would be "Tobacco" and the second would be "Cigarettes".
* **Is POS:** Checkmark this option if the SKU category can be purchased at the point of sale.
* **Dry Fleet:** Checkmark this option if the SKU category is dry fleet.
* **Reward:** Checkmark this option if it can be redeemed for loyalty points.
* **Service:** Checkmark this option if it is a service.
* **Loyalty:** Checkmark this option if the purchase of the product accumulates loyalty points.

When you have finished filling in the fields, click the **Save** button.

## Taxes
Inside this section you can consult all taxes created, edit them or create new ones.

The tax table displays:
* **Code:** Tax Code.
* **Description:** Tax description.
* **Type:** Type of tax (It can be a fixed tax, a percentage tax or a fixed tax per unit).
* **Amount:** The amount of tax (In the case of percentage tax, the percentage).
* **Date From / Date To:** Range of dates.
* **Options:** Edit the tax.

![Taxes](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Taxes.PNG)

To create a  tax, click  the **New** button.

![Taxes New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Taxes%20New.PNG) 

The fields to complete are the following:

* **Code:** The code of the new tax.
* **Description:** The description of the new tax.
* **Type:** Type of tax (Can be a fixed tax, a percentual tax or a fixed tax per unit).
* **Date from:** The date on which the tax takes effect.
* **Amount:** The amount of the tax (In the case of percentual tax, the percentage).

After filling in the fields **Date from** and **Amount** click the **Add** button. 

When you have finished filling in the fields, click the **Save** button.

## Terminals / Controllers

Within this section you can view, create and edit all terminals/controllers. The terminal is the point of sale of the site and the controller manages the pumps. For easy queries, there is a filter panel at the top.

-INSERTAR IMAGEN-

To create a Terminal/Controller, click on the New button.

-INSERTAR IMAGEN-

The fields to be completed are as follows:
* **Merchant:** Select the Merchant associated with the terminal/controller.
* **Site:** Select the site associated with the terminal/controller. 
* **Active:** Check the box to activate/deactivate the terminal/controller.
* **Terminal/controller type:** Select the type of terminal/controller (ATIO-ControlGas, ATIO-NanoCPI, ATIO StandAlone, VF-Commander, etc.).
* **Model:** Select the terminal/controller model.
* **Code:** Enter the terminal/controller code, which can be an alphanumeric code of up to 50 characters.
(ATIONET generates one automatically, but you can edit it. Except for the first 3 characters, as they represent the network subscription code).
* **Description:** Enter a description corresponding to the terminal/controller.
* **Assisted Pre-Authorizations Only:** Check the box to enable the terminal to perform assisted pre-authorizations.
* **TAG reader present:** Check this option if the terminal is capable of reading TAGs.
* **Driver ID Usage:** Select the action that ATIONet will take associated to the Driver ID of the transactions (None, Secondary Track or Code Validation).
* **Vehicle ID Usage:** Select the action that ATIONet will take associated to the Vehicle ID of the transactions (None, Secondary Track or Code Validation).
* **Maximum Volume Cut-off:** Enter the maximum volume that the terminal/controller will allow.
* **Maximum Amount Cut-off:** Enter the maximum amount to be authorized by the terminal/controller.
* **Operating system:** Enter the operating system of the terminal/controller.
* **Serial number:** Enter the serial number of the terminal/controller.
* **Track Encryption:** By entering a value, the terminal will be able to recognize an encrypted track and it will be recognized by ATIONET as a value if it exists. (IMPORTANT: For this reading to apply, the identifier model must be configured with the corresponding property).

***Configuration***

In this section you can indicate that the terminal will operate in offline mode (with the Local Agent) with the same configuration it has when online. Fields to complete: Message, Property Name, Factor Configuration, Modifier Configuration, Transaction Type.

When you have finished filling in the fields, press the **Add** button if you have completed the configuration, and finally **Save**.

## Vehicle
This view shows all the vehicles that have been created. Remember that it is not mandatory to load the vehicles to be able to operate, it is only necessary if you decide to associate the IDs to the vehicles. To facilitate queries, there is a filter panel at the top.

-INSERTAR IMAGEN-

In the **Options** column you can:
* **Assign Identifiers:** Assign/unassign identifiers to the vehicle.
* **Renewal of Identifiers:** Renew the identifiers associated with the vehicle.
* **Service Sheet:** Establish the service performed by the corresponding vehicle.
* **Favorites:** Add the vehicle to the favorites module.

## Warehouses
In this section you can create/edit warehouses. Warehouses is where installed identifications are stored.

![Warehouses](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Warehouses.PNG)

To create a Warehouse, click the **New** button.

![Warehouses New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Warehouses%20New.PNG)

When you have finished filling in the fields, click the **Save** button.

## Workflow Instances

In this section you can view the contingencies pending approval of the loyalty section.

## Zones
In this section you can create/edit zones. Zones is an area where several sites are associated to it. Generally a Territory Manager is associated to specific zone(s). To make queries easier, there is a panel of filters at the top.

![Zones](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Zones.PNG)

To create a Zone, click the **New** button.

![Zones New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Zones%20New.PNG)

When you have finished filling in the fields, click the **Save** button.
