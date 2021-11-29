## Introduction

Customer Data is a field of type `Dictonary<string, string>` meaning that every element in the collection has a **Key** and **Value**. The contents of this field vary according to the different business rules that are configured within the host. Mainly used for, but not limited to, *Prompt Rules* (see annex #)

Being a dictonary data type means that you may send any key/value combination and the host will take it as valid. However, only certain keys are taken into account in a request message, as well as some unique keys used for the response.

## Response Keys

The response keys are mainly used to provide information to the client making the request, whether it is a prompting request or certain information used in specific scenarios.

|Key|Description|
|----------|-----------|
|PromptOdometer|Indicates an *Odometer* prompt is requested by the host|
|MinOdometer|Indicates the minimum *Odometer* variation configured in the host|
|MaxOdometer|Indicates the maximum *Odometer* variation configured in the host|
|LastOdometer|Indicates the last *Odometer* reported for the vehicle|
|PromptEngineHours|Indicates an *Engine Hours* prompt is requested by the host|
|MinEngineHours|Indicates the minimum *Engine Hours* variation configured in the host|
|MaxEngineHours|Indicates the maximum *Engine Hours* variation configured in the host|
|LastEngineHours|Indicates the last *Engine Hours* reported for the vehicle|
|PromptDriverId|Indicates a *Driver Id* prompt is requested by the host|
|PromptVehicleId|Indicates a *Vehicle Id* prompt is requested by the host|
|PromptMiscellaneous|Indicates a *Miscellaneous* prompt is requested by the host|
|PromptTrailerNumber|Indicates a *Trailer Number* prompt is requested by the host|
|PromptTruckUnitNumber|Indicates a *Truck Unit Number* prompt is requested by the host|
|PromptPrimaryPin|Indicates a *Primary Pin* prompt is requested by the host|
|PromptSecondaryTrack|Indicates a *Secondary Track* prompt is requested by the host|
|PromptSecondaryPin|Indicates a *Secondary Pin* prompt is requested by the host|
|DualUseCard|Indicates whether the identification used is Dual or not|
|Tags|Returns a list of all active TAG type identifications the current vehicle has|
|ContractMode|Indicates the *Contract Mode* of the identification used for the transaction|

## Request Keys

The request keys are used to provide requested information to the Host. Usually sent in a follow-up request after the host's response, but can be sent in the first request as well.

|Key|Description|
|----------|-----------|
|Odometer|Vehicle's current Odometer|
|EngineHours|Vehicle's current Engine Hours|
|DriverId|Driver Id field provided by the client|
|VehicleId|Vehicle Id field provided by the client|
|Miscellaneous|Miscellaneous provided by the client|
|TrailerNumber|Vehicle's Trailer Number|
|TruckUnitNumber|Vehicle's Truck Unit Number|

<!--
|PromptPrimaryPin|Indicates a *Primary Pin* prompt is requested by the host|
|PromptSecondaryTrack|Indicates a *Secondary Track* prompt is requested by the host|
|PromptSecondaryPin|Indicates a *Secondary Pin* prompt is requested by the host|
|DualUseCard|Indicates whether the identification used is Dual or not|
|Tags|Returns a list of all active TAG type identifications the current vehicle has|
|ContractMode|Indicates the *Contract Mode* of the identification used for the transaction|


        public const string DriverLicenseState = "DriverLicenseState";
        public const string DriverLicenseNumber = "DriverLicenseNumber";
        public const string TripNumber = "TripNumber";
        public const string PurchaseOrderNumber = "PurchaseOrderNumber";
        public const string TrailerHourMeterReading = "TrailerHourMeterReading";

        public const string FastTrack = "FastTrack";
        public const string IdLoyaltyProgram = "IdLoyaltyProgram";

        public const string CustomField0 = "CustomField0";
        public const string CustomField1 = "CustomField1";
        public const string CustomField2 = "CustomField2";
        public const string CustomField3 = "CustomField3";
        public const string CustomField4 = "CustomField4";
        public const string CustomField5 = "CustomField5";
        public const string CustomField6 = "CustomField6";
        public const string CustomField7 = "CustomField7";
        public const string CustomField8 = "CustomField8";
        public const string CustomField9 = "CustomField9";
-->