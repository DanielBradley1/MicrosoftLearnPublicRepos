<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-host-list-sslcertificates?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# List hostSslCertificates

Namespace: microsoft.graph.security

Note

The Microsoft Graph API for Microsoft Defender Threat Intelligence requires an [active Defender Threat Intelligence Portal license and API add-on license](https://go.microsoft.com/fwlink/?linkid=2235706) for the tenant.

Get a list of [hostSslCertificate](https://learn.microsoft.com/en-us/graph/api/resources/security-hostsslcertificate?view=graph-rest-1.0) objects from the [host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0) navigation property.

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
GET /security/threatIntelligence/hosts/{hostId}/sslCertificates
```

## Optional query parameters

This method supports the `$count`, `$select`, `$orderBy`, `$top`, and `$skip` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [microsoft.graph.security.hostSslCertificate](https://learn.microsoft.com/en-us/graph/api/resources/security-hostsslcertificate?view=graph-rest-1.0) objects in the response body.

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
GET https://graph.microsoft.com/v1.0/security/threatIntelligence/hosts/contoso.com/sslCertificates?$count=true&$top=1&$skip=5
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.ThreatIntelligence.Hosts["{host-id}"].SslCertificates.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Count = true;
	requestConfiguration.QueryParameters.Top = 1;
	requestConfiguration.QueryParameters.Skip = 5;
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphsecurity "github.com/microsoftgraph/msgraph-sdk-go/security"
	  //other-imports
)


requestCount := true
requestTop := int32(1)
requestSkip := int32(5)

requestParameters := &graphsecurity.ThreatIntelligenceHostsItemSslCertificatesRequestBuilderGetQueryParameters{
	Count: &requestCount,
	Top: &requestTop,
	Skip: &requestSkip,
}
configuration := &graphsecurity.ThreatIntelligenceHostsItemSslCertificatesRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
sslCertificates, err := graphClient.Security().ThreatIntelligence().Hosts().ByHostId("host-id").SslCertificates().Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.security.HostSslCertificateCollectionResponse result = graphClient.security().threatIntelligence().hosts().byHostId("{host-id}").sslCertificates().get(requestConfiguration -> {
	requestConfiguration.queryParameters.count = true;
	requestConfiguration.queryParameters.top = 1;
	requestConfiguration.queryParameters.skip = 5;
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let sslCertificates = await client.api('/security/threatIntelligence/hosts/contoso.com/sslCertificates')
	.skip(5)
	.top(1)
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Security\ThreatIntelligence\Hosts\Item\SslCertificates\SslCertificatesRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new SslCertificatesRequestBuilderGetRequestConfiguration();
$queryParameters = SslCertificatesRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->count = true;
$queryParameters->top = 1;
$queryParameters->skip = 5;
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->security()->threatIntelligence()->hosts()->byHostId('host-id')->sslCertificates()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.security.threat_intelligence.hosts.item.ssl_certificates.ssl_certificates_request_builder import SslCertificatesRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = SslCertificatesRequestBuilder.SslCertificatesRequestBuilderGetQueryParameters(
		count = True,
		top = 1,
		skip = 5,
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.security.threat_intelligence.hosts.by_host_id('host-id').ssl_certificates.get(request_configuration = request_configuration)
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
      "id": "Y29udG9zby5jb20xNTUwMGZiOTY1NTE1MDVmMWVkYjI0ZGQzYjM2ZmNmZmRiNzY1ODMzYjgxMTg=",
      "firstSeenDateTime": "2023-03-10T01:20:47.000Z",
      "lastSeenDateTime": "2023-04-02T00:00:00.000Z",
      "ports": [
        {
          "port": 80,
          "firstSeenDateTime": "2023-03-10T01:20:47.000Z",
          "lastSeenDateTime": "2023-04-02T00:00:00.000Z"
        },
        {
          "port": 3000,
          "firstSeenDateTime": "2023-03-10T01:20:47.000Z",
          "lastSeenDateTime": "2023-04-02T00:00:00.000Z"
        }
      ],
      "host": {
        "@odata.type": "#microsoft.graph.security.hostName",
        "id": "contoso.com"
      },
      "sslCertificate": {
        "@odata.context": "$metadata#microsoft.graph.security.sslCertificate",
        "id": "ZmI5NjU1MTUwNWYxZWRiMjRkZDNiMzZmY2ZmZGI3NjU4MzNiODExOA==",
        "firstSeenDateTime": "2023-03-10T01:20:47.000Z",
        "lastSeenDateTime": "2023-04-02T00:00:00.000Z",
        "fingerprint": "fb:96:55:15:05:f1:ed:b2:4d:d3:b3:6f:cf:fd:b7:65:83:3b:81:18",
        "sslVersion": "3",
        "expirationDateTime": "2024-03-03T18:56:17.000Z",
        "issueDateTime": "2023-03-09T18:56:17.000Z",
        "sha1": "fb96551505f1edb24dd3b36fcffdb765833b8118",
        "serialNumber": "1137389559885717770175191329273386705719099773",
        "subject": {
          "commonName": "microsoft.com",
          "address": {
            "city": "Redmond",
            "countryOrRegion": "US",
            "postalCode": null,
            "postOfficeBox": null,
            "state": "WA",
            "street": null,
            "type": "unknown"
          },
          "email": null,
          "givenName": null,
          "organizationName": "Microsoft Corporation",
          "organizationUnitName": null,
          "serialNumber": null,
          "surname": null,
          "alternateName": [
            "pymes.microsoft.com",
            "mac2.microsoft.com",
            "sponsors.microsoft.com",
            "oemcommunity.microsoft.com",
            "gigjam.microsoft.com",
            "businesscentral.microsoft.com"
          ]
        },
        "issuer": {
          "commonName": "Microsoft Azure TLS Issuing CA 05",
          "address": {
            "city": null,
            "countryOrRegion": "US",
            "postalCode": null,
            "postOfficeBox": null,
            "state": null,
            "street": null,
            "type": "unknown"
          },
          "email": null,
          "givenName": null,
          "organizationName": "Microsoft Corporation",
          "organizationUnitName": null,
          "serialNumber": null,
          "surname": null,
          "alternateName": []
        }
      }
    }
  ]
}
```
