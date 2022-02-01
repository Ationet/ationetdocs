![ationetlogo](Content/Images/ATIOnetLogo_250x70.png)

|**Document Information**|.|
|--- |--- |
|**File:**|ATIONET-Local Agent Product Description-EN.MD|
|**Doc Version:**|1.0|
|**Release Date:**|03, Feb 2022|
|**Author:**|ATIONET LLC|


|**Change Log**|||
|--- |--- |--- |
|**Ver.**|**Date**|**Change Summary**|
|1.0|03/Feb/2022|- Initial version

</br>

# Contents

- [General Information](#general-information)
- [Transaction Processing](#transaction-processing)
- [Reconnection to ATIONET](#reconnection-to-ationet)
- [Rules and Validations](#rules-and-validations) 
- [Features not covered](#features-not-covered) 



</br>


# **General Information**

Local Agent is a product that allows us to configure an environment on a computer within a station to continue operating, even if we have connectivity problems at the station and do not have a connection with ATIONET at that time.

The product has the authorization logic implemented in ATIONET, for fuel dispatch. In turn, the same in its latest version allows it to be used with the Native protocol and with the Payware protocol.

In the case of having connectivity, ATIONET will be in charge of processing the authorization and providing the necessary response for dispatch. In case of losing connectivity, the LocalAgent will comply with such purpose, transparently in the process, processing the transaction and saving the pertinent information locally, to be sent to ATIONET when the connection is recovered.


<br>

# **Transaction Processing**

Below is an explanatory graphic of the flow that Local Agent performs when determining how the transaction will be processed:

![Procesamiento de Transacciones](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Local%20Agent/Procesamiento%20Transacciones.png)

1. The frame arrives from the terminal/controller to the Local Agent.
2. The connection to ATIONET is validated
    a. If there is a connection: Local Agent sends the frame and it is processed by ATIONET, which is responsible for generating the response of the operation.
    b. In case there is no connection: Local Agent is responsible for determining if it is feasible to process the frame offline, if so, the Offline Processing Engine will be responsible for processing it, generating the response of the operation.
3. The generated response is sent to the controller that generated the request.


<br>

# **Reconnection to ATIONET**

When recovering connection with ATIONET, the Local Agent performs two processes:

1. Download the news that has been generated in order to continue operating offline with the most up-to-date information possible.
2. Upload to ATIONET the transactions that have been processed offline.

Below is an explanatory graphic of the flow that Local Agent performs when recovering the connection:

![Reconexión a ATIONet](https://github.com/Ationet/ationetdocs/blob/master/Content/Images/Local%20Agent/Reconexi%C3%B3n%20ATIONet.png)

1. The Local Agent executes a process that evaluates the connection status with ATIONET
  1. If you continue offline, you maintain your Offline status and continue to trade offline.
  2. If it detects that you have a connection again:
    1. Request the news that may have arisen during the period that is offline.
    2. Download the new features of ATIONET and apply these new features.
    3. Evaluates if there are any transactions processed offline during the period you were offline. If so, send the news to ATIONET.


<br>

# **Rules and Validations**

The product contemplates the application of certain rules in the same way as the ATIONET cloud host, but it does not contemplate 100% of them, the reason is that being a local authorizer, it is not possible to replicate the same amount of information that is available at host level in the Local Agent, as this would affect the amount of data managed locally with the corresponding server requirement impact, and the amount of traffic that would need to be considered between the local server and the ATIONET host.

It must be taken into account that all the rules mentioned in this document are rules that apply to subaccounts, the Local Agent downloads all the rule configuration at the subaccount level and not at the vehicle or driver level, in order to simplify the volume of information that must be synchronized. This implies that any rule configured for a fleet, vehicle or driver that does not have a subaccount associated with it cannot be applied.

The rules that are applied in the Local Agent are detailed below:

- ***DateTime:*** Validate that the transaction is made between the established dates. There could be more than one such rule and I would reject if only one prevents it, even though there is another one that does allow it. The current logic downloads the rule values as integers and converts the validation date to one for comparison.
- ***Location:*** Validates that the transaction is made by any of the allowed terminals. Since the concept of site does not exist in Local Agent, the rule obtains all the terminals that belong to the sites of the rule.
- ***Fuel:*** Validates that the transaction has been carried out with one of the configured fuels.
- ***TransactionsLimit:*** Limits transaction maximums in volume or amount.
- ***DaysTime:*** Validate that the transaction is made between the established times and days. It still has the old format, which limits the same hours regardless of the day.
- ***Quota:***
  - **Days/Weeks/Months/Fortnight:** The value of the rule loaded in ATIONET is used, equally distributed among the periodicity units. Example, 10 dolars spread over 5 days, results in a rule of 2 dolars per day.
  - **Days / Times:** The rule of days / hours is applied to enable fuel dispatch.
  - **Current and upcoming:** The value resulting from the calculation mentioned in the previous point is downloaded, and it is placed as current and next. The current value is subtracted from what was consumed during the designated period. If you remain offline long enough to meet the quota times, the next value will start to be used.
  - **Annuals:** Annual fees are actually considered monthly fees spread evenly over 12 months.
  - **Global:** Offline there is the concept of a global quota (without periodicity) that is always validated first before the other quotas. Currently in ATIONET there is no way to charge a quota without periodicity, for which this concept is deprecated.
- ***Prompting:***
  - VehiclePIN, DriverPIN, DriverId, VehicleId, Miscellaneous, Odometer, EngineHours, TruckUnitNumber, TrailerNumber.
  - Odometer variation is validated, but not Engine Hours.
***Validations:***
- **Active:** Identifications.
- **Enabled:** Vehicle &amp; Driver.
- **ExpirationDate:** Identifications &amp; CompanyContracts.
- **SiteValidation:**  It only allows dispatch from the sites indicated by the contract.
- **FuelValidation:** If the contract is for products, it only allows dispatch of those that are configured.
- **Driver/Vehicle Relationships:** It only allows dispatching to Drivers or Vehicles that have identified a related Vehicle or Driver, respectively. It is not allowed to relate two equal entities.
- **CodeValidation:** As indicated in the terminal, the DriverId or VehicleId will be used as code validation.
- **SecondaryTrack:** As indicated in the terminal, the DriverId or VehicleId will be used as Secondary Track.
- **VehicleClass:**  It only allows dispatching the fuels indicated in the vehicle class. Also use it as a hint if possible.
- **FastTrack:** Allows the use of FastTrack and keeps track of your balance.
- **PriceChange:** If the terminal allows it, the price change is made according to what the contract says. Prices per Site are valid. **NO DISCOUNTS APPLY.**
- **BalanceMode:** Respects the distribution of balances of contracts and programs.
- **ProductAndMoney:** Allows authorization by multiple species and its limitations as indicated by the authorization mode of the terminal.
- **OfflineLimits:** Allows limiting values in percentage form. They always apply to the last thing before answering the authorization.


<br>


# **Funcionalidades no contempladas**

- **Subsidies**: does not support subsidies.
- **Keep pin lock**: when the pin entry attempts expire, the id is locked, but when returning to online mode it does not remain locked.
- **Fuel types**: does not include fuel types in offline mode.
- **Balance inquiry**: this functionality is out of scope.
- **Reverse transactions**: the reverse of transactions cannot be performed, it sends an unsupported transaction message.
- **Messages in Spanish**: the short message that is originally configured in Spanish, in its offline version, is generated in English. For example: Invalid Primary PIN, Transaction not supported, etc.


<br>

[Back to top](#contents)  :arrow_up:
