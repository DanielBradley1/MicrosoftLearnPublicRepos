<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macosredirectsinglesignonextension?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# macOSRedirectSingleSignOnExtension resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Represents a Redirect-type Single Sign-On extension profile for macOS devices.

Inherits from [macOSSingleSignOnExtension](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossinglesignonextension?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| extensionIdentifier | String | Gets or sets the bundle ID of the app extension that performs SSO for the specified URLs. |
| teamIdentifier | String | Gets or sets the team ID of the app extension that performs SSO for the specified URLs. |
| configurations | [keyTypedValuePair](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-keytypedvaluepair?view=graph-rest-beta) collection | Gets or sets a list of typed key-value pairs used to configure Credential-type profiles. This collection can contain a maximum of 500 elements. |
| urlPrefixes | String collection | One or more URL prefixes of identity providers on whose behalf the app extension performs single sign-on. URLs must begin with http:// or https://. All URL prefixes must be unique for all profiles. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.macOSRedirectSingleSignOnExtension",
  "extensionIdentifier": "String",
  "teamIdentifier": "String",
  "configurations": [
    {
      "@odata.type": "microsoft.graph.keyStringValuePair",
      "key": "String",
      "value": "String"
    }
  ],
  "urlPrefixes": [
    "String"
  ]
}
```
