<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-markuserascompromisedresponseaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-20 -->

# markUserAsCompromisedResponseAction resource type \(deprecated\)

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Important

The **markUserAsCompromisedResponseAction** resource type is deprecated and will be removed on October 1, 2026. Use [automatedAction](https://learn.microsoft.com/en-us/graph/api/resources/security-automatedaction?view=graph-rest-beta) \(grouped via [automatedActionSet](https://learn.microsoft.com/en-us/graph/api/resources/security-automatedactionset?view=graph-rest-beta)\) on the [detectionAction](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionaction?view=graph-rest-beta) resource instead.

Describes a response action that sets the user's risk level to "high" in Microsoft Entra ID. This response action sets the user's risk level to `high` in Microsoft Entra ID, which triggers the identity protection policies for a `high` risk level.

Inherits from [microsoft.graph.security.responseAction](https://learn.microsoft.com/en-us/graph/api/resources/security-responseaction?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| identifier | [microsoft.graph.security.markUserAsCompromisedEntityIdentifier](https://learn.microsoft.com/en-us/graph/api/resources/enums-security?view=graph-rest-beta#markuserascompromisedentityidentifier-values) | Unique identifier for the response action. The possible values are: `accountObjectId`, `initiatingProcessAccountObjectId`, `servicePrincipalId`, `recipientObjectId`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.markUserAsCompromisedResponseAction",
  "identifier": "String"
}
```
