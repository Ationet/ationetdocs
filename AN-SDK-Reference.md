![ationetlogo](Content/Images/ATIOnetLogo_250x70.png) 
# ATIOnet .NET SDK Reference
> **About:** This document describes and explains how to consume the .NET SDK for all ATIOnet APIs.	


<BR/>

|Document Information||
|--- |--- |
|File:|AN-SDK-Reference|
|Doc. Version:|1.0|
|Release Date:|10, July 2016|
|Author:|ATIOnet LLC|

|Change Log|||
|--- |--- |--- |
|Ver.|Date|Change summary|
|1.0|10/July/2016|Initial version|

</br>

<!--###Table of Content -->

## Contents

<!-- MarkdownTOC depth=3 -->

- [Introduction](#introduction)
- [Download / Installation](#download/installation)
- [Operation Types](#operation-types)
  -  [Auth](#auth)
  -  [Api](#api)
  -  [FMS](#fms)
  -  [Interface](#interface)
  -  [Loyalty](#loyalty)
  -  [Retail](#retail)
- [Consuming the SDK](#consuming-the-sdk)
  -  [Operation Types methods](#operation-types-methods)
	  -  [Auth Methods](#auth-methods)
	  -  [Api Methods](#api-methods)
	  -  [FMS Methods](#fms-methods)
	  -  [Interface Methods](#interface-methods)
	  -  [Loyalty Methods](#loyalty-methods)
	  -  [Retail Methods](#retail-methods)
- [Appendix A - Native Authorization Protocol Messages](#appendix-a---native-authorization-protocol-messages)
<!-- /MarkdownTOC -->

## Introduction
The ATIOnet SDK (Software development Kit) helps any developer that wants to interact with ATIOnet Platform. If you are integrating an existing software or want to extract data out of ATIOnet, the SDK will make this much easier, taking care of all the HTTP communication, error handling and retry policies.
ATIOnet SDK can be consumed from any .NET language.

## Download / Installation
ATIOnet SDK is hosted in [www.nuget.org](http://www.nuget.org). NuGet is the package manager for the Microsoft development platform including .NET. The NuGet client tools provide the ability to produce and consume packages. The NuGet Gallery is the central package repository used by all package authors and consumers.

## Operation Types
ATIOnet SDK is able to handle most of the ATIOnet modules (Operation Types). These operations are very specific to the responsibility they have in the platform, like for example *Authorization*, *FMS (Fuel Management Systems)*, *Loyalty*, etc. Each of this Operation Type, has a corresponding  module in the SDK. the complete list of *Operations Types* are listed below.


### Auth
The Auth Operation Type is the one in charge of interacting with the authorization engine. The authorization engine is the component that receives authorizations requests and decides if the transaction is approved or not. This SDK Operation Type should be use if you are building a POS or a terminal that will be sending authorization requests to ATIOnet. 

### Api
The Api Operation Type was design to be used by 3rd party software that need to get information from ATIOnet. With this Operation Type you can perform the functions performed by the ATIOnet Console.

### FMS
The FMS Operation Type is the one in charge of interacting with the FMS module. ATIOnet supports receiving *Inventory* and *Deliveries* transactions through this interface.

### Interface
The Interface Operation Type was design to be used by 3rd party software that need to get information from ATIOnet. With this Operation Type you can download transactions (fleet, loyalty, retail, rejected, approved and exceptions), current account movements, current account balances and loyalty current account.

### Loyalty
The Loyalty Operation Type is the one in charge of interacting with the Loyalty module. Using this Operation Type you will be able to send Loyalty transactions to ATIOnet among other features.

### Retail
The Retail Operation Type is the one in charge of interacting with the Retail module. Using this Operation Type you will be able to send Retail information (transactions, batch closes, etc) to ATIOnet among other features.


## Consuming the SDK
For this example we will use Visual Studio 2013 and we will create a Console Application.

1.  Inside Visual Studio create a new Console Application
![ationetlogo](Content/Includes/AN-SDK-Reference/01.png)
1.  Once the project is created, open the *Solution Explorer*, right click the project and select *Manage NuGet Packages*. This will open a pop up.
![ationetlogo](Content/Includes/AN-SDK-Reference/02.png)

3.  Inside the NuGet pop up, in the left part select *Online*, then in the right top corner type *ationet*. This will bring the list of packages found with this criteria. In this case only 1, **ATIOnet SDK**. Click *Install*, this will install the ATIOnet SDK packages and dependencies. Please accept terms and conditions for dependencies packages. 
![ationetlogo](Content/Includes/AN-SDK-Reference/03.png)

1.  In the sample below you will see how to download transactions. Open the Program.cs and type the following code:

```javascript


var client = new Ationet.Sdk.Interface.InterfaceOperations("https://native.ationet.com/", 
    "[YOUR-USERNAME]", "[YOUR-PASSWORD]");
var transactions = client.GetTransactions("XYZ", "", "", DateTime.Now.AddDays(-1));

foreach (var tran in transactions.Content)
{
    Console.WriteLine("{0} - {1} - {2}", tran.AuthorizationCode, tran.TerminalCode, tran.ProductAmountDispensed);
}


```

First, you need an instance of the *InterfaceOperations* class. The constructor of this class requires 3 parameters, the url, username and password.
Once you have an instance of the *InterfaceOperations* class you can start calling the different methods. Find below the list of all the methods by *Operation Type*:


## Operation Types methods
Each Operation Type class has multiple methods to perform specific operation against ATIOnet. Each of this methods has a set of parameters, some of them to determine behaviour and others to filter data.

### Auth Methods


<table>
     <thead>
        <tr> 
			<td>Method</td>
			<td>Parameters</td>
			<td>Description</td>
		</tr>
     </thead>
     <tbody>
        <tr>
          	<td>SendConfirmation</td>
            <td>AuthTransactionRequest</td>
            <td>Sends a <i>Confirmation</i> message to the host (learn more about transactions flow here:</td>
        </tr>
        <tr>
          	<td>SendConfirmationAsync</td>
            <td>AuthTransactionRequest</td>
            <td>Async version of the previous method</td>
        </tr>
        <tr>
          	<td>SendPreAuthorization</td>
            <td>AuthTransactionRequest</td>
            <td>Sends a <i>Pre Authorization</i> message to the host (learn more about transactions flow here:</td>
        </tr>
        <tr>
          	<td>SendPreAuthorizationAsync</td>
            <td>AuthTransactionRequest</td>
            <td>Async version of the previous method</td>
        </tr>
        <tr>
          	<td>SendSale</td>
            <td>AuthTransactionRequest</td>
            <td>Sends a <i>Sale</i> message to the host (learn more about transactions flow here:</td>
        </tr>
        <tr>
          	<td>SendSaleAsync</td>
            <td>AuthTransactionRequest</td>
            <td>Async version of the previous method</td>
        </tr>
	</tbody>
</table>
<BR/>
You can download a fully functional sample code from here: https://github.com/atioint/ationetsdksamples/tree/master/AtionetAuthSample](https://github.com/atioint/ationetsdksamples/tree/master/AtionetAuthSample

### Api Methods

#### AuditLog
|Type|Name|Description|
|--- |--- |--- |
|string|NetworkDateString||
|DateTime?|NetworkDate||
|string|NewData||
|string|OriginalData||
|Guid? |EntityId||
|string |MerchantName||
|string |CompanyName||
|string |NetworkName||
|string |UserName||
|Guid |UserId||
|string |OriginDescription||
|int? |Origin||
|string |ActionDescription||
|int |Action||
|string |SubCategoryDescription||
|int? |SubCategory||
|string |CategoryDescription||
|int |Category||
|int |Environment||
|Guid? |MerchantId||
|Guid? |CompanyId||
|Guid? |NetworkId||
|Guid |Id||
|DateTime |RealDate||
|string |RealDateString||

|Method|Parameters (Type / var name / default value / Descr)|Response|Description|
|--- |--- |--- |--- |
|GetLogs|List&lt;Guid>  userIds <BR> List&lt;int>  categories <BR> string dateFrom <BR> string dateTo = null <BR> Guid? idCompany = null<BR> int page = 1 <BR>int pageSize = 50 <BR>int? action = null <BR>int? subCategory = null <BR>string timeFrom = null <BR>string timeTo = null|AuditLogDto|Get list of the AuditLogDto|
|GetLogsAsync|List&lt;Guid>  userIds <BR>List&lt;int>  categories<BR> string dateFrom <BR>string dateTo = null <BR>Guid? idCompany = null <BR>int page = 1 <BR>int pageSize = 50 <BR>int? action = null <BR>int? subCategory = null <BR>string timeFrom = null <BR>string timeTo = null|AuditLogDto|Get list of the AuditLogDto|

#### CompanyDto
|Type|Name|Description|
|--- |--- |--- |
|string |Custom1||
|string |Custom0||
|byte? |DesactivationType||
|bool |Active||
|string |ContactPhone2||
|string |ContactPhone1||
|string |ContactEmail||
|string |ContactName||
|DateTime |UpdateDate||
|byte |Type||
|DateTime |CreationDate||
|string |IndustryDescription||
|Guid |IndustryId||
|string |Custom2||
|string |TaxpayerCategoryDescription||
|string |TaxPayerId||
|string |City||
|string |ZipCode||
|string |StateDescription||
|Guid |StateId||
|string |CountryDescription||
|Guid |CountryId||
|string |Street2||
|string |Street1||
|string |Name||
|string |Code||
|Guid |NetworkId||
|Guid |Id||
|Guid |TaxpayerCategoryId||
|string |Custom3||

|Method|Parameters|Response|Description|
|--- |--- |--- |--- |
|GetCompanies|List&lt;Guid>  companyIds = null <BR>string code = null <BR>string name = null <BR>string custom0 = null <BR>string custom1 = null <BR>string custom2 = null <BR>string custom3 = null <BR>DateTime? updateDate = null <BR>int page = 1 <BR>int pageSize = 50 <BR>string orderField = "name" <BR>string orderType = "asc"|CompanyDto|Get list of the CompanyDto|
|GetCompaniesAsync|List&lt;Guid> companyIds = null <BR>string code = null <BR>string name = null <BR>string custom0 = null <BR>string custom1 = null <BR>string custom2 = null <BR>string custom3 = null <BR>DateTime? updateDate = null <BR>int page = 1 <BR>int pageSize = 50 <BR>string orderField = "name" <BR>string orderType = "asc"|CompanyDto|Get list of the CompanyDto|
|GetCompany|Guid id|CompanyDto|Get individual CompanyDto|
|GetCompanyAsync|Guid id|CompanyDto|Get individual CompanyDto|
|CreateCompany|CompanyDto data|CompanyDto|Create CompanyDto|
|CreateCompanyAsync|CompanyDto data|CompanyDto|Create CompanyDto|
|UpdateCompany|Guid id <BR>CompanyDto data|string|Update CompanyDto|
|UpdateCompanyAsync|Guid id <BR>CompanyDto data|string|Update CompanyDto|


#### CompanyClassificationsConfigurationDto
|Data|Description|
|--- |--- |
|Guid IdCompany|Identification of de Company|
|string Classification1Label|classification 1 Label|
|string Classification2Label|classification 2 Label|
|string Classification3Label|classification 3 Label|
|string Classification4Label|classification 4 Label|
|bool Classification1Enabled|status for the use of the company|
|bool Classification2Enabled|status for the use of the company|
|bool Classification3Enabled|status for the use of the company|
|bool Classification4Enabled|status for the use of the company|

|Method|Parameters|Response|Description|
|--- |--- |--- |--- |
|GetCompaniesClassificationsConfiguration||CompanyClassificationsConfigurationDto|Get the configuractions of the Classifications Companies|
|GetCompaniesClassificationsConfigurationAsync||CompanyClassificationsConfigurationDto|Get the configuractions of the Classifications Companies|
|UpdateCompaniesClassificationsConfiguration|CompanyClassificationsConfigurationDto data|string|Update configuractions of the Classifications Companies|
|UpdateCompaniesClassificationsConfigurationAsync|CompanyClassificationsConfigurationDto data|string|Update configuractions of the Classifications Companies|

#### CompaniesGroupsMovementDto
|Data|Description|
|--- |--- |
|string TypeDescription||
|Guid? IdOrigen||
|byte Origen||
|DateTime NetworkDate||
|DateTime RealDate||
|bool IsDebit||
|string DisplayDateTimeString||
|Guid? IdCurrencyCode||
|string Description||
|byte Type||
|string CompaniesGroupDescription||
|Guid IdCompaniesGroup||
|Guid IdNetwork||
|Guid Id||
|decimal Amount||
|string DisplayNetworkDateTimeString||


|Method|Parameters|Response|Description|
|--- |--- |--- |--- |
|GetCompaniesGroupsMovements||CompaniesGroupsMovementDto|Get list of the CompaniesGroupsMovementDto|
|GetCompaniesGroupsMovements|Guid? companiesGroupId = null string companiesGroupCode = null string dateFrom = null string dateTo = null decimal? amountFrom = null decimal? amountTo = null byte? type = null byte? origin = null int page = 1 int pageSize = 50 string orderField = "networkDate" string orderType = "asc"|CompaniesGroupsMovementDto|Get list of the CompaniesGroupsMovementDto|
|GetCompaniesGroupsMovementsAsync|Guid? companiesGroupId = null string companiesGroupCode = null string dateFrom = null string dateTo = null decimal? amountFrom = null decimal? amountTo = null byte? type = null byte? origin = null int page = 1 int pageSize = 50 string orderField = "networkDate" string orderType = "asc"|CompaniesGroupsMovementDto|Get list of the CompaniesGroupsMovementDto|
|GetCompaniesGroupsMovementAsync|Guid id|CompaniesGroupsMovementDto|Get individual CompaniesGroupsMovementDto|
|CreateCompaniesGroupsMovement|CompanyClassificationsConfigurationDto data|string|Create a CompaniesGroupsMovement|
|CreateCompaniesGroupsMovementAsync|CompanyClassificationsConfigurationDto data|string|Create a CompaniesGroupsMovement|

#### CompanyClassificationDto
|Data|Description|
|--- |--- |
|Guid Id||
|Guid IdCompany||
|string Code||
|string Description||

|Method|Parameters|Response|Description|
|--- |--- |--- |--- |
|GetCompaniesClassifications1|int page = 1 int pageSize = 50 string orderType = "asc"|CompanyClassificationDto|Get list of the CompanyClassificationDto|
|GetCompaniesClassifications1Async|int page = 1 int pageSize = 50 string orderType = "asc"|CompanyClassificationDto|Get list of the CompanyClassificationDto|
|GetCompaniesClassifications2|int page = 1 int pageSize = 50 string orderType = "asc"|CompanyClassificationDto|Get list of the CompanyClassificationDto|
|GetCompaniesClassifications2Async|int page = 1 int pageSize = 50 string orderType = "asc"|CompanyClassificationDto|Get list of the CompanyClassificationDto|
|GetCompaniesClassifications3|int page = 1 int pageSize = 50 string orderType = "asc"|CompanyClassificationDto|Get list of the CompanyClassificationDto|
|GetCompaniesClassifications3Async|int page = 1 int pageSize = 50 string orderType = "asc"|CompanyClassificationDto|Get list of the CompanyClassificationDto|
|GetCompaniesClassifications4|int page = 1 int pageSize = 50 string orderType = "asc"|CompanyClassificationDto|Get list of the CompanyClassificationDto|
|GetCompaniesClassifications4Async|int page = 1 int pageSize = 50 string orderType = "asc"|CompanyClassificationDto|Get list of the CompanyClassificationDto|
|GetCompanyClassifications1|Guid id|CompanyClassificationDto|Get individual CompanyClassificationDto|
|GetCompanyClassifications1Async|Guid id|CompanyClassificationDto|Get individual CompanyClassificationDto|
|GetCompanyClassifications2|Guid id|CompanyClassificationDto|Get individual CompanyClassificationDto|
|GetCompanyClassifications2Async|Guid id|CompanyClassificationDto|Get individual CompanyClassificationDto|
|GetCompanyClassifications3|Guid id|CompanyClassificationDto|Get individual CompanyClassificationDto|
|GetCompanyClassifications3Async|Guid id|CompanyClassificationDto|Get individual CompanyClassificationDto|
|GetCompanyClassifications4|Guid id|CompanyClassificationDto|Get individual CompanyClassificationDto|
|GetCompanyClassifications4Async|Guid id|CompanyClassificationDto|Get individual CompanyClassificationDto|
|CreateCompaniesClassification1|CompanyClassificationDto data|CompanyClassificationDto|Create CompanyClassificationDto|
|CreateCompaniesClassification1Async|CompanyClassificationDto data|CompanyClassificationDto|Create CompanyClassificationDto|
|CreateCompaniesClassification2|CompanyClassificationDto data|CompanyClassificationDto|Create CompanyClassificationDto|
|CreateCompaniesClassification2Async|CompanyClassificationDto data|CompanyClassificationDto|Create CompanyClassificationDto|
|CreateCompaniesClassification3|CompanyClassificationDto data|CompanyClassificationDto|Create CompanyClassificationDto|
|CreateCompaniesClassification3Async|CompanyClassificationDto data|CompanyClassificationDto|Create CompanyClassificationDto|
|CreateCompaniesClassification4|CompanyClassificationDto data|CompanyClassificationDto|Create CompanyClassificationDto|
|CreateCompaniesClassification4Async|CompanyClassificationDto data|CompanyClassificationDto|Create CompanyClassificationDto|
|UpdateCompaniesClassification1|CompanyClassificationDto data|CompanyClassificationDto|Update CompanyClassificationDto|
|UpdateCompaniesClassification1Async|CompanyClassificationDto data|CompanyClassificationDto|Update CompanyClassificationDto|
|UpdateCompaniesClassification2|CompanyClassificationDto data|CompanyClassificationDto|Update CompanyClassificationDto|
|UpdateCompaniesClassification2Async|CompanyClassificationDto data|CompanyClassificationDto|Update CompanyClassificationDto|
|UpdateCompaniesClassification3|CompanyClassificationDto data|CompanyClassificationDto|Update CompanyClassificationDto|
|UpdateCompaniesClassification3Async|CompanyClassificationDto data|CompanyClassificationDto|Update CompanyClassificationDto|
|UpdateCompaniesClassification4|CompanyClassificationDto data|CompanyClassificationDto|Update CompanyClassificationDto|
|UpdateCompaniesClassification4Async|CompanyClassificationDto data|CompanyClassificationDto|Update CompanyClassificationDto|
|DeleteCompaniesClassification1|Guid id|string|delete CompanyClassificationDto|
|DeleteCompaniesClassification1Async|Guid id|string|delete CompanyClassificationDto|
|DeleteCompaniesClassification2|Guid id|string|delete CompanyClassificationDto|
|DeleteCompaniesClassification2Async|Guid id|string|delete CompanyClassificationDto|
|DeleteCompaniesClassification3|Guid id|string|delete CompanyClassificationDto|
|DeleteCompaniesClassification3Async|Guid id|string|delete CompanyClassificationDto|
|DeleteCompaniesClassification4|Guid id|string|delete CompanyClassificationDto|
|DeleteCompaniesClassification4Async|Guid id|string|delete CompanyClassificationDto|


#### CompanyContractDto
|Data|Description|
|--- |--- |
|List CompanyContractProductDto  Products||
|List CompanyContractSiteDto  Sites||
|List CompanyContractFuelDto  Fuels||
|CompanyContractBillingDto Billing||
|decimal? ReactivationAmount||
|byte? DeactivationType||
|bool Active||
|bool ValidateSites||
|decimal? SecurityLimit||
|decimal? Limit||
|Guid? CurrencyId||
|byte CurrentAccountMode||
|List CompanyContractDiscountDto  Discounts||
|short BalanceMode||
|byte Periodicity||
|string StartDate||
|decimal Version||
|string InternalCode||
|byte Mode||
|string Description||
|string Code||
|byte Type||
|Guid NetworksCompanyId||
|Guid CompanyId||
|Guid NetworkId||
|Guid Id||
|short Duration||
|bool MoneyBalance||

|Method|Parameters|Response|Description|
|--- |--- |--- |--- |
|GetContracts|string companyCode = null List Guid contractIds = null string code = null int page = 1 int pageSize = 50 string orderField = "description" string orderType = "asc"|CompanyContractDto|Get list of the CompanyContractDto|
|GetContractsAsync|string companyCode = null List Guid contractIds = null string code = null int page = 1 int pageSize = 50 string orderField = "description" string orderType = "asc"|CompanyContractDto|Get list of the CompanyContractDto|
|GetContract|Guid id|CompanyContractDto|Get individual CompanyContractDto|
|GetContractAsync|Guid id|CompanyContractDto|Get individual CompanyContractDto|
|CreateContract|CompanyContractDto data|CompanyContractDto|Create CompanyContractDto|
|CreateContractAsync|CompanyContractDto data|CompanyContractDto|Create CompanyContractDto|
|UpdateContract|CompanyContractDto data|CompanyContractDto|Update CompanyContractDto|
|UpdateContractAsync|CompanyContractDto data|CompanyContractDto|Update CompanyContractDto|

#### CompanyContractOverLimitDto
|Data|Description|
|--- |--- |
|Guid Id||
|Guid IdCompanyContract||
|string ContractName||
|Guid IdCompany||
|string CompanyName||
|Guid IdNetwork||
|string DateFrom||
|string DateTo||
|string CreationDate||
|string CreationNetworkDate||
|string NetworkTimeZone||
|decimal Value||
|byte Type||
|byte State||

|Method|Parameters|Response|Description|
|--- |--- |--- |--- |
|GetCompanyContractOverLimits|Guid? idCompany = null Guid? idCompanyContract = null string dateFrom = null string dateTo = null string creationDate = null byte? filterType = null int page = 1 int pageSize = 50 string orderField = "idFuelMaster" string orderType = "asc"|CompanyContractOverLimitDto|Get list of the CompanyContractOverLimitDto|
|GetCompanyContractOverLimitsAsync|Guid? idCompany = null Guid? idCompanyContract = null string dateFrom = null string dateTo = null string creationDate = null byte? filterType = null int page = 1 int pageSize = 50 string orderField = "idFuelMaster" string orderType = "asc"|CompanyContractOverLimitDto|Get list of the CompanyContractOverLimitDto|
|GetCompanyContractOverLimit|Guid id|CompanyContractOverLimitDto|Get individual CompanyContractOverLimitDto|
|GetCompanyContractOverLimitAsync|Guid id|CompanyContractOverLimitDto|Get individual CompanyContractOverLimitDto|
|CreateCompanyContractOverLimit|CompanyContractOverLimitDto data|CompanyContractOverLimitDto|Create CompanyContractOverLimitDto|
|CreateCompanyContractOverLimitAsync|CompanyContractOverLimitDto data|CompanyContractOverLimitDto|Create CompanyContractOverLimitDto|
|UpdateCompanyContractOverLimit|Guid id CompanyContractOverLimitDto data|CompanyContractOverLimitDto|Update CompanyContractOverLimitDto|
|UpdateCompanyContractOverLimitAsync|Guid id CompanyContractOverLimitDto data|CompanyContractOverLimitDto|Update CompanyContractOverLimitDto|

#### CompanyInvoiceDto
|Data|Description|
|--- |--- |
|Guid Id||
|Guid IdNetwork||
|Guid IdCompany||
|string InvoiceNumber||
|byte Type||
|DateTime Date||
|decimal Net||
|decimal Taxes||
|decimal? Total||
|IEnumerable CompanyInvoiceDetailDto CompaniesInvoicesDetails||
|IEnumerable TransactionDto  Transactions||

|Method|Parameters|Response|Description|
|--- |--- |--- |--- |
|GetInvoices|string companyCode = null List Guid companyIds = null string invoiceNumber = null byte? invoiceType = null DateTime? dateFrom = null DateTime? dateTo = null int page = 1 int pageSize = 50 string orderField = "description" string orderType = "asc"|CompanyInvoiceDto|Get list of the CompanyInvoiceDto|
|GetInvoicesAsync|string companyCode = null List Guid companyIds = null string invoiceNumber = null byte? invoiceType = null DateTime? dateFrom = null DateTime? dateTo = null int page = 1 int pageSize = 50 string orderField = "description" string orderType = "asc"|CompanyInvoiceDto|Get list of the CompanyInvoiceDto|
|GetInvoice|Guid id|CompanyInvoiceDto|Get individual CompanyInvoiceDto|
|GetInvoiceAsync|Guid id|CompanyInvoiceDto|Get individual CompanyInvoiceDto|
|CreateInvoice|CompanyInvoiceDto data|CompanyInvoiceDto|Create CompanyInvoiceDto|
|CreateInvoiceAsync|CompanyInvoiceDto data|CompanyInvoiceDto|Create CompanyInvoiceDto|
|UpdateInvoice|CompanyInvoiceDto data|string|Update CompanyInvoiceDto|
|UpdateInvoiceAsync|CompanyInvoiceDto data|string|Update CompanyInvoiceDto|

#### CurrentAccountReportDto
|Data|Description|
|--- |--- |
|short? CompanyContractDuration||
|int? CompanyContractAccountsLimit||
|decimal? CompanyContractVersion||
|string ContractCode||
|decimal? Balance||
|bool? IsDebit||
|decimal? CreditLimit||
|decimal? OverLimit||
|Guid? StatementId||
|string MovementTypeDescription||
|string CompanyContractDescription||
|string VehicleDescription||
|string DriverDescription||
|string CompleteName||
|string FuelName||
|string ModeDescription||
|decimal? Debit||
|decimal? Credit||
|decimal BillingValue||
|bool Enable||
|string CompanyContractExpirationDate||
|string IdentificationsDescription||
|string LocalDateShortString||
|byte? CompanyContractPeriodicity||
|DateTime? CompanyContractStartDate||
|string SiteFuelName||
|string NetworkFuelName||
|Guid Id||
|Guid? IdMovement||
|Guid? IdCompanyContract||
|Guid? IdFuelMaster||
|Guid? IdSubAccount||
|string Description||
|decimal Amount||
|Guid? IdCurrencyCode||
|Guid? IdUserAtionet||
|byte MovementType||
|string NetworkName||
|string LocalTimeString||
|string CompanyName||
|string MovementIdOrigin||
|string MovementDescription||
|byte ContractMode||
|Guid? VehicleId||
|string VehiclePlate||
|string VehicleCode||
|Guid? DriverId||
|string DriverCode||
|string DriverFirstName||
|string DriverLastName||
|string FuelMasterName||
|DateTime MovementDate||
|string DisplayDateTimeString||

|Method|Parameters|Response|Description|
|--- |--- |--- |--- |
|GetContractsBalance|Guid? idContract string dateFrom = null string dateTo = null string order = "desc" int page = 1 int pageSize = 50|CurrentAccountReportDto|Get list of the CurrentAccountReportDto|
|GetContractsBalanceAsync|Guid? idContract string dateFrom = null string dateTo = null string order = "desc" int page = 1 int pageSize = 50|CurrentAccountReportDto|Get list of the rentAccountReportDto|
|GetContractsMovements|Guid idContract string dateFrom = null string dateTo = null string order = "desc" int page = 1 int pageSize = 50|CurrentAccountReportDto|Get list of the CurrentAccountReportDto|
|GetContractsMovementsAsync|Guid idContract string dateFrom = null string dateTo = null string order = "desc" int page = 1 int pageSize = 50|CurrentAccountReportDto|Get list of the CurrentAccountReportDto|
|GetSubAccountsBalance|Guid? idContract=nullGuid? idSubAccount=null string dateFrom = null string dateTo = null  string order = "desc" int page = 1 int pageSize = 50|CurrentAccountReportDto|Get list of the CurrentAccountReportDto|
|GetSubAccountsBalanceAsync|Guid? idContract=nullGuid? idSubAccount=null string dateFrom = null string dateTo = null string order = "desc" int page = 1 int pageSize = 50|CurrentAccountReportDto|Get list of the CurrentAccountReportDto|
|GetSubAccountsMovements|Guid? idContract=nullGuid? idSubAccount=null string dateFrom = null string dateTo = null string order = "desc" int page = 1 int pageSize = 50|CurrentAccountReportDto|Get list of the CurrentAccountReportDto|
|GetSubAccountsMovementsAsync|Guid? idContract=nullGuid? idSubAccount=null string dateFrom = null string dateTo = null string order = "desc" int page = 1 int pageSize = 50|CurrentAccountReportDto|Get list of the CurrentAccountReportDto|

#### CountryDto
|Data|Description|
|--- |--- |
|Guid Id||
|string Name||

|Method|Parameters|Response|Description|
|--- |--- |--- |--- |
|GetCountries|int page = 1 int pageSize = 50|CompanyInvoiceDto|Get list of the CountryDto|
|GetCountriesAsync|int page = 1 int pageSize = 50|CountryDto|Get list of the CountryDto|

#### DriverDto
|Data|Description|
|--- |--- |
|string CompanyContractDuration||
|string Clasification2Description||
|Guid? Clasification3Id||
|string Clasification3Description||
|Guid? Clasification4Id||
|string Clasification4Description||
|List DriverRuleDto  Rules||
|List DriverVehicleDto2> Vehicles||
|List DriverIdentificationDto Identifications||
|List DriverLoyaltyIdentificationDto LoyaltyIdentifications||
|string Balance||
|string Consumption||
|string IdentificationsDescription||
|string LoyaltyProgramsDescription||
|string LoyaltyIdentificationsDescription||
|List DriverVehicleDto VehiclesDrivers||
|string Custom0||
|string Custom1||
|string Custom2||
|string Custom3||
|Guid? Clasification2Id||
|string Clasification1Description||
|Guid? Clasification1Id||
|string Email||
|Guid Id||
|Guid CompanyId||
|string CompanyName||
|string Code||
|string LastName||
|string FirstName||
|string CompleteName||
|string Birthdate||
|string LicenseNumber||
|decimal? AvaliableAmount||
|bool Enabled||
|string CountryName||
|Guid? StateId||
|string StateName||
|string City||
|string Street1||
|string Street2||
|string ZipCode||
|string PhoneNumber1||
|string PhoneNumber2||
|Guid? CountryId||
|decimal? AvaliableVolume||

|Method|Parameters|Response|Description|
|--- |--- |--- |--- |
|GetDrivers|List Guid identificationIds = null List Guid ruleIds = null List Guid classification1Ids = null List Guid classification2Ids = null List Guid classification3Ids = null List Guid classification4Ids = null string code = null string name = null string custom0 = null string custom1 = null string custom2 = null string custom3 = null int page = 1 int pageSize = 50 string orderField = "code" string orderType = "asc"|DriverDto|Get list of the DriverDto|
|GetDriversAsync|List Guid identificationIds = null List Guid ruleIds = null List Guid classification1Ids = null List Guid classification2Ids = null List Guid classification3Ids = null List Guid classification4Ids = null string code = null string name = null string custom0 = null string custom1 = null string custom2 = null string custom3 = null int page = 1 int pageSize = 50 string orderField = "code" string orderType = "asc"|DriverDto|Get list of the DriverDto|
|GetDriver|Guid id|DriverDto|Get individual DriverDto|
|GetDriverAsync|Guid id|DriverDto|Get individual DriverDto|
|CreateDriver|DriverDto data|DriverDto|Create DriverDto|
|CreateDriverAsync|DriverDto data|DriverDto|Create DriverDto|
|UpdateDriver|Guid id DriverDto data|string|Update DriverDto|
|UpdateDriverAsync|Guid id DriverDto data|string|Update DriverDto|

#### FleetDto
|Data|Description|
|--- |--- |
|string Clasification4Description||
|Guid? IdClasification4||
|string Clasification3Description||
|Guid? IdClasification3||
|string Clasification2Description||
|Guid? IdClasification2||
|string Clasification1Description||
|Guid? IdClasification1||
|string Code||
|string City||
|string StateDescription||
|Guid? IdState||
|string CountryDescriptiion||
|Guid? IdCountry||
|string Streep2||
|string Street1||
|string Name||
|string CompanyDescription||
|Guid IdCompany||
|Guid Id||
|List EntityRuleDto  Rules||

|Method|Parameters|Response|Description|
|--- |--- |--- |--- |
|GetFleets|string code = null string name = null int page = 1 int pageSize = 50 string orderField = "name" string orderType = "asc"|FleetDto|Get list of the FleetDto|
|GetFleetsAsync|string code = null string name = null int page = 1 int pageSize = 50 string orderField = "name" string orderType = "asc"|FleetDto|Get list of the FleetDto|
|GetFleet|Guid id|FleetDto|Get individual FleetDto|
|GetFleetAsync|Guid id|FleetDto|Get individual FleetDto|
|CreateFleet|FleetDto data|FleetDto|Create FleetDto|
|CreateFleetAsync|FleetDto data|FleetDto|Create FleetDto|
|UpdateFleet|Guid id FleetDto data|string|Update FleetDto|
|UpdateFleetAsync|Guid id FleetDto data|string|Update FleetDto|

#### FuelDto
|Data|Description|
|--- |--- |
|string CodeBrandFuelMasterDescription||
|Guid Id||
|Guid MerchantId||
|string MerchantName||
|Guid SiteId||
|string SiteShortName||
|Guid FuelsMasterId||
|string FuelMasterDescription||
|string BrandFuelMasterDescription||
|string Code||

|Method|Parameters|Response|Description|
|--- |--- |--- |--- |
|GetFuels|int page = 1 int pageSize = 50 string orderField = "code" string orderType = "asc"|FuelDto|Get list of the FuelDto|
|GetFuelsAsync|int page = 1 int pageSize = 50 string orderField = "code" string orderType = "asc"|FuelDto|Get list of the FuelDto|
|GetFuel|Guid id|FuelDto|Get individual FuelDto|
|GetFuelAsync|Guid id|FuelDto|Get individual FuelDto|
|CreateFuel|FuelDto data|FuelDto|Create FuelDto|
|CreateFuelAsync|FuelDto data|FuelDto|Create FuelDto|
|UpdateFuel|Guid id FuelDto data|string|Update FuelDto|
|UpdateFuelAsync|Guid id FuelDto data|string|Update FuelDto|

#### FuelsMasterDto
|Data|Description|
|--- |--- |
|Guid Id||
|short? Type||
|string Code||
|string Description||
|byte? ContingencyCode||

|Method|Parameters|Response|Description|
|--- |--- |--- |--- |
|GetFuelsMasters|int page = 1 int pageSize = 50 string orderField = "code" string orderType = "asc"|FuelsMasterDto|Get list of the FuelsMasterDto|
|GetFuelsMastersAsync|int page = 1 int pageSize = 50 string orderField = "code" string orderType = "asc"|FuelsMasterDto|Get list of the FuelsMasterDto|
|GetFuelsMaster|Guid id|FuelsMasterDto|Get individual FuelsMasterDto|
|GetFuelsMasterAsync|Guid id|FuelsMasterDto|Get individual FuelsMasterDto|

#### GiftCardClientDto
|Data|Description|
|--- |--- |
|string PIN||
|bool RequiresPIN||
|bool IdentificationActive||
|string TypeModelDescription||
|Guid TypeModelId||
|short Type||
|int RequestOrder||
|DateTime? RequestOrderDate||
|byte GiftCardState||
|DateTime CreationDate||
|int? PINDigits||
|Guid? GiftCardRequestOrderId||
|Guid GiftCardProgramValueId||
|Guid GiftCardDriverId||
|Guid GiftCardSubAccountId||
|Guid GiftCardIdentificationId||
|Guid GiftCardProgramId||
|string IdentificationLabel||
|string IdentificationTrackNumber||
|decimal? Balance||
|Guid NetworkId||
|Guid Id||
|string GiftCardProgramName||
|string PAN||

|Method|Parameters|Response|Description|
|--- |--- |--- |--- |
|GetGiftCardClients|Guid? programId = null byte? cardState = null DateTime? CreatedFrom = null DateTime? CreatedTo = null decimal? BalanceFrom = null decimal? BalanceTo = null bool? active = null int page = 1 int pageSize = 50 string orderField = "label" string orderType = "asc" string pan = ""|GiftCardClientDto|Get list of the GiftCardClientDto|
|GetGiftCardClientsAsync|Guid? programId = null byte? cardState = null DateTime? CreatedFrom = null DateTime? CreatedTo = null decimal? BalanceFrom = null decimal? BalanceTo = null bool? active = null int page = 1 int pageSize = 50 string orderField = "label" string orderType = "asc" string pan = ""|GiftCardClientDto|Get list of the GiftCardClientDto|
|GetGiftCardClient|Guid id|GiftCardClientDto|Get individual GiftCardClientDto|
|GetGiftCardClientAsync|Guid id|GiftCardClientDto|Get individual GiftCardClientDto|
|CreateGiftCardClient|GiftCardClientDto data|GiftCardClientDto|Create GiftCardClientDto|
|CreateGiftCardClientAsync|GiftCardClientDto data|GiftCardClientDto|Create GiftCardClientDto|
|UpdateGiftCardClient|GiftCardClientDto data|string|Update GiftCardClientDto|
|UpdateGiftCardClientAsync|GiftCardClientDto data|string|Update GiftCardClientDto|

#### GiftCardProgramDto
|Data|Description|
|--- |--- |
|List GiftCardProgramValueDto  Values||
|List GiftCardProgramSiteDto  Sites||
|List GiftCardProgramFuelDto  Fuels||
|List GiftCardProgramDiscountDto  Discounts||
|string BINRange||
|short? CardDuration||
|byte? CardPeriodicity||
|bool ActiveCards||
|bool ValidateSites||
|string StartDate||
|short Duration||
|byte Periodicity||
|byte CurrentAccountMode||
|bool Rechargable||
|bool SingleUse||
|string Description||
|string Name||
|string Code||
|string NetworkName||
|Guid NetworkId||
|Guid Id||
|GiftCardProgramIdentificationTypeModelDto IdentificationsTypesModel||
|GiftCardProgramRuleDto Rule||

|Method|Parameters|Response|Description|
|--- |--- |--- |--- |
|GetGiftCardPrograms|Guid? NetworkId Guid? IdSite string name = null int page = 1 int pageSize = 50 string orderField = "label" string orderType = "asc"|GiftCardProgramDto|Get list of the GiftCardProgramDto|
|GetGiftCardProgramsAsync|Guid? NetworkId Guid? IdSite string name = null int page = 1 int pageSize = 50 string orderField = "label" string orderType = "asc"|GiftCardProgramDto|Get list of the GiftCardProgramDto|
|GetGiftCardProgram|Guid id|GiftCardProgramDto|Get individual GiftCardProgramDto|
|GetGiftCardProgramAsync|Guid id|GiftCardProgramDto|Get individual GiftCardProgramDto|
|CreateGiftCardProgram|GiftCardProgramDto data|GiftCardProgramDto|Create GiftCardProgramDto|
|CreateGiftCardProgramAsync|GiftCardProgramDto data|GiftCardProgramDto|Create GiftCardProgramDto|
|UpdateGiftCardProgram|Guid id GiftCardProgramDto data|string|Update GiftCardProgramDto|
|UpdateGiftCardProgramAsync|Guid id GiftCardProgramDto data|string|Update GiftCardProgramDto|

#### IdentificationDto
|Data|Description|
|--- |--- |
|string SubAccountDescription||
|Guid? DriverId||
|Guid? VehicleId||
|Guid? ProgramId||
|string ProgramDescription||
|Guid? LoyaltyProgramId||
|string LoyaltyProgramDescription||
|Guid? ContractId||
|string ContractDescription||
|bool RequiresPINChange||
|Guid? IdCompany||
|string CompanyName||
|string DriverCode||
|string DriverFirstName||
|string DriverLastName||
|string VehicleCode||
|string VehiclePlate||
|Guid? SubAccountId||
|string DriverDescription||
|string PIN||
|string ExpirationDateShort||
|Guid NetworkId||
|string NetworkName||
|Guid Id||
|byte UseType||
|short? Type||
|Guid TypeModelId||
|string TypeModelDescription||
|string Label||
|string TrackNumber||
|string PAN||
|byte State||
|bool Active||
|string CreationDate||
|string UpdateDate||
|string AssignmentDate||
|string ExpirationDate||
|string AssignmentDateShort||
|int? RequestOrder||
|string VehicleDescription||

|Method|Parameters|Response|Description|
|--- |--- |--- |--- |
|GetIdentifications|List Guid  contractIds = null string label = null Guid? vehicle = null Guid? driver = null byte? type = null Guid? model = null Guid? program = null byte? status = null byte? active = null string pan = null int page = 1int pageSize = 50 string orderField = "label" string orderType = "asc"|IdentificationDto|Get list of the IdentificationDto|
|GetIdentificationsAsync|List Guid  contractIds = null string label = null Guid? vehicle = null Guid? driver = null byte? type = null Guid? model = null Guid? program = null byte? status = null byte? active = null string pan = null int page = 1int pageSize = 50 string orderField = "label" string orderType = "asc"|IdentificationDto|Get list of the IdentificationDto|
|GetIdentification|Guid id|IdentificationDto|Get individual IdentificationDto|
|GetIdentificationAsync|Guid id|IdentificationDto|Get individual IdentificationDto|
|CreateIdentification|IdentificationDto data|IdentificationDto|Create IdentificationDto|
|CreateIdentificationAsync|IdentificationDto data|IdentificationDto|Create IdentificationDto|
|UpdateIdentification|Guid id IdentificationDto data|string|Update IdentificationDto|
|UpdateIdentificationAsync|Guid id IdentificationDto data|string|Update IdentificationDto|

#### IdentificationDto
|Data|Description|
|--- |--- |
|Guid Id||
|string PIN||

|Method|Parameters|Response|Description|
|--- |--- |--- |--- |
|UpdateIdentificationChangePin|Guid id IdentificationsChangePinDto data|string|Update Pin of identification|
|UpdateIdentificationChangePinAsync|Guid id IdentificationsChangePinDto data|string|Update Pin of identification|

#### IdentificationsProviderDto
|Data|Description|
|--- |--- |
|Guid Id||
|Guid IdNetwork||
|tring Name||
|string Email||
|string EmailTemplate||

|Method|Parameters|Response|Description|
|--- |--- |--- |--- |
|GetIdentificationsProviders|string name = null int page = 1 int pageSize = 50 string orderField = "name" string orderType = "asc"|IdentificationsProviderDto|Get list of the IdentificationsProviderDto|
|GetIdentificationsProvidersAsync|string name = null int page = 1 int pageSize = 50 string orderField = "name" string orderType = "asc"|IdentificationsProviderDto|Get list of the IdentificationsProviderDto|
|GetIdentificationProvider|Guid id|IdentificationsProviderDto|Get individual IdentificationsProviderDto|
|GetIdentificationProviderAsync|Guid id|IdentificationsProviderDto|Get individual IdentificationsProviderDto|
|CreateIdentificationProvider|IdentificationsProviderDto data|IdentificationsProviderDto|Create IdentificationsProviderDto|
|CreateIdentificationProviderAsync|IdentificationsProviderDto data|IdentificationsProviderDto|Create IdentificationsProviderDto|
|UpdateIdentificationProvider|Guid id IdentificationsProviderDto data|string|Update IdentificationsProviderDto|
|UpdateIdentificationProviderAsync|Guid id IdentificationsProviderDto data|string|Update IdentificationsProviderDto|

#### IdentificationTypeModelDto
|Data|Description|
|--- |--- |
|Guid Id||
|Guid IdNetwork||
|short IdentificationType||
|string Description||
|bool Instalable||
|bool Personalized||
|bool Reusable||
|bool MultipleAssign||
|bool ValidateExpDate||
|bool RequierePin||
|int PinDigits||
|bool IgnoreTerminalVehicleIdBehavior||
|bool CustomTrack||
|bool RequiresPINChange||

|Method|Parameters|Response|Description|
|--- |--- |--- |--- |
|GetIdentificationTypeModels|short? identificationType = null int page = 1 int pageSize = 50 string orderField = "name" string orderType = "asc"|IdentificationTypeModelDto|Get list of the IdentificationTypeModelDto|
|GetIdentificationTypeModelsAsync|short? identificationType = null int page = 1 int pageSize = 50 string orderField = "name" string orderType = "asc"|IdentificationTypeModelDto|Get list of the IdentificationTypeModelDto|
|GetIdentificationtypeModel|Guid id|IdentificationTypeModelDto|Get individual IdentificationTypeModelDto|
|GetIdentificationtypeModelAsync|Guid id|IdentificationTypeModelDto|Get individual IdentificationTypeModelDto|

#### IdentityDto
|Data|Description|
|--- |--- |
|string ReportedCopy||
|string ReportedProcedureNumber||
|string ReportedIssueDate||
|string ReportedBirthDate||
|string ReportedSex||
|string ReportedLastName||
|string ReportedFirstName||
|string ReportedCountry||
|string ReportedIdentityNumber||
|bool UserConsent||
|string ProfilePicture||
|string ZipCode||
|string StreetAddress||
|DateTime? BirthDate||
|string Alias||
|string Name||
|byte? IdentityNumberType||
|string IdentityNumber||
|Guid IdNetwork||
|Guid Id||
|string PhoneNumber||
|List IdentityLoyaltyIdentificationDto  LoyaltyIdentifications||

|Method|Parameters|Response|Description|
|--- |--- |--- |--- |
|GetIdentities|string identitiyNumber = null string name = null bool? userConsent = null string searchText = null int page = 1 int pageSize = 50 string orderField = "name" string orderType = "asc"|IdentityDto|Get list of the IdentityDto|
|GetIdentitiesAsync|string identitiyNumber = null string name = null bool? userConsent = null string searchText = null int page = 1 int pageSize = 50 string orderField = "name" string orderType = "asc"|IdentityDto|Get list of the IdentityDto|
|GetIdentity|Guid id|IdentityDto|Get individual IdentityDto|
|GetIdentityAsync|Guid id|IdentityDto|Get individual IdentityDto|
|CreateIdentity|IdentityDto data|IdentityDto|Create IdentityDto|
|CreateIdentityAsync|IdentityDto data|IdentityDto|Create IdentityDto|
|UpdateIdentity|Guid id IdentityDto data|string|Update IdentityDto|
|UpdateIdentityAsync|Guid id IdentityDto data|string|Update IdentityDto|

#### LoyaltyAccountDto
|Data|Description|
|--- |--- |
|string VehiclePlate||
|Guid? IdFleet||
|Guid? IdVehicle||
|string DriverLastName||
|string DriverFirstName||
|string DriverEmail||
|string DriverCode||
|string DriverLicenseNumber||
|string VehicleCode||
|Guid? IdDriver||
|Guid IdNetwork||
|string IdentitiyName||
|byte IdentitiyNumberType||
|string IdentitiyNumber||
|Guid IdIdentity||
|Guid IdCompany||
|Guid IdCommunity||
|Guid Id||
|short CommunityTarget||
|IEnumerable LoyaltyClientCards||

|Method|Parameters|Response|Description|
|--- |--- |--- |--- |
|GetLoyaltyAccounts|string searchText = null string identificationLabel = null string identificationTrackNumber = null Guid? idCommunity = null Guid? idIdentity = null string identityNumber = null int page = 1 int pageSize = 50 string orderField = "label" string orderType = "asc"|LoyaltyAccountDto|Get list of the LoyaltyAccountDto|
|GetLoyaltyAccounts|string searchText = null string identificationLabel = null string identificationTrackNumber = null Guid? idCommunity = null Guid? idIdentity = null string identityNumber = null int page = 1 int pageSize = 50 string orderField = "label" string orderType = "asc"|LoyaltyAccountDto|Get list of the LoyaltyAccountDto|
|GetLoyaltyAccount|Guid id|LoyaltyAccountDto|Get individual LoyaltyAccountDto|
|GetLoyaltyAccountAsync|Guid id|LoyaltyAccountDto|Get individual LoyaltyAccountDto|
|CreateLoyaltyAccount|LoyaltyAccountDto data|LoyaltyAccountDto|Create LoyaltyAccountDto|
|CreateLoyaltyAccountAsync|LoyaltyAccountDto data|LoyaltyAccountDto|Create LoyaltyAccountDto|
|UpdateLoyaltyAccount|Guid id LoyaltyAccountDto data|string|Update LoyaltyAccountDto|
|UpdateLoyaltyAccountAsync|Guid id LoyaltyAccountDto data|string|Update LoyaltyAccountDto|

#### LoyaltyTransactionDto
|Data|Description|
|--- |--- |
|Guid? DriverId||
|string VehiclePlate||
|string VehicleCode||
|Guid? VehicleId||
|string FleetName||
|string FleetCode||
|string DriverCode||
|Guid? FleetId||
|string SecondaryLoyaltyAccountDescription||
|Guid? SecondaryLoyaltyAccountId||
|bool IsPrimaryLoyaltyAccountVehicle||
|string PrimaryLoyaltyAccountDescription||
|Guid? PrimaryLoyaltyAccountId||
|string SecondaryIdentificationPAN||
|bool IsSecondaryLoyaltyAccountVehicle||
|string DriverCompleteName||
|string AccountTypeDescription||
|string InvoiceNumber||
|bool EHVoided||
|bool Voided||
|short EHState||
|byte State||
|short ConciliationState||
|decimal? LoyaltyPoints||
|decimal? EHLoyaltyPoints||
|string EHComments||
|string EHAuthorizationCode||
|string UnitName||
|decimal? TransactionAmount||
|decimal? Amount||
|string EntryMethod||
|string ShiftNumber||
|int? BatchNumber||
|string SecondaryIdentificationLabel||
|List< PaymentsMethodDto PaymentMethods||
|Guid? SecondaryIdentificationId||
|string PrimaryIdentificationLabel||
|string StatusDescription||
|short? Status||
|string ModeDescription||
|short? Mode||
|string TypeDescription||
|short Type||
|string HostDateTime||
|string ResponseMessage||
|string AuthorizationCode||
|string TransactionSequenceNumber||
|string SubscriberName||
|string SubscriberCode||
|Guid? SubscriberId||
|Guid Id||
|string ResponseCode||
|string SubscriberDateTime||
|string SubscriberTimeZone||
|string SiteDateTime||
|Guid? PrimaryIdentificationId||
|string CompanyTaxpayerId||
|string CompanyName||
|string CompanyCode||
|Guid? CompanyId||
|string TerminalCode||
|Guid? TerminalId||
|string SiteName||
|string SiteCode||
|Guid? SiteId||
|string MerchantName||
|string MerchantCode||
|Guid? MerchantId||
|string DateTime||
|string SiteTimeZone||
|string PrimaryIdentificationPAN||
|List LoyaltyTransactionsProductDto  Products||

|Method|Parameters|Response|Description|
|--- |--- |--- |--- |
|GetLoyaltyTransactions|string dateTimeFrom = null string dateTimeTo = null int page = 1 int pageSize = 50 string orderField = "code" string orderType = "asc"|LoyaltyTransactionDto|Get list of the LoyaltyTransactionDto|
|GetLoyaltyTransactionsAsync|string dateTimeFrom = null string dateTimeTo = null int page = 1 int pageSize = 50 string orderField = "code" string orderType = "asc"|LoyaltyTransactionDto|Get list of the LoyaltyTransactionDto|
|GetLoyaltyTransaction|Guid id|LoyaltyTransactionDto|Get individual LoyaltyTransactionDto|
|GetLoyaltyTransactionAsync|Guid id|LoyaltyTransactionDto|Get individual LoyaltyTransactionDto|

#### MerchantDto
|Data|Description|
|--- |--- |
|string Custom1||
|string Custom0||
|bool Active||
|string ContactPhone2||
|string ContactPhone1||
|string ContactEmail||
|string ContactName||
|DateTime CreationDate||
|string IndustryDescription||
|Guid IndustryId||
|string Custom2||
|string TaxPayerId||
|string ZipCode||
|string StateDescription||
|Guid StateId||
|string CountryDescription||
|Guid CountryId||
|string Street2||
|string Street1||
|string Name||
|string Code||
|Guid Id||
|string City||
|string Custom3||

|Method|Parameters|Response|Description|
|--- |--- |--- |--- |
|GetMerchants|List Guid  merchantIds = null string code = null string name = null string custom0 = null string custom1 = null string custom2 = null string custom3 = null int page = 1 int pageSize = 50 string orderField = "name" string orderType = "asc"|MerchantDto|Get list of the MerchantDto|
|GetMerchantsAsync|List Guid  merchantIds = null string code = null string name = null string custom0 = null string custom1 = null string custom2 = null string custom3 = null int page = 1 int pageSize = 50 string orderField = "name" string orderType = "asc"|MerchantDto|Get list of the MerchantDto|
|GetMerchant|Guid id|MerchantDto|Get individual MerchantDto|
|GetMerchantAsync|Guid id|MerchantDto|Get individual MerchantDto|
|CreateMerchant|MerchantDto data|MerchantDto|Create MerchantDto|
|CreateMerchantAsync|MerchantDto data|MerchantDto|Create MerchantDto|
|UpdateMerchant|Guid id MerchantDto data|string|Update MerchantDto|
|UpdateMerchantAsync|Guid id MerchantDto data|string|Update MerchantDto|

#### MovementDto
|Data|Description|
|--- |--- |
|string OriginId||
|byte Origin||
|byte Type||
|DateTime NetworkDate||
|string NetworkTimeZone||
|DateTime RealDate||
|bool Reversed||
|string Description||
|Guid? UserAtionetId||
|Guid? ProcessBillingStatementId||
|Guid? FastTrackId||
|Guid? TransactionId||
|Guid CompanyId||
|Guid Id||
|Guid? LastMovementId||
|List MovementsDetailDto  DetailsMovementDto||

|Method|Parameters|Response|Description|
|--- |--- |--- |--- |
|GetMovements|Guid? idCompany=null Guid? fastTrackId = null Guid? lastMovementId = null Guid? processBillingStatementId = null Guid? transactionId = null Guid? userAtionetId = null string originId = null string description = null byte? origin = null byte? type = null bool? reversed = null string realDateFrom = null string realDateTo = null string order = "desc" int page = 1 int pageSize = 50|MovementDto|Get list of the MovementDto|
|GetMovementsAsync|Guid? idCompany=null Guid? fastTrackId = null Guid? lastMovementId = null Guid? processBillingStatementId = null Guid? transactionId = null Guid? userAtionetId = null string originId = null string description = null byte? origin = null byte? type = null bool? reversed = null string realDateFrom = null string realDateTo = null string order = "desc" int page = 1 int pageSize = 50|MovementDto|Get list of the MovementDto|
|GetMovement|Guid id|MovementDto|Get individual MovementDto|
|GetMovementAsync|Guid id|MovementDto|Get individual MovementDto|

#### NetworkDto
|Data|Description|
|--- |--- |
|string StateName||
|string TimeZone||
|string City||
|string Street1||
|string Street2||
|string ZipCode||
|string PhoneNumber1||
|string PhoneNumber2||
|string ContactName||
|string ContactEmail||
|string CreationDate||
|Guid StateId||
|Guid BrandId||
|string IdentificationRequestMail||
|string SupportMail||
|string SenderMail||
|bool IsEdiFactBillingProcessType||
|List NetworkCustomFieldsConfigurationDto  CustomFieldsConfigurations||
|List NetworkCompanyDto  Companies||
|List NetworkMerchantDto  Merchants||
|List NetworkFiscalConfigurationDto  FiscalConfigurations||
|string PrimaryColor||
|string SecondaryColor||
|string AccentColor||
|string BrandName||
|string NetworkLogoURL||
|string CountryName||
|string TaxPayerId||
|Guid Id||
|string Name||
|short Type||
|byte? BalanceMode||
|byte? CurrentAccountMode||
|byte BillingProcessType||
|short EdiFactTaxRegimeCode||
|string Code||
|string InternalCode||
|bool Active||
|bool SupportsLoyalty||
|Guid CountryId||
|bool SupportsInventory||
|bool SupportsTracking||
|bool SupportsFleet||
|bool SupportsAnalytics||
|bool SupportsConsumerCard||
|bool SupportsWorkflows||
|bool SupportsDriverMobileApp||
|bool SupportsCompanyMobileApp||
|bool SupportsMerchantMobileApp||
|bool SupportsNetworkMobileApp||
|Guid IndustryId||
|string IndustryDescription||
|bool SupportsOffline||
|string NetworkLogoExtension||

|Method|Parameters|Response|Description|
|--- |--- |--- |--- |
|GetNetworkAsync||NetworkDto|Get individual NetworkDto|
|GetNetworkAsync||NetworkDto|Get individual NetworkDto|

#### PaymentsMethodDto
|Data|Description|
|--- |--- |
|Guid Id||
|Guid NetworkId||
|string Code||
|string Description||
|decimal? Total||
|DateTime UpdateDate||

|Method|Parameters|Response|Description|
|--- |--- |--- |--- |
|GetPaymentsMethods|List Guid  paymentsMethodIds = null string code = null string description = null DateTime? updateDate = null int page = 1 int pageSize = 50 string orderField = "code" string orderType = "asc"|PaymentsMethodDto|Get list of the PaymentsMethodDto|
|GetPaymentsMethodsAsync|List Guid  paymentsMethodIds = null string code = null string description = null DateTime? updateDate = null int page = 1 int pageSize = 50 string orderField = "code" string orderType = "asc"|PaymentsMethodDto|Get list of the PaymentsMethodDto|
|GetPaymentsMethod|Guid id|PaymentsMethodDto|Get individual PaymentsMethodDto|
|GetPaymentsMethodAsync|Guid id|PaymentsMethodDto|Get individual PaymentsMethodDto|
|CreatePaymentsMethod|PaymentsMethodDto data|PaymentsMethodDto|Create PaymentsMethodDto|
|CreatePaymentsMethodAsync|PaymentsMethodDto data|PaymentsMethodDto|Create PaymentsMethodDto|
|UpdatePaymentsMethod|Guid id PaymentsMethodDto data|string|Update PaymentsMethodDto|
|UpdatePaymentsMethodAsync|Guid id PaymentsMethodDto data|string|Update PaymentsMethodDto|

#### ProgramDto
|Data|Description|
|--- |--- |
|bool SupportsDryProducts||
|string BINRange||
|decimal? GiftCardAmount||
|bool IsRechargeable||
|byte SupportsOffline||
|byte SupportsContingency||
|byte ApplyContractsSites||
|bool ValidateExpDate||
|byte BalanceMode||
|string Description||
|string CompanyName||
|Guid? CompanyId||
|string NetworkName||
|Guid NetworkId||
|string InternalCode||
|Guid Id||
|byte Type||
|ProgramRuleDto Rule||

|Method|Parameters|Response|Description|
|--- |--- |--- |--- |
|GetPrograms|List Guid programIds = null</br> string description = null</br> int page = 1</br> int pageSize = 50</br> string orderField = "name"</br> string orderType = "asc" string orderType = "asc"|List&lt;ProgramDto>|Get list of the ProgramDto|
|GetProgramsAsync|List Guid programIds = null</br> string description = null</br> int page = 1</br> int pageSize = 50</br> string orderField = "name"</br> string orderType = "asc" string orderType = "asc"|List&lt;ProgramDto>|Get list of the ProgramDto|
|GetProgram|Guid id|ProgramDto|Get individual ProgramDto|
|GetProgramAsync|Guid id|ProgramDto|Get individual ProgramDto|
|CreateProgram|ProgramDto data|ProgramDto|Create ProgramDto|
|CreateProgramAsync|ProgramDto data|ProgramDto|Create ProgramDto|
|UpdateProgram|Guid id ProgramDto data|string|Update ProgramDto|
|UpdateProgramAsync|Guid id ProgramDto data|string|Update ProgramDto|

#### RuleDto
|Data|Description|
|--- |--- |
|int? OdometerMaxVariation||
|bool EngineHoursReprompt||
|int? EngineHoursMinVariation||
|int? EngineHoursMaxVariation||
|bool DriverIdReprompt||
|bool DriverPINReprompt||
|bool TruckUnitNumberReprompt||
|bool TrailerNumberReprompt||
|decimal? ContingencyLimit||
|decimal? OfflineLimit||
|List SitesIds||
|byte Owner||
|List DaysTimeRuleType||
|string RuleTypeDescription||
|string RuleValues||
|Guid? ProgramId||
|string ProgramDescription||
|bool ExactDateTime||
|bool VehicleIdReprompt||
|bool SecondaryTrack||
|List FuelsIds||
|List Fuels||
|List Drivers||
|int? OdometerMinVariation||
|List Vehicles||
|bool OdometerReprompt||
|bool SecondaryTrackReprompt||
|Guid Id||
|Guid? NetworkId||
|string NetworkName||
|Guid? CompanyId||
|string CompanyName||
|Guid? MerchantId||
|string MerchantName||
|Guid? CompanyContractId||
|string ContractDescription||
|short? RuleType||
|string Description||
|byte? Periodicity||
|short? PeriodicityAmount||
|decimal? MoneyQuota||
|decimal? VolumeQuota||
|int? TimeFrom||
|int? TimeTo||
|int? DateFrom||
|int? DateTo||
|decimal? SecurityLimit||
|int? TransactionsQuantity||
|int? Retries||
|bool VehiclePINReprompt||
|bool MiscellaneousReprompt||
|List RuleFleetDto  Fleets||

|Method|Parameters|Response|Description|
|--- |--- |--- |--- |
|GetRules|string rule = null</br> short? ruleType = null</br> Guid? idVehicle = null</br> Guid? idDriver = null</br> Guid? idFleet = null</br> string customer = null</br> string company = null</br> string contract = null</br> int page = 1</br> int pageSize = 50</br> string orderField = "description"</br> string orderType = "asc"|List&lt;RuleDto>|Get list of the RuleDto|
|GetRulesAsync|string rule = null</br> short? ruleType = null</br> Guid? idVehicle = null</br> Guid? idDriver = null</br> Guid? idFleet = null</br> string customer = null</br> string company = null</br> string contract = null</br> int page = 1</br> int pageSize = 50</br> string orderField = "description"</br> string orderType = "asc"|List&lt;RuleDto>|Get list of the RuleDto|
|GetRule|Guid id|RuleDto|Get individual RuleDto|
|GetRuleAsync|Guid id|RuleDto|Get individual RuleDto|
|CreateRule|RuleDto data|RuleDto|Create RuleDto|
|CreateRuleAsync|RuleDto data|RuleDto|Create RuleDto|
|UpdateRule|Guid id RuleDto data|string|Update RuleDto|
|UpdateRuleAsync|Guid id RuleDto data|string|Update RuleDto|
|DeleteRule|Guid id|string|Get individual RuleDto|
|DeleteRuleAsync|Guid id|string|Get individual RuleDto|

#### ServiceFileEntryDto
|Data|Description|
|--- |--- |
|DateTime RecordDate||
|byte? ServiceFileTargetType||
|byte? TransactionType||
|int? EngineHours||
|int? Odometer||
|string FreeText||
|string StockKeepingUnitDescription||
|string ServiceEntryClass3Description||
|string ServiceEntryClass2Description||
|string ServiceEntryClass1Description||
|string ServiceEntryTypeGroupDescription||
|string ServiceEntryTypeDescription||
|string ServiceFileCode||
|string DriverDescription||
|string VehicleDescription||
|string NetworkName||
|Guid? IdStockKeepingUnit||
|Guid? IdServiceEntryClass3||
|Guid? IdServiceEntryClass2||
|Guid? IdServiceEntryClass1||
|Guid? IdLoyaltyTransaction||
|Guid? IdTransaction||
|Guid? IdServiceEntryTypeGroup||
|Guid? IdServiceEntryType||
|Guid? IdServiceFile||
|Guid? IdDriver||
|Guid? IdVehicle||
|Guid? IdNetwork||
|Guid Id||
|DateTime? EntryDate||
|DateTime? ExpirationDate||

|Method|Parameters|Response|Description|
|--- |--- |--- |--- |
|GetServiceFileEntries|List Guid  loyaltyPrograms = null List identifications = null List drivers = null List vehicles = null List groups = null List types = null List products = null string memberDate = null string dateFrom = null string dateTo = null int page = 1 int pageSize = 50|List&lt;ServiceFileEntryDto>|Get list of the ServiceFileEntryDto|
|GetServiceFileEntriesAsync|List Guid  loyaltyPrograms = null List identifications = null List drivers = null List vehicles = null List groups = null List types = null List products = null string memberDate = null string dateFrom = null string dateTo = null int page = 1 int pageSize = 50|List&lt;ServiceFileEntryDto>|Get list of the ServiceFileEntryDto|
|GetServiceFileEntry|Guid id|ServiceFileEntryDto|Get individual ServiceFileEntryDto|
|GetServiceFileEntryAsync|Guid id|ServiceFileEntryDto|Get individual ServiceFileEntryDto|
|CreateServiceFileEntry|ServiceFileEntryDto data|ServiceFileEntryDto|Create ServiceFileEntryDto|
|CreateServiceFileEntryAsync|ServiceFileEntryDto data|ServiceFileEntryDto|Create ServiceFileEntryDto|





### FMS Methods
<table>
     <thead>
        <tr> 
			<td>Method</td>
			<td>Parameters</td>
			<td>Description</td>
		</tr>
     </thead>
     <tbody>
        <tr>
          	<td>UploadNativeDeliveries</td>
            <td>TerminalCode (string), trama (List<FMSDeliveryData>), SystemModel (string), SystemVersion (string)</td>
            <td>loren impsum</td>
        </tr>
        <tr>
          	<td>UploadNativeDelivery</td>
            <td>TerminalCode (string), trama (FMSDeliveryData), SystemModel (string), SystemVersion (string)</td>
            <td>loren impsum</td>
        </tr>
        <tr>
          	<td>UploadNativeInventories</td>
            <td>TerminalCode (string), trama (List<FMSInventoryData>), SystemModel (string), SystemVersion (string)</td>
            <td>loren impsum</td>
        </tr>
        <tr>
          	<td>UploadNativeInventory</td>
            <td>TerminalCode (string), trama (FMSInventoryData), SystemModel (string), SystemVersion (string)</td>
            <td>loren impsum</td>
        </tr>
	</tbody>
</table>

### Interface Methods
<table>
     <thead>
        <tr> 
			<td>Method</td>
			<td>Parameters</td>
			<td>Description</td>
		</tr>
     </thead>
     <tbody>
        <tr>
          	<td>BalanceTransferContractToSubAccount</td>
            <td></td>
            <td>Transfers money from the contract to a sub account</td>
        </tr>
        <tr>
          	<td>BalanceTransferSubAccountToContract</td>
          	<td></td>
          	<td>Transfers money from the sub account to the contract</td>
        </tr>
        <tr>
          	<td>BalanceTransferSubAccountToSubAccount</td>
            <td></td>
            <td>Transfers money between sub accounts</td>
        </tr>
        <tr>
          	<td>BalanceTransferToContract</td>
            <td></td>
            <td>Transfers (deposit) money to a contract</td>
        </tr>
        <tr>
          	<td>BalanceTransferToSubAccount</td>
            <td></td>
            <td>Transfers (deposit) money to a sub account</td>
        </tr>
        <tr>
          	<td>BalanceWithdrawFromContract</td>
            <td></td>
            <td>Removes (Withdraw) money from a contract</td>
        </tr>
        <tr>
          	<td>BalanceWithdrawFromSubAccount</td>
            <td></td>
            <td>This method removes (Withdraw) money from a sub account</td>
        </tr>
        <tr>
          	<td>ContractBalanceDownload</td>
            <td></td>
            <td>This method downloads a contracts balances list</td>
        </tr>
		<tr>
          	<td>FastTrackDownload</td>	
            <td></td>
            <td>This method downloads a fast track list</td>
        </tr>
        <tr>
          	<td>GetDeliveries</td>
            <td></td>
            <td>This method downloads a deliveries list</td>
        </tr>
        <tr>
          	<td>GetExceptions</td>
            <td></td>
            <td>This method downloads a transaction exceptions list</td>
        </tr>
        <tr>
          	<td>GetInventories</td>
            <td></td>
            <td>This method downloads an inventories list</td>
        </tr>
        <tr>
          	<td>GetMovements</td>
            <td></td>
            <td>This method downloads current account movements</td>
        </tr>
        <tr>
          	<td>GetRetailBatchCloses</td>
            <td></td>
            <td>This method downloads retail batch closes</td>
        </tr>
        <tr>
          	<td>GetRetailTransactions</td>
            <td></td>
            <td>This method downloads retail transactions</td>
        </tr>
        <tr>
          	<td>GetStatements</td>
            <td></td>
            <td>This method downloads the statements</td>
        </tr>
        <tr>
          	<td>GetTransactions</td>
            <td></td>
            <td>This method downloads fleet transactions</td>
        </tr>
		<tr>
          	<td>GetTransactionsDisputes</td>
            <td></td>
            <td>This method downloads fleet transactions which are or were disputed</td>
        </tr>
        <tr>
          	<td>GetUncontrolledTransactions</td>
            <td></td>
            <td>This method downloads uncontrolled transactions</td>
        </tr>
		<tr>
          	<td>InsertFastTrackOrder</td>
            <td></td>
            <td>This method inserts fast tracks (trip orders)</td>
        </tr>
        <tr>
          	<td>InsertFastTrackOrder</td>
            <td></td>
            <td>This method inserts fast tracks (trip orders)</td>
        </tr>
        <tr>
          	<td>SubAccountBalanceDownload</td>
            <td></td>
            <td>This method downloads the balance of the sub accounts</td>
        </tr>
     </tbody>
</table>

### Loyalty Methods
<table>
     <thead>
        <tr> 
			<td>Method</td>
			<td>Parameters</td>
			<td>Description</td>
		</tr>
     </thead>
     <tbody>
        <tr>
          	<td>SendLoyaltyAccumulation</td>
            <td></td>
            <td>loren impsum</td>
        </tr>
        <tr>
          	<td>SendLoyaltyAccumulationAsync</td>
            <td></td>
            <td>loren impsum</td>
        </tr>
        <tr>
          	<td>SendLoyaltyBalanceInquiry</td>
            <td></td>
            <td>loren impsum</td>
        </tr>
        <tr>
          	<td>SendLoyaltyBalanceInquiryAsync</td>
            <td></td>
            <td>loren impsum</td>
        </tr>
	</tbody>
</table>

### Retail Methods
<table>
     <thead>
        <tr> 
			<td>Method</td>
			<td>Parameters</td>
			<td>Description</td>
		</tr>
     </thead>
     <tbody>
        <tr>
          	<td>SendRetailBatchClose</td>
            <td></td>
            <td>loren impsum</td>
        </tr>
        <tr>
          	<td>SendRetailBatchCloseAsync</td>
            <td></td>
            <td>loren impsum</td>
        </tr>
        <tr>
          	<td>SendSaleRecordsUpload</td>
            <td></td>
            <td>loren impsum</td>
        </tr>
        <tr>
          	<td>SendSaleRecordsUploadAsync</td>
            <td></td>
            <td>loren impsum</td>
        </tr>
	</tbody>
</table>

## Appendix A - Native Authorization Protocol Messages

Check this [document](AN-SDK-Reference.md) to have detailed information about each field in each message under the Native Authorization Protocol 
