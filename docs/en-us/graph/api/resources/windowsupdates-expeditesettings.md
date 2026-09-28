<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-expeditesettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# expediteSettings resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents settings for expediting the deployment of content.

The [catalog content](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-qualityupdatecatalogentry?view=graph-rest-beta) has the property **isExpeditable** set to `true` if it can be expedited. If an attempt is made to create a deployment tagged with **isExpedited** set to `true` but the content has **isExpeditable** set to `false`, then the operation might return a `400 Bad Request` response code. For more information, see [Deploy an expedited quality update using Windows Autopatch](https://learn.microsoft.com/en-us/graph/docs/concepts/windowsupdates-deploy-expedited-update.md).

An expedite readiness test is an expedited deployment that delivers no content to the device. The purpose of designating an expedited deployment as a readiness test is to ensure that the device meets the prerequisites for a successful expedited quality update deployment. An attempt that is made to create a deployment with **isExpedited** set to `false` and **isReadinessTest** set to `true` returns a `400 Bad Request` response code.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isExpedited | Boolean | `True` indicates that the deployment of the content is expedited. |
| isReadinessTest | Boolean | `True` indicates that the deployment is an expedite readiness test. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.expediteSettings",
  "isExpedited": "Boolean", 
  "isReadinessTest": "Boolean"
}
```
