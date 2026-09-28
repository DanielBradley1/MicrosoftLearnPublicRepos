<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-intune-info?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# root.intuneInfo object

Properties related to app support for Microsoft Intune.

Properties that reference this object type:

- [root.intuneInfo](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#intuneInfo-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "supportedMobileAppManagementVersion": "{string}"
}
```

```json
{
  "type": "object",
  "description": "The Intune-related properties for the app.",
  "properties": {
    "supportedMobileAppManagementVersion": {
      "type": "string",
      "description": "Supported mobile app managment version that the app is compliant with.",
      "maxLength": 64
    }
  },
  "additionalProperties": false
}
```

## Properties

#### supportedMobileAppManagementVersion

Supported [Microsoft Intune Mobile App Management](https://learn.microsoft.com/en-us/mem/intune/apps/app-management) \(MAM\) version. The value is a single version number in the `integer.integer` format, such as `1.2`, indicating the highest level of support the app confirms. If no value is provided, the app does not attest to be Intune MAM compliant.

**Type**  
string

**Required**  
—

**Constraints**  
Maximum string length: 64.

**Supported values**
