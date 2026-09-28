<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-background-load-configuration?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# root.backgroundLoadConfiguration object

Optional property containing background loading configuration. By opting in to this performance enhancement, your app is eligible to be loaded in the background in any Microsoft 365 application host that supports this feature.

Properties that reference this object type:

- [root.backgroundLoadConfiguration](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#backgroundLoadConfiguration-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "tabConfiguration": {
    "contentUrl": "{string}"
  }
}
```

```json
{
  "type": "object",
  "description": "Optional property containing background loading configuration. By opting into this performance enhancement, your app is eligible to be loaded in the background in any Microsoft 365 application host that supports this feature. Note that setting this property gives the host client permission to load the app in the background but does not guarantee the app will be preloaded at runtime. Whether an app is preloaded in the background will be dynamically determined based on usage and other criteria.",
  "properties": {
    "tabConfiguration": {
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
  },
  "additionalProperties": false
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "tabConfiguration": {
    "contentUrl": "{string}"
  }
}
```

```json
{
  "type": "object",
  "description": "Optional property containing background loading configuration. By opting in to this performance enhancement, your app is eligible to be loaded in the background in any Microsoft 365 application host that supports this feature.",
  "properties": {
    "tabConfiguration": {
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
  },
  "additionalProperties": false
}
```

- [Syntax](#tabpanel_3_syntax)
- [Schema](#tabpanel_3_schema)

```json
{
  "tabConfiguration": {
    "contentUrl": "{string}"
  }
}
```

```json
{
  "type": "object",
  "description": "Optional property containing background loading configuration. By opting in to this performance enhancement, your app is eligible to be loaded in the background in any Microsoft 365 application host that supports this feature.",
  "properties": {
    "tabConfiguration": {
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
  },
  "additionalProperties": false
}
```

## Properties

#### tabConfiguration

Optional property within backgroundLoadConfiguration containing tab settings for background loading.

**Type**  
[tabConfiguration](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-background-load-configuration-tab-configuration?view=m365-app-1.30)

**Required**  
—

**Constraints**  


**Supported values**
