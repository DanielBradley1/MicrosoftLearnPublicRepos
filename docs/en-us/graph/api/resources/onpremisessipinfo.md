<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onpremisessipinfo?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# onPremisesSipInfo resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

This complex type contains all onPremises SIP information related to the user.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isSipEnabled | Boolean | Indicates whether the user is currently enabled for on-premises Skype for Business. |
| sipDeploymentLocation | String | Indicates a fully qualified DNS name of the Microsoft Online Communications Server deployment. |
| sipPrimaryAddress | String | Serves as a unique identifier for each user on the on-premises Skype for Business. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.onPremisesSipInfo",
  "isSipEnabled": "Boolean",
  "sipDeploymentLocation": "String",
  "sipPrimaryAddress": "String"
}
```
