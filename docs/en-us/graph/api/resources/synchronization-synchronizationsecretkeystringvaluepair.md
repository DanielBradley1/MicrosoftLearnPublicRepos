<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationsecretkeystringvaluepair?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# synchronizationSecretKeyStringValuePair resource type

Namespace: microsoft.graph

Represents a single secret value. This object is configured in the **secrets** property of [synchronization](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronization?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| key | synchronizationSecret | The possible values are: `None`, `UserName`, `Password`, `SecretToken`, `AppKey`, `BaseAddress`, `ClientIdentifier`, `ClientSecret`, `SingleSignOnType`, `Sandbox`, `Url`, `Domain`, `ConsumerKey`, `ConsumerSecret`, `TokenKey`, `TokenExpiration`, `Oauth2AccessToken`, `Oauth2AccessTokenCreationTime`, `Oauth2RefreshToken`, `SyncAll`, `InstanceName`, `Oauth2ClientId`, `Oauth2ClientSecret`, `CompanyId`, `UpdateKeyOnSoftDelete`, `SynchronizationSchedule`, `SystemOfRecord`, `SandboxName`, `EnforceDomain`, `SyncNotificationSettings`, `SkipOutOfScopeDeletions`, `Oauth2AuthorizationCode`, `Oauth2RedirectUri`, `ApplicationTemplateIdentifier`, `Oauth2TokenExchangeUri`, `Oauth2AuthorizationUri`, `AuthenticationType`, `Server`, `PerformInboundEntitlementGrants`, `HardDeletesEnabled`, `SyncAgentCompatibilityKey`, `SyncAgentADContainer`, `ValidateDomain`, `TestReferences`, `ConnectionString`. |
| value | String | The value of the secret. |

### Supported key value pairs

| Key | Value |
| :--- | :--- |
| BaseAddress | The tenant URL / SCIM end point that you're trying to provision. |
| SecretToken | The token to authorize access to the application. This token is provided by the application developer. |
| SyncNotificationSettings | This property is used to determine if quarantine emails are sent. |
| SyncAll | Determines scope of sync between all users and groups or only ones that are assigned. When provisioning users into applications, the value is generally "True". |
| SkipOutOfScopeDeletions | Determines if accounts that go out of scope are or aren't disabled in the target. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "key": "String",
  "value": "String"
}
```
