<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/drivesettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-19 -->

# driveSettings resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the settings associated with a [drive](https://learn.microsoft.com/en-us/graph/api/resources/drive?view=graph-rest-beta). Contains configuration values that apply to the drive and its contents. This property isn't returned by default and must be selected using the `$select` query parameter.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| itemDefaultSensitivityLabelId | String | The ID of the default sensitivity label for items in the drive. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "itemDefaultSensitivityLabelId": "String"
}
```
