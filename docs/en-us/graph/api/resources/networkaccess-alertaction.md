<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-alertaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-31 -->

# alertAction resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a suggested action for admins to take for a given Global Secure Access [alert](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-alert?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actionLink | String | A link to more information or to perform the action \(if applicable\). |
| actionText | String | Text describing the action. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.alertAction",
  "actionText": "String",
  "actionLink": "String"
}
```
