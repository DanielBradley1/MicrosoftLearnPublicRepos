<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-copilot-agents-custom-engine-agents-disclaimer?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# root.copilotAgents.customEngineAgents.disclaimer object

For Microsoft internal use only. The disclaimer message shown to users before they interact with this application.

Properties that reference this object type:

- [root.copilotAgents.customEngineAgents.disclaimer](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-copilot-agents-custom-engine-agents?view=m365-app-1.30#disclaimer-property)

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
  "properties": {
    "text": {
      "type": "string",
      "description": "The message shown to users before they interact with this application. ",
      "maxLength": 500
    }
  },
  "required": [
    "text"
  ]
}
```

## Properties

#### text

The message shown to users before they interact with this application.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 500.

**Supported values**
