<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionstoreapp?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windowsInformationProtectionStoreApp resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Store App for Windows information protection

Inherits from [windowsInformationProtectionApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionapp?view=graph-rest-1.0)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | App display name. Inherited from [windowsInformationProtectionApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionapp?view=graph-rest-1.0) |
| description | String | The app's description. Inherited from [windowsInformationProtectionApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionapp?view=graph-rest-1.0) |
| publisherName | String | The publisher name Inherited from [windowsInformationProtectionApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionapp?view=graph-rest-1.0) |
| productName | String | The product name. Inherited from [windowsInformationProtectionApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionapp?view=graph-rest-1.0) |
| denied | Boolean | If true, app is denied protection or exemption. Inherited from [windowsInformationProtectionApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionapp?view=graph-rest-1.0) |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsInformationProtectionStoreApp",
  "displayName": "String",
  "description": "String",
  "publisherName": "String",
  "productName": "String",
  "denied": true
}
```
