<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/partner-security-affectedresource?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-08 -->

# affectedResource resource type

Namespace: microsoft.graph.partner.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Contains details of the resources that are affected by a security alert.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| resourceId | String | The resource path of the resource affected by the security alert. |
| resourceType | String | The type of resource. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.partner.security.affectedResource",
  "resourceId": "String",
  "resourceType": "String"
}
```
