![ationetlogo](Content/Images/ATIOnetLogo_250x70.png) 
# ATIONet Native Authorization Protocol Messages 
> **About:** This document describes each messages from the Authorization protocol, stating which field is optional and which one isn't.	

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
			<td>AN-Native_Auth_Protocol_Messages</td>
		</tr>
		<tr>
			<td align="right">Doc. Version:</td>
			<td>1.0</td>
		</tr>
		<tr>
			<td align="right">Release Date:</td>
			<td>17, January 2019</td>
		</tr>
		<tr>
			<td align="right">Author:</td>
			<td>ATIONet LLC</td>
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
          	<td>17/January/2019</td>
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

- [Authorization Protocol messages](#authorization-protocol-messages)

<!-- /MarkdownTOC -->

## Introduction
The ATIONet authorization engine exposes an API with a set of commands to perform any operation available in the platform. The table below describes field by field, what should be sent and what is expected to be received.

## Authorization Protocol messages
<table border="1">
	<thead>
		<tr valign="top">
			<th align="left" rowspan="2" valign="middle">
				Value
			</th>
			<th align="left" rowspan="2" valign="middle">
				Description
			</th>
		</tr>	
	</thead>
	<tbody>
		<tr valign="top">
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">Mandatory</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">M1</p>
			</td>
			<td>
				<p align="left">Mandatory. The same as original request</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">M2</p>
			</td>
			<td>
				<p align="left">Mandatory. The same as pre-authorization</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">Echo</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">E1</p>
			</td>
			<td>
				<p align="left">Echo from original request</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left">Optional</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">C</p>
			</td>
			<td>
				<p align="left">Conditional</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">C1</p>
			</td>
			<td>
				<p align="left">At least one field must be send</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">C2</p>
			</td>
			<td>
				<p align="left">Mandatory if product quantity is present</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">C3</p>
			</td>
			<td>
				<p align="left">At least one field must be sent. The same as original request</p>
			</td>
		</tr>
	</tbody>
</table>
</br>	
<table border="1">
	<thead>
		<tr valign="top">
			<th align="left" rowspan="2" valign="middle">
				Field Name
			</th>
			<th align="left" rowspan="2" valign="middle">
				Size
			</th>
			<th align="left" rowspan="2" valign="middle">
				Type
			</th>
			<th align="left" colspan="2">
				Pre-authorization
			</th>
			<th align="left" colspan="2">
				Completion
			</th>
			<th align="left" colspan="2">
				Contingency
			</th>
			<th align="left" colspan="2">
				Offline
			</th>
			<th align="left" colspan="2">
				Cancellation
			</th>
			<th align="left" colspan="2">
				Void
			</th>
		</tr>
		<tr valign="top">
			<th align="left">
				Request
			</th>
			<th align="left">
				Response
			</th>
			<th align="left">
				Request
			</th>
			<th align="left">
				Response
			</th>
			<th align="left">
				Request
			</th>
			<th align="left">
				Response
			</th>
			<th align="left">
				Request
			</th>
			<th align="left">
				Response
			</th>
			<th align="left">
				Request
			</th>
			<th align="left">
				Response
			</th>
			<th align="left">
				Request
			</th>
			<th align="left">
				Response
			</th>
		</tr>
	</thead>
	<tbody>
		<tr valign="top">
			<td>
				<p align="left">ApplicationType</p>
			</td>
			<td>
				<p align="left">3</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E1</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E1</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ProcessingMode</p>
			</td>
			<td>
				<p align="left">1</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E1</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E1</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">MessageFormatVersion</p>
			</td>
			<td>
				<p align="left">3</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E1</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E1</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">TerminalIdentification</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E1</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E1</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">DeviceTypeIdentifier</p>
			</td>
			<td>
				<p align="left">1</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E1</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E1</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SystemModel</p>
			</td>
			<td>
				<p align="left">10</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SystemVersion</p>
			</td>
			<td>
				<p align="left">10</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">TransactionCode</p>
			</td>
			<td>
				<p align="left">3</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">100</p>
			</td>
			<td>
				<p align="left">110</p>
			</td>
			<td>
				<p align="left">120</p>
			</td>
			<td>
				<p align="left">130</p>
			</td>
			<td>
				<p align="left">126</p>
			</td>
			<td>
				<p align="left">130</p>
			</td>
			<td>
				<p align="left">125</p>
			</td>
			<td>
				<p align="left">130</p>
			</td>
			<td>
				<p align="left">400</p>
			</td>
			<td>
				<p align="left">410</p>
			</td>
			<td>
				<p align="left">220</p>
			</td>
			<td>
				<p align="left">230</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">AccountType</p>
			</td>
			<td>
				<p align="left">1</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E1</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E1</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">EntryMethod</p>
			</td>
			<td>
				<p align="left">1</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E1</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E1</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ServiceCode</p>
			</td>
			<td>
				<p align="left">1</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">PumpNumber</p>
			</td>
			<td>
				<p align="left">2</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">E1</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">E1</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ProductCode</p>
			</td>
			<td>
				<p align="left">4</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left">C</p>
			</td>
			<td>
				<p align="left">C2</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">C2</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">C2</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ProductUnitPrice</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">decimal</p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left">C</p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ProductNetAmount</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">decimal</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ProductTaxes</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">Dictionary[string, decimal]</p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">0</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ProductAmount</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">decimal</p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left">C</p>
			</td>
			<td>
				<p align="left">C1</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">C1</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">C1</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ProductQuantity</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">decimal</p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left">C</p>
			</td>
			<td>
				<p align="left">C1</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">C1</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">C1</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">TransactionNetAmount</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">decimal</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ProductData</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">List[AtionetProduct]</p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">TransactionAmount</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">decimal</p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left">C</p>
			</td>
			<td>
				<p align="left">C1</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">C1</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">C1</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">UnitCode</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CurrencyCode</p>
			</td>
			<td>
				<p align="left">3</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">BatchNumber</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">int</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ShiftNumber</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">TransactionSequenceNumber</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">int</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M1</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M1</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">LocalTransactionDate</p>
			</td>
			<td>
				<p align="left">8</p>
			</td>
			<td>
				<p align="left">int</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">LocalTransactionTime</p>
			</td>
			<td>
				<p align="left">6</p>
			</td>
			<td>
				<p align="left">int</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">PrimaryTrack</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">PrimaryPIN</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SecondaryTrack</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SecondaryPIN</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CustomerData</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">Dictionary[string, string]</p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left">C</p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">TransactionExtendedData</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td valign="middle" rowspan="4">
				<p align="left">OriginalData</p>
				<p align="left">---> TransactionCode</p>
				<p align="left">---> LocalTransactionDate</p>
				<p align="left">---> LocalTransactionTime</p>
			</td>
			<td valign="top" rowspan="4">
				<p align="left">Var</p>
			</td>
			<td valign="top" rowspan="4">
				<p align="left">Dictionary[string, string]</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">M1</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">M1</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">C3</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">C3</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">C3</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">C3</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">AuthorizationCode</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">M2</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">C3</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">C3</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">InvoiceNumber</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ResponseCode</p>
			</td>
			<td>
				<p align="left">5</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ResponseText</p>
			</td>
			<td>
				<p align="left">20</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ReceiptData</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
	</tbody>
</table>	
</br>	
<table border="1">
	<thead>
		<tr valign="top">
			<th align="left" rowspan="2" valign="middle">
				Field Name
			</th>
			<th align="left" rowspan="2" valign="middle">
				Size
			</th>
			<th align="left" rowspan="2" valign="middle">
				Type
			</th>
			<th align="left" colspan="2">
				Sale
			</th>
			<th align="left" colspan="2">
				Offline
			</th>
			<th align="left" colspan="2">
				Refund
			</th>
			<th align="left" colspan="2">
				Cancellation
			</th>
			<th align="left" colspan="2">
				Void
			</th>
		</tr>
		<tr valign="top">
			<th align="left">
				Request
			</th>
			<th align="left">
				Response
			</th>
			<th align="left">
				Request
			</th>
			<th align="left">
				Response
			</th>
			<th align="left">
				Request
			</th>
			<th align="left">
				Response
			</th>
			<th align="left">
				Request
			</th>
			<th align="left">
				Response
			</th>
			<th align="left">
				Request
			</th>
			<th align="left">
				Response
			</th>
		</tr>
	</thead>
	<tbody>
		<tr valign="top">
			<td>
				<p align="left">ApplicationType</p>
			</td>
			<td>
				<p align="left">3</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E1</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E1</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ProcessingMode</p>
			</td>
			<td>
				<p align="left">1</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E1</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E1</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">MessageFormatVersion</p>
			</td>
			<td>
				<p align="left">3</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E1</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E1</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">TerminalIdentification</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E1</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E1</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">DeviceTypeIdentifier</p>
			</td>
			<td>
				<p align="left">1</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E1</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E1</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SystemModel</p>
			</td>
			<td>
				<p align="left">10</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SystemVersion</p>
			</td>
			<td>
				<p align="left">10</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">TransactionCode</p>
			</td>
			<td>
				<p align="left">3</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">200</p>
			</td>
			<td>
				<p align="left">210</p>
			</td>
			<td>
				<p align="left">205</p>
			</td>
			<td>
				<p align="left">210</p>
			</td>
			<td>
				<p align="left">203</p>
			</td>
			<td>
				<p align="left">210</p>
			</td>
			<td>
				<p align="left">400</p>
			</td>
			<td>
				<p align="left">410</p>
			</td>
			<td>
				<p align="left">220</p>
			</td>
			<td>
				<p align="left">230</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">AccountType</p>
			</td>
			<td>
				<p align="left">1</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E1</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E1</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">EntryMethod</p>
			</td>
			<td>
				<p align="left">1</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E1</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E1</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ServiceCode</p>
			</td>
			<td>
				<p align="left">1</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">PumpNumber</p>
			</td>
			<td>
				<p align="left">2</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">E1</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">E1</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ProductCode</p>
			</td>
			<td>
				<p align="left">4</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">C2</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">C2</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">C2</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ProductUnitPrice</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">decimal</p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ProductNetAmount</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">decimal</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ProductTaxes</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">Dictionary[string, decimal]</p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ProductAmount</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">decimal</p>
			</td>
			<td>
				<p align="left">C1</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">C1</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">C1</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ProductQuantity</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">decimal</p>
			</td>
			<td>
				<p align="left">C1</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">C1</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">C1</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">TransactionNetAmount</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">decimal</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ProductData</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">List[AtionetProduct]</p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">TransactionAmount</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">decimal</p>
			</td>
			<td>
				<p align="left">C1</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">C1</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">C1</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">UnitCode</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CurrencyCode</p>
			</td>
			<td>
				<p align="left">3</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">BatchNumber</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">int</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ShiftNumber</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">TransactionSequenceNumber</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">int</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M1</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M1</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">LocalTransactionDate</p>
			</td>
			<td>
				<p align="left">8</p>
			</td>
			<td>
				<p align="left">int</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">LocalTransactionTime</p>
			</td>
			<td>
				<p align="left">6</p>
			</td>
			<td>
				<p align="left">int</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">PrimaryTrack</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">PrimaryPIN</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SecondaryTrack</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">SecondaryPIN</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">CustomerData</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">Dictionary[string, string]</p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">O</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">TransactionExtendedData</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td valign="middle" rowspan="4">
				<p align="left">OriginalData</p>
				<p align="left">---> TransactionCode</p>
				<p align="left">---> LocalTransactionDate</p>
				<p align="left">---> LocalTransactionTime</p>
			</td>
			<td valign="top" rowspan="4">
				<p align="left">Var</p>
			</td>
			<td valign="top" rowspan="4">
				<p align="left">Dictionary[string, string]</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">M1</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">M1</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">C3</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">C3</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">C3</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">C3</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">AuthorizationCode</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">C3</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
			<td>
				<p align="left">C3</p>
			</td>
			<td>
				<p align="left">E</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">InvoiceNumber</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ResponseCode</p>
			</td>
			<td>
				<p align="left">5</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ResponseText</p>
			</td>
			<td>
				<p align="left">20</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left">M</p>
			</td>
		</tr>
		<tr valign="top">
			<td>
				<p align="left">ReceiptData</p>
			</td>
			<td>
				<p align="left">Var</p>
			</td>
			<td>
				<p align="left">string</p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
			<td>
				<p align="left"></p>
			</td>
		</tr>
	</tbody>
</table>  
