<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-element-relationship-set?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# root.elementRelationshipSet object

Describes relationships among individual app capabilities, including `staticTabs`, `configurableTabs`, `composeExtensions`, and `bots`. It's used to specify runtime dependencies to ensure that the app only launches in applicable Microsoft 365 hosts, such as Teams, Outlook, and the Microsoft 365 \(Office\) app. For more information, see [how to specify runtime requirements in your app manifest](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/specify-runtime-requirements).

Properties that reference this object type:

- [root.elementRelationshipSet](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#elementRelationshipSet-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "oneWayDependencies": [
    {
      "element": {
        elementReference object
      },
      "dependsOn": [
        {
          elementReference object
        }
      ]
    }
  ],
  "mutualDependencies": [
    [
      {
        "name": "bots | staticTabs | composeExtensions | configurableTabs",
        "id": "{string}",
        "commandIds": [
          "{string}"
        ]
      }
    ]
  ]
}
```

```json
{
  "type": "object",
  "properties": {
    "oneWayDependencies": {
      "type": "array",
      "items": {
        "$ref": "#/definitions/oneWayDependency"
      },
      "minItems": 1,
      "description": "An array containing multiple instances of unidirectional dependency relationships (each represented by a oneWayDependency object)."
    },
    "mutualDependencies": {
      "type": "array",
      "items": {
        "$ref": "#/definitions/mutualDependency"
      },
      "minItems": 1,
      "description": "An array containing multiple instances of mutual dependency relationships between elements (each represented by a mutualDependency object)."
    }
  },
  "anyOf": [
    {
      "required": [
        "oneWayDependencies"
      ]
    },
    {
      "required": [
        "mutualDependencies"
      ]
    }
  ],
  "additionalProperties": false
}
```

## Properties

#### oneWayDependencies

Defines one or more unidirectional dependency relationships among app components \(each represented by a `oneWayDependency` object with a *dependent* `element` and a `dependsOn` [`element`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-reference)\).

**Type**  
Array of [oneWayDependency](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/one-way-dependency?view=m365-app-1.30)

**Required**  
—

**Constraints**  
Minimum array items: 1.

**Supported values**  


#### mutualDependencies

Defines one or more mutual dependency relationships among app capabilities \(each represented by a `mutualDependency` array of [`element` objects](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-reference?view=m365-app-1.30)\).

Use the `mutualDependencies` array to group app capabilities that must load together to support their intended function. Each object in the array represents a set of mutually dependent app capabilities. The following JSON snippet shows a bot, static tab, message extension, and configurable tab that are mutually dependent on each other:

```json
"elementRelationshipSet": {
  "mutualDependencies" : [
    [
      {"name" : "bots", "id" : "bot-id"}, 
      {"name" : "staticTabs", "id" : "staticTab-id"},
      {"name" : "composeExtensions", "id" : "composeExtension-id"},
      {"name" : "configurableTabs", "id": "configurableTab-id"}
    ]
  ]
}
```

Note

The `mutualDependencies` property is a list of mutual dependency groups, and is defined in JSON as an array of arrays. The outer array defines the list of dependency groups and must have at least one item in the array. The inner array is the list of mutual dependencies for each group and must have at least two items in the array.

**Type**  
Array of [elementReference](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-reference?view=m365-app-1.30)

**Required**  
—

**Constraints**  
Minimum array items: 2. Minimum array items: 1.

**Supported values**  


## Examples

```json
{
"elementRelationshipSet": {
      "oneWayDependencies" : [
        {
          "element" : {
            "name" : "composeExtensions",
            "id" : "composeExtension-id",
            "commandIds": ["exampleCmd1", "exampleCmd2"]
          },
          "dependsOn" : [
              {"name" : "bots", "id" : "bot-id"}
          ]
        }
      ]
    }   
}
```
