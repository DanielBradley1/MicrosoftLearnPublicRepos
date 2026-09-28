<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/authenticationappdevicedetails?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# authenticationAppDeviceDetails resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Provides details about the app and device used during the Microsoft Entra authentication step. This object is configured in the **authenticationAppDeviceDetails** property of [signIn](https://learn.microsoft.com/en-us/graph/api/resources/signin?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| appVersion | String | The version of the client authentication app used during the authentication step. |
| clientApp | String | The name of the client authentication app used during the authentication step. |
| deviceId | String | ID of the device used during the authentication step. |
| operatingSystem | String | The operating system running on the device used for the authentication step. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.authenticationAppDeviceDetails",
  "deviceId": "String",
  "operatingSystem": "String",
  "clientApp": "String",
  "appVersion": "String"
}
```
