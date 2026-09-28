<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-buildversiondetails?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# buildVersionDetails resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the build version details of a product revision that is associated with a quality update.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| buildNumber | Int32 | The build number of the product release. Read-only. |
| majorVersion | Int32 | The major version of the product release. Read-only. |
| minorVersion | Int32 | The minor version of the product release. Read-only. |
| updateBuildRevision | Int32 | The update build revision number of the product revision. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.buildVersionDetails",
  "buildNumber": "Int32",
  "majorVersion": "Int32",
  "minorVersion": "Int32",
  "updateBuildRevision": "Int32"
}
```
