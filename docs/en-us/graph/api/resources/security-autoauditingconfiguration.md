<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-autoauditingconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-04-10 -->

# autoAuditingConfiguration resource type

Namespace: microsoft.graph.security

Represents the configuration settings for automatic auditing in Microsoft Defender for Identity. The config activates predefined audit policies that automatically log critical security events in Windows Event Viewer. For more information, see [Configure audit policies for Windows event logs](https://learn.microsoft.com/en-us/defender-for-identity/deploy/configure-windows-event-collection).

Inherits from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/security-autoauditingconfiguration-get?view=graph-rest-1.0) | [microsoft.graph.security.autoAuditingConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/security-autoauditingconfiguration?view=graph-rest-1.0) | Read the properties and relationships of [microsoft.graph.security.autoAuditingConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/security-autoauditingconfiguration?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/security-autoauditingconfiguration-update?view=graph-rest-1.0) | [microsoft.graph.security.autoAuditingConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/security-autoauditingconfiguration?view=graph-rest-1.0) | Update the properties of an autoAuditingConfiguration object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isAutomatic | Boolean | Indicates whether automatic auditing is enabled for Defender for Identity monitoring. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.autoAuditingConfiguration",
  "isAutomatic": "Boolean"
}
```
