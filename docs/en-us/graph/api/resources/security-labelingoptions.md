<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-labelingoptions?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# labelingOptions resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the labeling options that can be provided to the evaluation APIs. **labelingOptions** must be passed in to the [evaluateApplication](https://learn.microsoft.com/en-us/graph/api/security-sensitivitylabel-evaluateapplication?view=graph-rest-beta) API to specify details about the label that is to be applied.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| assignmentMethod | String | Describes whether the label was applied by an automated \(`standard`\) process or a person \(`privileged`\). |
| downgradeJustification | [downgradeJustification](https://learn.microsoft.com/en-us/graph/api/resources/security-downgradejustification?view=graph-rest-beta) | The downgrade justification object that indicates if downgrade was justified and, if so, the reason. |
| extendedProperties | [keyValuePair](https://learn.microsoft.com/en-us/graph/api/resources/keyvaluepair?view=graph-rest-beta) collection | Extended properties will be parsed and returned in the standard Microsoft Purview Information Protection labeled metadata format as part of the label information. |
| labelId | GUID | The GUID of the label that should be applied to the information. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.labelingOptions",
  "assignmentMethod": "String",
  "downgradeJustification": {
    "@odata.type": "microsoft.graph.security.downgradeJustification"
  },
  "extendedProperties": [
    {
      "@odata.type": "microsoft.graph.security.keyValuePair"
    }
  ],
  "labelId": "GUID"
}
```
