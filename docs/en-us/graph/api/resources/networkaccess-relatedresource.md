<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-relatedresource?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-31 -->

# relatedResource resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Abstract base type for related entities in Global Secure Access [alerts](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-alert?view=graph-rest-beta). This type is not intended to be instantiated directly.

This is an abstract type from which the following resources inherit:

- [relatedRemoteNetwork](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-relatedremotenetwork?view=graph-rest-beta) - Represents a remote network that was detected as unhealthy.
- [relatedThreatIntelligence](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-relatedthreatintelligence?view=graph-rest-beta) - Represents a threat intelligence that was detected.
- [relatedDestination](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-relateddestination?view=graph-rest-beta) - Represents a destination that was detected.
- [relatedTenant](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-relatedtenant?view=graph-rest-beta) - Represents a tenant that was detected.
- [relatedDevice](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-relateddevice?view=graph-rest-beta) - Represents a device that was detected.
- [relatedWebCategory](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-relatedwebcategory?view=graph-rest-beta) - Represents a web category that was detected.
- [relatedMalware](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-relatedmalware?view=graph-rest-beta) - Represents a detected malware.
- [relatedUser](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-relateduser?view=graph-rest-beta) - Represents a user involved in the alert.
- [relatedToken](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-relatedtoken?view=graph-rest-beta) - Represents a token involved in the alert.
- [relatedFile](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-relatedfile?view=graph-rest-beta) - Represents a file involved in the alert.
- [relatedFileHash](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-relatedfilehash?view=graph-rest-beta) - Represents a file hash involved in the alert.
- [relatedTransaction](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-relatedtransaction?view=graph-rest-beta) - Represents a transaction involved in the alert.
- [relatedUrl](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-relatedurl?view=graph-rest-beta) - Represents a destination URL involved in the alert.

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.relatedResource"
}
```
