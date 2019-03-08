![ationetlogo](Content/Images/ATIOnetLogo_250x70.png) 
# ATIOnet Supported Terminals List

> **About:** This documents list the Capture Terminals and Systems officially supported by ATIOnet.
Please refer to detailed information for specifics about each Terminal capabilities and requirements.	


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
			<td>AN-Supported_Terminals-TechGuide.md</td>
		</tr>
		<tr>
			<td align="right">Doc. Version:</td>
			<td>1.0</td>
		</tr>
		<tr>
			<td align="right">Release Date:</td>
			<td>20/July/2014</td>
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
        <!-- End of version table row -->
     </tbody>
</table>
</br>

<!-- ###Table of Content -->

<!-- Optional Terms & Definition section -->
        
### Definitions	

<dl>
 <dt>Terminal</dt>
  <dd>System or Device installed at the site responsible to perform the payment or purchase transaction capture and to communicate with ATIOnet</dd>
 <dt>FEP</dt>
 <dd>Front End Processor. Subsystem on the ATIOnet Host responsible to handle the interaction with one or more Terminal brands/models with a specific communication protocol.</dd>
</dl>

<!-- Content starts here -->
#### Disclaimer
Brand names, logos and trademarks used herein remain the property of their respective owners. This listing of any firm or their logos is not intended to imply any endorsement or direct affiliation with ATIO International LLC. 

The information contained herein is on an "as is" basis, without warranties or conditions of any kind, either express or implied, including, without limitation, any warranties or conditions of title, non-infringement, merchantability, or fitness for a particular purpose. You agree that you will not rely on and are solely responsible for determining the appropriateness of using the information provided on this web site and assume any risks associated with doing so.

## Supported Terminals

<table>
	<thead>
		<tr>
			<td>Type</td>
			<td>Brand</td>
			<td width=25%>Model</td>
			<td>Version</td>
			<td>FEP</td>
			<td width=30%>Comments</td>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>Indoor POS</td>
			<td>ControlGAS</td>
			<td>ControlGAS Wet&Dry POS</td>
			<td>1.0.8 and later</td>
			<td>Native</td>
			<td>Full online functionality. Offline operation when using ATIOnet Local Agent</td>
		</tr>
		<tr>
			<td>Outdoor POS</td>
			<td>ControlGAS</td>
			<td>ControlGAS Forecourt POS</td>	
			<td>4.10 and later</td>
			<td>Native</td>
			<td>Full online functionality. Offline operation when using ATIOnet Local Agent</td>
		</tr>
		<tr>
			<td>AVI</td>
			<td>ControlGAS</td>
			<td>ControlGAS w/Petratec's GPC</td>	
			<td>CG 4.10, GPC 6.0.4</td>
			<td>Native</td>
			<td>Online AVI identification with Ring TAGs. Offline operation when using ATIOnet Local Agent</td>
		</tr>
		<tr>
			<td>Site Controller</td>
			<td>Companytec</td>
			<td>CBC</td>	
			<td>06 and later</td>
			<td>Native</td>
			<td>Uses ATIOnet Local Agent. Dual identification Attendant and Cardholder using IdentifID cards</td>
		</tr>
		<tr>
			<td>Site Controller</td>
			<td>OPW FMS</td>
			<td>FSC-3000</td>	
			<td>10.0 and later</td>
			<td>Federated Network or ATIOnet Network</td>
			<td>May require an ATIOnet Gateway</td>
		</tr>
		<tr>
			<td>Site Controller</td>
			<td>ATIO International</td>
			<td>Nano CPI</td>	
			<td>2.0.0014 and later</td>
			<td>Native</td>
			<td>Uses ATIOnet Local Agent. May use retrofits for third-party OPTs or own OPT on selected Verifone Verix terminals</td>
		</tr>
		<tr>
			<td>Indoor POS</td>
			<td>Verifone</td>
			<td>Ruby Supersystem</td>	
			<td>Latest Latpak</td>
			<td>ISO 8583</td>
			<td>Requires a Verifone Card Controller v. </td>
		</tr>
		<tr>
			<td>Outdoor Terminal</td>
			<td>Verifone</td>	
			<td>IPT</td>	
			<td>N/A</td>
			<td>ISO 8583</td>
			<td>Requires a Verifone Card Controller v. </td>
		</tr>
		<tr>
			<td>Pay@Pump</td>
			<td>Verifone</td>
			<td>Secure Pump Payment </td>	
			<td>N/A</td>
			<td>ISO 8583</td>
			<td>Requires a Verifone Card Controller v. </td>
		</tr>
		<tr>
			<td>Indoor/Outdoor POS</td>
			<td>Verifone</td>
			<td>Stand-Alone Payment Terminal</td>	
			<td></td>
			<td>ISO 8583</td>
			<td>N/A</td>
		</tr>
	</tbody>
</table>
