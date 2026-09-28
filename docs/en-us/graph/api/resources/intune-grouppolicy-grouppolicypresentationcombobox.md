<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationcombobox?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# groupPolicyPresentationComboBox resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Represents an ADMX comboBox element and an ADMX text element.

Inherits from [groupPolicyUploadedPresentation](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyuploadedpresentation?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List groupPolicyPresentationComboBoxes](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicypresentationcombobox-list?view=graph-rest-beta) | [groupPolicyPresentationComboBox](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationcombobox?view=graph-rest-beta) collection | List properties and relationships of the [groupPolicyPresentationComboBox](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationcombobox?view=graph-rest-beta) objects. |
| [Get groupPolicyPresentationComboBox](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicypresentationcombobox-get?view=graph-rest-beta) | [groupPolicyPresentationComboBox](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationcombobox?view=graph-rest-beta) | Read properties and relationships of the [groupPolicyPresentationComboBox](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationcombobox?view=graph-rest-beta) object. |
| [Create groupPolicyPresentationComboBox](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicypresentationcombobox-create?view=graph-rest-beta) | [groupPolicyPresentationComboBox](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationcombobox?view=graph-rest-beta) | Create a new [groupPolicyPresentationComboBox](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationcombobox?view=graph-rest-beta) object. |
| [Delete groupPolicyPresentationComboBox](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicypresentationcombobox-delete?view=graph-rest-beta) | None | Deletes a [groupPolicyPresentationComboBox](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationcombobox?view=graph-rest-beta). |
| [Update groupPolicyPresentationComboBox](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicypresentationcombobox-update?view=graph-rest-beta) | [groupPolicyPresentationComboBox](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationcombobox?view=graph-rest-beta) | Update the properties of a [groupPolicyPresentationComboBox](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationcombobox?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| label | String | Localized text label for any presentation entity. The default value is empty. Inherited from [groupPolicyPresentation](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentation?view=graph-rest-beta) |
| id | String | Key of the entity. Inherited from [groupPolicyPresentation](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentation?view=graph-rest-beta) |
| lastModifiedDateTime | DateTimeOffset | The date and time the entity was last modified. Inherited from [groupPolicyPresentation](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentation?view=graph-rest-beta) |
| defaultValue | String | Localized default string displayed in the combo box. The default value is empty. |
| suggestions | String collection | Localized strings listed in the drop-down list of the combo box. The default value is empty. |
| required | Boolean | Specifies whether a value must be specified for the parameter. The default value is false. |
| maxLength | Int64 | An unsigned integer that specifies the maximum number of text characters for the parameter. The default value is 1023. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| definition | [groupPolicyDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinition?view=graph-rest-beta) | The group policy definition associated with the presentation. Inherited from [groupPolicyPresentation](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentation?view=graph-rest-beta) |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.groupPolicyPresentationComboBox",
  "label": "String",
  "id": "String (identifier)",
  "lastModifiedDateTime": "String (timestamp)",
  "defaultValue": "String",
  "suggestions": [
    "String"
  ],
  "required": true,
  "maxLength": 1024
}
```
