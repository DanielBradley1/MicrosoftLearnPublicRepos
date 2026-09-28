<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/recommendlabelaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# recommendLabelAction resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The Information Protection labels API is deprecated and will stop returning data on January 1, 2023. Please use the new [informationProtection](https://learn.microsoft.com/en-us/graph/api/resources/security-informationprotection?view=graph-rest-beta&preserve-view=true), [sensitivityLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-sensitivitylabel?view=graph-rest-beta&preserve-view=true), and associated resources.

Represents a label that should be recommended to the user for application to the file based on discovered sensitive information types. The [evaluateClassificationResults](https://learn.microsoft.com/en-us/graph/api/informationprotectionlabel-evaluateclassificationresults?view=graph-rest-beta) may return a **recommendLabelAction** if the Microsoft Purview Information Protection labeling policy is set to **recommend** and label rather than enforce a label. The user or appliation may choose to ignore or accept the recommendation.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actionSource | String | The possible values are: `manual`, `automatic`, `recommended`, `default`. |
| actions | [informationProtectionAction](https://learn.microsoft.com/en-us/graph/api/resources/informationprotectionaction?view=graph-rest-beta) collection | Actions to take if the label is accepted by the user. |
| label | [labelDetails](https://learn.microsoft.com/en-us/graph/api/resources/labeldetails?view=graph-rest-beta) | The label that is being recommended. |
| responsibleSensitiveTypeIds | Guid collection | The sensitive information type GUIDs that caused the recommendation to be given. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "actionSource": "String",
  "actions": [{"@odata.type": "microsoft.graph.informationProtectionAction"}],
  "label": {"@odata.type": "microsoft.graph.labelDetails"},
  "responsibleSensitiveTypeIds": ["Guid"]
}
```
