<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosazureadsinglesignonextension?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# iosAzureAdSingleSignOnExtension resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Represents an Azure AD-type Single Sign-On extension profile for iOS devices.

Inherits from [iosSingleSignOnExtension](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iossinglesignonextension?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| enableSharedDeviceMode | Boolean | Enables or disables shared device mode. |
| bundleIdAccessControlList | String collection | An optional list of additional bundle IDs allowed to use the AAD extension for single sign-on. |
| configurations | [keyTypedValuePair](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-keytypedvaluepair?view=graph-rest-beta) collection | Gets or sets a list of typed key-value pairs used to configure Credential-type profiles. This collection can contain a maximum of 500 elements. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.iosAzureAdSingleSignOnExtension",
  "enableSharedDeviceMode": true,
  "bundleIdAccessControlList": [
    "String"
  ],
  "configurations": [
    {
      "@odata.type": "microsoft.graph.keyTypedValuePair",
      "key": "String"
    }
  ]
}
```
