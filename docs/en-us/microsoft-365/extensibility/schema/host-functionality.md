<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/host-functionality?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# hostFunctionality object

An object representing a specific functionality that a host must support.

Properties that reference this object type:

- [root.bots.requirementSet.hostMustSupportFunctionalities](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-requirement-set?view=m365-app-1.30#hostMustSupportFunctionalities-property)
- [root.composeExtensions.requirementSet.hostMustSupportFunctionalities](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-requirement-set?view=m365-app-1.30#hostMustSupportFunctionalities-property)
- [root.staticTabs.requirementSet.hostMustSupportFunctionalities](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-requirement-set?view=m365-app-1.30#hostMustSupportFunctionalities-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "name": "dialogUrl | dialogUrlBot | dialogAdaptiveCard | dialogAdaptiveCardBot"
}
```

```json
{
  "type": "object",
  "properties": {
    "name": {
      "type": "string",
      "enum": [
        "dialogUrl",
        "dialogUrlBot",
        "dialogAdaptiveCard",
        "dialogAdaptiveCardBot"
      ],
      "description": "The name of the functionality."
    }
  },
  "required": [
    "name"
  ],
  "additionalProperties": false,
  "description": "An object representing a specific functionality that a host must support."
}
```

## Properties

#### name

The name of the functionality.

**Type**  
string

**Required**  
✅

**Constraints**  


**Supported values**  
Allowed values: `dialogUrl`, `dialogUrlBot`, `dialogAdaptiveCard`, `dialogAdaptiveCardBot`.

## Examples

```json
 {
    "hostMustSupportFunctionalities": [
        {"name": "dialogUrl"},
        {"name": "dialogUrlBot"}
    ]
}
```
