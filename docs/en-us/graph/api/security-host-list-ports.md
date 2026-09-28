<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-host-list-ports?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-05 -->

# List hostPorts

Namespace: microsoft.graph.security

Note

The Microsoft Graph API for Microsoft Defender Threat Intelligence requires an [active Defender Threat Intelligence Portal license and API add-on license](https://go.microsoft.com/fwlink/?linkid=2235706) for the tenant.

Get the list of [hostPort](https://learn.microsoft.com/en-us/graph/api/resources/security-hostport?view=graph-rest-1.0) resources associated with a [host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | ThreatIntelligence.Read.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | ThreatIntelligence.Read.All | Not available. |

## HTTP request

```http
GET /security/threatIntelligence/hosts/{hostId}/ports
```

## Optional query parameters

This method supports the `$count`, `$skip`, `$top`, `$select`, and `$expand` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

The following properties can be used for `$select` calls.

| Property | Example | Notes |
| :--- | :--- | :--- |
| All [hostPort](https://learn.microsoft.com/en-us/graph/api/resources/security-hostport?view=graph-rest-1.0) properties | `$select=id,firstSeenDateTime` | Use the name as it appears in the [hostPort](https://learn.microsoft.com/en-us/graph/api/resources/security-hostport?view=graph-rest-1.0) resource. |
| mostRecentSslCertificate | `$select=mostRecentSslCertificate` | You can't use `$select` on nested properties \(for example, `mostRecentSslCertificate/id`\). |
| host | `$select=host` | You can't use `$select` on nested properties \(for example, `host/id`\). |

The following properties can be used for `$expand` calls.

| Property | Example |
| :--- | :--- |
| mostRecentSslCertificate | `$expand=mostRecentSslCertificate` |

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [hostPort](https://learn.microsoft.com/en-us/graph/api/resources/security-hostport?view=graph-rest-1.0) objects in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/v1.0/security/threatIntelligence/hosts/8.8.8.8/ports
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.ThreatIntelligence.Hosts["{host-id}"].Ports.GetAsync();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
ports, err := graphClient.Security().ThreatIntelligence().Hosts().ByHostId("host-id").Ports().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.security.HostPortCollectionResponse result = graphClient.security().threatIntelligence().hosts().byHostId("{host-id}").ports().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let ports = await client.api('/security/threatIntelligence/hosts/8.8.8.8/ports')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->security()->threatIntelligence()->hosts()->byHostId('host-id')->ports()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.security.threat_intelligence.hosts.by_host_id('host-id').ports.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "id": "tKhoxnUMGirrHqYiMpsdaQRDZKBnXrao",
      "port": 443,
      "firstSeenDateTime": "2016-12-06T20:23:38.00Z",
      "lastSeenDateTime": "2023-07-18T23:24:01.00Z",
      "lastScanDateTime": "2023-07-18T23:24:29.00Z",
      "timesObserved": 15590,
      "status": "open",
      "protocol": "tcp",
      "banners": [
        {
          "banner": "HTTP/1.1 302 Found\r\nX-Content-Type-Options:...",
          "firstSeenDateTime": "2023-06-21T00:49:23.00Z",
          "lastSeenDateTime": "2023-07-18T15:31:57.00Z",
          "scanProtocol": "http_raw",
          "timesObserved": 2
        },
        {
          "banner": "HTTP/1.1 302 Found\r\nX-Content-Type-Options:...",
          "firstSeenDateTime": "2021-03-12T15:38:42.00Z",
          "lastSeenDateTime": "2023-07-18T15:22:16.00Z",
          "scanProtocol": "http_raw",
          "timesObserved": 2975
        }
      ],
      "services": [
        {
          "firstSeenDateTime": "2020-10-28T22:39:51.00Z",
          "lastSeenDateTime": "2023-07-18T22:13:54.00Z",
          "isRecent": true,
          "component": {
            "id": "EVfwHhqkUQESmqrKSFHobDUHDAKBsWLf",
            "name": "scaffolding on HTTPServer2",
            "version": "",
            "category": "Server"
          }
        },
        {
          "firstSeenDateTime": "2022-06-26T04:29:25.00Z",
          "lastSeenDateTime": "2023-07-18T00:54:13.00Z",
          "isRecent": false,
          "component": {
            "id": "ZobhjJgOwebxpsXdCUjfTpshygqgcfJj",
            "name": "nginx",
            "version": "1.18.0",
            "category": "Server"
          }
        }
      ],
      "mostRecentSslCertificate": {
        "id": "ZmI5NjU1MTUwNWYxZWRiMjRkZDNiMzZmY2ZmZGI3NjU4MzNiODExOA=="
      },
      "host": {
        "id": "85.13.139.18"
      }
    }
  ]
}
```
