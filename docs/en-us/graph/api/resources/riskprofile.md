<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/riskprofile?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# riskProfile resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Contains information for human and workload identity counts in a specific risk bucket.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| humanCount | Int32 | This is the count of human identities that have been assigned to this riskScoreBracket, |
| nonHumanCount | Int32 | This is the count of nonhuman identities that have been assigned to this riskScoreBracket |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.riskProfile",
  "humanCount": "Integer",
  "nonHumanCount": "Integer"
}
```
