<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/downgradejustification?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# downgradeJustification resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The Information Protection labels API is deprecated and will stop returning data on January 1, 2023. Please use the new [informationProtection](https://learn.microsoft.com/en-us/graph/api/resources/security-informationprotection?view=graph-rest-beta&preserve-view=true), [sensitivityLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-sensitivitylabel?view=graph-rest-beta&preserve-view=true), and associated resources.

Represents user input on why downgrade was performed. Downgrade justification might be required based on label policy configuration in Office Security and Compliance Center.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isDowngradeJustified | Boolean | Indicates whether the downgrade is or isn't justified. |
| justificationMessage | String | Message that indicates why a downgrade is justified. The message appears in administrative logs. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "isDowngradeJustified": true,
  "justificationMessage": "String"
}
```
