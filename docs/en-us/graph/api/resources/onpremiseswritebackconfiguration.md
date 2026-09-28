<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onpremiseswritebackconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-10-03 -->

# onPremisesWritebackConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Configuration in the [onPremisesDirectorySynchronization resource](https://learn.microsoft.com/en-us/graph/api/resources/onpremisesdirectorysynchronization?view=graph-rest-beta) to control how cloud created or owned objects are synchronized back to the on-premises directory.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| unifiedGroupContainer | String | The distinguished name of the on-premises container that the customer is using to store unified groups which are created in the cloud. |
| userContainer | String | The distinguished name of the on-premises container that the customer is using to store users which are created in the cloud. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.onPremisesWritebackConfiguration",
  "unifiedGroupContainer": "String",
  "userContainer": "String"
}
```
