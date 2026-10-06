<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-scope-constraints-group-chats?view=m365-app-prev -->
<!-- Sitemap-Last-Modified: 2026-09-30 -->

# root.scopeConstraints.groupChats object

A list of chat thread ids to which your app is restricted to

Properties that reference this object type:

- [root.scopeConstraints.groupChats](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-scope-constraints?view=m365-app-prev#groupChats-property)

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
```

## Properties

#### id

Chat's thread Id.

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
        "groupChats": [ 
          { "id": "%GROUP-CHATS-THREAD-ID" } 
        ] 
    }
}
```
