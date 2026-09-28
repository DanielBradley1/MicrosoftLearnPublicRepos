<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/dynamics-employee?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# employee resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an employee in Dynamics 365 Business Central.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get employee](https://learn.microsoft.com/en-us/graph/api/dynamics-employee-get?view=graph-rest-beta) | employee | Get an employee object. |
| [Create employee](https://learn.microsoft.com/en-us/graph/api/dynamics-create-employee?view=graph-rest-beta) | employee | Create an employee object. |
| [Update employee](https://learn.microsoft.com/en-us/graph/api/dynamics-employee-update?view=graph-rest-beta) | employee | Update an employee object. |
| [Delete employee](https://learn.microsoft.com/en-us/graph/api/dynamics-employee-delete?view=graph-rest-beta) | none | Delete an employee object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | GUID | The employee ID. Noneditable. |
| number | string | The employee number. Read-Only. |
| displayName | string | The employee givenName + surname. Read-Only. |
| givenName | string | The given name of the employee. |
| middleName | string | The middle name of the employee. |
| surname | string | The surname of the employee |
| jobTitle | string | The job title of the employee |
| address | [NAV.PostalAddress](https://learn.microsoft.com/en-us/graph/api/resources/dynamics-complextypes?view=graph-rest-beta) | Specifies the employee's address. This address appears on all resource documents for the employee. |
| phoneNumber | string | Specifies the employee's telephone number. |
| mobilePhone | string | Specifies the employee's mobile telephone number. |
| email | string | Specifies the employee's email address. |
| personalEmail | string | Specifies the employee's personal email address. |
| employmentDate | date | Specifies the date when the employee began to work for the company. |
| terminationDate | date | Specifies the date when the employee was terminated, due to retirement or dismissal, for example. |
| status | string | Specifies the employee's status. Possible values are Active, Inactive, or Terminated |
| birthDate | date | Specifies the employee's date of birth. |
| picture | stream | The employee picture. Read-Only. |
| lastModifiedDateTime | datetime | The last datetime the employee was modified. Read-Only. |

## Relationships

None

## JSON representation

The following JSON representation shows the resource type.

```json
{
    "id": "GUID",
    "number": "string",
    "displayName": "string",
    "givenName": "string",
    "middleName": "string",
    "surname": "string",
    "jobTitle": "string",
    "address": "NAV.PostalAddress",
    "phoneNumber": "string",
    "mobilePhone": "string",
    "email": "string",
    "personalEmail": "string",
    "employmentDate": "date",
    "terminationDate": "date",
    "status": "string",
    "birthDate": "date",
    "picture": "stream",
    "lastModifiedDateTime": "datetime"
}
```
