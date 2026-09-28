<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/registrationenforcement?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# registrationEnforcement resource type

Namespace: microsoft.graph

Enforce registration at sign-in time. This can currently only be used to remind users to set up targeted authentication methods \(for example, Microsoft Authenticator\) using the `authenticationMethodsRegistrationCampaign`.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authenticationMethodsRegistrationCampaign | [authenticationMethodsRegistrationCampaign](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodsregistrationcampaign?view=graph-rest-1.0) | Run campaigns to remind users to set up targeted authentication methods. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.registrationEnforcement",
  "authenticationMethodsRegistrationCampaign": {
    "@odata.type": "microsoft.graph.authenticationMethodsRegistrationCampaign"
  }
}
```
