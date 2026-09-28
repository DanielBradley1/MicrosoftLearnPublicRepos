<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-threatintelligence-list-whoisrecords?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-05 -->

# List whoisRecords

Namespace: microsoft.graph.security

Note

The Microsoft Graph API for Microsoft Defender Threat Intelligence requires an [active Defender Threat Intelligence Portal license and API add-on license](https://go.microsoft.com/fwlink/?linkid=2235706) for the tenant.

Get a list of [whoisRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-whoisrecord?view=graph-rest-1.0) objects.

> **Note:** You must include the `$search` query parameter in the request URL for this API.

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
GET /security/threatIntelligence/whoisRecords?$search="{value}"
```

## Optional query parameters

This method supports the `$count`, `$orderby`, `$search`, `$select`, `$skip`, and `$top` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

| Name | Description |
| :--- | :--- |
| $count | `$count` is supported to return a holistic count of the number of [whoisRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-whoisrecord?view=graph-rest-1.0) objects. `$count` is supported as a query parameter \(`?$count=true`\) or as a path parameter \(`/$count`\). |
| $orderby | `$orderby` supports some properties of the **whoisRecord** resource. For details, see [Supported properties with $orderby](#supported-properties-with-orderby). |
| $search | `$search` is **required** in the request URL of this API. The API currently only supports searching by one field in a call. For details, see [Supported properties with $search](#supported-properties-with-search). |
| $select | `$select` is supported to limit the properties returned in this query. |
| $skip | `$skip` is supported to skip over elements in pages. Combine with `$top` to perform pagination or use the `@odata.nextLink` for server-side pagination. |
| $top | `$top` is supported to limit the number of elements per page. Combine with `$skip` to perform pagination or use the `@odata.nextLink` for server-side pagination. |

### Supported properties with $orderby

The following properties can be used for `$orderby` calls.

| Property | Example | Notes |
| :--- | :--- | :--- |
| expirationDateTime | `$orderby=expirationDateTime desc` |  |
| host/id | `$orderby=host/id asc` | The full path is required for `$orderby` usage. |
| registrationDateTime | `$orderby=registrationDateTime desc` |  |

### Supported properties with $search

The following properties can be used for `$search` calls.

| Property | Example | Notes |
| :--- | :--- | :--- |
| abuse | `$search="abuse/address/state:WA"` | The `$search` must target a specific field of the [whoisContact](https://learn.microsoft.com/en-us/graph/api/resources/security-whoiscontact?view=graph-rest-1.0). |
| admin | `$search="admin/address/state:WA"` | The `$search` must target a specific field of the [whoisContact](https://learn.microsoft.com/en-us/graph/api/resources/security-whoiscontact?view=graph-rest-1.0). |
| billing | `$search="billing/address/state:WA"` | The `$search` must target a specific field of the [whoisContact](https://learn.microsoft.com/en-us/graph/api/resources/security-whoiscontact?view=graph-rest-1.0). |
| nameservers | `$search="nameservers/host/id:contoso.com"` | The `$search` must search against as specific host ID. |
| noc | `$search="noc/address/state:WA"` | The `$search` must target a specific field of the [whoisContact](https://learn.microsoft.com/en-us/graph/api/resources/security-whoiscontact?view=graph-rest-1.0). |
| registrant | `$search="registrant/address/state:WA"` | The `$search` must target a specific field of the [whoisContact](https://learn.microsoft.com/en-us/graph/api/resources/security-whoiscontact?view=graph-rest-1.0). |
| registrar | `$search="registrar/address/state:WA"` | The `$search` must target a specific field of the [whoisContact](https://learn.microsoft.com/en-us/graph/api/resources/security-whoiscontact?view=graph-rest-1.0). |
| technical | `$search="technical/address/state:WA"` | The `$search` must target a specific field of the [whoisContact](https://learn.microsoft.com/en-us/graph/api/resources/security-whoiscontact?view=graph-rest-1.0). |
| zone | `$search="zone/address/state:WA"` | The `$search` must target a specific field of the [whoisContact](https://learn.microsoft.com/en-us/graph/api/resources/security-whoiscontact?view=graph-rest-1.0). |

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [microsoft.graph.security.whoisRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-whoisrecord?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/v1.0/security/threatIntelligence/whoisRecords?$search="admin/address/state:WA&$orderby=registrationDateTime desc"
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.ThreatIntelligence.WhoisRecords.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Search = "\"admin/address/state:WA";
	requestConfiguration.QueryParameters.Orderby = new string []{ "registrationDateTime desc"" };
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


requestSearch := "\"admin/address/state:WA"

requestParameters := &graphsecurity.ThreatIntelligenceWhoisRecordsRequestBuilderGetQueryParameters{
	Search: &requestSearch,
	Orderby: [] string {"registrationDateTime desc""},
}
configuration := &graphsecurity.ThreatIntelligenceWhoisRecordsRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
whoisRecords, err := graphClient.Security().ThreatIntelligence().WhoisRecords().Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.security.WhoisRecordCollectionResponse result = graphClient.security().threatIntelligence().whoisRecords().get(requestConfiguration -> {
	requestConfiguration.queryParameters.search = "\"admin/address/state:WA";
	requestConfiguration.queryParameters.orderby = new String []{"registrationDateTime desc""};
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Security\ThreatIntelligence\WhoisRecords\WhoisRecordsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new WhoisRecordsRequestBuilderGetRequestConfiguration();
$queryParameters = WhoisRecordsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->search = "\"admin/address/state:WA";
$queryParameters->orderby = ["registrationDateTime desc""];
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->security()->threatIntelligence()->whoisRecords()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

Get-MgSecurityThreatIntelligenceWhoisRecord -Search '"admin/address/state:WA"' -Sort "registrationDateTime desc" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.security.threat_intelligence.whois_records.whois_records_request_builder import WhoisRecordsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = WhoisRecordsRequestBuilder.WhoisRecordsRequestBuilderGetQueryParameters(
		search = "\"admin/address/state:WA",
		orderby = ["registrationDateTime desc""],
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.security.threat_intelligence.whois_records.get(request_configuration = request_configuration)
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
      "@odata.type": "#microsoft.graph.security.whoisRecord",
      "id": "Y29udG9zby5jb20kJDY5NjQ3ODEyMDc3NDY1NzI0MzM=",
      "expirationDateTime": "2023-08-31T00:00:00Z",
      "registrationDateTime": "2022-07-30T09:43:19Z",
      "firstSeenDateTime": null,
      "lastSeenDateTime": null,
      "lastUpdateDateTime": "2023-06-24T08:34:15.984Z",
      "billing": null,
      "noc": null,
      "zone": null,
      "whoisServer": "rdap.markmonitor.com",
      "domainStatus": "client update prohibited,client transfer prohibited,client delete prohibited",
      "rawWhoisText": "Registrar: \n  Handle: 1891582_DOMAIN_COM-VRSN\n  LDH Name: contoso.com\n  Nameserver: \n    LDH Name: ns1.contoso.com\n    Event: \n      Action: last changed\n...",
      "abuse": {
        "email": "noreply@contoso.com",
        "name": null,
        "organization": null,
        "telephone": "+1.5555555555",
        "fax": null,
        "address": {
          "city": null,
          "countryOrRegion": null,
          "postalCode": null,
          "state": null,
          "street": null
        }
      },
      "admin": {
        "email": "noreply@contoso.com",
        "name": "Domain Administrator",
        "organization": "Contoso Org",
        "telephone": "+1.5555555555",
        "fax": "+1.5555555555",
        "address": {
          "city": "Redmond",
          "countryOrRegion": "US",
          "postalCode": "98052",
          "state": "WA",
          "street": "123 Fake St."
        }
      },
      "registrar": {
        "email": null,
        "name": null,
        "organization": "MarkMonitor Inc.",
        "telephone": null,
        "fax": null,
        "address": null
      },
      "registrant": {
        "email": "noreply@contoso.com",
        "name": "Domain Administrator",
        "organization": "Contoso Corporation",
        "telephone": "+1.5555555555",
        "fax": "+1.5555555555",
        "address": {
          "city": "Redmond",
          "countryOrRegion": "US",
          "postalCode": "98052",
          "state": "WA",
          "street": "123 Fake St."
        }
      },
      "technical": {
        "email": "noreply@contoso.com",
        "name": "Hostmaster",
        "organization": "Contoso Corporation",
        "telephone": "+1.5555555555",
        "fax": "+1.5555555555",
        "address": {
          "city": "Redmond",
          "countryOrRegion": "US",
          "postalCode": "98052",
          "state": "WA",
          "street": "123 Fake St."
        }
      },
      "nameservers": [
        {
          "firstSeenDateTime": null,
          "lastSeenDateTime": null,
          "host": {
            "id": "ns1.contoso-dns.com"
          }
        },
        {
          "firstSeenDateTime": null,
          "lastSeenDateTime": null,
          "host": {
            "id": "ns2.contoso-dns.com"
          }
        },
        {
          "firstSeenDateTime": null,
          "lastSeenDateTime": null,
          "host": {
            "id": "ns3.contoso-dns.com"
          }
        },
        {
          "firstSeenDateTime": null,
          "lastSeenDateTime": null,
          "host": {
            "id": "ns4.contoso-dns.com"
          }
        }
      ],
      "host": {
        "id": "contoso.com"
      }
    }
  ]
}
```
