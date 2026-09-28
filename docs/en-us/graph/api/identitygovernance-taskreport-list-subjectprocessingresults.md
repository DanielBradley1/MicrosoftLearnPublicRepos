<!-- Source: https://learn.microsoft.com/en-us/graph/api/identitygovernance-taskreport-list-subjectprocessingresults?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-17 -->

# List subjectProcessingResults

Namespace: microsoft.graph.identityGovernance

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get a list of the [subjectProcessingResult](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-subjectprocessingresult?view=graph-rest-beta) objects associated with a [taskReport](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-taskreport?view=graph-rest-beta).

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | LifecycleWorkflows-Reports.Read.All | LifecycleWorkflows.Read.All, LifecycleWorkflows.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | LifecycleWorkflows-Reports.Read.All | LifecycleWorkflows.Read.All, LifecycleWorkflows.ReadWrite.All |

## HTTP request

```http
GET /identityGovernance/lifecycleWorkflows/workflows/{workflowId}/taskReports/{taskReportId}/subjectProcessingResults
```

## Optional query parameters

This method supports the `$count`, `$filter`, `$orderby`, and `$expand` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [subjectProcessingResult](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-subjectprocessingresult?view=graph-rest-beta) objects in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/identityGovernance/lifecycleWorkflows/workflows/14879a93-6b91-4153-b7e6-5df4a7b7c5c8/taskReports/f1a23456-789b-0cde-1234-56789abcdef0/subjectProcessingResults
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#identityGovernance/lifecycleWorkflows/workflows('14879a93-6b91-4153-b7e6-5df4a7b7c5c8')/taskReports('f1a23456-789b-0cde-1234-56789abcdef0')/subjectProcessingResults",
  "value": [
    {
      "id": "6c6d9550-4adc-117f-b307-ee188d511d67",
      "completedDateTime": "2026-05-15T10:35:00Z",
      "failedTasksCount": 0,
      "processingStatus": "completed",
      "scheduledDateTime": "2026-05-15T10:30:00Z",
      "startedDateTime": "2026-05-15T10:30:15Z",
      "totalTasksCount": 3,
      "totalUnprocessedTasksCount": 0,
      "workflowExecutionType": "extensibilityOnDemand",
      "workflowVersion": 1,
      "subject": {
        "@odata.type": "#microsoft.graph.identityGovernance.provisioningObjectWorkflowSubject",
        "id": "b74f0fae-b1f3-4c96-9bf0-d4d8a8e37cbe",
        "attributeSetEntries": []
      }
    }
  ]
}
```
