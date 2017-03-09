# 8. Identifiers 

The Access Point needs a set of identifiers to determine the recipient of a message exchange (Digital Business Council, 2016c). These values need to be provided to the Access Point, the detail of how this is done is implementation specific and hence not described in this document.

## 8.1 Party Identifier 
Party identifiers are used in the following instances: 
 - Querying DNS for a DCP endpoint (Digital Business Council, 2016a); 
 - Querying DCP for a list of capabilities (Digital Business Council, 2016b); and 
 - Identifying participants of a message exchange. 

Party identifiers align to ebCore Party Id (OASIS, 2010). The format is: 

*Type:* urn:oasis:names:tc:ebcore:partyid-type:iso6523:<scheme id> 

*Value:* <identifier> 

**Example:** 

In this case an Australian ABN is used, ISO 6523 scheme is 0151, and the identifier is the ABN. 



| | | 
| --- |------- |
**Term** |**Definition**| 
Business Process | A 
