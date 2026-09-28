<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-recommendlabelaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# recommendLabelAction resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a label that should be recommended to the user for application to the file based on discovered sensitive information types. The [evaluateClassificationResults](https://learn.microsoft.com/en-us/graph/api/security-sensitivitylabel-evaluateclassificationresults?view=graph-rest-beta) might return a **recommendLabelAction** if the Microsoft Purview Information Protection labeling policy is set to `recommend` a label rather than `enforce` a label. The user or application might choose to ignore or accept the recommendation.

Inherits from [informationProtectionAction](https://learn.microsoft.com/en-us/graph/api/resources/security-informationprotectionaction?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actions | [informationProtectionAction](https://learn.microsoft.com/en-us/graph/api/resources/security-informationprotectionaction?view=graph-rest-beta) collection | Actions to take if the label is accepted by the user. |
| actionSource | String | Specifies why the label was selected. The possible values are: `manual`, `automatic`, `recommended`, `default`. |
| responsibleSensitiveTypeIds | GUID collection | The sensitive information type GUIDs that caused the recommendation to be given. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| sensitivityLabel | [microsoft.graph.security.sensitivityLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-sensitivitylabel?view=graph-rest-beta) | The label that is being recommended. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.recommendLabelAction",
  "actions": [
    {
      "@odata.type": "microsoft.graph.security.addContentFooterAction"
    }
  ],
  "actionSource": "String",
  "responsibleSensitiveTypeIds": [
    "GUID"
  ]
}
```
