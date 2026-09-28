<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/devicedetail?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# deviceDetail resource type

Namespace: microsoft.graph

Indicates details of the device used in a sign-in activity. Includes information like device browser and OS info and if the device is Microsoft Entra ID-managed. This object is configured in the **deviceDetail** property of [signIn](https://learn.microsoft.com/en-us/graph/api/resources/signin?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| browser | String | Indicates the browser information of the used in the sign-in. Populated for devices registered in Microsoft Entra. |
| deviceId | String | Refers to the unique ID of the device used in the sign-in. Populated for devices registered in Microsoft Entra. |
| displayName | String | Refers to the name of the device used in the sign-in. Populated for devices registered in Microsoft Entra. |
| isCompliant | Boolean | Indicates whether the device is compliant or not. |
| isManaged | Boolean | Indicates if the device is managed or not. |
| operatingSystem | String | Indicates the OS name and version used in the sign-in. |
| trustType | String | Indicates information on whether the device used in the sign-in is workplace-joined, Microsoft Entra-joined, domain-joined. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "browser": "String",
  "deviceId": "String",
  "displayName": "String",
  "isCompliant": true,
  "isManaged": true,
  "operatingSystem": "String",
  "trustType": "String"
}
```
