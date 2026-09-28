<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/trustframeworkkeyset?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-20 -->

# trustFrameworkKeySet resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a trust framework keyset/policy key. The Identity Experience framework stores the secrets, which can be used in the policies. The secrets can be passwords, certificates, or other files. In the portal, these entities are shown as `Policy keys`. The Identity Experience framework uses the JSON Web Key \(JWK\) standard for the keysets. This entity follows the format specified in [RFC 7517 Section 5](https://tools.ietf.org/html/rfc7517#section-5).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/trustframework-list-keysets?view=graph-rest-beta) | [trustFrameworkKeySet](https://learn.microsoft.com/en-us/graph/api/resources/trustframeworkkeyset?view=graph-rest-beta) collection | Get a list of the [trustFrameworkKeySet](https://learn.microsoft.com/en-us/graph/api/resources/trustframeworkkeyset?view=graph-rest-beta) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/trustframework-post-keysets?view=graph-rest-beta) | [trustFrameworkKeySet](https://learn.microsoft.com/en-us/graph/api/resources/trustframeworkkeyset?view=graph-rest-beta) | Create a new [trustFrameworkKeySet](https://learn.microsoft.com/en-us/graph/api/resources/trustframeworkkeyset?view=graph-rest-beta) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/trustframeworkkeyset-get?view=graph-rest-beta) | [trustFrameworkKeySet](https://learn.microsoft.com/en-us/graph/api/resources/trustframeworkkeyset?view=graph-rest-beta) | Read the properties and relationships of a [trustFrameworkKeySet](https://learn.microsoft.com/en-us/graph/api/resources/trustframeworkkeyset?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/trustframeworkkeyset-update?view=graph-rest-beta) | [trustFrameworkKeySet](https://learn.microsoft.com/en-us/graph/api/resources/trustframeworkkeyset?view=graph-rest-beta) | Update the properties of a [trustFrameworkKeySet](https://learn.microsoft.com/en-us/graph/api/resources/trustframeworkkeyset?view=graph-rest-beta) object. |
| [Generate key](https://learn.microsoft.com/en-us/graph/api/trustframeworkkeyset-generatekey?view=graph-rest-beta) | [trustFrameworkKey](https://learn.microsoft.com/en-us/graph/api/resources/trustframeworkkey?view=graph-rest-beta) | Generate a key in keyset. |
| [Upload secret](https://learn.microsoft.com/en-us/graph/api/trustframeworkkeyset-uploadsecret?view=graph-rest-beta) | [trustFrameworkKey](https://learn.microsoft.com/en-us/graph/api/resources/trustframeworkkey?view=graph-rest-beta) | Upload a string based secret. |
| [Get active key](https://learn.microsoft.com/en-us/graph/api/trustframeworkkeyset-getactivekey?view=graph-rest-beta) | [trustFrameworkKey](https://learn.microsoft.com/en-us/graph/api/resources/trustframeworkkey?view=graph-rest-beta) | Get currently active key in the keyset. |
| [Upload X.509 certificate](https://learn.microsoft.com/en-us/graph/api/trustframeworkkeyset-uploadcertificate?view=graph-rest-beta) | [trustFrameworkKey](https://learn.microsoft.com/en-us/graph/api/resources/trustframeworkkey?view=graph-rest-beta) | Upload a X.509 certificate. |
| [Upload PKCS12 certificate](https://learn.microsoft.com/en-us/graph/api/trustframeworkkeyset-uploadpkcs12?view=graph-rest-beta) | [trustFrameworkKey](https://learn.microsoft.com/en-us/graph/api/resources/trustframeworkkey?view=graph-rest-beta) | Upload a PKCS12 format certificate. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier of the trustframework keyset Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| keys | [trustFrameworkKey](https://learn.microsoft.com/en-us/graph/api/resources/trustframeworkkey?view=graph-rest-beta) collection | A collection of the keys. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| keys\_v2 | [trustFrameworkKey\_v2](https://learn.microsoft.com/en-us/graph/api/resources/trustframeworkkey_v2?view=graph-rest-beta) collection | A collection of the keys. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.trustFrameworkKeySet",
  "id": "String (identifier)",
  "keys": [
    {
      "@odata.type": "microsoft.graph.trustFrameworkKey"
    }
  ]
}
```
