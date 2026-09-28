<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/parentlabeldetails?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# parentLabelDetails resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the label details of an information protection parent label. **parentLabelDetails** provides information about a single information protection label. Can be returned by [evaluateRemoval](https://learn.microsoft.com/en-us/graph/api/informationprotectionlabel-evaluateremoval?view=graph-rest-beta), [evaluateApplication](https://learn.microsoft.com/en-us/graph/api/informationprotectionlabel-evaluateapplication?view=graph-rest-beta), and [extractLabel](https://learn.microsoft.com/en-us/graph/api/informationprotectionlabel-extractlabel?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| color | String | The color that the user interface should display for the label, if configured. |
| description | String | The admin-defined description for the label. |
| id | String | The label ID is a globally unique identifier \(GUID\). |
| isActive | Boolean | Indicates whether the label is active or not. Active labels should be hidden or disabled in user interfaces. |
| name | String | The plaintext name of the label. |
| sensitivity | Int32 | The sensitivity value of the label, where lower is less sensitive. |
| tooltip | String | The tooltip that should be displayed for the label in a user interface. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "color": "String",
  "description": "String",
  "id": "String",
  "isActive": true,
  "name": "String",
  "sensitivity": 1024,
  "tooltip": "String"
}
```
