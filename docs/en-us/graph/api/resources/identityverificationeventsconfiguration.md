<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identityverificationeventsconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-30 -->

# identityVerificationEventsConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the tenant-level configuration that controls the collection and exposure of identity verification events and credential provenance information for Verified ID verification. This configuration applies to the entire tenant and isn't scoped to individual Verified ID profiles. It's contained by the [verifiableCredentialsAuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/verifiablecredentialsauthenticationmethodconfiguration?view=graph-rest-beta) resource and has no operations of its own.

When this configuration is disabled, no new identity verification events or credential provenance information are collected and retained events can't be accessed. Disabling the configuration doesn't delete retained data.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isEnabled | Boolean | Indicates whether identity verification events and credential provenance information are collected and exposed for Verified ID verification across the tenant. The default value is `false` when this property is omitted from the configuration object. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityVerificationEventsConfiguration",
  "isEnabled": "Boolean"
}
```
