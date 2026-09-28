<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossystemextensiontypemapping?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# macOSSystemExtensionTypeMapping resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Represents a mapping between team identifiers for macOS system extensions and system extension types.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| teamIdentifier | String | Gets or sets the team identifier used to sign the system extension. |
| allowedTypes | [macOSSystemExtensionType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossystemextensiontype?view=graph-rest-beta) | Gets or sets the allowed macOS system extension types. Possible values are: `driverExtensionsAllowed`, `networkExtensionsAllowed`, `endpointSecurityExtensionsAllowed`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.macOSSystemExtensionTypeMapping",
  "teamIdentifier": "String",
  "allowedTypes": "String"
}
```
