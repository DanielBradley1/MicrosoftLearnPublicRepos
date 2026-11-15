<!-- Source: https://learn.microsoft.com/en-us/graph/api/serviceactivity-getmetricsforagentidautonomoussigninsuccess?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# serviceActivity: getMetricsForAgentIdAutonomousSignInSuccess

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Retrieve the number of completed autonomous sign-ins by Agent IDs during a specified time period.

In Agent ID autonomous sign-ins, the agent signs in and acts as itself, including both Agent ID instances and designated service principals. These sign-ins are distinct from Agent ID interactive sign-ins, in which agents sign in on behalf of human users.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Reports.Read.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Reports.Read.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Global Reader
- Reports Reader
- Security Reader
- Security Administrator
- Security Operator

## HTTP request

```http
GET /reports/serviceActivity/getMetricsForAgentIdAutonomousSignInSuccess(inclusiveIntervalStartDateTime={inclusiveIntervalStartDateTime},exclusiveIntervalEndDateTime={exclusiveIntervalEndDateTime})
```

## Function parameters

In the request URL, provide the following query parameters with values.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| aggregationIntervalInMinutes | Int32 | Aggregation interval in minutes. The default value is `15`, which sets the data to be aggregated into 15-minute sets. Allowed values are `5`, `10`, `15`, and `30`. Optional. |
| exclusiveIntervalEndDateTime | DateTimeOffset | Set the ending date and time in UTC. Required. |
| inclusiveIntervalStartDateTime | DateTimeOffset | Set the starting date and time in UTC. The earliest start time allowed is 30 days in the past. Required. |

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | \*\*\*\*\*\* Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this function returns a `200 OK` response code and a [serviceActivityValueMetric](https://learn.microsoft.com/en-us/graph/api/resources/serviceactivityvaluemetric?view=graph-rest-beta) collection in the response body.

## Examples

### Example 1: Get autonomous sign-in success metrics

#### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/reports/serviceActivity/getMetricsForAgentIdAutonomousSignInSuccess(inclusiveIntervalStartDateTime=2023-01-01T00:00:00Z,exclusiveIntervalEndDateTime=2023-01-01T00:30:00Z,aggregationIntervalInMinutes=10)
```

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#Collection(microsoft.graph.serviceActivityValueMetric)",
  "value": [
    {
      "intervalStartDateTime": "2023-01-01T00:00:00Z",
      "value": 4
    },
    {
      "intervalStartDateTime": "2023-01-01T00:10:00Z",
      "value": 5
    },
    {
      "intervalStartDateTime": "2023-01-01T00:20:00Z",
      "value": 4
    }
  ]
}
```
