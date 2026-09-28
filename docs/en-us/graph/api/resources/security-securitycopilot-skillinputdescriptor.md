<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-securitycopilot-skillinputdescriptor?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-04 -->

# skillInputDescriptor resource type

Namespace: microsoft.graph.security.securityCopilot

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Defines the capabilities of a skill in Security Copilot. For more information, see the [Security Copilot Agent manifest](https://learn.microsoft.com/en-us/copilot/security/developer/agent-manifest).

**NOTE** This object is currently unsupported.

Inherits from [microsoft.graph.security.securityCopilot.skillVariableDescriptor](https://learn.microsoft.com/en-us/graph/api/resources/security-securitycopilot-skillvariabledescriptor?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| defaultValue | String | Unsupported. |
| description | String | Unsupported. Inherited from [microsoft.graph.security.securityCopilot.skillVariableDescriptor](https://learn.microsoft.com/en-us/graph/api/resources/security-securitycopilot-skillvariabledescriptor?view=graph-rest-beta). |
| isRequired | Boolean | Unsupported. |
| name | String | Unsupported. Inherited from [microsoft.graph.security.securityCopilot.skillVariableDescriptor](https://learn.microsoft.com/en-us/graph/api/resources/security-securitycopilot-skillvariabledescriptor?view=graph-rest-beta). |
| placeholderValue | String | Unsupported. |
| type | [microsoft.graph.security.securityCopilot.skillTypeDescriptor](https://learn.microsoft.com/en-us/graph/api/resources/security-securitycopilot-skilltypedescriptor?view=graph-rest-beta) | Unsupported. Inherited from [microsoft.graph.security.securityCopilot.skillVariableDescriptor](https://learn.microsoft.com/en-us/graph/api/resources/security-securitycopilot-skillvariabledescriptor?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.securityCopilot.skillInputDescriptor",
  "name": "String",
  "description": "String",
  "type": {
    "@odata.type": "microsoft.graph.security.securityCopilot.skillTypeDescriptor"
  },
  "isRequired": "Boolean",
  "defaultValue": "String",
  "placeholderValue": "String"
}
```
