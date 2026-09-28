<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-authorization?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# root.authorization object

Represents authorization requirements for the app.

Properties that reference this object type:

- [root.authorization](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#authorization-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "permissions": {
    "resourceSpecific": [
      {
        resourceSpecific object
      }
    ]
  }
}
```

```json
{
  "type": "object",
  "description": "Specify and consolidates authorization related information for the App.",
  "additionalProperties": false,
  "properties": {
    "permissions": {
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
  }
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "permissions": {
    "resourceSpecific": [
      {
        resourceSpecific object
      }
    ]
  }
}
```

```json
{
  "type": "object",
  "description": "Specify and consolidates authorization related information for the App.",
  "additionalProperties": false,
  "properties": {
    "permissions": {
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
  }
}
```

## Properties

#### permissions

List of permissions that the app needs to function.

**Type**  
[permissions](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-authorization-permissions?view=m365-app-1.30)

**Required**  
—

**Constraints**  


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
