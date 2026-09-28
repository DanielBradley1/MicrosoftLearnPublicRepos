<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyuploadeddefinition?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# groupPolicyUploadedDefinition resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The entity describes all of the information about a single group policy.

Inherits from [groupPolicyDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinition?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List groupPolicyUploadedDefinitions](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicyuploadeddefinition-list?view=graph-rest-beta) | [groupPolicyUploadedDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyuploadeddefinition?view=graph-rest-beta) collection | List properties and relationships of the [groupPolicyUploadedDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyuploadeddefinition?view=graph-rest-beta) objects. |
| [Get groupPolicyUploadedDefinition](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicyuploadeddefinition-get?view=graph-rest-beta) | [groupPolicyUploadedDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyuploadeddefinition?view=graph-rest-beta) | Read properties and relationships of the [groupPolicyUploadedDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyuploadeddefinition?view=graph-rest-beta) object. |
| [Create groupPolicyUploadedDefinition](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicyuploadeddefinition-create?view=graph-rest-beta) | [groupPolicyUploadedDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyuploadeddefinition?view=graph-rest-beta) | Create a new [groupPolicyUploadedDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyuploadeddefinition?view=graph-rest-beta) object. |
| [Delete groupPolicyUploadedDefinition](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicyuploadeddefinition-delete?view=graph-rest-beta) | None | Deletes a [groupPolicyUploadedDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyuploadeddefinition?view=graph-rest-beta). |
| [Update groupPolicyUploadedDefinition](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicyuploadeddefinition-update?view=graph-rest-beta) | [groupPolicyUploadedDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyuploadeddefinition?view=graph-rest-beta) | Update the properties of a [groupPolicyUploadedDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyuploadeddefinition?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| classType | [groupPolicyDefinitionClassType](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinitionclasstype?view=graph-rest-beta) | Identifies the type of groups the policy can be applied to. Inherited from [groupPolicyDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinition?view=graph-rest-beta). Possible values are: `user`, `machine`. |
| displayName | String | The localized policy name. Inherited from [groupPolicyDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinition?view=graph-rest-beta) |
| explainText | String | The localized explanation or help text associated with the policy. The default value is empty. Inherited from [groupPolicyDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinition?view=graph-rest-beta) |
| categoryPath | String | The localized full category path for the policy. Inherited from [groupPolicyDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinition?view=graph-rest-beta) |
| supportedOn | String | Localized string used to specify what operating system or application version is affected by the policy. Inherited from [groupPolicyDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinition?view=graph-rest-beta) |
| policyType | [groupPolicyType](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicytype?view=graph-rest-beta) | Specifies the type of group policy. Inherited from [groupPolicyDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinition?view=graph-rest-beta). Possible values are: `admxBacked`, `admxIngested`. |
| hasRelatedDefinitions | Boolean | Signifies whether or not there are related definitions to this definition Inherited from [groupPolicyDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinition?view=graph-rest-beta) |
| groupPolicyCategoryId | Guid | The category id of the parent category Inherited from [groupPolicyDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinition?view=graph-rest-beta) |
| minDeviceCspVersion | String | Minimum required CSP version for device configuration in this definition Inherited from [groupPolicyDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinition?view=graph-rest-beta) |
| minUserCspVersion | String | Minimum required CSP version for user configuration in this definition Inherited from [groupPolicyDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinition?view=graph-rest-beta) |
| version | String | Setting definition version Inherited from [groupPolicyDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinition?view=graph-rest-beta) |
| id | String | Key of the entity. Inherited from [groupPolicyDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinition?view=graph-rest-beta) |
| lastModifiedDateTime | DateTimeOffset | The date and time the entity was last modified. Inherited from [groupPolicyDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinition?view=graph-rest-beta) |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| definitionFile | [groupPolicyDefinitionFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinitionfile?view=graph-rest-beta) | The group policy file associated with the definition. Inherited from [groupPolicyDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinition?view=graph-rest-beta) |
| category | [groupPolicyCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicycategory?view=graph-rest-beta) | The group policy category associated with the definition. Inherited from [groupPolicyDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinition?view=graph-rest-beta) |
| presentations | [groupPolicyPresentation](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentation?view=graph-rest-beta) collection | The group policy presentations associated with the definition. Inherited from [groupPolicyDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinition?view=graph-rest-beta) |
| previousVersionDefinition | [groupPolicyDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinition?view=graph-rest-beta) | Definition of the previous version of this definition Inherited from [groupPolicyDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinition?view=graph-rest-beta) |
| nextVersionDefinition | [groupPolicyDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinition?view=graph-rest-beta) | Definition of the next version of this definition Inherited from [groupPolicyDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinition?view=graph-rest-beta) |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.groupPolicyUploadedDefinition",
  "classType": "String",
  "displayName": "String",
  "explainText": "String",
  "categoryPath": "String",
  "supportedOn": "String",
  "policyType": "String",
  "hasRelatedDefinitions": true,
  "groupPolicyCategoryId": "Guid",
  "minDeviceCspVersion": "String",
  "minUserCspVersion": "String",
  "version": "String",
  "id": "String (identifier)",
  "lastModifiedDateTime": "String (timestamp)"
}
```
