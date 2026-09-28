<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-companyterms-termsandconditionsassignment?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# termsAndConditionsAssignment resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

A termsAndConditionsAssignment entity represents the assignment of a given Terms and Conditions \(T&C\) policy to a given group. Users in the group will be required to accept the terms in order to have devices enrolled into Intune.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List termsAndConditionsAssignments](https://learn.microsoft.com/en-us/graph/api/intune-companyterms-termsandconditionsassignment-list?view=graph-rest-1.0) | [termsAndConditionsAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-companyterms-termsandconditionsassignment?view=graph-rest-1.0) collection | List properties and relationships of the [termsAndConditionsAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-companyterms-termsandconditionsassignment?view=graph-rest-1.0) objects. |
| [Get termsAndConditionsAssignment](https://learn.microsoft.com/en-us/graph/api/intune-companyterms-termsandconditionsassignment-get?view=graph-rest-1.0) | [termsAndConditionsAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-companyterms-termsandconditionsassignment?view=graph-rest-1.0) | Read properties and relationships of the [termsAndConditionsAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-companyterms-termsandconditionsassignment?view=graph-rest-1.0) object. |
| [Create termsAndConditionsAssignment](https://learn.microsoft.com/en-us/graph/api/intune-companyterms-termsandconditionsassignment-create?view=graph-rest-1.0) | [termsAndConditionsAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-companyterms-termsandconditionsassignment?view=graph-rest-1.0) | Create a new [termsAndConditionsAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-companyterms-termsandconditionsassignment?view=graph-rest-1.0) object. |
| [Delete termsAndConditionsAssignment](https://learn.microsoft.com/en-us/graph/api/intune-companyterms-termsandconditionsassignment-delete?view=graph-rest-1.0) | None | Deletes a [termsAndConditionsAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-companyterms-termsandconditionsassignment?view=graph-rest-1.0). |
| [Update termsAndConditionsAssignment](https://learn.microsoft.com/en-us/graph/api/intune-companyterms-termsandconditionsassignment-update?view=graph-rest-1.0) | [termsAndConditionsAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-companyterms-termsandconditionsassignment?view=graph-rest-1.0) | Update the properties of a [termsAndConditionsAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-companyterms-termsandconditionsassignment?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier of the entity. |
| target | [deviceAndAppManagementAssignmentTarget](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceandappmanagementassignmenttarget?view=graph-rest-1.0) | Assignment target that the T&C policy is assigned to. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.termsAndConditionsAssignment",
  "id": "String (identifier)",
  "target": {
    "@odata.type": "microsoft.graph.scopeTagGroupAssignmentTarget",
    "targetType": "String",
    "entraObjectId": "String"
  }
}
```
