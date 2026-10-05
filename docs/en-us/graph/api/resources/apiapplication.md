<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/apiapplication?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-11-09 -->

# apiApplication resource type

Namespace: microsoft.graph

Specifies settings for an [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0) that implements a web API.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| acceptMappedClaims | Boolean | When `true`, allows an application to use claims mapping without specifying a custom signing key. |
| knownClientApplications | Guid collection | Used for bundling consent if you have a solution that contains two parts: a client app and a custom web API app. If you set the appID of the client app to this value, the user only consents once to the client app. Microsoft Entra ID knows that consenting to the client means implicitly consenting to the web API and automatically provisions service principals for both APIs at the same time. Both the client and the web API app must be registered in the same tenant. |
| oauth2PermissionScopes | [permissionScope](https://learn.microsoft.com/en-us/graph/api/resources/permissionscope?view=graph-rest-1.0) collection | The definition of the delegated permissions exposed by the web API represented by this application registration. These delegated permissions may be requested by a client application, and may be granted by users or administrators during consent. Delegated permissions are sometimes referred to as OAuth 2.0 scopes. |
| preAuthorizedApplications | [preAuthorizedApplication](https://learn.microsoft.com/en-us/graph/api/resources/preauthorizedapplication?view=graph-rest-1.0) collection | Lists the client applications that are preauthorized with the specified delegated permissions to access this application's APIs. Users aren't required to consent to any preauthorized application \(for the permissions specified\). However, any other permissions not listed in preAuthorizedApplications \(requested through incremental consent for example\) will require user consent. |
| requestedAccessTokenVersion | Int32 | Specifies the access token version expected by this resource. This changes the version and format of the JWT produced independent of the endpoint or client used to request the access token.  <br>  <br>The endpoint used, v1.0 or v2.0, is chosen by the client and only impacts the version of id\_tokens. Resources need to explicitly configure **requestedAccessTokenVersion** to indicate the supported access token format.  <br>  <br>Possible values for **requestedAccessTokenVersion** are `1`, `2`, or `null`. If the value is `null`, this defaults to `1`, which corresponds to the v1.0 endpoint.  <br>  <br>If **signInAudience** on the application is configured as `AzureADandPersonalMicrosoftAccount` or `PersonalMicrosoftAccount`, the value for this property must be `2`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "acceptMappedClaims": true,
  "knownClientApplications": ["Guid"],
  "oauth2PermissionScopes": [{"@odata.type": "microsoft.graph.permissionScope"}],
  "preAuthorizedApplications": [{"@odata.type": "microsoft.graph.preAuthorizedApplication"}],
  "requestedAccessTokenVersion": 2
}
```
