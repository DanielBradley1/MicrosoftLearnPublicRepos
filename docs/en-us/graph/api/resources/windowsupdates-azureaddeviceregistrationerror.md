<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-azureaddeviceregistrationerror?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# azureADDeviceRegistrationError resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

An error in the registration process of an [Microsoft Entra device](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-azureaddevice?view=graph-rest-beta) that prevents Windows Autopatch from enrolling the device in update management or deploying content to the device.

Inherits from [updatableAssetError](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatableasseterror?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| reason | microsoft.graph.windowsUpdates.azureADDeviceRegistrationErrorReason | The reason why the registration encountered an error. The possible values are: `invalidGlobalDeviceId`, `invalidAzureADDeviceId`, `missingTrustType`, `invalidAzureADJoin`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.azureADDeviceRegistrationError",
  "reason": "String"
}
```
