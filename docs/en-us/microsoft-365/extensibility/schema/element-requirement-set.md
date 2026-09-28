<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/element-requirement-set?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# elementRequirementSet object

An object representing a set of requirements that the host must support for the element.

Properties that reference this object type:

- [root.bots.requirementSet](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-bots?view=m365-app-1.30#requirementSet-property)
- [root.composeExtensions.requirementSet](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-compose-extensions?view=m365-app-1.30#requirementSet-property)
- [root.staticTabs.requirementSet](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-static-tabs?view=m365-app-1.30#requirementSet-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "hostMustSupportFunctionalities": [
    {
      "name": "dialogUrl | dialogUrlBot | dialogAdaptiveCard | dialogAdaptiveCardBot"
    }
  ]
}
```

```json
{
  "type": "object",
  "properties": {
    "hostMustSupportFunctionalities": {
      "type": "array",
      "items": {
        "$ref": "#/definitions/hostFunctionality"
      },
      "minItems": 1
    }
  },
  "required": [
    "hostMustSupportFunctionalities"
  ],
  "additionalProperties": false,
  "description": "An object representing a set of requirements that the host must support for the element."
}
```

## Properties

#### hostMustSupportFunctionalities

Specifies one or more runtime capabilities the element requires to function properly. For more information, see [how to specify runtime requirements in your app manifest](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/specify-runtime-requirements).

**Type**  
Array of [hostFunctionality](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/host-functionality?view=m365-app-1.30)

**Required**  
✅

**Constraints**  
Minimum array items: 1.

**Supported values**  


## Examples

```json
{
    "staticTabs": [
        {
            "requirementSet": {
                "hostMustSupportFunctionalities": [
                  {"name": "dialogUrl"},
                  {"name": "dialogUrlBot"}
                ]
            }
        }
    ],
}
```

```json
{
    "bots": [
        {
            "requirementSet": {
                "hostMustSupportFunctionalities": [
                  {"name": "dialogUrl"},
                  {"name": "dialogUrlBot"}
                ]
            }
        }
    ],
}
```

```json
{
    "composeExtensions": [
        {
            "requirementSet": {
                "hostMustSupportFunctionalities": [
                  {"name": "dialogUrl"},
                  {"name": "dialogUrlBot"}
                ]
            }
        }
    ],
}
```
