
![ationetlogo](Content/Images/ATIOnetLogo_250x70.png)

|**Document Information**|.|
|--- |--- |
|**File:**|Operations procedure for ATIONET T650p Stand Alone terminal-EN.md|
|**Doc Version:**|1.0|
|**Release Date:**|02, July 2026|
|**Author:**|ATIONET LLC|


|**Change Log**|||
|--- |--- |--- |
|**Ver.**|**Date**|**Change Summary**|
|1.0|02/Jul/2026|- Initial version

- [Introduction](#Introduction)
- [Operations](#Operations)
- [Fleet Menu](#Fleet-Menu)
  - [Authorization](#Authorization)
  - [Completion](#Completion)
  - [Postpaid](#Postpaid)
  - [Receipt](#Receipt)
  - [Check Balance](#Check-Balance)
  - [Delete Pending Transactions](#Delete-Pending-Transactions)
  - [Cancel Transaction](#Cancel-Transaction)
- [Tasks Menu](#Tasks-Menu)
  - [Change PIN](#Change-PIN)
  - [Close Batch](#Close-Batch)
- [Loyalty Menu](#Loyalty-Menu)
  - [Enroll in Loyalty Program](#Enroll-in-Loyalty-Program)
  - [Check Loyalty Balance](#Check-Loyalty-Balance)
  - [Redeem Points](#Redeem-Points)
  - [Redeem Rewards](#Redeem-Rewards)
  - [Close Loyalty Batch](#Close-Loyalty-Batch)
  - [Reverse Points Accrual](#Reverse-Points-Accrual)

- [Maintenance](#Maintenance)
  - [Change the Supervisor's Password](#Change-the-Supervisor's-Password)
  - [Create or edit products](#Create-or-edit-products)
  - [Sync Now](#Sync-Now)
  - [Send Logs](#Send-Logs)
  - [Settings](#Settings)
      - [Language](#Language)
      - [Controller](#Controller)
      - [ATIONET](#ATIONET)
      - [Modules](#Modules)
      - [Terminal Management](#Terminal-Management)
      - [Tickets & Sites](#Tickets-&-Sites)
      - [Other](#Other)

     
## Introduction
This manual is intended to assist and guide users in using the ATIONET T650p standalone terminal. ATIONET standalone terminals allow users to authorize fleet transactions on ATIONET hosts.

## Operations
The following details all operations available on the T650p standalone terminals:

**> Fleet Menu**
- Authorization
- Finalization
- Postpaid
- Receipt
- Check Balance
- Delete Pending Transactions
- Cancel Transaction

**> Tasks Menu**
- Change PIN
- Close batch

**> Loyalty Menu**
- Enroll in Loyalty Program
- Check Loyalty Balance
- Redeem Points 
- Redeem Rewards
- Close Loyalty Batch
- Reverse Accumulation 

**> Maintenance**
- Change the supervisor's password
- Create or edit products
- Sync Now
- Send logs
- Settings


## Fleet Menu
IMAGE

## Authorization
During normal operation, the transaction is divided into two steps. First, a pre-authorization is performed at the POS terminal to obtain authorization to proceed with the transaction and to determine the maximum amount that can be processed. Once the transaction is processed, a confirmation takes place, during which the actual amount is reported.

Pre-authorization involves communicating with the central system and obtaining the balance authorized by it. Furthermore, reserving this balance means it cannot be used simultaneously elsewhere. This means that, ALWAYS after a pre-authorization, a finalization or cancellation of the pending pre-authorization must be performed to update the balance in the central system.

Start the transaction by selecting the AUTHORIZATION option from the touchscreen menu.
The system will now prompt you to enter the identification assigned to the vehicle/driver, either manually or using other scanning methods.
Select the corresponding product you wish to process.
Once all the data has been entered, the POS terminal will display the message “Processing...” while it communicates with the central system to request authorization.
If the transaction is not authorized, the system will display an error message, and after selecting “Accept,” the terminal will print a receipt.
If the transaction is authorized, the system will respond with a confirmation message, and the terminal will then print an authorization receipt. The receipt indicates the authorized amount for the shipment corresponding to that identifier in that transaction.


## Completion

Once the transfer is complete, you must confirm the transaction in the system. To do so, follow these steps:

Start the confirmation by selecting the FINALIZATION option from the touchscreen menu.
Remember that the amount sent cannot exceed the amount authorized during the preauthorization.
If you enter an amount greater than the preauthorized amount, you will receive an error message and the transaction will NOT be confirmed.

If the information entered is correct, the transaction will be confirmed on the server.
The screen will display the message “Transaction Complete,” and the POS terminal will print the transaction receipt.


## Post-Payment

In some circumstances, the sale may have already taken place and the shipment completed without following the normal pre-authorization and confirmation process. It is important to note that when processing a post-payment transaction, the system will apply the same restrictions that would have been applied during pre-authorization; therefore, if you attempt to enter a sale for an amount or volume that is not authorized for that merchant ID at that time, the sale will be rejected. If this occurs, you will need to contact customer support to determine how to proceed with the sale.

Start the sale by selecting the POSTPAYMENT option from the touchscreen menu.
The POS terminal will prompt you to present the ID associated with the sale so it can be recorded.
After scanning the ID, the terminal displays “Processing...” while it communicates with the central systems to report the sale.
If the transaction is not authorized, the system will display an error message, and after selecting “Accept,” the terminal will print the receipt.
If the entered data is correct, the transaction will be confirmed on the server. The screen will display the message “TRANSACTION COMPLETED,” and the POS terminal will print the transaction receipt.
If the transaction is authorized, the system will respond with a confirmation message like the one in the example and print an authorization receipt.


## Receipt
If for any reason you need to reprint the last receipt issued, you can do so from this menu.

Start the operation by selecting the RECEIPT option from the touchscreen menu.
The screen will display the last TWO transactions. When you select either of these two, the POS terminal will automatically print a copy of the indicated receipt.


## Balance Inquiry

This operation displays the maximum amount that can be dispensed in the next transaction for a specific ID. Perform this inquiry when the limits for the vehicle in question are unknown to avoid making multiple pre-authorization attempts that may be declined. If the balance shown does not match the amount the customer believes they have, contact customer support to determine how to proceed.

Start the sale by selecting the BALANCE INQUIRY option from the touchscreen menu.

The POS terminal will prompt you to present the ID associated with the vehicle/driver whose balance you wish to check.

After scanning the ID, the terminal displays “Processing...” while it communicates with the central systems to check the balance.

The system responds with the maximum amount available for the shipment. This is displayed on the screen, and the POS terminal also prints a receipt with this information.


## Clear Pending Transactions

If, for any reason, one or more preauthorizations have been made but the corresponding transfers have not been completed, you will need to release the balance from these preauthorizations to restore the account balance to normal.

To cancel the preauthorization, select the option "DELETE PENDING TRANSACTIONS" from the touchscreen menu.

The POS terminal will prompt you to present the ID associated with the preauthorization you wish to cancel.

After scanning the ID, the terminal displays the corresponding transaction; to proceed, press the **Delete!** button. The POS terminal will then communicate with the central systems to cancel the preauthorization.

Once the server has responded confirming the cancellation of the preauthorization, the screen will display a confirmation message. The preauthorization balance is now available for use again.


## Reverse Transaction
If an error occurs while processing a transaction in the system and the shift has not yet been closed, this option allows you to void the transaction and process it correctly.

Start the operation by selecting the CANCEL TRANSACTION option from the touchscreen menu.
The POS terminal will prompt you for the supervisor’s password, and once entered, it will ask for the authorization code for the transaction to be canceled. 
Before proceeding with the cancellation, you will be asked one last time to confirm; to proceed, press the **YES** button.
The POS terminal will then instruct the system to cancel the transaction. During this process, the screen will display “Processing…”.
Once the cancellation process is successfully completed, the POS terminal displays a message and prints a confirmation receipt or an error receipt if the process failed.


## Tasks Menu
IMAGE

## Change PIN

This option allows you to change the PIN for a specific user ID.
To do this, press the button in the CHANGE PIN menu.
Then enter the ID for which you want to change the PIN, enter the old PIN, then enter the NEW PIN, and press Accept.


## Batch Close
This feature allows you to group a set of transactions for later analysis and processing. It is generally recommended to close a batch at the end of each shift at the gas station. This makes it easy to reconcile transactions paid for using any of the payment methods processed by ATIONET.

Start the operation by selecting the BATCH CLOSE option from the touchscreen menu.
Supervisor permissions are required to proceed with the batch close. Enter the supervisor’s password.
Next, a brief verification step appears; after pressing the **YES** button, the corresponding close will proceed, and once the operation is complete, the POS terminal will display a message indicating “OPERATION COMPLETED” and print the closing receipt.


## Loyalty Menu

ATIONET Loyalty maintains a separate loyalty account for each program member. The account balance increases with points-earning transactions and decreases with points redemptions and according to the program’s expiration rules. Adjustment and transfer transactions can also increase or decrease the account balance, depending on the sign of the transaction.

At the point of service (store, kiosk, online store, etc.), the points accumulation process is typically linked to a purchase or payment transaction, in which customers earn points in exchange for their purchase.

A given loyalty program may have none, one, or several accumulation rules. Accumulation rules are processed in real time when an accumulation transaction request is received and tell ATIONET Loyalty how many points should be added to the member’s account. However, the transaction entry may also specify a specific number of points to be awarded to the account, overriding the program’s rules.

IMAGE

## Loyalty
Start the transaction by selecting the LOYALTY option from the touchscreen menu, then enter the corresponding loyalty ID either manually or via other scanning methods. Next, choose between earning points or applying a discount, then select the product type (Fuel or Groceries) and the corresponding amount or quantity.
Once all the data has been entered, the POS terminal will display the message “Processing...” while it communicates with the central system to process the points accumulation.
If the transaction is authorized, the system will display a confirmation message, and the terminal will then print a points receipt. The receipt shows the points earned or the discount applied for that ID, depending on the type of transaction you wished to perform.


## Loyalty Balance Inquiry
This transaction displays the maximum amount that can be dispensed in the next transaction for a loyalty-registered ID. Perform this inquiry when the limits for the vehicle in question are unknown to avoid making multiple pre-authorization attempts that may be declined. If the balance shown does not match the amount the customer believes they have, contact customer support to determine how to proceed.

Start the sale by selecting the BALANCE INQUIRY option from the touchscreen menu.

The POS terminal will prompt you to present the ID associated with the ID number whose balance you wish to check.

After scanning the ID, the terminal displays “Processing...” while it communicates with the central systems to check the balance.

The system responds with the maximum amount available for transfer. This amount is displayed on the screen, and the POS terminal also prints a receipt with this information.


## Redeeming Points 
In this section, you can redeem available points for various rewards.
When you press the **POINT REDEMPTION** button, the system will prompt you for the corresponding loyalty ID. Next, select the product you wish to redeem and then select the quantity. Finally, press the **Confirm** button, and after processing your request, the POS terminal will print a receipt with the redemption details.


## Redeeming Rewards
In this section, you can redeem rewards using the camera features.
First, tap the **Redeem Rewards** button, which will activate the device’s camera.
Then, scan the QR code for the corresponding prize, and finally, if you have the required points, the redemption will be processed.
Afterward, a receipt will be printed showing the details of the redemption.


## Loyalty Batch Close
This feature allows you to group a set of transactions for later analysis and processing. It is generally recommended to perform a batch close at the end of each operating shift at the gas station. This makes it easy to reconcile transactions paid for using any of the payment methods processed by ATIONET.

Start the operation by selecting the BATCH CLOSE option from the touchscreen menu.
Supervisor permissions are required to proceed with the batch close. Enter the supervisor password.
The POS terminal will ask one final time if you want to perform the close. It will then request that the central system close and process the batch. During this process, the screen displays “Processing…”.
When the process is complete, the POS terminal displays a message indicating “OPERATION COMPLETED” and prints the closing receipt.
The closing receipt includes a unique identification number generated by the server, the number of transactions processed since the last closing, the total sales, cancellations, and the cumulative amount for the period.


## Accumulation Reversal 
If an error occurs while processing an accumulation in the system, this option allows you to reverse it and process it correctly.

Start the operation by selecting the REVERSE TRANSACTION option from the touchscreen menu.
The POS terminal will prompt you for the supervisor’s password, and once entered, it will ask for the authorization code for the transaction to be canceled. 
Before proceeding with the cancellation, you will be asked one last time to confirm; to proceed, press the **YES** button.
The POS terminal will then instruct the system to reverse the transaction. During this process, the screen will display “Processing…”.
Once the cancellation process is successfully completed, the POS terminal displays a message and prints a confirmation receipt or an error receipt if the process failed.


## Maintenance

IMAGE

## Change the Supervisor’s Password
If for any reason you need to change the supervisor password, you can do so from this menu.

Start the process by selecting the SUPERVISOR PASSWORD option from the touchscreen menu.
Enter the new supervisor password, then re-enter it to confirm.
Once the password change process is complete, the POS terminal will display a confirmation message or an error message if the process failed.


## Create or Edit Products
This operation allows you to configure all fuels available for dispensing. From here, you can set the fuel’s name, price, and code. It is very important to use the same code as in the central system, since ATIONET uses this code to identify the product being dispensed.

Start the process by selecting the FUELS & SKUs option from the touchscreen menu.

You will now see two lists: one where you can add the desired fuels and another where you can add the desired SKUs. To add a new one, simply select the + sign.

The system will now prompt you to enter the fuel’s name, code, and price. Once everything is complete, select the Create option.

If for any reason you need to modify an existing fuel, simply select the fuel from the list, and the system will display all its details; then, just edit the fields.


## Sync Now
This section is used to establish a connection with the Terminal Management service. This service allows you to remotely manage, configure, and update terminals, as well as monitor multiple terminals.
Contact support@atioinc.com for more details about the Terminal Management service


## Send logs
To send logs, you must first establish a connection with the “Terminal Management” service, as this button is used to send terminal logs.


## Configuration
The settings menu allows you to modify the POS parameters. These operations are not routine and always require the supervisor’s password to access.

> [!NOTE]
It is important to note that the images only show the initial view of each section; you must scroll down the screen to see the rest of the settings for each section


## ***Language***

In this section, you can set the desired language for the terminal. To do so, press the button labeled with the language and select your preferred language.
(Currently, the terminal supports English and Spanish).

IMAGE
  
## ***Controller***

In this section, you can select the type of controller to be used to operate the station. To do so, scroll left and right to navigate through the available system types.
(Currently, the terminal supports the Stand Alone and Fusion Business Service systems.)

IMAGE

If you select the FUSION service, you will need to enter the IP address, port, and payment type code corresponding to the terminal.
IMAGE

## ***ATIONET***

In this section, you will configure the information related to the ATIONET system.

You must enter the following information: 

* Native URL: Enter the URL for the corresponding environment
    - BETA URL: https://native-beta.ationet.com/
    - Production URL: https://native.ationet.com/
  
* Terminal ID: Enter the same terminal code configured in your ATIONET portal subscription.

* Set "Amount" as default instead of "Volume": Enable this option so that, by default, the "Amount" field is displayed first instead of "Volume."

* Fixed Prompts for Transactions: When this option is enabled, a menu with multiple options will appear; when selected, these prompts will appear whenever transactions are performed.

The information that can be requested is as follows:

- Attendee ID
- Driver’s ID
- Vehicle identification
- Odometer reading
- Engine hours
- Trailer
- Miscellaneous
- Truck unit
- Secondary identification
- Primary PIN
- Secondary PIN

IMAGE

## ***Modules***

In this section, you can select the modules you want to use. Enabling or disabling modules will change the main menu view.
To select a module, scroll left and right to navigate among the different modules and press the “Enable Operations” button to enable the module.

IMAGE

Additionally, in the Loyalty module, you must add a user with the "Loyalty API" role on the ATIONET portal. You can also select the type of loyalty system you wish to use. (You can use Discounts, Points, or both.)

IMAGE

## Terminal Management

In this section, you can configure the Terminal Management service.
Contact support@atioinc.com for more details about the Terminal Management service.

IMAGE

## ***Tickets & Sites***

In this section, you can configure the main information for the site, with the **Code** and **Name** being the most important fields.
These are the site configuration options:

- Site Code
- Site Name
- Site Address
- Site Tax ID

You can then configure what information will appear when the ticket is printed. 
The following information can be displayed:

- Driver ID
- Vehicle ID
- Company name
- Primary identification
- Secondary identification
- Company price

Additionally, certain information on the receipt can be customized, such as the title, subtitle, footer, and footnote.

* Print transaction details in columns: When this option is enabled, transaction details will be displayed in columns rather than in list order.

The last available option to configure allows you to display the invoice number instead of the authorization code.
Finally, at the bottom of this section, you’ll find a preview of the final receipt based on the settings you’ve configured, which you can print to have a physical copy. 

IMAGE

## ***Other***

In this section, you can configure information such as the unit of measure for fuel/CNG and the currency used for the transaction.
In addition, there is a "Print Settings" button; pressing it will cause the terminal to print certain additional settings, such as the version installed on the terminal or the system ID.

IMAGE
