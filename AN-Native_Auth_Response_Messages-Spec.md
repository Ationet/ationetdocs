![ationetlogo](Content/Images/ATIOnetLogo_250x70.png)
# ATIONet - Authorization Response Messages

<table>
	<tr>
		<th colspan="2" align="left">Document Information</th>
	</tr>
	<tr>
		<td>Archivo:</td>
		<td>AN-Native_Auth_Response_Messages-Spec</td>
	</tr>
	<tr>
		<td>Version documento:</td>
		<td>1.0</td>
	</tr>
	<tr>
		<td>Date:</td>
		<td>February 3rd 2016</td>
	</tr>
	<tr>
		<td>Autor:</td>
		<td>ATIO International LLC</td>
	</tr>
</table>

<table>
	<tr>
		<th colspan="3" align="left">Change Log</th>
	</tr>
	<tr>
		<td>Ver.</td>
		<td>Date</td>
		<td>Change Log</td>
	</tr>
	<tr valign="top">
		<td>1.0</td>
		<td>February 3rd 2016</td>
		<td>Initial version.</td>
	</tr>
</table>

<table>

<tr>
	<th align="center">Code</th>
	<th align="center">Short Message</th>
	<th align="center">Long Message</th>
	<th align="center">Reason</th>
</tr>
<tr><td>00000</td>	<td>Authorized</td><td>Authorized</td><td>The transaction has been authorized</td></tr>
<tr><td>10000</td>	<td>Invalid Date</td><td>Invalid Date </td><td>One of the provided dates is invalid or has an invalid format</td></tr>
<tr><td>10001</td>	<td>Invalid Time</td><td>Invalid Time </td><td>One of the provided times is invalid or has an invalid format</td></tr>
<tr><td>10002</td>	<td>Invalid Seq num</td><td>Invalid Sequence num</td><td></td></tr>
<tr><td>10003</td>	<td>Invalid Acc type</td><td>Invalid Account type</td><td></td></tr>
<tr><td>10004</td>	<td>Invalid App type</td><td>Invalid Application type</td><td></td></tr>
<tr><td>10005</td>	<td>Invalid Proc mode</td><td>Invalid Processing mode</td><td></td></tr>
<tr><td>10006</td>	<td>Invalid Mess format</td><td>Invalid Message format</td><td></td></tr>
<tr><td>10007</td>	<td>Invalid Dev type</td><td>Invalid Device type</td><td></td></tr>
<tr><td>10008</td>	<td>Invalid Sys model</td><td>Invalid System model</td><td></td></tr>
<tr><td>10009</td>	<td>Invalid Sys ver	Invalid</td><td> System version</td><td></td></tr>
<tr><td>10010</td>	<td>Invalid Entry method</td><td>Invalid Entry method</td><td></td></tr>
<tr><td>10011</td>	<td>Invalid Unit code</td><td>Invalid Unit code</td><td></td></tr>
<tr><td>10012</td>	<td>Invalid DateTime</td><td>Invalid DateTime</td><td></td></tr>
<tr><td>10013</td>	<td>Invalid Pri track</td><td>Invalid Primary track</td><td></td></tr>
<tr><td>10014</td>	<td>Invalid Prod data</td><td>Invalid Product data</td><td></td></tr>
<tr><td>10015</td>	<td>Prod data req</td><td>Product Data Required</td><td></td></tr>
<tr><td>10016</td>	<td>Invalid Batch number</td><td>Invalid Batch number</td><td></td></tr>
<tr><td>10017</td>	<td>Invalid Respone code</td><td>Invalid Respone code</td><td></td></tr>
<tr><td>10018</td>	<td>Invalid Terminal</td><td>Invalid Terminal </td><td></td></tr>
<tr><td>11000</td>	<td>Merch not found</td><td>Merchant not found</td><td></td></tr>
<tr><td>11001</td>	<td>NetMerch not found</td><td>Network Merchant not found</td><td></td></tr>
<tr><td>11002</td>	<td>Site not found</td><td>Site not found</td><td></td></tr>
<tr><td>11003</td>	<td>Prot not found</td><td>Protocol not found</td><td></td></tr>
<tr><td>11004</td>	<td>TType not found</td><td>Terminal Type not found</td><td></td></tr>
<tr><td>11005</td>	<td>Fuel mapping needed</td><td>Fuel mapping needed</td><td></td></tr>
<tr><td>11006</td>	<td>Fuel not found</td><td>Fuel not found</td><td></td></tr>
<tr><td>11007</td>	<td>Comp not found</td><td>Company not found</td><td></td></tr>
<tr><td>11008</td>	<td>NetComp not found</td><td>Network Company not found</td><td></td></tr>
<tr><td>11009</td>	<td>Contr not found</td><td>Contract not found</td><td></td></tr>
<tr><td>11010</td>	<td>Subacc not found</td><td>Sub account not found</td><td></td></tr>
<tr><td>11011</td>	<td>SecSubacc not found</td><td>Secondary Sub account not found</td><td></td></tr>
<tr><td>11012</td>	<td>Veh or dri not found</td><td>Vehicle or driver not found</td><td></td></tr>
<tr><td>11013</td>	<td>Empty subaccount</td><td>Empty sub account</td><td></td></tr>
<tr><td>11014</td>	<td>Empty sec subaccount</td><td>Empty secondary sub account</td><td></td></tr>
<tr><td>11015</td>	<td>Fuel needed</td><td>Fuel needed</td><td></td></tr>
<tr><td>11016</td>	<td>Fuel not in contr</td><td>Fuel not in contract</td><td></td></tr>
<tr><td>11017</td>	<td>Fuel not in vehclas</td><td>Fuel not in vehicle class</td><td></td></tr>
<tr><td>11018</td>	<td>Comp money needed</td><td>Company money needed</td><td></td></tr>
<tr><td>11019</td>	<td>Merch money needed</td><td>Merchant money needed</td><td></td></tr>
<tr><td>11020</td>	<td>Comp qty needed</td><td>Company quantity needed</td><td></td></tr>
<tr><td>11021</td>	<td>Merch qty needed</td><td>Merchant quantity needed</td><td></td></tr>
<tr><td>11022</td>	<td>Fleet not found</td><td>Fleet not found</td><td></td></tr>
<tr><td>11023</td>	<td>Trans not found</td><td>Transaction not found</td><td></td></tr>
<tr><td>12000</td>	<td>Auth amount exceeded</td><td>Authorized amount exceeded</td><td></td></tr>
<tr><td>12001</td>	<td>Auth qty exceeded</td><td>Authorized quantity exceeded</td><td></td></tr>
<tr><td>12002</td>	<td>Auth with diff PPU</td><td>Authorization with different PPU</td><td></td></tr>
<tr><td>12003</td>	<td>Tr amount exceeded</td><td>Transaction amount exceeded</td><td></td></tr>
<tr><td>13000</td>	<td>Term does not exist</td><td>Terminal does not exist</td><td></td></tr>
<tr><td>13001</td>	<td>Netw does not exist</td><td>Network does not exist</td><td></td></tr>
<tr><td>13002</td>	<td>Id does not exist</td><td>Id does not exist</td><td></td></tr>
<tr><td>13003</td>	<td>SecId does not exist</td><td>Secondary Id does not exist</td><td></td></tr>
<tr><td>13004</td>	<td>Both veh ids</td><td>Both are vehicle identifications</td><td></td></tr>
<tr><td>13005</td>	<td>Both driv ids</td><td>  	Both are driver identifications</td><td></td></tr>
<tr><td>13006</td>	<td>Subacc in diff cont</td><td>Sub account in different contract</td><td></td></tr>
<tr><td>13007</td>	<td>Id is not active</td><td>Identification is not active</td><td></td></tr>
<tr><td>13008</td>	<td>Id has expired</td><td>Identification has expired</td><td></td></tr>
<tr><td>13009</td>	<td>SecId is not active</td><td>Secondary identification is not active</td><td></td></tr>
<tr><td>13010</td>	<td>SecId has expired</td><td>Secondary identification has expired</td><td></td></tr>
<tr><td>13011</td>	<td>Vehicle not enabled</td><td>Vehicle not enabled</td><td></td></tr>
<tr><td>13012</td>	<td>Driver not enabled</td><td>Driver not enabled</td><td></td></tr>
<tr><td>13013</td>	<td>Contract has expired</td><td>Contract has expired</td><td></td></tr>
<tr><td>13014</td>	<td>Site not in contr</td><td>Site not in contract</td><td></td></tr>
<tr><td>13015</td>	<td>Driver Needed</td><td>Driver Needed</td><td></td></tr>
<tr><td>13016</td>	<td>Driver not related</td><td>Driver not related</td><td></td></tr>
<tr><td>13017</td>	<td>Vehicle Needed</td><td>Vehicle Needed</td><td></td></tr>
<tr><td>13018</td>	<td>Vehicle not related</td><td>Vehicle not related</td><td></td></tr>
<tr><td>13019</td>	<td>Duplicate TSN</td><td>Duplicate TSN</td><td></td></tr>
<tr><td>13020</td>	<td>Retry does not match</td><td>Retry does not match</td><td></td></tr>
<tr><td>13021</td>	<td>Auth does not exist</td><td>Authorization does not exist</td><td></td></tr>
<tr><td>13022</td>	<td>Auth not authorized</td><td>Authorization not authorized</td><td></td></tr>
<tr><td>13023</td>	<td>Auth with diff secid</td><td>Authorization with different secondary id</td><td></td></tr>
<tr><td>13024</td>	<td>Auth with diff id</td><td>Authorization with different id</td><td></td></tr>
<tr><td>13025</td>	<td>Auth with diff fuel</td><td>Authorization with different fuel</td><td></td></tr>
<tr><td>13026</td>	<td>Auth with diff term</td><td>Authorization with different terminal</td><td></td></tr>
<tr><td>13027</td>	<td>Auth with diff netw</td><td>Authorization with different network</td><td></td></tr>
<tr><td>13028</td>	<td>Auth with diff merch</td><td>Authorization with different merchant</td><td></td></tr>
<tr><td>13029</td>	<td>Auth with diff nwmr</td><td>Authorization with different network-merchant</td><td></td></tr>
<tr><td>13030</td>	<td>Auth with diff site</td><td>Authorization with different site</td><td></td></tr>
<tr><td>13031</td>	<td>Auth with diff prot</td><td>Authorization with diff protocol</td><td></td></tr>
<tr><td>13032</td>	<td>Auth with diff tt</td><td>Authorization with different terminal type</td><td></td></tr>
<tr><td>13033</td>	<td>Auth with diff comp</td><td>Authorization with different company</td><td></td></tr>
<tr><td>13034</td>	<td>Auth with diff nwcp</td><td>Authorization with diff network-company</td><td></td></tr>
<tr><td>13035</td>	<td>Auth with dif contr</td><td>Authorization with different contract</td><td></td></tr>
<tr><td>13036</td>	<td>Auth with diff subacc</td><td>Authorization with different sub account</td><td></td></tr>
<tr><td>13037</td>	<td>Auth with dif sec sa</td><td>Authorization with different secondary sub account</td><td></td></tr>
<tr><td>13038</td>	<td>Auth with diff vehicle</td><td>Authorization with different vehicle</td><td></td></tr>
<tr><td>13039</td>	<td>Auth with diff driver</td><td>Authorization with different driver</td><td></td></tr>
<tr><td>13040</td>	<td>Not contingency Auth</td><td>Not a contingency authorization</td><td></td></tr>
<tr><td>14000</td>	<td>CA movement declined</td><td>Current account movement declined</td><td></td></tr>
<tr><td>14001</td>	<td>Merchant CA mov dec</td><td>Merchant current account movement declined</td><td></td></tr>
<tr><td>20000</td>	<td>Unit price needed</td><td>Unit price needed</td><td></td></tr>
<tr><td>20001</td>	<td>Max quota not set</td><td>Maximum quiota not set</td><td></td></tr>
<tr><td>40000</td>	<td>Insufficient balance</td><td>Insufficient balance</td><td></td></tr>
<tr><td>40001</td>	<td>Unable prods auth</td><td>Unable to authorize by product</td><td></td></tr>
<tr><td>40002</td>	<td>Veh-class qty exc</td><td>Vahicle class tank capacity excedeed</td><td></td></tr>
<tr><td>40003</td>	<td>TType qty exc</td><td>Terminal type quantity excedeed</td><td></td></tr>
<tr><td>40004</td>	<td>Term qty excedeed</td><td>Terminal quantity excedeed</td><td></td></tr>
<tr><td>40005</td>	<td>Term money excedeed</td><td>Terminal money excedeed</td><td></td></tr>
<tr><td>40006</td>	<td>Offline lim excedeed</td><td>Offline limit excedeed</td><td></td></tr>
<tr><td>40100</td>	<td>Site not authorized</td><td>Site not authorized</td><td></td></tr>
<tr><td>40101</td>	<td>Site not authorized</td><td>Site not authorized</td><td></td></tr>
<tr><td>40102</td>	<td>Site not authorized</td><td>Site not authorized</td><td></td></tr>
<tr><td>40103</td>	<td>Site not authorized</td><td>Site not authorized</td><td></td></tr>
<tr><td>40200</td>	<td>Fuel not authorized</td><td>Fuel not authorized</td><td></td></tr>
<tr><td>40201</td>	<td>Fuel not authorized</td><td>Fuel not authorized</td><td></td></tr>
<tr><td>40202</td>	<td>Fuel not authorized</td><td>Fuel not authorized</td><td></td></tr>
<tr><td>40203</td>	<td>Fuel not authorized</td><td>Fuel not authorized</td><td></td></tr>
<tr><td>20300</td>	<td>Quota not set</td><td>Quota not set</td><td></td></tr>
<tr><td>40300</td>	<td>Veh money excedeed</td><td>Vehicle money excedeed</td><td></td></tr>
<tr><td>40301</td>	<td>Driv money excedeed</td><td>Driver money excedeed</td><td></td></tr>
<tr><td>40302</td>	<td>Fuel money excedeed</td><td>Fuel money excedeed</td><td></td></tr>
<tr><td>40303</td>	<td>Site money excedeed</td><td>Site money excedeed</td><td></td></tr>
<tr><td>40304</td>	<td>Fleet money excedeed</td><td>Fleet money excedeed</td><td></td></tr>
<tr><td>40305</td>	<td>Veh qty excedeed</td><td>Veh quantity excedeed</td><td></td></tr>
<tr><td>40306</td>	<td>Driv qty excedeed</td><td>Driv quantity excedeed</td><td></td></tr>
<tr><td>40307</td>	<td>Fuel qty excedeed</td><td>Fuel quantity excedeed</td><td></td></tr>
<tr><td>40308</td>	<td>Site qty excedeed</td><td>Site quantity excedeed</td><td></td></tr>
<tr><td>40309</td>	<td>Fleet qty excedeed</td><td>Fleet quantity excedeed</td><td></td></tr>
<tr><td>20400</td>	<td>Quota not set</td><td>Quota not set</td><td></td></tr>
<tr><td>40400</td>	<td>Veh money excedeed</td><td>Vehicle money excedeed</td><td></td></tr>
<tr><td>40401</td>	<td>Driv money excedeed</td><td>Driver money excedeed</td><td></td></tr>
<tr><td>40402</td>	<td>Fuel money excedeed</td><td>Fuel money excedeed</td><td></td></tr>
<tr><td>40403</td>	<td>Site money excedeed</td><td>Site money excedeed</td><td></td></tr>
<tr><td>40404</td>	<td>Fleet money excedeed</td><td>Fleet money excedeed</td><td></td></tr>
<tr><td>40405</td>	<td>Veh qty excedeed</td><td>Veh quantity excedeed</td><td></td></tr>
<tr><td>40406</td>	<td>Driv qty excedeed</td><td>Driv quantity excedeed</td><td></td></tr>
<tr><td>40407</td>	<td>Fuel qty excedeed</td><td>Fuel quantity excedeed</td><td></td></tr>
<tr><td>40408</td>	<td>Site qty excedeed</td><td>Site quantity excedeed</td><td></td></tr>
<tr><td>40409</td>	<td>Fleet qty excedeed</td><td>Fleet quantity excedeed</td><td></td></tr>
<tr><td>40410</td>	<td>Veh tran excedeed</td><td>Vehicle transactions excedeed</td><td></td></tr>
<tr><td>40411</td>	<td>Driv tran excedeed</td><td>Driv transactions excedeed</td><td></td></tr>
<tr><td>40412</td>	<td>Prod tran excedeed</td><td>Prod transactions excedeed</td><td></td></tr>
<tr><td>40413</td>	<td>Site tran excedeed</td><td>Site transactions excedeed</td><td></td></tr>
<tr><td>40414</td>	<td>Fleet tran excedeed</td><td>Fleet transactions excedeed</td><td></td></tr>
<tr><td>20500</td>	<td>Retries exceeded</td><td>Retries exceeded</td><td></td></tr>
<tr><td>40500</td>	<td>Prompting needed</td><td>Prompting needed</td><td></td></tr>
<tr><td>40501</td>	<td>Pri PIN needed</td><td>Primary PIN needed</td><td></td></tr>
<tr><td>40502</td>	<td>Sec PIN needed</td><td>Secondary PIN needed</td><td></td></tr>
<tr><td>40503</td>	<td>Invalid  Pri PIN</td><td>Invalid primary PIN</td><td></td></tr>
<tr><td>40504</td>	<td>Invalid Sec PIN</td><td>Invalid secondary PIN</td><td></td></tr>
<tr><td>40505</td>	<td>Sec Track needed</td><td>Secondary track needed</td><td></td></tr>
<tr><td>40506</td>	<td>Invalid Odometer</td><td>Invalid odometer</td><td></td></tr>
<tr><td>40507</td>	<td>Invalid Eng Hours</td><td>Invalid engine hours</td><td></td></tr>
<tr><td>20600</td>	<td>Week days not set</td><td>Week days not set</td><td></td></tr>
<tr><td>40600</td>	<td>Day not authorized</td><td>Day not authorized</td><td></td></tr>
<tr><td>40601</td>	<td>Day not authorized</td><td>Day not authorized</td><td></td></tr>
<tr><td>40602</td>	<td>Day not authorized</td><td>Day not authorized</td><td></td></tr>
<tr><td>40603</td>	<td>Day not authorized</td><td>Day not authorized</td><td></td></tr>
<tr><td>40604</td>	<td>Day not authorized</td><td>Day not authorized</td><td></td></tr>
<tr><td>20700</td>	<td>DateTime not set</td><td>DateTime not set</td><td></td></tr>
<tr><td>40700</td>	<td>DateTime not auth</td><td>DateTime not auth</td><td></td></tr>
<tr><td>40701</td>	<td>DateTime not auth</td><td>DateTime not auth</td><td></td></tr>
<tr><td>40702</td>	<td>DateTime not auth</td><td>DateTime not auth</td><td></td></tr>
<tr><td>40703</td>	<td>DateTime not auth</td><td>DateTime not auth</td><td></td></tr>
<tr><td>40704</td>	<td>DateTime not auth</td><td>DateTime not auth</td><td></td></tr>
<tr><td>40705</td>	<td>DateTime not auth</td><td>DateTime not auth</td><td></td></tr>
<tr><td>40706</td>	<td>DateTime not auth</td><td>DateTime not auth</td><td></td></tr>
<tr><td>40707</td>	<td>DateTime not auth</td><td>DateTime not auth</td><td></td></tr>
<tr><td>40708</td>	<td>DateTime not auth</td><td>DateTime not auth</td><td></td></tr>
<tr><td>40709</td>	<td>DateTime not auth</td><td>DateTime not auth</td><td></td></tr>
<tr><td>40710</td>	<td>DateTime not auth</td><td>DateTime not auth</td><td></td></tr>
<tr><td>40711</td>	<td>DateTime not auth</td><td>DateTime not auth</td><td></td></tr>
<tr><td>40712</td>	<td>DateTime not auth</td><td>DateTime not auth</td><td></td></tr>
<tr><td>40713</td>	<td>DateTime not auth</td><td>DateTime not auth</td><td></td></tr>
<tr><td>40714</td>	<td>DateTime not auth</td><td>DateTime not auth</td><td></td></tr>
<tr><td>40715</td>	<td>DateTime not auth</td><td>DateTime not auth</td><td></td></tr>
<tr><td>40716</td>	<td>DateTime not auth</td><td>DateTime not auth</td><td></td></tr>
<tr><td>40717</td>	<td>DateTime not auth</td><td>DateTime not auth</td><td></td></tr>
<tr><td>40718</td>	<td>DateTime not auth</td><td>DateTime not auth</td><td></td></tr>
<tr><td>40719</td>	<td>DateTime not auth</td><td>DateTime not auth</td><td></td></tr>
<tr><td>40720</td>	<td>DateTime not auth</td><td>DateTime not auth</td><td></td></tr>
<tr><td>40721</td>	<td>DateTime not auth</td><td>DateTime not auth</td><td></td></tr>
<tr><td>40722</td>	<td>DateTime not auth</td><td>DateTime not auth</td><td></td></tr>
<tr><td>40723</td>	<td>DateTime not auth</td><td>DateTime not auth</td><td></td></tr>
<tr><td>40724</td>	<td>DateTime not auth</td><td>DateTime not auth</td><td></td></tr>
<tr><td>40725</td>	<td>DateTime not auth</td><td>DateTime not auth</td><td></td></tr>
<tr><td>40726</td>	<td>DateTime not auth</td><td>DateTime not auth</td><td></td></tr>
<tr><td>40727</td>	<td>DateTime not auth</td><td>DateTime not auth</td><td></td></tr>
<tr><td>40728</td>	<td>DateTime not auth</td><td>DateTime not auth</td><td></td></tr>
<tr><td>40729</td>	<td>DateTime not auth</td><td>DateTime not auth</td><td></td></tr>
<tr><td>20800</td>	<td>Week days not set</td><td>Week days not set</td><td></td></tr>
<tr><td>20801</td>	<td>Time not set</td><td>Time not set</td><td></td></tr>
<tr><td>40800</td>	<td>Day not authorized</td><td>Day not authorized</td><td></td></tr>
<tr><td>40801</td>	<td>Day not authorized</td><td>Day not authorized</td><td></td></tr>
<tr><td>40802</td>	<td>Day not authorized</td><td>Day not authorized</td><td></td></tr>
<tr><td>40803</td>	<td>Day not authorized</td><td>Day not authorized</td><td></td></tr>
<tr><td>40804</td>	<td>Day not authorized</td><td>Day not authorized</td><td></td></tr>
<tr><td>40805</td>	<td>DaysTime not auth</td><td>Day not authorized</td><td></td></tr>
<tr><td>40806</td>	<td>DaysTime not auth</td><td>Day not authorized</td><td></td></tr>
<tr><td>40807</td>	<td>DaysTime not auth</td><td>Day not authorized</td><td></td></tr>
<tr><td>40808</td>	<td>DaysTime not auth</td><td>Day not authorized</td><td></td></tr>
<tr><td>40809</td>	<td>DaysTime not auth</td><td>Day not authorized</td><td></td></tr>
<tr><td>40810</td>	<td>DaysTime not auth</td><td>Day not authorized</td><td></td></tr>
<tr><td>40811</td>	<td>DaysTime not auth</td><td>Day not authorized</td><td></td></tr>
<tr><td>40812</td>	<td>DaysTime not auth</td><td>Day not authorized</td><td></td></tr>
<tr><td>40813</td>	<td>DaysTime not auth</td><td>Day not authorized</td><td></td></tr>
<tr><td>40814</td>	<td>DaysTime not auth</td><td>Day not authorized</td><td></td></tr>
<tr><td>20900</td>	<td>Quota Not Set</td><td>Quota Not Set</td><td></td></tr>
<tr><td>40900</td>	<td>Veh money exceeded</td><td>Vehicle money exceeded</td><td></td></tr>
<tr><td>40901</td>	<td>Driv money exceeded</td><td>Driver money exceeded</td><td></td></tr>
<tr><td>40902</td>	<td>Site money exceeded</td><td>Site money exceeded</td><td></td></tr>
<tr><td>40903</td>	<td>Fleet money exceeded</td><td>Fleet money exceeded</td><td></td></tr>
<tr><td>21000</td>	<td>Quota not set</td><td>Quota not set</td><td></td></tr>
<tr><td>41000</td>	<td>Veh money exceeded</td><td>Vehicle money exceeded</td><td></td></tr>
<tr><td>41001</td>	<td>Driv money exceeded</td><td>Driver money exceeded</td><td></td></tr>
<tr><td>41002</td>	<td>Site money exceeded</td><td>Site money exceeded</td><td></td></tr>
<tr><td>41003</td>	<td>Fleet money exceeded</td><td>Fleet money exceeded</td><td></td></tr>
<tr><td>50000</td>	<td>App Error</td><td>Application Error</td><td></td></tr>
</table>