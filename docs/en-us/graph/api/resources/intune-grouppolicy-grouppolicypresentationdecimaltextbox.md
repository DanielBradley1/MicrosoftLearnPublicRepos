<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationdecimaltextbox?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# groupPolicyPresentationDecimalTextBox resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Represents an ADMX decimalTextBox element and an ADMX decimal element.

Inherits from [groupPolicyUploadedPresentation](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyuploadedpresentation?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List groupPolicyPresentationDecimalTextBoxes](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicypresentationdecimaltextbox-list?view=graph-rest-beta) | [groupPolicyPresentationDecimalTextBox](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationdecimaltextbox?view=graph-rest-beta) collection | List properties and relationships of the [groupPolicyPresentationDecimalTextBox](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationdecimaltextbox?view=graph-rest-beta) objects. |
| [Get groupPolicyPresentationDecimalTextBox](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicypresentationdecimaltextbox-get?view=graph-rest-beta) | [groupPolicyPresentationDecimalTextBox](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationdecimaltextbox?view=graph-rest-beta) | Read properties and relationships of the [groupPolicyPresentationDecimalTextBox](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationdecimaltextbox?view=graph-rest-beta) object. |
| [Create groupPolicyPresentationDecimalTextBox](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicypresentationdecimaltextbox-create?view=graph-rest-beta) | [groupPolicyPresentationDecimalTextBox](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationdecimaltextbox?view=graph-rest-beta) | Create a new [groupPolicyPresentationDecimalTextBox](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationdecimaltextbox?view=graph-rest-beta) object. |
| [Delete groupPolicyPresentationDecimalTextBox](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicypresentationdecimaltextbox-delete?view=graph-rest-beta) | None | Deletes a [groupPolicyPresentationDecimalTextBox](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationdecimaltextbox?view=graph-rest-beta). |
| [Update groupPolicyPresentationDecimalTextBox](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicypresentationdecimaltextbox-update?view=graph-rest-beta) | [groupPolicyPresentationDecimalTextBox](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationdecimaltextbox?view=graph-rest-beta) | Update the properties of a [groupPolicyPresentationDecimalTextBox](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationdecimaltextbox?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| label | String | Localized text label for any presentation entity. The default value is empty. Inherited from [groupPolicyPresentation](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentation?view=graph-rest-beta) |
| id | String | Key of the entity. Inherited from [groupPolicyPresentation](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentation?view=graph-rest-beta) |
| lastModifiedDateTime | DateTimeOffset | The date and time the entity was last modified. Inherited from [groupPolicyPresentation](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentation?view=graph-rest-beta) |
| defaultValue | Int64 | An unsigned integer that specifies the initial value for the decimal text box. The default value is 1. |
| spin | Boolean | If true, create a spin control; otherwise, create a text box for numeric entry. The default value is true. |
| spinStep | Int64 | An unsigned integer that specifies the increment of change for the spin control. The default value is 1. |
| required | Boolean | Requirement to enter a value in the parameter box. The default value is false. |
| minValue | Int64 | An unsigned integer that specifies the minimum allowed value. The default value is 0. |
| maxValue | Int64 | An unsigned integer that specifies the maximum allowed value. The default value is 9999. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| definition | [groupPolicyDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinition?view=graph-rest-beta) | The group policy definition associated with the presentation. Inherited from [groupPolicyPresentation](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentation?view=graph-rest-beta) |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.groupPolicyPresentationDecimalTextBox",
  "label": "String",
  "id": "String (identifier)",
  "lastModifiedDateTime": "String (timestamp)",
  "defaultValue": 1024,
  "spin": true,
  "spinStep": 1024,
  "required": true,
  "minValue": 1024,
  "maxValue": 1024
}
```
