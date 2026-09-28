<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatemanagementenrollment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-23 -->

# updateManagementEnrollment resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents per-category enrollment information for Windows Updates across supported update categories.

Inherits from [updatableAssetEnrollment](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatableassetenrollment?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| driver | [microsoft.graph.windowsUpdates.updateCategoryEnrollmentInformation](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatecategoryenrollmentinformation?view=graph-rest-beta) | Information about the enrollment state of the device in driver update management. |
| feature | [microsoft.graph.windowsUpdates.updateCategoryEnrollmentInformation](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatecategoryenrollmentinformation?view=graph-rest-beta) | Information about the enrollment state of the device in feature update management. |
| quality | [microsoft.graph.windowsUpdates.updateCategoryEnrollmentInformation](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatecategoryenrollmentinformation?view=graph-rest-beta) | Information about the enrollment state of the device in quality update management. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.updateManagementEnrollment",
  "driver": {
    "@odata.type": "microsoft.graph.windowsUpdates.updateCategoryEnrollmentInformation"
  },
  "feature": {
    "@odata.type": "microsoft.graph.windowsUpdates.updateCategoryEnrollmentInformation"
  },
  "quality": {
    "@odata.type": "microsoft.graph.windowsUpdates.updateCategoryEnrollmentInformation"
  }
}
```
