<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/one-way-dependency?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# oneWayDependency object

Describes the unidirectional dependency of one app capability \(X\) to another \(Y\). If a Microsoft 365 runtime host doesn't support a required capability \(Y\), the dependent capability \(X\) won't load or surface to the user.

Properties that reference this object type:

- [root.elementRelationshipSet.oneWayDependencies](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-element-relationship-set?view=m365-app-1.30#oneWayDependencies-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "element": {
    "name": "bots | staticTabs | composeExtensions | configurableTabs",
    "id": "{string}",
    "commandIds": [
      "{string}"
    ]
  },
  "dependsOn": [
    {
      "name": "bots | staticTabs | composeExtensions | configurableTabs",
      "id": "{string}",
      "commandIds": [
        "{string}"
      ]
    }
  ]
}
```

```json
{
  "type": "object",
  "properties": {
    "element": {
      "$ref": "#/definitions/elementReference"
    },
    "dependsOn": {
      "type": "array",
      "minItems": 1,
      "items": {
        "$ref": "#/definitions/elementReference"
      }
    }
  },
  "required": [
    "element",
    "dependsOn"
  ],
  "additionalProperties": false,
  "description": "An object representing a unidirectional dependency relationship, where one specific element (referred to as the \u0060element\u0060) relies on an array of other elements (referred to as the \u0060dependsOn\u0060) in a single direction."
}
```

## Properties

#### element

Represents an individual app capability \(represented by [`element`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-reference)\) that has a one-way runtime dependency on another capability being loaded.

**Type**  
[elementReference](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-reference?view=m365-app-1.30)

**Required**  
✅

**Constraints**  


**Supported values**  


#### dependsOn

Defines one or more app capabilities \(each represented by [`element`](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-reference)\) required for the specified `element` to load.

**Type**  
Array of [elementReference](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-reference?view=m365-app-1.30)

**Required**  
✅

**Constraints**  
Minimum array items: 1.

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
