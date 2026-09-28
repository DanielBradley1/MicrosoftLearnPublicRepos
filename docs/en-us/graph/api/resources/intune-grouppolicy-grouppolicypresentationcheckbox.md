<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationcheckbox?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# groupPolicyPresentationCheckBox resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Represents an ADMX checkBox element and an ADMX boolean element.

Inherits from [groupPolicyUploadedPresentation](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyuploadedpresentation?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List groupPolicyPresentationCheckBoxes](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicypresentationcheckbox-list?view=graph-rest-beta) | [groupPolicyPresentationCheckBox](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationcheckbox?view=graph-rest-beta) collection | List properties and relationships of the [groupPolicyPresentationCheckBox](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationcheckbox?view=graph-rest-beta) objects. |
| [Get groupPolicyPresentationCheckBox](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicypresentationcheckbox-get?view=graph-rest-beta) | [groupPolicyPresentationCheckBox](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationcheckbox?view=graph-rest-beta) | Read properties and relationships of the [groupPolicyPresentationCheckBox](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationcheckbox?view=graph-rest-beta) object. |
| [Create groupPolicyPresentationCheckBox](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicypresentationcheckbox-create?view=graph-rest-beta) | [groupPolicyPresentationCheckBox](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationcheckbox?view=graph-rest-beta) | Create a new [groupPolicyPresentationCheckBox](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationcheckbox?view=graph-rest-beta) object. |
| [Delete groupPolicyPresentationCheckBox](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicypresentationcheckbox-delete?view=graph-rest-beta) | None | Deletes a [groupPolicyPresentationCheckBox](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationcheckbox?view=graph-rest-beta). |
| [Update groupPolicyPresentationCheckBox](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicypresentationcheckbox-update?view=graph-rest-beta) | [groupPolicyPresentationCheckBox](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationcheckbox?view=graph-rest-beta) | Update the properties of a [groupPolicyPresentationCheckBox](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationcheckbox?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| label | String | Localized text label for any presentation entity. The default value is empty. Inherited from [groupPolicyPresentation](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentation?view=graph-rest-beta) |
| id | String | Key of the entity. Inherited from [groupPolicyPresentation](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentation?view=graph-rest-beta) |
| lastModifiedDateTime | DateTimeOffset | The date and time the entity was last modified. Inherited from [groupPolicyPresentation](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentation?view=graph-rest-beta) |
| defaultChecked | Boolean | Default value for the check box. The default value is false. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| definition | [groupPolicyDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinition?view=graph-rest-beta) | The group policy definition associated with the presentation. Inherited from [groupPolicyPresentation](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentation?view=graph-rest-beta) |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.groupPolicyPresentationCheckBox",
  "label": "String",
  "id": "String (identifier)",
  "lastModifiedDateTime": "String (timestamp)",
  "defaultChecked": true
}
```
