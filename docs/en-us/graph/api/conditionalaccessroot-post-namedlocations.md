<!-- Source: https://learn.microsoft.com/en-us/graph/api/conditionalaccessroot-post-namedlocations?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# Create namedLocation

Namespace: microsoft.graph

Create a new [namedLocation](https://learn.microsoft.com/en-us/graph/api/resources/namedlocation?view=graph-rest-1.0) object. Named locations can be either [ipNamedLocation](https://learn.microsoft.com/en-us/graph/api/resources/ipnamedlocation?view=graph-rest-1.0) or [countryNamedLocation](https://learn.microsoft.com/en-us/graph/api/resources/countrynamedlocation?view=graph-rest-1.0) objects.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Policy.Read.All and Policy.ReadWrite.ConditionalAccess | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Policy.Read.All and Policy.ReadWrite.ConditionalAccess | Not available. |

Important

For delegated access using work or school accounts where the signed-in user is acting on another user, they must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Security Administrator
- Conditional Access Administrator

## HTTP request

```http
POST /identity/conditionalAccess/namedLocations
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of an [ipNamedLocation](https://learn.microsoft.com/en-us/graph/api/resources/ipnamedlocation?view=graph-rest-1.0) or [countryNamedLocation](https://learn.microsoft.com/en-us/graph/api/resources/countrynamedlocation?view=graph-rest-1.0) object. You must specify the **@odata.type** of the derived type, that is, `#microsoft.graph.ipNamedLocation` for an [ipNamedLocation](https://learn.microsoft.com/en-us/graph/api/resources/ipnamedlocation?view=graph-rest-1.0) object or `#microsoft.graph.countryNamedLocation` for a [countryNamedLocation](https://learn.microsoft.com/en-us/graph/api/resources/countrynamedlocation?view=graph-rest-1.0) object.

The following table lists the properties that are required to create an [ipNamedLocation](https://learn.microsoft.com/en-us/graph/api/resources/ipnamedlocation?view=graph-rest-1.0) object.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Human-readable name of the location. Required. |
| ipRanges | [ipRange](https://learn.microsoft.com/en-us/graph/api/resources/iprange?view=graph-rest-1.0) collection | List of IP address ranges in IPv4 CIDR format \(e.g. 1.2.3.4/32\) or any allowable IPv6 format from IETF RFC596. Required. The **@odata.type** of the ipRange is also required. |

The following table lists the properties that are required to create an [countryNamedLocation](https://learn.microsoft.com/en-us/graph/api/resources/countrynamedlocation?view=graph-rest-1.0) object.

| Property | Type | Description |
| :--- | :--- | :--- |
| countriesAndRegions | String collection | List of countries and/or regions in two-letter format specified by ISO 3166-2. Required. |
| displayName | String | Human-readable name of the location. Required. |

## Response

If successful, this method returns a `201 Created`response code and a new [ipNamedLocation](https://learn.microsoft.com/en-us/graph/api/resources/ipnamedlocation?view=graph-rest-1.0) or [countryNamedLocation](https://learn.microsoft.com/en-us/graph/api/resources/countrynamedlocation?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Create an ipNamedLocation

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

```http
POST https://graph.microsoft.com/v1.0/identity/conditionalAccess/namedLocations
Content-type: application/json

{
    "@odata.type": "#microsoft.graph.ipNamedLocation",
    "displayName": "Untrusted IP named location",
    "isTrusted": false,
    "ipRanges": [
        {
            "@odata.type": "#microsoft.graph.iPv4CidrRange",
            "cidrAddress": "12.34.221.11/22"
        },
        {
            "@odata.type": "#microsoft.graph.iPv6CidrRange",
            "cidrAddress": "2001:0:9d38:90d6:0:0:0:0/63"
        }
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new IpNamedLocation
{
	OdataType = "#microsoft.graph.ipNamedLocation",
	DisplayName = "Untrusted IP named location",
	IsTrusted = false,
	IpRanges = new List<IpRange>
	{
		new IPv4CidrRange
		{
			OdataType = "#microsoft.graph.iPv4CidrRange",
			CidrAddress = "12.34.221.11/22",
		},
		new IPv6CidrRange
		{
			OdataType = "#microsoft.graph.iPv6CidrRange",
			CidrAddress = "2001:0:9d38:90d6:0:0:0:0/63",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.ConditionalAccess.NamedLocations.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewNamedLocation()
displayName := "Untrusted IP named location"
requestBody.SetDisplayName(&displayName) 
isTrusted := false
requestBody.SetIsTrusted(&isTrusted) 


ipRange := graphmodels.NewIPv4CidrRange()
cidrAddress := "12.34.221.11/22"
ipRange.SetCidrAddress(&cidrAddress) 
ipRange1 := graphmodels.NewIPv6CidrRange()
cidrAddress := "2001:0:9d38:90d6:0:0:0:0/63"
ipRange1.SetCidrAddress(&cidrAddress) 

ipRanges := []graphmodels.IpRangeable {
	ipRange,
	ipRange1,
}
requestBody.SetIpRanges(ipRanges)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
namedLocations, err := graphClient.Identity().ConditionalAccess().NamedLocations().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

IpNamedLocation namedLocation = new IpNamedLocation();
namedLocation.setOdataType("#microsoft.graph.ipNamedLocation");
namedLocation.setDisplayName("Untrusted IP named location");
namedLocation.setIsTrusted(false);
LinkedList<IpRange> ipRanges = new LinkedList<IpRange>();
IPv4CidrRange ipRange = new IPv4CidrRange();
ipRange.setOdataType("#microsoft.graph.iPv4CidrRange");
ipRange.setCidrAddress("12.34.221.11/22");
ipRanges.add(ipRange);
IPv6CidrRange ipRange1 = new IPv6CidrRange();
ipRange1.setOdataType("#microsoft.graph.iPv6CidrRange");
ipRange1.setCidrAddress("2001:0:9d38:90d6:0:0:0:0/63");
ipRanges.add(ipRange1);
namedLocation.setIpRanges(ipRanges);
NamedLocation result = graphClient.identity().conditionalAccess().namedLocations().post(namedLocation);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const namedLocation = {
    '@odata.type': '#microsoft.graph.ipNamedLocation',
    displayName: 'Untrusted IP named location',
    isTrusted: false,
    ipRanges: [
        {
            '@odata.type': '#microsoft.graph.iPv4CidrRange',
            cidrAddress: '12.34.221.11/22'
        },
        {
            '@odata.type': '#microsoft.graph.iPv6CidrRange',
            cidrAddress: '2001:0:9d38:90d6:0:0:0:0/63'
        }
    ]
};

await client.api('/identity/conditionalAccess/namedLocations')
	.post(namedLocation);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\IpNamedLocation;
use Microsoft\Graph\Generated\Models\IpRange;
use Microsoft\Graph\Generated\Models\IPv4CidrRange;
use Microsoft\Graph\Generated\Models\IPv6CidrRange;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new IpNamedLocation();
$requestBody->setOdataType('#microsoft.graph.ipNamedLocation');
$requestBody->setDisplayName('Untrusted IP named location');
$requestBody->setIsTrusted(false);
$ipRangesIpRange1 = new IPv4CidrRange();
$ipRangesIpRange1->setOdataType('#microsoft.graph.iPv4CidrRange');
$ipRangesIpRange1->setCidrAddress('12.34.221.11/22');
$ipRangesArray []= $ipRangesIpRange1;
$ipRangesIpRange2 = new IPv6CidrRange();
$ipRangesIpRange2->setOdataType('#microsoft.graph.iPv6CidrRange');
$ipRangesIpRange2->setCidrAddress('2001:0:9d38:90d6:0:0:0:0/63');
$ipRangesArray []= $ipRangesIpRange2;
$requestBody->setIpRanges($ipRangesArray);


$result = $graphServiceClient->identity()->conditionalAccess()->namedLocations()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	"@odata.type" = "#microsoft.graph.ipNamedLocation"
	displayName = "Untrusted IP named location"
	isTrusted = $false
	ipRanges = @(
		@{
			"@odata.type" = "#microsoft.graph.iPv4CidrRange"
			cidrAddress = "12.34.221.11/22"
		}
		@{
			"@odata.type" = "#microsoft.graph.iPv6CidrRange"
			cidrAddress = "2001:0:9d38:90d6:0:0:0:0/63"
		}
	)
}

New-MgIdentityConditionalAccessNamedLocation -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.ip_named_location import IpNamedLocation
from msgraph.generated.models.ip_range import IpRange
from msgraph.generated.models.i_pv4_cidr_range import IPv4CidrRange
from msgraph.generated.models.i_pv6_cidr_range import IPv6CidrRange
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = IpNamedLocation(
	odata_type = "#microsoft.graph.ipNamedLocation",
	display_name = "Untrusted IP named location",
	is_trusted = False,
	ip_ranges = [
		IPv4CidrRange(
			odata_type = "#microsoft.graph.iPv4CidrRange",
			cidr_address = "12.34.221.11/22",
		),
		IPv6CidrRange(
			odata_type = "#microsoft.graph.iPv6CidrRange",
			cidr_address = "2001:0:9d38:90d6:0:0:0:0/63",
		),
	],
)

result = await graph_client.identity.conditional_access.named_locations.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#namedLocations/$entity",
    "@odata.type": "#microsoft.graph.ipNamedLocation",
    "id": "0854951d-5fc0-4eb1-b392-9b2c9d7949c2",
    "displayName": "Untrusted IP named location",
    "modifiedDateTime": "2019-09-04T01:11:34.9387578Z",
    "createdDateTime": "2019-09-04T01:11:34.9387578Z",
    "isTrusted": false,
    "ipRanges": [
        {
            "@odata.type": "#microsoft.graph.iPv4CidrRange",
            "cidrAddress": "12.34.221.11/22"
        },
        {
            "@odata.type": "#microsoft.graph.iPv6CidrRange",
            "cidrAddress": "2001:0:9d38:90d6:0:0:0:0/63"
        }
    ]
}
```

### Example 2: Create a countryNamedLocation

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

```http
POST https://graph.microsoft.com/v1.0/identity/conditionalAccess/namedLocations
Content-type: application/json

{
    "@odata.type": "#microsoft.graph.countryNamedLocation",
    "displayName": "Named location with unknown countries and regions",
    "countriesAndRegions": [
        "US",
        "GB"
    ],
    "includeUnknownCountriesAndRegions": true
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new CountryNamedLocation
{
	OdataType = "#microsoft.graph.countryNamedLocation",
	DisplayName = "Named location with unknown countries and regions",
	CountriesAndRegions = new List<string>
	{
		"US",
		"GB",
	},
	IncludeUnknownCountriesAndRegions = true,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.ConditionalAccess.NamedLocations.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewNamedLocation()
displayName := "Named location with unknown countries and regions"
requestBody.SetDisplayName(&displayName) 
countriesAndRegions := []string {
	"US",
	"GB",
}
requestBody.SetCountriesAndRegions(countriesAndRegions)
includeUnknownCountriesAndRegions := true
requestBody.SetIncludeUnknownCountriesAndRegions(&includeUnknownCountriesAndRegions) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
namedLocations, err := graphClient.Identity().ConditionalAccess().NamedLocations().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

CountryNamedLocation namedLocation = new CountryNamedLocation();
namedLocation.setOdataType("#microsoft.graph.countryNamedLocation");
namedLocation.setDisplayName("Named location with unknown countries and regions");
LinkedList<String> countriesAndRegions = new LinkedList<String>();
countriesAndRegions.add("US");
countriesAndRegions.add("GB");
namedLocation.setCountriesAndRegions(countriesAndRegions);
namedLocation.setIncludeUnknownCountriesAndRegions(true);
NamedLocation result = graphClient.identity().conditionalAccess().namedLocations().post(namedLocation);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const namedLocation = {
    '@odata.type': '#microsoft.graph.countryNamedLocation',
    displayName: 'Named location with unknown countries and regions',
    countriesAndRegions: [
        'US',
        'GB'
    ],
    includeUnknownCountriesAndRegions: true
};

await client.api('/identity/conditionalAccess/namedLocations')
	.post(namedLocation);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\CountryNamedLocation;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CountryNamedLocation();
$requestBody->setOdataType('#microsoft.graph.countryNamedLocation');
$requestBody->setDisplayName('Named location with unknown countries and regions');
$requestBody->setCountriesAndRegions(['US', 'GB', 	]);
$requestBody->setIncludeUnknownCountriesAndRegions(true);

$result = $graphServiceClient->identity()->conditionalAccess()->namedLocations()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	"@odata.type" = "#microsoft.graph.countryNamedLocation"
	displayName = "Named location with unknown countries and regions"
	countriesAndRegions = @(
	"US"
"GB"
)
includeUnknownCountriesAndRegions = $true
}

New-MgIdentityConditionalAccessNamedLocation -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.country_named_location import CountryNamedLocation
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CountryNamedLocation(
	odata_type = "#microsoft.graph.countryNamedLocation",
	display_name = "Named location with unknown countries and regions",
	countries_and_regions = [
		"US",
		"GB",
	],
	include_unknown_countries_and_regions = True,
)

result = await graph_client.identity.conditional_access.named_locations.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#namedLocations/$entity",
    "@odata.type": "#microsoft.graph.countryNamedLocation",
    "id": "1c4427fd-0885-4a3d-8b23-09a899ffa959",
    "displayName": "Named location with unknown countries and regions",
    "modifiedDateTime": "2019-09-04T01:08:02.5249255Z",
    "createdDateTime": "2019-09-04T01:08:02.5249255Z",
    "countriesAndRegions": [
        "US",
        "GB"
    ],
    "includeUnknownCountriesAndRegions": true
}
```
