<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/industrydata-referencedefinition?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# referenceDefinition resource type

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an enumerated reference value. Each supported industry domain receives a distinct collection of default values and customers can further customize them by overriding default values or adding new values to the tenant. The **referenceDefinition** objects are used throughout the system, both for configuration and validating data during transformation.

Each **referenceDefinition** uses a composite identifier of `{referenceType}-{code}`. This provides a more natural developer experience as the vast majority of code values are defined by a standard body, which allows developers in specific industry domains to better recognize the format.

The following are examples of types:

- **refRole**: Used when associating and validated during import
- **refOrgType**: Used when associating and validated during import
- **userMatchTarget**: Only used for configuration

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/industrydata-referencedefinition-list?view=graph-rest-beta) | [microsoft.graph.industryData.referenceDefinition](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-referencedefinition?view=graph-rest-beta) collection | Get a list of the **referenceDefinition** objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/industrydata-referencedefinition-get?view=graph-rest-beta) | [microsoft.graph.industryData.referenceDefinition](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-referencedefinition?view=graph-rest-beta) | Read the properties and relationships of a **referenceDefinition** object. |
| [Create](https://learn.microsoft.com/en-us/graph/api/industrydata-referencedefinition-post?view=graph-rest-beta) | [microsoft.graph.industryData.referenceDefinition](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-referencedefinition?view=graph-rest-beta) | Create a new **referenceDefinition** object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/industrydata-referencedefinition-update?view=graph-rest-beta) | [microsoft.graph.industryData.referenceDefinition](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-referencedefinition?view=graph-rest-beta) | Update the properties of a **referenceDefinition** object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/industrydata-referencedefinition-delete?view=graph-rest-beta) | None | Delete a **referenceDefinition** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| code | String | The code value for the definition that must be unique within the **referenceType**. |
| createdDateTime | DateTimeOffset | The date and time when the definition was created. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| displayName | String | A human-readable representation of the reference code value for display in a user interface. |
| isDisabled | Boolean | Indicates whether the definition is disabled. |
| lastModifiedDateTime | DateTimeOffset | The date and time when the definition was most recently changed. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| referenceType | String | The categorical type for a collection of enumerated values. |
| sortIndex | Int32 | The index that specifies the order in which to present the definition to the user. Must be unique within the referenceType. |
| source | String | The standards body or organization source which defined the code. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.industryData.referenceDefinition",
  "code": "String",
  "createdDateTime": "String (timestamp)",
  "displayName": "String",
  "isDisabled": "Boolean",
  "lastModifiedDateTime": "String (timestamp)",
  "referenceType": "String",
  "sortIndex": "Int32",
  "source": "String"
}
```
