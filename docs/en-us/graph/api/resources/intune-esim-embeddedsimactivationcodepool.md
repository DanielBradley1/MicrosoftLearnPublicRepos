<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-esim-embeddedsimactivationcodepool?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# embeddedSIMActivationCodePool resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

A pool represents a group of embedded SIM activation codes.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List embeddedSIMActivationCodePools](https://learn.microsoft.com/en-us/graph/api/intune-esim-embeddedsimactivationcodepool-list?view=graph-rest-beta) | [embeddedSIMActivationCodePool](https://learn.microsoft.com/en-us/graph/api/resources/intune-esim-embeddedsimactivationcodepool?view=graph-rest-beta) collection | List properties and relationships of the [embeddedSIMActivationCodePool](https://learn.microsoft.com/en-us/graph/api/resources/intune-esim-embeddedsimactivationcodepool?view=graph-rest-beta) objects. |
| [Get embeddedSIMActivationCodePool](https://learn.microsoft.com/en-us/graph/api/intune-esim-embeddedsimactivationcodepool-get?view=graph-rest-beta) | [embeddedSIMActivationCodePool](https://learn.microsoft.com/en-us/graph/api/resources/intune-esim-embeddedsimactivationcodepool?view=graph-rest-beta) | Read properties and relationships of the [embeddedSIMActivationCodePool](https://learn.microsoft.com/en-us/graph/api/resources/intune-esim-embeddedsimactivationcodepool?view=graph-rest-beta) object. |
| [Create embeddedSIMActivationCodePool](https://learn.microsoft.com/en-us/graph/api/intune-esim-embeddedsimactivationcodepool-create?view=graph-rest-beta) | [embeddedSIMActivationCodePool](https://learn.microsoft.com/en-us/graph/api/resources/intune-esim-embeddedsimactivationcodepool?view=graph-rest-beta) | Create a new [embeddedSIMActivationCodePool](https://learn.microsoft.com/en-us/graph/api/resources/intune-esim-embeddedsimactivationcodepool?view=graph-rest-beta) object. |
| [Delete embeddedSIMActivationCodePool](https://learn.microsoft.com/en-us/graph/api/intune-esim-embeddedsimactivationcodepool-delete?view=graph-rest-beta) | None | Deletes a [embeddedSIMActivationCodePool](https://learn.microsoft.com/en-us/graph/api/resources/intune-esim-embeddedsimactivationcodepool?view=graph-rest-beta). |
| [Update embeddedSIMActivationCodePool](https://learn.microsoft.com/en-us/graph/api/intune-esim-embeddedsimactivationcodepool-update?view=graph-rest-beta) | [embeddedSIMActivationCodePool](https://learn.microsoft.com/en-us/graph/api/resources/intune-esim-embeddedsimactivationcodepool?view=graph-rest-beta) | Update the properties of a [embeddedSIMActivationCodePool](https://learn.microsoft.com/en-us/graph/api/resources/intune-esim-embeddedsimactivationcodepool?view=graph-rest-beta) object. |
| [assign action](https://learn.microsoft.com/en-us/graph/api/intune-esim-embeddedsimactivationcodepool-assign?view=graph-rest-beta) | [embeddedSIMActivationCodePoolAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-esim-embeddedsimactivationcodepoolassignment?view=graph-rest-beta) collection |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for the embedded SIM activation code pool. System generated value assigned when created. |
| displayName | String | The admin defined name of the embedded SIM activation code pool. |
| createdDateTime | DateTimeOffset | The time the embedded SIM activation code pool was created. Generated service side. |
| modifiedDateTime | DateTimeOffset | The time the embedded SIM activation code pool was last modified. Updated service side. |
| activationCodes | [embeddedSIMActivationCode](https://learn.microsoft.com/en-us/graph/api/resources/intune-esim-embeddedsimactivationcode?view=graph-rest-beta) collection | The activation codes which belong to this pool. This navigation property is used to post activation codes to Intune but cannot be used to read activation codes from Intune. |
| activationCodeCount | Int32 | The total count of activation codes which belong to this pool. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| assignments | [embeddedSIMActivationCodePoolAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-esim-embeddedsimactivationcodepoolassignment?view=graph-rest-beta) collection | Navigational property to a list of targets to which this pool is assigned. |
| deviceStates | [embeddedSIMDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-esim-embeddedsimdevicestate?view=graph-rest-beta) collection | Navigational property to a list of device states for this pool. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.embeddedSIMActivationCodePool",
  "id": "String (identifier)",
  "displayName": "String",
  "createdDateTime": "String (timestamp)",
  "modifiedDateTime": "String (timestamp)",
  "activationCodes": [
    {
      "@odata.type": "microsoft.graph.embeddedSIMActivationCode",
      "integratedCircuitCardIdentifier": "String",
      "matchingIdentifier": "String",
      "smdpPlusServerAddress": "String"
    }
  ],
  "activationCodeCount": 1024
}
```
