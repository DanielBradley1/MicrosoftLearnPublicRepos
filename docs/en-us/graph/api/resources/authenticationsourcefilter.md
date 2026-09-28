<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/authenticationsourcefilter?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# authenticationSourceFilter resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Filter based on the source of the authentication that is used to determine whether the listener is evaluated.

The **includeApplications** property can be used to enable self-service sign up on an application in Microsoft Entra ID. Learn more by reading our documentation for [enabling applications in a self-service sign up user flow](https://learn.microsoft.com/en-us/azure/active-directory/external-identities/self-service-sign-up-user-flow#add-applications-to-the-self-service-sign-up-user-flow).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| includeApplications | String collection | Applications to include for evaluation of the [authenticationListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationlistener?view=graph-rest-beta). These applications trigger the associated action when used as the client application in the authentication flow. The application identifer is the application's client id. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.authenticationSourceFilter",
  "includeApplications": [
    "String"
  ]
}
```
