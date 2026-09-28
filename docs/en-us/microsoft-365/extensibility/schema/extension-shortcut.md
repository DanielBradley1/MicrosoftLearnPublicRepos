<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-shortcut?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# extensionShortcut object

Array of mappings from actions to the key combinations that invoke the actions.

Properties that reference this object type:

- [root.extensions.keyboardShortcuts.shortcuts](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-keyboard-shortcut?view=m365-app-1.30#shortcuts-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "key": {
    "default": "{string}",
    "mac": "{string}",
    "web": "{string}",
    "windows": "{string}"
  },
  "actionId": "{string}"
}
```

```json
{
  "type": "object",
  "properties": {
    "key": {
      "type": "object",
      "$ref": "#/definitions/extensionKeyCombination"
    },
    "actionId": {
      "type": "string",
      "description": "The ID of an execution-type action that handles this key combination.",
      "minLength": 1,
      "maxLength": 64
    }
  },
  "required": [
    "key",
    "actionId"
  ]
}
```

## Properties

#### key

**Type**  
[extensionKeyCombination](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-key-combination?view=m365-app-1.30)

**Required**  
✅

**Constraints**  


**Supported values**  


#### actionId

The ID of an execution-type action that handles this key combination.

**Type**  
string

**Required**  
✅

**Constraints**  
Minimum string length: 1. Maximum string length: 64.

**Supported values**
