<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-hostport-get?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Get hostPort

Namespace: microsoft.graph.security

Note

The Microsoft Graph API for Microsoft Defender Threat Intelligence requires an [active Defender Threat Intelligence Portal license and API add-on license](https://go.microsoft.com/fwlink/?linkid=2235706) for the tenant.

Read the properties and relationships of a [hostPort](https://learn.microsoft.com/en-us/graph/api/resources/security-hostport?view=graph-rest-1.0) object.

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
GET /security/threatIntelligence/hostPorts/{hostPortId}
```

## Optional query parameters

This method supports the `$select` and `$expand` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

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

If successful, this method returns a `200 OK` response code and a [hostPort](https://learn.microsoft.com/en-us/graph/api/resources/security-hostport?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/v1.0/security/threatIntelligence/hostPorts/ODUuMTMuMTM5LjE4JCQyMQ==
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.ThreatIntelligence.HostPorts["{hostPort-id}"].GetAsync();
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
hostPorts, err := graphClient.Security().ThreatIntelligence().HostPorts().ByHostPortId("hostPort-id").Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.security.HostPort result = graphClient.security().threatIntelligence().hostPorts().byHostPortId("{hostPort-id}").get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let hostPort = await client.api('/security/threatIntelligence/hostPorts/ODUuMTMuMTM5LjE4JCQyMQ==')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->security()->threatIntelligence()->hostPorts()->byHostPortId('hostPort-id')->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

Get-MgSecurityThreatIntelligenceHostPort -HostPortId $hostPortId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.security.threat_intelligence.host_ports.by_host_port_id('hostPort-id').get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": {
    "@odata.type": "#microsoft.graph.security.hostPort",
    "id": "ODUuMTMuMTM5LjE4JCQyMQ==",
    "port": 21,
    "firstSeenDateTime": "2016-17-13T08:43:41.00Z",
    "lastSeenDateTime": "2023-08-09T23:18:21.00Z",
    "lastScanDateTime": "2023-08-09T23:20:33.00Z",
    "timesObserved": 3698,
    "status": "open",
    "protocol": "tcp",
    "banners": [
      {
        "banner": "220 FTP on dd44024.kasserver.com ready\r\n",
        "firstSeenDateTime": "2021-03-08T16:21:28.00Z",
        "lastSeenDateTime": "2023-08-09T23:18:21.00Z",
        "scanProtocol": "telnet",
        "timesObserved": 274
      }
    ],
    "services": [
      {
        "firstSeenDateTime": "2021-05-26T01:05:09.00Z",
        "lastSeenDateTime": "2023-08-09T12:59:13.00Z",
        "isRecent": true,
        "component": {
          "id": "T3BlblNTSCQkOC4ycDEkJFJlbW90ZSBBY2Nlc3MkJDg1LjEzLjEzOS4xOA==",
          "name": "OpenSSH",
          "version": "8.2p1",
          "category": "Remote Access"
        }
      }
    ],
    "mostRecentSslCertificate": {
      "id": "ZDg5ZTNiZDQzZDVkOTA5YjQ3YTE4OTc3YWE5ZDVjZTM2Y2VlMTg0Yw=="
    },
    "host": {
      "id": "85.13.139.18"
    }
  }
}
```
