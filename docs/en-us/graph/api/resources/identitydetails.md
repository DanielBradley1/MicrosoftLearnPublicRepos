<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitydetails?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# identityDetails resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Represents the details for identity findings

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | A date specifiying when the Identity was created, could be null |
| lastActiveDateTime | DateTimeOffset | A date specifiying when the Identity was active last time, could be null |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityDetails",
  "createdDateTime": "String (timestamp)",
  "lastActiveDateTime": "String (timestamp)"
}
```
