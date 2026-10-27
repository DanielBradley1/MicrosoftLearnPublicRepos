<!-- Source: https://learn.microsoft.com/en-us/graph/api/tenantdatasecurityandgovernance-processcontent?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-24 -->

# tenantDataSecurityAndGovernance: processContent

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Process content from an agent interaction against tenant data protection policies. The protected agent is identified in **protectedAppMetadata.applicationLocation**, and the other parties in the interaction are identified in **activityMetadata.participants**.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Content.Process.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Content.Process.All | Not available. |

The `Content.Process.All` permission requires administrator consent.

## HTTP request

```http
POST /security/dataSecurityAndGovernance/processContent
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |
| If-None-Match | The ETag returned by [tenantProtectionScopeContainer: compute](https://learn.microsoft.com/en-us/graph/api/tenantprotectionscopecontainer-compute?view=graph-rest-beta). Optional. Use this header to determine whether the cached policy state changed. |

## Request body

In the request body, supply a JSON object with the following parameter.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| contentToProcess | [processContentRequest](https://learn.microsoft.com/en-us/graph/api/resources/processcontentrequest?view=graph-rest-beta) | The content and metadata to evaluate. Required. For agent evaluation, set **evaluationScope.type** to `agent`; specify a [policyLocationAgent](https://learn.microsoft.com/en-us/graph/api/resources/policylocationagent?view=graph-rest-beta) in **protectedAppMetadata.applicationLocation**; and include at least one concrete participant in **activityMetadata.participants**. |

## Response

If successful, this action returns a `200 OK` response code and a [processContentResponse](https://learn.microsoft.com/en-us/graph/api/resources/processcontentresponse?view=graph-rest-beta) object in the response body.

### Response headers

| Name | Description |
| :--- | :--- |
| ETag | Indicates the current policy state. If the ETag changes and **protectionScopeState** is `modified`, refresh the cached scopes by calling [tenantProtectionScopeContainer: compute](https://learn.microsoft.com/en-us/graph/api/tenantprotectionscopecontainer-compute?view=graph-rest-beta). |

## Examples

### Request

The following example evaluates a human prompt before it enters a protected agent.

```http
POST https://graph.microsoft.com/beta/security/dataSecurityAndGovernance/processContent
Authorization: Bearer {token}
Content-Type: application/json
If-None-Match: "8936456543210"

{
  "contentToProcess": {
    "contentEntries": [
      {
        "@odata.type": "microsoft.graph.processConversationMetadata",
        "identifier": "d01b09f7-b666-4ec9-9819-217a68ef1345",
        "name": "Human prompt",
        "content": {
          "@odata.type": "microsoft.graph.textContent",
          "data": "Summarize this confidential document."
        },
        "correlationId": "3691e553-9db2-4b7b-a84f-3d248d3c8335",
        "sequenceNumber": 1,
        "isTruncated": false,
        "createdDateTime": "2026-08-05T17:00:00Z",
        "modifiedDateTime": "2026-08-05T17:00:00Z"
      }
    ],
    "activityMetadata": {
      "activity": "uploadText",
      "participants": [
        {
          "@odata.type": "microsoft.graph.userParticipant",
          "value": "11111111-1111-1111-1111-111111111111"
        }
      ]
    },
    "integratedAppMetadata": {
      "name": "Agent365.Sydney",
      "version": "2026.8.5.1"
    },
    "deviceMetadata": {},
    "protectedAppMetadata": {
      "applicationLocation": {
        "@odata.type": "microsoft.graph.policyLocationAgent",
        "value": "22222222-2222-2222-2222-222222222222",
        "agentMetadata": {
          "agentAdministrativeUnitId": "bbbbbbbb-bbbb-bbbb-bbbb-bbbbbbbbbbbb",
          "agentBlueprintId": "aaaaaaaa-aaaa-aaaa-aaaa-aaaaaaaaaaaa",
          "agentCategory": "Agents.Foundry.MicrosoftAzure",
          "agentOwner": "owner@contoso.com",
          "agentPublisher": "Contoso",
          "altAgentIds": [
            "sydney-agent-22222222"
          ],
          "isEntraAgentId": true
        }
      }
    },
    "evaluationScope": {
      "type": "agent"
    }
  }
}
```

### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json
ETag: "8936456543210"

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#microsoft.graph.processContentResponse",
  "@odata.type": "#microsoft.graph.processContentResponse",
  "protectionScopeState": "notModified",
  "policyActions": [
    {
      "@odata.type": "#microsoft.graph.restrictAccessAction",
      "action": "restrictAccess",
      "restrictionAction": "block"
    }
  ],
  "processingErrors": []
}
```
