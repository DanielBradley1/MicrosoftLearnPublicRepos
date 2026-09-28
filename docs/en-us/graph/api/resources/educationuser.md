<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/educationuser?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# educationUser resource type

Namespace: microsoft.graph

A user in the system. This is an education-specific variant of the user with the same **id** that Microsoft Graph will return from the non-education-specific `/users` endpoint. This object provides a targeted subset of properties from the core [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) object and adds a set of education-specific properties such as **primaryRole**, **student**, and **teacher** data.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/educationuser-list?view=graph-rest-1.0) | [educationUser](https://learn.microsoft.com/en-us/graph/api/resources/educationuser?view=graph-rest-1.0) collection | Get a list of the [educationUser](https://learn.microsoft.com/en-us/graph/api/resources/educationuser?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/educationuser-post?view=graph-rest-1.0) | [educationUser](https://learn.microsoft.com/en-us/graph/api/resources/educationuser?view=graph-rest-1.0) | Create a new [educationUser](https://learn.microsoft.com/en-us/graph/api/resources/educationuser?view=graph-rest-1.0) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/educationuser-get?view=graph-rest-1.0) | [educationUser](https://learn.microsoft.com/en-us/graph/api/resources/educationuser?view=graph-rest-1.0) | Read the properties and relationships of an [educationUser](https://learn.microsoft.com/en-us/graph/api/resources/educationuser?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/educationuser-update?view=graph-rest-1.0) | [educationUser](https://learn.microsoft.com/en-us/graph/api/resources/educationuser?view=graph-rest-1.0) | Update the properties of an [educationUser](https://learn.microsoft.com/en-us/graph/api/resources/educationuser?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/educationuser-delete?view=graph-rest-1.0) | None | Delete an [educationUser](https://learn.microsoft.com/en-us/graph/api/resources/educationuser?view=graph-rest-1.0) object. |
| [Get changes to users](https://learn.microsoft.com/en-us/graph/api/educationuser-delta?view=graph-rest-1.0) | [educationUser](https://learn.microsoft.com/en-us/graph/api/resources/educationuser?view=graph-rest-1.0) collection | Get incremental changes to the resource collection. |
| [List taught classes](https://learn.microsoft.com/en-us/graph/api/educationuser-list-taughtclasses?view=graph-rest-1.0) | [educationClass](https://learn.microsoft.com/en-us/graph/api/resources/educationclass?view=graph-rest-1.0) collection | Get the **educationClass** resources from the **taughtClasses** navigation property. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accountEnabled | Boolean | `True` if the account is enabled; otherwise, `false`. This property is required when a user is created. Supports `$filter`. |
| assignedLicenses | [assignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/assignedlicense?view=graph-rest-1.0) collection | The licenses that are assigned to the user. Not nullable. |
| assignedPlans | [assignedPlan](https://learn.microsoft.com/en-us/graph/api/resources/assignedplan?view=graph-rest-1.0) collection | The plans that are assigned to the user. Read-only. Not nullable. |
| businessPhones | String collection | The telephone numbers for the user. **Note:** Although this is a string collection, only one number can be set for this property. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The entity who created the user. |
| department | String | The name for the department in which the user works. Supports `$filter`. |
| displayName | String | The name displayed in the address book for the user. This is usually the combination of the user's first name, middle initial, and last name. This property is required when a user is created and it cannot be cleared during updates. Supports `$filter` and `$orderby`. |
| externalSource | educationExternalSource | Where this user was created from. The possible values are: `sis`, `manual`. |
| externalSourceDetail | String | The name of the external source this resource was generated from. |
| givenName | String | The given name \(first name\) of the user. Supports `$filter`. |
| id | String | Object identifier. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| mail | String | The SMTP address for the user, for example, `jeff@contoso.com`. Read-Only. Supports `$filter`. |
| mailingAddress | [physicalAddress](https://learn.microsoft.com/en-us/graph/api/resources/physicaladdress?view=graph-rest-1.0) | The mail address of the user. |
| mailNickname | String | The mail alias for the user. This property must be specified when a user is created. Supports `$filter`. |
| middleName | String | The middle name of the user. |
| mobilePhone | String | The primary cellular telephone number for the user. |
| officeLocation | String | The office location for the user. |
| onPremisesInfo | [educationOnPremisesInfo](https://learn.microsoft.com/en-us/graph/api/resources/educationonpremisesinfo?view=graph-rest-1.0) | Additional information used to associate the Microsoft Entra user with its Active Directory counterpart. |
| passwordPolicies | String | Specifies password policies for the user. This value is an enumeration with one possible value being `DisableStrongPassword`, which allows weaker passwords than the default policy to be specified. `DisablePasswordExpiration` can also be specified. The two can be specified together; for example: `DisablePasswordExpiration, DisableStrongPassword`. |
| passwordProfile | [passwordProfile](https://learn.microsoft.com/en-us/graph/api/resources/passwordprofile?view=graph-rest-1.0) | Specifies the password profile for the user. The profile contains the user's password. This property is required when a user is created. The password in the profile must satisfy minimum requirements as specified by the **passwordPolicies** property. By default, a strong password is required. |
| preferredLanguage | String | The preferred language for the user that should follow the ISO 639-1 code, for example, `en-US`. |
| primaryRole | educationUserRole | Default role for a user. The user's role might be different in an individual class. The possible values are: `student`, `teacher`, `none`, `unknownFutureValue`. |
| provisionedPlans | [provisionedPlan](https://learn.microsoft.com/en-us/graph/api/resources/provisionedplan?view=graph-rest-1.0) collection | The plans that are provisioned for the user. Read-only. Not nullable. |
| refreshTokensValidFromDateTime | DateTimeOffset | Any refresh tokens or sessions tokens \(session cookies\) issued before this time are invalid, and applications get an error when using an invalid refresh or sessions token to acquire a delegated access token \(to access APIs such as Microsoft Graph\). If this happens, the application needs to acquire a new refresh token by requesting the authorized endpoint.  <br>  <br>Requires `$select` to retrieve. Read-only. |
| relatedContacts | [relatedContact](https://learn.microsoft.com/en-us/graph/api/resources/relatedcontact?view=graph-rest-1.0) collection | Related records associated with the user. Read-only. |
| residenceAddress | [physicalAddress](https://learn.microsoft.com/en-us/graph/api/resources/physicaladdress?view=graph-rest-1.0) | The address where the user lives. |
| showInAddressList | Boolean | `True` if the Outlook Global Address List should contain this user; otherwise, `false`. If not set, this will be treated as `true`. For users invited through the invitation manager, this property will be set to `false`. |
| student | [educationStudent](https://learn.microsoft.com/en-us/graph/api/resources/educationstudent?view=graph-rest-1.0) | If the primary role is student, this block will contain student specific data. |
| surname | String | The user's surname \(family name or last name\). Supports `$filter`. |
| teacher | [educationTeacher](https://learn.microsoft.com/en-us/graph/api/resources/educationteacher?view=graph-rest-1.0) | If the primary role is teacher, this block will contain teacher specific data. |
| usageLocation | String | A two-letter country code \(ISO standard 3166\). Required for users who will be assigned licenses due to a legal requirement to check for availability of services in countries or regions. Examples include: `US`, `JP`, and `GB`. Not nullable. Supports `$filter`. |
| userPrincipalName | String | The user principal name \(UPN\) of the user. The UPN is an internet-style login name for the user based on the internet standard RFC 822. By convention, this should map to the user's email name. The general format is `alias@domain`, where domain must be present in the tenant's collection of verified domains. This property is required when a user is created. The verified domains for the tenant can be accessed from the **verifiedDomains** property of the [organization](https://learn.microsoft.com/en-us/graph/api/resources/organization?view=graph-rest-1.0). Supports `$filter` and `$orderby`. |
| userType | String | A string value that can be used to classify user types in your directory, such as `Member` and `Guest`. Supports `$filter`. |

Important

When using Delegated permission scopes, Microsoft Graph will only return a limited set of properties: **id**, **primaryRole**, **accountEnabled**, **displayName**, **givenName**, **surname**, **userPrincipalName**, **userType**, **onPremisesInfo**, **student/externalId**, **teacher/externalId**. If your application requires additional properties, you must use Application permission scopes.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| assignments | [educationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/educationassignment?view=graph-rest-1.0) collection | Assignments belonging to the user. |
| classes | [educationClass](https://learn.microsoft.com/en-us/graph/api/resources/educationclass?view=graph-rest-1.0) collection | Classes to which the user belongs. Nullable. |
| schools | [educationSchool](https://learn.microsoft.com/en-us/graph/api/resources/educationschool?view=graph-rest-1.0) collection | Schools to which the user belongs. Nullable. |
| taughtClasses | [educationClass](https://learn.microsoft.com/en-us/graph/api/resources/educationclass?view=graph-rest-1.0) collection | Classes for which the user is a teacher. |
| user | [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) | The directory user that corresponds to this user. |
| rubrics | [educationRubric](https://learn.microsoft.com/en-us/graph/api/resources/educationrubric?view=graph-rest-1.0) collection | When set, the grading rubric attached to the assignment. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.educationUser",
  "accountEnabled": "Boolean",
  "assignedLicenses": [
    {
      "@odata.type": "microsoft.graph.assignedLicense"
    }
  ],
  "assignedPlans": [
    {
      "@odata.type": "microsoft.graph.assignedPlan"
    }
  ],
  "businessPhones": ["String"],
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "department": "String",
  "displayName": "String",
  "externalSource": "String",
  "externalSourceDetail": "String",
  "givenName": "String",
  "id": "String (identifier)",
  "mail": "String",
  "mailingAddress": {
    "@odata.type": "microsoft.graph.physicalAddress"
  },
  "mailNickname": "String",
  "middleName": "String",
  "mobilePhone": "String",
  "officeLocation": "String",
  "onPremisesInfo": {
    "@odata.type": "microsoft.graph.educationOnPremisesInfo"
  },
  "passwordPolicies": "String",
  "passwordProfile": {
    "@odata.type": "microsoft.graph.passwordProfile"
  },
  "preferredLanguage": "String",
  "primaryRole": "String",
  "provisionedPlans": [
    {
      "@odata.type": "microsoft.graph.provisionedPlan"
    }
  ],
  "refreshTokensValidFromDateTime": "String (timestamp)",
  "residenceAddress": {
    "@odata.type": "microsoft.graph.physicalAddress"
  },
  "showInAddressList": "Boolean",
  "student": {
    "@odata.type": "microsoft.graph.educationStudent"
  },
  "surname": "String",
  "teacher": {
    "@odata.type": "microsoft.graph.educationTeacher"
  },
  "usageLocation": "String",
  "userPrincipalName": "String",
  "userType": "String"
}
```
