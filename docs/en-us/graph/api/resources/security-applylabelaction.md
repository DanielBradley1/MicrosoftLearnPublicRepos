<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-applylabelaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# applyLabelAction resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a set of actions that should be taken to apply or update a label. **applyLabelAction** is returned when the result of a label evaluation operation is that a label should be applied. The **actions** property contains an [informationProtectionAction](https://learn.microsoft.com/en-us/graph/api/resources/security-informationprotectionaction?view=graph-rest-beta) collection that describes the full set of actions to apply the label, including removal of old metadata, content marking, and protection.

Inherits from [informationProtectionAction](https://learn.microsoft.com/en-us/graph/api/resources/security-informationprotectionaction?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actions | [informationProtectionAction](https://learn.microsoft.com/en-us/graph/api/resources/security-informationprotectionaction?view=graph-rest-beta) collection | The collection of actions that should be implemented by the caller. |
| actionSource | [actionSource](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#actionsource-values) | Specifies why the label was selected. The possible values are: `manual`, `automatic`, `recommended`, `default`. |
| responsibleSensitiveTypeIds | GUID collection | If the label was the result of an automatic classification, supply the list of sensitive info type GUIDs that resulted in the returned label. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| sensitivityLabel | [microsoft.graph.security.sensitivityLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-sensitivitylabel?view=graph-rest-beta) | The label that corresponds to the set of actions returned by the API. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.applyLabelAction",
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
