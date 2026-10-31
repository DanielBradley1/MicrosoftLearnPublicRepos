<!-- Source: https://learn.microsoft.com/en-us/graph/api/restorepoint-search?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-28 -->

# restorePoint: search

Namespace: microsoft.graph

Search for the [restorePoint](https://learn.microsoft.com/en-us/graph/api/resources/restorepoint?view=graph-rest-1.0) objects associated with a [protectionUnit](https://learn.microsoft.com/en-us/graph/api/resources/protectionunitbase?view=graph-rest-1.0). You can also provide **policyId** to scope the search to a protection policy and validate that the specified protection units belong to that policy.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | BackupRestore-Search.Read.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | BackupRestore-Search.Read.All | Not available. |

## HTTP request

```http
POST /solutions/backupRestore/restorePoints/search
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the following parameters.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| artifactQuery | [artifactQuery](https://learn.microsoft.com/en-us/graph/api/resources/artifactquery?view=graph-rest-1.0) | Contains an expression that specifies the criteria for search. Optional. |
| policyId | String | The identifier of the protection policy that contains the specified protection units. Optional. |
| protectionUnitIds | String collection | The ID of the protection units. Required. |
| protectionTimePeriod | [timePeriod](https://learn.microsoft.com/en-us/graph/api/resources/timeperiod?view=graph-rest-1.0) | The start and end date time of the protection period. Required. |
| restorePointPreference | [restorePointPreference](https://learn.microsoft.com/en-us/graph/api/restorepoint-search?view=graph-rest-1.0#restorepointpreference-values) | Indicates which restore point to return. The possible values are `oldest`, `latest`. Optional. |
| tags | [restorePointTags](https://learn.microsoft.com/en-us/graph/api/resources/restorepoint?view=graph-rest-1.0#restorepointtags-values) | The type of the restore point. The possible values are `None`, `FastRestore`, `UnknownFutureValue`. Optional. |

### restorePointPreference values

| Member | Description |
| :--- | :--- |
| latest | Returns the latest restore point for a given protection time period. |
| oldest | Returns the oldest restore point for a given protection time period. |

## Response

If successful, this action returns a `200 OK` response code and a [restorePointSearchResponse](https://learn.microsoft.com/en-us/graph/api/resources/restorepointsearchresponse?view=graph-rest-1.0) object in the response body.

Note

- Calls return one restore point per protection unit.
- You can include a maximum of 20 protection units in a single request, and the response isn't paginated.
- When you provide an expression for the **artifactQuery** property, you must provide only one protection unit ID in the **protectionUnitIds** property.
- When you provide **policyId**, the service validates that every protection unit belongs to the specified policy.

For a list of possible error responses, see [Backup Storage API error responses](https://learn.microsoft.com/en-us/graph/backup-storage-error-codes).

## Examples

### Example 1: Search request

#### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/v1.0/solutions/backupRestore/restorePoints/search
Content-Type: application/json

{
    "policyId": "9fec8e78-bce4-4aaf-ab1b-5451cc387264",
    "protectionUnitIds": ["23014d8c-71fe-4d00-a01a-31850bc5b42a", "43014d8c-71fe-4d00-a01a-31850bc5b42b", "63014d8c-71fe-4d00-a01a-31850bc5b42c", "83014d8c-71fe-4d00-a01a-31850bc5b42d"],
    "protectionTimePeriod": {
        "startDateTime": "2021-01-01T00:00:00Z",
        "endDateTime": "2021-01-08T00:00:00Z"
    },
    "restorePointPreference": "latest",
    "tags": "fastRestore"
}
```

#### Response

- Calls return a maximum of five restore points.
- You can include a maximum of 20 protection units in a single request, and the response isn't paginated.

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context":"/solutions/backupRestore/$metadata#restorePoints",
    "searchResponseId": "M2UyZDAwMDAwMDMxMzkzYTMyNj",
    "searchResults": [
        {
            "restorePoint": {
                "@odata.type": "#microsoft.graph.restorePoint",
                "id":"1f1fccc3-a642-4f61-bf49-f37b9a888279",
                "protectionDateTime":"2023-01-04T00:00:00Z",
                "expirationDateTime":"2024-01-04T00:00:00Z",
                "protectionUnit":{
                   "@odata.type": "#microsoft.graph.siteProtectionUnit",
                   "id":"23014d8c-71fe-4d00-a01a-31850bc5b42a",
                   "siteId":"344d9337-d8f0-456e-92cd-00a3abdd2093",
                   "policyId":"9fec8e78-bce4-4aaf-ab1b-5451cc387264"
               },
               "tags": "fastRestore"
            }
        },
        {
            "restorePoint": {
                "@odata.type": "#microsoft.graph.restorePoint",
                "id":"cdf4a823-sfde-ki2s-kmsj-clu2nsdk43ga",
                "protectionDateTime":"2023-01-03T00:00:00Z",
                "expirationDateTime":"2024-01-03T00:00:00Z",
                "protectionUnit":{
                   "@odata.type": "#microsoft.graph.siteProtectionUnit",
                   "id":"43014d8c-71fe-4d00-a01a-31850bc5b42b",
                   "siteId":"344d9337-d8f0-456e-92cd-00a3abdd2093",
                   "policyId":"9fec8e78-bce4-4aaf-ab1b-5451cc387264"
               },
               "tags": "fastRestore"
            }
        },
        {
            "restorePoint": {
                "@odata.type": "#microsoft.graph.restorePoint",
                "id":"1f1fccc3-a642-4f61-bf49-f37b9a888280",
                "protectionDateTime":"2023-01-02T00:00:00Z",
                "expirationDateTime":"2024-01-02T00:00:00Z",
                "protectionUnit":{
                   "@odata.type": "#microsoft.graph.siteProtectionUnit",
                   "id":"83014d8c-71fe-4d00-a01a-31850bc5b42c",
                   "siteId":"344d9337-d8f0-456e-92cd-00a3abdd2093",
                   "policyId":"9fec8e78-bce4-4aaf-ab1b-5451cc387264"
                },
                "tags": "fastRestore"
            }
        }
    ],
    "noResultProtectionUnitIds": ["63014d8c-71fe-4d00-a01a-31850bc5b42c"]
}
```

### Example 2: Search with artifactQuery expression

#### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/v1.0/solutions/backupRestore/restorePoints/search
Content-Type: application/json

{
  "artifactQuery": {
    "queryExpression": "(Sender -eq 'abc@contoso.com') -and (Subject -like '*Check email*' -or Subject -like ' Important') -and (HasAttachment -eq 'true') -and (PitrDumpsterActionTriggeredTime -gt '{2024-09-21T08:20:00.0000000Z}')",
    "artifactType": "message"
  },
  "protectionUnitIds": ["23014d8c-71fe-4d00-a01a-31850bc5b42a"],
  "protectionTimePeriod": {
    "startDateTime": "2021-01-01T00:00:00Z"
  },
  "restorePointPreference": "oldest"
}
```

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "/solutions/backupRestore/$metadata#restorePoints",
  "searchResponseId": "M2UyZDAwMDAwMDMxMzkzYTMyNj",
  "searchResults": [
    {
      "artifactHitCount": 26,
      "restorePoint": {
        "@odata.type": "#microsoft.graph.restorePoint",
        "id": "1f1fccc3-a642-4f61-bf49-f37b9a888279",
        "protectionDateTime": "2023-01-04T00:00:00Z",
        "expirationDateTime": "2024-01-04T00:00:00Z",
        "protectionUnit": {
          "@odata.type": "#microsoft.graph.siteProtectionUnit",
          "id": "23014d8c-71fe-4d00-a01a-31850bc5b42a",
          "siteId": "344d9337-d8f0-456e-92cd-00a3abdd2093",
          "policyId": "9fec8e78-bce4-4aaf-ab1b-5451cc387264"
        },
        "tags": "fastRestore"
      }
    }
  ]
}
```
