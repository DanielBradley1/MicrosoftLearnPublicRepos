<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/credentialuserregistrationcount?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# credentialUserRegistrationCount resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the current state of how many users in your organization are registered for self-service password reset and multifactor authentication capabilities. For more information about license requirements for this feature, see [Authentication Methods Activity: Permissions and licenses](https://learn.microsoft.com/en-us/entra/identity/authentication/howto-authentication-methods-activity#permissions-and-licenses).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/reportroot-getcredentialuserregistrationcount?view=graph-rest-beta) | credentialUserRegistrationCount collection | Report the current state of how many users in your organization are registered for self-service password reset and multifactor authentication \(MFA\) capabilities. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the activity. Read-only. |
| totalUserCount | Int64 | Provides the count of users with **accountEnabled** set to `true` in the tenant. |
| userRegistrationCounts | [userRegistrationCount](https://learn.microsoft.com/en-us/graph/api/resources/userregistrationcount?view=graph-rest-beta) collection | A collection of registration count and status information for users in your tenant. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id" : "String",
  "totalUserCount" : 23123,
  "userRegistrationCounts" :
  [
    { "registrationStatus":"registered", "registrationCount": 23423 },
    { "registrationStatus":"enabled", "registrationCount": 4234 },
    { "registrationStatus":"capable", "registrationCount": 323 },
    { "registrationStatus":"mfaRegistered", "registrationCount": 33 }
  ]
}
```
