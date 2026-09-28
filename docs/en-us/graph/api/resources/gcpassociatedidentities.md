<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/gcpassociatedidentities?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# gcpAssociatedIdentities resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

A container for different kinds of GCP identities.

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| all | [gcpIdentity](https://learn.microsoft.com/en-us/graph/api/resources/gcpidentity?view=graph-rest-beta) collection | The list of GCP identities. |
| serviceAccounts | [gcpServiceAccount](https://learn.microsoft.com/en-us/graph/api/resources/gcpserviceaccount?view=graph-rest-beta) collection | The list of GCP service accounts. |
| users | [gcpUser](https://learn.microsoft.com/en-us/graph/api/resources/gcpuser?view=graph-rest-beta) collection | The list of GCP users. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.gcpAssociatedIdentities"
}
```
