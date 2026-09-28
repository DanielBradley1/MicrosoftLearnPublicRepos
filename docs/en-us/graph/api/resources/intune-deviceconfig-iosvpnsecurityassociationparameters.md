<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosvpnsecurityassociationparameters?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# iosVpnSecurityAssociationParameters resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

VPN Security Association Parameters

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| securityEncryptionAlgorithm | [vpnEncryptionAlgorithmType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-vpnencryptionalgorithmtype?view=graph-rest-beta) | Encryption algorithm. Possible values are: `aes256`, `des`, `tripleDes`, `aes128`, `aes128Gcm`, `aes256Gcm`, `aes192`, `aes192Gcm`, `chaCha20Poly1305`. |
| securityIntegrityAlgorithm | [vpnIntegrityAlgorithmType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-vpnintegrityalgorithmtype?view=graph-rest-beta) | Integrity algorithm. Possible values are: `sha2_256`, `sha1_96`, `sha1_160`, `sha2_384`, `sha2_512`, `md5`. |
| securityDiffieHellmanGroup | Int32 | Diffie-Hellman Group |
| lifetimeInMinutes | Int32 | Lifetime \(minutes\) |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.iosVpnSecurityAssociationParameters",
  "securityEncryptionAlgorithm": "String",
  "securityIntegrityAlgorithm": "String",
  "securityDiffieHellmanGroup": 1024,
  "lifetimeInMinutes": 1024
}
```
