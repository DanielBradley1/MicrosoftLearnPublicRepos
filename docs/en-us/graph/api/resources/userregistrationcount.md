<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/userregistrationcount?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# userRegistrationCount resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the registration count and status for users in your tenant.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| registrationCount | Int64 | Provides the registration count for your tenant. |
| registrationStatus | String | Represents the status of user registration. The possible values are: `registered`, `enabled`, `capable`, and `mfaRegistered`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{ 
  "registrationStatus":"String", 
  "registrationCount": 23423
}
```
