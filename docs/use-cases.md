# 6. Use Cases

This document describes the method of exchange for business documents between two Access Points. Access Points use business discovery services, implemented by DCL and DCP, to determine the receiver of an electronic business document. Access Points therefore act as clients to business discovery services. The DCP and DCL business discovery services are detailed in separate implementation guides. 

The use cases listed in this section are separated in two categories: 
 1. Use cases dealing with the actual operation of sending and receiving business documents; and 
 2. Use cases dealing with configuration and registration of information to enable the operational use cases. 
 
## 6.1 Sending a Business Document (including Dynamic Discovery) 

![Usecase-Logo](/images/usecase-6.1.PNG)


## 6.2 Maintenance of Dynamic Discovery Information 
![Usecase2-Logo](/images/Usecase-6.2.PNG)


## 6.3 Use Case Descriptions 
The table below provides a list of business and system use cases that represent the functionality required to support the eDelivery solution. 

Table 2: Relevant Use Cases 

|  |  |  |  |  |
| --- |------- | --- | ------- | ------- |
**Use Case ID** |**Actors**| **Description** |**High Level Process**| **Present In** |
SUC002 | Digital Capability Publisher, Access Point, Digital Capability Locator | Register DCP Alias Address | Maintenance | Implementation guides for: Access Point, Digital Capability Publisher and Digital Capability Locator |
SUC003 | Access Point, Digital Capability Publisher | Register Capability | Maintenance | Implementation guides for: Digital Capability Publisher and Access Point |
SUC005 | Access Point, Digital Capability Publisher, Digital Capability Locator | Lookup Participant's Digital Capabilities (this includes SUC006) | Sending a business document | Implementation guides for: Access Point, Digital Capability Publisher and Digital Capability Locator |
SUC006 | Access Point, Digital Capability Locator | Lookup DCP Alias Address | Sending a business document | Implementation guides for: Access Point and Digital Capability Locator |
SUC013 | Access Point, Digital Capability Publisher, Digital Capability Locator | Remove DCP Alias Address | Maintenance | Implementation guides for: Access Point, Digital Capability Publisher and Digital Capability Locator |
SUC014 | Access Point, Digital Capability Publisher | Update Capability | Maintenance | Implementation guides for: Digital Capability Publisher and Access Point |
SUC015 | Access Point, Digital Capability Publisher | Remove Capability | Maintenance | Implementation guides for: Digital Capability Publisher and Access Point |
SUC018 | Access Point, Business/Sender, Digital Capability Locator | List accredited Access Points |eDelivery on boarding / Maintenance | Implementation guides for: Digital Capability Locator and Access Point |


|  |  |  |  |  |
| --- |------- | --- | ------- | ------- |
**Use Case ID** |**Actors**| **Description** |**High Level Process**| **Present In** |
BUC033 | Access Point, Digital Capability Publisher, Digital Capability Locator | List of Participant’s Digital Capabilities (Note: looking up all a participant’s capabilities is optional, and could be used by the sender to determine a trading partner’s ability to receive business documents) (this includes SUC006) | Maintenance/ Sending a business document | Implementation guides for: Digital Capability Locator, Digital Capability Publisher and Access Point |
BUC036 | Access Point, Digital Capability Publisher, Digital Capability Locator |Business On-boarding (Note: this includes a business new to eInvoicing or a business changing a service provider) (this includes SUC002, SUC003, SUC014) | eDelivery On-boarding / Maintenance | Implementation guides for: Access Point, Digital Capability Publisher and Digital Capability Locator 
BUC100 | Access Point, Digital Capability Publisher, Digital Capability Locator | Send Business Document to Recipient (this includes SUC005) | Sending a business document | Implementation guides for: Access Point , Digital Capability Publisher and Digital Capability Locator |

This document addresses BUC100 which is the main responsibility of Access Points i.e. sending and receiving business documents and messages. Access points are also responsible for the maintenance of business capability information in the business discovery components. These services are detailed in the respective implementation guides. 
