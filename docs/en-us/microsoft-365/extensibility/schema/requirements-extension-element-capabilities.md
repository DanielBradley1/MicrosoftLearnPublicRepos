<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/requirements-extension-element-capabilities?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# requirementsExtensionElement.capabilities object

Specifies the [requirement sets](https://learn.microsoft.com/en-us/javascript/api/requirement-sets) and the minimum version necessary for your add-in to function properly. This object determines your add-in availability across different Office applications and versions, ensuring that your add-in is only available on platforms that can support its features.

Important

Configuring requirements can be error prone. We strongly recommend that you familiarize yourself with [Specify Office Add-in requirements in the unified manifest for Microsoft 365](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/requirements-property-unified-manifest) and [Understand the logic of API requirement configuration](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/understand-requirement-configuration).

Properties that reference this object type:

- [root.extensions.alternates.requirements.capabilities](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/requirements-extension-element?view=m365-app-1.30#capabilities-property)
- [root.extensions.appDeeplinks.requirements.capabilities](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/requirements-extension-element?view=m365-app-1.30#capabilities-property)
- [root.extensions.autoRunEvents.requirements.capabilities](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/requirements-extension-element?view=m365-app-1.30#capabilities-property)
- [root.extensions.contentRuntimes.requirements.capabilities](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/requirements-extension-element?view=m365-app-1.30#capabilities-property)
- [root.extensions.contextMenus.requirements.capabilities](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/requirements-extension-element?view=m365-app-1.30#capabilities-property)
- [root.extensions.getStartedMessages.requirements.capabilities](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/requirements-extension-element?view=m365-app-1.30#capabilities-property)
- [root.extensions.keyboardShortcuts.requirements.capabilities](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/requirements-extension-element?view=m365-app-1.30#capabilities-property)
- [root.extensions.requirements.capabilities](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/requirements-extension-element?view=m365-app-1.30#capabilities-property)
- [root.extensions.ribbons.requirements.capabilities](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/requirements-extension-element?view=m365-app-1.30#capabilities-property)
- [root.extensions.runtimes.requirements.capabilities](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/requirements-extension-element?view=m365-app-1.30#capabilities-property)

Properties that reference this object type:

- [root.extensions.alternates.requirements.capabilities](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/requirements-extension-element?view=m365-app-1.30#capabilities-property)
- [root.extensions.autoRunEvents.requirements.capabilities](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/requirements-extension-element?view=m365-app-1.30#capabilities-property)
- [root.extensions.contentRuntimes.requirements.capabilities](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/requirements-extension-element?view=m365-app-1.30#capabilities-property)
- [root.extensions.contextMenus.requirements.capabilities](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/requirements-extension-element?view=m365-app-1.30#capabilities-property)
- [root.extensions.getStartedMessages.requirements.capabilities](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/requirements-extension-element?view=m365-app-1.30#capabilities-property)
- [root.extensions.keyboardShortcuts.requirements.capabilities](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/requirements-extension-element?view=m365-app-1.30#capabilities-property)
- [root.extensions.requirements.capabilities](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/requirements-extension-element?view=m365-app-1.30#capabilities-property)
- [root.extensions.ribbons.requirements.capabilities](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/requirements-extension-element?view=m365-app-1.30#capabilities-property)
- [root.extensions.runtimes.requirements.capabilities](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/requirements-extension-element?view=m365-app-1.30#capabilities-property)

Properties that reference this object type:

- [root.extensions.alternates.requirements.capabilities](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/requirements-extension-element?view=m365-app-1.30#capabilities-property)
- [root.extensions.autoRunEvents.requirements.capabilities](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/requirements-extension-element?view=m365-app-1.30#capabilities-property)
- [root.extensions.requirements.capabilities](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/requirements-extension-element?view=m365-app-1.30#capabilities-property)
- [root.extensions.ribbons.requirements.capabilities](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/requirements-extension-element?view=m365-app-1.30#capabilities-property)
- [root.extensions.runtimes.requirements.capabilities](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/requirements-extension-element?view=m365-app-1.30#capabilities-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "name": "{string}",
  "minVersion": "{string}",
  "maxVersion": "{string}"
}
```

```json
{
  "type": "object",
  "properties": {
    "name": {
      "type": "string",
      "description": "Identifies the name of the requirement sets that the add-in needs to run.",
      "maxLength": 128
    },
    "minVersion": {
      "type": "string",
      "description": "Identifies the minimum version for the requirement sets that the add-in needs to run."
    },
    "maxVersion": {
      "type": "string",
      "description": "Identifies the maximum version for the requirement sets that the add-in needs to run."
    }
  },
  "additionalProperties": false,
  "required": [
    "name"
  ]
}
```

## Properties

#### name

Identifies the name of the requirement set.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 128.

**Supported values**  


#### minVersion

Identifies the minimum version for the requirement set.

**Type**  
string

**Required**  
—

**Constraints**  


**Supported values**  


#### maxVersion

Identifies the maximum version for the requirement set.

**Type**  
string

**Required**  
—

**Constraints**  


**Supported values**  


## Examples

```json
{
  "capabilities": [
    {
      "name": "Mailbox",
      "minVersion": "1.1"
    }
  ]
}
```
