<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-downgradejustification?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# downgradeJustification resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the user input on why downgrade was performed. The downgrade justification might be required based on the label policy configuration in Office Security and Compliance Center.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isDowngradeJustified | Boolean | Indicates whether the downgrade is or isn't justified. |
| justificationMessage | String | Message that indicates why a downgrade is justified. The message appears in administrative logs. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.downgradeJustification",
  "isDowngradeJustified": "Boolean",
  "justificationMessage": "String"
}
```
