<!-- Source: https://learn.microsoft.com/en-us/graph/api/networkaccess-logs-list-connections?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-15 -->

# List connections

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get a list of [connection](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-connection?view=graph-rest-beta) objects and their properties.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | NetworkAccess-Reports.Read.All | NetworkAccess.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | NetworkAccess-Reports.Read.All | NetworkAccess.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Global Secure Access Log Reader
- Global Secure Access Administrator
- Security Administrator

## HTTP request

```http
GET /networkAccess/logs/connections
```

## Optional query parameters

This method supports the following OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

| Name | Syntax | Notes |
| :--- | :--- | :--- |
| Server-side pagination | @odata.nextLink=https://graph.microsoft.com/beta/networkAccess/logs/connections?$skiptoken="generatedtoken" | The page size defaults to and is limited to 1000. |
| Filter | /logs/connections?$filter=status eq 'active' | All properties are filterable. Filter by status, trafficType, deviceCategory, and other connection properties. |
| Sort | /logs/connections?$orderby=createdDateTime desc | You can order by all properties. Sort by createdDateTime, transactionCount, and other properties. |
| Top | /logs/connections?$top=50 | Limit the number of results. Maximum value is 1000. |

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [microsoft.graph.networkaccess.connection](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-connection?view=graph-rest-beta) objects in the response body.

## Examples

### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/beta/networkAccess/logs/connections
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.NetworkAccess.Logs.Connections.GetAsync();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
connections, err := graphClient.NetworkAccess().Logs().Connections().Get(context.Background(), nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.networkaccess.ConnectionCollectionResponse result = graphClient.networkAccess().logs().connections().get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let connections = await client.api('/networkAccess/logs/connections')
	.version('beta')
	.get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->networkAccess()->logs()->connections()->get()->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.NetworkAccess

Get-MgBetaNetworkAccessLogConnection
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.network_access.logs.connections.get()
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.networkaccess.connection",
      "id": "6e3f9793-04a3-9473-f647-29adc069debb",
      "createdDateTime": "2025-04-20T10:00:00Z",
      "tenantId": "contoso.onmicrosoft.com",
      "lastUpdateDateTime": "2025-04-20T10:15:00Z",
      "endDateTime": "2025-04-20T10:30:00Z",
      "status": "active",
      "trafficType": "internet",
      "transactionCount": 10,
      "transactionBlockCount": 1,
      "sentBytes": 15360,
      "receivedBytes": 30720,
      "destinationIp": "13.107.6.152",
      "destinationPort": 443,
      "destinationFqdn": "graph.microsoft.com",
      "userId": "87d349ed-44d7-43e1-9a83-5f2406dee5bd",
      "sourceIp": "192.168.1.100",
      "sourcePort": 54321,
      "initiatingProcessName": "msedge.exe",
      "deviceId": "5b7c0300-45c3-487c-a6d3-a3098cb6e51b",
      "deviceOperatingSystem": "Windows",
      "deviceOperatingSystemVersion": "10.0.19045",
      "agentVersion": "1.0.2307.15",
      "applicationSnapshot": {
        "@odata.type": "microsoft.graph.networkaccess.applicationSnapshot",
        "appId": "00000003-0000-0000-c000-000000000000"
      },
      "privateAccessDetails": {
        "@odata.type": "microsoft.graph.networkaccess.privateAccessDetails",
        "connectorId": "e1a83a2c-5689-4f1c-b8ba-698606c784c9",
        "connectorName": "connector-1",
        "connectorIp": "10.0.0.100",
        "connectionStatus": "active",
        "accessType": "privateAccess",
        "processingRegion": "westus2"
      },
      "deviceCategory": "client",
      "userPrincipalName": "johndoe@contoso.com",
      "transportProtocol": "tcp",
      "networkProtocol": "ipv4",
      "popProcessingRegion": "westus2",
      "homeTenantId": "253ba0d4-b3b0-4825-8cd8-0f5338fade6a",
      "crossTenantAccessType": "b2bCollaboration",
      "deviceJoinType": "microsoftEntraJoined"
    },
    {
      "@odata.type": "#microsoft.graph.networkaccess.connection",
      "id": "7f4e8694-15b4-8584-g758-30bdc179efcc",
      "createdDateTime": "2025-04-20T10:05:00Z",
      "tenantId": "contoso.onmicrosoft.com",
      "lastUpdateDateTime": "2025-04-20T10:20:00Z",
      "status": "active",
      "trafficType": "microsoft365",
      "transactionCount": 5,
      "transactionBlockCount": 0,
      "sentBytes": 8192,
      "receivedBytes": 16384,
      "destinationIp": "40.99.4.10",
      "destinationPort": 443,
      "destinationFqdn": "outlook.office365.com",
      "userId": "87d349ed-44d7-43e1-9a83-5f2406dee5bd",
      "sourceIp": "192.168.1.100",
      "sourcePort": 54322,
      "initiatingProcessName": "outlook.exe",
      "deviceId": "5b7c0300-45c3-487c-a6d3-a3098cb6e51b",
      "deviceCategory": "client",
      "userPrincipalName": "johndoe@contoso.com",
      "transportProtocol": "tcp",
      "networkProtocol": "ipv4",
      "popProcessingRegion": "westus2",
      "homeTenantId": null,
      "crossTenantAccessType": "none",
      "deviceJoinType": "none"
    }
  ]
}
```
