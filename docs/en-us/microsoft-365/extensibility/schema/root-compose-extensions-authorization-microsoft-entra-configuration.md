<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-authorization-microsoft-entra-configuration?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# root.composeExtensions.authorization.microsoftEntraConfiguration object

Object capturing details needed to do microsoftEntra auth flow. Applicable only when auth type is `microsoftEntra`.

Properties that reference this object type:

- [root.composeExtensions.authorization.microsoftEntraConfiguration](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-authorization?view=m365-app-1.30#microsoftEntraConfiguration-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "supportsSingleSignOn": {boolean}
}
```

```json
{
  "type": "object",
  "description": "Object capturing details needed to do microsoftEntra auth flow. It will be only present when auth type is microsoftEntra.",
  "properties": {
    "supportsSingleSignOn": {
      "type": "boolean",
      "default": false,
      "description": "Boolean indicating whether single sign on is configured for the app."
    }
  },
  "additionalProperties": false
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "supportsSingleSignOn": {boolean}
}
```

```json
{
  "type": "object",
  "description": "Object capturing details needed to do single aad auth flow. It will be only present when auth type is entraId.",
  "properties": {
    "supportsSingleSignOn": {
      "type": "boolean",
      "default": false,
      "description": "Boolean indicating whether single sign on is configured for the app."
    }
  },
  "additionalProperties": false
}
```

## Properties

#### supportsSingleSignOn

Boolean indicating whether single sign on is configured for the app.

**Type**  
boolean

**Required**  
—

**Constraints**  


**Supported values**  
Default value: `False`.
