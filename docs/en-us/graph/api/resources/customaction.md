<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/customaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# customAction resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The Information Protection labels API is deprecated and will stop returning data on January 1, 2023. Please use the new [informationProtection](https://learn.microsoft.com/en-us/graph/api/resources/security-informationprotection?view=graph-rest-beta&preserve-view=true), [sensitivityLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-sensitivitylabel?view=graph-rest-beta&preserve-view=true), and associated resources.

Represents any custom actions that a label may provide, if configured by the administrator. Custom actions might be defined as part of an [informationProtectionLabel](https://learn.microsoft.com/en-us/graph/api/resources/informationprotectionlabel?view=graph-rest-beta) via Office 365 Security and Compliance Center's PowerShell module. The actions must be understood by the consuming application.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| name | String | Name of the custom action. |
| properties | [keyValuePair](https://learn.microsoft.com/en-us/graph/api/resources/keyvaluepair?view=graph-rest-beta) collection | Properties, in key value pair format, of the action. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "name": "String",
  "properties": [{"@odata.type": "microsoft.graph.keyValuePair"}]
}
```
