<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-threatintelligence-list-sslcertificates?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# List sslCertificates

Namespace: microsoft.graph.security

Note

The Microsoft Graph API for Microsoft Defender Threat Intelligence requires an [active Defender Threat Intelligence Portal license and API add-on license](https://go.microsoft.com/fwlink/?linkid=2235706) for the tenant.

Get a list of [sslCertificate](https://learn.microsoft.com/en-us/graph/api/resources/security-sslcertificate?view=graph-rest-1.0) objects and their properties.

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
GET /security/threatIntelligence/sslCertificates?$search="{property_name}:{property_value}"
```

## Optional query parameters

This method supports the `$count`, `$orderby`, `$select`, `$skip`, and `$top` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

| Name | Description |
| :--- | :--- |
| $count | Returns a holistic count of the number of [sslCertificate](https://learn.microsoft.com/en-us/graph/api/resources/security-sslcertificate?view=graph-rest-1.0) objects. You can specify `$count` as a query parameter \(`?$count=true`\) or as a path parameter \(`/$count`\). |
| $orderby | Supports some properties of the **sslCertificate** resource, as listed in [Properties that support $orderby](#properties-that-support-orderby). |
| $search | **Required** parameter. Currently supports searching by only one property in a call.  <br>Don't include any colon \(':'\) in the search string; simply remove any colon from the property value in the search string, if it exists.  <br>For more information, see [Properties that support $search](#properties-that-support-search). |
| $select | Limits the properties returned in this query. |
| $skip | Skips over elements in pages. You can combine with `$top` to perform pagination or use the URL returned in `@odata.nextLink` for server-side pagination. |
| $top | Limits the number of elements per page. You can combine with `$skip` to perform pagination or use the URL returned in `@odata.nextLink` for server-side pagination. |

### Properties that support $orderby

Use any of the following properties with the `$orderby` query parameter.

| Property | Example |
| :--- | :--- |
| firstSeenDateTime | `$orderby=firstSeenDateTime desc` |
| lastSeenDateTime | `$orderby=lastSeenDateTime desc` |

### Properties that support $search

Use any of the following properties with the `$search` query parameter.

| Property | Example | Notes |
| :--- | :--- | :--- |
| fingerprint | `$search="fingerprint:a3b59e5fe884ee1f34d98eef858e3fb662ac104a"` | **fingerprint** property values may contain a colon \(':'\). In general, don't include any colon \(:\) in a search string. Simply remove it from the property value in the search string, if it exists. |
| issuer | `$search="issuer/commonName:Contoso"` | Specify in the search string a specific property of the [sslCertificateEntity](https://learn.microsoft.com/en-us/graph/api/resources/security-sslcertificateentity?view=graph-rest-1.0) type. |
| serialNumber | `$search="serialNumber:abc123"` | Returns [sslCertificate](https://learn.microsoft.com/en-us/graph/api/resources/security-sslcertificate?view=graph-rest-1.0) resources with the **serialNumber** property matching the property value in the search string. |
| sha1 | `$search="sha1:abc123"` | Returns [sslCertificate](https://learn.microsoft.com/en-us/graph/api/resources/security-sslcertificate?view=graph-rest-1.0) resources with the **sha1** property matching the property value in the search string. |
| subject | `$search="subject/commonName:Contoso"` | Specify in the search string a specific property of the [sslCertificateEntity](https://learn.microsoft.com/en-us/graph/api/resources/security-sslcertificateentity?view=graph-rest-1.0) type. |

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [microsoft.graph.security.sslCertificate](https://learn.microsoft.com/en-us/graph/api/resources/security-sslcertificate?view=graph-rest-1.0) objects in the response body.

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
GET https://graph.microsoft.com/v1.0/security/threatIntelligence/sslCertificates?$search="subject/commonName:microsoft.com"&$count=true&$top=1
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.ThreatIntelligence.SslCertificates.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Search = "\"subject/commonName:microsoft.com\"";
	requestConfiguration.QueryParameters.Count = true;
	requestConfiguration.QueryParameters.Top = 1;
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


requestSearch := "\"subject/commonName:microsoft.com\""
requestCount := true
requestTop := int32(1)

requestParameters := &graphsecurity.ThreatIntelligenceSslCertificatesRequestBuilderGetQueryParameters{
	Search: &requestSearch,
	Count: &requestCount,
	Top: &requestTop,
}
configuration := &graphsecurity.ThreatIntelligenceSslCertificatesRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
sslCertificates, err := graphClient.Security().ThreatIntelligence().SslCertificates().Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.security.SslCertificateCollectionResponse result = graphClient.security().threatIntelligence().sslCertificates().get(requestConfiguration -> {
	requestConfiguration.queryParameters.search = "\"subject/commonName:microsoft.com\"";
	requestConfiguration.queryParameters.count = true;
	requestConfiguration.queryParameters.top = 1;
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let sslCertificates = await client.api('/security/threatIntelligence/sslCertificates')
	.search('subject/commonName:microsoft.com')
	.top(1)
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Security\ThreatIntelligence\SslCertificates\SslCertificatesRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new SslCertificatesRequestBuilderGetRequestConfiguration();
$queryParameters = SslCertificatesRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->search = "\"subject/commonName:microsoft.com\"";
$queryParameters->count = true;
$queryParameters->top = 1;
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->security()->threatIntelligence()->sslCertificates()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

Get-MgSecurityThreatIntelligenceSslCertificate -Search '"subject/commonName:microsoft.com"' -CountVariable CountVar -Top 1 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.security.threat_intelligence.ssl_certificates.ssl_certificates_request_builder import SslCertificatesRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = SslCertificatesRequestBuilder.SslCertificatesRequestBuilderGetQueryParameters(
		search = "\"subject/commonName:microsoft.com\"",
		count = True,
		top = 1,
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.security.threat_intelligence.ssl_certificates.get(request_configuration = request_configuration)
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
          "street": null
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
          "street": null
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
  ]
}
```
