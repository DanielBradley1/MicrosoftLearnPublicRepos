<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/gcpscope?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# gcpScope resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Represents the service and resource type of a GCP resource. For example, a compute instance resource has a `compute` **service** and `instances` **resourceType**.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| resourceType | String | Type of GCP resource. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| service | [authorizationSystemTypeService](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemtypeservice?view=graph-rest-beta) | Service associated with a resource in an authorization system. This is auto-expanded. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.gcpScope",
  "resourceType": "String"
}
```
