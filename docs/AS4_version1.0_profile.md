# 7. AS4 Version 1.0 Profile (Normative) 

The standards used in the Access Point Implementation Guide are based on freely available open standards. This section describes the Profile of these standards to make the standard suitable for Australian B2B messaging. 

## 7.1 Messaging Model 
The messaging model in Figure 5 illustrates the following entities: 

   - **Message Producer:** Business applications or middleware submit message content to the sending Message Service Handler (MSH). A business user typically interacts with the business application and has no knowledge of the MSH; 
   - **Sending Message Service Handler:** The sending MSH packages the message content and sends the message to the intended receiving MSH; 
   - **Receiving Message Service Handler:** The receiving MSH receives a message from the sending MSH. The message includes the content which is delivered to the message consumer; and 
   - **Message Consumer:** The message consumer is the receiver of the business content. 

![Messaging-model_Logo](/images/Messaging-model.PNG)

The receiving MSH can be the initiator of the message exchange in the case of pulling a message from the sending MSH. In this Profile however, the sending MSH is always the initiating MSH. The interface between message producer and sending MSH or receiving MSH and message consumer is implementation specific and not defined in this Profile. 

## 7.2 AS4 ebHandler Profile 
This specification is based on the OASIS standard AS4 ebHandler Profile of ebMS 3.0 Version 1.0 (OASIS, 2013) and provides further guidelines on the use of the Profile in the Australian B2B context. This specification has precedence over the OASIS AS4 standard. 

AS4 defines several conformance Profiles each addressing certain use cases. The Profile suitable for use by Access Points is the ebHandler Profile. Other Profiles support occasionally connected endpoints and are useful for sending messages between corners 1 and 2 or 3 and 4. These Profiles are not included in this document. 

It should be noted that conforming to this Profile does not mean conformance to the AS4 standard. However, if an implementation conforms to the AS4 standard, it will also conform to this Profile. 

### 7.2.1 Message Exchange Patterns 
Access Points act as network nodes and are expected to always be connected to the network. It is therefore NOT REQUIRED for Access Points to support pulling of messages when receiving messages from other Access Points. 

Although ebMS3 supports choreography of message exchanges, choreography of business processes SHOULD be handled by the business applications. ebMS3 MessageId’s correlate messages between two Message Service Handlers and do not carry over to other sections of a transmission (e.g. from corner 3 to corner 4). A two-way Message Exchange Pattern is therefore NOT REQUIRED in the messaging protocol. In this Profile, MessageId and RefToMessageId are only used to correlate signal response messages to user messages. ConversationId is mandatory as per the ebMS3 standard. This element MUST be populated with a tracking identifier. 

Support is REQUIRED for the following Message Exchange Pattern: 
 
 1. **One Way/Push:** The sending of an eb:Receipt MUST be supported to allow reliable messaging as per the AS4 standard. This Profile only REQUIRES support for the ‘response’ reply pattern. An eb:Receipt or eb:Error signal message is returned on the back-channel of the underlying transport protocol. 

As this Profile is defined in the context of a four-corner model, support for multi-hop message routing (OASIS, 2011) is NOT REQUIRED.

### 7.2.2 Message Partitioning 
Pulling of messages is NOT REQUIRED for this Profile when sending or receiving between Access Points which negates the need for message partition channels. If business applications are required to directly submit or receive messages, support for message partitioning is RECOMMENDED. 

### 7.2.3 Message Packaging 
The Council’s AS4 message structure includes a standard message header based on SOAP and MIME enveloping. This Profile does not support payloads in the SOAP body element, all payloads are encoded as MIME parts, including the SOAP envelope as per section 5.1.1 of the ebMS3 standard (OASIS, 2007, p. 34). 

![Messagepackagining_Logo](/images/Message-packaging.PNG)

A message is either a user message or a signal message. Multiple payloads MAY be present and relate to PayloadInfo elements. 
Payloads MUST be compressed according to the AS4 Additional Features Compression section 3.1 (OASIS, 2013, p. 24). The size of a message, including compressed payloads, MUST NOT exceed 10 megabytes. Support for large message splitting and joining of messages as defined in (OASIS, 2011) is NOT REQUIRED. 

### 7.2.4 User Message 
Only one user message is allowed in the SOAP header. The user message describes the transport of business information and includes sender and receiver information. 

### 7.2.5 Signal Message 
Signal messages do not carry a user message. A signal message is used as a response to a user message. A response can be an acknowledgement of a receipt or an error. The RefToMessageId will refer to the user message for which the response is sent. 

### 7.2.6 Error Handling
Errors MUST be reported as a response to a request. Sending errors as a separate request is NOT REQUIRED. 

### 7.2.7 Security
Access Points MUST implement security measures when using the public internet for message exchanges. 

#### 7.2.7.1 Transport Layer Security 
Transport layer security provides message confidentiality between Access Points. Implementations MUST support TLS version 1.2. Fallback to or earlier versions of TLS or SSL MUST NOT be used. TLS versions with known vulnerabilities MUST NOT be used. 
Ciphers that offer perfect forward secrecy are RECOMMENDED when configuring TLS. 
Access Points are REQUIRED to implement mutual exchange of certificates (Dierks & Rescorla, 2008, p. 55). Receiving Access Points MUST only process messages from Access Points that send a known client certificate. Client and server certificates are published in the Digital Capability Locator (Digital Business Council, 2016a). These certificates SHOULD be used to verify peer certificates. 

#### 7.2.7.2 Message Layer Security 
Encryption and signing of business messages is the responsibility of business systems and is NOT REQUIRED for this Profile between Access Points. 

### 7.2.8 Reliable Messaging and Reception Awareness
When a receiving MSH is not available due to unforseen errors, reliability and reception awareness ensure the message will be delivered once the receiving MSH becomes available. This is enabled by REQUIRING receipts on the synchronous return leg of the transport protocol. Reception awareness errors SHOULD BE reported to the message producer. 

### 7.2.9 Extension Properties 
This standard allows the use of Message Properties and Part Properties. The use of these properties must be agreed between partners. 
Processing Mode Parameters 

### 7.2.10 Processing Mode Parameters 
This section contains a summary of PMode parameters relevant to AS4 features for this conformance Profile. An AS4 handler MUST support and understand those that are mentioned as ‘required’. For each parameter, either: 
 - Full support is required: An implementation MUST support the possible options for this parameter. 
 - Partial support is required: Support for a subset of values is required. 
 - No support is required: An implementation is not required to support the features controlled by this parameter, and therefore is not required to understand this parameter. 

An AS4 handler is expected to support the PMode set below both as a Sender (of the user message) and as a Receiver. 

#### 7.2.10.1 General PMode parameters 
 - **PMode.ID:** support not required 
    PMode.ID is required by AS4 but not required by this Profile. 
    PModes are identified by the PMode.Agreement setting 
 - **PMode.Agreement:** support required 
 - **PMode.MEP:** support required for: http://www.oasis-open.org/committees/ebxml-msg/one-way 
 - **PMode.MEPbinding:** support required for: http://www.oasis-open.org/committees/ebxml-msg/push 
 - **PMode.Initiator.Party:** support required 
 - **PMode.Initiator.Role:** support required for: http://docs.oasis-open.org/ebxml-msg/ebms/v3.0/ns/core/200704/defaultRole 
 - **(PMode.Initiator.Authorization.username** and **PMode.Initiator.Authorization.password):** support not required 
 - **PMode.Responder.Party:** support required 
 - **PMode.Responder.Role:** support required for: http://docs.oasis-open.org/ebxml-msg/ebms/v3.0/ns/core/200704/defaultRole 
 - **(PMode.Responder.Authorization.username** and **PMode.Responder.Authorization.password):** support not required 


#### 7.2.10.2 PMode[1].Protocol 
 - **PMode[1].Protocol.Address:** support required for ‘http’ protocol 
 - **PMode[1].Protocol.SOAPVersion:** support required for SOAP 1.2 


#### 7.2.10.3 PMode[1].BusinessInfo 
 - **PMode[1].BusinessInfo.Service:** support required 
 - **PMode[1].BusinessInfo.Action:** support required 
 - **PMode[1].BusinessInfo.Properties[]:** support not required 
 - **PMode[1].BusinessInfo.PayloadProfile[]:** support not required 
 - **PMode[1].BusinessInfo.PayloadProfile.maxSize:** support required for 10000 kilobytes 


#### 7.2.10.4 PMode[1].ErrorHandling 
 - **PMode[1].ErrorHandling.Report.SenderErrorsTo:** support not required 
 - **PMode[1].ErrorHandling.Report.ReceiverErrorsTo:** support not required 
 - **PMode[1].ErrorHandling.Report.AsResponse:** support required (true). 
 - **PMode[1].ErrorHandling.Report.ProcessErrorNotifyConsumer:** support not required 
 - **PMode[1].ErrorHandling.Report.ProcessErrorNotifyProducer:** support required (true/false) 
 - **PMode[1].ErrorHandling.Report.DeliveryFailuresNotifyProducer:** support required (true/false) 


#### 7.2.10.5 PMode[1].Reliability 
Support not required. 


#### 7.2.10.6 PMode[1].Security 
 - **PMode[1].Security.WSSVersion:** support not required 
 - **PMode[1].Security.X509.Sign:** support not required 
 - **PMode[1].Security. X509.Encryption:** support not required 
 - **PMode[1].Security.UsernameToken:** support not required 
 - **PMode[1].Security.PModeAuthorize:** support required (false) 
 - **PMode[1].Security.SendReceipt:** support required (true) 
 - **PMode[1].Security.SendReceipt.NonRepudiation:** support required (false) 


#### 7.2.10.7 PMode[1].PayloadService 
 - **PMode[1].PayloadService.CompressionType:** support required for application/gzip 


#### 7.2.10.8 PMode[1].ReceptionAwareness 
 - **PMode[1].ReceptionAwareness:** support required and when set to true, the **PMode[1].Security.SendReceipt** must also be set to true 
 - **PMode[1].ReceptionAwareness.Retry:** support required 
 - **PMode[1].ReceptionAwareness.Retry.Parameters:** support required 
 - **PMode[1].ReceptionAwareness.DuplicateDetection:** support required 
 - **PMode[1].ReceptionAwareness.DetectDuplicates.Parameters:** support required. 
 
