# 8. Identifiers 

The Access Point needs a set of identifiers to determine the recipient of a message exchange (Digital Business Council, 2016c). These values need to be provided to the Access Point, the detail of how this is done is implementation specific and hence not described in this document.

## 8.1 Party Identifier 
Party identifiers are used in the following instances: 
 - Querying DNS for a DCP endpoint (Digital Business Council, 2016a); 
 - Querying DCP for a list of capabilities (Digital Business Council, 2016b); and 
 - Identifying participants of a message exchange. 

Party identifiers align to ebCore Party Id (OASIS, 2010). The format is: 

*Type:* urn:oasis:names:tc:ebcore:partyid-type:iso6523:<scheme id> 

*Value:*  <identifier &gt; 

**Example:** 

In this case an Australian ABN is used, ISO 6523 scheme is 0151, and the identifier is the ABN.

![Party-identifier_Logo](/images/party_identifier.PNG)


## 8.2 Action Identifier 
The action identifier corresponds to the document identifier in the Digital Capability Publisher (Digital Business Council, 2016b). This value is aligned to the Profile ID in the eInvoicing Implementation Guide (section 9). 

**Example:**
![action_identifier_Logo] (/images/action-identifier.PNG)


## 8.3 Service Identifier 
The service identifier corresponds to the process identifier in the Digital Capability Publisher (Digital Business Council, 2016b). This value is aligned to the Customisation ID in the eInvoicing Implementation Guide (section 9). 
The type attribute SHOULD NOT be used. The encoding of the service values is per the Digital Capability Publisher Implementation Guide. 

**Example:**
![service-identifier_Logo] (/images/service-identifier.PNG)


## 8.4 Agreement Identifier 
Agreement value defined by the Digital Business Council: 
http://resources.digitalbusinesscouncil.com.au/dbc/services/exchange/ebms3/Profile 
