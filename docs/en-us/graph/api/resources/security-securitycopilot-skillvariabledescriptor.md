<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-securitycopilot-skillvariabledescriptor?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-04 -->

# skillVariableDescriptor resource type

Namespace: microsoft.graph.security.securityCopilot

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Defines the capabilities of a skill in Security Copilot. For more information, see the [Security Copilot Agent manifest](https://learn.microsoft.com/en-us/copilot/security/developer/agent-manifest).

This entire resource is currently unsupported.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | Unsupported. |
| name | String | Unsupported. |
| type | [microsoft.graph.security.securityCopilot.skillTypeDescriptor](https://learn.microsoft.com/en-us/graph/api/resources/security-securitycopilot-skilltypedescriptor?view=graph-rest-beta) | Unsupported. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.securityCopilot.skillVariableDescriptor",
  "name": "String",
  "description": "String",
  "type": {
    "@odata.type": "microsoft.graph.security.securityCopilot.skillTypeDescriptor"
  }
}
```
