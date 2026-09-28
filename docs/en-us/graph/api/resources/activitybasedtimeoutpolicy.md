<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/activitybasedtimeoutpolicy?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-18 -->

# activityBasedTimeoutPolicy resource type

Namespace: microsoft.graph

Represents a policy that can control the idle timeout for web sessions for [applications that support activity-based timeout functionality](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/idle-session-timeout-web-apps). Applications enforce automatic sign out after a period of inactivity. This type of policy can only be applied at the organization level \(by setting the **isOrganizationDefault** property to `true`\).

Inherits from [stsPolicy](https://learn.microsoft.com/en-us/graph/api/resources/stspolicy?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/activitybasedtimeoutpolicy-list?view=graph-rest-1.0) | [activityBasedTimeoutPolicy](https://learn.microsoft.com/en-us/graph/api/resources/activitybasedtimeoutpolicy?view=graph-rest-1.0) | Read properties and relationships of activityBasedTimeoutPolicy objects. |
| [Create](https://learn.microsoft.com/en-us/graph/api/activitybasedtimeoutpolicy-post-activitybasedtimeoutpolicies?view=graph-rest-1.0) | [activityBasedTimeoutPolicy](https://learn.microsoft.com/en-us/graph/api/resources/activitybasedtimeoutpolicy?view=graph-rest-1.0) | Create an activityBasedTimeoutPolicy object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/activitybasedtimeoutpolicy-get?view=graph-rest-1.0) | [activityBasedTimeoutPolicy](https://learn.microsoft.com/en-us/graph/api/resources/activitybasedtimeoutpolicy?view=graph-rest-1.0) | Read properties and relationships of an activityBasedTimeoutPolicy object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/activitybasedtimeoutpolicy-update?view=graph-rest-1.0) | None | Update an activityBasedTimeoutPolicy object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/activitybasedtimeoutpolicy-delete?view=graph-rest-1.0) | None | Delete an activityBasedTimeoutPolicy object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| definition | String collection | A string collection containing a JSON string that defines the rules and settings for this policy. See below for more details about the JSON schema for this property. Required. |
| displayName | String | Display name for this policy. Required. |
| id | String | Unique identifier for this policy. Read-only. |
| isOrganizationDefault | Boolean | If set to true, activates this policy. There can be many policies for the same policy type, but only one can be activated as the organization default. Optional, default value is false. |

### Properties of an activity-based timeout policy definition

The properties below form the JSON object that represents an activity-based timeout policy. This JSON object must be **converted to a string with quotations escaped** to be inserted into the **definition** property. An example is shown below in JSON format:

```json
{
  "definition":["{\"ActivityBasedTimeoutPolicy\":{\"Version\":1,\"ApplicationPolicies\":[{\"ApplicationId\":\"default\",\"WebSessionIdleTimeout\":\"01:00:00\"},{\"ApplicationId\":\"c44b4083-3bb0-49c1-b47d-974e53cbdf3c\",\"WebSessionIdleTimeout\":\"00:15:00\"}]}}"]
}
```

> **Note:** All time durations in these properties are specified in the format "dd.hh:mm:ss".

> **Note:** Max values for properties denoted in "days" are 1 second short of the denoted number of days. For example, the max value of 1 days is specified as "23:59:59".

| Property | Type | Description |
| :--- | :--- | :--- |
| ApplicationPolicies | JSON object | Collection of application policy. An application policy, is a combination of an ApplicationId and a WebSessionIdleTimeout:  <br><br><br>- **ApplicationId**: Allowed values:<br><br>  - default: applies the policy to all applications that support activity-based timeout functionality but don't have application-specific override<br>  - c44b4083-3bb0-49c1-b47d-974e53cbdf3c: applies the policy to the Azure portal<br><br>- **WebSessionIdleTimeout**: The period of user inactivity after which the user's web session is considered expired. The minimum value is 5 minutes; the maximum value is one day. |
| Version | Integer | Policy version. Set value of 1. Required. |

## Relationships

None

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "definition": ["String"],
  "description": "String",
  "displayName": "String",
  "id": "String (identifier)",
  "isOrganizationDefault": true
}
```
