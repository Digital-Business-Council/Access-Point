# APPENDIX A: PMode Parameters 
## A.1 Base Agreement 

This list of PMode parameters defines the default values on which other agreements are based. Other agreements may override these settings if required. 

| | | 
| --- |------- |
**General PMode Parameters** | | 
PMode.Agreement |http://resources.digitalbusinesscouncil.com.au/dbc/services/ exchange/ebms3profile/current |
PMode.MEP | http://www.oasis-open.org/committees/ebxml-msg/one-way |
PMode.MEPbinding | http://www.oasis-open.org/committees/ebxml-msg/push |
PMode.Initiator.Party | Determined by the message producer |
PMode.Initiator.Role | http://docs.oasis-open.org/ebxml-msg/ebms/v3.0/ns/ core/200704/defaultRole |
PMode.Responder.Party | Determined by the message producer. |
PMode.Responder.Role | http://docs.oasis-open.org/ebxml-msg/ebms/v3.0/ns/ core/200704/defaultRole |
**PMode[1].Protocol**| |
PMode[1].Protocol.Address | Receiving Access Point URL. Determined from DCL/DCP lookup |
PMode[1].Protocol.SOAPVersion | 1.2 |
PMode[1].BusinessInfo.Service | The value for this element is copied from the Digital Capability Publisher values when using dynamic discovery. |
PMode[1].BusinessInfo.Action | The value for this element is copied from the Digital Capability Publisher values when using dynamic discovery. |
PMode[1].BusinessInfo.PayloadProfile.maxSize | 10000 (kilobytes) |
**PMode[1].ErrorHandling** | |
PMode[1].ErrorHandling.Report.AsResponse | true |
**PMode[1].Security** | |
PMode[1].Security.PModeAuthorize | false |
PMode[1].Security.SendReceipt | true |
PMode[1].Security.SendReceipt.NonRepudiation | false |
PMode[1].ErrorHandling.Report.ProcessError NotifyProducer | true |
PMode[1].ErrorHandling.Report.DeliveryFailures NotifyProducer | true |
Pmode[1].Security.SendReceipt.ReplyPattern | response |
**PMode[1].PayloadService** | |
PMode[1].PayloadService.CompressionType | application/gzip |
PMode[1].ReceptionAwareness | true |
PMode[1].ReceptionAwareness.Retry | true |
PMode[1].ReceptionAwareness.Retry.| maxretries=3;period=120000 |
Parameters | Period is two minutes which corresponds to the lowest SLA value for response. |
PMode[1].ReceptionAwareness.Duplicate Detection | true |
PMode[1].ReceptionAwareness.DetectDuplicates. Parameters | maxsize=10Mb;checkwindow=7D. Maximum log size is 10Mb for checking. Duplicate check window is guaranteed of seven days minimum. 





