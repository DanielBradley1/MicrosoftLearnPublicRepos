<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/awsassociatedidentities?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# awsAssociatedIdentities resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

A container for the different kinds of AWS identities.

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| all | [awsIdentity](https://learn.microsoft.com/en-us/graph/api/resources/awsidentity?view=graph-rest-beta) collection | The list of all AWS identities. |
| roles | [awsRole](https://learn.microsoft.com/en-us/graph/api/resources/awsrole?view=graph-rest-beta) collection | The list of AWS roles. |
| users | [awsUser](https://learn.microsoft.com/en-us/graph/api/resources/awsuser?view=graph-rest-beta) collection | The list of AWS users. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.awsAssociatedIdentities"
}
```
