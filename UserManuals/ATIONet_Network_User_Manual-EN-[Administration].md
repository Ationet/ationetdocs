![ationetlogo](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/ATIOnetLogo_250x70.png)

# Contents

- [Administration](#administration)
	- [Brands](#brands)
	- [Companies](#companies)
	- [Companies Groups](#companies-groups)
	- [Companies Groups – Movements](#companies-groups--movements)
	- [Drivers](#drivers)
	- [Fuels](#fuels)
	- [Fuels Masters Groups](#fuels-masters-groups)
	- [Gift Card](#gift-card)
	- [Gift Cards Request](#gift-cards-request)
	- [Identifications](#identifications)
	- [Identifications Models](#identifications-models)
	- [Identifications Providers](#identifications-providers)
	- [Installations](#installations)
	- [Merchants](#merchants)
	- [Notifications](#notifications)
	- [Payment Methods](#payment-methods)
	- [Rack Prices](#rack-prices)
	- [Sites](#sites)
	- [SKUs](#skus)
	- [SKUs categories](#skus-categories)
	- [Taxes](#taxes)
	- [Terminals / Controllers](#terminals--controllers)
	- [Users](#users)
	- [Vehicle](#vehicle)
	- [Vouchers](#vouchers)
	- [Warehouses](#warehouses)
	- [Zones](#zones)

## Administration
In this module you can create and edit Companies, Merchants, Sites, Identifications, Payment Methods and Users among other things.

### Brands
In ATIONet the term brand refers to the name for each master fuel available in ATIONet. This section lists all brands created in the Network.

![Brands](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Brands.PNG)

For every Network ATIONet already has a **DEFAULT** brand created with the following fuels:

![Brand DEFAULT](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Brand%20DEFAULT.PNG)

To create a new Brand, click the **New** button:

![Brands New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Brands%20New.PNG)

The fields to complete are the following:

* **Name:** The name of the new brand.
* **Fuel:** Select the ATIONet Master Fuel you wish to rename.
* **Fuel Name:** Input the new name for your fuel.

### Companies
In ATIONet the term company refers to the entity that owns the fleet. In this section you can see the existing companies with their details and edit them if you want. You can also filter them by name and/or code.

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

### Companies Groups
This section lists all company groups created on the Network. This feature will allow you to group up companies into one.

![Companies Groups](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Companies%20Groups.PNG)

To create a new Company Group, click on the **New** button.

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

### Companies Groups – Movements
This sections lists all movements (deposits, withrawals, completions, etc.) for all the Company Groups of the Network.

![Companies Groups Movements](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Companies%20Groups%20Movements.PNG)

Note that you must first complete the field **Companies Group** and then click on the **Search** button in order to see all their movements.

To create a new movement, click on the **New** button:

![Companies Groups Movements New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Companies%20Groups%20Movements%20New.PNG)

The fields to complete are the following:

* **Description:** Input a short description of the movement.
* **Companies Group:** Select the Companies Group associated to the movement.
* **Type:** Select the type of movement (deposit or withrawal).
* **Amount:** Input the amount associated to the movement.

### Drivers
This view lists drivers who have been discharged. You can filter them by name, ID, company, etc. Also, in the options column to the right, you can choose to assign an ID, edit it, or mark the driver as a favorite.

![Drivers](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Drivers.PNG)

### Fuels
This view lists fuel mappings and their respected code for all sites that have **Required Fuel Mapping** option enabled (for more info on fuel mapping click [here](#sites)). To make queries easier there is a panel of filters at the top.

![Fuels](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Fuels.PNG)

To create new fuel mapping, click the **New** button.

![Fuels New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Fuels%20New.PNG)

* **Site:** Select the site associated to the fuel mapping.
* **Fuels Masters:** Select the master fuel associated to the fuel mapping.
* **Code:** Input the code associated to the fuel mapping.

### Fuels Masters Groups
This view lists all fuel groups created. This option enables the possibility to group up several master fuels into one.

![Fuel Masters Groups](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Fuels%20Masters%20Groups.PNG)

To create a new group, click the **New** button.

![Fuels Masters Groups New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Fuels%20Masters%20Groups%20New.PNG)

* **Code:** Input the fuels masters group code.
* **Name:** Input the name of the fuels masters group.
* **Description:** Input a description for the fuels masters group.
* **Fuel:** Select all fuels associated to the fuels masters group.
* **CO2 Emission Coefficient:** Input the coefficient for the CO2 emission of all fuels in the group.

### Gift Card
In this section you can consult the created gift cards. You can perform batch actions such as activating or deactivating them. To make queries easier there is a panel of filters at the top.

To create a new Gift Card, click the **New** button.

![Gift Card](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Gift%20Card.PNG)

The fields to fill in to create a new gift card are the following:

![Gift Card New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Gift%20Card%20New.PNG)

* **Program**: The program to which the gift card will be associated.
* **Contract**: The contract to which the gift card will be associated.
* **Label**: The label is the inscription on the back of the card.
* **PAN**: The PAN is the number between 1 and 19 characters found on the gift card.
* **Track**: The Track is the information contained in the card, which is divided into three parts. In this field, you can customize what the second field of the track contains.
* **Type**: Select whether the gift card is a Card, TAG, Chipkey, Manual Entry, ATIONet Card or ATIONet TAG.
* **Model**: The model of the gift card.
* **Expiration Date**: The expiration date of the gift card.

When you have finished filling in the fields, click the **Save** button.

### Gift Cards Request
In this section, you can consult and request lots of gift cards.

![Gift Cards Request](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Gift%20Card%20Request.PNG)

To order a new set of gift cards, click the **New Request** button.

![Gift Cards Request New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Gift%20Card%20Request%20New.PNG)

The fields to complete are the following:

* **Program**: Select the program assigned to the batch of cards you are requesting.
* **Contract**: Select the contract of the program assigned to the batch of cards you are requesting.
* **Quantity**: Enter the number of cards you want to apply.
* **Expiration Date**: Enter the date the gift cards expire.
* **Type**: Select the type. It can be Card, TAG, Chipkey, Manual Entry, ATIONet Card or ATIONet TAG.
* **Model**: Select the model. It can be ATIONet CG, Card or Gift Card.

### Identifications
The identification is the physical means used by ATIONet to identify a vehicle or driver. ATIONet supports various types of identification, such as card, TAG, chip, ATIONet card, manual entry, barcode and iButton. When an identification is associated to a Vehicle or Driver, a sub-account is created. In this section, the identification already created will be shown. In the options column you can edit the identification, enable or disable it, release it.

![Identifications](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Identifications.PNG)

#### Create a new identification
To create a new identification click on the **New** button in the upper left side.

The form to create a new identification receives the following parameters:

![New Identification](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Identifications%20New.PNG)

* **Type:** Can be Card, TAG, Chipkey, Manual Entry, ATIOnet Card or ATIOnet TAG.
* **Model:** The model of the type of identification selected in **Type**.
* **Type of use:** Can be fleet, loyalty or dual.
* **Program:** The program to which this identification will be assigned.
* **Loyalty program:** The loyalty program to which this identifier will be assigned.
* **Label:** The name on the card (for example Pablo Pérez)
* **Track:** The track is the information that has the identification engraved inside it. It is divided into three parts. In this field you can edit what the second field of the track contains.
* **PAN:** A number between 1 and 19 characters found in the identification. 
* **PIN:** The PIN of the identification (this option will only be available if the identification model has the **PIN** option enabled.

### Identifications Models
The models of identification vary according to the necessity of the client. They can be a Card type (a magnetic card), TAG, Chipkey or Manual Entry (a code entered by hand).

![Identification Models](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Identifications%20Model.PNG)

#### Create a new identification model

To create a new identificaiton model click on the **New** button located on the upper left side.

The form to create a new identification model receives the following parameters:

![New Identification Model](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Identifications%20Model%20New.PNG)

* **Type:** Can be Card, TAG, Chipkey or Manual Entry type.
* **Description:** The description of the new identification model.
* **Installable:** Whether it is installable or not.
* **Personalized:** Whether it is personalized or not.
* **Reusable:** Whether it is reusable or not.
* **Supports multiple assignments:** Whether it supports multiple assignments or not.
* **Valid expiration date:** Whether it validates the expiration date or not.
* **Ignore behavior of vehicle id in terminal:** Ignore the behavior of vehicle id in terminal or not.
* **Requires PIN** If it requires PIN or not.

When you have finished making the changes click the **Save** button.

### Identifications Providers
In this section you can upload any provider you wish to send your identifications to production. You will first have a list of all providers created for the Network.

![Identification Providers](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Identification%20Provider.PNG)

To create a new provider, click the **New** button.

![Identification Providers New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Identification%20Provider%20New.PNG)

The fields to complete are the following:

* **Name:** Input the providers name.
* **Email:** Input the providers contact email
* **E-mail Template:** Input the email body you wish to send to your provider.

<br>

* **File Settings For Export:** Select the format you wish to send the identification information to your provider. You can either send it as Excel, CSV or Text. You can also select what information to send on the file (First Name, Last Name, Card Number, Track Number, etc.).

### Installations
In ATIONet, the fact that identifier needs to be placed by a technician is known as **Installations**. 

In this section you can consult all the installations carried out, listed by Date, Work Order, the identifications installed, the vehicle in which the identification was installed, the deposit from which the identification was removed and the technician who installed it.

![Installations](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Installation.PNG)

To create a new installation, click on the **New** button.

![Installation New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Installation%20New.PNG)

The fields you have to fill in are the following:

* **Work Order**: The unique number related to the work order document.
* **Technician**: The technician who carried out the installation.
* **Company**: The company of which the vehicle to which the installation was made was a part.
* **Date**: The date on which the installation was carried out.
* **Contract**: The contract to which the vehicle is linked.
* **Vehicle**: The vehicle to which the installation was made.
* **Deposit**: The deposit is the physical place where the identifier was removed to place it.
* **Has OBD**: Mark this option if the vehicle has an On-Board Diagnostics.

If you have OBD, more fields will be displayed:

* **ID**: Enter the OBD ID.
* **Model**: Select the OBD model.
* **Sensor**: Tilde this option if the OBD has a sensor.
* **Initial Odometer**: Enter the initial odometer.
* **Proportion**: Enter the OBD proportions.

Then, in the Identification section, enter the Identification. When finished, click the **Save** button.

### Merchants
In ATIONet the term merchant refers to the company that owns the sites. In this section you can view, create and edit all merchants within the Network.

![Merhcants](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Merchants.PNG)

To create a new merchant, click the **New** button.

![Merchants New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Merchants%20New.PNG)

The fields to complete are the following:

* **Tax Payer Id:** Input the company taxpayer identification.
* **Active:** Checkmark to enable/disable the group company.
* **Code:** Input the company unique code.
* **Name:** Input the company name.
* **Automatically Generated:** Checkmark this option to have the **code** automatically generated.
* **Street 1:** Input the company primary street.
* **Street 2:** Input the company secondary street (if applicable).
* **Zip Code:** Input the company zip code.
* **City:** Input the company city.
* **Country:** Input the company country.
* **State:** Input the company state.
* **Contact Name:** Input the company contact name.
* **Contact Email:** Input the company contact email.
* **Phone Number 1:** Input the company primary phone number.
* **Phone Number 2:** Input the company secondary phone number (if applicable).

When finished, click the **Save** button.

### Notifications
In this section each user can select their own notifications to be received either by email or sms.

![Notifications](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Notification.PNG)

1. ***Inventory***
   * **New Delivery notification:** Get a notification for each delivery detected.
   * **Inventorty low notification:** Get a notification when the inventory is low.
   * **Water volume notification alert:** Get a notification when the water is low.
2. ***Contract***
   * **Contract balance low notification:** Get a notification when a contract balance is low.
   * **Contract balance empty notification:** Get a notification when a contract has no balance.
   * **Percent Credit Notification:** Get a notification when a percent credit is reached (click on the pencil to configure the percent).
   * **Low amount balance:** Get a notification when a balance amount is reached (click on the pencil to configure the amount).
   * **Company Contract Deposit:** Get a notification when a deposit to a contract is detected.
3. ***Identification***
   * **Identifications in risk of expiration notification:** Get a notification when an identification is about to expire.
4. ***Loyalty***
   * **New loyalty account notification:** Get a notification when a new loyalty program was detected.
   * **Loyalty points accumulation notification:** Get a notification when an accumulation was detected.
   * **Notification loyalty exceptions:** Get a notification when a exception was detected.
5. ***Billing***
   * **Billing process notification:** Get a notification when a bulling process was detected.
   * **Merchant Charges:** Get a notification when merchant charges were detected.
   * **External Charges:** Get a notification when external charges were detected.
6. ***Transactions***
   * **New contingency transaction notification:** Get a notification when a new contingency was detected.
   * **Transaction to review notification:** Get a notification when an exception marked to be reviwed was detected.
   * **Fuel Out Exception:** Get a notification when an exception for fuel out was detected.
   * **Transaction Exception:** Get a notification when an exception is detected.
   * **Incorrect PIN:** Get a notification when a rejected transaction for incorrect PIN was detected.
   * **Transaction Rejected:** Get a notification when a rejected transaction was detected.
   * **Disputed Transactions:** Get a notification when a disputed transaction was detected.

#### Company Notifications
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

### Payment Methods
Payment methods are the different ways in which you can pay for a transaction: cash, credit card, debit card, gift cards, etc. ATIONet is a tool for a merchant to create their own means of payment: a fuel payment card.

![Payment Methods](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Payment%20Methods.PNG)

To create a new payment method, click on the **New** button in the upper left hand corner.

The form to create a new payment method receives the following parameters:

![Payment Method New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Payment%20Methods%20New.PNG)

* **Code:** The code of the new payment method.
* **Description:** The description of the new payment method.

When finished completing all fields, click the **Save** button.

### Quotations

### Rack Prices
In this section you can view all rack prices generated by the Network. Rack prices are used when a company contract has no prices configured (that is if the option is enables inside the contract configuration).

![Rack Prices](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Rack%20Prices.PNG)

To create a new rack price, click the **New** button.

![Rack Prices New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Rack%20Prices%20New.PNG)

* **Fuel:** Select the fuel associated to the price.
* **Value:** Input the value price of the fuel.
* **Date From:** Input the start date for the fuel price.

When finished completing all fields, click the **Save** button.

### Sites
The Site represents the service station. You assign terminals to a site and also it may have associated a location rules. This section lists the sites already entered in the system and their characteristics and you can also create new ones. You can also add taxes to sites directly from the **Options** column

![Sites](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Sites.PNG)

To create a site, click the **New** button.

![Sites New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Sites%20New.PNG)

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
* **Require Fuel Mapping:** Checkmark this option if specific fuel codes need to be configured for the site (if not, [ATIONet Master Fuel Codes]() will be used).
* **Recipient Emails:** Input the email addresses associated to the site (they will receive the billing statements for the site).
* **Latitude:** Input the latitude of the site.
* **Longitude:** Input the longitude of the site.
* **Currency:** Señect the currency associated to the site.

<br>

* **Inventory Low Notification:** Input the low inventory amount. When reached, contacts in **recipient emails** will receive a notification.
* **Water Volume Notification Alert:** Input the low water volume. When reached, contacts in **recipient emails** will receive a notification.

### SKUs
Stock Keeping Units (SKUs) are non-fuel products. In this section you can consult the created SKUs and edit them by clicking on the pencil icon in the options column.

![SKUs](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/SKUs.PNG)

To create a new SKU, click on the **New** button.

![SKUs New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/SKUs%20New.PNG)

The fields to complete are the following:

* **Code**: The SKU code.
* **Description**: The description of the SKU.
* **Short Description**: A short description of the SKU.
* **Ultra Short Description**: A very short description of the SKU.
* **POS Product Type**: Select what type of product it is.
* **Fuel Product**: Checkmark this option if the SKU is a fuel product.
* **SKU Category**: Enter the category to which the SKU belongs.
* **Measurement Unit**: Enter the unit in which the SKU is measured.
* **Sellable**: Checkmark this option if the SKU is sellable.
* **Weightable**: Checkmark this option if the SKU is weighable.
* **Fractional**: Checkmark this option if the SKU is fractional.
* **Stockable**: Checkmark this option if the SKU is storable.
* **Consignment**: Checkmark this option if the SKU is in consignment.
* **Availability From/To**: Select the dates among which the SKU is available.
* **Is POS**: Checkmark this option if the SKU is sold at the point of sale.
* **Dry Fleet**: Checkmark this option if the SKU is a dry product.
* **Reward**: Checkmark this option if the SKU can be redeemed for reward points.
* **Service**: Checkmark this option if the SKU is a service.
* **Loyalty**: Checkmark this option if the SKU accumulates points.

Pricebook:

* **Site**: Select the site to which you will charge the SKU price.
* **Date From**: Select the date on which the SKU goes into effect.
* **Price**: Indicate the price of the SKU.
* **Currency**: Select the currency in which the SKU is priced.

Items:

* **POS Code Format**: Select the point-of-sale code format.
* **POS Code**: Enter a point-of-sale code.

When you have finished filling those two fields, click the **Add** button.

* **Taxes**: Enter the SKU tax code.

### SKUs categories
In this section you can consult the categories of SKUs (Stock Keeping Units) already created and, if you want, edit them by clicking on the pencil icon in the options column.

![SKUs Categories](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/SKUs%20Category.PNG)

To create a new SKU, click on the **New** button.

![SKUs Categories New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/SKUs%20Category%20New.PNG)

The fields to complete are the following:

* **Code**: The SKU category code.
* **Name**: The name of the SKU category.
* **Short Description**: A short description of the SKU category.
* **First/Second Parent Category**: For example, if the SKU category was "Camel Cigarettes", the first parent category would be "Tobacco" and the second would be "Cigarettes".
* **Is POS**: Checkmark this option if the SKU category can be purchased at the point of sale.
* **Dry Fleet**: Checkmark this option if the SKU category is dry fleet.
* **Reward**: Checkmark this option if it can be redeemed for loyalty points.
* **Service**: Checkmark this option if it is a service.
* **Loyalty**: Checkmark this option if the purchase of the product accumulates loyalty points. 

### Taxes
The tax table displays:
* **Code:** Tax Code.
* **Description:** Tax description.
* **Type:** Type of tax (It can be a fixed tax, a percentage tax or a fixed tax per unit).
* **Amount:** The amount of tax (In the case of percentage tax, the percentage).
* **Date From / Date To:** Range of dates.
* **Options:** Edit the tax.

![Taxes](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Taxes.PNG)

To create a new tax, click on the **New** button in the upper left corner.

![Taxes New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Taxes%20New.PNG) 

The form to create a new tax receives the following parameters:

* **Code:** The code of the new tax.
* **Description:** The description of the new tax.
* **Type:** Type of tax (Can be a fixed tax, a percentual tax or a fixed tax per unit).
* **Date from:** The date on which the tax takes effect.
* **Amount:** The amount of the tax (In the case of percentual tax, the percentage).

After filling in the fields **Date from** and **Amount** click the **Add** button. 

When you have finished making the changes, click the **Save** button.

### Terminals / Controllers
Inside this section you can view, create and edit all terminals/controllers. The terminal is the point of sale of the site and the controller manages the pumps.

![Terminals](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Terminals.PNG)

To create a Terminal/Controller, click the **New** button.

![Terminals New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Terminals%20New.PNG)

* **Merchant:** Select the merchant associated to the terminal/controller.
* **Site:** Select the site associated to the terminal/controller
* **Active:** Checkmark to enable/disable the terminal/controller.
* **Terminal/Controller Type:** Select the terminal/controller type (ATIO-ControlGas, ATIO-NanoCPI, ATIO StandAlone, VF-Commander, etc.).
* **Model:** Select the terminal/controller model.
* **Code:** Input the terminal/controller code (ATIONet generates one automatically, but you can edit it. Except for the 3 first characters, since they represent the Subscription Code for the Network).
* **Description:** Input the terminal/controller description.
* **TAG Reader Present:** Checkmark this option if the terminal is capable of reading TAGs.
* **Driver Id Usage:** Select the action ATIONet will take associated to the Driver Id from transactions (None, Secondary Track or Code Validation).
* **Vehicle Id Usage:** Select the action ATIONet will take associated to the Vehicle Id from transactions (None, Secondary Track or Code Validation).
* **Maximum Volume Cut Off:** Input the maximum volume the terminal/controller will authorize.
* **Maximum Amount Cut Off:** Input the maximum amount the terminal/controller will authorize.
* **Operative System:** Input the terminal/controller operative system.
* **Serial Number:** Input the terminal/controller serial number.

When finished completing all fields, click the **Save** button.

### Users
In this view you can consult the users of the Network. You can edit them by clicking on the pencil icon in the options column, enable/disable a user by clicking on the padlock icon and reset the password with the star icon.

![Users](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Users.PNG)

To create a new User, click on the **New** button.

![Users New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Users%20New.PNG)

The fields to complete are the following:

* **User Mail**: The user's email address.
* **Name**: The user's name.
* **Social Security**: The user's document.
* **Street 1**: The street where the user resides.
* **Street 2**: Another street of reference, as it can be the one of the corner.
* **Country**: The user's country.
* **State**: The state of the user's country.
* **Zip Code**: The postal code of the locality where the user resides.
* **Phone Number 1**: The user's phone.
* **Phone Number 2**: The user's other phone if available.

<br>

* **Role**: The role that the new user will assume.
* **Entity**: The entity assigned to the user.

### Vehicle
This view lists all vehicles that have been created for the Network. Remember that it is not mandatory to load vehicles in order to operate, it is only necessary if you decide to associate the identifications to vehicles.

![Vehicles](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Vehicles.PNG)

Under the **Options** column you can

* **Assign Identification:** Assign/Unassign identifications to the vehicle.  
* **Renew Identification:** Renew the identification associated to the vehicle.
* **Favorites:** Add the vehicle to the **favorites** module.

### Vouchers
This view lists all vouchers created by companies.

![Vouchers](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Vouchers.PNG)

### Warehouses
In this section you can create/edit warehouses. Warehouses is where installed identifications are stored.

![Warehouses](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Warehouses.PNG)

To create a Warehouse, click the **New** button.

![Warehouses New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Warehouses%20New.PNG)

### Zones
In this section you can create/edit zones. Zones is an area where several sites are associated to it. Generally a Territory Manager is associated to specicif zone(s).

![Zones](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Zones.PNG)

To create a Zone, click the **New** button.

![Zones New](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/User%20Manual%20ATIONet/Administration/Zones%20New.PNG)
