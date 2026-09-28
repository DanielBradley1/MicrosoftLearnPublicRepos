<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/appcredentialsigninactivity?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-31 -->

# appCredentialSignInActivity resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an application credential activity in a given tenant. This resource contains information about the last usage time of an application credential.

For more information about this report, see [Usage and insights report: Microsoft Entra application activity \(preview\)](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-usage-insights-report?tabs=microsoft-entra-admin-center#microsoft-entra-application-activity-preview)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/reportroot-list-appcredentialsigninactivities?view=graph-rest-beta) | [appCredentialSignInActivity](https://learn.microsoft.com/en-us/graph/api/resources/appcredentialsigninactivity?view=graph-rest-beta) collection | Get a list of [appCredentialSignInActivity](https://learn.microsoft.com/en-us/graph/api/resources/appcredentialsigninactivity?view=graph-rest-beta) objects that contains recent activity of application credentials. |
| [Get](https://learn.microsoft.com/en-us/graph/api/appcredentialsigninactivity-get?view=graph-rest-beta) | [appCredentialSignInActivity](https://learn.microsoft.com/en-us/graph/api/resources/appcredentialsigninactivity?view=graph-rest-beta) | Get an [appCredentialSignInActivity](https://learn.microsoft.com/en-us/graph/api/resources/appcredentialsigninactivity?view=graph-rest-beta) object that contains recent activity of an application credential. |

## Properties

| Property | Type | Description |
| --- | --- | --- |
| appId | String | The globally unique **appId** \(also called *client ID* on the Microsoft Entra admin center\) of the credentialed application. |
| appObjectId | String | The ID of the credential application instance. |
| createdDateTime | DateTimeOffset | The date and time when the credential was created. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| credentialOrigin | applicationKeyOrigin | The type the key credential originated from. The possible values are: `application`, `servicePrincipal`, `unknownFutureValue`. |
| expirationDateTime | DateTimeOffset | The date and time when the credential is set to expire. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| id | String | The unique identifier of the **appCredentialSignInActivity** instance in the response. |
| keyId | String | The key ID of the credential. |
| keyType | applicationKeyType | Specifies the key type. The possible values are: `clientSecret`, `certificate`, `unknownFutureValue`. |
| keyUsage | applicationKeyUsage | Specifies what the key was used for. The possible values are: `sign`, `verify`, `unknownFutureValue`. |
| resourceId | String | The ID of the accessed resource. |
| servicePrincipalObjectId | String | The ID of the service principal. |
| signInActivity | [signInActivity](https://learn.microsoft.com/en-us/graph/api/resources/signinactivity?view=graph-rest-beta) | The sign-in activity of the credential across all flows. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.appCredentialSignInActivity",
  "appId": "String",
  "appObjectId": "String",
  "createdDateTime": "String (timestamp)",
  "credentialOrigin": "String",
  "expirationDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "keyId": "String",
  "keyType": "String",
  "keyUsage": "String",
  "resourceId": "String",
  "servicePrincipalObjectId": "String",
  "signInActivity": {"@odata.type": "microsoft.graph.signInActivity"}
}
```
