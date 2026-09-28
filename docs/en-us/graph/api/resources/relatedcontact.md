<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/relatedcontact?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# relatedContact resource type

Namespace: microsoft.graph

Represents a contact record related to an [educationUser](https://learn.microsoft.com/en-us/graph/api/resources/educationuser?view=graph-rest-1.0) that provides information for guardians, aides, doctors, and so on.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accessConsent | Boolean | Indicates whether the user has been consented to access student data. |
| displayName | String | Name of the contact. Required. |
| emailAddress | String | Primary email address of the contact. Required. |
| mobilePhone | String | Mobile phone number of the contact. |
| relationship | contactRelationship | Relationship to the user. The possible values are: `parent`, `relative`, `aide`, `doctor`, `guardian`, `child`, `other`, `unknownFutureValue`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "accessConsent": true,
  "displayName": "String",
  "emailAddress": "String",
  "mobilePhone": "String",
  "relationship": "String"
}
```
