# Ationet Native Protocol Integration Version 2.2

Change Logs

|**General Document Information**||
| :- | :- |
|**Version:**|2\.2|
|**Version Status:**|Definitive Edition|
|**Date Version:**|29/02/2024|
|||

|**Revision Log**||||
| :- | :- | :- | :- |
|**Version**|**Date**|**Description**|**Autor**|
|1\.0|23/02/2024|Initial version|Cabral, Matías|
|2\.0|29/02/2024|Update document format, diagrams integrations, add diagrams sequence, add descriptions process |Yañez, Alexis|
|2\.1|07/03/2024|Messaging was completed. Host validation diagram added.|Yañez, Alexis|
|2\.2|08/03/2024|Updated diagrams to Lucidchart format|Yañez, Alexis|

|**Distribution / ATIONET Approval**||||
| :- | :- | :- | :- |
|**Version**|**Date**|**Approver / Role**|**Signature**|
|1\.0|dd/mmm/yyyy|Pending||
|2\.0|dd/mmm/yyyy|Pending||
|2\.1|dd/mmm/yyyy|Pending||
|2\.2|dd/mmm/yyyy|Pending||




**Index**

[Introduction	5****](#_toc160812874)**

[**Purpose	5****](#_toc160812875)

[**What is ATIONET?	5****](#_toc160812876)

[**Solution Architecture	7****](#_toc160812877)

[**Definitions	7****](#_toc160812878)

[**Diagram	8****](#_toc160812879)

[**Integration with ATIONET	9****](#_toc160812880)

[**ATIONET Native Transactions Protocol Specification	9****](#_toc160812881)

[**ATIONET Administrative Transactions Protocol Specification	9****](#_toc160812882)

[**Environments	10****](#_toc160812883)

[**Test Environment	10****](#_toc160812884)

[**Beta Environment	10****](#_toc160812885)

[**Productive Environment	10****](#_toc160812886)

[**Message Information	11****](#_toc160812887)

[**Message Structure	11****](#_toc160812888)

[**Body Format Example:	11****](#_toc160812889)

[**Error Handling	12****](#_toc160812890)

[**Message Sequence	13****](#_toc160812891)

[**Normal Authorization Flow	13****](#_toc160812892)

[**Pre-Authorization	15****](#_toc160812893)

[**Sequence Diagram - Normal Flow	16****](#_toc160812894)

[**Sequence Diagram – Re Prompt	17****](#_toc160812895)

[**Sequence Diagram - Communication Problems	19****](#_toc160812896)

[**Message Information	21****](#_toc160812897)

[**Completion	22****](#_toc160812898)

[**Sequence Diagram	23****](#_toc160812899)

[**Sequence Diagram - Communication Problems	24****](#_toc160812900)

[**Sequence Diagram - Conflict Problems	26****](#_toc160812901)

[**Message Information	28****](#_toc160812902)

[**Zero Completion (Pre-Authorization Cancelation)	28****](#_toc160812903)

[**Balance Inquiry	29****](#_toc160812904)

[**Sequence Diagram	30****](#_toc160812905)

[**Message Information	30****](#_toc160812906)

[**Sale	31****](#_toc160812907)

[**Sequence Diagram	31****](#_toc160812908)

[**Sequence Diagram - Communication Problems	32****](#_toc160812909)

[**Message Information	34****](#_toc160812910)

[**Cancellation	35****](#_toc160812911)

[**Sequence Diagram	35****](#_toc160812912)

[**Message Information	36****](#_toc160812913)

[**Void	37****](#_toc160812914)

[**Sequence Diagram	38****](#_toc160812915)

[**Message Information	39****](#_toc160812916)

[**Keep Alive	40****](#_toc160812917)

[**Sequence Diagram	41****](#_toc160812918)

[**Message Information	41****](#_toc160812919)




# <a name="_toc102571956"></a>**<a name="_toc160193598"></a><a name="_toc265766844"></a><a name="_toc160812874"></a>**Introduction

## <a name="_toc160193599"></a><a name="_toc160812875"></a>Purpose

The purpose of this document is to specify in detail the integration with ATIONET Native protocol. 

## <a name="_definitions"></a><a name="_toc160812876"></a>What is ATIONET?
Is a technology platform for cloud services for service stations or fuel dispatch centers.

Ationet oversees verifying the possibility of fuel dispatch. 

For this purpose, it applies different validations to determine whether the dispatch request received can be carried out. 

We can separate the validations as follows:

1) Validation of the request structure.
2) Ensuring the integrity of the data received, validating that the information submitted by the consumer is valid for our subscription.
3) Rules validation: this point is closely related to the configuration in the Ationet portal, where the user can determine whether a client must meet certain requirements to perform a dispatch. At the same time, he has the possibility to apply restrictions that allow / prevent fuel dispatching.
4) Validates the user's current account is validated to determine if he/she has a balance to operate.

![image](https://github.com/Ationet/ationetdocs/assets/96298341/f879ac7b-d87b-4ac2-a4d8-c32cc9fa8f0d)


Once the structure and integrity of the information is assured, **the combination of the rules applied, and the balance will result in the client's availability to operate.**

Allows the creation and management of fleet programs, loyalty programs, gift cards, and other commercial platform products. The software authorizes transactions received from any third-party POS terminal or platform.
# <a name="_toc160193601"></a><a name="_toc160812877"></a>Solution Architecture

## <a name="_toc160193600"></a><a name="_toc160812878"></a>Definitions

|<a name="_host"></a>Host|A computer system that is accessed by a user working at a remote location. In this document, Host is always the ATIONET Host.|
| :- | :- |
|Terminal|An electronic merchant card processing device responsible for transaction capture, display output to the cashier and/or to the cardholder on screen and/or print format.|
|Controller|A client system that can send or receive data to and from ATIONET’s Host. A Controller controls or includes one or more terminal. When there is only one Terminal connected to a Controller, Terminal and Controller are equivalent.|


<a name="_toc160193602"></a>
## <a name="_toc160812879"></a>Diagram

![image](https://github.com/Ationet/ationetdocs/assets/96298341/426e2e12-72aa-4ade-b007-11fb7a48bd46)


**
## <a name="_toc160193603"></a><a name="_toc160812880"></a>Integration with ATIONET

Third-party systems integrate with ATIONET via a set of APIs (Application Programming Interfaces). Each ATIONET’s API is described on a separate Protocol Specification. The complete documentation of ATIONET API’s is comprised of:

## <a name="_toc160193604"></a><a name="_toc160812881"></a>ATIONET Native Transactions Protocol Specification

Covers financial transactions for transaction capture systems (payment terminals, site controllers and point of sale systems), including sales and refunds.

## <a name="_toc160193605"></a><a name="_toc160812882"></a>ATIONET Administrative Transactions Protocol Specification

Describes a set of functions complementing the transaction-capture business, for example Batch or Shift Close. These functions enhance the capabilities of the integration, but their implementation is not mandatory.

<a name="_toc160193608"></a>
# <a name="_toc160812883"></a>Environments 

Ationet has multiple environments to ensure to be able to perform the relevant tests at the time of integration. For this reason, Ationet has:

## <a name="_toc160193609"></a><a name="_toc160812884"></a>Test Environment
This environment is used for development, allowing to test the advances that are generated.

URL Environment: <https://native-test.ationet.com/>v1/auth

## <a name="_toc160193610"></a><a name="_toc160812885"></a>Beta Environment
It is a more stable environment, which already contains a finalized version. It is used to test the developments in search of errors, prior to their passage to production.

URL Environment: <https://native-beta.ationet.com/>v1/auth

## <a name="_toc160193611"></a><a name="_toc160812886"></a>Productive Environment
The productive version of Ationet.

URL Environment: <https://native.ationet.com/>v1/auth

**
# <a name="_toc160193612"></a><a name="_toc160812887"></a>Message Information	

## <a name="_toc160193613"></a><a name="_toc160812888"></a>Message Structure
All Transaction API messages share the same base structure with slight modifications depending on which *TransactionCode* you use. All requests must be made with a **POST** method and the body uses a JSON format, as well as their responses.

### <a name="_toc160193614"></a><a name="_toc160812889"></a>Body Format Example:
{

`	`"FieldName":"StringValue",

`	`"FieldName":"StringValue",

`	`"FieldName": Value

}

Only one request is accepted on each message.

For detailed information about the request structure provided by Ationet, please visit our [technical documentation](https://github.com/Ationet/ationetdocs/blob/master/AN-Native_Transaction_Protocol-Spec.md#7-transaction-request-treq-message-format).

You can also obtain a detailed description about the fields that compose the requests / responses, [in this section of our technical documentation](https://github.com/Ationet/ationetdocs/blob/master/AN-Native_Transaction_Protocol-Spec.md#6-field-descriptions).

Likewise, if you wish to obtain details of each field and description of the response message provided by Ationet, please visit our [technical documentation](https://github.com/Ationet/ationetdocs/blob/master/AN-Native_Transaction_Protocol-Spec.md#8-transaction-response-tresp-message-format).

On the other hand, if you wish to obtain details on the obligatory nature of each field in the request/response messages, you can visit [our technical documentation](https://github.com/Ationet/ationetdocs/blob/master/AN-Native_Auth_Protocol_Messages.md#authorization-protocol-messages), which details this information in each type of message.







# <a name="_toc160193615"></a><a name="_toc160812890"></a>Error Handling

Success/failure exits on the Native Transaction Protocol will be handled via HTTP status codes.

Successful request will get a HTTP 200 and the resulting response.

Transactions intended to post a command, for example Authorizations and Pre-Authorizations will return a single JSON-formatted item with the *Response Code* and *Response Text*. The body of these responses will never be empty.

Failure to process the request will be indicated by an HTTP 400’s range status code. The body will contain a single JSON-formatted item with the “ResponseCode”, “ResponseMessage” and “ResponseError” fields.

Refer to [Response Codes annex](https://github.com/Ationet/ationetdocs/blob/master/Annexes/AN-Native-AuthResponseCodes-Annex.md) for a complete list of supported codes.


# <a name="_toc160193637"></a><a name="_toc160812891"></a>Message Sequence
This section will detail the sequence of messages that must be followed to integrate with Ationet.

## <a name="_toc160812892"></a>Normal Authorization Flow
This diagram shows the complete flow, without alternative paths, to perform a successful transaction against Ationet in a pre-authorization operation.

![image](https://github.com/Ationet/ationetdocs/assets/96298341/8b4610ee-d926-4899-9bb0-a72ce73ba652)



In this case:

1. The terminal / controller sends a pre-authorization to the Ationet host.
1. Ationet accepts the pre-authorization either in whole or in part.
1. The terminal / controller sends a completion to Ationet.
1. Ationet accepts the completion.
1. End of flow.

<a name="_toc160193638"></a>
## <a name="_toc160812893"></a>Pre-Authorization

Send a request to the Host containing the **TransactionCode** with the value **100** indicating that it is a **Pre-Authorization.**

Other important fields to consider would be:

- TerminalIdentification
- TransactionSecuenceNumber
- PrimaryTrack
- TransactionAmount, ProductCode, ProductUnitPrice, ProductAmount, ProductQuantity
- LocalTransactionDate: local transaction date in yyyymmdd format
- LocalTransactionTime: local transaction time in hhmmss format

<a name="_toc160193639"></a>
### <a name="_toc160812894"></a>Sequence Diagram - Normal Flow
Corresponds to the case where a pre-authorization is requested and when a response is obtained, the pre-authorization flow ends.

![image](https://github.com/Ationet/ationetdocs/assets/96298341/322edb50-7e4d-4e28-8dd8-c8dcb38bedc1)


### <a name="_sequence_diagram_–"></a><a name="_toc160193640"></a><a name="_toc160812895"></a>Sequence Diagram – Re Prompt
Corresponds to the case where a pre-authorization is requested and Ationet requires additional information to authorize or reject it.

![image](https://github.com/Ationet/ationetdocs/assets/96298341/2fdebde5-3a94-4074-b86e-7a2207cc82d1)


###
In ATIONet rules refer to limits that can be configured by the company and associated to different entities. Inside this view you can consult, create, or edit rules. 

When the entity has a request rule, if the client sends a Pre-authorization and it does not contain the additional information configured to be requested, ATIONET will respond requesting such additional information to approve it.

The transaction will remain in Request Required status waiting for the customer to send the required information. 

The following codes represents the ATIONet promptings needed as well:

|**Name**|**Code**|
| :-: | :-: |
|**GeneralPromptingNeeded**|40500|
|**PrimaryTrackPinPromptingNeeded**|40501|
|**SecondaryTrackPinPromptingNeeded**|40502|
|**PrimaryTrackPinPromptingInvalid**|40503|
|**SecondaryTrackPinPromptingInvalid**|40504|
|**OdometerPromptingInvalid**|40506|
|**EngineHoursPromptingInvalid**|40507|



Additionally, there are response codes that represent that the transaction has been rejected and that it is no longer possible to send more additional information (prompting) to complete the remaining information of the transaction. 

|**Name**|**Code**|
| :-: | :-: |
|**PromptingRetriesExceeded**|**20500**|
|**PrimaryTrackOutOfPinTries**|**40508**|
|**SecondaryTrackOutOfPinTries**|**40509**|
|**BlockedPrimaryTrackOutOfPinTries**|**40510**|
|**BlockedSecondaryTrackOutOfPinTries**|**40511**|

To answer a request, it will be necessary to resend the original request (same TSN, date and time) including the requested fields in CustomerData. 

At the protocol level, the information of the requests and their values are managed inside the CustomerData object. The required values will be requested with the following key: Prompt[Field], where [Field] can take any value needed (and there can be more than 1 in the same message). 

[In this appendix](https://github.com/Ationet/ationetdocs/blob/master/Annexes/AN-Native-CustomerData-Annex.md), you can obtain information on CustomerData to evaluate the response obtained. 
### <a name="_toc160812896"></a>Sequence Diagram - Communication Problems

This scenario contemplates communication problems in the pre-authorization request. It contemplates the case in which the request has not reached the Ationet Host, and in which the response provided by Ationet has not reached its destination. 

In both cases it is necessary to proceed with a cancellation message, as detailed in the document.

If there is no response to the cancellation, a maximum of 3 consecutive cancellation retries must be made. 

If there is still no response to the cancellation from the host, it is recommended to store the cancellation, so that it can be reattempted later.

In case Ationet responds to the cancellation, **the flow MUST TERMINATE**, regardless of whether the cancellation was authorized or not**. And it must be removed from the store and forward so that it is not sent again.**

On the other hand, when initiating a new pre-authorization, it is important that a new transaction sequence number is generated, to restart a new pre-authorization flow.

**If you need to cancel a pre-authorization on demand (not due to technical problems)**, please review the [Zero Completion implementation](#_zero_completion_\(pre-authorization).

Please validate the cancellation message in this [section of the document](#_cancellation).

![image](https://github.com/Ationet/ationetdocs/assets/96298341/2fed0035-2484-46bd-a914-9a5431a51052)

### <a name="_toc160193641"></a><a name="_toc160812897"></a>Message Information

For information on the request, please visit the [following link to the technical documentation](https://github.com/Ationet/ationetdocs/blob/master/AN-Native_Transaction_Protocol-Spec.md#131-pre-authorization-request-sample).

For information on the response, please visit the [following link to the technical documentation](https://github.com/Ationet/ationetdocs/blob/master/AN-Native_Transaction_Protocol-Spec.md#1312-pre-authorization-response-sample).

Once sent the Host will return a **response**, several of the data returned are the same structure as the **request**.

The fields we are most interested in are the AuthorizationCode to identify the transaction and the ResponseCode that indicates the result of the request.

The **ResponseCode** we expect is **00000** which indicates that the transaction was authorized.

If not authorized, the **ResponseCode** will be different and the **ResponseText** and **LongResponseText** fields will give us more information about the result obtained, as shown in the following extract from **response.**

We should also note that we may get response codes that indicate that Ationet is requesting additional data. This can be seen in the [Sequence Diagram - Re Prompt.](#_sequence_diagram_–)



##
## <a name="_toc160812898"></a>Completion

Once we have an authorized **Pre-Authorization**, we can finalize the sale with a Completion.

The fields to highlight in this **request** are the **TransactionCode** in **120** that indicates that it is a **Completion**, and the fields that come directly from the **response** of the **Pre-Authorization**, mainly the **AuthorizationCode** that identifies the transaction.

For the rest of the fields, the terminal / controller should fill in as appropriate, such as amount dispatched, quantity dispatched, etc.

Upon receiving a response from Ationet for completion, **the flow should be terminated, regardless of whether the response code is authorized or not.**


### <a name="_toc160812899"></a>Sequence Diagram

![image](https://github.com/Ationet/ationetdocs/assets/96298341/4635cac0-5e8b-4346-9b09-356ec58458ed)

###

### <a name="_toc160812900"></a>Sequence Diagram - Communication Problems

This scenario contemplates communication problems in the request for completion. It contemplates the case where the request did not reach the Ationet Host, and where the response provided by Ationet did not reach its destination. 

In both cases it is necessary to proceed with a cancellation message, as detailed in the document.

If there is no response to the cancellation, a maximum of 3 consecutive retries must be made. 

If there is still no response from the host, it is recommended to store the cancellation, so that it can be reattempted later.

In case of a response from Ationet**, the flow MUST END**, regardless of whether the cancellation was authorized or not. **And the cancellation must be removed from the store and forward so that it is not sent again**.

Please validate the cancellation message in this [section of the document](#_cancellation).

![image](https://github.com/Ationet/ationetdocs/assets/96298341/810246bc-82b0-4e3e-b592-2e3b63f8f770)


### <a name="_toc160812901"></a>Sequence Diagram - Conflict Problems

This scenario describes the case where Ationet returns a conflict message when processing a completion. 

This case occurs when Ationet received the completion message, did not receive a cancellation, and the completion is reported again. 

In this case, Ationet will respond with HTTP Code 409 indicating that there is a conflict.

What to do, when receiving an HTTP Code 409 when sending a completion, is:

1. Send a cancellation for that sale completion.
1. Ensure that the cancellation was processed correctly (Receiving a 410 frame with Response Code 00000 (Authorized)).
1. Resend the sale completion.

Please validate the cancellation message in this [section of the document](#_cancellation).

![image](https://github.com/Ationet/ationetdocs/assets/96298341/471d5f10-edbb-4a51-85b3-7dff1ca455c1)

### <a name="_toc160812902"></a>Message Information

For information on the request, please visit the [following link to the technical documentation](https://github.com/Ationet/ationetdocs/blob/master/AN-Native_Transaction_Protocol-Spec.md#1321-completion-request-sample).

For information on the response, please visit the [following link to the technical documentation](https://github.com/Ationet/ationetdocs/blob/master/AN-Native_Transaction_Protocol-Spec.md#1322-completion-response-sample).

The host will return a **response**, again we need to check the **ResponseCode**

In the case that when sending a completion, the response is that it was not authorized, the transaction flow is terminated.

### <a name="_zero_completion_(pre-authorization"></a><a name="_toc160812903"></a>Zero Completion (Pre-Authorization Cancelation)
In case you wish to cancel a pre-authorization that has been authorized, it is necessary to send a completion with amounts/quantities dispatched in zero. This will allow Ationet to revert the balance reserved in the pre-authorization.



## <a name="_toc160812904"></a>Balance Inquiry
Ationet allows you to obtain the customer's available funds through the Balance Inquiry message.

The message has the same structure as a pre-authorization, except that the Transaction Code is 102.

This message behaves similarly to a pre-authorization, except that it does not perform the balance reservation.

On the other hand, it is important to remember that Ationet will return the AVAILABLE according to the conjunction of the rules that apply at the time of the query plus the balance availability in the current account.

The response will be a frame with Transaction Code 112.

The reasons for rejection in this message, obtained in the Response Code, may be caused by the following:

1. Validation of the request structure
1. Integrity of the data received.

In case the client does not have available, the transaction will exit with zero authorized amount.

In the case of a communication error, where you do not get a response from the Host, in this case you can retry the message.


### <a name="_toc160812905"></a>Sequence Diagram

![image](https://github.com/Ationet/ationetdocs/assets/96298341/f083c0d5-b99c-44ec-94c9-5286e4a648cb)
### <a name="_toc160812906"></a>Message Information

For information on the request, please visit the [following link to the technical documentation](https://github.com/Ationet/ationetdocs/blob/master/AN-Native_Transaction_Protocol-Spec.md#1331-balance-inquiry-request-sample).

For information on the response, please visit the [following link to the technical documentation](https://github.com/Ationet/ationetdocs/blob/master/AN-Native_Transaction_Protocol-Spec.md#1332-balance-inquiry-response-sample).

## <a name="_toc160812907"></a>Sale
Ationet allows to report a fuel dispatch without going through the pre-authorization flow. For this purpose, the sales message is available. 

The terminal will send a sale message, and Ationet will run the rules engine, since the sale does not have an associated pre-authorization, so it is necessary to validate the rules.

The sale can be approved or rejected.

### <a name="_toc160812908"></a>Sequence Diagram
![image](https://github.com/Ationet/ationetdocs/assets/96298341/a387f409-c404-480b-b4a4-e239bd5c5797)

### <a name="_toc160812909"></a>Sequence Diagram - Communication Problems

This scenario contemplates communication problems in the request for sale. It contemplates the case where the request did not reach the Ationet Host, and where the response provided by Ationet did not reach its destination. 

In both cases it is necessary to proceed with a cancellation message, as detailed in the document.

If there is no response to the cancellation, a maximum of 3 consecutive retries must be made. 

If there is still no response from the host, it is recommended to store the cancellation, so that it can be reattempted later.

In case of a response from Ationet**, the flow MUST END**, regardless of whether the cancellation was authorized or not. **And the cancellation must be removed from the store and forward so that it is not sent again**.

Please validate the cancellation message in this [section of the document](#_cancellation).

![image](https://github.com/Ationet/ationetdocs/assets/96298341/986ed069-a6db-468f-b91b-4431073e4233)



### <a name="_toc160812910"></a>Message Information

For information on the request, please visit the [following link to the technical documentation](https://github.com/Ationet/ationetdocs/blob/master/AN-Native_Transaction_Protocol-Spec.md#1341-sale-request-sample).

For information on the response, please visit the [following link to the technical documentation](https://github.com/Ationet/ationetdocs/blob/master/AN-Native_Transaction_Protocol-Spec.md#1342-sale-response-sample).


## <a name="_cancellation"></a><a name="_toc160812911"></a>Cancellation

This message corresponds to a technical cancellation. It is used when there is a communication problem between the terminal / controller and the Ationet Host, to reverse the movements and be able to perform the flow again.

In the reauthorization and Completion messages, the flow for the use of this message was specified.

The basic flow is shown here, without considering the particularities detailed above.
###
### <a name="_toc160812912"></a>Sequence Diagram

![image](https://github.com/Ationet/ationetdocs/assets/96298341/01c55870-51fd-421a-af90-d9159dfa2450)

### <a name="_toc160812913"></a>Message Information

For information on the request, please visit the [following link to the technical documentation](https://github.com/Ationet/ationetdocs/blob/master/AN-Native_Transaction_Protocol-Spec.md#1331-cancellation-request-sample).

For information on the response, please visit the [following link to the technical documentation](https://github.com/Ationet/ationetdocs/blob/master/AN-Native_Transaction_Protocol-Spec.md#1331-cancellation-response-sample).


## <a name="_toc160812914"></a>Void
This message allows you to reverse a Completion or Sale, returning the consumption, if the transaction has not been billed.

In case Ationet **rejects the message because the transaction has already been billed**, the transaction dispute flow should be followed to reverse the consumption from the Ationet portal.

In any other case, the flow should be given as **terminated**.

Ationet will provide the following response code if the transaction is billed, allowing to identify that a dispute is required to be made in the portal.

|**Name**|**Code**|
| :-: | :-: |
|**TransactionAlreadyBilled**|**13048**|


### <a name="_toc160812915"></a>Sequence Diagram
![image](https://github.com/Ationet/ationetdocs/assets/96298341/a9eabf70-5ebb-4f0e-b385-dd748caa72c0)



### <a name="_toc160812916"></a>Message Information

For information on the request, please visit the [following link to the technical documentation](https://github.com/Ationet/ationetdocs/blob/master/AN-Native_Transaction_Protocol-Spec.md#1351-void-request-sample).

For information on the response, please visit the [following link to the technical documentation](https://github.com/Ationet/ationetdocs/blob/master/AN-Native_Transaction_Protocol-Spec.md#1352-void-response-sample).


## <a name="_toc160812917"></a>Keep Alive

The terminal must implement a KeepAlive message to inform Ationet that it is operational, the structure of which is attached to this document.

This message should be sent every 1 to 3 hours. This time span must be configurable from the terminal.

Ationet will respond with an HTTP Status Code 200 to indicate that it is active.

**Important: in this case, the controller to be used is the maintenance controller, so the URL should be formed as follows:**


[{URLEnvironment}/](https://native-test.ationet.com/)v1/maintenance
###
### <a name="_toc160812918"></a>Sequence Diagram
![image](https://github.com/Ationet/ationetdocs/assets/96298341/a373ef51-a739-4724-a9b1-a44e0d92e7e9)


### <a name="_toc160812919"></a>Message Information

For information on the request, please visit the [following link to the technical documentation](https://github.com/Ationet/ationetdocs/blob/master/AN-Native_Transaction_Protocol-Spec.md#1371-keep-alive-request-sample).

For information on the response, please visit the [following link to the technical documentation](https://github.com/Ationet/ationetdocs/blob/master/AN-Native_Transaction_Protocol-Spec.md#1372-keep-alive-response-sample).
