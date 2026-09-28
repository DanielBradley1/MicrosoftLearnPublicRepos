<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists-commands?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# root.bots.commandLists.commands object

An optional list of commands that your bot can recommend to users. The object is an array \(maximum of 3 elements\) with all elements of type `object`; you must define a separate command list for each scope that your bot supports.

Properties that reference this object type:

- [root.bots.commandLists.commands](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots-command-lists?view=m365-app-1.30#commands-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "title": "{string}",
  "description": "{string}",
  "type": "basic | prompt",
  "prompt": "{string}"
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "title": {
      "type": "string",
      "description": "The bot command name",
      "maxLength": 128
    },
    "description": {
      "type": "string",
      "description": "A simple text description or an example of the command syntax and its arguments.",
      "maxLength": 4000
    },
    "type": {
      "type": "string",
      "enum": [
        "basic",
        "prompt"
      ],
      "description": "Type of the command. Default is basic",
      "default": "basic"
    },
    "prompt": {
      "type": "string",
      "maxLength": 4000,
      "description": "The prompt text to be used by Teams when user initiates the command from one of the entry points"
    }
  },
  "required": [
    "title"
  ]
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "title": "{string}",
  "description": "{string}"
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "title": {
      "type": "string",
      "description": "The bot command name",
      "maxLength": 128
    },
    "description": {
      "type": "string",
      "description": "A simple text description or an example of the command syntax and its arguments.",
      "maxLength": 4000
    }
  },
  "required": [
    "title",
    "description"
  ]
}
```

- [Syntax](#tabpanel_3_syntax)
- [Schema](#tabpanel_3_schema)

```json
{
  "title": "{string}",
  "description": "{string}"
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "title": {
      "type": "string",
      "description": "The bot command name",
      "maxLength": 32
    },
    "description": {
      "type": "string",
      "description": "A simple text description or an example of the command syntax and its arguments.",
      "maxLength": 128
    }
  },
  "required": [
    "title",
    "description"
  ]
}
```

## Properties

#### title

The bot command name.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 128.

**Supported values**  


#### title

The bot command name.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 32.

**Supported values**  


#### description

A simple text description or an example of the command syntax and its arguments.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 4000.

**Supported values**  


#### description

A simple text description or an example of the command syntax and its arguments.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 4000.

**Supported values**  


#### description

A simple text description or an example of the command syntax and its arguments.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 128.

**Supported values**  


#### type

Type of the command. Default is basic

**Type**  
string

**Required**  
—

**Constraints**  


**Supported values**  
Allowed values: `basic`, `prompt`.

#### prompt

The prompt text to be used by Teams when user initiates the command from one of the entry points

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 4000.

**Supported values**  


#### prompt

The prompt text to be used by Teams when user initiates the command from one of the entry points

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 4000.

**Supported values**  


## Examples

```json
{
 "bots": [
        {
            "commandLists": [
                {
                    "commands": [
                        {
                            "title": "Personal command 1",
                            "description": "Description of Personal command 1"
                        },
                        {
                            "title": "Personal command N",
                            "description": "Description of Personal command N"
                        }
                    ]
                }
            ]
        }
    ]
}
```
