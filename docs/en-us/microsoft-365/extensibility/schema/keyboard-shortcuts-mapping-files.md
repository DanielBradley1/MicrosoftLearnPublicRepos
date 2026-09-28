<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/keyboard-shortcuts-mapping-files?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# keyboardShortcutsMappingFiles object

Specifies the full URLs for shortcuts mapping and localization resource files that don't directly support the unified manifest.

Properties that reference this object type:

- [root.extensions.keyboardShortcuts.keyMappingFiles](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-keyboard-shortcut?view=m365-app-1.30#keyMappingFiles-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "shortcutsUrl": "{string}",
  "localizationResourceUrl": "{string}"
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "shortcutsUrl": {
      "$ref": "#/definitions/secureHttpUrl",
      "description": "The full URL of the JSON file that will contain the keyboard combination configuration on Office application and platform combinations that don\u0027t directly support the unified manifest."
    },
    "localizationResourceUrl": {
      "$ref": "#/definitions/secureHttpUrl",
      "description": "The full URL of a file that provides supplemental resource, such as localized strings, for the file specified in the shortcutsUrl attribute."
    }
  },
  "required": [
    "shortcutsUrl"
  ]
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "shortcutsUrl": "{string}",
  "localizationResourceUrl": "{string}"
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "shortcutsUrl": {
      "$ref": "#/definitions/httpsUrl",
      "description": "The full URL of the JSON file that will contain the keyboard combination configuration on Office application and platform combinations that don\u0027t directly support the unified manifest."
    },
    "localizationResourceUrl": {
      "$ref": "#/definitions/httpsUrl",
      "description": "The full URL of a file that provides supplemental resource, such as localized strings, for the file specified in the shortcutsUrl attribute."
    }
  },
  "required": [
    "shortcutsUrl"
  ]
}
```

## Properties

#### shortcutsUrl

The full URL of the JSON file that will contain the keyboard combination configuration on Office application and platform combinations that don't directly support the unified manifest.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 2048.

**Supported values**  
The string must start with `https://`.

#### shortcutsUrl

The full URL of the JSON file that will contain the keyboard combination configuration on Office application and platform combinations that don't directly support the unified manifest.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 2048.

**Supported values**  
The string must start with `http://` or `https://`.

#### localizationResourceUrl

The full URL of a file that provides supplemental resource, such as localized strings, for the file specified in the shortcutsUrl attribute.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 2048.

**Supported values**  
The string must start with `https://`.

#### localizationResourceUrl

The full URL of a file that provides supplemental resource, such as localized strings, for the file specified in the shortcutsUrl attribute.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 2048.

**Supported values**  
The string must start with `http://` or `https://`.
