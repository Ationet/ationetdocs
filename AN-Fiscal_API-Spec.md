![ationetlogo](Content/Images/ATIOnetLogo_250x70.png) 
# ATIOnet Fiscal API Reference
> **About:** This document describes and explains how to consume the Ationet.Fiscal APIs.	

</br>

<table>
	<thead>
		<tr>
			<td colspan="2" class="tablehead">Document Information</td>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td width="20%" class="rowhead" align="right">File:</td>
			<td>AN-Fiscal-API-Reference</td>
		</tr>
		<tr>
			<td align="right">Doc. Version:</td>
			<td>1.0</td>
		</tr>
		<tr>
			<td align="right">Release Date:</td>
			<td>12, May 2020</td>
		</tr>
		<tr>
			<td align="right">Author:</td>
			<td>ATIOnet LLC</td>
		</tr>
	</tbody>
</table>

<table>
     <thead>
          <tr>
          	<td colspan="3">Change Log</td>
          </tr>
     </thead>
     <tbody>
        <tr>
          	<td>Ver.</td>
            <td>Date</td>
            <td>Change summary</td>
        </tr>
        <!-- Insert a table row like this for each version -->
        <tr>
          	<td>1.0</td>
          	<td>12/May/2020</td>
          	<td>Initial version</td>
        </tr>
        <!-- End of version table row -->
     </tbody>
</table>
</br>

<!--###Table of Content -->

## Contents

<!-- MarkdownTOC depth=3 -->

- [Introduction](#introduction)
- [Operation Types](#operation-types)
  -  [Auth](#authentication)
  -  [Fiscalize](#fiscalize)
- [Consuming the SDK](#consuming-the-sdk)
  -  [Operation Types methods](#operation-types-methods)
	  -  [Authentication Method](#auth-method)
	  -  [Fiscalize Methods](#fiscalize-methods)
- [Appendix A - Native Authorization Protocol Messages](#appendix-a---native-authorization-protocol-messages)
<!-- /MarkdownTOC -->

## Introduction
The Ationet.Fiscal.API is an API that allows ATIOnet to be integrated with the different worldwide billing platforms. 
The ATIOnet Web platform consumes this API for billing and clearing processes natively.
ATIOnet exposes this API so that it can be consumed externally following the instructions found in
this reference manual.

## Operation Types

### Authentication
The authentication operation type is responsible for interacting with the Ationet STS authorization engine.

The STS authorization engine is the component that receives authorization requests and decides whether or not the transaction is approved.
To be able to make a successful authorization request, it is necessary to have a user registered in ATIOnet with specific roles for Fiscal API.

The authentication operation type will receive the username and password and return a bearer access token when the STS confirms that the information is correct and that the user has the right permissions. Otherwise it will deny access to the Fiscal API.


Without the authorization bearer token, none of the other operations of the Fiscal API can be executed. 

### Fiscal
The Fiscal Operation Type is the main operation of the Fiscal API.
This operation receives a JSON object with all the information necessary for the digital stamping of a fiscal document.

According to the transaction code received as a parameter, the Fiscal API has the ability to decide what kind of operation will be doing against a specific Fiscal Entity.

As a result, we will obtain the Fiscal ID for the document stamped and the corresponding PDF or XML document, depending on the Fiscal Entity.

For now, the only Fiscal Entity implemented is the SAT for Mexico, implemented through the Edifact company.

## Consuming the API
Aclaration: For all the examples we will be using Postman.

### API URL
To consume the Fiscal API you should point to this URL: fiscal.ationet.com 

---
### Authentication Methods

<table>
     <thead>
        <tr> 
			<td>Method</td>
			<td>Parameters</td>
			<td>Description</td>
			<td>Response</td>
		</tr>
     </thead>
     <tbody>
        <tr>
          	<td>Authenticate</td>
            <td>UserAuth</td>
            <td>Sends a <i>Authentication</i> message to the host. The Fiscal API will negociate the authentication bearer token with the ATIOnet STS.</td>
			<td>Token</td>
        </tr>
 	</tbody>
</table>
<b>UserAuth specification</b>
<br/>
<table>
	<thead>
		<tr>
			<td>Property</td>
			<td>Description</td>
			<td>Data Type</td>
			<td>Required</td>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>UserName</td>
			<td>ATIOnet provided username</td>
			<td>String</td>
			<td>Yes</td>
		</tr>
		<tr>
			<td>Password</td>
			<td>Password corresponding to the UserName.</td>
			<td>String</td>
			<td>Yes</td>
		</tr>
	</tbody>
</table>
<b>Token Result specification</b>
<table>
	<thead>
		<tr>
			<td>Property</td>
			<td>Description</td>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>AccessToken</td>
			<td>The authentication bearer access token unique id. This will be needed to consume the Fiscalize methods.</td>
		</tr>
		<tr>
			<td>TokenType</td>
			<td>The type of the token. Will be always bearer.</td>
		</tr>
		<tr>
			<td>ExpiresIn</td>
			<td>Indicates when the token will expire.</td>
		</tr>
		<tr>
			<td>RefreshToken</td>
			<td>No use for this property.</td>
		</tr>
	</tbody>
</table>
---
### Fiscal Methods
<table>
     <thead> 
        <tr>
			<td>Method</td>
			<td>Parameters</td>
			<td>Description</td>
			<td>Response</td>
		</tr>
     </thead>
     <tbody>
        <tr>
          	<td>Fiscalize</td>
            <td>FiscalizeRequest</td>
            <td>Sends a <i>Fiscalization</i> message to the host.</td>
			<td>FiscalizationResult</td>
        </tr>
	</tbody>
</table>
<b>FiscalizeRequest Class specification</b>
<br/>
<table>
	<thead>
		<tr>
			<td>Property</td>
			<td>Description</td>
			<td>Data Type</td>
			<td>Required</td>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>SystemModel</td>
			<td>Name of the application that is consuming the API.</td>
			<td>String</td>
			<td>Yes</td>
		</tr>
		<tr>
			<td>SystemVersion</td>
			<td>ATIOnet Fiscal api Version.</td>
			<td>String</td>
			<td>Yes</td>
		</tr>
		<tr>
			<td>MessageFormatVersion</td>
			<td>ATIOnet Fiscal api message format version</td>
			<td>String</td>
			<td>Yes</td>
		</tr>
		<tr>
			<td>TransactionCode</td>
			<td>The ATIOnet transaction code corresponding to a specific fiscal request. See <i>TransactionCodes Specifications.<i/></td>
			<td>String</td>
			<td>Yes</td>
		</tr>
		<tr>
			<td>NetworkId</td>
			<td>ATIOnet Network Id for the fiscal document sender data.</td>
			<td>String</td>
			<td>Yes</td>
		</tr>
		<tr>
			<td>NetworkCode</td>
			<td>ATIOnet Network Code for the fiscal document sender data.</td>
			<td>String</td>
			<td>Yes</td>
		</tr>
		<tr>
			<td>Id</td>
			<td>Fiscal document Id</td>
			<td>String</td>
			<td>Yes</td>
		</tr>
		<tr>
			<td>Number</td>
			<td>Fiscal document Number</td>
			<td>String</td>
			<td>Yes</td>
		</tr>
		<tr>
			<td>CustomerTaxPayerId</td>
			<td>Tax Payer Id for the fiscal document receiver data.</td>
			<td>String</td>
			<td>Yes</td>
		</tr>
		<tr>
			<td>CustomerBusinessName</td>
			<td>Business Name for the fiscal document receiver data.</td>
			<td>String</td>
			<td>Yes</td>
		</tr>
		<tr>
			<td>CustomerStreet</td>
			<td>Address Street for the fiscal document receiver data.</td>
			<td>String</td>
			<td>No</td>
		</tr>
		<tr>
			<td>CustomerZipCode</td>
			<td>Address Zip Code for the fiscal document receiver data.</td>
			<td>String</td>
			<td>Yes</td>
		</tr>
		<tr>
			<td>CustomerCity</td>
			<td>Address City for the fiscal document receiver data.</td>
			<td>String</td>
			<td>No</td>
		</tr>
		<tr>
			<td>CustomerState</td>
			<td>Address State for the fiscal document receiver data.</td>
			<td>String</td>
			<td>No</td>
		</tr>
		<tr>
			<td>CustomerCountry</td>
			<td>Address Country for the fiscal document receiver data.</td>
			<td>String</td>
			<td>No</td>
		</tr>
		<tr>
			<td>Date</td>
			<td>Fiscal document Date.</td>
			<td>Date</td>
			<td>Yes</td>
		</tr>
		<tr>
			<td>Currency</td>
			<td>Fiscal document amount currency.</td>
			<td>String</td>
			<td>Yes</td>
		</tr>
		<tr>
			<td>Net</td>
			<td>Fiscal document net amount.</td>
			<td>Decimal</td>
			<td>Yes</td>
		</tr>
		<tr>
			<td>SubTotal</td>
			<td>Fiscal document sub-total amount.</td>
			<td>Decimal</td>
			<td>Yes</td>
		</tr>
		<tr>
			<td>Discounts</td>
			<td>Fiscal document discounts amount.</td>
			<td>Decimal</td>
			<td>Yes</td>
		</tr>
		<tr>
			<td>Tax</td>
			<td>Fiscal document total tax amount.</td>
			<td>Decimal</td>
			<td>Yes</td>
		</tr>
		<tr>
			<td>Total</td>
			<td>Fiscal document total amount.</td>
			<td>Decimal</td>
			<td>Yes</td>
		</tr>
		<tr>
			<td>Transactions</td>
			<td>List of the Transactions assosiated with the Fiscal document. See the <i>Transactions specifications</i></td>
			<td>TransactionCollection</td>
			<td>Yes</td>
		</tr>
		<tr>
			<td>Taxes</td>
			<td>List of the Taxes associated with the Fiscal document. See the <i>Taxes specifications</i></td>
			<td>TaxCollection</td>
			<td>No</td>
		</tr>
	</tbody>
</table>
<b>Transaction specifications</b>
<br/>
<table>
	<thead>
		<tr>
			<td>Property</td>
			<td>Description</td>
			<td>Data Type</td>
			<td>Required</td>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>Code</td>
			<td>Transaction code in origin system.</td>
			<td>String</td>
			<td>Yes</td>
		</tr>
		<tr>
			<td>Date</td>
			<td>Transaction Date</td>
			<td>Date</td>
			<td>Yes</td>
		</tr>
		<tr>
			<td>ProductCode</td>
			<td>Transaction Product Code</td>
			<td>String</td>
			<td>Yes</td>
		</tr>
		<tr>
			<td>ProductName</td>
			<td>Transaction Product Name</td>
			<td>String</td>
			<td>Yes</td>
		</tr>
		<tr>
			<td>UnitPrice</td>
			<td>Transaction Product Unit Price</td>
			<td>Decimal</td>
			<td>Yes</td>
		</tr>
		<tr>
			<td>Quantity</td>
			<td>Transaction Product Quantity</td>
			<td>Decimal</td>
			<td>Yes</td>
		</tr>
		<tr>
			<td>Net</td>
			<td>Transaction Product Net Amount</td>
			<td>Decimal</td>
			<td>Yes</td>
		</tr>
		<tr>
			<td>SubTotal</td>
			<td>Transaction SubTotal</td>
			<td>Decimal</td>
			<td>Yes</td>
		</tr>
		<tr>
			<td>Total</td>
			<td>Transaction Total</td>
			<td>Decimal</td>
			<td>Yes</td>
		</tr>
		<tr>
			<td>UnitCode</td>
			<td>Transaction UnitCode.</td>
			<td>String</td>
			<td>Yes</td>
		</tr>
		<tr>
			<td>UnitDescription</td>
			<td>Transaction UnitDescription.</td>
			<td>String</td>
			<td>Yes</td>
		</tr>
		<tr>
			<td>SiteCode</td>
			<td>Transaction Site Code.</td>
			<td>String</td>
			<td>Yes</td>
		</tr>
		<tr>
			<td>Tax</td>
			<td>Transaction Tax.</td>
			<td>Decimal</td>
			<td>Yes</td>
		</tr>
		<tr>
			<td>Taxes</td>
			<td>List of the Transaction Taxes. <i>See Tax Specifications</i></td>
			<td>TaxCollection</td>
			<td>Yes</td>
		</tr>
	</tbody>
</table>
<b>FiscalizationResult specification</b>
<br/>
<table>
	<thead>
		<tr>
			<td>Property</td>
			<td>Description</td>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>FiscalId</td>
			<td>The Fiscal Id generated after the document Stamp in the Fiscal Entity.</td>
		</tr>
		<tr>
			<td>TransactionCode</td>
			<td>The ATIOnet transaction code corresponding to a specific fiscal request. See <i>TransactionCodes Specifications.<i/></td>
		</tr>
		<tr>
			<td>ResponseCode</td>
			<td>The transaction code that ATIOnet returns to a corresponding request. See <i>ResponseCodes Specifications.<i/></td>
		</tr>
		<tr>
			<td>ResponseText</td>
			<td>Fiscal API Response message.</td>
		</tr>
		<tr>
			<td>ExternalResponseCode</td>
			<td>Fiscal Entity response code.</td>
		</tr>
		<tr>
			<td>DigitalSignature</td>
			<td>The digital Signature of corresponding to the Stamp document.</td>
		</tr>
		<tr>
			<td>PDF</td>
			<td>Stamp document in PDF format returned by the Fiscal Entity.</td>
		</tr>
		<tr>
			<td>XML</td>
			<td>Stamp document in XML format returned by the Fiscal Entity.</td>
		</tr>
	</tbody>
</table>
<br/>
<b>TransactionCodes specifications</b>
<table>
	<thead>
		<tr>
			<td>Transaction Code</td>
			<td>Description</td>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>1500</td>
			<td>StatementRequest</td>
		</tr>
		<tr>
			<td>1510</td>
			<td>StatementResponse</td>
		</tr>
		<tr>
			<td>1520</td>
			<td>ClearingRequest</td>
		</tr>
		<tr>
			<td>1530</td>
			<td>ClearingResponse</td>
		</tr>
		<tr>
			<td>1540</td>
			<td>InvoiceRequest</td>
		</tr>
		<tr>
			<td>1550</td>
			<td>InvoiceResponse</td>
		</tr>
		<tr>
			<td>1560</td>
			<td>CreditNoteRequest</td>
		</tr>
		<tr>
			<td>1580</td>
			<td>CreditNoteResponse</td>
		</tr>
	</tbody>
</table>
<b>ResponseCodes specifications</b>
<br/>
<table>
	<thead>
		<tr>
			<td>Response Code</td>
			<td>Description</td>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>00000</td>
			<td>Sucess</td>
		</tr>
		<tr>
			<td>00001</td>
			<td>Error</td>
		</tr>
	</tbody>
</table>