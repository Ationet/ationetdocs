## Introduction

**Receipt Data** is a field of type `Dictonary<string, string>` meaning that every element in the collection has a **Key** and **Value**. The contents of this field vary according to the different business rules that are configured within the host. Mainly used for information related to the transaction that the Terminal / Controller may want to print in a physical receipt. Is is only present in host responses.

## Keys

| Key                                   | Description                                      |
| ------------------------------------- | ------------------------------------------------ |
| CustomerName                          | Primary *SubAccount* description                 |
| CustomerSecondaryName                 | Secondary *SubAccount* description               |
| CustomerPlate                         | *Vehicle* plate                                  |
| CustomerIdentification                | Primary *SubAccount* Code                        |
| CustomerSecondaryIdentification       | Secondary *SubAccount* Code                      |
| CustomerPAN                           | Primary *Identification* PAN                     |
| CustomerSecondaryPAN                  | Secondary *Identification* PAN                   |
| CustomerLabel                         | Primary *Identification* Label                   |
| CustomerSecondaryLabel                | Secondary *Identification* Label                 |
| CustomerTaxPayerId                    | *Company* Tax Payer Id                           |
| CustomerTruckUnitNumber               | *Track Unit Number* echo from *CustomerData*     |
| CustomerTrailerNumber                 | *Trailer Number* echo from *CustomerData*        |
| CustomerDriverId                      | *Driver Id* echo from *CustomerData*             |
| CustomerDriverLicenseState            | *Driver License State* echo from *CustomerData*  |
| CustomerDriverLicenseNumber           | *Driver License Number* echo from *CustomerData* |
| CustomerTripNumber                    | *Trip Number* echo from *CustomerData*           |
| CustomerPurchaseOrderNumber           | *Purchase Order Number* echo from *CustomerData* |
| CustomerVehicleId                     | *Vehicle Id* echo from *CustomerData*            |
| CustomerVehicleCode                   |                                                  |
| CustomerVehiclePlate                  |                                                  |
| CustomerVehicleModel                  |                                                  |
| CustomerVehicleBrand                  |                                                  |
| CustomerMiscellaneous                 |                                                  |
| CustomerEngineHours                   |                                                  |
| CustomerOdometer                      |                                                  |
| CustomerTrailerHourMeterReading       |                                                  |
| CustomerFleet                         |                                                  |
| CustomerLastOdometer                  |                                                  |
| CustomerLastOdometerDate              |                                                  |
| CompanyCode                           |                                                  |
| CompanyName                           |                                                  |
| CompanyStreet1                        |                                                  |
| CompanyStreet2                        |                                                  |
| CompanyCity                           |                                                  |
| CompanyZipCode                        |                                                  |
| CompanyState                          |                                                  |
| CompanyCountry                        |                                                  |
| CompanyTaxPayerId                     |                                                  |
| CompanyTaxPayerCategory               |                                                  |
| ContractMode                          |                                                  |
| SubscriberName                        |                                                  |
| AvailableBalance                      |                                                  |
| CustomerClassification1Label          |                                                  |
| CustomerClassification1Value          |                                                  |
| CustomerClassification2Label          |                                                  |
| CustomerClassification2Value          |                                                  |
| CustomerClassification3Label          |                                                  |
| CustomerClassification3Value          |                                                  |
| CustomerClassification4Label          |                                                  |
| CustomerClassification4Value          |                                                  |
| CustomerSecondaryClassification1Label |                                                  |
| CustomerSecondaryClassification1Value |                                                  |
| CustomerSecondaryClassification2Label |                                                  |
| CustomerSecondaryClassification2Value |                                                  |
| CustomerSecondaryClassification3Label |                                                  |
| CustomerSecondaryClassification3Value |                                                  |
| CustomerSecondaryClassification4Label |                                                  |
| CustomerSecondaryClassification4Value |                                                  |
| TransactionId                         |                                                  |
| AuthorizationType                     |                                                  |
| CustomerCustom0Label                  |                                                  |
| CustomerCustom0Value                  |                                                  |
| CustomerCustom1Label                  |                                                  |
| CustomerCustom1Value                  |                                                  |
| CustomerCustom2Label                  |                                                  |
| CustomerCustom2Value                  |                                                  |
| CustomerCustom3Label                  |                                                  |
| CustomerCustom3Value                  |                                                  |
| CustomerCustomOperation0Label         |                                                  |
| CustomerCustomOperation0Value         |                                                  |
| CustomerCustomOperation1Label         |                                                  |
| CustomerCustomOperation1Value         |                                                  |
| CustomerCustomOperation2Label         |                                                  |
| CustomerCustomOperation2Value         |                                                  |
| CustomerCustomOperation3Label         |                                                  |
| CustomerCustomOperation3Value         |                                                  |
| CustomerCustomOperation4Label         |                                                  |
| CustomerCustomOperation4Value         |                                                  |
| ContractBalanceMode                   |                                                  |
| FuelName                              |                                                  |