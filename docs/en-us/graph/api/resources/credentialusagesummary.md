<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/credentialusagesummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-12 -->

# credentialUsageSummary resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Important

The credential usage summary details API is deprecated and will stop returning data on August 1, 2025. Use the new [User Registration Activity Summary](https://learn.microsoft.com/en-us/graph/api/resources/userregistrationactivitysummary?view=graph-rest-beta) API instead.

Represents the current state of how many users in your organization are using self-service password reset capabilities. For more information about license requirements for this feature, see [Authentication Methods Activity: Permissions and licenses](https://learn.microsoft.com/en-us/entra/identity/authentication/howto-authentication-methods-activity#permissions-and-licenses).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/reportroot-getcredentialusagesummary?view=graph-rest-beta) | credentialUsageSummary | Read properties and relationships of a credentialUsageSummary object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authMethod | [usageAuthMethod](https://learn.microsoft.com/en-us/graph/api/resources/usageauthmethod?view=graph-rest-beta) | Represents the authentication method that the user used. |
| failureActivityCount | Int64 | Provides the count of failed resets or registration data. |
| feature | featureType | Defines the feature to report. The possible values are: `registration`, `reset`, `unknownFutureValue`. |
| id | String | The unique identifier for the activity. Read-only. |
| successfulActivityCount | Int64 | Provides the count of successful registrations or resets. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id" : "String",
  "feature":"string",
  "successfulActivityCount":"Int64",
  "failureActivityCount": "Int64",
  "authMethod": "string"
}
```
