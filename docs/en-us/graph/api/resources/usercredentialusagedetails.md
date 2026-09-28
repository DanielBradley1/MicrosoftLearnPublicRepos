<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/usercredentialusagedetails?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-12 -->

# userCredentialUsageDetails resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Important

The user credential usage details API is deprecated and will stop returning data on August 1, 2025. Use the new [User Events Summary](https://learn.microsoft.com/en-us/graph/api/resources/usereventssummary?view=graph-rest-beta) API instead.

Represents the self-service password reset usage for a given tenant. Details include user information, status of the reset, and the reason for failure. For more information about license requirements for this feature, see [Authentication Methods Activity: Permissions and licenses](https://learn.microsoft.com/en-us/entra/identity/authentication/howto-authentication-methods-activity#permissions-and-licenses).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/reportroot-list-usercredentialusagedetails?view=graph-rest-beta) | [userCredentialUsageDetails](https://learn.microsoft.com/en-us/graph/api/resources/usercredentialusagedetails?view=graph-rest-beta) | Read properties and relationships of a userCredentialUsageDetails object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authMethod | [usageAuthMethod](https://learn.microsoft.com/en-us/graph/api/resources/usageauthmethod?view=graph-rest-beta) | Represents the authentication method that the user used. |
| eventDateTime | DateTimeOffset | The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| failureReason | String | Provides the failure reason for the corresponding reset or registration workflow. |
| feature | featureType | The possible values are: `registration`, `reset`, `unknownFutureValue`. |
| id | String | Read-only. The unique identifier for the activity. Read-only. |
| isSuccess | Boolean | Indicates success or failure of the workflow. |
| userDisplayName | String | User name of the user performing the reset or registration workflow. |
| userPrincipalName | String | User principal name of the user performing the reset or registration workflow. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id" : "String",
  "feature":"string",
  "userPrincipalName":"String",
  "userDisplayName": "String",
  "isSuccess" : true,
  "authMethod": "string",
  "failureReason": "String",
  "eventDateTime" : "DateTimeOffset"
}
```
