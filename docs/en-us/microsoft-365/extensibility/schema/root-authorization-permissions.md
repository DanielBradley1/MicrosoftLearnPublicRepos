<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-authorization-permissions?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# root.authorization.permissions object

List of permissions that the app needs to function.

Properties that reference this object type:

- [root.authorization.permissions](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-authorization?view=m365-app-1.30#permissions-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "resourceSpecific": [
    {
      "name": "{string}",
      "type": "Application | Delegated"
    }
  ]
}
```

```json
{
  "type": "object",
  "description": "List of permissions that the app needs to function.",
  "additionalProperties": false,
  "properties": {
    "resourceSpecific": {
      "description": "Permissions that guard data access on a resource instance level.",
      "maxItems": 16,
      "type": "array",
      "uniqueItems": true,
      "items": {
        "type": "object",
        "additionalProperties": false,
        "properties": {
          "name": {
            "type": "string",
            "description": "The name of the resource-specific permission.",
            "maxLength": 128
          },
          "type": {
            "type": "string",
            "enum": [
              "Application",
              "Delegated"
            ],
            "description": "The type of the resource-specific permission."
          }
        },
        "required": [
          "name",
          "type"
        ]
      }
    }
  }
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "resourceSpecific": [
    {
      "name": "{string}",
      "type": "Application | Delegated"
    }
  ]
}
```

```json
{
  "type": "object",
  "description": "List of permissions that the app needs to function.",
  "additionalProperties": false,
  "properties": {
    "resourceSpecific": {
      "description": "Permissions that must be granted on a per resource instance basis.",
      "maxItems": 16,
      "type": "array",
      "uniqueItems": true,
      "items": {
        "type": "object",
        "additionalProperties": false,
        "properties": {
          "name": {
            "type": "string",
            "description": "The name of the resource-specific permission.",
            "maxLength": 128
          },
          "type": {
            "type": "string",
            "enum": [
              "Application",
              "Delegated"
            ],
            "description": "The type of the resource-specific permission: delegated vs application."
          }
        },
        "required": [
          "name",
          "type"
        ]
      }
    }
  }
}
```

## Properties

#### resourceSpecific

Permissions that guard data access on resource instance level.

**Type**  
Array of [resourceSpecific](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-authorization-permissions-resource-specific?view=m365-app-1.30)

**Required**  
—

**Constraints**  
Maximum array items: 16. Array items must be unique.

**Supported values**  


## Examples

```json
{
    "authorization": {
        "permissions": {
            "resourceSpecific": [
                {
                    "type": "Application",
                    "name": "ChannelSettings.Read.Group"
                },
                {
                    "type": "Delegated",
                    "name": "ChannelMeetingParticipant.Read.Group"
                }
            ]
        }
    }
}
```
