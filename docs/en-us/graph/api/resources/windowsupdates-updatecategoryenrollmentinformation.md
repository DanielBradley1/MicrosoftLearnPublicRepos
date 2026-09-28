<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatecategoryenrollmentinformation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-23 -->

# updateCategoryEnrollmentInformation resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents information about the enrollment of a device into management by the service of a certain update category.

Note

For devices enrolled in feature update management, the `enrolledWithPolicy` state means that the device is enrolled in feature update management and is assigned to a policy. The `enrolled` state indicates that the device is enrolled in feature update management but isn't assigned to a policy, and it doesn't receive feature updates.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| enrollmentState | microsoft.graph.windowsUpdates.enrollmentState | Represents the last known enrollment state of the device. Possible values are: `notEnrolled`, `enrolled`, `enrolledWithPolicy`, `enrolling`, `unenrolling`, `unknownFutureValue`. Read-only. |
| lastModifiedDateTime | DateTimeOffset | The date and time when the **enrollmentState** was last modified. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2024, is `2024-01-01T00:00:00Z`. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.updateCategoryEnrollmentInformation",
  "enrollmentState": "String",
  "lastModifiedDateTime": "String (timestamp)"
}
```
