<!-- Source: https://learn.microsoft.com/en-us/graph/api/identitygovernance-userprocessingresult-list-reprocessedruns?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# List reprocessedRuns for userProcessingResults

Namespace: microsoft.graph.identityGovernance

List reprocessed [run](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-run?view=graph-rest-1.0) objects for a [userProcessingResult](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-userprocessingresult?view=graph-rest-1.0).

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Global Reader* and *Lifecycle Workflows Administrator* are the least privileged roles supported for this operation.

## HTTP request

```http
GET /identityGovernance/lifecycleWorkflows/deletedItems/workflows/{workflowId}/executionScope/{userProcessingResultId}/reprocessedRuns
```

## Optional query parameters

Not supported.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [run](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-run?view=graph-rest-1.0) objects in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
GET https://graph.microsoft.com/v1.0/identityGovernance/lifecycleWorkflows/deletedItems/workflows/78799042-265a-4e8f-8d61-94a2dcd2d395/executionScope/dad77a47-6eda-4de7-bc37-fe8eb5aaf17d/reprocessedRuns
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let reprocessedRuns = await client.api('/identityGovernance/lifecycleWorkflows/deletedItems/workflows/78799042-265a-4e8f-8d61-94a2dcd2d395/executionScope/dad77a47-6eda-4de7-bc37-fe8eb5aaf17d/reprocessedRuns')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://canary.graph.microsoft.com/lcwdev/$metadata#identityGovernance/lifecycleWorkflows/workflows('78799042-265a-4e8f-8d61-94a2dcd2d395')/userProcessingResults",
  "value": [
   {
   "id": "78799042-265a-4e8f-8d61-94a2dcd2d395_638927104150522341",
   "completedDateTime": null,
   "failedTasksCount": 0,
   "failedUsersCount": 0,
   "lastUpdatedDateTime": "2025-09-05T23:07:02.9206151Z",
   "processingStatus": "inProgress",
   "scheduledDateTime": "2025-09-05T23:06:55.0522341Z",
   "startedDateTime": "2025-09-05T23:07:02.9206143Z",
   "successfulUsersCount": 0,
   "totalTasksCount": 0,
   "totalUsersCount": 0,
   "totalUnprocessedTasksCount": 0,
   "workflowExecutionType": "activatedWithScope",
   "activatedOnScope": {
    "@odata.type": "#microsoft.graph.identityGovernance.activateProcessingResultScope",
    "taskScope": "allTasks",
    "processingResults": [
     {
      "id": "78799042-265a-4e8f-8d61-94a2dcd2d395_1_78799042-265a-4e8f-8d61-94a2dcd2d395_638927021459357126_0cdd8963-1c30-4632-a1f2-ac96723069cb",
      "completedDateTime": "2025-09-05T20:50:16.3660921Z",
      "failedTasksCount": 1,
      "processingStatus": "completedWithErrors",
      "scheduledDateTime": "2025-09-05T20:48:50.4546835Z",
      "startedDateTime": "2025-09-05T20:49:37.6050235Z",
      "totalTasksCount": 1,
      "totalUnprocessedTasksCount": 0,
      "workflowExecutionType": "onDemand",
      "workflowVersion": 1,
      "subject": {
       "id": "0cdd8963-1c30-4632-a1f2-ac96723069cb"
      }
     }
    ]
   },
   "reprocessedRuns": []
  }
  ]
}
```
