<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-whoisrecord-get?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Get whoisRecord

Namespace: microsoft.graph.security

Note

The Microsoft Graph API for Microsoft Defender Threat Intelligence requires an [active Defender Threat Intelligence Portal license and API add-on license](https://go.microsoft.com/fwlink/?linkid=2235706) for the tenant.

Get the specified [whoisRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-whoisrecord?view=graph-rest-1.0) resource.

Specify the desired **whoisRecord** in one of the following two ways:

- Identify a [host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0) and get its current **whoisRecord**.
- Specify an **id** value to get the corresponding **whoisRecord**.

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

To get the current **whoisRecord** for the specified **host**:

```http
GET /security/threatIntelligence/hosts/{hostId}/whois
```

To get the specified **whoisRecord**:

```http
GET /security/threatIntelligence/whoisRecords/{whoisRecordId}
```

## Optional query parameters

This method supports the `$select` OData query parameter to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [microsoft.graph.security.whoisRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-whoisrecord?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Get the whoisRecord resource for the specified host

#### Request

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
GET https://graph.microsoft.com/v1.0/security/threatIntelligence/hosts/contoso.com/whois
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.ThreatIntelligence.Hosts["{host-id}"].Whois.GetAsync();
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
whois, err := graphClient.Security().ThreatIntelligence().Hosts().ByHostId("host-id").Whois().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.security.WhoisRecord result = graphClient.security().threatIntelligence().hosts().byHostId("{host-id}").whois().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let whoisRecord = await client.api('/security/threatIntelligence/hosts/contoso.com/whois')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->security()->threatIntelligence()->hosts()->byHostId('host-id')->whois()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

Get-MgSecurityThreatIntelligenceHostWhoi -HostId $hostId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.security.threat_intelligence.hosts.by_host_id('host-id').whois.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

---

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#microsoft.graph.security.whoisRecord",
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
    "rawWhoisText": "Registrar: \n  Handle: 1891582_DOMAIN_COM-VRSN\n  LDH Name: contoso.com\n  Nameserver: \n    LDH Name: ns1-205.azure-dns.com\n    Event: \n      Action: last changed\n...",
    "abuse": {
        "email": "abusecomplaints@markmonitor.com",
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
        "email": "domains@microsoft.com",
        "name": "Domain Administrator",
        "organization": "Microsoft Corporation",
        "telephone": "+1.5555555555",
        "fax": "+1.5555555555",
        "address": {
            "city": "Redmond",
            "countryOrRegion": "US",
            "postalCode": "98052",
            "state": "WA",
            "street": "One Microsoft Way"
        }
    },
    "registrar": {
        "email": null,
        "name": null,
        "organization": "MarkMonitor Inc.",
        "telephone": null,
        "fax": null,
        "address": {
            "city": "Meridian",
            "countryOrRegion": "US",
            "postalCode": "83646",
            "state": "ID",
            "street": "3540 E Longwing Ln"
        }
    },
    "registrant": {
        "email": "domains@microsoft.com",
        "name": "Domain Administrator",
        "organization": "Microsoft Corporation",
        "telephone": "+1.5555555555",
        "fax": "+1.5555555555",
        "address": {
            "city": "Redmond",
            "countryOrRegion": "US",
            "postalCode": "98052",
            "state": "WA",
            "street": "One Microsoft Way"
        }
    },
    "technical": {
        "email": "msnhst@microsoft.com",
        "name": "MSN Hostmaster",
        "organization": "Microsoft Corporation",
        "telephone": "+1.5555555555",
        "fax": "+1.5555555555",
        "address": {
            "city": "Redmond",
            "countryOrRegion": "US",
            "postalCode": "98052",
            "state": "WA",
            "street": "One Microsoft Way"
        }
    },
    "nameservers": [
      {
        "firstSeenDateTime": null,
        "lastSeenDateTime": null,
        "host": {
            "id": "ns1-205.azure-dns.com"
        }
      },
      {
        "firstSeenDateTime": null,
        "lastSeenDateTime": null,
        "host": {
            "id": "ns2-205.azure-dns.net"
        }
      },
      {
        "firstSeenDateTime": null,
        "lastSeenDateTime": null,
        "host": {
            "id": "ns3-205.azure-dns.org"
        }
      },
      {
        "firstSeenDateTime": null,
        "lastSeenDateTime": null,
        "host": {
            "id": "ns4-205.azure-dns.info"
        }
      }
  ],
    "host": {
        "@odata.type": "#microsoft.graph.security.host",
        "id": "contoso.com"
    }
}
```

### Example 2: Get the whoisRecord resource using its id property

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```msgraph
GET https://graph.microsoft.com/v1.0/security/threatIntelligence/whoisRecords/Y29udG9zby5jb20kJDY5NjQ3ODEyMDc3NDY1NzI0MzM=
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.ThreatIntelligence.WhoisRecords["{whoisRecord-id}"].GetAsync();
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
whoisRecords, err := graphClient.Security().ThreatIntelligence().WhoisRecords().ByWhoisRecordId("whoisRecord-id").Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.security.WhoisRecord result = graphClient.security().threatIntelligence().whoisRecords().byWhoisRecordId("{whoisRecord-id}").get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let whoisRecord = await client.api('/security/threatIntelligence/whoisRecords/Y29udG9zby5jb20kJDY5NjQ3ODEyMDc3NDY1NzI0MzM=')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->security()->threatIntelligence()->whoisRecords()->byWhoisRecordId('whoisRecord-id')->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

Get-MgSecurityThreatIntelligenceWhoisRecord -WhoisRecordId $whoisRecordId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.security.threat_intelligence.whois_records.by_whois_record_id('whoisRecord-id').get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

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
```
