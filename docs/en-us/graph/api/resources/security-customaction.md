<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-customaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# customAction resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents any custom actions that a label may provide, if configured by the administrator. Custom actions might be defined as part of an [sensitivityLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-sensitivitylabel?view=graph-rest-beta) via the Microsoft 365 Security and Compliance Center module for PowerShell. The consuming application must understand the actions.

Inherits from [informationProtectionAction](https://learn.microsoft.com/en-us/graph/api/resources/security-informationprotectionaction?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| name | String | Name of the custom action. |
| properties | [keyValuePair](https://learn.microsoft.com/en-us/graph/api/resources/keyvaluepair?view=graph-rest-beta) collection | Properties, in key-value pair format, of the action. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.customAction",
  "name": "String",
  "properties": [
    {
      "@odata.type": "microsoft.graph.security.keyValuePair"
    }
  ]
}
```
