<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatableasseterror?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# updatableAssetError resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

An abstract type that represents an error which prevents Windows Autopatch from enrolling an [azureADDevice](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-azureaddevice?view=graph-rest-beta) in update management, or deploying content to the device.

All updatable asset errors are of the derived type, [azureADDeviceRegistrationError](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-azureaddeviceregistrationerror?view=graph-rest-beta).

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.updatableAssetError"
}
```
