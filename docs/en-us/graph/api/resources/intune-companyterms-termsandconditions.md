<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-companyterms-termsandconditions?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# termsAndConditions resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

A termsAndConditions entity represents the metadata and contents of a given Terms and Conditions \(T&C\) policy. T&C policies’ contents are presented to users upon their first attempt to enroll into Intune and subsequently upon edits where an administrator has required re-acceptance. They enable administrators to communicate the provisions to which a user must agree in order to have devices enrolled into Intune.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List termsAndConditionses](https://learn.microsoft.com/en-us/graph/api/intune-companyterms-termsandconditions-list?view=graph-rest-1.0) | [termsAndConditions](https://learn.microsoft.com/en-us/graph/api/resources/intune-companyterms-termsandconditions?view=graph-rest-1.0) collection | List properties and relationships of the [termsAndConditions](https://learn.microsoft.com/en-us/graph/api/resources/intune-companyterms-termsandconditions?view=graph-rest-1.0) objects. |
| [Get termsAndConditions](https://learn.microsoft.com/en-us/graph/api/intune-companyterms-termsandconditions-get?view=graph-rest-1.0) | [termsAndConditions](https://learn.microsoft.com/en-us/graph/api/resources/intune-companyterms-termsandconditions?view=graph-rest-1.0) | Read properties and relationships of the [termsAndConditions](https://learn.microsoft.com/en-us/graph/api/resources/intune-companyterms-termsandconditions?view=graph-rest-1.0) object. |
| [Create termsAndConditions](https://learn.microsoft.com/en-us/graph/api/intune-companyterms-termsandconditions-create?view=graph-rest-1.0) | [termsAndConditions](https://learn.microsoft.com/en-us/graph/api/resources/intune-companyterms-termsandconditions?view=graph-rest-1.0) | Create a new [termsAndConditions](https://learn.microsoft.com/en-us/graph/api/resources/intune-companyterms-termsandconditions?view=graph-rest-1.0) object. |
| [Delete termsAndConditions](https://learn.microsoft.com/en-us/graph/api/intune-companyterms-termsandconditions-delete?view=graph-rest-1.0) | None | Deletes a [termsAndConditions](https://learn.microsoft.com/en-us/graph/api/resources/intune-companyterms-termsandconditions?view=graph-rest-1.0). |
| [Update termsAndConditions](https://learn.microsoft.com/en-us/graph/api/intune-companyterms-termsandconditions-update?view=graph-rest-1.0) | [termsAndConditions](https://learn.microsoft.com/en-us/graph/api/resources/intune-companyterms-termsandconditions?view=graph-rest-1.0) | Update the properties of a [termsAndConditions](https://learn.microsoft.com/en-us/graph/api/resources/intune-companyterms-termsandconditions?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier of the T&C policy. |
| createdDateTime | DateTimeOffset | DateTime the object was created. |
| lastModifiedDateTime | DateTimeOffset | DateTime the object was last modified. |
| displayName | String | Administrator-supplied name for the T&C policy. |
| description | String | Administrator-supplied description of the T&C policy. |
| title | String | Administrator-supplied title of the terms and conditions. This is shown to the user on prompts to accept the T&C policy. |
| bodyText | String | Administrator-supplied body text of the terms and conditions, typically the terms themselves. This is shown to the user on prompts to accept the T&C policy. |
| acceptanceStatement | String | Administrator-supplied explanation of the terms and conditions, typically describing what it means to accept the terms and conditions set out in the T&C policy. This is shown to the user on prompts to accept the T&C policy. |
| version | Int32 | Integer indicating the current version of the terms. Incremented when an administrator makes a change to the terms and wishes to require users to re-accept the modified T&C policy. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| assignments | [termsAndConditionsAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-companyterms-termsandconditionsassignment?view=graph-rest-1.0) collection | The list of assignments for this T&C policy. |
| acceptanceStatuses | [termsAndConditionsAcceptanceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-companyterms-termsandconditionsacceptancestatus?view=graph-rest-1.0) collection | The list of acceptance statuses for this T&C policy. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.termsAndConditions",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "displayName": "String",
  "description": "String",
  "title": "String",
  "bodyText": "String",
  "acceptanceStatement": "String",
  "version": 1024
}
```
