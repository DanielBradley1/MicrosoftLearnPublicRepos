<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-message-handlers-value?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# root.composeExtensions.messageHandlers.value object

Properties that reference this object type:

- [root.composeExtensions.messageHandlers.value](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-message-handlers?view=m365-app-1.30#value-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "domains": [
    "{string}"
  ],
  "supportsAnonymousAccess": {boolean},
  "supportsAnonymizedPayloads": {boolean}
}
```

```json
{
  "type": "object",
  "properties": {
    "domains": {
      "type": "array",
      "description": "A list of domains that the link message handler can register for, and when they are matched the app will be invoked",
      "items": {
        "type": "string",
        "maxLength": 2048
      }
    },
    "supportsAnonymousAccess": {
      "type": "boolean",
      "description": "A boolean value that indicates whether the app\u0027s link message handler supports anonymous invoke flow. [Deprecated]. This property has been superceded by \u0027supportsAnonymizedPayloads\u0027.",
      "default": false
    },
    "supportsAnonymizedPayloads": {
      "type": "boolean",
      "description": "A boolean value that indicates whether the app\u0027s link message handler supports anonymous invoke flow.",
      "default": false
    }
  }
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "domains": [
    "{string}"
  ],
  "supportsAnonymizedPayloads": {boolean}
}
```

```json
{
  "type": "object",
  "properties": {
    "domains": {
      "type": "array",
      "description": "A list of domains that the link message handler can register for, and when they are matched the app will be invoked",
      "items": {
        "type": "string",
        "maxLength": 2048
      }
    },
    "supportsAnonymizedPayloads": {
      "type": "boolean",
      "description": "A boolean that indicates whether the app\u0027s link message handler supports anonymous invoke flow.",
      "default": false
    }
  },
  "additionalProperties": false
}
```

- [Syntax](#tabpanel_3_syntax)
- [Schema](#tabpanel_3_schema)

```json
{
  "domains": [
    "{string}"
  ],
  "supportsAnonymizedPayloads": {boolean}
}
```

```json
{
  "type": "object",
  "properties": {
    "domains": {
      "type": "array",
      "description": "A list of domains that the link message handler can register for, and when they are matched the app will be invoked",
      "items": {
        "type": "string",
        "maxLength": 2048
      }
    },
    "supportsAnonymizedPayloads": {
      "type": "boolean",
      "description": "A boolean that indicates whether the app\u0027s link message handler supports anonymous invoke flow.",
      "default": false
    }
  }
}
```

## Properties

#### domains

Array of domains that the link message handler can register for, and when they are matched the app will be invoked.

**Type**  
Array of string

**Required**  
—

**Constraints**  
Maximum string length: 2048.

**Supported values**  


#### supportsAnonymousAccess

**\[Deprecated\]**. This property has been superceded by `supportsAnonymizedPayloads`.

**Type**  
boolean

**Required**  
—

**Constraints**  


**Supported values**  
Default value: `False`.

#### supportsAnonymizedPayloads

A boolean value that indicates whether the app's link message handler supports anonymous invoke flow. To enable zero install for link unfurling, the value needs to be set to `true`.

**Type**  
boolean

**Required**  
—

**Constraints**  


**Supported values**  
Default value: `False`.

## Examples

```json
{
"composeExtensions": [
        {
            "messageHandlers": [
                {
                    "value": {
                        "domains": [
                            "mysite.someplace.com",
                            "othersite.someplace.com"
                        ],
                        "supportsAnonymizedPayloads": false
                    }
                }
            ]
        }
    ]
}
```
