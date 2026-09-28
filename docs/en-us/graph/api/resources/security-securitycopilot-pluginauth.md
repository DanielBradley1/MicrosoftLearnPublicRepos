<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-securitycopilot-pluginauth?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-04 -->

# pluginAuth resource type

Namespace: microsoft.graph.security.securityCopilot

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

This describes the set of authorization types available for a Security Copilot [plugin](https://learn.microsoft.com/en-us/graph/api/resources/security-securitycopilot-plugin?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authType | microsoft.graph.security.securityCopilot.pluginAuthTypes | Plugin authorization types. The possible values are: `none`, `basic`, `aPIKey`, `oAuthAuthorizationCodeFlow`, `oAuthClientCredentialsFlow`, `aad`, `serviceHttp`, `aadDelegated`, `oAuthPasswordGrantFlow`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.securityCopilot.pluginAuth",
  "authType": "String"
}
```
