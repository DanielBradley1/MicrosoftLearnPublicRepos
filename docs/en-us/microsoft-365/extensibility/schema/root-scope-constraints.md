<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-scope-constraints?view=m365-app-prev -->
<!-- Sitemap-Last-Modified: 2026-06-29 -->

# root.scopeConstraints object

The scope constraints imposed on an app to specify in which threads you can install the app. When no constraints are specified, you can install the app to all threads within the specific scope.

Properties that reference this object type:

- [root.scopeConstraints](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-prev#scopeConstraints-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "teams": [
    {
      "id": "{string}"
    }
  ],
  "groupChats": [
    {
      "id": "{string}"
    }
  ]
}
```

```json
{
  "type": "object",
  "properties": {
    "teams": {
      "type": "array",
      "description": "A list of team thread ids to which your app is restricted to",
      "maxItems": 128,
      "items": {
        "type": "object",
        "properties": {
          "id": {
            "description": "Team\u0027s thread Id",
            "type": "string",
            "maxLength": 64
          }
        },
        "required": [
          "id"
        ],
        "additionalProperties": false
      }
    },
    "groupChats": {
      "type": "array",
      "description": "A list of chat thread ids to which your app is restricted to",
      "maxItems": 128,
      "items": {
        "type": "object",
        "properties": {
          "id": {
            "description": "Chat\u0027s thread Id",
            "type": "string",
            "maxLength": 64
          }
        },
        "required": [
          "id"
        ],
        "additionalProperties": false
      }
    }
  },
  "additionalProperties": false
}
```

## Properties

#### teams

A list of team thread ids to which your app is restricted to.

**Type**  
Array of [teams](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-scope-constraints-teams?view=m365-app-prev)

**Required**  
—

**Constraints**  
Maximum array items: 128.

**Supported values**  


#### groupChats

A list of chat thread ids to which your app is restricted to.

**Type**  
Array of [groupChats](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-scope-constraints-group-chats?view=m365-app-prev)

**Required**  
—

**Constraints**  
Maximum array items: 128.

**Supported values**  


## Examples

```json
{
    "scopeConstraints": { 
        "teams": [ 
            { "id": "%TEAMS-THREAD-ID" } 
        ], 
        "groupChats": [ 
          { "id": "%GROUP-CHATS-THREAD-ID" } 
        ] 
    }
}
```
