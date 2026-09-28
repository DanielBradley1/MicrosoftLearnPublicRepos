<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-key-combination?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# extensionKeyCombination object

[Sets the customs key combinations](https://learn.microsoft.com/en-us/office/dev/add-ins/design/keyboard-shortcuts?tabs=jsonmanifest#define-custom-keyboard-shortcuts) for your Office Add-in on different platform \(i.e. default, windows, web and mac\).

Properties that reference this object type:

- [root.extensions.keyboardShortcuts.shortcuts.key](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-shortcut?view=m365-app-1.30#key-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "default": "{string}",
  "mac": "{string}",
  "web": "{string}",
  "windows": "{string}"
}
```

```json
{
  "type": "object",
  "description": "Key combinations in different platform (i.e. default, windows, web and mac).",
  "properties": {
    "default": {
      "type": "string",
      "description": "Fallback key for any platform that isn\u0027t specified.",
      "pattern": "^[A-Za-z0-9-_\u002B]\u002B$",
      "minLength": 1,
      "maxLength": 32
    },
    "mac": {
      "type": "string",
      "description": "key for mac platform. Alt is mapped to the Option key.",
      "pattern": "^[A-Za-z0-9-_\u002B]\u002B$",
      "minLength": 1,
      "maxLength": 32
    },
    "web": {
      "type": "string",
      "description": "key for web platform.",
      "pattern": "^[A-Za-z0-9-_\u002B]\u002B$",
      "minLength": 1,
      "maxLength": 32
    },
    "windows": {
      "type": "string",
      "description": "key for windows platform. Command is mapped to the Ctrl key.",
      "pattern": "^[A-Za-z0-9-_\u002B]\u002B$",
      "minLength": 1,
      "maxLength": 32
    }
  },
  "required": [
    "default"
  ]
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "default": "{string}",
  "mac": "{string}",
  "web": "{string}",
  "windows": "{string}"
}
```

```json
{
  "type": "object",
  "description": "Key combinations in different platform (i.e. default, windows, web and mac).",
  "properties": {
    "default": {
      "type": "string",
      "description": "Fallback key for any platform that isn\u0027t specified.",
      "pattern": "^[A-Za-z0-9-_\u002B]\u002B$",
      "minLength": 1,
      "maxLength": 32
    },
    "mac": {
      "type": "string",
      "description": "key for mac platform. Alt is mapped to the Option key.",
      "pattern": "^[A-Za-z0-9-_\u002B]\u002B$",
      "minLength": 1,
      "maxLength": 32
    },
    "web": {
      "type": "string",
      "pattern": "^[A-Za-z0-9-_\u002B]\u002B$",
      "description": "key for web platform.",
      "minLength": 1,
      "maxLength": 32
    },
    "windows": {
      "type": "string",
      "description": "key for windows platform. Command is mapped to the Ctrl key.",
      "pattern": "^[A-Za-z0-9-_\u002B]\u002B$",
      "minLength": 1,
      "maxLength": 32
    }
  },
  "required": [
    "default"
  ]
}
```

## Properties

#### default

The default custom key combination. Also, the fallback key combination for any platform that isn't specified.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
✅

**Constraints**  
Minimum string length: 1. Maximum string length: 32.

**Supported values**  
The string value must contain only letters, numbers, hyphens, underscores, and plus signs.

#### mac

The custom key for Mac platform. Alt is mapped to the Option key.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
—

**Constraints**  
Minimum string length: 1. Maximum string length: 32.

**Supported values**  
The string value must contain only letters, numbers, hyphens, underscores, and plus signs.

#### web

The custom key for web platform.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
—

**Constraints**  
Minimum string length: 1. Maximum string length: 32.

**Supported values**  
The string value must contain only letters, numbers, hyphens, underscores, and plus signs.

#### windows

Custom key for windows platform. Command is mapped to the Ctrl key.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
—

**Constraints**  
Minimum string length: 1. Maximum string length: 32.

**Supported values**  
The string value must contain only letters, numbers, hyphens, underscores, and plus signs.
