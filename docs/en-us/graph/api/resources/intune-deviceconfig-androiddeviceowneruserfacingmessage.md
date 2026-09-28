<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androiddeviceowneruserfacingmessage?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# androidDeviceOwnerUserFacingMessage resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Represents a user-facing message with locale information as well as a default message to be used if the user's locale doesn't match with any of the localized messages

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| localizedMessages | [keyValuePair](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-keyvaluepair?view=graph-rest-beta) collection | The list of <locale, message> pairs. This collection can contain a maximum of 500 elements. |
| defaultMessage | String | The default message displayed if the user's locale doesn't match with any of the localized messages |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.androidDeviceOwnerUserFacingMessage",
  "localizedMessages": [
    {
      "@odata.type": "microsoft.graph.keyValuePair",
      "name": "String",
      "value": "String"
    }
  ],
  "defaultMessage": "String"
}
```
