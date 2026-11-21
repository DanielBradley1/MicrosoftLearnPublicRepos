<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackageagentmanagerscope -->
<!-- Sitemap-Last-Modified: 2026-11-18 -->

# copilotPackageAgentManagerScope resource type

This reference describes only the beta contract. Select **beta** to view it; availability depends on the matching schema and backend release.

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

The manager audience supplied to [Activate](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackageactivationresult-activate). This reviewed beta value isn't a regular-package acquisition audience or the stored recipients of an individual approval request.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `principals` | [copilotPackageActivationPrincipal](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackageactivationprincipal) collection | Non-nullable. Supply an explicit empty array for `everyone` or `noOne`; supply one or more user/group entries for `specificUsers`. No ordering, duplicate-rejection, or group-expansion guarantee is introduced. |
| `scope` | copilotPackageAgentManagerScopeType | Non-nullable. The manager-audience selection. See the enumeration below. |

### copilotPackageAgentManagerScopeType enumeration

| Value | Description |
| :--- | :--- |
| `everyone` | All agent managers can create instances from the template. |
| `specificUsers` | The selected users or groups can create instances. |
| `noOne` | No manager audience is selected. |
| `unknownFutureValue` | Reserved for enum evolution; not an accepted manager-audience input. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.copilotPackageAgentManagerScope",
  "principals": [
    {
      "@odata.type": "microsoft.graph.copilotPackageActivationPrincipal"
    }
  ],
  "scope": "String"
}
```
