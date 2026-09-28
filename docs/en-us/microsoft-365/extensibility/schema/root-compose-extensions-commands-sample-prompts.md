<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-commands-sample-prompts?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# root.composeExtensions.commands.samplePrompts object

Property used by Microsoft 365 Copilot to display prompts supported by the agent to the user. For Microsoft 365 Copilot scenarios, this property is required in order to pass app validation for store submission.

Properties that reference this object type:

- [root.composeExtensions.commands.samplePrompts](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions-commands?view=m365-app-1.30#samplePrompts-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "text": "{string}"
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "text": {
      "type": "string",
      "description": "This string will hold the sample prompt",
      "maxLength": 128
    }
  },
  "required": [
    "text"
  ]
}
```

## Properties

#### text

Content of the sample prompt.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 128.

**Supported values**  


#### text

Content of the sample prompt.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 128.

**Supported values**
