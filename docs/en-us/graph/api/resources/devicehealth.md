<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/devicehealth?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-26 -->

# deviceHealth resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a device's health, including any errors.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| lastConnectionTime | DateTimeOffset | The last time the device was connected. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
    "lastConnectionTime": "String (timestamp)"
}
```
