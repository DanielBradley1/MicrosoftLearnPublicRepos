<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-applicationsnapshot?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-04-11 -->

# applicationSnapshot resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents details about the destination application accessed during a network transaction.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| appId | String | The unique identifier of the application accessed during the transaction. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.applicationSnapshot",
  "appId": "String"
}
```
