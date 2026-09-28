<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/informationprotectionlabel?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# informationProtectionLabel resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The Information Protection labels API is deprecated and will stop returning data on January 1, 2023. Please use the new [informationProtection](https://learn.microsoft.com/en-us/graph/api/resources/security-informationprotection?view=graph-rest-beta&preserve-view=true), [sensitivityLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-sensitivitylabel?view=graph-rest-beta&preserve-view=true), and associated resources.

Describes the information protection label that details how to properly apply a sensitivity label to information. The **informationProtectionLabel** resource describes the configuration of sensitivity labels that apply to a user or tenant.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List informationProtectionLabel](https://learn.microsoft.com/en-us/graph/api/informationprotectionpolicy-list-labels?view=graph-rest-beta) \(deprecated\) | [informationProtectionLabel](https://learn.microsoft.com/en-us/graph/api/resources/informationprotectionlabel?view=graph-rest-beta) collection | List all configured information protection labels for a user or tenant. |
| [Get informationProtectionLabel](https://learn.microsoft.com/en-us/graph/api/informationprotectionlabel-get?view=graph-rest-beta) \(deprecated\) | [informationProtectionLabel](https://learn.microsoft.com/en-us/graph/api/resources/informationprotectionlabel?view=graph-rest-beta) | Given a specific label ID, return the **informationProtectionLabel**. |
| [evaluateapplication](https://learn.microsoft.com/en-us/graph/api/informationprotectionlabel-evaluateapplication?view=graph-rest-beta) \(deprecated\) | [informationProtectionAction](https://learn.microsoft.com/en-us/graph/api/resources/informationprotectionaction?view=graph-rest-beta) collection | Given an input of [contentInfo](https://learn.microsoft.com/en-us/graph/api/resources/contentinfo?view=graph-rest-beta) and [labelingOptions](https://learn.microsoft.com/en-us/graph/api/resources/labelingoptions?view=graph-rest-beta), compute the set of actions require to apply the label. |
| [evaluateClassificationResults](https://learn.microsoft.com/en-us/graph/api/informationprotectionlabel-evaluateclassificationresults?view=graph-rest-beta) \(deprecated\) | [informationProtectionAction](https://learn.microsoft.com/en-us/graph/api/resources/informationprotectionaction?view=graph-rest-beta) collection | Given an input of [contentInfo](https://learn.microsoft.com/en-us/graph/api/resources/contentinfo?view=graph-rest-beta) and classification results, compute the set of actions require to apply the label. |
| [evaluateRemoval](https://learn.microsoft.com/en-us/graph/api/informationprotectionlabel-evaluateremoval?view=graph-rest-beta) \(deprecated\) | [informationProtectionAction](https://learn.microsoft.com/en-us/graph/api/resources/informationprotectionaction?view=graph-rest-beta) collection | Given an input of [contentInfo](https://learn.microsoft.com/en-us/graph/api/resources/contentinfo?view=graph-rest-beta) and [downgradeJustification](https://learn.microsoft.com/en-us/graph/api/resources/downgradejustification?view=graph-rest-beta), compute the actions that should be taken to remove the label. |
| [extractLabel](https://learn.microsoft.com/en-us/graph/api/informationprotectionlabel-extractlabel?view=graph-rest-beta) \(deprecated\) | [informationProtectionContentLabel](https://learn.microsoft.com/en-us/graph/api/resources/informationprotectioncontentlabel?view=graph-rest-beta) | Given an input of [contentInfo](https://learn.microsoft.com/en-us/graph/api/resources/contentinfo?view=graph-rest-beta), return details on the [informationProtectionLabel](https://learn.microsoft.com/en-us/graph/api/resources/informationprotectionlabel?view=graph-rest-beta) that the metadata represents. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| color | String | The color that the UI should display for the label, if configured. |
| description | String | The admin-defined description for the label. |
| id | String | The label ID is a globally unique identifier \(GUID\) |
| isActive | Boolean | Indicates whether the label is active or not. Active labels should be hidden or disabled in UI. |
| name | String | The plaintext name of the label. |
| sensitivity | Int32 | The sensitivity value of the label, where lower is less sensitive. |
| tooltip | String | The tooltip that should be displayed for the label in a UI. |
| parent | labelDetails | The parent label associated with a child label. Null if label has no parent. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "color": "String",
  "description": "String",
  "id": "String (identifier)",
  "isActive": true,
  "name": "String",
  "sensitivity": 1024,
  "tooltip": "String",
  "parent": {"@odata.type": "microsoft.graph.labelDetails" }
}
```
