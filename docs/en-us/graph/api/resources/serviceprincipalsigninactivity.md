<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipalsigninactivity?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-31 -->

# servicePrincipalSignInActivity resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the service principal sign-in activity usage in a given tenant. This resource contains information about the last usage time of a service principal.

For more information about this report, see [Usage and insights report: Service principal sign-in activity \(preview\)](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-usage-insights-report?tabs=microsoft-entra-admin-center#service-principal-sign-in-activity-preview)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/reportroot-list-serviceprincipalsigninactivities?view=graph-rest-beta) | [servicePrincipalSignInActivity](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipalsigninactivity?view=graph-rest-beta) collection | Get a list of [servicePrincipalSignInActivity](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipalsigninactivity?view=graph-rest-beta) objects that contains sign-in activity information for service principals in a Microsoft Entra tenant. |
| [Get](https://learn.microsoft.com/en-us/graph/api/serviceprincipalsigninactivity-get?view=graph-rest-beta) | [servicePrincipalSignInActivity](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipalsigninactivity?view=graph-rest-beta) | Get a [servicePrincipalSignInActivity](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipalsigninactivity?view=graph-rest-beta) object that contains sign-in activity information for a service principal in a Microsoft Entra tenant. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| appId | String | The globally unique **appId** \(also called *client ID* on the Microsoft Entra admin center\) of the credentialed resource application. |
| applicationAuthenticationClientSignInActivity | [signInActivity](https://learn.microsoft.com/en-us/graph/api/resources/signinactivity?view=graph-rest-beta) | The sign-in activity of the application in a app-only authentication flow \(app-to-app tokens\) where the application acts like a client. |
| applicationAuthenticationResourceSignInActivity | [signInActivity](https://learn.microsoft.com/en-us/graph/api/resources/signinactivity?view=graph-rest-beta) | The sign-in activity of the application in a app-only authentication flow \(app-to-app tokens\) where the application acts like a resource. |
| delegatedClientSignInActivity | [signInActivity](https://learn.microsoft.com/en-us/graph/api/resources/signinactivity?view=graph-rest-beta) | The sign-in activity of the application in a delegated flow \(user sign-in\) where the application acts like a client. |
| delegatedResourceSignInActivity | [signInActivity](https://learn.microsoft.com/en-us/graph/api/resources/signinactivity?view=graph-rest-beta) | The sign-in activity of the application in a delegated flow \(user sign-in\) where the application acts like a resource. |
| id | String | The unique ID for each service principal sign-in event. |
| lastSignInActivity | [signInActivity](https://learn.microsoft.com/en-us/graph/api/resources/signinactivity?view=graph-rest-beta) | The most recent sign-in activity of the application across delegated or app-only flows where the application is used either as a client or resource. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.servicePrincipalSignInActivity",
  "appId": "String",
  "applicationAuthenticationClientSignInActivity": {"@odata.type": "microsoft.graph.signInActivity"},
  "applicationAuthenticationResourceSignInActivity": {"@odata.type": "microsoft.graph.signInActivity"},
  "delegatedClientSignInActivity": {"@odata.type": "microsoft.graph.signInActivity"},
  "delegatedResourceSignInActivity": {"@odata.type": "microsoft.graph.signInActivity"},
  "id": "String (identifier)",
  "lastSignInActivity": {"@odata.type": "microsoft.graph.signInActivity"}
}
```
