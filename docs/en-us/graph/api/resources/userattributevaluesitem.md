<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/userattributevaluesitem?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# userAttributeValuesItem resource type

Namespace: microsoft.graph

Represents user flow attribute values within a user flow when there are multiple selections to choose from. The userAttributeValuesItem is applicable to the userInputTypes of `radioSingleSelect`, `dropdownSingleSelect`, and `checkboxMultiSelect` for an [identityUserFlowAttributeAssignment](https://learn.microsoft.com/en-us/graph/api/resources/identityuserflowattributeassignment?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isDefault | Boolean | Determines whether the value is set as the default. |
| name | String | The display name of the property displayed to the user in the user flow. |
| value | String | The value that is set when this item is selected. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.userAttributeValuesItem",
  "name": "String",
  "value": "String",
  "isDefault": "Boolean"
}
```
