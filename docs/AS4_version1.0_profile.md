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
