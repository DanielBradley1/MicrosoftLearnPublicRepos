<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationtext?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# groupPolicyPresentationText resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Represents an ADMX text element.

Inherits from [groupPolicyUploadedPresentation](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyuploadedpresentation?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List groupPolicyPresentationTexts](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicypresentationtext-list?view=graph-rest-beta) | [groupPolicyPresentationText](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationtext?view=graph-rest-beta) collection | List properties and relationships of the [groupPolicyPresentationText](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationtext?view=graph-rest-beta) objects. |
| [Get groupPolicyPresentationText](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicypresentationtext-get?view=graph-rest-beta) | [groupPolicyPresentationText](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationtext?view=graph-rest-beta) | Read properties and relationships of the [groupPolicyPresentationText](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationtext?view=graph-rest-beta) object. |
| [Create groupPolicyPresentationText](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicypresentationtext-create?view=graph-rest-beta) | [groupPolicyPresentationText](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationtext?view=graph-rest-beta) | Create a new [groupPolicyPresentationText](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationtext?view=graph-rest-beta) object. |
| [Delete groupPolicyPresentationText](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicypresentationtext-delete?view=graph-rest-beta) | None | Deletes a [groupPolicyPresentationText](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationtext?view=graph-rest-beta). |
| [Update groupPolicyPresentationText](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicypresentationtext-update?view=graph-rest-beta) | [groupPolicyPresentationText](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationtext?view=graph-rest-beta) | Update the properties of a [groupPolicyPresentationText](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationtext?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| label | String | Localized text label for any presentation entity. The default value is empty. Inherited from [groupPolicyPresentation](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentation?view=graph-rest-beta) |
| id | String | Key of the entity. Inherited from [groupPolicyPresentation](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentation?view=graph-rest-beta) |
| lastModifiedDateTime | DateTimeOffset | The date and time the entity was last modified. Inherited from [groupPolicyPresentation](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentation?view=graph-rest-beta) |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| definition | [groupPolicyDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinition?view=graph-rest-beta) | The group policy definition associated with the presentation. Inherited from [groupPolicyPresentation](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentation?view=graph-rest-beta) |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.groupPolicyPresentationText",
  "label": "String",
  "id": "String (identifier)",
  "lastModifiedDateTime": "String (timestamp)"
}
```
