<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettingdefinition?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementSettingDefinition resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Entity representing the defintion for a given setting

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceManagementSettingDefinitions](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementsettingdefinition-list?view=graph-rest-beta) | [deviceManagementSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettingdefinition?view=graph-rest-beta) collection | List properties and relationships of the [deviceManagementSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettingdefinition?view=graph-rest-beta) objects. |
| [Get deviceManagementSettingDefinition](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementsettingdefinition-get?view=graph-rest-beta) | [deviceManagementSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettingdefinition?view=graph-rest-beta) | Read properties and relationships of the [deviceManagementSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettingdefinition?view=graph-rest-beta) object. |
| [Create deviceManagementSettingDefinition](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementsettingdefinition-create?view=graph-rest-beta) | [deviceManagementSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettingdefinition?view=graph-rest-beta) | Create a new [deviceManagementSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettingdefinition?view=graph-rest-beta) object. |
| [Delete deviceManagementSettingDefinition](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementsettingdefinition-delete?view=graph-rest-beta) | None | Deletes a [deviceManagementSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettingdefinition?view=graph-rest-beta). |
| [Update deviceManagementSettingDefinition](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementsettingdefinition-update?view=graph-rest-beta) | [deviceManagementSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettingdefinition?view=graph-rest-beta) | Update the properties of a [deviceManagementSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettingdefinition?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The ID of the setting definition |
| valueType | [deviceManangementIntentValueType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanangementintentvaluetype?view=graph-rest-beta) | The data type of the value. Possible values are: `integer`, `boolean`, `string`, `complex`, `collection`, `abstractComplex`. |
| displayName | String | The setting's display name |
| isTopLevel | Boolean | If the setting is top level, it can be configured without the need to be wrapped in a collection or complex setting |
| description | String | The setting's description |
| placeholderText | String | Placeholder text as an example of valid input |
| documentationUrl | String | Url to setting documentation |
| headerTitle | String | title of the setting header represents a category/section of a setting/settings |
| headerSubtitle | String | subtitle of the setting header for more details about the category/section |
| keywords | String collection | Keywords associated with the setting |
| constraints | [deviceManagementConstraint](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementconstraint?view=graph-rest-beta) collection | Collection of constraints for the setting value |
| dependencies | [deviceManagementSettingDependency](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettingdependency?view=graph-rest-beta) collection | Collection of dependencies on other settings |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementSettingDefinition",
  "id": "String (identifier)",
  "valueType": "String",
  "displayName": "String",
  "isTopLevel": true,
  "description": "String",
  "placeholderText": "String",
  "documentationUrl": "String",
  "headerTitle": "String",
  "headerSubtitle": "String",
  "keywords": [
    "String"
  ],
  "constraints": [
    {
      "@odata.type": "microsoft.graph.deviceManagementSettingAppConstraint",
      "supportedTypes": [
        "String"
      ]
    }
  ],
  "dependencies": [
    {
      "@odata.type": "microsoft.graph.deviceManagementSettingDependency",
      "definitionId": "String",
      "constraints": [
        {
          "@odata.type": "microsoft.graph.deviceManagementSettingAppConstraint",
          "supportedTypes": [
            "String"
          ]
        }
      ]
    }
  ]
}
```
