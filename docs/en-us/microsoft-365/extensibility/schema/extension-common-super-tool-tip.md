<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-super-tool-tip?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# extensionCommonSuperToolTip object

Configures a supertip.

Properties that reference this object type:

- [root.extensions.contextMenus.menus.controls.items.supertip](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-custom-control-menu-item?view=m365-app-1.30#supertip-property)
- [root.extensions.contextMenus.menus.controls.supertip](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-custom-group-controls-item?view=m365-app-1.30#supertip-property)
- [root.extensions.ribbons.fixedControls.supertip](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-array-fixed-control-item?view=m365-app-1.30#supertip-property)
- [root.extensions.ribbons.tabs.groups.controls.items.supertip](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-custom-control-menu-item?view=m365-app-1.30#supertip-property)
- [root.extensions.ribbons.tabs.groups.controls.supertip](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-custom-group-controls-item?view=m365-app-1.30#supertip-property)

Properties that reference this object type:

- [root.extensions.ribbons.fixedControls.supertip](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-array-fixed-control-item?view=m365-app-1.30#supertip-property)
- [root.extensions.ribbons.tabs.groups.controls.items.supertip](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-custom-control-menu-item?view=m365-app-1.30#supertip-property)
- [root.extensions.ribbons.tabs.groups.controls.supertip](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-custom-group-controls-item?view=m365-app-1.30#supertip-property)

Properties that reference this object type:

- [root.extensions.ribbons.tabs.groups.controls.items.supertip](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-custom-control-menu-item?view=m365-app-1.30#supertip-property)
- [root.extensions.ribbons.tabs.groups.controls.supertip](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-common-custom-group-controls-item?view=m365-app-1.30#supertip-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "title": "{string}",
  "description": "{string}"
}
```

```json
{
  "type": "object",
  "properties": {
    "title": {
      "type": "string",
      "description": "Title text of the super tip. Maximum length is 64 characters.",
      "maxLength": 64
    },
    "description": {
      "type": "string",
      "description": "Description of the super tip. Maximum length is 250 characters.",
      "maxLength": 250
    }
  },
  "additionalProperties": false,
  "required": [
    "title",
    "description"
  ]
}
```

## Properties

#### title

Specifies the title text of the supertip.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 64.

**Supported values**  


#### description

Specifies the description of the supertip.

Note

The `description` property isn't supported in Outlook on the web or [new Outlook on Windows](https://support.microsoft.com/office/656bb8d9-5a60-49b2-a98b-ba7822bc7627).

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 250.

**Supported values**  


## Remarks

Supertips aren't supported in Office on the web, except that in Outlook on the web and [new Outlook on Windows](https://support.microsoft.com/office/656bb8d9-5a60-49b2-a98b-ba7822bc7627), the `supertip.title` property is supported.

## Examples

```json
{
    "supertip": {
      "title": "My Menu",
      "description": "Menu with 2 actions"
    }
}
```
