# 10. Generic settings 

This section defines the common settings for exchanging messages within the Council’s Framework. 

## 10.1 PMode Settings 

A list of base PMode settings are listed in Appendix A.1 Base Agreement. 

## 10.2 User message 

**eb:Messaging/eb:UserMessage/eb:MessageInfo** 

| | |
| ---| ----|
eb:Timestamp | The REQUIRED Timestamp element has a value representing the date at which the message header was created, and is conforming to a dateTime (W3C, 2012). It MUST be expressed as UTC. Indicating UTC in the Timestamp element by including the 'Z' identifier is optional. E.g. 2016-07-01T00:00:00 |
eb:MessageId |  unique identifier to identify a message exchange between two Access Points. It is recommended to use a universally unique identifier which can be achieved using a UUID (Leach, Mealling, & Salz, 2005). |

**eb:Messaging/eb:UserMessage/eb:PartyInfo**
| | |
| ---| ----|
eb:From/eb:PartyId@type | The party ID type uses scheme identifiers from the iso6523 catalog. urn:oasis:names:tc:ebcore:partyid-type:iso6523:&lt;iso6523 scheme &gt; |
eb:From/eb:PartyId | The value of the PartyId element depends on the type. |
eb:From/eb:Role | http://docs.oasis-open.org/ebxml-msg/ebms/v3.0/ns/core/200704/defaultRole |
eb:To/eb:PartyId@type | The party ID type uses scheme identifiers from the iso6523 catalog. urn:oasis:names:tc:ebcore:partyid-type:iso6523:&lt;iso6523 scheme &gt; |
eb:To/eb:PartyId | The value of the PartyId element depends on the type. |
eb:To/eb:Role | http://docs.oasis-open.org/ebxml-msg/ebms/v3.0/ns/core/200704/defaultRole |


**eb:Messaging/eb:UserMessage/eb:CollaborationInfo**
| | |
| ---| ----|
eb:AgreementRef | http://resources.digitalbusinesscouncil.com.au/dbc/services/exchange/ebms3profile/current |
eb:Service | The value for this element is copied from the Digital Capability Publisher values when using dynamic discovery. |
eb:Action | The value for this element is copied from the Digital Capability Publisher values when using dynamic discovery. |
eb:ConversationId | A unique identifier to track a message though the system. This value MUST be a universally unique identifier as described by RFC4122 (Leach, Mealling, & Salz, 2005). |

**eb:Messaging/eb:UserMessage/eb:PayloadInfo/eb:PartInfo** 
| | |
| ---| ----|
@href |Reference to the MIME part |@href |Reference to the MIME part |----|@href |Reference to the MIME part |

**eb:Messaging/eb:UserMessage/eb:PayloadInfo/eb:PartInfo/eb:PartProperties                                                           These are generic values for attached payloads. Each payload must be compressed as required by the Profile.**
| | |
| ---| ----|
eb:Property@name | CompressionType |
eb:Property | application/gzip |


### 10.2.1 Example User Message 

![usermessage_Logo](/images/usermessage-example.PNG)


## 10.3 Signal Response Message 
A signal response message must be returned by the receiving Access Point. The RefToMessageId value is populated with the value of the MessageId element from the received user message.
Non repudiation of receipt is not required in the Profile. Non repudiation of receipt is a business concern and support in this messaging protocol has been removed. 
  
| | |
| ---| ----|
**eb:Messaging/eb:SignalMessage/eb:MessageInfo** |
eb:Timestamp | The REQUIRED Timestamp element has a value representing the date at which the message header was created, and is conforming to a dateTime (W3C, 2012). It MUST be expressed as UTC. Indicating UTC in the Timestamp element by including the 'Z' identifier is optional. E.g. 2016-07-01T00:00:00 |
eb:MessageId | A unique identifier to identify a message exchange between two Access Points. It is recommended to use a universally unique identifier which can be achieved using a UUID (Leach, Mealling, & Salz, 2005). |
eb:RefToMessageId | This value is copied from the incoming user message. |

### 10.3.1 Example Response Message 

![responsemessage_Logo](/images/responsemessage-example.PNG) 


## 10.4 Error Message 
All standard ebMS3 and AS4 error codes are supported by this Profile. Table 3 summarises the possible errors that can arise from use of the Council’s ebMS3/AS4 Profile. It includes errors specified in section 6.7.1 ebMS Processing Errors (OASIS, 2007) and errors from the AS4 Profile (OASIS, 2013). It does not include errors from sections 6.7.2 Security Processing Errors, 6.7.2 Reliable Messaging Errors and errors from OASIS ebXML Messaging Services Version 3.0: Part 2, Advanced Features (OASIS, 2011). 

| | |
| ---| ----|
**eb:Messaging/eb:SignalMessage/eb:MessageInfo** |
eb:Timestamp |The REQUIRED Timestamp element has a value representing the date at which the message header was created, and is conforming to a dateTime (W3C, 2012). It MUST be expressed as UTC. Indicating UTC in the Timestamp element by including the 'Z' identifier is optional. E.g. 2016-07-01T00:00:00 |
eb:MessageId | A unique identifier to identify a message exchange between two Access Points. It is recommended to use a universally unique identifier which can be achieved using a UUID (Leach, Mealling, & Salz, 2005). |
**eb:Messaging/eb:SignalMessage/eb:Error**|
@origin | ebMS |
@category | Depends on the error code |
@errorCode | ebMS3/AS4 error code |
@severity | Depends on the error code |
@refToMessageInError | Copied of eb:MessageId from the incoming user message. |
eb:Description | A human readable description of the error. |



*Table 3: Subset of ebMS3 and AS4 Error Codes applicable for this Profile* 

| | | | | |
| ---| ----| ----| ----| ----|
**Error Code**| **Short Description** | **Recommended Severity** | **Category Value** | **Description or Semantics**|
EBMS:0001 | ValueNotRecognised | Failure | Content | Although the message document is well formed and schema valid, some elements/attribute contains a value that could not be recognised and therefore could not be used by the MSH |
EBMS:0002 | FeatureNotSupported | Warning | Content | Although the message document is well formed and schema valid, some element/attribute value cannot be processed as expected because the related feature is not supported by the MSH |
EBMS:0003 | ValueInconsistent | Failure | Content | Although the message is well formed and schema valid, some element/attribute is inconsistent either with the content of other element/attribute, or with, or with the processing mode of the MSH, or with the normative requirements of the ebMS specification. |
EBMS:0004 | Other | Failure | Content | An error has occurred that has prevented the message from being correctly processed. A short description SHOULD BE provided by the MSH with this error |
EBMS:0005 | ConnectionFailure | Failure | Communication | The MSH is experiencing temporary or permanent failure in trying to open a transport connection with a remote MSH |
EBMS:0006 | | | |Not supported |
EBMS:0007 | MimeInconsistency |Failure  | Unpackaging | The use of MIME is not consistent with the required usage in this specification |
EBMS:0008  | FeatureNotSupported | Failure | Unpackaging | Although the message is well formed and schema valid, the presence or absence of some element/attribute is not consistent with the capability of the MSH, with respect to the supported features. |
EBMS:0009 | InvalidHeader | Failure | Unpackaging | The ebMS header is either not well formed as an XML document, or does not conform to the ebMS packaging rules. |
EBMS:0010 | ProcessingModeMismatch | Failure | Processing | The ebMS header or another header expected by the MSH is not compatible with the expected content, based on the associated PMode. |
EBMS:0011 | ExternalPayloadError | Failure | Content | The MSH is unable to resolve an external reference (i.e. a Part that is not contained within the ebMS Message, as identified by a PartInfo/ref URI) |
EBMS:0301 | MissingReceipt | Failure | Communication | A receipt has not been received for a message that was previously sent by the MSH generating this error |
EBMS:0302 | InvalidReceipt | Failure | Communication | A Receipt has been received for a message that was previously sent by the MSH generating this error, but the content does not match the message content. |
EBMS:0303 | DecompressionFailure | Failure | Communication | An error occurred during the decompression |

### 10.4.1 Example Error Message 

![errormessage_Logo](/images/errormessage-example.PNG)



 




