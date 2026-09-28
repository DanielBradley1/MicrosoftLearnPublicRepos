<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/qrcodepinauthenticationmethodconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-02-13 -->

# qrCodePinAuthenticationMethodConfiguration resource type

Namespace: microsoft.graph

Represents the policy configuration for the QR code PIN authentication method in the tenant. Authentication method policies define configuration settings and users or groups that are enabled to use the authentication method. This policy allows administrators to configure the standard QR code lifetime and PIN length requirements.

Inherits from [authenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodconfiguration?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/qrcodepinauthenticationmethodconfiguration-get?view=graph-rest-1.0) | [qrCodePinAuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/qrcodepinauthenticationmethodconfiguration?view=graph-rest-1.0) | Read the properties and relationships of a QR code PIN authentication method policy. |
| [Update](https://learn.microsoft.com/en-us/graph/api/qrcodepinauthenticationmethodconfiguration-update?view=graph-rest-1.0) | [qrCodePinAuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/qrcodepinauthenticationmethodconfiguration?view=graph-rest-1.0) | Update the properties of a QR code PIN authentication method policy. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/qrcodepinauthenticationmethodconfiguration-delete?view=graph-rest-1.0) | None | Delete a QR code PIN authentication method policy and revert to the default configuration. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| excludeTargets | [excludeTarget](https://learn.microsoft.com/en-us/graph/api/resources/excludetarget?view=graph-rest-1.0) collection | Groups of users that are excluded from the policy. Inherited from [authenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodconfiguration?view=graph-rest-1.0). |
| id | String | The authentication method policy identifier. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). Read-only. |
| pinLength | Int32 | The required length of the PIN. The minimum length is 8 digits \(as per NIST standards\), and the maximum is 20 digits. |
| standardQRCodeLifetimeInDays | Int32 | The lifetime of standard QR codes in days. The default is 365 days and the maximum is 395 days \(13 months\). The minimum is 1 day. |
| state | authenticationMethodState | The state of the policy. Inherited from [authenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodconfiguration?view=graph-rest-1.0). The possible values are: `enabled`, `disabled`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| includeTargets | [authenticationMethodTarget](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodtarget?view=graph-rest-1.0) collection | Groups of users that are included and enabled in the policy. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.qrCodePinAuthenticationMethodConfiguration",
  "id": "String (identifier)",
  "excludeTargets": [{"@odata.type": "microsoft.graph.excludeTarget"}],
  "pinLength": "Integer",
  "standardQRCodeLifetimeInDays": "Integer",
  "state": "String"
}
```

## Related content

- [qrCodePinAuthenticationMethod resource type](https://learn.microsoft.com/en-us/graph/api/resources/qrcodepinauthenticationmethod?view=graph-rest-1.0)
- [authenticationMethodConfiguration resource type](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodconfiguration?view=graph-rest-1.0)
