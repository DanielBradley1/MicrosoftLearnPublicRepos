<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-05-19 -->

# cloudPcConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the Cloud PC specification, including image and operating system locale settings for provisioning.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| imageDisplayName | String | The display name of the image. Read-only. |
| imageId | String | The unique identifier of the operating system image used for provisioning new Cloud PCs. The format for a gallery type image is: `{publisherName_offerName_skuName}`. |
| imageType | cloudPcProvisioningPolicyImageType | The type of operating system image \(custom or gallery\) used for provisioning on Cloud PCs. The possible values are: `gallery`, `custom`, `unknownFutureValue`. The default value is `gallery`. |
| osLocale | String | The operating system locale for the Cloud PC. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcConfiguration",
  "imageDisplayName": "String",
  "imageId": "String",
  "imageType": "String",
  "osLocale": "String"
}
```
