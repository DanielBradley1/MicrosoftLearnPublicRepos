<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/services -->
<!-- Sitemap-Last-Modified: 2022-07-06 -->

# Supporting services

The following services are used internally within the Microsoft environment to support coauthoring provided as part of the Cloud Storage Partner Program \(CSPP\) Plus program tier.

## Office Collaboration Service \(OCS\)

The Office Collaboration Service \(OCS\) is part of CSPP Plus when two or more users are collaborating on a document at the same time. OCS isn't required for coauthoring.

OCS improves coauthoring performance, reduces load on the host by allowing clients to exchange coauthoring edits quickly amongst themselves, and greatly increases the number of supported active coauthors. OCS can also merge changes from multiple users, as needed. OCS saves these accumulated edits to the host on a regular basis.

Clients initially connect to the host directly, then transition to OCS when real-time collaboration is needed. In some cases, clients can transition back out of OCS into host-mode collaboration. Most document editing doesn't start an OCS session and the use of the OCS service is transparent to both end-users and hosts.

OCS is a part of CSPP Plus for Office for Desktop, Office for the web, and Microsoft 365 for mobile.

### OCS session start

An OCS *session*, which is an internal construct within the OCS service, keeps active coauthoring document state on behalf of one or more end-users.

A session starts in the following scenarios:

- A second client joins the document. This could be another user, the same user editing the same document on a different device, or, if on the web, a different browser tab. Additional clients that open the document can connect to the already established OCS session.
- Local internet connectivity has recently been restored.
- Five minutes have elapsed since the last OCS session failure.

Applications can disable OCS transitions in certain scenarios where they can't support OCS coauthoring. For example, Word doesn't support OCS for .docm documents. In these cases, applications would continue to save their changes to the host directly.

### Client transition out of OCS

Clients can transition out of an OCS session for the following reasons:

- The OCS session has ended due to a fatal service error.
- The client's transition to OCS has failed.
- All other users have left the document and five minutes have elapsed.
- OCS incompatible content was added to the document.
- The user has lost permissions to the document or the user’s access token for the document is about to expire.

## Real Time Channel \(RTC\) service

The Real Time Channel \(RTC\) service provides real-time peer-to-peer connectivity between clients participating in an Office document coauthoring session.

The RTC service supports the following:

- Accelerated transfer of coauthoring changes and typing between clients.
- Information about presence in the document by other users, such as cursor location, display of users in the *Coauth Gallery*, and so on.
