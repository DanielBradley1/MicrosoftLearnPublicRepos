<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-background-load-configuration-tab-configuration?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# root.backgroundLoadConfiguration.tabConfiguration object

Optional property within backgroundLoadConfiguration containing tab settings for background loading.

Properties that reference this object type:

- [root.backgroundLoadConfiguration.tabConfiguration](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-background-load-configuration?view=m365-app-1.30#tabConfiguration-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "contentUrl": "{string}"
}
```

```json
{
  "type": "object",
  "description": "Optional property within backgroundLoadConfiguration containing tab settings for background loading. Setting tabConfiguration indicates that the app supports background loading of tabs.",
  "properties": {
    "contentUrl": {
      "$ref": "#/definitions/anyHttpUrl",
      "description": "Required URL for background loading. This can be the same contentUrl from the staticTabs section or an alternative endpoint used for background loading."
    }
  },
  "required": [
    "contentUrl"
  ],
  "additionalProperties": false
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "contentUrl": "{string}"
}
```

```json
{
  "type": "object",
  "description": "Optional property within backgroundLoadConfiguration containing tab settings for background loading.",
  "properties": {
    "contentUrl": {
      "$ref": "#/definitions/anyHttpUrl",
      "description": "Required URL for background loading. This can be the same contentUrl from the staticTabs section or an alternative endpoint used for background loading."
    }
  },
  "required": [
    "contentUrl"
  ],
  "additionalProperties": false
}
```

- [Syntax](#tabpanel_3_syntax)
- [Schema](#tabpanel_3_schema)

```json
{
  "contentUrl": "{string}"
}
```

```json
{
  "type": "object",
  "description": "Optional property within backgroundLoadConfiguration containing tab settings for background loading.",
  "properties": {
    "contentUrl": {
      "$ref": "#/definitions/httpsUrl",
      "description": "Required URL for background loading. This can be the same contentUrl from the staticTabs section or an alternative endpoint used for background loading."
    }
  },
  "required": [
    "contentUrl"
  ],
  "additionalProperties": false
}
```

## Properties

#### contentUrl

Required URL for background loading. This can be the same contentUrl from the staticTabs section or an alternative endpoint used for background loading.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 2048.

**Supported values**  
The string must start with `http://` or `https://`.
