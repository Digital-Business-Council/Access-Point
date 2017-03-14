# APPENDIX B: Use Cases 
## BUC100 Send Business Document to Recipient 

### Purpose 
This high level use case describes the end to end process of sending a business document to a recipient. 

### Assumptions 
N/A 

### Preconditions 
 1. The Sender, Recipient, Capability Publisher and the Access Points are participants in eDelivery. 

### Post conditions 
 1. The recipient receives the Sender’s business document successfully. 

### Basic Flow 
 1. The Sender populates the business document with the required information (identifier and scheme, document type and process); 
 2. The Sender sends the business document to their Access Point; 
 3. The sending Access Point performs the business discovery process to obtain the capability of the recipient (which includes obtaining the service endpoint of the receiving Access Point): a. <<include>> SUC005 – Lookup Participant’s Digital Capability; 
 4. The sending Access Point sends the business document to the recipient’s nominated Access Point for the business document type; 
 5. The receiving Access Point receives the business document successfully; 
 6. The receiving Access Point sends the business document to the recipient; 
 7. The recipient receives the business document from their nominated Access Point successfully; 
 8. End flow. 
 
## BUC033 List Participant’s Capabilities 

### Purpose 
This use case describes the steps required for a party, possibly a sender, to discover the entire capabilities (i.e. every process) supported by a participant. This use case is optional as it would only be useful if there were more than one process supported by a participant. It is not necessary for a Sender to discover all capabilities of a Recipient to send a business document from corners 1 to 4. 

### Assumptions 
 1. Any party, even those not participating in eDelivery, can view a Participant’s Capabilities; and 
 2. No authentication or authorisation checks are required. 

### Pre-conditions 
 1. The requester needs to know the identifier of the participant they are looking up. 

### Post-conditions 
 1. The recipient’s digital capabilities have been determined by a participant. 

### Basic Flow 
 1. The requester establishes the location of the recipient’s digital capabilities: a. <<include>> SUC006 - Lookup Participant’s DCP Alias Address; 
 2. The requester constructs the request to retrieve a recipient’s capability list; 
 3. The requester sends the request to the recipient’s Digital Capability Publisher; 
 4. The Digital Capability Publisher creates the response including the capabilities for each process the participant has in their capability record; 
 5. The requester receives the response; 
 6. End flow. 
 
## BUC036 Business On-boarding 

### Purpose 
This use case describes the process to on-board a business to a single Digital Capability Publisher and/or one or more Access Point services for eDelivery. This does not include Access Point (AP) and Digital Capability Publisher (DCP) service providers themselves, who are covered by the process described in BUC010 i.e. Service Provider On-Boarding. 

There are a number of scenarios covered by this use case: 
 1. A business is entering the eDelivery framework for the first time (new participant); and 

 2. A business changes their service provider(s) to a single or multiple service provider (noting a business can only have one DCP service provider): 
 
  a. The business moves both services from one service provider to one or more service providers. 
 
  b. The business moves only their Access Point service for a particular process to a new service provider.
 
  c. The business moves only the DCP service to a new service provider. 
 
  d. The business has AP and DCP services with separate providers and consolidates the services with one provider. 
 
  e. The business has different Service Providers for DCP and AP services, and moves each service to two new Service Providers. 
 
### Assumptions 

 1. A Service Provider can operate an Access Point and/or a Capability Register but it is not mandatory to provide both services. 

 2. Where a Service Provider can provide both services, a business can choose to use both or either service offered by the service provider. 


### Constraints 

 1. The Service Provider, when providing both services, must create and maintain the business’ DCL entry and DCP capability record. 

 2. When the business enters into agreements with a DCP service provider and one or more Access Point service providers, the DCP Service provider is responsible for coordinating, creating and maintaining the DCL entry and DCP record on behalf of the business for the duration of this arrangement as it will need all Access Point details to create the business’ Capability record in their nominated DCP. 

 3. When the business has its own Access Point, the Service Provider for DCP services is responsible for creating and maintaining the DCL entry, creating the capability record and responding to requests by the business to update the AP details the business uses as required. 

 4. In AP service provider change events, the Service Provider holding the business’ capability record must comply with AP Service Provider request to update the capability record with the new Access Point details. 

 5. As defined in the Council’s service provider agreements, the losing (Old) Service Provider must cooperate with the gaining (New) Service Provider during portability/change of service events. 

 6. Only one capability record can exist in the eDelivery framework for a participant; this record contains all the capabilities of the business. 
 
### Pre-conditions 

 1. The business has obtained an Australian Business Number (ABN) from the Australian Business Register (ABR) or a GLN, DUNS or other Council approved identifier. 

 2. The business is required to receive business documents supported by the Council and the Framework. 

 3. The New Service Provider is accredited by the Council. 
 
### Post-conditions 
 1. The business has agreements with one or more Service Providers for receiving Council supported business processes and documents through one or more Access Point providers and only one DCP provider, having either become a new participant or changed service providers. 
 
 2. The business is discoverable in the Digital Capability Locator and, if the new DCP is listed in the DCL entry. 

### Basic Flow – New Participant in eInvoicing; Business chooses to use a single Service Provider for both Access Point and DCP services. 
 1. The business determines their requirements; 
 
 2. The business investigates the services offered and pricing of various service providers; 
 
 3. The business determines the Service Provider(s) that meets their requirements; 
 
 4. The business enters an agreement with the New Service Provider; 
 
 5. The New Service Provider determines if the business’ capability is already registered in a capability register (this also determines if the client has an Access Point service in the framework also); 

 6. The business does not have an existing capability record registered and requires it to be created in the New Service Provider’s DCP; 
 
 7. The New Service Provider determines the client does not have an Access Point service and will use the New Service Provider’s AP; 
 
 8. The New Service Provider adds its own supported Access Point address, transport Profiles, document types and processes to the business’ capability record in its own Digital Capability Publisher: a. <<include>> SUC003 – Register Capability. 

 9. The New Service Provider requests the capability address (DCL entry) be added to the Digital Capability Locator: a. <<include>> SUC002 – Register Capability Address. 
 
 10. The New Service Provider informs the business the on-boarding activities have been completed; 

 11. End flow. 
 
### Alternate Flows 

 1. New Participant; Business is signing up to DCP service only (participant may have an AP of its own or is signing a separate agreement with a different AP Service Provider). 

  a. At step 6, the New Service Provider determines the Business is entering into an agreement with a different Access Point service      provider or is using its own Access Point; 

  b. The New Service Provider obtains the AP endpoint address and transport Profile it supports for each document and process, from either the Business (if using its own AP) or the Business’ AP Service Provider(s); 
  
  c. The New Service Provider creates a capability record including AP endpoint address, transport Profile, document and process types; i. <<include>> SUC003 – Register Capability. 

  d. Resume at step 9. 

 2. Existing Participant; the business is moving both services to the New Service Provider. 

  a. At step 6, the New Service Provider discovers the business has an existing DCP service that needs to be changed to the New Service 
     Provider’s DCP service; 

  b. The New Service Provider informs the Losing DCP Service Provider they are now providing the business’ DCP service; 

  c. The Losing DCP Service Provider deprecates the business’ capability record in their DCP; 

  d. The New Service Provider informs the previous Access Point service provider they are the business’ nominated Access Point service 
     provider; 

  e. The New Service Provider creates a capability record including the AP endpoint address(es), transport Profile(s), document and 
     process types; i. <<include>> SUC003 – Register Capability. 

  f. Resume at step 9. 
