# 7. AS4 Version 1.0 Profile (Normative) 

The standards used in the Access Point Implementation Guide are based on freely available open standards. This section describes the Profile of these standards to make the standard suitable for Australian B2B messaging. 

## 7.1 Messaging Model 
The messaging model in Figure 5 illustrates the following entities: 
 - **Message Producer:** Business applications or middleware submit message content to the sending Message Service Handler (MSH). A business user typically interacts with the business application and has no knowledge of the MSH; 
 - **Sending Message Service Handler:** The sending MSH packages the message content and sends the message to the intended receiving MSH; 
 - **Receiving Message Service Handler:** The receiving MSH receives a message from the sending MSH. The message includes the content which is delivered to the message consumer; and 
 - **Message Consumer:** The message consumer is the receiver of the business content. 

![Messaging-model_Logo] (/images/Messaging-model.PNG)

The receiving MSH can be the initiator of the message exchange in the case of pulling a message from the sending MSH. In this Profile however, the sending MSH is always the initiating MSH. The interface between message producer and sending MSH or receiving MSH and message consumer is implementation specific and not defined in this Profile. 

## 7.2 AS4 ebHandler Profile 
This specification is based on the OASIS standard AS4 ebHandler Profile of ebMS 3.0 Version 1.0 (OASIS, 2013) and provides further guidelines on the use of the Profile in the Australian B2B context. This specification has precedence over the OASIS AS4 standard. 

AS4 defines several conformance Profiles each addressing certain use cases. The Profile suitable for use by Access Points is the ebHandler Profile. Other Profiles support occasionally connected endpoints and are useful for sending messages between corners 1 and 2 or 3 and 4. These Profiles are not included in this document. 

It should be noted that conforming to this Profile does not mean conformance to the AS4 standard. However, if an implementation conforms to the AS4 standard, it will also conform to this Profile. 

### 7.2.1 Message Exchange Patterns 
Access Points act as network nodes and are expected to always be connected to the network. It is therefore NOT REQUIRED for Access Points to support pulling of messages when receiving messages from other Access Points. 

Although ebMS3 supports choreography of message exchanges, choreography of business processes SHOULD be handled by the business applications. ebMS3 MessageId’s correlate messages between two Message Service Handlers and do not carry over to other sections of a transmission (e.g. from corner 3 to corner 4). A two-way Message Exchange Pattern is therefore NOT REQUIRED in the messaging protocol. In this Profile, MessageId and RefToMessageId are only used to correlate signal response messages to user messages. ConversationId is mandatory as per the ebMS3 standard. This element MUST be populated with a tracking identifier. 

Support is REQUIRED for the following Message Exchange Pattern: 
 1. **One Way/Push** 
 The sending of an eb:Receipt MUST be supported to allow reliable messaging as per the AS4 standard. This Profile only REQUIRES support for the ‘response’ reply pattern. An eb:Receipt or eb:Error signal message is returned on the back-channel of the underlying transport protocol. 

As this Profile is defined in the context of a four-corner model, support for multi-hop message routing (OASIS, 2011) is NOT REQUIRED.

### 7.2.2 Message Partitioning 
Pulling of messages is NOT REQUIRED for this Profile when sending or receiving between Access Points which negates the need for message partition channels. If business applications are required to directly submit or receive messages, support for message partitioning is RECOMMENDED. 

### 7.2.3 Message Packaging 
The Council’s AS4 message structure includes a standard message header based on SOAP and MIME enveloping. This Profile does not support payloads in the SOAP body element, all payloads are encoded as MIME parts, including the SOAP envelope as per section 5.1.1 of the ebMS3 standard (OASIS, 2007, p. 34). 

![Messagepackagining_Logo] (/images/Message-packaging.PNG)

A message is either a user message or a signal message. Multiple payloads MAY be present and relate to PayloadInfo elements. 
Payloads MUST be compressed according to the AS4 Additional Features Compression section 3.1 (OASIS, 2013, p. 24). The size of a message, including compressed payloads, MUST NOT exceed 10 megabytes. Support for large message splitting and joining of messages as defined in (OASIS, 2011) is NOT REQUIRED. 
