<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identityuserflowattributeassignment?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-06-19 -->

# identityUserFlowAttributeAssignment resource type

Namespace: microsoft.graph

Represents how attributes are collected in an identity user flow. and allows customization options for collecting attributes within the user flow. You can have multiple identityUserFlowAttributeAssignments within a single user flow that creates the experience for providing the information required by the user to complete sign-up.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/identityuserflowattributeassignment-get?view=graph-rest-1.0) | [identityUserFlowAttributeAssignment](https://learn.microsoft.com/en-us/graph/api/resources/identityuserflowattributeassignment?view=graph-rest-1.0) | Read the properties and relationships of an identityUserFlowAttributeAssignment object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/identityuserflowattributeassignment-update?view=graph-rest-1.0) | None | Update the properties of an identityUserFlowAttributeAssignment object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/identityuserflowattributeassignment-delete?view=graph-rest-1.0) | None | Delete a specific identityUserFlowAttributeAssignment object. |
| [Get order](https://learn.microsoft.com/en-us/graph/api/identityuserflowattributeassignment-getorder?view=graph-rest-1.0) | [assignmentOrder](https://learn.microsoft.com/en-us/graph/api/resources/assignmentorder?view=graph-rest-1.0) | Gets the order of the identityUserFlowAttributes being collected within a user flow. |
| [Set order](https://learn.microsoft.com/en-us/graph/api/identityuserflowattributeassignment-setorder?view=graph-rest-1.0) | None | Sets the order of the identityUserFlowAttributes being collected within a user flow. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name of the identityUserFlowAttribute within a user flow. |
| id | String | The identifier of the identityUserFlowAttributeAssignment. This identifier is immutable after it's created and is a read-only property. |
| isOptional | Boolean | Determines whether the identityUserFlowAttribute is optional. `true` means the user doesn't have to provide a value. `false` means the user can't complete sign-up without providing a value. |
| requiresVerification | Boolean | Determines whether the identityUserFlowAttribute requires verification, and is only used for verifying the user's phone number or email address. |
| userAttributeValues | [userAttributeValuesItem](https://learn.microsoft.com/en-us/graph/api/resources/userattributevaluesitem?view=graph-rest-1.0) collection | The input options for the user flow attribute. Only applicable when the userInputType is `radioSingleSelect`, `dropdownSingleSelect`, or `checkboxMultiSelect`. |
| userInputType | identityUserFlowAttributeInputType | The input type of the user flow attribute. The possible values are: `textBox`, `dateTimeDropdown`, `radioSingleSelect`, `dropdownSingleSelect`, `emailBox`, `checkboxMultiSelect`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| userAttribute | [identityUserFlowAttribute](https://learn.microsoft.com/en-us/graph/api/resources/identityuserflowattribute?view=graph-rest-1.0) | The user attribute that you want to add to your user flow. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityUserFlowAttributeAssignment",
  "id": "String (identifier)",
  "isOptional": "Boolean",
  "requiresVerification": "Boolean",
  "userInputType": "String",
  "userAttributeValues": [
    {
      "@odata.type": "microsoft.graph.userAttributeValuesItem"
    }
  ],
  "displayName": "String"
}
```
