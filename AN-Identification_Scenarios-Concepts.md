![ationetlogo](Content/Images/ATIOnetLogo_250x70.png) 
# ATIOnet Identification Scenarios

> **About:** This document describes the different possible combinations of steps and data request procedures to identify a cardholder that can be implemented on ATIOnet.
These capabilities may vary according to the capture device, protocol and susbscription model.  		

</br>

<table>
	<thead>
		<tr>
			<td colspan="2" class="tablehead">Document Information</td>
		</tr>
	</thead>
	<tfoot>
		<td colspan="2"> </td>
	</tfoot>
	<tbody>
		<tr>
			<td width="20%" class="rowhead" align="right">File:</td>
			<td>AN-Identification_Scenarios-Concepts</td>
		</tr>
		<tr>
			<td align="right">Doc. Version:</td>
			<td>1.0</td>
		</tr>
		<tr>
			<td align="right">Release Date:</td>
			<td>20, July 2014</td>
		</tr>
		<tr>
			<td align="right">Author:</td>
			<td>ATIO International LLC</td>
		</tr>
	</tbody>
</table>

<table>
     <thead>
          <tr>
          	<td colspan="3">Change Log</td>
          </tr>
     </thead>
     <tfoot>
          <td colspan="3"> </td>
     </tfoot>
     <tbody>
        <tr>
          	<td>Ver.</td>
            <td>Date</td>
            <td>Change summary</td>
        </tr>
        <!-- Insert a table row like this for each version -->
        <tr>
          	<td>1.0</td>
          	<td>20/July/2014</td>
          	<td>Initial version</td>
        </tr>
        <tr>
            <td>1.1</td>
            <td>06/August/2014</td>
            <td>Splitted some scenarios to clarity</td>
        </tr>
        <!-- End of version table row -->
     </tbody>
</table>
</br>

### Table of Content
<!-- MarkdownTOC depth=3 -->

- Definitions
- Overview
- Identifications and Prompts
- Relevant Configuration
  - Prompting Rules
  - Terminal / Controller Configuration
  - Enforced Vehicle-Driver relation
- Use of PINs
- Scenarios

<!-- /MarkdownTOC -->


<!-- Optional Terms & Definition section -->
        
### Definitions	

<dl>
  <dt>Terminal</dt>
  <dd>The device or system in charge of handling the interaction with the cardholder and/or the attendant and, eventually, controlling the fuel delivery.</dd>
  <dt>Cardholder</dt>
  <dd>The person, vehicle or unit that is identified as the subject of the transaction</dd>
  <dt>Sub-account</dt>
  <dd>A particular account whithin a Contract with an assigned balance</dd>
  <dt>Identification</dt>
  <dd>Any mean to identify a cardholder regardless of the technology involved. It can be any type of media support or piece of information presented to a capture device in order to identify a cardholder</dd>

</dl>

<!-- Content starts here -->
## Overview
Every transaction on ATIOnet starts with a secure identification of a sub-account to be affected (debit or credit) by the transaction. A sub-account can be a Vehicle -or broadly a Unit- or a Driver -broadly a Person.
On ATIOnet, every transaction impacts a single sub-account, it is called a sub-account because it is always part of a Contrat (its parent account). It is common to request two Identifications on the same transaction, usually to identify the Vehicle and the Driver or viceversa.

On ATIOnet Native Transaction Protocol, there are two sets of Identification fields, a Primary ID and a Secondary ID; it is up to the Terminal to decide which one is Primary or Secondary but the common practice is to send the ID presented first as the Primary. Most of the Terminals have the capability to capture a second ID and send it as a prompt on the authorization request. ATIOnet is capable of taking such prompt and processing it as a the secondary Identification.

It is important to note that only the sub-account linked to the Primary Identification will have their balance affected by the transaction; the Secondary Identification will be used to perform a two-fold identification capture and may have the related entities affected on its statistics and counters (like quotas or mileage calculation) but the money or volume sold will be accounted to the Primary sub-account only.

## Identifications and Prompts

In ATIOnet's language, an **Identification** is the generic name given to any media support, device, or piece of information that could be used to identify a card-holder at transaction-capture time, for example magnetic cards, chipkeys, read-only TAGs, smart-cards, read/write TAGs, 1D and 2D bardcodes, eButtons, and manually-entered codes.</br>
ATIOnet implements specific features for certain identification technologies, like the Vehicle Installation Flow for AVI's ring TAGs, or reusable and embossable attributes; but the minimum common functionality is that the Terminal is responsible to capture and send the proper Identification ID.

A **Prompt** is a piece of data captured at the site during transaction capture. Prompts are conditional, meaning that can be required or not by ATIOnet to process a transaction request, depending on a combination of configuration and/or business rules. If the Terminal fails to send all required Prompts for a given transaction request, ATIOnet responds with a specific decline code and message, also including the list of prompts that must be sent for the transaction. The Terminal should process the response and re-send the request with the complete information. Prompts usually are codes or values manually entered at the Terminal, but could be preconfigured or calculated values at the Terminal, or directly captured from the Identification media or device.</br>
Common prompts include Truck ID, Trailer ID, Odometer and Engine hours, known as _Customer data_. But some prompts are related to the identification of the cardholder, as Driver ID and Vehicle ID. 

Certain combinations of operation conditions and a business rules cause that a Prompt is treated as an Identification or a part of an Identification. For example, if a Vehicle is configured to require dual identification (Vehicle plus Driver), ATIOnet expects both the Primary and Secondary tracks to be present on the request or the transaction. But if the terminal system does not support two card swipes, the Terminal in ATIOnet may be configured to use the ```Driver ID``` prompt as the Driver's Identification Track.



## Relevant Configuration

### Prompting Rules
Some prompts, when enforced via Rules, can help with the Identification.
Terminals supporting re-prompt functionality can activate prompts of missing information dinamically reacting to specific decline codes received from the Host.

<dl>
  <dt>Truck Number</dt>
  <dd>Vehicle ID (Unit Code)</dd>
  <dt>Vehicle PIN</dt>
  <dd>Secure numeric value associated to the Vehicle</dd>
  <dt>Driver ID</dt>
  <dd>Driver Identification number, must match the Driver Code on the system</dd>
  <dt>Driver PIN</dt>
  <dd>Secure number associated to the Driver</dd>
</dl>

> **Note about Vehicle and Driver ID data-type:** ATIOnet supports alphanumeric values in Vehicles and Drivers, but if you plan to use them as IDs, take into consideration that most capture terminals don't accept string input on those prompts, so numeric-only values should be used instead.

### Terminal / Controller Configuration
The flag ```Use Driver Id as Driver Card Track``` parameter forces the system to pass the Driver ID prompt as a Secondary Track (secondary identification), instead of taking it as an information-only prompt. This is useful to implement a two-fold authentication on terminals that doesn't accept dual card-swipe.

### Enforced Vehicle-Driver relation
Vehicle can be linked to one or more Drivers and viceversa from the Vehicle and Driver administration tools. When the Primary sub-account is linked to another, ATIOnet will automatically enforce a two-fold authentication, meaning that both the Vehicle and the Driver should be identified successfully at capture time and the relation must be satisfied in order for the transaction to be approved.

## Use of PINs
PINs are not an identification per-se, they are supporting mechanisms to validate that the individual present at capture time is rightfully in posession of the Vehicle and/or Driver ID numbers. Meaning that the actual data to be used as the record locators are the Vehicle ID or the Driver ID, the PINs only add a security layer on top of a solely manual entry.
Although the parameter is ```Vehicle PIN``` or ```Driver PIN```, the PIN is actually tied to the Identification (the card, hard-key, token, manual-entry etc.) and not directly to the Vehicle or Driver

## Scenarios

<table>
  <thead>
    <tr>
      <td width=40%>Scenario</td>
      <td>Description / Configuration strategy & Comments</td>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Single Vehicle</td>
      <td>Only the Vehicle Identification is required.Assign at least one Identification to a Vehicle-type sub-account</td>
    </tr>
    <tr>
      <td>Single Driver</td>
      <td>Assign at least one Identification to a Driver-type sub-account</td>
    </tr>
    <tr>
      <td>Dual ID, Vehicle(s) enabled for a/some Driver(s)</td>
      <td>Configure a relation between the Vehicle(s) and the Driver(s). The Vehicle's balances, cummmulators, counters and mileage will be impacted; for the Driver, only their cummulators will be affected</td>
    </tr>
    <tr>
      <td>Dual ID, Driver(s) authorized for a/some Vehicle(s)</td>
      <td>Configure a relation between the Drivers(s) and the Vehicles(s). The Driver(s) balances, cummmulators and counters will be impacted; to the Vehicles, only their cummulators and mileage will be modified. Only applies to Terminals with dual swipe capability</td>
    </tr>
    <tr>
      <td>Single Vehicle card with manual entry of Driver ID</td>
      <td>Transaction is completed against Vehicle's sub-account, Driver ID is informative</td>
    </tr>
    <tr>
      <td>Dual ID, Vehicle card with Driver ID manual prompt</td>
      <td>If Terminal is configured to pass Driver ID as a secondary track, functions as a full dual ID scenario, validating the Vehicle ID and the Driver ID, if there are Vehicle/Driver relations configured those will be enforced.</td>
    </tr>
    <tr>
      <td>Vehicle ID or Vehicle card plus Vehicle PIN</td>
      <td>PIN entry used as an entry validation, it has to match the PIN for the Identification presented for the Vehicle. On a single Driver Identification scenario, where the Vehicle ID is not required, if the Vehicle ID prompt is active the content of the field is ignored, as there is no Vehicle ID to validate.</td>
    </tr>
    <tr>
      <td>Driver ID or Driver card plus Driver PIN</td>
      <td>Same as Vehicle case above, but applies to a Driver-type ID and sub-accounts</td>
    </tr>
  </tbody>
</table>

