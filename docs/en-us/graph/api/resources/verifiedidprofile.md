<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/verifiedidprofile?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-04 -->

# verifiedIdProfile resource type

Namespace: microsoft.graph

Verified ID profiles defining set of properties and usage patterns.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/identityverifiedidroot-list-profiles?view=graph-rest-1.0) | [verifiedIdProfile](https://learn.microsoft.com/en-us/graph/api/resources/verifiedidprofile?view=graph-rest-1.0) collection | Get a list of the verifiedIdProfile objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/identityverifiedidroot-post-profiles?view=graph-rest-1.0) | [verifiedIdProfile](https://learn.microsoft.com/en-us/graph/api/resources/verifiedidprofile?view=graph-rest-1.0) | Create a new verifiedIdProfile object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/verifiedidprofile-get?view=graph-rest-1.0) | [verifiedIdProfile](https://learn.microsoft.com/en-us/graph/api/resources/verifiedidprofile?view=graph-rest-1.0) | Read the properties and relationships of [verifiedIdProfile](https://learn.microsoft.com/en-us/graph/api/resources/verifiedidprofile?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/verifiedidprofile-update?view=graph-rest-1.0) | [verifiedIdProfile](https://learn.microsoft.com/en-us/graph/api/resources/verifiedidprofile?view=graph-rest-1.0) | Update the properties of a verifiedIdProfile object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/identityverifiedidroot-delete-profiles?view=graph-rest-1.0) | None | Delete a verifiedIdProfile object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | Description for the verified ID profile. Required. |
| faceCheckConfiguration | [faceCheckConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/facecheckconfiguration?view=graph-rest-1.0) | Set of properties configuring Entra Verified ID Face Check behavior. Required. |
| id | String | Profile identifier. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| lastModifiedDateTime | DateTimeOffset | DateTime the profile was last modified. Optional. |
| name | String | Display name for the verified ID profile. Required. |
| priority | Int32 | Defines profile processing priority if multiple profiles are configured. Optional. |
| state | verifiedIdProfileState | Enablement state for the profile. The possible values are: `enabled`, `disabled`, `unknownFutureValue`. Required. |
| verifierDid | String | Decentralized Identifier \(DID\) string that represents the verifier in the verifiable credential exchange. Required. |
| verifiedIdProfileConfiguration | [verifiedIdProfileConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/verifiedidprofileconfiguration?view=graph-rest-1.0) | Set of properties expressing the accepted issuer, claims binding, and credential type. Required. |
| verifiedIdUsageConfigurations | [verifiedIdUsageConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/verifiedidusageconfiguration?view=graph-rest-1.0) collection | Collection defining the usage purpose for the profile. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.verifiedIdProfile",
  "id": "String (identifier)",
  "name": "String",
  "description": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "state": "String",
  "verifierDid": "String",
  "priority": "Integer",
  "verifiedIdProfileConfiguration": {
    "@odata.type": "microsoft.graph.verifiedIdProfileConfiguration"
  },
  "faceCheckConfiguration": {
    "@odata.type": "microsoft.graph.faceCheckConfiguration"
  },
  "verifiedIdUsageConfigurations": [
    {
      "@odata.type": "microsoft.graph.verifiedIdUsageConfiguration"
    }
  ]
}
```
