<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcdomainjoinkeyvaultpasswordconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-30 -->

# cloudPcDomainJoinKeyVaultPasswordConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a domain join configuration in which an Azure Key Vault secret contains the password.

Use this type for the **keyVaultIntentConfiguration** property of [cloudPcKeyVaultDomainJoinCredential](https://learn.microsoft.com/en-us/graph/api/resources/cloudpckeyvaultdomainjoincredential?view=graph-rest-beta). The **userIdentity** property identifies the Active Directory user associated with the password.

Inherits from [cloudPcDomainJoinKeyVaultIntentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcdomainjoinkeyvaultintentconfiguration?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| userIdentity | [cloudPcDomainJoinUserIdentity](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcdomainjoinuseridentity?view=graph-rest-beta) | The Active Directory user identity used to join devices to the domain. Set **@odata.type** to `#microsoft.graph.cloudPcDomainJoinPlainTextUserIdentity` to specify the user principal name. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcDomainJoinKeyVaultPasswordConfiguration",
  "userIdentity": { "@odata.type": "microsoft.graph.cloudPcDomainJoinUserIdentity" }
}
```
