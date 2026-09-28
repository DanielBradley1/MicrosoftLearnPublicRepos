<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-companyterms-termsandconditionsgroupassignment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# termsAndConditionsGroupAssignment resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

A termsAndConditionsGroupAssignment entity represents the assignment of a given Terms and Conditions \(T&C\) policy to a given group. Users in the group will be required to accept the terms in order to have devices enrolled into Intune.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List termsAndConditionsGroupAssignments](https://learn.microsoft.com/en-us/graph/api/intune-companyterms-termsandconditionsgroupassignment-list?view=graph-rest-beta) | [termsAndConditionsGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-companyterms-termsandconditionsgroupassignment?view=graph-rest-beta) collection | List properties and relationships of the [termsAndConditionsGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-companyterms-termsandconditionsgroupassignment?view=graph-rest-beta) objects. |
| [Get termsAndConditionsGroupAssignment](https://learn.microsoft.com/en-us/graph/api/intune-companyterms-termsandconditionsgroupassignment-get?view=graph-rest-beta) | [termsAndConditionsGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-companyterms-termsandconditionsgroupassignment?view=graph-rest-beta) | Read properties and relationships of the [termsAndConditionsGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-companyterms-termsandconditionsgroupassignment?view=graph-rest-beta) object. |
| [Create termsAndConditionsGroupAssignment](https://learn.microsoft.com/en-us/graph/api/intune-companyterms-termsandconditionsgroupassignment-create?view=graph-rest-beta) | [termsAndConditionsGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-companyterms-termsandconditionsgroupassignment?view=graph-rest-beta) | Create a new [termsAndConditionsGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-companyterms-termsandconditionsgroupassignment?view=graph-rest-beta) object. |
| [Delete termsAndConditionsGroupAssignment](https://learn.microsoft.com/en-us/graph/api/intune-companyterms-termsandconditionsgroupassignment-delete?view=graph-rest-beta) | None | Deletes a [termsAndConditionsGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-companyterms-termsandconditionsgroupassignment?view=graph-rest-beta). |
| [Update termsAndConditionsGroupAssignment](https://learn.microsoft.com/en-us/graph/api/intune-companyterms-termsandconditionsgroupassignment-update?view=graph-rest-beta) | [termsAndConditionsGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-companyterms-termsandconditionsgroupassignment?view=graph-rest-beta) | Update the properties of a [termsAndConditionsGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-companyterms-termsandconditionsgroupassignment?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier of the entity. |
| targetGroupId | String | Unique identifier of a group that the T&C policy is assigned to. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| termsAndConditions | [termsAndConditions](https://learn.microsoft.com/en-us/graph/api/resources/intune-companyterms-termsandconditions?view=graph-rest-beta) | Navigation link to the terms and conditions that are assigned. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.termsAndConditionsGroupAssignment",
  "id": "String (identifier)",
  "targetGroupId": "String"
}
```
