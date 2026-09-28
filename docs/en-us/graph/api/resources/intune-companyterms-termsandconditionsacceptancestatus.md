<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-companyterms-termsandconditionsacceptancestatus?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# termsAndConditionsAcceptanceStatus resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

A termsAndConditionsAcceptanceStatus entity represents the acceptance status of a given Terms and Conditions \(T&C\) policy by a given user. Users must accept the most up-to-date version of the terms in order to retain access to the Company Portal.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List termsAndConditionsAcceptanceStatuses](https://learn.microsoft.com/en-us/graph/api/intune-companyterms-termsandconditionsacceptancestatus-list?view=graph-rest-1.0) | [termsAndConditionsAcceptanceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-companyterms-termsandconditionsacceptancestatus?view=graph-rest-1.0) collection | List properties and relationships of the [termsAndConditionsAcceptanceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-companyterms-termsandconditionsacceptancestatus?view=graph-rest-1.0) objects. |
| [Get termsAndConditionsAcceptanceStatus](https://learn.microsoft.com/en-us/graph/api/intune-companyterms-termsandconditionsacceptancestatus-get?view=graph-rest-1.0) | [termsAndConditionsAcceptanceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-companyterms-termsandconditionsacceptancestatus?view=graph-rest-1.0) | Read properties and relationships of the [termsAndConditionsAcceptanceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-companyterms-termsandconditionsacceptancestatus?view=graph-rest-1.0) object. |
| [Create termsAndConditionsAcceptanceStatus](https://learn.microsoft.com/en-us/graph/api/intune-companyterms-termsandconditionsacceptancestatus-create?view=graph-rest-1.0) | [termsAndConditionsAcceptanceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-companyterms-termsandconditionsacceptancestatus?view=graph-rest-1.0) | Create a new [termsAndConditionsAcceptanceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-companyterms-termsandconditionsacceptancestatus?view=graph-rest-1.0) object. |
| [Delete termsAndConditionsAcceptanceStatus](https://learn.microsoft.com/en-us/graph/api/intune-companyterms-termsandconditionsacceptancestatus-delete?view=graph-rest-1.0) | None | Deletes a [termsAndConditionsAcceptanceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-companyterms-termsandconditionsacceptancestatus?view=graph-rest-1.0). |
| [Update termsAndConditionsAcceptanceStatus](https://learn.microsoft.com/en-us/graph/api/intune-companyterms-termsandconditionsacceptancestatus-update?view=graph-rest-1.0) | [termsAndConditionsAcceptanceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-companyterms-termsandconditionsacceptancestatus?view=graph-rest-1.0) | Update the properties of a [termsAndConditionsAcceptanceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-companyterms-termsandconditionsacceptancestatus?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier of the entity. |
| userDisplayName | String | Display name of the user whose acceptance the entity represents. |
| acceptedVersion | Int32 | Most recent version number of the T&C accepted by the user. |
| acceptedDateTime | DateTimeOffset | DateTime when the terms were last accepted by the user. |
| userPrincipalName | String | The userPrincipalName of the User that accepted the term. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| termsAndConditions | [termsAndConditions](https://learn.microsoft.com/en-us/graph/api/resources/intune-companyterms-termsandconditions?view=graph-rest-1.0) | Navigation link to the terms and conditions that are assigned. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.termsAndConditionsAcceptanceStatus",
  "id": "String (identifier)",
  "userDisplayName": "String",
  "acceptedVersion": 1024,
  "acceptedDateTime": "String (timestamp)",
  "userPrincipalName": "String"
}
```
