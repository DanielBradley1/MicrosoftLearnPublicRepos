<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/credentialuserregistrationdetails?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# credentialUserRegistrationDetails resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Important

The credential user registration details API is deprecated and will stop returning data on June 30, 2024. Use the new [User registration details](https://learn.microsoft.com/en-us/graph/api/resources/userregistrationdetails?view=graph-rest-beta) API instead.

Represents the details of the usage of self-service password reset and multi-factor authentication \(MFA\) for all registered users. Details include user information, status of registration, and the authentication method used.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/reportroot-list-credentialuserregistrationdetails?view=graph-rest-beta) | credentialUserRegistrationDetails collection | Get a list of [credentialUserRegistrationDetails](https://learn.microsoft.com/en-us/graph/api/resources/credentialuserregistrationdetails?view=graph-rest-beta) objects for a given tenant. |
|  |  |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authMethods | registrationAuthMethod collection | Represents the authentication method that the user has registered. The possible values are: `email`, `mobilePhone`, `officePhone`, `securityQuestion` \(only used for self-service password reset\), `appNotification`, `appCode`, `alternateMobilePhone` \(supported only in registration\), `fido`, `appPassword`, `unknownFutureValue`. |
| id | String | The unique identifier for the activity. Read-only. |
| isCapable | Boolean | Indicates whether the user is ready to perform self-service password reset or MFA. |
| isEnabled | Boolean | Indicates whether the user enabled to perform self-service password reset. |
| isMfaRegistered | Boolean | Indicates whether the user is registered for MFA. |
| isRegistered | Boolean | Indicates whether the user has registered any authentication methods for self-service password reset. |
| userDisplayName | String | Provides the user name of the corresponding user. |
| userPrincipalName | String | Provides the user principal name of the corresponding user. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id" : "String",
  "userPrincipalName":"String",
  "userDisplayName": "String",
  "authMethods": ["string"],
  "isRegistered" : false,
  "isEnabled" : true,
  "isCapable" : false,
  "isMfaRegistered" : true
}
```
