<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementcomplexsettingdefinition?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementComplexSettingDefinition resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Entity representing the defintion for a complex setting

Inherits from [deviceManagementSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettingdefinition?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceManagementComplexSettingDefinitions](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementcomplexsettingdefinition-list?view=graph-rest-beta) | [deviceManagementComplexSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementcomplexsettingdefinition?view=graph-rest-beta) collection | List properties and relationships of the [deviceManagementComplexSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementcomplexsettingdefinition?view=graph-rest-beta) objects. |
| [Get deviceManagementComplexSettingDefinition](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementcomplexsettingdefinition-get?view=graph-rest-beta) | [deviceManagementComplexSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementcomplexsettingdefinition?view=graph-rest-beta) | Read properties and relationships of the [deviceManagementComplexSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementcomplexsettingdefinition?view=graph-rest-beta) object. |
| [Create deviceManagementComplexSettingDefinition](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementcomplexsettingdefinition-create?view=graph-rest-beta) | [deviceManagementComplexSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementcomplexsettingdefinition?view=graph-rest-beta) | Create a new [deviceManagementComplexSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementcomplexsettingdefinition?view=graph-rest-beta) object. |
| [Delete deviceManagementComplexSettingDefinition](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementcomplexsettingdefinition-delete?view=graph-rest-beta) | None | Deletes a [deviceManagementComplexSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementcomplexsettingdefinition?view=graph-rest-beta). |
| [Update deviceManagementComplexSettingDefinition](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementcomplexsettingdefinition-update?view=graph-rest-beta) | [deviceManagementComplexSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementcomplexsettingdefinition?view=graph-rest-beta) | Update the properties of a [deviceManagementComplexSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementcomplexsettingdefinition?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The ID of the setting definition Inherited from [deviceManagementSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettingdefinition?view=graph-rest-beta) |
| valueType | [deviceManangementIntentValueType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanangementintentvaluetype?view=graph-rest-beta) | The data type of the value Inherited from [deviceManagementSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettingdefinition?view=graph-rest-beta). Possible values are: `integer`, `boolean`, `string`, `complex`, `collection`, `abstractComplex`. |
| displayName | String | The setting's display name Inherited from [deviceManagementSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettingdefinition?view=graph-rest-beta) |
| isTopLevel | Boolean | If the setting is top level, it can be configured without the need to be wrapped in a collection or complex setting Inherited from [deviceManagementSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettingdefinition?view=graph-rest-beta) |
| description | String | The setting's description Inherited from [deviceManagementSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettingdefinition?view=graph-rest-beta) |
| placeholderText | String | Placeholder text as an example of valid input Inherited from [deviceManagementSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettingdefinition?view=graph-rest-beta) |
| documentationUrl | String | Url to setting documentation Inherited from [deviceManagementSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettingdefinition?view=graph-rest-beta) |
| headerTitle | String | title of the setting header represents a category/section of a setting/settings Inherited from [deviceManagementSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettingdefinition?view=graph-rest-beta) |
| headerSubtitle | String | subtitle of the setting header for more details about the category/section Inherited from [deviceManagementSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettingdefinition?view=graph-rest-beta) |
| keywords | String collection | Keywords associated with the setting Inherited from [deviceManagementSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettingdefinition?view=graph-rest-beta) |
| constraints | [deviceManagementConstraint](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementconstraint?view=graph-rest-beta) collection | Collection of constraints for the setting value Inherited from [deviceManagementSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettingdefinition?view=graph-rest-beta) |
| dependencies | [deviceManagementSettingDependency](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettingdependency?view=graph-rest-beta) collection | Collection of dependencies on other settings Inherited from [deviceManagementSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettingdefinition?view=graph-rest-beta) |
| propertyDefinitionIds | String collection | The definitions of each property of the complex setting |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementComplexSettingDefinition",
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
  ],
  "propertyDefinitionIds": [
    "String"
  ]
}
```
