<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-automatedaction?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-03 -->

# automatedAction resource type

Namespace: microsoft.graph.security

Represents an automated response action configured in the **automatedActions** property of a [detectionAction](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionaction?view=graph-rest-1.0) for a [detectionRule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-1.0). This type is abstract and cannot be instantiated directly. Use one of the following derived types, differentiated by `@odata.type`:

- [accountObjectIdAction](https://learn.microsoft.com/en-us/graph/api/resources/security-accountobjectidaction?view=graph-rest-1.0)
- [accountSidAction](https://learn.microsoft.com/en-us/graph/api/resources/security-accountsidaction?view=graph-rest-1.0)
- [deviceAction](https://learn.microsoft.com/en-us/graph/api/resources/security-deviceaction?view=graph-rest-1.0)
- [emailAction](https://learn.microsoft.com/en-us/graph/api/resources/security-emailaction?view=graph-rest-1.0)
- [fileAction](https://learn.microsoft.com/en-us/graph/api/resources/security-fileaction?view=graph-rest-1.0)
- [isolateDeviceAction](https://learn.microsoft.com/en-us/graph/api/resources/security-isolatedeviceaction?view=graph-rest-1.0)
- [stopAndQuarantineFileAction](https://learn.microsoft.com/en-us/graph/api/resources/security-stopandquarantinefileaction?view=graph-rest-1.0)

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.automatedAction"
}
```
