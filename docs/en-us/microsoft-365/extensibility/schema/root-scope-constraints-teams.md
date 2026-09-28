<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-scope-constraints-teams?view=m365-app-prev -->
<!-- Sitemap-Last-Modified: 2026-06-29 -->

# root.scopeConstraints.teams object

A list of team thread ids to which your app is restricted to

Properties that reference this object type:

- [root.scopeConstraints.teams](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-scope-constraints?view=m365-app-prev#teams-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "id": "{string}"
}
```

```json
{
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
```

## Properties

#### id

Team's thread Id.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 64.

**Supported values**  


## Examples

```json
{
    "scopeConstraints": { 
        "teams": [ 
            { "id": "%TEAMS-THREAD-ID" } 
        ]
    }
}
```
