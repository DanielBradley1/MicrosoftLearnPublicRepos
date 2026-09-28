<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-commands-parameters-choices?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# root.composeExtensions.commands.parameters.choices object

The choice options for the parameter. Use only when `parameters.inputType` is `choiceset`.

Properties that reference this object type:

- [root.composeExtensions.commands.parameters.choices](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-commands-parameters?view=m365-app-1.30#choices-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "title": "{string}",
  "value": "{string}"
}
```

```json
{
  "type": "object",
  "properties": {
    "title": {
      "type": "string",
      "description": "Title of the choice",
      "maxLength": 128
    },
    "value": {
      "type": "string",
      "description": "Value of the choice",
      "maxLength": 512
    }
  },
  "additionalProperties": false,
  "required": [
    "title",
    "value"
  ]
}
```

## Properties

#### title

Title of the choice.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 128.

**Supported values**  


#### value

Value of the choice.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 512.

**Supported values**  


## Examples

```json
{
"composeExtensions": [
        {
            "commands": [
                {
                    "parameters": [
                        {
                            "choices": [
                                {
                                    "title": "Title of the choice",
                                    "value": "Value of the choice"
                                }
                            ]
                        }
                    ]
                },
            ],
        }
    ]
}
```
