<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/mutualtlsoauthconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-01-02 -->

# mutualTlsOauthConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a list of certificate authorities \(CAs\) that are permitted to issue certificates for a specific set of objects used for mTLS.

This object is typically created by a device authority on their own Microsoft Entra tenant. In some cases, the user might choose to create this object in their Microsoft Entra tenant.

Inherits from [trustedCertificateAuthorityBase](https://learn.microsoft.com/en-us/graph/api/resources/trustedcertificateauthoritybase?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/certificateauthoritypath-list-mutualtlsoauthconfigurations?view=graph-rest-beta) | [mutualTlsOauthConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/mutualtlsoauthconfiguration?view=graph-rest-beta) collection | Get a list of the available [mutualTlsOauthConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/mutualtlsoauthconfiguration?view=graph-rest-beta) resources. |
| [Create](https://learn.microsoft.com/en-us/graph/api/certificateauthoritypath-post-mutualtlsoauthconfigurations?view=graph-rest-beta) | [mutualTlsOauthConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/mutualtlsoauthconfiguration?view=graph-rest-beta) | Create a [mutualTlsOauthConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/mutualtlsoauthconfiguration?view=graph-rest-beta) resource that contains a specified certificate authority object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/mutualtlsoauthconfiguration-get?view=graph-rest-beta) | [mutualTlsOauthConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/mutualtlsoauthconfiguration?view=graph-rest-beta) | Get the properties and relationships of the specified [mutualTlsOauthConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/mutualtlsoauthconfiguration?view=graph-rest-beta) resource. |
| [Update](https://learn.microsoft.com/en-us/graph/api/mutualtlsoauthconfiguration-update?view=graph-rest-beta) | [mutualTlsOauthConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/mutualtlsoauthconfiguration?view=graph-rest-beta) | Update the specified [mutualTlsOauthConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/mutualtlsoauthconfiguration?view=graph-rest-beta) resource. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/mutualtlsoauthconfiguration-delete?view=graph-rest-beta) | None | Delete the specified [mutualTlsOauthConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/mutualtlsoauthconfiguration?view=graph-rest-beta) resource. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| certificateAuthorities | [certificateAuthority](https://learn.microsoft.com/en-us/graph/api/resources/certificateauthority?view=graph-rest-beta) collection | Multi-value property that represents a list of trusted certificate authorities. Inherited from [trustedCertificateAuthorityBase](https://learn.microsoft.com/en-us/graph/api/resources/trustedcertificateauthoritybase?view=graph-rest-beta). |
| deletedDateTime | DateTimeOffset | Date and time when this object was deleted. Always `null` when the object hasn't been deleted. Inherited from [trustedCertificateAuthorityBase](https://learn.microsoft.com/en-us/graph/api/resources/trustedcertificateauthoritybase?view=graph-rest-beta). |
| displayName | String | Friendly name. Supports `$filter` \(`eq`, `in`\). |
| id | String | The unique identifier for the **mutualTlsOauthConfiguration** object. Inherited from [trustedCertificateAuthorityBase](https://learn.microsoft.com/en-us/graph/api/resources/trustedcertificateauthoritybase?view=graph-rest-beta). Supports `$filter` \(`eq`, `in`\). |
| tlsClientAuthParameter | tlsClientRegistrationMetadata | Specifies the field in the certificate that contains the subject ID. The possible values are: `tls_client_auth_subject_dn`, `tls_client_auth_san_dns`, `tls_client_auth_san_uri`, `tls_client_auth_san_ip`, `tls_client_auth_san_email`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.mutualTlsOauthConfiguration",
  "certificateAuthorities": [{"@odata.type": "microsoft.graph.certificateAuthority"}],
  "deletedDateTime": "String (timestamp)",
  "displayName": "String",
  "id": "String (identifier)",
  "tlsClientAuthParameter": "String"
}
```
