<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-cryptographysuite?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# cryptographySuite resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

VPN Security Association Parameters

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| encryptionMethod | [vpnEncryptionAlgorithmType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-vpnencryptionalgorithmtype?view=graph-rest-beta) | Encryption Method. Possible values are: `aes256`, `des`, `tripleDes`, `aes128`, `aes128Gcm`, `aes256Gcm`, `aes192`, `aes192Gcm`, `chaCha20Poly1305`. |
| integrityCheckMethod | [vpnIntegrityAlgorithmType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-vpnintegrityalgorithmtype?view=graph-rest-beta) | Integrity Check Method. Possible values are: `sha2_256`, `sha1_96`, `sha1_160`, `sha2_384`, `sha2_512`, `md5`. |
| dhGroup | [diffieHellmanGroup](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-diffiehellmangroup?view=graph-rest-beta) | Diffie Hellman Group. Possible values are: `group1`, `group2`, `group14`, `ecp256`, `ecp384`, `group24`. |
| cipherTransformConstants | [vpnEncryptionAlgorithmType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-vpnencryptionalgorithmtype?view=graph-rest-beta) | Cipher Transform Constants. Possible values are: `aes256`, `des`, `tripleDes`, `aes128`, `aes128Gcm`, `aes256Gcm`, `aes192`, `aes192Gcm`, `chaCha20Poly1305`. |
| authenticationTransformConstants | [authenticationTransformConstant](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-authenticationtransformconstant?view=graph-rest-beta) | Authentication Transform Constants. Possible values are: `md5_96`, `sha1_96`, `sha_256_128`, `aes128Gcm`, `aes192Gcm`, `aes256Gcm`. |
| pfsGroup | [perfectForwardSecrecyGroup](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-perfectforwardsecrecygroup?view=graph-rest-beta) | Perfect Forward Secrecy Group. Possible values are: `pfs1`, `pfs2`, `pfs2048`, `ecp256`, `ecp384`, `pfsMM`, `pfs24`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.cryptographySuite",
  "encryptionMethod": "String",
  "integrityCheckMethod": "String",
  "dhGroup": "String",
  "cipherTransformConstants": "String",
  "authenticationTransformConstants": "String",
  "pfsGroup": "String"
}
```
