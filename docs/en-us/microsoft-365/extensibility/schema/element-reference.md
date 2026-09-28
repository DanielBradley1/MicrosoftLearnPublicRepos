<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-reference?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# elementReference object

Describes an app capability \(`element`\) in an `elementRelationshipSet`.

Properties that reference this object type:

- [root.elementRelationshipSet.oneWayDependencies.dependsOn](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/one-way-dependency?view=m365-app-1.30#dependsOn-property)
- [root.elementRelationshipSet.oneWayDependencies.element](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/one-way-dependency?view=m365-app-1.30#element-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "name": "bots | staticTabs | composeExtensions | configurableTabs",
  "id": "{string}",
  "commandIds": [
    "{string}"
  ]
}
```

```json
{
  "type": "object",
  "properties": {
    "name": {
      "type": "string",
      "enum": [
        "bots",
        "staticTabs",
        "composeExtensions",
        "configurableTabs"
      ]
    },
    "id": {
      "type": "string"
    },
    "commandIds": {
      "type": "array",
      "minItems": 1,
      "items": {
        "type": "string"
      }
    }
  },
  "required": [
    "name",
    "id"
  ],
  "additionalProperties": false
}
```

## Properties

#### name

The type of app capability.

**Type**  
string

**Required**  
✅

**Constraints**  


**Supported values**  
Allowed values: `bots`, `staticTabs`, `composeExtensions`, `configurableTabs`.

#### id

If there are multiple instances of a bot, tab, or message extension, this property defines a specific instance of the capability. It maps to `botId` for bots, `entityId` for static tabs, and `id` for configurable tabs and message extensions.

**Type**  
string

**Required**  
✅

**Constraints**  


**Supported values**  


#### commandIds

List of one or more message extension commands that are dependent on the specified `dependsOn` capability. Use only for message extensions.

**Type**  
Array of string

**Required**  
—

**Constraints**  
Minimum array items: 1.

**Supported values**  


## Examples

```json
{
  "element" : {
    "name" : "composeExtensions",
    "id" : "composeExtension-id",
    "commandIds": ["exampleCmd1", "exampleCmd2"]
  }
}
```
