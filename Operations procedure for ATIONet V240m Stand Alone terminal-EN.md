![ationetlogo](Content/Images/ATIOnetLogo_250x70.png)

|**Document Information**|.|
|--- |--- |
|**File:**|Operations procedure for ATIONet V240m Stand Alone terminal-EN.md|
|**Doc Version:**|1.0|
|**Release Date:**|09, April 2021|
|**Author:**|ATIONet LLC|


|**Change Log**|||
|--- |--- |--- |
|**Ver.**|**Date**|**Change Summary**|
|1.0|09/Apr/2021|- Initial version

# Contents

- [Introduction](#introduction)
- [Operations](#operations)
- [Main Menu](#main-menu)
  - [Pre-Authorization](#pre-authorization)
  - [Confirmation](#confirmation)
  - [Clear Pending Pre-Authorization](#clear-pending-pre-authorization)
  - [Sale](#sale)
  - [Balance Enquiry](#balance-enquiry)
  - [Loyalty](#loyalty)
    - [Accumulation](#accumulation)
    - [Accumulation Refund](#accumulation-refund)
    - [Balance Enquiry](#balance-enquiry-1)
- [Maintenance](#maintenance)
  - [Batch Close](#batch-close)
  - [Print Last Receipt](#print-last-receipt)
  - [Reverse Transaction](#reverse-transaction)
  - [Active GiftCard](#activate-giftcard)
  - [Recharge CC](#recharge-cc)
- [Configuration](#configuration)
  - [Supervisor Password](#supervisor-password)
  - [Fuels](#fuels)

## Introduction

This manual is aimed to help and guide the user with the ATIONet V240m Stand Alone terminal. ATIONet Stand Alone terminals allows the user to authorize fleet transactions in ATIONet hosts.

## Operations

Inside this section we will cover all available operations within the V240m Stand Alone terminals:

- Main Menu
  - Pre-Authorization
  - Confirmation
  - Clear Pending Pre-Authorization
  - Sale
  - Balance Enquiry
  - Loyalty
    - Accumulation
    - Accumulation Refund
    - Balance Enquiry
- Maintenance
  - Batch Close
  - Print Last Receipt
  - Reverse Transaction
  - Active GiftCard
  - Recharge CC
- Configuration
  - Supervisor Password
  - Fuels

## Main Menu

### Pre-Authorization

During normal operation the transaction is divided into two operations. First a pre-authorization is done from the POS to obtain the authorization to continue with the transaction and the amount of the maximum dispatch. After the dispatch has been done, the confirmation takes place, in which the real amount is reported.

The pre-authorization involves communication with the central system and retrieval of the balance that it authorizes. Also, capturing this balance implies that it cannot be used simultaneously from elsewhere. This means that ALWAYS after a pre-authorization there should be a completion or a pre-authorization pending delete performed to update the balance in the central system.

- Start the operation by selecting from the touch-pad menu the option **PRE-AUTHORIZATION**.
- The system will now prompt to present the identification that was assigned to the vehicle/driver. For Manual Entry or other reading methods (for example scanner) select the **Others** option.
- Select the corresponding product that you intend to dispatch.
- Once all the data has been responded, the POS will display the message **Processing...** while communicating with the central system to request authorization.
-	If the transaction is unauthorized the system will respond with an error message and after selecting Ok the terminal prints the ticket.
-	If the transaction is authorized the system will respond with a confirmation message and then the terminal prints an authorization ticket. The ticket indicates the authorized amount to dispatch for that identifier in that transaction.

Proceed with the dispatch following what was indicated on the ticket.


### Confirmation

Upon completion of the dispatch it is necessary to confirm the transaction in the system. To do so, follow these steps:

- Start the confirmation by selecting from the touch-pad menu the option **CONFIRMATION**.
- Remember that the dispatched amount cannot exceed the authorized amount in the pre-authorization.

If you enter an amount greater than the pre-authorized you&#39;ll receive an error message and the transaction will NOT be confirmed.

Press the green button to re-enter the correct amount.
- If the data entered is correct, the operation will be confirmed on the server.

The display will show the message **Operation Completed** and the POS will print the ticket of the transaction.

This first copy of the ticket is for the station and is normally requested to be signed by the Customer. The terminal will then prompt to print a second copy for the client. To do so just press the green button to print or the red button to not do so.

### Clear Pending Pre-Authorization

If for some reason there has been made ​​one or more pre-authorizations and the corresponding dispatches have not been performed, it will be necessary to release the balance of these pre-authorizations to normalize the balance of the account.

- Start the pre-auth cancellation by selecting from the touch-pad menu the option **CLEAR PENDING PRE-AUTHORIZATION**.

- The POS will ask to present the identification that is associated to the pre-authorization to be cancelled.
- The identification that was assigned to the vehicle/driver should now be presented through the terminal.
- After reading the identification, the terminal displays **Processing...** while communicating with the central systems to cancel the pre-authorization.
- When the server has responded confirming the cancellation of the pre-authorization the screen displays a confirmation message. The balance of the pre-authorization is now available for use again.

### Sale

Under some circumstances it may be the case that the sale has already been made ​​and the dispatch was completed without following the normal flow of pre-authorization and confirmation. It is important to note that when processing a sale, the system will apply the same restrictions that had been applied in a pre-authorization, therefore, if you try to enter a sale for an amount or volume that is not authorized for that identifier at the time, the sale will be rejected. If this happens it will be necessary to contact the help desk to determine how to proceed with the sale.

- Start the sale by selecting from the touch-pad menu the option **SALE**.
- The POS will ask to present the identification associated with the sale to be informed.
- After reading the identification, the terminal displays **Processing...** while communicating with the central systems to report the sale.
- If the transaction is unauthorized the system will respond with an error message and after selecting **Ok** the terminal prints the ticket. In the example: **ID does not exist**.
- If the data entered is correct the operation will be confirmed on the server.
The display will show the message **OPERATION COMPLETED** and the POS will print the ticket of the transaction.
- If the transaction is authorized the system will respond with a confirmation message like the example and will print an authorization ticket.

### Balance Enquiry

This operation indicates the maximum that can be dispatched in the next transaction to a specific identification. Perform this query when the limits of the vehicle involved are unknown to avoid making multiple attempts of pre-authorization that can be denied. If the reported balance does not correspond with the amount the Customer believes he has, it is necessary to contact the help desk to determine how to proceed.

- Start the sale by selecting from the touch-pad menu the option **BALANCE ENQUIRY**.

- The POS will ask to present the identification associated to the vehicle/driver you desire to check the balance.
- After reading the identification, the terminal displays **Processing...** while communicating with the central systems to check the balance.
- The system responds with the maximum amount available for dispatch. It is shown on screen and the POS also prints a ticket with such information.

### Loyalty

ATIOnet Loyalty keeps a separate Loyalty Account for each Loyalty Member. The account balance is incremented by Accumulation Transactions and decremented by Accumulation Refunds and Program&#39;s Expiration Rules. Adjustment and Transfer transactions may also add to or reduce the balance of the account, depending on the sign of the operation.

There are three type of Loyalty operations inside the POS:

- Accumulation
- Accumulation Refund
- Balance Enquiry

At the Service Point (Store, Kiosk, Web market, etc.), the Accumulation process is usually related to a purchase or payment operation, where the customers earn Points in exchange to their business.

A given Loyalty Program may have none, one or several Accumulation Rules. Accumulation Rules are processed on real-time when an Accumulation Transaction Request is received and tell ATIOnet Loyalty how many Points must be add to the Member&#39;s account. But also the Capture may specify a certain amount of Points to be awarded to the account, overriding Program&#39;s rules.

#### Accumulation

- Start the operation by selecting from the touch-pad menu the option **LOYALTY** and then **ACCUMULATION**.
- The system will now ask to present the Loyalty identification. For Manual Entry or other reading methods (for example scanner) select the **Others** option.
- Select the corresponding product that you intend to accumulate points.
- The system will then prompt to enter the transaction&#39;s quantity.
- Once all the data has been responded, the POS will display the message **Processing...** while communicating with the central system to process the accumulation.
- If the transaction is authorized the system will respond with a confirmation message and then the terminal prints an accumulation ticket. The ticket indicates the accumulated amount for that identifier in that transaction.

#### Accumulation Refund

If for some reason an accumulation already performed needs to be refunded it will be necessary to:

- Start the operation by selecting from the touch-pad menu the option **LOYALTY** and then **ACCUMULATION REFUND**.
- The POS will now ask to present the identification associated to the accumulated transaction to be refunded.
- The system will then prompt to enter the **Authorization Code** associated to the accumulated transaction to be refunded.
- Once all the data has been responded, the POS will display the message **Processing...** while communicating with the central system to process the accumulation refund.
- If the transaction is authorized the system will respond with a confirmation message and then the terminal prints the refund ticket.


#### Balance Enquiry

This operation indicates the total accumulated to a specific identification.

- Start the operation by selecting from the touch-pad menu the option **LOYALTY** and then **BALANCE ENQUIRY**.
- The POS will ask to present the identification associated to the vehicle/driver you desire to check the balance.
- After reading the identification, the terminal displays **Processing...** while communicating with the central systems to check the balance.
- The system responds with the accumulated points available. It is shown on screen and the POS also prints a ticket with such information.

## Maintenance

The Maintenance menu provides access to system operations that are not directly related to the operation of the same transaction. That is, operations that are not made with the same frequency as those for processing transactions in the system.

### Batch Close

This concept allows grouping a set of transactions for further analysis and processing convalescence. Usually, it is recommended to perform a batch close for each closing operating shift at the gas station. This way you can easily reconcile transactions that were paid with any of the means of payment processed by ATIONET.

- Start the operation by selecting from the touch-pad menu the option **BATCH CLOSE**.

- In order to proceed with the batch close, you require supervisor permits. Please enter the supervisor password.
- The POS will ask the Central System to close a batch and process it. During that process, **Processing…** is displayed on screen.
- When the process finishes the POS displays a message indicating **OPERATION COMPLETED** and prints the closure ticket.
- The closure ticket includes a unique identification number generated by the server, the number of processed transactions from the last close, the total sales, cancellations and acumulated amount during the period.

### Print Last Receipt

If for some reason it is necessary to reprint the last ticket issued (typically when the printer paper is locked), this can be done from this menu.

- Start the operation by selecting from the touch-pad menu the option **PRINT LAST RECEIPT**.

- The POS will automatically print a copy of the last receipt issued. You cannot re-print any other ticket.

### Reverse Transaction

If there is an error while processing a transaction in the system and the turn still has not been closed, this option can be used to override it and process it properly.

- Start the operation by selecting from the touch-pad menu the option **REVERSE TRANSACTION**.
- The POS will request the authorization code of the transaction to be canceled. You can find the authorization code in the ticket. Press the green button to process the void transaction.
- The POS will ask the system to annul the transaction. During that process, **Processing…** will be displayed on screen.
- Upon completion of the annulment process correctly, the POS displays a message indicating so and prints a confirmation ticket or an error one if the process had failed.

### Activate GiftCard

### Recharge CC

## Configuration

Configuration menu provides access to modify POS parameters. These operations are not common and require in all cases Supervisor password.

### Supervisor Password

If for some reason it is necessary to modify the supervisor password, it can be done from this menu.

- Start the operation by selecting from the touch-pad menu the option **SUPERVISOR PASSWORD**.
- Enter the current password to perform this operation and then press the green button to confirm.
- Insert the new password and press the green button to continue.
- Upon completion of the password changing process the POS will display a confirmation message or an error if the process had failed.

### Fuels

This operation will allow you to configure all fuels available for dispatch. From here you&#39;ll be able to configure the Fuel&#39;s name, price and code. It is very important to configure the same code as in the central system, since it is with this code that ATIONet recognizes the product being dispatched.

- Start the operation by selecting from the touch-pad menu the option **FUELS**.

- The system will now prompt to enter the supervisor password. Enter the corresponding password and press the green button to confirm.
- You will now have a list of all Fuels added in the POS. To add one just select the **+** sign.
- The system will now prompt to complete the Fuel&#39;s name, code and price. Once all is completed select the **Create** option.
- If for some reason it is necessary to modify an existing fuel, just select the fuel from the list and the system will prompt all the fuel details and just edit the fields.
