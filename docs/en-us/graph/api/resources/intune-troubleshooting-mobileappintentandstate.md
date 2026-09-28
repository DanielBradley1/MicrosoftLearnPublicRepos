<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-mobileappintentandstate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# mobileAppIntentAndState resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

MobileApp Intent and Install State for a given device.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List mobileAppIntentAndStates](https://learn.microsoft.com/en-us/graph/api/intune-troubleshooting-mobileappintentandstate-list?view=graph-rest-beta) | [mobileAppIntentAndState](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-mobileappintentandstate?view=graph-rest-beta) collection | List properties and relationships of the [mobileAppIntentAndState](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-mobileappintentandstate?view=graph-rest-beta) objects. |
| [Get mobileAppIntentAndState](https://learn.microsoft.com/en-us/graph/api/intune-troubleshooting-mobileappintentandstate-get?view=graph-rest-beta) | [mobileAppIntentAndState](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-mobileappintentandstate?view=graph-rest-beta) | Read properties and relationships of the [mobileAppIntentAndState](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-mobileappintentandstate?view=graph-rest-beta) object. |
| [Create mobileAppIntentAndState](https://learn.microsoft.com/en-us/graph/api/intune-troubleshooting-mobileappintentandstate-create?view=graph-rest-beta) | [mobileAppIntentAndState](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-mobileappintentandstate?view=graph-rest-beta) | Create a new [mobileAppIntentAndState](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-mobileappintentandstate?view=graph-rest-beta) object. |
| [Delete mobileAppIntentAndState](https://learn.microsoft.com/en-us/graph/api/intune-troubleshooting-mobileappintentandstate-delete?view=graph-rest-beta) | None | Deletes a [mobileAppIntentAndState](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-mobileappintentandstate?view=graph-rest-beta). |
| [Update mobileAppIntentAndState](https://learn.microsoft.com/en-us/graph/api/intune-troubleshooting-mobileappintentandstate-update?view=graph-rest-beta) | [mobileAppIntentAndState](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-mobileappintentandstate?view=graph-rest-beta) | Update the properties of a [mobileAppIntentAndState](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-mobileappintentandstate?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | UUID for the object |
| managedDeviceIdentifier | String | Device identifier created or collected by Intune. |
| userId | String | Identifier for the user that tried to enroll the device. |
| mobileAppList | [mobileAppIntentAndStateDetail](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-mobileappintentandstatedetail?view=graph-rest-beta) collection | The list of payload intents and states for the tenant. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.mobileAppIntentAndState",
  "id": "String (identifier)",
  "managedDeviceIdentifier": "String",
  "userId": "String",
  "mobileAppList": [
    {
      "@odata.type": "microsoft.graph.mobileAppIntentAndStateDetail",
      "applicationId": "String",
      "displayName": "String",
      "mobileAppIntent": "String",
      "displayVersion": "String",
      "installState": "String",
      "supportedDeviceTypes": [
        {
          "@odata.type": "microsoft.graph.mobileAppSupportedDeviceType",
          "type": "String",
          "minimumOperatingSystemVersion": "String",
          "maximumOperatingSystemVersion": "String"
        }
      ]
    }
  ]
}
```
