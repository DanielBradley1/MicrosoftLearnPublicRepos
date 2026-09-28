<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinition?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# groupPolicyDefinition resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The entity describes all of the information about a single group policy.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get groupPolicyDefinition](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicydefinition-get?view=graph-rest-beta) | [groupPolicyDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinition?view=graph-rest-beta) | Read properties and relationships of the [groupPolicyDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinition?view=graph-rest-beta) object. |
| [Update groupPolicyDefinition](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicydefinition-update?view=graph-rest-beta) | [groupPolicyDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinition?view=graph-rest-beta) | Update the properties of a [groupPolicyDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinition?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| classType | [groupPolicyDefinitionClassType](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinitionclasstype?view=graph-rest-beta) | Identifies the type of groups the policy can be applied to. Possible values are: `user`, `machine`. |
| displayName | String | The localized policy name. |
| explainText | String | The localized explanation or help text associated with the policy. The default value is empty. |
| categoryPath | String | The localized full category path for the policy. |
| supportedOn | String | Localized string used to specify what operating system or application version is affected by the policy. |
| policyType | [groupPolicyType](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicytype?view=graph-rest-beta) | Specifies the type of group policy. Possible values are: `admxBacked`, `admxIngested`. |
| hasRelatedDefinitions | Boolean | Signifies whether or not there are related definitions to this definition |
| groupPolicyCategoryId | Guid | The category id of the parent category |
| minDeviceCspVersion | String | Minimum required CSP version for device configuration in this definition |
| minUserCspVersion | String | Minimum required CSP version for user configuration in this definition |
| version | String | Setting definition version |
| id | String | Key of the entity. |
| lastModifiedDateTime | DateTimeOffset | The date and time the entity was last modified. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| definitionFile | [groupPolicyDefinitionFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinitionfile?view=graph-rest-beta) | The group policy file associated with the definition. |
| category | [groupPolicyCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicycategory?view=graph-rest-beta) | The group policy category associated with the definition. |
| presentations | [groupPolicyPresentation](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentation?view=graph-rest-beta) collection | The group policy presentations associated with the definition. |
| previousVersionDefinition | [groupPolicyDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinition?view=graph-rest-beta) | Definition of the previous version of this definition |
| nextVersionDefinition | [groupPolicyDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinition?view=graph-rest-beta) | Definition of the next version of this definition |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.groupPolicyDefinition",
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
