<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationdropdownlist?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# groupPolicyPresentationDropdownList resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Represents an ADMX dropdownList element and an ADMX enum element.

Inherits from [groupPolicyUploadedPresentation](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyuploadedpresentation?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List groupPolicyPresentationDropdownLists](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicypresentationdropdownlist-list?view=graph-rest-beta) | [groupPolicyPresentationDropdownList](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationdropdownlist?view=graph-rest-beta) collection | List properties and relationships of the [groupPolicyPresentationDropdownList](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationdropdownlist?view=graph-rest-beta) objects. |
| [Get groupPolicyPresentationDropdownList](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicypresentationdropdownlist-get?view=graph-rest-beta) | [groupPolicyPresentationDropdownList](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationdropdownlist?view=graph-rest-beta) | Read properties and relationships of the [groupPolicyPresentationDropdownList](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationdropdownlist?view=graph-rest-beta) object. |
| [Create groupPolicyPresentationDropdownList](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicypresentationdropdownlist-create?view=graph-rest-beta) | [groupPolicyPresentationDropdownList](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationdropdownlist?view=graph-rest-beta) | Create a new [groupPolicyPresentationDropdownList](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationdropdownlist?view=graph-rest-beta) object. |
| [Delete groupPolicyPresentationDropdownList](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicypresentationdropdownlist-delete?view=graph-rest-beta) | None | Deletes a [groupPolicyPresentationDropdownList](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationdropdownlist?view=graph-rest-beta). |
| [Update groupPolicyPresentationDropdownList](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicypresentationdropdownlist-update?view=graph-rest-beta) | [groupPolicyPresentationDropdownList](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationdropdownlist?view=graph-rest-beta) | Update the properties of a [groupPolicyPresentationDropdownList](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationdropdownlist?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| label | String | Localized text label for any presentation entity. The default value is empty. Inherited from [groupPolicyPresentation](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentation?view=graph-rest-beta) |
| id | String | Key of the entity. Inherited from [groupPolicyPresentation](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentation?view=graph-rest-beta) |
| lastModifiedDateTime | DateTimeOffset | The date and time the entity was last modified. Inherited from [groupPolicyPresentation](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentation?view=graph-rest-beta) |
| defaultItem | [groupPolicyPresentationDropdownListItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationdropdownlistitem?view=graph-rest-beta) | Localized string value identifying the default choice of the list of items. |
| items | [groupPolicyPresentationDropdownListItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationdropdownlistitem?view=graph-rest-beta) collection | Represents a set of localized display names and their associated values. |
| required | Boolean | Requirement to enter a value in the parameter box. The default value is false. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| definition | [groupPolicyDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinition?view=graph-rest-beta) | The group policy definition associated with the presentation. Inherited from [groupPolicyPresentation](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentation?view=graph-rest-beta) |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.groupPolicyPresentationDropdownList",
  "label": "String",
  "id": "String (identifier)",
  "lastModifiedDateTime": "String (timestamp)",
  "defaultItem": {
    "@odata.type": "microsoft.graph.groupPolicyPresentationDropdownListItem",
    "displayName": "String",
    "value": "String"
  },
  "items": [
    {
      "@odata.type": "microsoft.graph.groupPolicyPresentationDropdownListItem",
      "displayName": "String",
      "value": "String"
    }
  ],
  "required": true
}
```
