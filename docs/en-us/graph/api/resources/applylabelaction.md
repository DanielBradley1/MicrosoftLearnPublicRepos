<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/applylabelaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# applyLabelAction resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The Information Protection labels API is deprecated and will stop returning data on January 1, 2023. Please use the new [informationProtection](https://learn.microsoft.com/en-us/graph/api/resources/security-informationprotection?view=graph-rest-beta&preserve-view=true), [sensitivityLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-sensitivitylabel?view=graph-rest-beta&preserve-view=true), and associated resources.

Represents a set of actions that should be taken to apply or update a label. **applyLabelAction** is returned when the result of a label evaluation operation is that a label should be applied. The `actions` property contains an [informationProtectionAction](https://learn.microsoft.com/en-us/graph/api/resources/informationprotectionaction?view=graph-rest-beta) collection that described the full set of actions to *apply* the label, including removal of old metadata, content marking, and protection.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actionSource | String | The possible values are: `manual`, `automatic`, `recommended`, `default`. |
| actions | [informationProtectionAction](https://learn.microsoft.com/en-us/graph/api/resources/informationprotectionaction?view=graph-rest-beta) collection | The collection of specific actions that should be taken by the consuming application to label the document. See [informationProtectionAction](https://learn.microsoft.com/en-us/graph/api/resources/informationprotectionaction?view=graph-rest-beta) for the full list. |
| label | [labelDetails](https://learn.microsoft.com/en-us/graph/api/resources/labeldetails?view=graph-rest-beta) | Object that describes the details of the label to apply. |
| responsibleSensitiveTypeIds | Guid collection | If the label was the result of an automatic classification, supply the list of sensitive info type GUIDs that resulted in the returned label. |

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
