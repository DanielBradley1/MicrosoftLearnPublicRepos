<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/labelingoptions?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# labelingOptions resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The Information Protection labels API is deprecated and will stop returning data on January 1, 2023. Please use the new [informationProtection](https://learn.microsoft.com/en-us/graph/api/resources/security-informationprotection?view=graph-rest-beta&preserve-view=true), [sensitivityLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-sensitivitylabel?view=graph-rest-beta&preserve-view=true), and associated resources.

Represents the labeling options that can be provided to the evaluation APIs. **labelingOptions** must be passed in to the [evaluateApplication](https://learn.microsoft.com/en-us/graph/api/informationprotectionlabel-evaluateapplication?view=graph-rest-beta) API to specify details about the label that is to be applied.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| assignmentMethod | String | The possible values are: `standard`, `privileged`, `auto`. |
| downgradeJustification | [downgradeJustification](https://learn.microsoft.com/en-us/graph/api/resources/downgradejustification?view=graph-rest-beta) | The downgrade justification object that indicates if downgrade was justified and, if so, the reason. |
| extendedProperties | [keyValuePair](https://learn.microsoft.com/en-us/graph/api/resources/keyvaluepair?view=graph-rest-beta) collection | Extended properties will be parsed and returned in the standard MIP labeled metadata format as part of the label information. |
| labelId | Guid | The GUID of the label that should be applied to the information. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "assignmentMethod": "String",
  "downgradeJustification": {"@odata.type": "microsoft.graph.downgradeJustification"},
  "extendedProperties": [{"@odata.type": "microsoft.graph.keyValuePair"}],
  "labelId": "Guid"
}
```
