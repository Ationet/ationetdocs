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
- [Download / Installation](#download-installation)
- [Operation Types](#operation-types)
  -  [Auth](#auth)
  -  [FMS](#fms)
  -  [Interface](#interface)
  -  [Loyalty](#loyalty)
  -  [Retail](#retail)
- [Consuming the SDK](#consuming-the-sdk)
  -  [Operation Types methods](#operation-types-methods)
	  -  [Auth Methods](#auth-methods)
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
</BR>
|Data|Description|
|--- |--- |
|string NetworkDateString||
|DateTime? NetworkDate||
|string NewData||
|string OriginalData||
|Guid? EntityId||
|string MerchantName||
|string CompanyName||
|string NetworkName||
|string UserName||
|Guid UserId||
|string OriginDescription||
|int? Origin||
|string ActionDescription||
|int Action||
|string SubCategoryDescription||
|int? SubCategory||
|string CategoryDescription||
|int Category||
|int Environment||
|Guid? MerchantId||
|Guid? CompanyId||
|Guid? NetworkId||
|Guid Id||
|DateTime RealDate||
|string RealDateString||

|Method|Parameters|Response|Description|
|--- |--- |--- |--- |
|GetLogs|List Guid  userIds List int  categories string dateFrom string dateTo = null Guid? idCompany = null int page = 1 int pageSize = 50 int? action = null int? subCategory = null string timeFrom = null string timeTo = null|AuditLogDto|Get list of the AuditLogDto|
|GetLogsAsync|List Guid  userIds List int  categories string dateFrom string dateTo = null Guid? idCompany = null int page = 1 int pageSize = 50 int? action = null int? subCategory = null string timeFrom = null string timeTo = null|AuditLogDto|Get list of the AuditLogDto|

</BR>
<table>
		<h4>CompanyDto</h4>
			<thead>
				<tr> 
					<td>Data</td>
					<td>Description</td>
				</tr>
			</thead>
			<tbody>
			<tr>
                <td>string Custom1</td>
                <td></td>
            </tr>
            <tr>
                <td>string Custom0</td>
                <td></td>
            </tr>
            <tr>
                <td>byte? DesactivationType</td>
                <td></td>
            </tr>
            <tr>
                <td>bool Active</td>
                <td></td>
            </tr>
            <tr>
                <td>string ContactPhone2</td>
                <td></td>
            </tr>
            <tr>
                <td>string ContactPhone1</td>
                <td></td>
            </tr>
            <tr>
                <td>string ContactEmail</td>
                <td></td>
            </tr>
            <tr>
                <td>string ContactName</td>
                <td></td>
            </tr>
            <tr>
                <td>DateTime UpdateDate</td>
                <td></td>
            </tr>
            <tr>
                <td>byte Type</td>
                <td></td>
            </tr>
            <tr>
                <td>DateTime CreationDate</td>
                <td></td>
            </tr>
            <tr>
                <td>string IndustryDescription</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid IndustryId</td>
                <td></td>
            </tr>
            <tr>
                <td>string Custom2</td>
                <td></td>
            </tr>
            <tr>
                <td>string TaxpayerCategoryDescription</td>
                <td></td>
            </tr>
            <tr>
                <td>string TaxPayerId</td>
                <td></td>
            </tr>
            <tr>
                <td>string City</td>
                <td></td>
            </tr>
            <tr>
                <td>string ZipCode</td>
                <td></td>
            </tr>
            <tr>
                <td>string StateDescription</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid StateId</td>
                <td></td>
            </tr>
            <tr>
                <td>string CountryDescription</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid CountryId</td>
                <td></td>
            </tr>
            <tr>
                <td>string Street2</td>
                <td></td>
            </tr>
            <tr>
                <td>string Street1</td>
                <td></td>
            </tr>
            <tr>
                <td>string Name</td>
                <td></td>
            </tr>
            <tr>
                <td>string Code</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid NetworkId</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid Id</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid TaxpayerCategoryId</td>
                <td></td>
            </tr>
            <tr>
                <td>string Custom3</td>
                <td></td>
            </tr>
			</tbody>
</table>
<table>
	 <thead>
		<tr> 
			<td>Method</td>
			<td>Parameters</td>
			<td>Response</td>
			<td>Description</td>
			
		</tr>
	 </thead>
	 <tbody>
		<tr>
			<td>GetCompanies</td>
			<td>List Guid  companyIds = null</br> string code = null</br> string name = null</br> string custom0 = null</br> string custom1 = null</br> string custom2 = null</br> string custom3 = null</br> DateTime? updateDate = null</br> int page = 1</br> int pageSize = 50</br> string orderField = "name"</br> string orderType = "asc"</td>
			<td>CompanyDto</td>
			<td>Get list of the CompanyDto</td>
		</tr>
		<tr>
			<td>GetCompaniesAsync</td>
			<td>List Guid  companyIds = null</br> string code = null</br> string name = null</br> string custom0 = null</br> string custom1 = null</br> string custom2 = null</br> string custom3 = null</br> DateTime? updateDate = null</br> int page = 1</br> int pageSize = 50</br> string orderField = "name"</br> string orderType = "asc"</td>
			<td>CompanyDto</td>
			<td>Get list of the CompanyDto</td>
		</tr>

		<tr>
			<td>GetCompany</td>
			<td>Guid id</td>
			<td>CompanyDto</td>
			<td>Get individual CompanyDto</td>
		</tr>
		<tr>
			<td>GetCompanyAsync</td>
			<td>Guid id</td>
			<td>CompanyDto</td>
			<td>Get individual CompanyDto</td>
		</tr>
		
		<tr>
			<td>CreateCompany</td>
			<td>CompanyDto data</td>
			<td>CompanyDto</td>
			<td>Create CompanyDto</td>
		</tr>
		<tr>
			<td>CreateCompanyAsync</td>
			<td>CompanyDto data</td>
			<td>CompanyDto</td>
			<td>Create CompanyDto</td>
		</tr>
	
		<tr>
			<td>UpdateCompany</td>
			<td>Guid id </br>CompanyDto data</td>
			<td>string</td>
			<td>Update CompanyDto</td>
		</tr>
		<tr>
			<td>UpdateCompanyAsync</td>
			<td>Guid id </br>CompanyDto data</td>
			<td>string</td>
			<td>Update CompanyDto</td>
		</tr>
	</tbody>
</table>
</BR>
<table>
		<h4>CompanyClassificationsConfigurationDto</h4>
			<thead>
				<tr> 
					<td>Data</td>
					<td>Description</td>
				</tr>
			</thead>
			<tbody>
				<tr> 
					<td>Guid IdCompany</td>
					<td>Identification of de Company</td>
				</tr>
				<tr> 
					<td>string Classification1Label</td>
					<td>classification 1 Label</td>
				</tr>
				<tr> 
					<td>string Classification2Label</td>
					<td>classification 2 Label</td>
				</tr>
				<tr> 
					<td>string Classification3Label</td>
					<td>classification 3 Label</td>
				</tr>
				<tr> 
					<td>string Classification4Label</td>
					<td>classification 4 Label</td>
				</tr>
				<tr> 
					<td>bool Classification1Enabled</td>
					<td>status for the use of the company</td>
				</tr>
				<tr> 
					<td>bool Classification2Enabled</td>
					<td>status for the use of the company</td>
				</tr>
				<tr> 
					<td>bool Classification3Enabled</td>
					<td>status for the use of the company</td>
				</tr>
				<tr> 
					<td>bool Classification4Enabled</td>
					<td>status for the use of the company</td>
				</tr>
			</tbody>
</table>
<table>
	
	 <thead>
		<tr> 
			<td>Method</td>
			<td>Parameters</td>
			<td>Response</td>
			<td>Description</td>

		</tr>
	 </thead>
	 <tbody>
		<tr>
			<td>GetCompaniesClassificationsConfiguration</td>
			<td></td>
			<td>CompanyClassificationsConfigurationDto</td>
			<td>Get the configuractions of the Classifications Companies</td>
		</tr>
		<tr>
			<td>GetCompaniesClassificationsConfigurationAsync</td>
			<td></td>
			<td>CompanyClassificationsConfigurationDto</td>
			<td>Get the configuractions of the Classifications Companies</td>
			
		</tr>
		<tr>
			<td>UpdateCompaniesClassificationsConfiguration</td>
			<td>CompanyClassificationsConfigurationDto data</td>
			<td>string</td>
			<td>Update configuractions of the Classifications Companies</td>
			
		</tr>
		<tr>
			<td>UpdateCompaniesClassificationsConfigurationAsync</td>
			<td>CompanyClassificationsConfigurationDto data</td>
			<td>string</td>
			<td>Update configuractions of the Classifications Companies</td>
		</tr>
	</tbody>
</table>
</BR>
<table>
		<h4>CompaniesGroupsMovementDto</h4>
			<thead>
				<tr> 
					<td>Data</td>
					<td>Description</td>
				</tr>
			</thead>
			<tbody>
				<tr> 
					<td>string TypeDescription</td>
					<td></td>
				</tr>
				<tr> 
					<td>Guid? IdOrigen</td>
					<td></td>
				</tr>
				<tr> 
					<td>byte Origen</td>
					<td></td>
				</tr>
				<tr> 
					<td>DateTime NetworkDate</td>
					<td></td>
				</tr>
				<tr> 
					<td>DateTime RealDate</td>
					<td></td>
				</tr>
				<tr> 
					<td>bool IsDebit</td>
					<td></td>
				</tr>
				<tr> 
					<td>string DisplayDateTimeString </td>
					<td></td>
				</tr>
				<tr> 
					<td>Guid? IdCurrencyCode</td>
					<td></td>
				</tr>
				<tr> 
					<td>string Description</td>
					<td></td>
				</tr>
				<tr> 
					<td>byte Type</td>
					<td></td>
				</tr>
				<tr> 
					<td>string CompaniesGroupDescription</td>
					<td></td>
				</tr>
				<tr> 
					<td>Guid IdCompaniesGroup</td>
					<td></td>
				</tr>
				<tr> 
					<td>Guid IdNetwork</td>
					<td></td>
				</tr>
				<tr> 
					<td>Guid Id</td>
					<td></td>
				</tr>
				<tr> 
					<td>decimal Amount</td>
					<td></td>
				</tr>
				<tr> 
					<td>string DisplayNetworkDateTimeString</td>
					<td></td>
				</tr>
			</tbody>
</table>
<table>
	
	 <thead>
		<tr> 
			<td>Method</td>
			<td>Parameters</td>
			<td>Response</td>
			<td>Description</td>
			
		</tr>
	 </thead>
	 <tbody>
		<tr>
			<td>GetCompaniesGroupsMovements</td>
			<td></td>
			<td>CompaniesGroupsMovementDto</td>
			<td>Get list of the CompaniesGroupsMovementDto</td>
		</tr>
		<tr>
			<td>GetCompaniesGroupsMovements</td>
			<td>Guid? companiesGroupId = null </br>string companiesGroupCode = null</br> string dateFrom = null</br> string dateTo = null</br> decimal? amountFrom = null</br> decimal? amountTo = null</br> byte? type = null</br> byte? origin = null</br> int page = 1</br> int pageSize = 50</br> string orderField = "networkDate"</br> string orderType = "asc"</td>
			<td>CompaniesGroupsMovementDto</td>
			<td>Get list of the CompaniesGroupsMovementDto</td>
		</tr>
		<tr>
			<td>GetCompaniesGroupsMovementsAsync</td>
			<td>Guid? companiesGroupId = null </br>string companiesGroupCode = null</br> string dateFrom = null</br> string dateTo = null</br> decimal? amountFrom = null</br> decimal? amountTo = null</br> byte? type = null</br> byte? origin = null</br> int page = 1</br> int pageSize = 50</br> string orderField = "networkDate"</br> string orderType = "asc"</td>
			<td>CompaniesGroupsMovementDto</td>
			<td>Get list of the CompaniesGroupsMovementDto</td>
		</tr>
		<tr>
			<td>GetCompaniesGroupsMovementAsync</td>
			<td>Guid id</td>
			<td>CompaniesGroupsMovementDto</td>
			<td>Get individual CompaniesGroupsMovementDto</td>
			
		</tr>
		<tr>
			<td>CreateCompaniesGroupsMovement</td>
			<td>CompanyClassificationsConfigurationDto data</td>
			<td>string</td>
			<td>Create a CompaniesGroupsMovement</td>
			
		</tr>
		<tr>
			<td>CreateCompaniesGroupsMovementAsync</td>
			<td>CompanyClassificationsConfigurationDto data</td>
			<td>string</td>
			<td>Create a CompaniesGroupsMovement</td>
		</tr>
	</tbody>
</table>
<table>
		<h4>CompanyClassificationDto</h4>
			<thead>
				<tr> 
					<td>Data</td>
					<td>Description</td>
				</tr>
			</thead>
			<tbody>
				<tr> 
					<td>Guid Id</td>
					<td></td>
				</tr>
				<tr> 
					<td>Guid IdCompany</td>
					<td></td>
				</tr>
				<tr> 
					<td>string Code</td>
					<td></td>
				</tr>
				<tr> 
					<td>string Description</td>
					<td></td>
				</tr>
			</tbody>
</table>
</BR>
<table>
	
	 <thead>
		<tr> 
			<td>Method</td>
			<td>Parameters</td>
			<td>Response</td>
			<td>Description</td>
			
		</tr>
	 </thead>
	 <tbody>
		<tr>
			<td>GetCompaniesClassifications1</td>
			<td>int page = 1</br> int pageSize = 50</br> string orderType = "asc"</td>
			<td>CompanyClassificationDto</td>
			<td>Get list of the CompanyClassificationDto</td>
		</tr>
		<tr>
			<td>GetCompaniesClassifications1Async</td>
			<td>int page = 1</br> int pageSize = 50</br> string orderType = "asc"</td>
			<td>CompanyClassificationDto</td>
			<td>Get list of the CompanyClassificationDto</td>
		</tr>
		<tr>
			<td>GetCompaniesClassifications2</td>
			<td>int page = 1</br> int pageSize = 50</br> string orderType = "asc"</td>
			<td>CompanyClassificationDto</td>
			<td>Get list of the CompanyClassificationDto</td>
		</tr>
		<tr>
			<td>GetCompaniesClassifications2Async</td>
			<td>int page = 1</br> int pageSize = 50</br> string orderType = "asc"</td>
			<td>CompanyClassificationDto</td>
			<td>Get list of the CompanyClassificationDto</td>
		</tr>
		<tr>
			<td>GetCompaniesClassifications3</td>
			<td>int page = 1</br> int pageSize = 50</br> string orderType = "asc"</td>
			<td>CompanyClassificationDto</td>
			<td>Get list of the CompanyClassificationDto</td>
		</tr>
		<tr>
			<td>GetCompaniesClassifications3Async</td>
			<td>int page = 1</br> int pageSize = 50</br> string orderType = "asc"</td>
			<td>CompanyClassificationDto</td>
			<td>Get list of the CompanyClassificationDto</td>
		</tr>
		<tr>
			<td>GetCompaniesClassifications4</td>
			<td>int page = 1</br> int pageSize = 50</br> string orderType = "asc"</td>
			<td>CompanyClassificationDto</td>
			<td>Get list of the CompanyClassificationDto</td>
		</tr>
		<tr>
			<td>GetCompaniesClassifications4Async</td>
			<td>int page = 1</br> int pageSize = 50</br> string orderType = "asc"</td>
			<td>CompanyClassificationDto</td>
			<td>Get list of the CompanyClassificationDto</td>
		</tr>
		<tr>
			<td>GetCompanyClassifications1</td>
			<td>Guid id</td>
			<td>CompanyClassificationDto</td>
			<td>Get individual CompanyClassificationDto</td>
		</tr>
		<tr>
			<td>GetCompanyClassifications1Async</td>
			<td>Guid id</td>
			<td>CompanyClassificationDto</td>
			<td>Get individual CompanyClassificationDto</td>
		</tr>
		<tr>
			<td>GetCompanyClassifications2</td>
			<td>Guid id</td>
			<td>CompanyClassificationDto</td>
			<td>Get individual CompanyClassificationDto</td>
		</tr>
		<tr>
			<td>GetCompanyClassifications2Async</td>
			<td>Guid id</td>
			<td>CompanyClassificationDto</td>
			<td>Get individual CompanyClassificationDto</td>
		</tr>
		<tr>
			<td>GetCompanyClassifications3</td>
			<td>Guid id</td>
			<td>CompanyClassificationDto</td>
			<td>Get individual CompanyClassificationDto</td>
		</tr>
		<tr>
			<td>GetCompanyClassifications3Async</td>
			<td>Guid id</td>
			<td>CompanyClassificationDto</td>
			<td>Get individual CompanyClassificationDto</td>
		</tr>
		<tr>
			<td>GetCompanyClassifications4</td>
			<td>Guid id</td>
			<td>CompanyClassificationDto</td>
			<td>Get individual CompanyClassificationDto</td>
		</tr>
		<tr>
			<td>GetCompanyClassifications4Async</td>
			<td>Guid id</td>
			<td>CompanyClassificationDto</td>
			<td>Get individual CompanyClassificationDto</td>
		</tr>
		<tr>
			<td>CreateCompaniesClassification1</td>
			<td>CompanyClassificationDto data</td>
			<td>CompanyClassificationDto</td>
			<td>Create CompanyClassificationDto</td>
		</tr>
		<tr>
			<td>CreateCompaniesClassification1Async</td>
			<td>CompanyClassificationDto data</td>
			<td>CompanyClassificationDto</td>
			<td>Create CompanyClassificationDto</td>
		</tr>
		<tr>
			<td>CreateCompaniesClassification2</td>
			<td>CompanyClassificationDto data</td>
			<td>CompanyClassificationDto</td>
			<td>Create CompanyClassificationDto</td>
		</tr>
		<tr>
			<td>CreateCompaniesClassification2Async</td>
			<td>CompanyClassificationDto data</td>
			<td>CompanyClassificationDto</td>
			<td>Create CompanyClassificationDto</td>
		</tr>
		<tr>
			<td>CreateCompaniesClassification3</td>
			<td>CompanyClassificationDto data</td>
			<td>CompanyClassificationDto</td>
			<td>Create CompanyClassificationDto</td>
		</tr>
		<tr>
			<td>CreateCompaniesClassification3Async</td>
			<td>CompanyClassificationDto data</td>
			<td>CompanyClassificationDto</td>
			<td>Create CompanyClassificationDto</td>
		</tr>
		<tr>
			<td>CreateCompaniesClassification4</td>
			<td>CompanyClassificationDto data</td>
			<td>CompanyClassificationDto</td>
			<td>Create CompanyClassificationDto</td>
		</tr>
		<tr>
			<td>CreateCompaniesClassification4Async</td>
			<td>CompanyClassificationDto data</td>
			<td>CompanyClassificationDto</td>
			<td>Create CompanyClassificationDto</td>
		</tr>
		<tr>
			<td>UpdateCompaniesClassification1</td>
			<td>CompanyClassificationDto data</td>
			<td>CompanyClassificationDto</td>
			<td>Update CompanyClassificationDto</td>
		</tr>
		<tr>
			<td>UpdateCompaniesClassification1Async</td>
			<td>CompanyClassificationDto data</td>
			<td>CompanyClassificationDto</td>
			<td>Update CompanyClassificationDto</td>
		</tr>
		<tr>
			<td>UpdateCompaniesClassification2</td>
			<td>CompanyClassificationDto data</td>
			<td>CompanyClassificationDto</td>
			<td>Update CompanyClassificationDto</td>
		</tr>
		<tr>
			<td>UpdateCompaniesClassification2Async</td>
			<td>CompanyClassificationDto data</td>
			<td>CompanyClassificationDto</td>
			<td>Update CompanyClassificationDto</td>
		</tr>
		<tr>
			<td>UpdateCompaniesClassification3</td>
			<td>CompanyClassificationDto data</td>
			<td>CompanyClassificationDto</td>
			<td>Update CompanyClassificationDto</td>
		</tr>
		<tr>
			<td>UpdateCompaniesClassification3Async</td>
			<td>CompanyClassificationDto data</td>
			<td>CompanyClassificationDto</td>
			<td>Update CompanyClassificationDto</td>
		</tr>
		<tr>
			<td>UpdateCompaniesClassification4</td>
			<td>CompanyClassificationDto data</td>
			<td>CompanyClassificationDto</td>
			<td>Update CompanyClassificationDto</td>
		</tr>
		<tr>
			<td>UpdateCompaniesClassification4Async</td>
			<td>CompanyClassificationDto data</td>
			<td>CompanyClassificationDto</td>
			<td>Update CompanyClassificationDto</td>
		</tr>
		<tr>
			<td>DeleteCompaniesClassification1</td>
			<td>Guid id</td>
			<td>string</td>
			<td>delete CompanyClassificationDto</td>
		</tr>
		<tr>
			<td>DeleteCompaniesClassification1Async</td>
			<td>Guid id</td>
			<td>string</td>
			<td>delete CompanyClassificationDto</td>
		</tr>
		<tr>
			<td>DeleteCompaniesClassification2</td>
			<td>Guid id</td>
			<td>string</td>
			<td>delete CompanyClassificationDto</td>
		</tr>
		<tr>
			<td>DeleteCompaniesClassification2Async</td>
			<td>Guid id</td>
			<td>string</td>
			<td>delete CompanyClassificationDto</td>
		</tr>
		<tr>
			<td>DeleteCompaniesClassification3</td>
			<td>Guid id</td>
			<td>string</td>
			<td>delete CompanyClassificationDto</td>
		</tr>
		<tr>
			<td>DeleteCompaniesClassification3Async</td>
			<td>Guid id</td>
			<td>string</td>
			<td>delete CompanyClassificationDto</td>
		</tr>
		<tr>
			<td>DeleteCompaniesClassification4</td>
			<td>Guid id</td>
			<td>string</td>
			<td>delete CompanyClassificationDto</td>
		</tr>
		<tr>
			<td>DeleteCompaniesClassification4Async</td>
			<td>Guid id</td>
			<td>string</td>
			<td>delete CompanyClassificationDto</td>
		</tr>
	</tbody>
</table>
<BR/>
<table>
		<h4>CompanyContractDto</h4>
			<thead>
				<tr> 
					<td>Data</td>
					<td>Description</td>
				</tr>
			</thead>
			<tbody>
				<tr> 
					<td>List CompanyContractProductDto  Products</td>
					<td></td>
				</tr>
				<tr> 
					<td>List CompanyContractSiteDto  Sites</td>
					<td></td>
				</tr>
				<tr> 
					<td>List CompanyContractFuelDto  Fuels</td>
					<td></td>
				</tr>
				<tr> 
					<td>CompanyContractBillingDto Billing</td>
					<td></td>
				</tr>
				<tr> 
					<td>decimal? ReactivationAmount</td>
					<td></td>
				</tr>
				<tr> 
					<td>byte? DeactivationType</td>
					<td></td>
				</tr>
				<tr> 
					<td>bool Active</td>
					<td></td>
				</tr>
				<tr> 
					<td>bool ValidateSites</td>
					<td></td>
				</tr>
				<tr> 
					<td>decimal? SecurityLimit</td>
					<td></td>
				</tr>
				<tr> 
					<td>decimal? Limit</td>
					<td></td>
				</tr>
				<tr> 
					<td>Guid? CurrencyId</td>
					<td></td>
				</tr>
				<tr> 
					<td>byte CurrentAccountMode</td>
					<td></td>
				</tr>
				<tr> 
					<td>List CompanyContractDiscountDto  Discounts</td>
					<td></td>
				</tr>
				<tr> 
					<td>short BalanceMode</td>
					<td></td>
				</tr>
				<tr> 
					<td>byte Periodicity</td>
					<td></td>
				</tr>
				<tr> 
					<td>string StartDate</td>
					<td></td>
				</tr>
				<tr> 
					<td>decimal Version</td>
					<td></td>
				</tr>
				<tr> 
					<td>string InternalCode</td>
					<td></td>
				</tr>
				<tr> 
					<td>byte Mode</td>
					<td></td>
				</tr>
				<tr> 
					<td>string Description</td>
					<td></td>
				</tr>
				<tr> 
					<td>string Code</td>
					<td></td>
				</tr>
				<tr> 
					<td>byte Type</td>
					<td></td>
				</tr>
				<tr> 
					<td>Guid NetworksCompanyId</td>
					<td></td>
				</tr>
				<tr> 
					<td>Guid CompanyId</td>
					<td></td>
				</tr>
				<tr> 
					<td>Guid NetworkId</td>
					<td></td>
				</tr>
				<tr> 
					<td>Guid Id</td>
					<td></td>
				</tr>
				<tr> 
					<td>short Duration</td>
					<td></td>
				</tr>
				<tr> 
					<td>bool MoneyBalance</td>
					<td></td>
				</tr>
			</tbody>
</table>
<table>
	 <thead>
		<tr> 
			<td>Method</td>
			<td>Parameters</td>
			<td>Response</td>
			<td>Description</td>
			
		</tr>
	 </thead>
	 <tbody>
		<tr>
			<td>GetContracts</td>
			<td>string companyCode = null</br> List Guid contractIds = null</br> string code = null</br> int page = 1</br> int pageSize = 50</br> string orderField = "description"</br> string orderType = "asc"</td>
			<td>CompanyContractDto</td>
			<td>Get list of the CompanyContractDto</td>
		</tr>
		<tr>
			<td>GetContractsAsync</td>
			<td>string companyCode = null</br> List Guid contractIds = null</br> string code = null</br> int page = 1</br> int pageSize = 50</br> string orderField = "description"</br> string orderType = "asc"</td>
			<td>CompanyContractDto</td>
			<td>Get list of the CompanyContractDto</td>
		</tr>

		<tr>
			<td>GetContract</td>
			<td>Guid id</td>
			<td>CompanyContractDto</td>
			<td>Get individual CompanyContractDto</td>
		</tr>
		<tr>
			<td>GetContractAsync</td>
			<td>Guid id</td>
			<td>CompanyContractDto</td>
			<td>Get individual CompanyContractDto</td>
		</tr>
		
		<tr>
			<td>CreateContract</td>
			<td>CompanyContractDto data</td>
			<td>CompanyContractDto</td>
			<td>Create CompanyContractDto</td>
		</tr>
		<tr>
			<td>CreateContractAsync</td>
			<td>CompanyContractDto data</td>
			<td>CompanyContractDto</td>
			<td>Create CompanyContractDto</td>
		</tr>
	
		<tr>
			<td>UpdateContract</td>
			<td>CompanyContractDto data</td>
			<td>CompanyContractDto</td>
			<td>Update CompanyContractDto</td>
		</tr>
		<tr>
			<td>UpdateContractAsync</td>
			<td>CompanyContractDto data</td>
			<td>CompanyContractDto</td>
			<td>Update CompanyContractDto</td>
		</tr>
	
		
	</tbody>
</table>
<BR/>
<table>
		<h4>CompanyContractOverLimitDto</h4>
			<thead>
				<tr> 
					<td>Data</td>
					<td>Description</td>
				</tr>
			</thead>
			<tbody>			
			<tr> 
				<td>Guid Id</td>
				<td></td>
			</tr>
			<tr> 
				<td>Guid IdCompanyContract</td>
				<td></td>
			</tr>
			<tr> 
				<td>string ContractName</td>
				<td></td>
			</tr>
			<tr> 
				<td>Guid IdCompany</td>
				<td></td>
			</tr>
			<tr> 
				<td>string CompanyName</td>
				<td></td>
			</tr>
			<tr> 
				<td>Guid IdNetwork</td>
				<td></td>
			</tr>
			<tr> 
				<td>string DateFrom</td>
				<td></td>
			</tr>
			<tr> 
				<td>string DateTo</td>
				<td></td>
			</tr>
			<tr> 
				<td>string CreationDate</td>
				<td></td>
			</tr>
			<tr> 
				<td>string CreationNetworkDate</td>
				<td></td>
			</tr>
			<tr> 
				<td>string NetworkTimeZone</td>
				<td></td>
			</tr>
			<tr> 
				<td>decimal Value</td>
				<td></td>
			</tr>
			<tr> 
				<td>byte Type</td>
				<td></td>
			</tr>
			<tr> 
				<td>byte State</td>
				<td></td>
			</tr>
			</tbody>
</table>
<table>
	 <thead>
		<tr> 
			<td>Method</td>
			<td>Parameters</td>
			<td>Response</td>
			<td>Description</td>
			
		</tr>
	 </thead>
	 <tbody>
		<tr>
			<td>GetCompanyContractOverLimits</td>
			<td>Guid? idCompany = null</br> Guid? idCompanyContract = null</br> string dateFrom = null</br> string dateTo = null</br> string creationDate = null</br> byte? filterType = null</br> int page = 1</br> int pageSize = 50</br> string orderField = "idFuelMaster"</br> string orderType = "asc"</td>
			<td>CompanyContractOverLimitDto</td>
			<td>Get list of the CompanyContractOverLimitDto</td>
		</tr>
		<tr>
			<td>GetCompanyContractOverLimitsAsync</td>
			<td>Guid? idCompany = null</br> Guid? idCompanyContract = null</br> string dateFrom = null</br> string dateTo = null</br> string creationDate = null</br> byte? filterType = null</br> int page = 1</br> int pageSize = 50</br> string orderField = "idFuelMaster"</br> string orderType = "asc"</td>
			<td>CompanyContractOverLimitDto</td>
			<td>Get list of the CompanyContractOverLimitDto</td>
		</tr>

		<tr>
			<td>GetCompanyContractOverLimit</td>
			<td>Guid id</td>
			<td>CompanyContractOverLimitDto</td>
			<td>Get individual CompanyContractOverLimitDto</td>
		</tr>
		<tr>
			<td>GetCompanyContractOverLimitAsync</td>
			<td>Guid id</td>
			<td>CompanyContractOverLimitDto</td>
			<td>Get individual CompanyContractOverLimitDto</td>
		</tr>
		
		<tr>
			<td>CreateCompanyContractOverLimit</td>
			<td>CompanyContractOverLimitDto data</td>
			<td>CompanyContractOverLimitDto</td>
			<td>Create CompanyContractOverLimitDto</td>
		</tr>
		<tr>
			<td>CreateCompanyContractOverLimitAsync</td>
			<td>CompanyContractOverLimitDto data</td>
			<td>CompanyContractOverLimitDto</td>
			<td>Create CompanyContractOverLimitDto</td>
		</tr>
	
		<tr>
			<td>UpdateCompanyContractOverLimit</td>
			<td>Guid id</br> CompanyContractOverLimitDto data</td>
			<td>CompanyContractOverLimitDto</td>
			<td>Update CompanyContractOverLimitDto</td>
		</tr>
		<tr>
			<td>UpdateCompanyContractOverLimitAsync</td>
			<td>Guid id</br> CompanyContractOverLimitDto data</td>
			<td>CompanyContractOverLimitDto</td>
			<td>Update CompanyContractOverLimitDto</td>
		</tr>
	</tbody>
</table>
<BR/>
<table>
		<h4>CompanyInvoiceDto</h4>
			<thead>
				<tr> 
					<td>Data</td>
					<td>Description</td>
				</tr>
			</thead>
			<tbody>
			<tr> 
				<td>Guid Id</td>
				<td></td>
			</tr>
			<tr> 
				<td>Guid IdNetwork</td>
				<td></td>
			</tr>
			<tr> 
				<td>Guid IdCompany</td>
				<td></td>
			</tr>
			<tr> 
				<td>string InvoiceNumber</td>
				<td></td>
			</tr>
			<tr> 
				<td>byte Type</td>
				<td></td>
			</tr>
			<tr> 
				<td>DateTime Date</td>
				<td></td>
			</tr>
			<tr> 
				<td>decimal Net</td>
				<td></td>
			</tr>
			<tr> 
				<td>decimal Taxes</td>
				<td></td>
			</tr>
			<tr> 
				<td>decimal? Total</td>
				<td></td>
			</tr>
			<tr> 
				<td>IEnumerable CompanyInvoiceDetailDto CompaniesInvoicesDetails</td>
				<td></td>
			</tr>
			<tr> 
				<td>IEnumerable TransactionDto  Transactions</td>
				<td></td>
			</tr>
			
			</tbody>
</table>
<table>
	 <thead>
		<tr> 
			<td>Method</td>
			<td>Parameters</td>
			<td>Response</td>
			<td>Description</td>
			
		</tr>
	 </thead>
	 <tbody>
		<tr>
			<td>GetInvoices</td>
			<td>string companyCode = null</br> List Guid companyIds = null</br> string invoiceNumber = null</br> byte? invoiceType = null</br> DateTime? dateFrom = null</br> DateTime? dateTo = null</br> int page = 1</br> int pageSize = 50</br> string orderField = "description"</br> string orderType = "asc"</td>
			<td>CompanyInvoiceDto</td>
			<td>Get list of the CompanyInvoiceDto</td>
		</tr>
		<tr>
			<td>GetInvoicesAsync</td>
			<td>string companyCode = null</br> List Guid companyIds = null</br> string invoiceNumber = null</br> byte? invoiceType = null</br> DateTime? dateFrom = null</br> DateTime? dateTo = null</br> int page = 1</br> int pageSize = 50</br> string orderField = "description"</br> string orderType = "asc"</td>
			<td>CompanyInvoiceDto</td>
			<td>Get list of the CompanyInvoiceDto</td>
		</tr>

		<tr>
			<td>GetInvoice</td>
			<td>Guid id</td>
			<td>CompanyInvoiceDto</td>
			<td>Get individual CompanyInvoiceDto</td>
		</tr>
		<tr>
			<td>GetInvoiceAsync</td>
			<td>Guid id</td>
			<td>CompanyInvoiceDto</td>
			<td>Get individual CompanyInvoiceDto</td>
		</tr>
		
		<tr>
			<td>CreateInvoice</td>
			<td>CompanyInvoiceDto data</td>
			<td>CompanyInvoiceDto</td>
			<td>Create CompanyInvoiceDto</td>
		</tr>
		<tr>
			<td>CreateInvoiceAsync</td>
			<td>CompanyInvoiceDto data</td>
			<td>CompanyInvoiceDto</td>
			<td>Create CompanyInvoiceDto</td>
		</tr>
	
		<tr>
			<td>UpdateInvoice</td>
			<td>CompanyInvoiceDto data</td>
			<td>string</td>
			<td>Update CompanyInvoiceDto</td>
		</tr>
		<tr>
			<td>UpdateInvoiceAsync</td>
			<td>CompanyInvoiceDto data</td>
			<td>string</td>
			<td>Update CompanyInvoiceDto</td>
		</tr>
	</tbody>
</table>
<BR/>
<table>
		<h4>CurrentAccountReportDto</h4>
			<thead>
				<tr> 
					<td>Data</td>
					<td>Description</td>
				</tr>
			</thead>
			<tbody>
			<tr> 
				<td>short? CompanyContractDuration</td><td></td></tr>
			<tr>
				<td>int? CompanyContractAccountsLimit</td>
				<td></td>
			</tr>
			<tr>
				<td>decimal? CompanyContractVersion</td>
				<td></td>
			</tr>
			<tr>
				<td>string ContractCode</td>
				<td></td>
			</tr>
			<tr>
				<td>decimal? Balance</td>
				<td></td>
			</tr>
			<tr>
				<td>bool? IsDebit</td>
				<td></td>
			</tr>
			<tr>
				<td>decimal? CreditLimit</td>
				<td></td>
			</tr>
			<tr>
				<td>decimal? OverLimit</td>
				<td></td>
			</tr>
			<tr>
				<td>Guid? StatementId</td>
				<td></td>
			</tr>
			<tr>
				<td>string MovementTypeDescription</td>
				<td></td>
			</tr>
			<tr>
				<td>string CompanyContractDescription</td>
				<td></td>
			</tr>
			<tr>
				<td>string VehicleDescription</td>
				<td></td>
			</tr>
			<tr>
				<td>string DriverDescription</td>
				<td></td>
			</tr>
			<tr>
				<td>string CompleteName</td>
				<td></td>
			</tr>
			<tr>
				<td>string FuelName</td>
				<td></td>
			</tr>
			<tr>
				<td>string ModeDescription</td>
				<td></td>
			</tr>
			<tr>
				<td>decimal? Debit</td>
				<td></td>
			</tr>
			<tr>
				<td>decimal? Credit</td>
				<td></td>
			</tr>
			<tr>
				<td>decimal BillingValue</td>
				<td></td>
			</tr>
			<tr>
				<td>bool Enable</td>
				<td></td>
			</tr>
			<tr>
				<td>string CompanyContractExpirationDate</td>
				<td></td>
			</tr>
			<tr>
				<td>string IdentificationsDescription</td>
				<td></td>
			</tr>
			<tr>
				<td>string LocalDateShortString</td>
				<td></td>
			</tr>
			<tr>
				<td>byte? CompanyContractPeriodicity</td>
				<td></td>
			</tr>
			<tr>
				<td>DateTime? CompanyContractStartDate</td>
				<td></td>
			</tr>
			<tr>
				<td>string SiteFuelName</td>
				<td></td>
			</tr>
			<tr>
				<td>string NetworkFuelName</td>
				<td></td>
			</tr>
			<tr>
				<td>Guid Id</td>
				<td></td>
			</tr>
			<tr>
				<td>Guid? IdMovement</td>
				<td></td>
			</tr>
			<tr>
				<td>Guid? IdCompanyContract</td>
				<td></td>
			</tr>
			<tr>
				<td>Guid? IdFuelMaster</td>
				<td></td>
			</tr>
			<tr>
				<td>Guid? IdSubAccount</td>
				<td></td>
			</tr>
			<tr>
				<td>string Description</td>
				<td></td>
			</tr>
			<tr>
				<td>decimal Amount</td>
				<td></td>
			</tr>
			<tr>
				<td>Guid? IdCurrencyCode</td>
				<td></td>
			</tr>
			<tr>
				<td>Guid? IdUserAtionet</td>
				<td></td>
			</tr>
			<tr>
				<td>byte MovementType</td>
				<td></td>
			</tr>
			<tr>
				<td>string NetworkName</td>
				<td></td>
			</tr>
			<tr>
				<td>string LocalTimeString</td>
				<td></td>
			</tr>
			<tr>
				<td>string CompanyName</td>
				<td></td>
			</tr>
			<tr>
				<td>string MovementIdOrigin</td>
				<td></td>
			</tr>
			<tr>
				<td>string MovementDescription</td>
				<td></td>
			</tr>
			<tr>
				<td>byte ContractMode</td>
				<td></td>
			</tr>
			<tr>
				<td>Guid? VehicleId</td>
				<td></td>
			</tr>
			<tr>
				<td>string VehiclePlate</td>
				<td></td>
			</tr>
			<tr>
				<td>string VehicleCode</td>
				<td></td>
			</tr>
			<tr>
				<td>Guid? DriverId</td>
				<td></td>
			</tr>
			<tr>
				<td>string DriverCode</td>
				<td></td>
			</tr>
			<tr>
				<td>string DriverFirstName</td>
				<td></td>
			</tr>
			<tr>
				<td>string DriverLastName</td>
				<td></td>
			</tr>
			<tr>
				<td>string FuelMasterName</td>
				<td></td>
			</tr>
			<tr>
				<td>DateTime MovementDate</td>
				<td></td>
			</tr>
			<tr>
				<td>string DisplayDateTimeString</td>
				<td></td>
			</tr>
			
			</tbody>
</table>
<table>
	 <thead>
		<tr> 
			<td>Method</td>
			<td>Parameters</td>
			<td>Response</td>
			<td>Description</td>
			
		</tr>
	 </thead>
	 <tbody>
		<tr>
			<td>GetContractsBalance</td>
			<td>Guid? idContract</br> 
			  string dateFrom = null</br> string dateTo = null</br>
			  string order = "desc"</br> int page = 1</br> int pageSize = 50</td>
			<td>CurrentAccountReportDto</td>
			<td>Get list of the CurrentAccountReportDto</td>
		</tr>
		<tr>
			<td>GetContractsBalanceAsync</td>
			<td>Guid? idContract</br> 
			  string dateFrom = null</br> string dateTo = null</br>
			  string order = "desc"</br> int page = 1</br> int pageSize = 50</td>
			<td>CurrentAccountReportDto</td>
			<td>Get list of the CurrentAccountReportDto</td>
		</tr>
		<tr>
			<td>GetContractsMovements</td>
			<td>Guid idContract</br> 
			  string dateFrom = null</br> string dateTo = null</br>
			  string order = "desc"</br> int page = 1</br> int pageSize = 50</td>
			<td>CurrentAccountReportDto</td>
			<td>Get list of the CurrentAccountReportDto</td>
		</tr>
		<tr>
			<td>GetContractsMovementsAsync</td>
			<td>Guid idContract</br> 
			  string dateFrom = null</br> string dateTo = null</br>
			  string order = "desc"</br> int page = 1</br> int pageSize = 50</td>
			<td>CurrentAccountReportDto</td>
			<td>Get list of the CurrentAccountReportDto</td>
		</tr>
		<tr>
			<td>GetSubAccountsBalance</td>
			<td> Guid? idContract=null</br>Guid? idSubAccount=null</br>
			  string dateFrom = null</br> string dateTo = null</br>
			  string order = "desc"</br> int page = 1</br> int pageSize = 50</td>
			<td>CurrentAccountReportDto</td>
			<td>Get list of the CurrentAccountReportDto</td>
		</tr>
		<tr>
			<td>GetSubAccountsBalanceAsync</td>
			<td> Guid? idContract=null</br>Guid? idSubAccount=null</br>
			  string dateFrom = null</br> string dateTo = null</br>
			  string order = "desc"</br> int page = 1</br> int pageSize = 50</td>
			<td>CurrentAccountReportDto</td>
			<td>Get list of the CurrentAccountReportDto</td>
		</tr>
				<tr>
			<td>GetSubAccountsMovements</td>
			<td> Guid? idContract=null</br>Guid? idSubAccount=null</br>
			  string dateFrom = null</br> string dateTo = null</br>
			  string order = "desc"</br> int page = 1</br> int pageSize = 50</td>
			<td>CurrentAccountReportDto</td>
			<td>Get list of the CurrentAccountReportDto</td>
		</tr>
		<tr>
			<td>GetSubAccountsMovementsAsync</td>
			<td> Guid? idContract=null</br>Guid? idSubAccount=null</br>
			  string dateFrom = null</br> string dateTo = null</br>
			  string order = "desc"</br> int page = 1</br> int pageSize = 50</td>
			<td>CurrentAccountReportDto</td>
			<td>Get list of the CurrentAccountReportDto</td>
		</tr>
	</tbody>
</table>
<BR/>
<table>
		<h4>CountryDto</h4>
			<thead>
				<tr> 
					<td>Data</td>
					<td>Description</td>
				</tr>
			</thead>
			<tbody>
			<tr> 
				<td>Guid Id</td>
				<td></td>
				</tr>
			<tr>
				<td>string Name</td>
				<td></td>
			</tr>
			
			</tbody>
</table>
<table>
	 <thead>
		<tr> 
			<td>Method</td>
			<td>Parameters</td>
			<td>Response</td>
			<td>Description</td>
			
		</tr>
	 </thead>
	 <tbody>
		<tr>
			<td>GetCountries</td>
			<td>int page = 1</br> int pageSize = 50</td>
			<td>CompanyInvoiceDto</td>
			<td>Get list of the CountryDto</td>
		</tr>
		<tr>
			<td>GetCountriesAsync</td>
			<td>int page = 1</br> int pageSize = 50</td>
			<td>CountryDto</td>
			<td>Get list of the CountryDto</td>
		</tr>
	</tbody>
</table>
<BR/>
<table>
		<h4>DriverDto</h4>
			<thead>
				<tr> 
					<td>Data</td>
					<td>Description</td>
				</tr>
			</thead>
			        <tbody>
            <tr>
                <td>string CompanyContractDuration </td>
                <td></td>
            </tr>
            <tr>
                <td>string Clasification2Description</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? Clasification3Id</td>
                <td></td>
            </tr>
            <tr>
                <td>string Clasification3Description</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? Clasification4Id</td>
                <td></td>
            </tr>
            <tr>
                <td>string Clasification4Description</td>
                <td></td>
            </tr>
            <tr>
                <td>List DriverRuleDto  Rules</td>
                <td></td>
            </tr>
            <tr>
                <td>List DriverVehicleDto2> Vehicles</td>
                <td></td>
            </tr>
            <tr>
                <td>List DriverIdentificationDto Identifications</td>
                <td></td>
            </tr>
            <tr>
                <td>List DriverLoyaltyIdentificationDto LoyaltyIdentifications</td>
                <td></td>
            </tr>
            <tr>
                <td>string Balance</td>
                <td></td>
            </tr>
            <tr>
                <td>string Consumption</td>
                <td></td>
            </tr>
            <tr>
                <td>string IdentificationsDescription</td>
                <td></td>
            </tr>
            <tr>
                <td>string LoyaltyProgramsDescription</td>
                <td></td>
            </tr>
            <tr>
                <td>string LoyaltyIdentificationsDescription</td>
                <td></td>
            </tr>
            <tr>
                <td>List DriverVehicleDto VehiclesDrivers</td>
                <td></td>
            </tr>
            <tr>
                <td>string Custom0</td>
                <td></td>
            </tr>
            <tr>
                <td>string Custom1</td>
                <td></td>
            </tr>
            <tr>
                <td>string Custom2</td>
                <td></td>
            </tr>
            <tr>
                <td>string Custom3</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? Clasification2Id</td>
                <td></td>
            </tr>
            <tr>
                <td>string Clasification1Description</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? Clasification1Id</td>
                <td></td>
            </tr>
            <tr>
                <td>string Email</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid Id</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid CompanyId</td>
                <td></td>
            </tr>
            <tr>
                <td>string CompanyName</td>
                <td></td>
            </tr>
            <tr>
                <td>string Code</td>
                <td></td>
            </tr>
            <tr>
                <td>string LastName</td>
                <td></td>
            </tr>
            <tr>
                <td>string FirstName</td>
                <td></td>
            </tr>
            <tr>
                <td>string CompleteName</td>
                <td></td>
            </tr>
            <tr>
                <td>string Birthdate</td>
                <td></td>
            </tr>
            <tr>
                <td>string LicenseNumber</td>
                <td></td>
            </tr>
            <tr>
                <td>decimal? AvaliableAmount</td>
                <td></td>
            </tr>
            <tr>
                <td>bool Enabled</td>
                <td></td>
            </tr>
            <tr>
                <td>string CountryName</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? StateId</td>
                <td></td>
            </tr>
            <tr>
                <td>string StateName</td>
                <td></td>
            </tr>
            <tr>
                <td>string City</td>
                <td></td>
            </tr>
            <tr>
                <td>string Street1</td>
                <td></td>
            </tr>
            <tr>
                <td>string Street2</td>
                <td></td>
            </tr>
            <tr>
                <td>string ZipCode</td>
                <td></td>
            </tr>
            <tr>
                <td>string PhoneNumber1</td>
                <td></td>
            </tr>
            <tr>
                <td>string PhoneNumber2</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? CountryId</td>
                <td></td>
            </tr>
            <tr>
                <td>decimal? AvaliableVolume</td>
                <td></td>
            </tr>
			</tbody>
</table>
<table>
	 <thead>
		<tr> 
			<td>Method</td>
			<td>Parameters</td>
			<td>Response</td>
			<td>Description</td>
			
		</tr>
	 </thead>
	 <tbody>
		<tr>
			<td>GetDrivers</td>
			<td>List Guid identificationIds = null</br> List Guid ruleIds = null</br> List Guid classification1Ids = null</br> List Guid classification2Ids = null</br> List Guid classification3Ids = null</br> List Guid classification4Ids = null</br> string code = null</br> string name = null</br> string custom0 = null</br> string custom1 = null</br> string custom2 = null</br> string custom3 = null</br> int page = 1</br> int pageSize = 50</br> string orderField = "code"</br> string orderType = "asc"</td>
			<td>DriverDto</td>
			<td>Get list of the DriverDto</td>
		</tr>
		<tr>
			<td>GetDriversAsync</td>
			<td>List Guid identificationIds = null</br> List Guid ruleIds = null</br> List Guid classification1Ids = null</br> List Guid classification2Ids = null</br> List Guid classification3Ids = null</br> List Guid classification4Ids = null</br> string code = null</br> string name = null</br> string custom0 = null</br> string custom1 = null</br> string custom2 = null</br> string custom3 = null</br> int page = 1</br> int pageSize = 50</br> string orderField = "code"</br> string orderType = "asc"</td>
			<td>DriverDto</td>
			<td>Get list of the DriverDto</td>
		</tr>

		<tr>
			<td>GetDriver</td>
			<td>Guid id</td>
			<td>DriverDto</td>
			<td>Get individual DriverDto</td>
		</tr>
		<tr>
			<td>GetDriverAsync</td>
			<td>Guid id</td>
			<td>DriverDto</td>
			<td>Get individual DriverDto</td>
		</tr>
		
		<tr>
			<td>CreateDriver</td>
			<td>DriverDto data</td>
			<td>DriverDto</td>
			<td>Create DriverDto</td>
		</tr>
		<tr>
			<td>CreateDriverAsync</td>
			<td>DriverDto data</td>
			<td>DriverDto</td>
			<td>Create DriverDto</td>
		</tr>
	
		<tr>
			<td>UpdateDriver</td>
			<td>Guid id </br>DriverDto data</td>
			<td>string</td>
			<td>Update DriverDto</td>
		</tr>
		<tr>
			<td>UpdateDriverAsync</td>
			<td>Guid id </br>DriverDto data</td>
			<td>string</td>
			<td>Update DriverDto</td>
		</tr>
	</tbody>
</table>
<BR/>
<table>
		<h4>FleetDto</h4>
			<thead>
				<tr> 
					<td>Data</td>
					<td>Description</td>
				</tr>
			</thead>
			<tbody>
            <tr>
                <td>string Clasification4Description</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? IdClasification4</td>
                <td></td>
            </tr>
            <tr>
                <td>string Clasification3Description</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? IdClasification3</td>
                <td></td>
            </tr>
            <tr>
                <td>string Clasification2Description</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? IdClasification2</td>
                <td></td>
            </tr>
            <tr>
                <td>string Clasification1Description</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? IdClasification1</td>
                <td></td>
            </tr>
            <tr>
                <td>string Code</td>
                <td></td>
            </tr>
            <tr>
                <td>string City</td>
                <td></td>
            </tr>
            <tr>
                <td>string StateDescription</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? IdState</td>
                <td></td>
            </tr>
            <tr>
                <td>string CountryDescriptiion</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? IdCountry</td>
                <td></td>
            </tr>
            <tr>
                <td>string Streep2</td>
                <td></td>
            </tr>
            <tr>
                <td>string Street1</td>
                <td></td>
            </tr>
            <tr>
                <td>string Name</td>
                <td></td>
            </tr>
            <tr>
                <td>string CompanyDescription</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid IdCompany</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid Id</td>
                <td></td>
            </tr>
            <tr>
                <td>List EntityRuleDto  Rules</td>
                <td></td>
            </tr>
			</tbody>
</table>
<table>
	 <thead>
		<tr> 
			<td>Method</td>
			<td>Parameters</td>
			<td>Response</td>
			<td>Description</td>
			
		</tr>
	 </thead>
	 <tbody>
		<tr>
			<td>GetFleets</td>
			<td>string code = null</br> string name = null</br> int page = 1</br> int pageSize = 50</br> string orderField = "name"</br> string orderType = "asc"</td>
			<td>FleetDto</td>
			<td>Get list of the FleetDto</td>
		</tr>
		<tr>
			<td>GetFleetsAsync</td>
			<td>string code = null</br> string name = null</br> int page = 1</br> int pageSize = 50</br> string orderField = "name"</br> string orderType = "asc"</td>
			<td>FleetDto</td>
			<td>Get list of the FleetDto</td>
		</tr>

		<tr>
			<td>GetFleet</td>
			<td>Guid id</td>
			<td>FleetDto</td>
			<td>Get individual FleetDto</td>
		</tr>
		<tr>
			<td>GetFleetAsync</td>
			<td>Guid id</td>
			<td>FleetDto</td>
			<td>Get individual FleetDto</td>
		</tr>
		
		<tr>
			<td>CreateFleet</td>
			<td>FleetDto data</td>
			<td>FleetDto</td>
			<td>Create FleetDto</td>
		</tr>
		<tr>
			<td>CreateFleetAsync</td>
			<td>FleetDto data</td>
			<td>FleetDto</td>
			<td>Create FleetDto</td>
		</tr>
	
		<tr>
			<td>UpdateFleet</td>
			<td>Guid id </br>FleetDto data</td>
			<td>string</td>
			<td>Update FleetDto</td>
		</tr>
		<tr>
			<td>UpdateFleetAsync</td>
			<td>Guid id </br>FleetDto data</td>
			<td>string</td>
			<td>Update FleetDto</td>
		</tr>
	</tbody>
</table>
<BR/>
<table>
		<h4>FuelDto</h4>
			<thead>
				<tr> 
					<td>Data</td>
					<td>Description</td>
				</tr>
			</thead>
			<tbody>
            <tr>
                <td>string CodeBrandFuelMasterDescription</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid Id</td>
                <td></td>
            </tr>
			<tr>
                <td>Guid MerchantId</td>
                <td></td>
            </tr>
            <tr>
                <td>string MerchantName</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid SiteId</td>
                <td></td>
            </tr>
            <tr>
                <td>string SiteShortName</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid FuelsMasterId</td>
                <td></td>
            </tr>
            <tr>
                <td>string FuelMasterDescription</td>
                <td></td>
            </tr>
            <tr>
                <td>string BrandFuelMasterDescription</td>
                <td></td>
            </tr>
            <tr>
                <td>string Code</td>
                <td></td>
            </tr>
			</tbody>
</table>
<table>
	 <thead>
		<tr> 
			<td>Method</td>
			<td>Parameters</td>
			<td>Response</td>
			<td>Description</td>
			
		</tr>
	 </thead>
	 <tbody>
		<tr>
			<td>GetFuels</td>
			<td>int page = 1</br> int pageSize = 50</br> string orderField = "code"</br> string orderType = "asc"</td>
			<td>FuelDto</td>
			<td>Get list of the FuelDto</td>
		</tr>
		<tr>
			<td>GetFuelsAsync</td>
			<td>int page = 1</br> int pageSize = 50</br> string orderField = "code"</br> string orderType = "asc"</td>
			<td>FuelDto</td>
			<td>Get list of the FuelDto</td>
		</tr>

		<tr>
			<td>GetFuel</td>
			<td>Guid id</td>
			<td>FuelDto</td>
			<td>Get individual FuelDto</td>
		</tr>
		<tr>
			<td>GetFuelAsync</td>
			<td>Guid id</td>
			<td>FuelDto</td>
			<td>Get individual FuelDto</td>
		</tr>
		
		<tr>
			<td>CreateFuel</td>
			<td>FuelDto data</td>
			<td>FuelDto</td>
			<td>Create FuelDto</td>
		</tr>
		<tr>
			<td>CreateFuelAsync</td>
			<td>FuelDto data</td>
			<td>FuelDto</td>
			<td>Create FuelDto</td>
		</tr>
	
		<tr>
			<td>UpdateFuel</td>
			<td>Guid id </br>FuelDto data</td>
			<td>string</td>
			<td>Update FuelDto</td>
		</tr>
		<tr>
			<td>UpdateFuelAsync</td>
			<td>Guid id </br>FuelDto data</td>
			<td>string</td>
			<td>Update FuelDto</td>
		</tr>
	</tbody>
</table>
<BR/>
<table>
		<h4>FuelsMasterDto</h4>
			<thead>
				<tr> 
					<td>Data</td>
					<td>Description</td>
				</tr>
			</thead>
			<tbody>
			 <tr>
                <td>Guid Id</td>
                <td></td>
            </tr>
            <tr>
                <td>short? Type</td>
                <td></td>
            </tr> 
			<tr>
                <td>string Code</td>
                <td></td>
            </tr>
            <tr>
                <td>string Description</td>
                <td></td>
            </tr>
            <tr>
                <td>byte? ContingencyCode</td>
                <td></td>
            </tr>
           
			</tbody>
</table>
<table>
	 <thead>
		<tr> 
			<td>Method</td>
			<td>Parameters</td>
			<td>Response</td>
			<td>Description</td>
			
		</tr>
	 </thead>
	 <tbody>
		<tr>
			<td>GetFuelsMasters</td>
			<td>int page = 1</br> int pageSize = 50</br> string orderField = "code"</br> string orderType = "asc"</td>
			<td>FuelsMasterDto</td>
			<td>Get list of the FuelsMasterDto</td>
		</tr>
		<tr>
			<td>GetFuelsMastersAsync</td>
			<td>int page = 1</br> int pageSize = 50</br> string orderField = "code"</br> string orderType = "asc"</td>
			<td>FuelsMasterDto</td>
			<td>Get list of the FuelsMasterDto</td>
		</tr>

		<tr>
			<td>GetFuelsMaster</td>
			<td>Guid id</td>
			<td>FuelsMasterDto</td>
			<td>Get individual FuelsMasterDto</td>
		</tr>
		<tr>
			<td>GetFuelsMasterAsync</td>
			<td>Guid id</td>
			<td>FuelsMasterDto</td>
			<td>Get individual FuelsMasterDto</td>
		</tr>
	</tbody>
</table>
<BR/>
<table>
		<h4>GiftCardClientDto</h4>
			<thead>
				<tr> 
					<td>Data</td>
					<td>Description</td>
				</tr>
			</thead>
			<tbody>
            <tr>
                <td>string PIN</td>
                <td></td>
            </tr>
            <tr>
                <td>bool RequiresPIN</td>
                <td></td>
            </tr>
            <tr>
                <td>bool IdentificationActive</td>
                <td></td>
            </tr>
            <tr>
                <td>string TypeModelDescription</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid TypeModelId</td>
                <td></td>
            </tr>
            <tr>
                <td>short Type</td>
                <td></td>
            </tr>
            <tr>
                <td>int RequestOrder</td>
                <td></td>
            </tr>
            <tr>
                <td>DateTime? RequestOrderDate</td>
                <td></td>
            </tr>
            <tr>
                <td>byte GiftCardState</td>
                <td></td>
            </tr>
            <tr>
                <td>DateTime CreationDate</td>
                <td></td>
            </tr>
            <tr>
                <td>int? PINDigits</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? GiftCardRequestOrderId</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid GiftCardProgramValueId</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid GiftCardDriverId</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid GiftCardSubAccountId</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid GiftCardIdentificationId</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid GiftCardProgramId</td>
                <td></td>
            </tr>
            <tr>
                <td>string IdentificationLabel</td>
                <td></td>
            </tr>
            <tr>
                <td>string IdentificationTrackNumber</td>
                <td></td>
            </tr>
            <tr>
                <td>decimal? Balance</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid NetworkId</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid Id</td>
                <td></td>
            </tr>
            <tr>
                <td>string GiftCardProgramName</td>
                <td></td>
            </tr>
            <tr>
                <td>string PAN</td>
                <td></td>
            </tr>
			</tbody>
</table>
<table>
	 <thead>
		<tr> 
			<td>Method</td>
			<td>Parameters</td>
			<td>Response</td>
			<td>Description</td>
			
		</tr>
	 </thead>
	 <tbody>
		<tr>
			<td>GetGiftCardClients</td>
			<td>Guid? programId = null</br> byte? cardState = null</br> DateTime? CreatedFrom = null</br> DateTime? CreatedTo = null</br> decimal? BalanceFrom = null</br> decimal? BalanceTo = null</br> bool? active = null</br> int page = 1</br> int pageSize = 50</br> string orderField = "label"</br> string orderType = "asc"</br> string pan = ""</td>
			<td>GiftCardClientDto</td>
			<td>Get list of the GiftCardClientDto</td>
		</tr>
		<tr>
			<td>GetGiftCardClientsAsync</td>
			<td>Guid? programId = null</br> byte? cardState = null</br> DateTime? CreatedFrom = null</br> DateTime? CreatedTo = null</br> decimal? BalanceFrom = null</br> decimal? BalanceTo = null</br> bool? active = null</br> int page = 1</br> int pageSize = 50</br> string orderField = "label"</br> string orderType = "asc"</br> string pan = ""</td>
			<td>GiftCardClientDto</td>
			<td>Get list of the GiftCardClientDto</td>
		</tr>

		<tr>
			<td>GetGiftCardClient</td>
			<td>Guid id</td>
			<td>GiftCardClientDto</td>
			<td>Get individual GiftCardClientDto</td>
		</tr>
		<tr>
			<td>GetGiftCardClientAsync</td>
			<td>Guid id</td>
			<td>GiftCardClientDto</td>
			<td>Get individual GiftCardClientDto</td>
		</tr>
		
		<tr>
			<td>CreateGiftCardClient</td>
			<td>GiftCardClientDto data</td>
			<td>GiftCardClientDto</td>
			<td>Create GiftCardClientDto</td>
		</tr>
		<tr>
			<td>CreateGiftCardClientAsync</td>
			<td>GiftCardClientDto data</td>
			<td>GiftCardClientDto</td>
			<td>Create GiftCardClientDto</td>
		</tr>
	
		<tr>
			<td>UpdateGiftCardClient</td>
			<td>GiftCardClientDto data</td>
			<td>string</td>
			<td>Update GiftCardClientDto</td>
		</tr>
		<tr>
			<td>UpdateGiftCardClientAsync</td>
			<td>GiftCardClientDto data</td>
			<td>string</td>
			<td>Update GiftCardClientDto</td>
		</tr>
	</tbody>
</table>
<BR/>
<table>
		<h4>GiftCardProgramDto</h4>
			<thead>
				<tr> 
					<td>Data</td>
					<td>Description</td>
				</tr>
			</thead>
			<tbody>
            <tr>
                <td>List GiftCardProgramValueDto  Values</td>
                <td></td>
            </tr>
            <tr>
                <td>List GiftCardProgramSiteDto  Sites</td>
                <td></td>
            </tr>
            <tr>
                <td>List GiftCardProgramFuelDto  Fuels</td>
                <td></td>
            </tr>
            <tr>
                <td>List GiftCardProgramDiscountDto  Discounts</td>
                <td></td>
            </tr>
            <tr>
                <td>string BINRange</td>
                <td></td>
            </tr>
            <tr>
                <td>short? CardDuration</td>
                <td></td>
            </tr>
            <tr>
                <td>byte? CardPeriodicity</td>
                <td></td>
            </tr>
            <tr>
                <td>bool ActiveCards</td>
                <td></td>
            </tr>
            <tr>
                <td>bool ValidateSites</td>
                <td></td>
            </tr>
            <tr>
                <td>string StartDate</td>
                <td></td>
            </tr>
            <tr>
                <td>short Duration</td>
                <td></td>
            </tr>
            <tr>
                <td>byte Periodicity</td>
                <td></td>
            </tr>
            <tr>
                <td>byte CurrentAccountMode</td>
                <td></td>
            </tr>
            <tr>
                <td>bool Rechargable</td>
                <td></td>
            </tr>
            <tr>
                <td>bool SingleUse</td>
                <td></td>
            </tr>
            <tr>
                <td>string Description</td>
                <td></td>
            </tr>
            <tr>
                <td>string Name</td>
                <td></td>
            </tr>
            <tr>
                <td>string Code</td>
                <td></td>
            </tr>
            <tr>
                <td>string NetworkName</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid NetworkId</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid Id</td>
                <td></td>
            </tr>
            <tr>
                <td>GiftCardProgramIdentificationTypeModelDto IdentificationsTypesModel</td>
                <td></td>
            </tr>
            <tr>
                <td>GiftCardProgramRuleDto Rule</td>
                <td></td>
            </tr>
			</tbody>
</table>
<table>
	 <thead>
		<tr> 
			<td>Method</td>
			<td>Parameters</td>
			<td>Response</td>
			<td>Description</td>
			
		</tr>
	 </thead>
	 <tbody>
		<tr>
			<td>GetGiftCardPrograms</td>
			<td>Guid? NetworkId</br> Guid? IdSite</br> string name = null</br> int page = 1</br> int pageSize = 50</br> string orderField = "label"</br> string orderType = "asc"</td>
			<td>GiftCardProgramDto</td>
			<td>Get list of the GiftCardProgramDto</td>
		</tr>
		<tr>
			<td>GetGiftCardProgramsAsync</td>
			<td>Guid? NetworkId</br> Guid? IdSite</br> string name = null</br> int page = 1</br> int pageSize = 50</br> string orderField = "label"</br> string orderType = "asc"</td>
			<td>GiftCardProgramDto</td>
			<td>Get list of the GiftCardProgramDto</td>
		</tr>

		<tr>
			<td>GetGiftCardProgram</td>
			<td>Guid id</td>
			<td>GiftCardProgramDto</td>
			<td>Get individual GiftCardProgramDto</td>
		</tr>
		<tr>
			<td>GetGiftCardProgramAsync</td>
			<td>Guid id</td>
			<td>GiftCardProgramDto</td>
			<td>Get individual GiftCardProgramDto</td>
		</tr>
		
		<tr>
			<td>CreateGiftCardProgram</td>
			<td>GiftCardProgramDto data</td>
			<td>GiftCardProgramDto</td>
			<td>Create GiftCardProgramDto</td>
		</tr>
		<tr>
			<td>CreateGiftCardProgramAsync</td>
			<td>GiftCardProgramDto data</td>
			<td>GiftCardProgramDto</td>
			<td>Create GiftCardProgramDto</td>
		</tr>
	
		<tr>
			<td>UpdateGiftCardProgram</td>
			<td>Guid id </br>GiftCardProgramDto data</td>
			<td>string</td>
			<td>Update GiftCardProgramDto</td>
		</tr>
		<tr>
			<td>UpdateGiftCardProgramAsync</td>
			<td>Guid id </br>GiftCardProgramDto data</td>
			<td>string</td>
			<td>Update GiftCardProgramDto</td>
		</tr>
	</tbody>
</table>
<BR/>
<table>
		<h4>IdentificationDto</h4>
			<thead>
				<tr> 
					<td>Data</td>
					<td>Description</td>
				</tr>
			</thead>
			<tbody>
            <tr>
                <td>string SubAccountDescription</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? DriverId</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? VehicleId</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? ProgramId</td>
                <td></td>
            </tr>
            <tr>
                <td>string ProgramDescription</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? LoyaltyProgramId</td>
                <td></td>
            </tr>
            <tr>
                <td>string LoyaltyProgramDescription</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? ContractId</td>
                <td></td>
            </tr>
            <tr>
                <td>string ContractDescription</td>
                <td></td>
            </tr>
            <tr>
                <td>bool RequiresPINChange</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? IdCompany</td>
                <td></td>
            </tr>
            <tr>
                <td>string CompanyName</td>
                <td></td>
            </tr>
            <tr>
                <td>string DriverCode</td>
                <td></td>
            </tr>
            <tr>
                <td>string DriverFirstName</td>
                <td></td>
            </tr>
            <tr>
                <td>string DriverLastName</td>
                <td></td>
            </tr>
            <tr>
                <td>string VehicleCode</td>
                <td></td>
            </tr>
            <tr>
                <td>string VehiclePlate</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? SubAccountId</td>
                <td></td>
            </tr>
            <tr>
                <td>string DriverDescription { get; }
			 </tr>
            <tr>
                <td>string PIN</td>
                <td></td>
            </tr>
            <tr>
                <td>string ExpirationDateShort</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid NetworkId</td>
                <td></td>
            </tr>
            <tr>
                <td>string NetworkName</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid Id</td>
                <td></td>
            </tr>
            <tr>
                <td>byte UseType</td>
                <td></td>
            </tr>
            <tr>
                <td>short? Type</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid TypeModelId</td>
                <td></td>
            </tr>
            <tr>
                <td>string TypeModelDescription</td>
                <td></td>
            </tr>
            <tr>
                <td>string Label</td>
                <td></td>
            </tr>
            <tr>
                <td>string TrackNumber</td>
                <td></td>
            </tr>
            <tr>
                <td>string PAN</td>
                <td></td>
            </tr>
            <tr>
                <td>byte State</td>
                <td></td>
            </tr>
            <tr>
                <td>bool Active</td>
                <td></td>
            </tr>
            <tr>
                <td>string CreationDate</td>
                <td></td>
            </tr>
            <tr>
                <td>string UpdateDate</td>
                <td></td>
            </tr>
            <tr>
                <td>string AssignmentDate</td>
                <td></td>
            </tr>
            <tr>
                <td>string ExpirationDate</td>
                <td></td>
            </tr>
            <tr>
                <td>string AssignmentDateShort</td>
                <td></td>
            </tr>
            <tr>
                <td>int? RequestOrder</td>
                <td></td>
            </tr>
            <tr>
                <td>string VehicleDescription</td>
                <td></td>
            </tr>
			</tbody>
</table>
<table>
	 <thead>
		<tr> 
			<td>Method</td>
			<td>Parameters</td>
			<td>Response</td>
			<td>Description</td>
			
		</tr>
	 </thead>
	 <tbody>
		<tr>
			<td>GetIdentifications</td>
			<td>List Guid  contractIds = null</br> string label = null</br> Guid? vehicle = null</br> Guid? driver = null</br> byte? type = null</br> Guid? model = null</br> Guid? program = null</br> byte? status = null</br> byte? active = null</br> string pan = null</br> int page = 1</br>int pageSize = 50</br> string orderField = "label"</br> string orderType = "asc"</td>
			<td>IdentificationDto</td>
			<td>Get list of the IdentificationDto</td>
		</tr>
		<tr>
			<td>GetIdentificationsAsync</td>
			<td>List Guid  contractIds = null</br> string label = null</br> Guid? vehicle = null</br> Guid? driver = null</br> byte? type = null</br> Guid? model = null</br> Guid? program = null</br> byte? status = null</br> byte? active = null</br> string pan = null</br> int page = 1</br>int pageSize = 50</br> string orderField = "label"</br> string orderType = "asc"</td>
			<td>IdentificationDto</td>
			<td>Get list of the IdentificationDto</td>
		</tr>

		<tr>
			<td>GetIdentification</td>
			<td>Guid id</td>
			<td>IdentificationDto</td>
			<td>Get individual IdentificationDto</td>
		</tr>
		<tr>
			<td>GetIdentificationAsync</td>
			<td>Guid id</td>
			<td>IdentificationDto</td>
			<td>Get individual IdentificationDto</td>
		</tr>
		
		<tr>
			<td>CreateIdentification</td>
			<td>IdentificationDto data</td>
			<td>IdentificationDto</td>
			<td>Create IdentificationDto</td>
		</tr>
		<tr>
			<td>CreateIdentificationAsync</td>
			<td>IdentificationDto data</td>
			<td>IdentificationDto</td>
			<td>Create IdentificationDto</td>
		</tr>
	
		<tr>
			<td>UpdateIdentification</td>
			<td>Guid id </br>IdentificationDto data</td>
			<td>string</td>
			<td>Update IdentificationDto</td>
		</tr>
		<tr>
			<td>UpdateIdentificationAsync</td>
			<td>Guid id </br>IdentificationDto data</td>
			<td>string</td>
			<td>Update IdentificationDto</td>
		</tr>
	</tbody>
</table>
<BR/>
<table>
		<h4>IdentificationDto</h4>
			<thead>
				<tr> 
					<td>Data</td>
					<td>Description</td>
				</tr>
			</thead>
			<tbody>
            <tr>
                <td>Guid Id</td>
                <td></td>
            </tr>
            <tr>
                <td>string PIN</td>
                <td></td>
            </tr>
            
			</tbody>
</table>
<table>
	 <thead>
		<tr> 
			<td>Method</td>
			<td>Parameters</td>
			<td>Response</td>
			<td>Description</td>
			
		</tr>
	 </thead>
	 <tbody>
		
		<tr>
			<td>UpdateIdentificationChangePin</td>
			<td>Guid id </br>IdentificationsChangePinDto data</td>
			<td>string</td>
			<td>Update Pin of identification</td>
		</tr>
		<tr>
			<td>UpdateIdentificationChangePinAsync</td>
			<td>Guid id </br>IdentificationsChangePinDto data</td>
			<td>string</td>
			<td>Update Pin of identification</td>
		</tr>
	</tbody>
</table>
<BR/>
<table>
		<h4>IdentificationsProviderDto</h4>
			<thead>
				<tr> 
					<td>Data</td>
					<td>Description</td>
				</tr>
			</thead>
			<tbody>
            <tr>
                <td>Guid Id</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid IdNetwork</td>
                <td></td>
            </tr>
            <tr>
                <td>tring Name</td>
                <td></td>
            </tr>
            <tr>
                <td>string Email</td>
                <td></td>
            </tr>
            <tr>
                <td>string EmailTemplate</td>
                <td></td>
            </tr>
			</tbody>
</table>
<table>
	 <thead>
		<tr> 
			<td>Method</td>
			<td>Parameters</td>
			<td>Response</td>
			<td>Description</td>
			
		</tr>
	 </thead>
	 <tbody>
		<tr>
			<td>GetIdentificationsProviders</td>
			<td>string name = null</br> int page = 1</br> int pageSize = 50</br> string orderField = "name"</br> string orderType = "asc"</td>
			<td>IdentificationsProviderDto</td>
			<td>Get list of the IdentificationsProviderDto</td>
		</tr>
		<tr>
			<td>GetIdentificationsProvidersAsync</td>
			<td>string name = null</br> int page = 1</br> int pageSize = 50</br> string orderField = "name"</br> string orderType = "asc"</td>
			<td>IdentificationsProviderDto</td>
			<td>Get list of the IdentificationsProviderDto</td>
		</tr>

		<tr>
			<td>GetIdentificationProvider</td>
			<td>Guid id</td>
			<td>IdentificationsProviderDto</td>
			<td>Get individual IdentificationsProviderDto</td>
		</tr>
		<tr>
			<td>GetIdentificationProviderAsync</td>
			<td>Guid id</td>
			<td>IdentificationsProviderDto</td>
			<td>Get individual IdentificationsProviderDto</td>
		</tr>
		
		<tr>
			<td>CreateIdentificationProvider</td>
			<td>IdentificationsProviderDto data</td>
			<td>IdentificationsProviderDto</td>
			<td>Create IdentificationsProviderDto</td>
		</tr>
		<tr>
			<td>CreateIdentificationProviderAsync</td>
			<td>IdentificationsProviderDto data</td>
			<td>IdentificationsProviderDto</td>
			<td>Create IdentificationsProviderDto</td>
		</tr>
	
		<tr>
			<td>UpdateIdentificationProvider</td>
			<td>Guid id </br>IdentificationsProviderDto data</td>
			<td>string</td>
			<td>Update IdentificationsProviderDto</td>
		</tr>
		<tr>
			<td>UpdateIdentificationProviderAsync</td>
			<td>Guid id </br>IdentificationsProviderDto data</td>
			<td>string</td>
			<td>Update IdentificationsProviderDto</td>
		</tr>
	</tbody>
</table>
<BR/>
<table>
		<h4>IdentificationTypeModelDto</h4>
			<thead>
				<tr> 
					<td>Data</td>
					<td>Description</td>
				</tr>
			</thead>
			<tbody>
            <tr>
                <td>Guid Id</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid IdNetwork</td>
                <td></td>
            </tr>
            <tr>
                <td>short IdentificationType</td>
                <td></td>
            </tr>
            <tr>
                <td>string Description</td>
                <td></td>
            </tr>
            <tr>
                <td>bool Instalable</td>
                <td></td>
            </tr>
            <tr>
                <td>bool Personalized</td>
                <td></td>
            </tr>
            <tr>
                <td>bool Reusable</td>
                <td></td>
            </tr>
            <tr>
                <td>bool MultipleAssign</td>
                <td></td>
            </tr>
            <tr>
                <td>bool ValidateExpDate</td>
                <td></td>
            </tr>
            <tr>
                <td>bool RequierePin</td>
                <td></td>
            </tr>
            <tr>
                <td>int PinDigits</td>
                <td></td>
            </tr>
            <tr>
                <td>bool IgnoreTerminalVehicleIdBehavior</td>
                <td></td>
            </tr>
            <tr>
                <td>bool CustomTrack</td>
                <td></td>
            </tr>
            <tr>
                <td>bool RequiresPINChange</td>
                <td></td>
            </tr>
			</tbody>
</table>
<table>
	 <thead>
		<tr> 
			<td>Method</td>
			<td>Parameters</td>
			<td>Response</td>
			<td>Description</td>
			
		</tr>
	 </thead>
	 <tbody>
		<tr>
			<td>GetIdentificationTypeModels</td>
			<td>short? identificationType = null</br> int page = 1</br> int pageSize = 50</br> string orderField = "name"</br> string orderType = "asc"</td>
			<td>IdentificationTypeModelDto</td>
			<td>Get list of the IdentificationTypeModelDto</td>
		</tr>
		<tr>
			<td>GetIdentificationTypeModelsAsync</td>
			<td>short? identificationType = null</br> int page = 1</br> int pageSize = 50</br> string orderField = "name"</br> string orderType = "asc"</td>
			<td>IdentificationTypeModelDto</td>
			<td>Get list of the IdentificationTypeModelDto</td>
		</tr>

		<tr>
			<td>GetIdentificationtypeModel</td>
			<td>Guid id</td>
			<td>IdentificationTypeModelDto</td>
			<td>Get individual IdentificationTypeModelDto</td>
		</tr>
		<tr>
			<td>GetIdentificationtypeModelAsync</td>
			<td>Guid id</td>
			<td>IdentificationTypeModelDto</td>
			<td>Get individual IdentificationTypeModelDto</td>
		</tr>
	
	</tbody>
</table>
<BR/>
<table>
		<h4>IdentityDto</h4>
			<thead>
				<tr> 
					<td>Data</td>
					<td>Description</td>
				</tr>
			</thead>
			<tbody>
            <tr>
                <td>string ReportedCopy</td>
                <td></td>
            </tr>
            <tr>
                <td>string ReportedProcedureNumber</td>
                <td></td>
            </tr>
            <tr>
                <td>string ReportedIssueDate</td>
                <td></td>
            </tr>
            <tr>
                <td>string ReportedBirthDate</td>
                <td></td>
            </tr>
            <tr>
                <td>string ReportedSex</td>
                <td></td>
            </tr>
            <tr>
                <td>string ReportedLastName</td>
                <td></td>
            </tr>
            <tr>
                <td>string ReportedFirstName</td>
                <td></td>
            </tr>
            <tr>
                <td>string ReportedCountry</td>
                <td></td>
            </tr>
            <tr>
                <td>string ReportedIdentityNumber</td>
                <td></td>
            </tr>
            <tr>
                <td>bool UserConsent</td>
                <td></td>
            </tr>
            <tr>
                <td>string ProfilePicture</td>
                <td></td>
            </tr>
            <tr>
                <td>string ZipCode</td>
                <td></td>
            </tr>
            <tr>
                <td>string StreetAddress</td>
                <td></td>
            </tr>
            <tr>
                <td>DateTime? BirthDate</td>
                <td></td>
            </tr>
            <tr>
                <td>string Alias</td>
                <td></td>
            </tr>
            <tr>
                <td>string Name</td>
                <td></td>
            </tr>
            <tr>
                <td>byte? IdentityNumberType</td>
                <td></td>
            </tr>
            <tr>
                <td>string IdentityNumber</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid IdNetwork</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid Id</td>
                <td></td>
            </tr>
            <tr>
                <td>string PhoneNumber</td>
                <td></td>
            </tr>
            <tr>
                <td>List IdentityLoyaltyIdentificationDto  LoyaltyIdentifications</td>
                <td></td>
            </tr>
			</tbody>
</table>
<table>
	 <thead>
		<tr> 
			<td>Method</td>
			<td>Parameters</td>
			<td>Response</td>
			<td>Description</td>
			
		</tr>
	 </thead>
	 <tbody>
		<tr>
			<td>GetIdentities</td>
			<td>string identitiyNumber = null</br> string name = null</br> bool? userConsent = null</br> string searchText = null</br> int page = 1</br> int pageSize = 50</br> string orderField = "name"</br> string orderType = "asc"</td>
			<td>IdentityDto</td>
			<td>Get list of the IdentityDto</td>
		</tr>
		<tr>
			<td>GetIdentitiesAsync</td>
			<td>string identitiyNumber = null</br> string name = null</br> bool? userConsent = null</br> string searchText = null</br> int page = 1</br> int pageSize = 50</br> string orderField = "name"</br> string orderType = "asc"</td>
			<td>IdentityDto</td>
			<td>Get list of the IdentityDto</td>
		</tr>

		<tr>
			<td>GetIdentity</td>
			<td>Guid id</td>
			<td>IdentityDto</td>
			<td>Get individual IdentityDto</td>
		</tr>
		<tr>
			<td>GetIdentityAsync</td>
			<td>Guid id</td>
			<td>IdentityDto</td>
			<td>Get individual IdentityDto</td>
		</tr>
		
		<tr>
			<td>CreateIdentity</td>
			<td>IdentityDto data</td>
			<td>IdentityDto</td>
			<td>Create IdentityDto</td>
		</tr>
		<tr>
			<td>CreateIdentityAsync</td>
			<td>IdentityDto data</td>
			<td>IdentityDto</td>
			<td>Create IdentityDto</td>
		</tr>
	
		<tr>
			<td>UpdateIdentity</td>
			<td>Guid id </br>IdentityDto data</td>
			<td>string</td>
			<td>Update IdentityDto</td>
		</tr>
		<tr>
			<td>UpdateIdentityAsync</td>
			<td>Guid id </br>IdentityDto data</td>
			<td>string</td>
			<td>Update IdentityDto</td>
		</tr>
	</tbody>
</table>
<BR/>
<table>
		<h4>LoyaltyAccountDto</h4>
			<thead>
				<tr> 
					<td>Data</td>
					<td>Description</td>
				</tr>
			</thead>
			<tbody>
            <tr>
                <td>string VehiclePlate</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? IdFleet</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? IdVehicle</td>
                <td></td>
            </tr>
            <tr>
                <td>string DriverLastName</td>
                <td></td>
            </tr>
            <tr>
                <td>string DriverFirstName</td>
                <td></td>
            </tr>
            <tr>
                <td>string DriverEmail</td>
                <td></td>
            </tr>
            <tr>
                <td>string DriverCode</td>
                <td></td>
            </tr>
            <tr>
                <td>string DriverLicenseNumber</td>
                <td></td>
            </tr>
            <tr>
                <td>string VehicleCode</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? IdDriver</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid IdNetwork</td>
                <td></td>
            </tr>
            <tr>
                <td>string IdentitiyName</td>
                <td></td>
            </tr>
            <tr>
                <td>byte IdentitiyNumberType</td>
                <td></td>
            </tr>
            <tr>
                <td>string IdentitiyNumber</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid IdIdentity</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid IdCompany</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid IdCommunity</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid Id</td>
                <td></td>
            </tr>
            <tr>
                <td>short CommunityTarget</td>
                <td></td>
            </tr>
            <tr>
                <td>IEnumerable<LoyaltyAccountIdentificationDto> LoyaltyClientCards</td>
                <td></td>
            </tr>
			</tbody>
</table>
<table>
	 <thead>
		<tr> 
			<td>Method</td>
			<td>Parameters</td>
			<td>Response</td>
			<td>Description</td>
			
		</tr>
	 </thead>
	 <tbody>
		<tr>
			<td>GetLoyaltyAccounts</td>
			<td>string searchText = null</br> string identificationLabel = null</br> string identificationTrackNumber = null</br> Guid? idCommunity = null</br> Guid? idIdentity = null</br> string identityNumber = null</br> int page = 1</br> int pageSize = 50</br> string orderField = "label"</br> string orderType = "asc"</td>
			<td>LoyaltyAccountDto</td>
			<td>Get list of the LoyaltyAccountDto</td>
		</tr>
		<tr>
			<td>GetLoyaltyAccounts</td>
			<td>string searchText = null</br> string identificationLabel = null</br> string identificationTrackNumber = null</br> Guid? idCommunity = null</br> Guid? idIdentity = null</br> string identityNumber = null</br> int page = 1</br> int pageSize = 50</br> string orderField = "label"</br> string orderType = "asc"</td>
			<td>LoyaltyAccountDto</td>
			<td>Get list of the LoyaltyAccountDto</td>
		</tr>

		<tr>
			<td>GetLoyaltyAccount</td>
			<td>Guid id</td>
			<td>LoyaltyAccountDto</td>
			<td>Get individual LoyaltyAccountDto</td>
		</tr>
		<tr>
			<td>GetLoyaltyAccountAsync</td>
			<td>Guid id</td>
			<td>LoyaltyAccountDto</td>
			<td>Get individual LoyaltyAccountDto</td>
		</tr>
		
		<tr>
			<td>CreateLoyaltyAccount</td>
			<td>LoyaltyAccountDto data</td>
			<td>LoyaltyAccountDto</td>
			<td>Create LoyaltyAccountDto</td>
		</tr>
		<tr>
			<td>CreateLoyaltyAccountAsync</td>
			<td>LoyaltyAccountDto data</td>
			<td>LoyaltyAccountDto</td>
			<td>Create LoyaltyAccountDto</td>
		</tr>
	
		<tr>
			<td>UpdateLoyaltyAccount</td>
			<td>Guid id </br>LoyaltyAccountDto data</td>
			<td>string</td>
			<td>Update LoyaltyAccountDto</td>
		</tr>
		<tr>
			<td>UpdateLoyaltyAccountAsync</td>
			<td>Guid id </br>LoyaltyAccountDto data</td>
			<td>string</td>
			<td>Update LoyaltyAccountDto</td>
		</tr>
	</tbody>
</table>
<BR/>
<table>
		<h4>LoyaltyTransactionDto</h4>
			<thead>
				<tr> 
					<td>Data</td>
					<td>Description</td>
				</tr>
			</thead>
			<tbody>
             <tr>
                <td>Guid? DriverId</td>
                <td></td>
            </tr>
            <tr>
                <td>string VehiclePlate</td>
                <td></td>
            </tr>
            <tr>
                <td>string VehicleCode</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? VehicleId</td>
                <td></td>
            </tr>
            <tr>
                <td>string FleetName</td>
                <td></td>
            </tr>
            <tr>
                <td>string FleetCode</td>
                <td></td>
            </tr>
            <tr>
                <td>string DriverCode</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? FleetId</td>
                <td></td>
            </tr>
            <tr>
                <td>string SecondaryLoyaltyAccountDescription</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? SecondaryLoyaltyAccountId</td>
                <td></td>
            </tr>
            <tr>
                <td>bool IsPrimaryLoyaltyAccountVehicle</td>
                <td></td>
            </tr>
            <tr>
                <td>string PrimaryLoyaltyAccountDescription</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? PrimaryLoyaltyAccountId</td>
                <td></td>
            </tr>
            <tr>
                <td>string SecondaryIdentificationPAN</td>
                <td></td>
            </tr>
            <tr>
                <td>bool IsSecondaryLoyaltyAccountVehicle</td>
                <td></td>
            </tr>
            <tr>
                <td>string DriverCompleteName</td>
                <td></td>
            </tr>
            <tr>
                <td>string AccountTypeDescription</td>
                <td></td>
            </tr>
            <tr>
                <td>string InvoiceNumber</td>
                <td></td>
            </tr>
            <tr>
                <td>bool EHVoided</td>
                <td></td>
            </tr>
            <tr>
                <td>bool Voided</td>
                <td></td>
            </tr>
            <tr>
                <td>short EHState</td>
                <td></td>
            </tr>
            <tr>
                <td>byte State</td>
                <td></td>
            </tr>
            <tr>
                <td>short ConciliationState</td>
                <td></td>
            </tr>
            <tr>
                <td>decimal? LoyaltyPoints</td>
                <td></td>
            </tr>
            <tr>
                <td>decimal? EHLoyaltyPoints</td>
                <td></td>
            </tr>
            <tr>
                <td>string EHComments</td>
                <td></td>
            </tr>
            <tr>
                <td>string EHAuthorizationCode</td>
                <td></td>
            </tr>
            <tr>
                <td>string UnitName</td>
                <td></td>
            </tr>
            <tr>
                <td>decimal? TransactionAmount</td>
                <td></td>
            </tr>
            <tr>
                <td>decimal? Amount</td>
                <td></td>
            </tr>
            <tr>
                <td>string EntryMethod</td>
                <td></td>
            </tr>
            <tr>
                <td>string ShiftNumber</td>
                <td></td>
            </tr>
            <tr>
                <td>int? BatchNumber</td>
                <td></td>
            </tr>
            <tr>
                <td>string SecondaryIdentificationLabel</td>
                <td></td>
            </tr>
            <tr>
                <td>List< PaymentsMethodDto PaymentMethods</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? SecondaryIdentificationId</td>
                <td></td>
            </tr>
            <tr>
                <td>string PrimaryIdentificationLabel</td>
                <td></td>
            </tr>
            <tr>
                <td>string StatusDescription</td>
                <td></td>
            </tr>
            <tr>
                <td>short? Status</td>
                <td></td>
            </tr>
            <tr>
                <td>string ModeDescription</td>
                <td></td>
            </tr>
            <tr>
                <td>short? Mode</td>
                <td></td>
            </tr>
            <tr>
                <td>string TypeDescription</td>
                <td></td>
            </tr>
            <tr>
                <td>short Type</td>
                <td></td>
            </tr>
            <tr>
                <td>string HostDateTime</td>
                <td></td>
            </tr>
            <tr>
                <td>string ResponseMessage</td>
                <td></td>
            </tr>
            <tr>
                <td>string AuthorizationCode</td>
                <td></td>
            </tr>
            <tr>
                <td>string TransactionSequenceNumber</td>
                <td></td>
            </tr>
            <tr>
                <td>string SubscriberName</td>
                <td></td>
            </tr>
            <tr>
                <td>string SubscriberCode</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? SubscriberId</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid Id</td>
                <td></td>
            </tr>
            <tr>
                <td>string ResponseCode</td>
                <td></td>
            </tr>
            <tr>
                <td>string SubscriberDateTime</td>
                <td></td>
            </tr>
            <tr>
                <td>string SubscriberTimeZone</td>
                <td></td>
            </tr>
            <tr>
                <td>string SiteDateTime</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? PrimaryIdentificationId</td>
                <td></td>
            </tr>
            <tr>
                <td>string CompanyTaxpayerId</td>
                <td></td>
            </tr>
            <tr>
                <td>string CompanyName</td>
                <td></td>
            </tr>
            <tr>
                <td>string CompanyCode</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? CompanyId</td>
                <td></td>
            </tr>
            <tr>
                <td>string TerminalCode</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? TerminalId</td>
                <td></td>
            </tr>
            <tr>
                <td>string SiteName</td>
                <td></td>
            </tr>
            <tr>
                <td>string SiteCode</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? SiteId</td>
                <td></td>
            </tr>
            <tr>
                <td>string MerchantName</td>
                <td></td>
            </tr>
            <tr>
                <td>string MerchantCode</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? MerchantId</td>
                <td></td>
            </tr>
            <tr>
                <td>string DateTime</td>
                <td></td>
            </tr>
            <tr>
                <td>string SiteTimeZone</td>
                <td></td>
            </tr>
            <tr>
                <td>string PrimaryIdentificationPAN</td>
                <td></td>
            </tr>
            <tr>
                <td>List LoyaltyTransactionsProductDto  Products</td>
                <td></td>
            </tr>
			</tbody>
</table>
<table>
	 <thead>
		<tr> 
			<td>Method</td>
			<td>Parameters</td>
			<td>Response</td>
			<td>Description</td>
			
		</tr>
	 </thead>
	 <tbody>
		<tr>
			<td>GetLoyaltyTransactions</td>
			<td>string dateTimeFrom = null</br> string dateTimeTo = null</br> int page = 1</br> int pageSize = 50</br> string orderField = "code"</br> string orderType = "asc"</td>
			<td>LoyaltyTransactionDto</td>
			<td>Get list of the LoyaltyTransactionDto</td>
		</tr>
		<tr>
			<td>GetLoyaltyTransactionsAsync</td>
			<td>string dateTimeFrom = null</br> string dateTimeTo = null</br> int page = 1</br> int pageSize = 50</br> string orderField = "code"</br> string orderType = "asc"</td>
			<td>LoyaltyTransactionDto</td>
			<td>Get list of the LoyaltyTransactionDto</td>
		</tr>

		<tr>
			<td>GetLoyaltyTransaction</td>
			<td>Guid id</td>
			<td>LoyaltyTransactionDto</td>
			<td>Get individual LoyaltyTransactionDto</td>
		</tr>
		<tr>
			<td>GetLoyaltyTransactionAsync</td>
			<td>Guid id</td>
			<td>LoyaltyTransactionDto</td>
			<td>Get individual LoyaltyTransactionDto</td>
		</tr>
	
	</tbody>
</table>
<BR/>
<table>
		<h4>MerchantDto</h4>
			<thead>
				<tr> 
					<td>Data</td>
					<td>Description</td>
				</tr>
			</thead>
			<tbody>
             <tr>
                <td>string Custom1</td>
                <td></td>
            </tr>
            <tr>
                <td>string Custom0</td>
                <td></td>
            </tr>
            <tr>
                <td>bool Active</td>
                <td></td>
            </tr>
            <tr>
                <td>string ContactPhone2</td>
                <td></td>
            </tr>
            <tr>
                <td>string ContactPhone1</td>
                <td></td>
            </tr>
            <tr>
                <td>string ContactEmail</td>
                <td></td>
            </tr>
            <tr>
                <td>string ContactName</td>
                <td></td>
            </tr>
            <tr>
                <td>DateTime CreationDate</td>
                <td></td>
            </tr>
            <tr>
                <td>string IndustryDescription</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid IndustryId</td>
                <td></td>
            </tr>
            <tr>
                <td>string Custom2</td>
                <td></td>
            </tr>
            <tr>
                <td>string TaxPayerId</td>
                <td></td>
            </tr>
            <tr>
                <td>string ZipCode</td>
                <td></td>
            </tr>
            <tr>
                <td>string StateDescription</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid StateId</td>
                <td></td>
            </tr>
            <tr>
                <td>string CountryDescription</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid CountryId</td>
                <td></td>
            </tr>
            <tr>
                <td>string Street2</td>
                <td></td>
            </tr>
            <tr>
                <td>string Street1</td>
                <td></td>
            </tr>
            <tr>
                <td>string Name</td>
                <td></td>
            </tr>
            <tr>
                <td>string Code</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid Id</td>
                <td></td>
            </tr>
            <tr>
                <td>string City</td>
                <td></td>
            </tr>
            <tr>
                <td>string Custom3</td>
                <td></td>
            </tr>
			</tbody>
</table>
<table>
	 <thead>
		<tr> 
			<td>Method</td>
			<td>Parameters</td>
			<td>Response</td>
			<td>Description</td>
			
		</tr>
	 </thead>
	 <tbody>
		<tr>
			<td>GetMerchants</td>
			<td>List Guid  merchantIds = null</br> string code = null</br> string name = null</br> string custom0 = null</br> string custom1 = null</br> string custom2 = null</br> string custom3 = null</br> int page = 1</br> int pageSize = 50</br> string orderField = "name"</br> string orderType = "asc"</td>
			<td>MerchantDto</td>
			<td>Get list of the MerchantDto</td>
		</tr>
		<tr>
			<td>GetMerchantsAsync</td>
			<td>List Guid  merchantIds = null</br> string code = null</br> string name = null</br> string custom0 = null</br> string custom1 = null</br> string custom2 = null</br> string custom3 = null</br> int page = 1</br> int pageSize = 50</br> string orderField = "name"</br> string orderType = "asc"</td>
			<td>MerchantDto</td>
			<td>Get list of the MerchantDto</td>
		</tr>

		<tr>
			<td>GetMerchant</td>
			<td>Guid id</td>
			<td>MerchantDto</td>
			<td>Get individual MerchantDto</td>
		</tr>
		<tr>
			<td>GetMerchantAsync</td>
			<td>Guid id</td>
			<td>MerchantDto</td>
			<td>Get individual MerchantDto</td>
		</tr>
		
		<tr>
			<td>CreateMerchant</td>
			<td>MerchantDto data</td>
			<td>MerchantDto</td>
			<td>Create MerchantDto</td>
		</tr>
		<tr>
			<td>CreateMerchantAsync</td>
			<td>MerchantDto data</td>
			<td>MerchantDto</td>
			<td>Create MerchantDto</td>
		</tr>
	
		<tr>
			<td>UpdateMerchant</td>
			<td>Guid id </br>MerchantDto data</td>
			<td>string</td>
			<td>Update MerchantDto</td>
		</tr>
		<tr>
			<td>UpdateMerchantAsync</td>
			<td>Guid id </br>MerchantDto data</td>
			<td>string</td>
			<td>Update MerchantDto</td>
		</tr>
	</tbody>
</table>
<BR/>
<table>
		<h4>MovementDto</h4>
			<thead>
				<tr> 
					<td>Data</td>
					<td>Description</td>
				</tr>
			</thead>
			<tbody>
             <tr>
                <td>string OriginId</td>
                <td></td>
            </tr>
            <tr>
                <td>byte Origin</td>
                <td></td>
            </tr>
            <tr>
                <td>byte Type</td>
                <td></td>
            </tr>
            <tr>
                <td>DateTime NetworkDate</td>
                <td></td>
            </tr>
            <tr>
                <td>string NetworkTimeZone</td>
                <td></td>
            </tr>
            <tr>
                <td>DateTime RealDate</td>
                <td></td>
            </tr>
            <tr>
                <td>bool Reversed</td>
                <td></td>
            </tr>
            <tr>
                <td>string Description</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? UserAtionetId</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? ProcessBillingStatementId</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? FastTrackId</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? TransactionId</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid CompanyId</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid Id</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? LastMovementId</td>
                <td></td>
            </tr>
            <tr>
                <td>List MovementsDetailDto  DetailsMovementDto</td>
                <td></td>
            </tr>
			</tbody>
</table>
<table>
	 <thead>
		<tr> 
			<td>Method</td>
			<td>Parameters</td>
			<td>Response</td>
			<td>Description</td>
			
		</tr>
	 </thead>
	 <tbody>
		<tr>
			<td>GetMovements</td>
			<td>Guid? idCompany=null</br>
			  Guid? fastTrackId = null</br> Guid? lastMovementId = null</br> Guid? processBillingStatementId = null</br> Guid? transactionId = null</br> Guid? userAtionetId = null</br>
			  string originId = null</br> string description = null</br>
			  byte? origin = null</br> byte? type = null</br> bool? reversed = null</br>
			  string realDateFrom = null</br> string realDateTo = null</br>
			  string order = "desc"</br> int page = 1</br> int pageSize = 50</td>
			<td>MovementDto</td>
			<td>Get list of the MovementDto</td>
		</tr>
		<tr>
			<td>GetMovementsAsync</td>
			<td>Guid? idCompany=null</br>
			  Guid? fastTrackId = null</br> Guid? lastMovementId = null</br> Guid? processBillingStatementId = null</br> Guid? transactionId = null</br> Guid? userAtionetId = null</br>
			  string originId = null</br> string description = null</br>
			  byte? origin = null</br> byte? type = null</br> bool? reversed = null</br>
			  string realDateFrom = null</br> string realDateTo = null</br>
			  string order = "desc"</br> int page = 1</br> int pageSize = 50</td>

			<td>MovementDto</td>
			<td>Get list of the MovementDto</td>
		</tr>

		<tr>
			<td>GetMovement</td>
			<td>Guid id</td>
			<td>MovementDto</td>
			<td>Get individual MovementDto</td>
		</tr>
		<tr>
			<td>GetMovementAsync</td>
			<td>Guid id</td>
			<td>MovementDto</td>
			<td>Get individual MovementDto</td>
		</tr>
	
	</tbody>
</table>
<BR/>
<table>
		<h4>NetworkDto</h4>
			<thead>
				<tr> 
					<td>Data</td>
					<td>Description</td>
				</tr>
			</thead>
			<tbody>
             <tr>
                <td>string StateName</td>
                <td></td>
            </tr>
            <tr>
                <td>string TimeZone</td>
                <td></td>
            </tr>
            <tr>
                <td>string City</td>
                <td></td>
            </tr>
            <tr>
                <td>string Street1</td>
                <td></td>
            </tr>
            <tr>
                <td>string Street2</td>
                <td></td>
            </tr>
            <tr>
                <td>string ZipCode</td>
                <td></td>
            </tr>
            <tr>
                <td>string PhoneNumber1</td>
                <td></td>
            </tr>
            <tr>
                <td>string PhoneNumber2</td>
                <td></td>
            </tr>
            <tr>
                <td>string ContactName</td>
                <td></td>
            </tr>
            <tr>
                <td>string ContactEmail</td>
                <td></td>
            </tr>
            <tr>
                <td>string CreationDate</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid StateId</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid BrandId</td>
                <td></td>
            </tr>
            <tr>
                <td>string IdentificationRequestMail</td>
                <td></td>
            </tr>
            <tr>
                <td>string SupportMail</td>
                <td></td>
            </tr>
            <tr>
                <td>string SenderMail</td>
                <td></td>
            </tr>
            <tr>
                <td>bool IsEdiFactBillingProcessType</td>
                <td></td>
            </tr>
            <tr>
                <td>List NetworkCustomFieldsConfigurationDto  CustomFieldsConfigurations</td>
                <td></td>
            </tr>
            <tr>
                <td>List NetworkCompanyDto  Companies</td>
                <td></td>
            </tr>
            <tr>
                <td>List NetworkMerchantDto  Merchants</td>
                <td></td>
            </tr>
            <tr>
                <td>List NetworkFiscalConfigurationDto  FiscalConfigurations</td>
                <td></td>
            </tr>
            <tr>
                <td>string PrimaryColor</td>
                <td></td>
            </tr>
            <tr>
                <td>string SecondaryColor</td>
                <td></td>
            </tr>
            <tr>
                <td>string AccentColor</td>
                <td></td>
            </tr>
            <tr>
                <td>string BrandName</td>
                <td></td>
            </tr>
            <tr>
                <td>string NetworkLogoURL</td>
                <td></td>
            </tr>
            <tr>
                <td>string CountryName</td>
                <td></td>
            </tr>
            <tr>
                <td>string TaxPayerId</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid Id</td>
                <td></td>
            </tr>
            <tr>
                <td>string Name</td>
                <td></td>
            </tr>
            <tr>
                <td>short Type</td>
                <td></td>
            </tr>
            <tr>
                <td>byte? BalanceMode</td>
                <td></td>
            </tr>
            <tr>
                <td>byte? CurrentAccountMode</td>
                <td></td>
            </tr>
            <tr>
                <td>byte BillingProcessType</td>
                <td></td>
            </tr>
            <tr>
                <td>short EdiFactTaxRegimeCode</td>
                <td></td>
            </tr>
            <tr>
                <td>string Code</td>
                <td></td>
            </tr>
            <tr>
                <td>string InternalCode</td>
                <td></td>
            </tr>
            <tr>
                <td>bool Active</td>
                <td></td>
            </tr>
            <tr>
                <td>bool SupportsLoyalty</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid CountryId</td>
                <td></td>
            </tr>
            <tr>
                <td>bool SupportsInventory</td>
                <td></td>
            </tr>
            <tr>
                <td>bool SupportsTracking</td>
                <td></td>
            </tr>
            <tr>
                <td>bool SupportsFleet</td>
                <td></td>
            </tr>
            <tr>
                <td>bool SupportsAnalytics</td>
                <td></td>
            </tr>
            <tr>
                <td>bool SupportsConsumerCard</td>
                <td></td>
            </tr>
            <tr>
                <td>bool SupportsWorkflows</td>
                <td></td>
            </tr>
            <tr>
                <td>bool SupportsDriverMobileApp</td>
                <td></td>
            </tr>
            <tr>
                <td>bool SupportsCompanyMobileApp</td>
                <td></td>
            </tr>
            <tr>
                <td>bool SupportsMerchantMobileApp</td>
                <td></td>
            </tr>
            <tr>
                <td>bool SupportsNetworkMobileApp</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid IndustryId</td>
                <td></td>
            </tr>
            <tr>
                <td>string IndustryDescription</td>
                <td></td>
            </tr>
            <tr>
                <td>bool SupportsOffline</td>
                <td></td>
            </tr>
            <tr>
                <td>string NetworkLogoExtension</td>
                <td></td>
            </tr>
			</tbody>
</table>
<table>
	 <thead>
		<tr> 
			<td>Method</td>
			<td>Parameters</td>
			<td>Response</td>
			<td>Description</td>
			
		</tr>
	 </thead>
	 <tbody>
		
		<tr>
			<td>GetNetworkAsync</td>
			<td></td>
			<td>NetworkDto</td>
			<td>Get individual NetworkDto</td>
		</tr>
		<tr>
			<td>GetNetworkAsync</td>
			<td></td>
			<td>NetworkDto</td>
			<td>Get individual NetworkDto</td>
		</tr>
	
	</tbody>
</table>
<BR/>
<table>
		<h4>PaymentsMethodDto</h4>
			<thead>
				<tr> 
					<td>Data</td>
					<td>Description</td>
				</tr>
			</thead>
			<tbody>
			<tr>
                <td>Guid Id</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid NetworkId</td>
                <td></td>
            </tr>
            <tr>
                <td>string Code</td>
                <td></td>
            </tr>
            <tr>
                <td>string Description</td>
                <td></td>
            </tr>
            <tr>
                <td>decimal? Total</td>
                <td></td>
            </tr>
            <tr>
                <td>DateTime UpdateDate</td>
                <td></td>
            </tr>
            
			</tbody>
</table>
<table>
	 <thead>
		<tr> 
			<td>Method</td>
			<td>Parameters</td>
			<td>Response</td>
			<td>Description</td>
			
		</tr>
	 </thead>
	 <tbody>
		<tr>
			<td>GetPaymentsMethods</td>
			<td>List Guid  paymentsMethodIds = null</br> string code = null</br> string description = null</br> DateTime? updateDate = null</br> int page = 1</br> int pageSize = 50</br> string orderField = "code"</br> string orderType = "asc"</td>
			<td>PaymentsMethodDto</td>
			<td>Get list of the PaymentsMethodDto</td>
		</tr>
		<tr>
			<td>GetPaymentsMethodsAsync</td>
			<td>List Guid  paymentsMethodIds = null</br> string code = null</br> string description = null</br> DateTime? updateDate = null</br> int page = 1</br> int pageSize = 50</br> string orderField = "code"</br> string orderType = "asc"</td>
			<td>PaymentsMethodDto</td>
			<td>Get list of the PaymentsMethodDto</td>
		</tr>

		<tr>
			<td>GetPaymentsMethod</td>
			<td>Guid id</td>
			<td>PaymentsMethodDto</td>
			<td>Get individual PaymentsMethodDto</td>
		</tr>
		<tr>
			<td>GetPaymentsMethodAsync</td>
			<td>Guid id</td>
			<td>PaymentsMethodDto</td>
			<td>Get individual PaymentsMethodDto</td>
		</tr>
		
		<tr>
			<td>CreatePaymentsMethod</td>
			<td>PaymentsMethodDto data</td>
			<td>PaymentsMethodDto</td>
			<td>Create PaymentsMethodDto</td>
		</tr>
		<tr>
			<td>CreatePaymentsMethodAsync</td>
			<td>PaymentsMethodDto data</td>
			<td>PaymentsMethodDto</td>
			<td>Create PaymentsMethodDto</td>
		</tr>
	
		<tr>
			<td>UpdatePaymentsMethod</td>
			<td>Guid id </br>PaymentsMethodDto data</td>
			<td>string</td>
			<td>Update PaymentsMethodDto</td>
		</tr>
		<tr>
			<td>UpdatePaymentsMethodAsync</td>
			<td>Guid id </br>PaymentsMethodDto data</td>
			<td>string</td>
			<td>Update PaymentsMethodDto</td>
		</tr>
	</tbody>
</table>
<BR/>
<table>
		<h4>ProgramDto</h4>
			<thead>
				<tr> 
					<td>Data</td>
					<td>Description</td>
				</tr>
			</thead>
			<tbody>
			 <tr>
                <td>bool SupportsDryProducts</td>
                <td></td>
            </tr>
            <tr>
                <td>string BINRange</td>
                <td></td>
            </tr>
            <tr>
                <td>decimal? GiftCardAmount</td>
                <td></td>
            </tr>
            <tr>
                <td>bool IsRechargeable</td>
                <td></td>
            </tr>
            <tr>
                <td>byte SupportsOffline</td>
                <td></td>
            </tr>
            <tr>
                <td>byte SupportsContingency</td>
                <td></td>
            </tr>
            <tr>
                <td>byte ApplyContractsSites</td>
                <td></td>
            </tr>
            <tr>
                <td>bool ValidateExpDate</td>
                <td></td>
            </tr>
            <tr>
                <td>byte BalanceMode</td>
                <td></td>
            </tr>
            <tr>
                <td>string Description</td>
                <td></td>
            </tr>
            <tr>
                <td>string CompanyName</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? CompanyId</td>
                <td></td>
            </tr>
            <tr>
                <td>string NetworkName</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid NetworkId</td>
                <td></td>
            </tr>
			<tr>
                <td>string InternalCode</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid Id</td>
                <td></td>
            </tr>
            <tr>
                <td>byte Type</td>
                <td></td>
            </tr>
            <tr>
                <td>ProgramRuleDto Rule</td>
                <td></td>
            </tr>

            
			</tbody>
</table>
<table>
	 <thead>
		<tr> 
			<td>Method</td>
			<td>Parameters</td>
			<td>Response</td>
			<td>Description</td>
			
		</tr>
	 </thead>
	 <tbody>
		<tr>
			<td>GetProgramsAsync</td>
			<td>List Guid programIds = null</br> string description = null</br> int page = 1</br> int pageSize = 50</br> string orderField = "name"</br> string orderType = "asc"</td>
			<td>Get list of the ProgramDto</td>
		</tr>
		<tr>
			<td>GetProgramsAsync</td>
			<td>List Guid programIds = null</br> string description = null</br> int page = 1</br> int pageSize = 50</br> string orderField = "name"</br> string orderType = "asc"</td>
			<td>Get list of the ProgramDto</td>
		</tr>

		<tr>
			<td>GetProgram</td>
			<td>Guid id</td>
			<td>ProgramDto</td>
			<td>Get individual ProgramDto</td>
		</tr>
		<tr>
			<td>GetProgramAsync</td>
			<td>Guid id</td>
			<td>ProgramDto</td>
			<td>Get individual ProgramDto</td>
		</tr>
		
		<tr>
			<td>CreateProgram</td>
			<td>ProgramDto data</td>
			<td>ProgramDto</td>
			<td>Create ProgramDto</td>
		</tr>
		<tr>
			<td>CreateProgramAsync</td>
			<td>ProgramDto data</td>
			<td>ProgramDto</td>
			<td>Create ProgramDto</td>
		</tr>
	
		<tr>
			<td>UpdateProgram</td>
			<td>Guid id </br>ProgramDto data</td>
			<td>string</td>
			<td>Update ProgramDto</td>
		</tr>
		<tr>
			<td>UpdateProgramAsync</td>
			<td>Guid id </br>ProgramDto data</td>
			<td>string</td>
			<td>Update ProgramDto</td>
		</tr>
	</tbody>
</table>
<BR/>
<table>
		<h4>RuleDto</h4>
			<thead>
				<tr> 
					<td>Data</td>
					<td>Description</td>
				</tr>
			</thead>
			<tbody>
			<tr>
                <td>int? OdometerMaxVariation</td>
                <td></td>
            </tr>
            <tr>
                <td>bool EngineHoursReprompt</td>
                <td></td>
            </tr>
            <tr>
                <td>int? EngineHoursMinVariation</td>
                <td></td>
            </tr>
            <tr>
                <td>int? EngineHoursMaxVariation</td>
                <td></td>
            </tr>
            <tr>
                <td>bool DriverIdReprompt</td>
                <td></td>
            </tr>
            <tr>
                <td>bool DriverPINReprompt</td>
                <td></td>
            </tr>
            <tr>
                <td>bool TruckUnitNumberReprompt</td>
                <td></td>
            </tr>
            <tr>
                <td>bool TrailerNumberReprompt</td>
                <td></td>
            </tr>
            <tr>
                <td>decimal? ContingencyLimit</td>
                <td></td>
            </tr>
            <tr>
                <td>decimal? OfflineLimit</td>
                <td></td>
            </tr>
            <tr>
                <td>List<Guid> SitesIds</td>
                <td></td>
            </tr>
            <tr>
                <td>byte Owner</td>
                <td></td>
            </tr>
            <tr>
                <td>List<DaysTimeRuleTypeDto> DaysTimeRuleType</td>
                <td></td>
            </tr>
            <tr>
                <td>string RuleTypeDescription</td>
                <td></td>
            </tr>
            <tr>
                <td>string RuleValues</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? ProgramId</td>
                <td></td>
            </tr>
            <tr>
                <td>string ProgramDescription</td>
                <td></td>
            </tr>
            <tr>
                <td>bool ExactDateTime</td>
                <td></td>
            </tr>
            <tr>
                <td>bool VehicleIdReprompt</td>
                <td></td>
            </tr>
            <tr>
                <td>bool SecondaryTrack</td>
                <td></td>
            </tr>
            <tr>
                <td>List<Guid> FuelsIds</td>
                <td></td>
            </tr>
            <tr>
                <td>List<RuleFuelDto> Fuels</td>
                <td></td>
            </tr>
            <tr>
                <td>List<RuleDriverDto> Drivers</td>
                <td></td>
            </tr>
            <tr>
                <td>int? OdometerMinVariation</td>
                <td></td>
            </tr>
            <tr>
                <td>List<RuleVehicleDto> Vehicles</td>
                <td></td>
            </tr>
            <tr>
                <td>bool OdometerReprompt</td>
                <td></td>
            </tr>
            <tr>
                <td>bool SecondaryTrackReprompt</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid Id</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? NetworkId</td>
                <td></td>
            </tr>
            <tr>
                <td>string NetworkName</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? CompanyId</td>
                <td></td>
            </tr>
            <tr>
                <td>string CompanyName</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? MerchantId</td>
                <td></td>
            </tr>
            <tr>
                <td>string MerchantName</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? CompanyContractId</td>
                <td></td>
            </tr>
            <tr>
                <td>string ContractDescription</td>
                <td></td>
            </tr>
            <tr>
                <td>short? RuleType</td>
                <td></td>
            </tr>
            <tr>
                <td>string Description</td>
                <td></td>
            </tr>
            <tr>
                <td>byte? Periodicity</td>
                <td></td>
            </tr>
            <tr>
                <td>short? PeriodicityAmount</td>
                <td></td>
            </tr>
            <tr>
                <td>decimal? MoneyQuota</td>
                <td></td>
            </tr>
            <tr>
                <td>decimal? VolumeQuota</td>
                <td></td>
            </tr>
            <tr>
                <td>int? TimeFrom</td>
                <td></td>
            </tr>
            <tr>
                <td>int? TimeTo</td>
                <td></td>
            </tr>
            <tr>
                <td>int? DateFrom</td>
                <td></td>
            </tr>
            <tr>
                <td>int? DateTo</td>
                <td></td>
            </tr>
            <tr>
                <td>decimal? SecurityLimit</td>
                <td></td>
            </tr>
            <tr>
                <td>int? TransactionsQuantity</td>
                <td></td>
            </tr>
            <tr>
                <td>int? Retries</td>
                <td></td>
            </tr>
            <tr>
                <td>bool VehiclePINReprompt</td>
                <td></td>
            </tr>
            <tr>
                <td>bool MiscellaneousReprompt</td>
                <td></td>
            </tr>
            <tr>
                <td>List RuleFleetDto  Fleets</td>
                <td></td>
            </tr>

            
			</tbody>
</table>
<table>
	 <thead>
		<tr> 
			<td>Method</td>
			<td>Parameters</td>
			<td>Response</td>
			<td>Description</td>
			
		</tr>
	 </thead>
	 <tbody>
		<tr>
			<td>GetRules</td>
			<td>string rule = null</br> short? ruleType = null</br> Guid? idVehicle = null</br> Guid? idDriver = null</br> Guid? idFleet = null</br> string customer = null</br> string company = null</br> string contract = null</br> int page = 1</br> int pageSize = 50</br> string orderField = "description"</br> string orderType = "asc"</td>
			<td>Get list of the RuleDto</td>
		</tr>
		<tr>
			<td>GetRulesAsync</td>
			<td>string rule = null</br> short? ruleType = null</br> Guid? idVehicle = null</br> Guid? idDriver = null</br> Guid? idFleet = null</br> string customer = null</br> string company = null</br> string contract = null</br> int page = 1</br> int pageSize = 50</br> string orderField = "description"</br> string orderType = "asc"</td>
			<td>Get list of the RuleDto</td>
		</tr>

		<tr>
			<td>GetRule</td>
			<td>Guid id</td>
			<td>RuleDto</td>
			<td>Get individual RuleDto</td>
		</tr>
		<tr>
			<td>GetRuleAsync</td>
			<td>Guid id</td>
			<td>RuleDto</td>
			<td>Get individual RuleDto</td>
		</tr>
		
		<tr>
			<td>CreateRule</td>
			<td>RuleDto data</td>
			<td>RuleDto</td>
			<td>Create RuleDto</td>
		</tr>
		<tr>
			<td>CreateRuleAsync</td>
			<td>RuleDto data</td>
			<td>RuleDto</td>
			<td>Create RuleDto</td>
		</tr>
	
		<tr>
			<td>UpdateRule</td>
			<td>Guid id </br>RuleDto data</td>
			<td>string</td>
			<td>Update RuleDto</td>
		</tr>
		<tr>
			<td>UpdateRuleAsync</td>
			<td>Guid id </br>RuleDto data</td>
			<td>string</td>
			<td>Update RuleDto</td>
		</tr>
		<tr>
			<td>DeleteRule</td>
			<td>Guid id</td>
			<td>string</td>
			<td>Get individual RuleDto</td>
		</tr>
		<tr>
			<td>DeleteRuleAsync</td>
			<td>Guid id</td>
			<td>string</td>
			<td>Get individual RuleDto</td>
		</tr>
	</tbody>
</table>
<BR/>
<table>
		<h4>ServiceFileEntryDto</h4>
			<thead>
				<tr> 
					<td>Data</td>
					<td>Description</td>
				</tr>
			</thead>
			<tbody>
			<tr>
                <td>DateTime RecordDate</td>
                <td></td>
            </tr>
            <tr>
                <td>byte? ServiceFileTargetType</td>
                <td></td>
            </tr>
            <tr>
                <td>byte? TransactionType</td>
                <td></td>
            </tr>
            <tr>
                <td>int? EngineHours</td>
                <td></td>
            </tr>
            <tr>
                <td>int? Odometer</td>
                <td></td>
            </tr>
            <tr>
                <td>string FreeText</td>
                <td></td>
            </tr>
            <tr>
                <td>string StockKeepingUnitDescription</td>
                <td></td>
            </tr>
            <tr>
                <td>string ServiceEntryClass3Description</td>
                <td></td>
            </tr>
            <tr>
                <td>string ServiceEntryClass2Description</td>
                <td></td>
            </tr>
            <tr>
                <td>string ServiceEntryClass1Description</td>
                <td></td>
            </tr>
            <tr>
                <td>string ServiceEntryTypeGroupDescription</td>
                <td></td>
            </tr>
            <tr>
                <td>string ServiceEntryTypeDescription</td>
                <td></td>
            </tr>
            <tr>
                <td>string ServiceFileCode</td>
                <td></td>
            </tr>
            <tr>
                <td>string DriverDescription</td>
                <td></td>
            </tr>
            <tr>
                <td>string VehicleDescription</td>
                <td></td>
            </tr>
            <tr>
                <td>string NetworkName</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? IdStockKeepingUnit</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? IdServiceEntryClass3</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? IdServiceEntryClass2</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? IdServiceEntryClass1</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? IdLoyaltyTransaction</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? IdTransaction</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? IdServiceEntryTypeGroup</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? IdServiceEntryType</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? IdServiceFile</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? IdDriver</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? IdVehicle</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid? IdNetwork</td>
                <td></td>
            </tr>
            <tr>
                <td>Guid Id</td>
                <td></td>
            </tr>
            <tr>
                <td>DateTime? EntryDate</td>
                <td></td>
            </tr>
            <tr>
                <td>DateTime? ExpirationDate</td>
                <td></td>
            </tr>
            
			</tbody>
</table>
<table>
	 <thead>
		<tr> 
			<td>Method</td>
			<td>Parameters</td>
			<td>Response</td>
			<td>Description</td>
			
		</tr>
	 </thead>
	 <tbody>
		<tr>
			<td>GetServiceFileEntries</td>
			<td>List Guid  loyaltyPrograms = null</br> List<Guid> identifications = null</br> List<Guid> drivers = null</br> List<Guid> vehicles = null</br> List<Guid> groups = null</br> List<Guid> types = null</br> List<Guid> products = null</br> string memberDate = null</br> string dateFrom = null</br> string dateTo = null</br> int page = 1</br> int pageSize = 50</td>
			<td>Get list of the ServiceFileEntryDto</td>
		</tr>
		<tr>
			<td>GetServiceFileEntriesAsync</td>
			<td>List Guid  loyaltyPrograms = null</br> List<Guid> identifications = null</br> List<Guid> drivers = null</br> List<Guid> vehicles = null</br> List<Guid> groups = null</br> List<Guid> types = null</br> List<Guid> products = null</br> string memberDate = null</br> string dateFrom = null</br> string dateTo = null</br> int page = 1</br> int pageSize = 50</td>
			<td>Get list of the ServiceFileEntryDto</td>
			<td>Get list of the ServiceFileEntryDto</td>
		</tr>

		<tr>
			<td>GetServiceFileEntry</td>
			<td>Guid id</td>
			<td>ServiceFileEntryDto</td>
			<td>Get individual ServiceFileEntryDto</td>
		</tr>
		<tr>
			<td>GetServiceFileEntryAsync</td>
			<td>Guid id</td>
			<td>ServiceFileEntryDto</td>
			<td>Get individual ServiceFileEntryDto</td>
		</tr>
		
		<tr>
			<td>CreateServiceFileEntry</td>
			<td>ServiceFileEntryDto data</td>
			<td>ServiceFileEntryDto</td>
			<td>Create ServiceFileEntryDto</td>
		</tr>
		<tr>
			<td>CreateServiceFileEntryAsync</td>
			<td>ServiceFileEntryDto data</td>
			<td>ServiceFileEntryDto</td>
			<td>Create ServiceFileEntryDto</td>
		</tr>
	</tbody>
</table>
<BR/>
<BR/>
<BR/>
<BR/>
<BR/>




<BR/>

















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
