<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyuploadeddefinitionfile?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# groupPolicyUploadedDefinitionFile resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The entity represents an ADMX \(Administrative Template\) XML file uploaded by Administrator. The ADMX file contains a collection of group policy definitions and their locations by category path. The group policy definition file also contains the languages supported as determined by the language dependent ADML \(Administrative Template\) language files.

Inherits from [groupPolicyDefinitionFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinitionfile?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List groupPolicyUploadedDefinitionFiles](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicyuploadeddefinitionfile-list?view=graph-rest-beta) | [groupPolicyUploadedDefinitionFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyuploadeddefinitionfile?view=graph-rest-beta) collection | List properties and relationships of the [groupPolicyUploadedDefinitionFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyuploadeddefinitionfile?view=graph-rest-beta) objects. |
| [Get groupPolicyUploadedDefinitionFile](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicyuploadeddefinitionfile-get?view=graph-rest-beta) | [groupPolicyUploadedDefinitionFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyuploadeddefinitionfile?view=graph-rest-beta) | Read properties and relationships of the [groupPolicyUploadedDefinitionFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyuploadeddefinitionfile?view=graph-rest-beta) object. |
| [Create groupPolicyUploadedDefinitionFile](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicyuploadeddefinitionfile-create?view=graph-rest-beta) | [groupPolicyUploadedDefinitionFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyuploadeddefinitionfile?view=graph-rest-beta) | Create a new [groupPolicyUploadedDefinitionFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyuploadeddefinitionfile?view=graph-rest-beta) object. |
| [Delete groupPolicyUploadedDefinitionFile](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicyuploadeddefinitionfile-delete?view=graph-rest-beta) | None | Deletes a [groupPolicyUploadedDefinitionFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyuploadeddefinitionfile?view=graph-rest-beta). |
| [Update groupPolicyUploadedDefinitionFile](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicyuploadeddefinitionfile-update?view=graph-rest-beta) | [groupPolicyUploadedDefinitionFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyuploadeddefinitionfile?view=graph-rest-beta) | Update the properties of a [groupPolicyUploadedDefinitionFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyuploadeddefinitionfile?view=graph-rest-beta) object. |
| [addLanguageFiles action](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicyuploadeddefinitionfile-addlanguagefiles?view=graph-rest-beta) | None |  |
| [removeLanguageFiles action](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicyuploadeddefinitionfile-removelanguagefiles?view=graph-rest-beta) | None |  |
| [updateLanguageFiles action](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicyuploadeddefinitionfile-updatelanguagefiles?view=graph-rest-beta) | None |  |
| [uploadNewVersion action](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicyuploadeddefinitionfile-uploadnewversion?view=graph-rest-beta) | None |  |
| [remove action](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicyuploadeddefinitionfile-remove?view=graph-rest-beta) | None |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The localized friendly name of the ADMX file. Inherited from [groupPolicyDefinitionFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinitionfile?view=graph-rest-beta) |
| description | String | The localized description of the policy settings in the ADMX file. The default value is empty. Inherited from [groupPolicyDefinitionFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinitionfile?view=graph-rest-beta) |
| languageCodes | String collection | The supported language codes for the ADMX file. Inherited from [groupPolicyDefinitionFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinitionfile?view=graph-rest-beta) |
| targetPrefix | String | Specifies the logical name that refers to the namespace within the ADMX file. Inherited from [groupPolicyDefinitionFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinitionfile?view=graph-rest-beta) |
| targetNamespace | String | Specifies the URI used to identify the namespace within the ADMX file. Inherited from [groupPolicyDefinitionFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinitionfile?view=graph-rest-beta) |
| policyType | [groupPolicyType](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicytype?view=graph-rest-beta) | Specifies the type of group policy. Inherited from [groupPolicyDefinitionFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinitionfile?view=graph-rest-beta). Possible values are: `admxBacked`, `admxIngested`. |
| revision | String | The revision version associated with the file. Inherited from [groupPolicyDefinitionFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinitionfile?view=graph-rest-beta) |
| fileName | String | The file name of the ADMX file without the path. For example: edge.admx Inherited from [groupPolicyDefinitionFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinitionfile?view=graph-rest-beta) |
| id | String | Key of the entity. Inherited from [groupPolicyDefinitionFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinitionfile?view=graph-rest-beta) |
| lastModifiedDateTime | DateTimeOffset | The date and time the entity was last modified. Inherited from [groupPolicyDefinitionFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinitionfile?view=graph-rest-beta) |
| status | [groupPolicyUploadedDefinitionFileStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyuploadeddefinitionfilestatus?view=graph-rest-beta) | The upload status of the uploaded ADMX file. Possible values are: `none`, `uploadInProgress`, `available`, `assigned`, `removalInProgress`, `uploadFailed`, `removalFailed`. |
| content | Binary | The contents of the uploaded ADMX file. |
| uploadDateTime | DateTimeOffset | The uploaded time of the uploaded ADMX file. |
| defaultLanguageCode | String | The default language of the uploaded ADMX file. |
| groupPolicyUploadedLanguageFiles | [groupPolicyUploadedLanguageFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyuploadedlanguagefile?view=graph-rest-beta) collection | The list of ADML files associated with the uploaded ADMX file. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| definitions | [groupPolicyDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinition?view=graph-rest-beta) collection | The group policy definitions associated with the file. Inherited from [groupPolicyDefinitionFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinitionfile?view=graph-rest-beta) |
| groupPolicyOperations | [groupPolicyOperation](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyoperation?view=graph-rest-beta) collection | The list of operations on the uploaded ADMX file. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.groupPolicyUploadedDefinitionFile",
  "displayName": "String",
  "description": "String",
  "languageCodes": [
    "String"
  ],
  "targetPrefix": "String",
  "targetNamespace": "String",
  "policyType": "String",
  "revision": "String",
  "fileName": "String",
  "id": "String (identifier)",
  "lastModifiedDateTime": "String (timestamp)",
  "status": "String",
  "content": "binary",
  "uploadDateTime": "String (timestamp)",
  "defaultLanguageCode": "String",
  "groupPolicyUploadedLanguageFiles": [
    {
      "@odata.type": "microsoft.graph.groupPolicyUploadedLanguageFile",
      "fileName": "String",
      "languageCode": "String",
      "content": "binary",
      "id": "String",
      "lastModifiedDateTime": "String (timestamp)"
    }
  ]
}
```
