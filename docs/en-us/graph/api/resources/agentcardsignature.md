<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/agentcardsignature?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-04-28 -->

# agentCardSignature resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Important

**Upcoming change to Agent Registry APIs**

Starting May 2026, the Agent Registry APIs in Microsoft Graph will be replaced by the [Agent Registry APIs powered by Microsoft Agent 365](https://learn.microsoft.com/en-us/microsoft-agent-365/admin/graph-api). This change consolidates agent management experiences to make it easier to observe, govern, and secure all agents in your tenant. We recommend that you plan to migrate to the new Agent 365-based APIs when they are released. Learn more about [Agent Registry convergence with Microsoft Agent 365](https://learn.microsoft.com/en-us/entra/agent-id/agent-registry-convergence).

Represents a JWS signature of an agent card, as defined in the [agentInstance](https://learn.microsoft.com/en-us/graph/api/resources/agentinstance?view=graph-rest-beta) object. This follows the JSON format of an RFC 7515 JSON Web Signature \(JWS\).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| header | [jwsHeader](https://learn.microsoft.com/en-us/graph/api/resources/jwsheader?view=graph-rest-beta) | The unprotected JWS header values. |
| protected | String | The protected JWS header for the signature. This is a Base64url-encoded JSON object, as per RFC 7515. |
| signature | String | The computed signature, Base64url-encoded. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.agentCardSignature",
  "protected": "String",
  "signature": "String",
  "header": {
    "@odata.type": "microsoft.graph.jwsHeader"
  }
}
```
