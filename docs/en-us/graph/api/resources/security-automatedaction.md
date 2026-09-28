<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-automatedaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-20 -->

# automatedAction resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an automated response action configured in the **automatedActions** property of a [detectionAction](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionaction?view=graph-rest-beta) for a [detectionRule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-beta). This type is abstract and cannot be instantiated directly. Use one of the following derived types, differentiated by `@odata.type`:

- [accountObjectIdAction](https://learn.microsoft.com/en-us/graph/api/resources/security-accountobjectidaction?view=graph-rest-beta)
- [accountSidAction](https://learn.microsoft.com/en-us/graph/api/resources/security-accountsidaction?view=graph-rest-beta)
- [deviceAction](https://learn.microsoft.com/en-us/graph/api/resources/security-deviceaction?view=graph-rest-beta)
- [emailAction](https://learn.microsoft.com/en-us/graph/api/resources/security-emailaction?view=graph-rest-beta)
- [fileAction](https://learn.microsoft.com/en-us/graph/api/resources/security-fileaction?view=graph-rest-beta)
- [isolateDeviceAction](https://learn.microsoft.com/en-us/graph/api/resources/security-isolatedeviceaction?view=graph-rest-beta)
- [stopAndQuarantineFileAction](https://learn.microsoft.com/en-us/graph/api/resources/security-stopandquarantinefileaction?view=graph-rest-beta)

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
