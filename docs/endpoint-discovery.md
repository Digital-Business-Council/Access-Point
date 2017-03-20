# 9. Endpoint Discovery 
All document exchanges between corners two and three, including dynamic discovery of endpoints, follow a process similar to Figure 7. This implementation guide does not describe how these steps are executed. Dynamic discovery of endpoints changes the way an endpoint is identified. 

The endpoint address of a message exchange is determined by querying the Digital Capability Publisher with the following identifiers: 
 - Recipient Party ID 
 - Document ID 

This returns a signed service metadata structure with a list of processes. Each process has a list of endpoints. A process is identified by a process ID, the endpoint is identified by the transport Profile. 

![Dynamic-discover_Logo](/images/Endpoint-discovery.PNG)
