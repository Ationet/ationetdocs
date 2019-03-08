![ationetlogo](Content/Images/ATIOnetLogo_250x70.png) 
# ATIOnet Feature List

> **UNRELEASED DOCUMENT - TEST DATA**

<table>
	<thead>
		<tr>
			<td width=10%>Area</td>
			<td width=20%>Feature</td>
			<td width=30%>Function</td>
			<td width=40%>Benefit</td>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>Administration</td>
			<td>Self-provisioning</td>
			<td>Data maintenance is distributed across Network, Merchants and Fleet Companies administrators, based on data ownership and roles</td>
			<td></td>
		</tr>
		<tr>
			<td>Identifications</td>
			<td>Type and Models</td>
			<td>Define specialized behavior for each type of Identification technology</td>
			<td></td>
		</tr>
		<tr>
			<td>Identifications</td>
			<td>Attributes</td>
			<td>Specify whether an Identification is Reusable, Personalized, Installable</td>
			<td></td>
		</tr>
		<tr>
			<td>Identifications</td>
			<td>Programs</td>
			<td>Define a set of restrictions and/or exceptions to apply to a set of identifiers</td>
			<td></td>
		</tr>
		<tr>
			<td>Organization</td>
			<td>Fleet Attribute</td>
			<td>Allows to group the vehicles in large hierarchical groups</td>
			<td></td>
		</tr>
		<tr>
			<td>Organization</td>
			<td>User-defined classifications</td>
			<td>Allows to group the vehicles by different (up-to 4) criteria defined by the user</td>
			<td></td>
		</tr>
		<tr>
			<td>Organization</td>
			<td>Vehicles and Drivers</td>
			<td>Cardholders can be Drivers (persons) or Vehicles (any kind of unit)</td>
			<td></td>
		</tr>
		<tr>
			<td>Organization</td>
			<td>Vehicle classes</td>
			<td>User-defined types of units (brand/models) with mileage and product restrictions attributes</td>
			<td></td>
		</tr>
		<tr>
			<td>Restrictions</td>
			<td>Rules - Timing</td>
			<td>Allows restriction of When a cardholder can purchase</td>
			<td></td>
		</tr>
		<tr>
			<td>Restrictions</td>
			<td>Rules - Product</td>
			<td>Allows restriction of the Product(s) allowed for a given cardholder</td>
			<td></td>
		</tr>
		<tr>
			<td>Restrictions</td>
			<td>Rules - Location</td>
			<td>Allows restriction of on what sites a cardholder can run a transaction</td>
			<td></td>
		</tr>
		<tr>
			<td>Restrictions</td>
			<td>Rules - Quotas</td>
			<td>Allows to limit the amount or volume that a cardholder can consume during a certain time (fixed or periodic)</td>
			<td></td>
		</tr>
		<tr>
			<td>Restrictions</td>
			<td>Contingency limits</td>
			<td>Special limits may be configured to be applied on contingency transactions</td>
			<td></td>
		</tr>
		<tr>
			<td>Restrictions</td>
			<td>Offline limits</td>
			<td>Special limits may be configured to be applied to transactions authorized offline</td>
			<td></td>
		</tr>
		<tr>
			<td>Restrictions</td>
			<td>Multiple inheritance</td>
			<td>A transaction may apply to restrictions set on different entities of the system, for example: applied directly to the cardholder, inherited from the Fleet and from the Contract</td>
			<td></td>
		</tr>
		<tr>
			<td>Security</td>
			<td>Job roles</td>
			<td>Assign function-oriented set of attributions to users</td>
			<td></td>
		</tr>
		<tr>
			<td>Security</td>
			<td>SSL</td>
			<td>Encripted access to WEB portals and interfaces</td>
			<td></td>
		</tr>
		<tr>
			<td>Transaction Processing</td>
			<td>Vehicles and Accounts</td>
			<td>A given vehicle may have many accounts with different contracts or subscribers</td>
			<td></td>
		</tr>
		<tr>
			<td>Transaction Processing</td>
			<td>Most restrictive condition</td>
			<td>Restricts the authorization to the minimum value resulting from all applicable restrictions</td>
			<td></td>
		</tr>
		<tr>
			<td>Transaction Processing</td>
			<td>Dual Identification</td>
			<td>Based on configuration, a transaction may require Driver and Vehicle identification</td>
			<td></td>
		</tr>
		<tr>
			<td>Transaction Processing</td>
			<td>Re-prompting</td>
			<td>A transaction with missing required fields may trigger a special Decline response code instructing the Terminal to retry the transaction after collecting missing data</td>
			<td></td>
		</tr>
		<tr>
			<td>Transaction Processing</td>
			<td>Exceptions</td>
			<td>Transaction are automatically flagged as Unlawful, Invalid, Suspicious, Declined and Observed, depending a set of business rules.</td>
			<td></td>
		</tr>
		<tr>
			<td>Transaction Processing</td>
			<td>Exceptions - To-be-reviewed</td>
			<td>Some non-critical exception conditions may flag the transaction as To-be-reviewed. TBR transactions are approved but not considered </td>
			<td></td>
		</tr>
		<tr>
			<td>Transaction Processing</td>
			<td>Splitted processing</td>
			<td>A transaction is processed by two separate engines, the Rules engine and the Accounts engine, which could be a third-party remote service</td>
			<td></td>
		</tr>
		<tr>
			<td>Transaction Processing</td>
			<td>Multiple FEPs</td>
			<td>Each Terminal protocol is accepted via a specific Front-end Processor</td>
			<td></td>
		</tr>
		<tr>
			<td>Transaction Processing</td>
			<td>Multi-instance FEPs</td>
			<td>Automatic load manager starts and stops instances of Front-end Processors according to system load</td>
			<td></td>
		</tr>
		<tr>
			<td>Transaction Processing</td>
			<td>Low-level logging</td>
			<td>A messaging-level can be activated dinamically to diagnose problems with a site or Terminal type</td>
			<td></td>
		</tr>
		<tr>
			<td>Transaction Processing</td>
			<td>Automatic tax disaggregation</td>
			<td>Extract included taxes on payment transaction to display tax totals in Statements</td>
			<td></td>
		</tr>
		<tr>
			<td>Transaction Processing</td>
			<td>Terminal independent rules engine</td>
			<td>Rules, restrictions and statistics enforced and tracked across different types or Terminals (restrictions may apply)</td>
			<td></td>
		</tr>
		<tr>
			<td>Transaction Processing</td>
			<td>Explicit detailed tax data</td>
			<td>Native protocol supports detailed tax information for proper presentation on Statements</td>
			<td></td>
		</tr>
		<tr>
			<td>Transaction Processing</td>
			<td></td>
			<td></td>
			<td></td>
		</tr>

	</tbody>
</table>