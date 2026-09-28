<!-- Source: https://learn.microsoft.com/en-us/graph/api/configurationbaseline-createsnapshot?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-31 -->

# configurationBaseline: createSnapshot

Namespace: microsoft.graph

Create a [configurationSnapshotJob](https://learn.microsoft.com/en-us/graph/api/resources/configurationsnapshotjob?view=graph-rest-1.0) asynchronously. This API allows an admin to asynchronously create a snapshot and initiate the extraction of the current tenant configuration. If the snapshot job is successfully created, it indicates that the asynchronous extraction process is initiated.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | ConfigurationMonitoring.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | ConfigurationMonitoring.ReadWrite.All | Not available. |

## HTTP request

```http
POST /admin/configurationManagement/configurationSnapshots/createSnapshot
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table lists the parameters that are required when you call this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| description | String | User-friendly description of the snapshot given by the user. Optional. |
| displayName | String | User-friendly name given by the user during the creation of the snapshot. Required. |
| resources | String collection | Names of the resources for which the admin wants to create a snapshot. Required. |

## Response

If successful, this action returns a `200 OK` response code and a [configurationSnapshotJob](https://learn.microsoft.com/en-us/graph/api/resources/configurationsnapshotjob?view=graph-rest-1.0) in the response body.

## Examples

### Request

The following example shows a request that creates a snapshot with two Exchange resources.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
POST https://graph.microsoft.com/v1.0/admin/configurationManagement/configurationSnapshots/createSnapshot
Content-Type: application/json

{
  "displayName": "Snapshot Demo",
  "description": "This is Snapshot Description",
  "resources": [
    "microsoft.exchange.sharedmailbox",
    "microsoft.exchange.transportrule"
  ]
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const configurationSnapshotJob = {
  displayName: 'Snapshot Demo',
  description: 'This is Snapshot Description',
  resources: [
    'microsoft.exchange.sharedmailbox',
    'microsoft.exchange.transportrule'
  ]
};

await client.api('/admin/configurationManagement/configurationSnapshots/createSnapshot')
	.post(configurationSnapshotJob);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#microsoft.graph.configurationSnapshotJob",
  "id": "c91a1470-acc9-4585-bc03-522ae898f82f",
  "displayName": "Snapshot Demo",
  "description": "This is a snapshot description.",
  "tenantId": "2fcf1c68-b412-4c85-bfb2-cb20152a6843",
  "status": "notStarted",
  "resources": [
    "microsoft.exchange.sharedmailbox",
    "microsoft.exchange.transportrule"
  ],
  "createdDateTime": "2025-02-18T15:43:59.7935268Z",
  "completedDateTime": "0001-01-01T00:00:00Z",
  "resourceLocation": "",
  "createdBy": {
    "user": {
      "id": "98ceffcc-7c54-4227-8844-835af5a023ce",
      "displayName": "Test Contoso User"
    }
  }
}
```
