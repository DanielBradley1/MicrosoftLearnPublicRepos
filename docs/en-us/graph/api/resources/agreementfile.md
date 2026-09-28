<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/agreementfile?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# agreementFile resource type

Namespace: microsoft.graph

Represents a customizable terms-of-use agreement file that a tenant manages with Microsoft Entra. It contains metadata about the agreement file \(for example, the name, the language, and whether it's the default file\).

Inherits from [agreementFileProperties](https://learn.microsoft.com/en-us/graph/api/resources/agreementfileproperties?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get default file](https://learn.microsoft.com/en-us/graph/api/agreementfile-get?view=graph-rest-1.0) | [agreementFile](https://learn.microsoft.com/en-us/graph/api/resources/agreementfile?view=graph-rest-1.0) | Read the properties and relationships of an [agreementFile](https://learn.microsoft.com/en-us/graph/api/resources/agreementfile?view=graph-rest-1.0) object. |
| [List files](https://learn.microsoft.com/en-us/graph/api/agreement-list-files?view=graph-rest-1.0) | [agreementFile](https://learn.microsoft.com/en-us/graph/api/resources/agreementfile?view=graph-rest-1.0) collection | Get a list of the [agreementFile](https://learn.microsoft.com/en-us/graph/api/resources/agreementfile?view=graph-rest-1.0) objects and their properties. |
| [Create localized files](https://learn.microsoft.com/en-us/graph/api/agreement-post-files?view=graph-rest-1.0) | [agreementFile](https://learn.microsoft.com/en-us/graph/api/resources/agreementfile?view=graph-rest-1.0) | Create a new [agreementFile](https://learn.microsoft.com/en-us/graph/api/resources/agreementfile?view=graph-rest-1.0) object. |
| [List localized files](https://learn.microsoft.com/en-us/graph/api/agreementfile-list-localizations?view=graph-rest-1.0) | [agreementFileLocalization](https://learn.microsoft.com/en-us/graph/api/resources/agreementfilelocalization?view=graph-rest-1.0) collection | Get the agreementFileLocalization resources from the localizations navigation property. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date time representing when the file was created. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [agreementFileProperties](https://learn.microsoft.com/en-us/graph/api/resources/agreementfileproperties?view=graph-rest-1.0). |
| displayName | String | Localized display name of the policy file of an agreement. The localized display name is shown to end users who view the agreement. Inherited from [agreementFileProperties](https://learn.microsoft.com/en-us/graph/api/resources/agreementfileproperties?view=graph-rest-1.0). |
| fileData | [agreementFileData](https://learn.microsoft.com/en-us/graph/api/resources/agreementfiledata?view=graph-rest-1.0) | Data that represents the terms of use PDF document. Read-only. Inherited from [agreementFileProperties](https://learn.microsoft.com/en-us/graph/api/resources/agreementfileproperties?view=graph-rest-1.0). |
| fileName | String | Name of the agreement file \(for example, TOU.pdf\). Read-only. Inherited from [agreementFileProperties](https://learn.microsoft.com/en-us/graph/api/resources/agreementfileproperties?view=graph-rest-1.0). |
| id | String | The identifier of the agreementFileVersion object. Read-only. Inherited from [agreementFileProperties](https://learn.microsoft.com/en-us/graph/api/resources/agreementfileproperties?view=graph-rest-1.0). |
| isDefault | Boolean | If none of the languages matches the client preference, indicates whether this is the default agreement file. If none of the files are marked as default, the first one is treated as the default. Read-only. Inherited from [agreementFileProperties](https://learn.microsoft.com/en-us/graph/api/resources/agreementfileproperties?view=graph-rest-1.0). |
| isMajorVersion | Boolean | Indicates whether the agreement file is a major version update. Major version updates invalidate the agreement's acceptances on the corresponding language. Inherited from [agreementFileProperties](https://learn.microsoft.com/en-us/graph/api/resources/agreementfileproperties?view=graph-rest-1.0). |
| language | String | The language of the agreement file in the format "languagecode2-country/regioncode2". "languagecode2" is a lowercase two-letter code derived from ISO 639-1, while "country/regioncode2" is derived from ISO 3166 and usually consists of two uppercase letters, or a BCP-47 language tag. For example, U.S. English is `en-US`. Read-only. Inherited from [agreementFileProperties](https://learn.microsoft.com/en-us/graph/api/resources/agreementfileproperties?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| localizations | [agreementFileLocalization](https://learn.microsoft.com/en-us/graph/api/resources/agreementfilelocalization?view=graph-rest-1.0) collection | The localized version of the terms of use agreement files attached to the agreement. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "fileData": {"@odata.type": "microsoft.graph.agreementFile"},
  "fileName": "String",
  "id": "String (identifier)",
  "isDefault": true,
  "language": "String"
}
```
