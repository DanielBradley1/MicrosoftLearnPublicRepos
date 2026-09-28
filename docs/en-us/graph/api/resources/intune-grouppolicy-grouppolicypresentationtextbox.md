<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationtextbox?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# groupPolicyPresentationTextBox resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Represents an ADMX textBox element and an ADMX text element.

Inherits from [groupPolicyUploadedPresentation](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyuploadedpresentation?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List groupPolicyPresentationTextBoxes](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicypresentationtextbox-list?view=graph-rest-beta) | [groupPolicyPresentationTextBox](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationtextbox?view=graph-rest-beta) collection | List properties and relationships of the [groupPolicyPresentationTextBox](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationtextbox?view=graph-rest-beta) objects. |
| [Get groupPolicyPresentationTextBox](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicypresentationtextbox-get?view=graph-rest-beta) | [groupPolicyPresentationTextBox](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationtextbox?view=graph-rest-beta) | Read properties and relationships of the [groupPolicyPresentationTextBox](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationtextbox?view=graph-rest-beta) object. |
| [Create groupPolicyPresentationTextBox](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicypresentationtextbox-create?view=graph-rest-beta) | [groupPolicyPresentationTextBox](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationtextbox?view=graph-rest-beta) | Create a new [groupPolicyPresentationTextBox](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationtextbox?view=graph-rest-beta) object. |
| [Delete groupPolicyPresentationTextBox](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicypresentationtextbox-delete?view=graph-rest-beta) | None | Deletes a [groupPolicyPresentationTextBox](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationtextbox?view=graph-rest-beta). |
| [Update groupPolicyPresentationTextBox](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicypresentationtextbox-update?view=graph-rest-beta) | [groupPolicyPresentationTextBox](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationtextbox?view=graph-rest-beta) | Update the properties of a [groupPolicyPresentationTextBox](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationtextbox?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| label | String | Localized text label for any presentation entity. The default value is empty. Inherited from [groupPolicyPresentation](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentation?view=graph-rest-beta) |
| id | String | Key of the entity. Inherited from [groupPolicyPresentation](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentation?view=graph-rest-beta) |
| lastModifiedDateTime | DateTimeOffset | The date and time the entity was last modified. Inherited from [groupPolicyPresentation](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentation?view=graph-rest-beta) |
| defaultValue | String | Localized default string displayed in the text box. The default value is empty. |
| required | Boolean | Requirement to enter a value in the text box. Default value is false. |
| maxLength | Int64 | An unsigned integer that specifies the maximum number of text characters. Default value is 1023. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| definition | [groupPolicyDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinition?view=graph-rest-beta) | The group policy definition associated with the presentation. Inherited from [groupPolicyPresentation](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentation?view=graph-rest-beta) |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.groupPolicyPresentationTextBox",
  "label": "String",
  "id": "String (identifier)",
  "lastModifiedDateTime": "String (timestamp)",
  "defaultValue": "String",
  "required": true,
  "maxLength": 1024
}
```
