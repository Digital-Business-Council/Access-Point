# 10. Generic settings 

This section defines the common settings for exchanging messages within the Council’s Framework. 

## 10.1 PMode Settings 

A list of base PMode settings are listed in Appendix A.1 Base Agreement. 

## 10.2 User message 


| | |
| ---| ----|
**eb:Messaging/eb:UserMessage/eb:MessageInfo** |
eb:Timestamp | The REQUIRED Timestamp element has a value representing the date at which the message header was created, and is conforming to a dateTime (W3C, 2012). It MUST be expressed as UTC. Indicating UTC in the Timestamp element by including the 'Z' identifier is optional. E.g. 2016-07-01T00:00:00 |
eb:MessageId |  unique identifier to identify a message exchange between two Access Points. It is recommended to use a universally unique identifier which can be achieved using a UUID (Leach, Mealling, & Salz, 2005). |
**eb:Messaging/eb:UserMessage/eb:PartyInfo**|
eb:From/eb:PartyId@type | The party ID type uses scheme identifiers from the iso6523 catalog. urn:oasis:names:tc:ebcore:partyid-type:iso6523:<iso6523 scheme> |
eb:From/eb:PartyId | The value of the PartyId element depends on the type. |
eb:From/eb:Role | http://docs.oasis-open.org/ebxml-msg/ebms/v3.0/ns/core/200704/defaultRole |
eb:To/eb:PartyId@type | The party ID type uses scheme identifiers from the iso6523 catalog. urn:oasis:names:tc:ebcore:partyid-type:iso6523:<iso6523 scheme> |
eb:To/eb:PartyId | The value of the PartyId element depends on the type. |
eb:To/eb:Role | http://docs.oasis-open.org/ebxml-msg/ebms/v3.0/ns/core/200704/defaultRole |
**eb:Messaging/eb:UserMessage/eb:CollaborationInfo**|
eb:AgreementRef | http://resources.digitalbusinesscouncil.com.au/dbc/services/exchange/ebms3profile/current |
eb:Service | The value for this element is copied from the Digital Capability Publisher values when using dynamic discovery. |
eb:Action | The value for this element is copied from the Digital Capability Publisher values when using dynamic discovery. |
eb:ConversationId | A unique identifier to track a message though the system. This value MUST be a universally unique identifier as described by RFC4122 (Leach, Mealling, & Salz, 2005). |




