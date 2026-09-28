<!-- Source: https://learn.microsoft.com/en-us/graph/api/ipnamedlocation-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-09-10 -->

# Update ipNamedlocation

Namespace: microsoft.graph

Update the properties of an [ipNamedLocation](https://learn.microsoft.com/en-us/graph/api/resources/ipnamedlocation?view=graph-rest-1.0) object.

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
PATCH /identity/conditionalAccess/namedLocations/{id}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-type | application/json. Required. |

## Request body

In the request body, supply the values for relevant fields that should be updated. Existing properties that aren't included in the request body maintains their previous values or are recalculated based on changes to other property values. For best performance, don't include existing values that haven't changed.

You must specify the **@odata.type** as `#microsoft.graph.ipNamedLocation`.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Human-readable name of the location. |
| ipRanges | [ipRange](https://learn.microsoft.com/en-us/graph/api/resources/iprange?view=graph-rest-1.0) collection | List of IP address ranges in IPv4 CIDR format \(1.2.3.4/32\) or any allowable IPv6 format from IETF RFC5962. To retain any existing **ipRange** objects, you must add them to this object in addition to any new objects; to remove any **ipRange** objects, exclude them from this object. |
| isTrusted | Boolean | The value is `true` if this location is explicitly trusted. |

## Response

If successful, this method returns a `204 No Content` response code. It doesn't return anything in the response body.

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

```http
PATCH https://graph.microsoft.com/v1.0/identity/conditionalAccess/namedLocations/0854951d-5fc0-4eb1-b392-9b2c9d7949c2
Content-type: application/json

{
    "@odata.type": "#microsoft.graph.ipNamedLocation",
    "displayName": "Untrusted named location with only IPv4 address",
    "isTrusted": false,
    "ipRanges": [
        {
            "@odata.type": "#microsoft.graph.iPv4CidrRange",
            "cidrAddress": "6.5.4.3/18"
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
	DisplayName = "Untrusted named location with only IPv4 address",
	IsTrusted = false,
	IpRanges = new List<IpRange>
	{
		new IPv4CidrRange
		{
			OdataType = "#microsoft.graph.iPv4CidrRange",
			CidrAddress = "6.5.4.3/18",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.ConditionalAccess.NamedLocations["{namedLocation-id}"].PatchAsync(requestBody);
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
displayName := "Untrusted named location with only IPv4 address"
requestBody.SetDisplayName(&displayName) 
isTrusted := false
requestBody.SetIsTrusted(&isTrusted) 


ipRange := graphmodels.NewIPv4CidrRange()
cidrAddress := "6.5.4.3/18"
ipRange.SetCidrAddress(&cidrAddress) 

ipRanges := []graphmodels.IpRangeable {
	ipRange,
}
requestBody.SetIpRanges(ipRanges)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
namedLocations, err := graphClient.Identity().ConditionalAccess().NamedLocations().ByNamedLocationId("namedLocation-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

IpNamedLocation namedLocation = new IpNamedLocation();
namedLocation.setOdataType("#microsoft.graph.ipNamedLocation");
namedLocation.setDisplayName("Untrusted named location with only IPv4 address");
namedLocation.setIsTrusted(false);
LinkedList<IpRange> ipRanges = new LinkedList<IpRange>();
IPv4CidrRange ipRange = new IPv4CidrRange();
ipRange.setOdataType("#microsoft.graph.iPv4CidrRange");
ipRange.setCidrAddress("6.5.4.3/18");
ipRanges.add(ipRange);
namedLocation.setIpRanges(ipRanges);
NamedLocation result = graphClient.identity().conditionalAccess().namedLocations().byNamedLocationId("{namedLocation-id}").patch(namedLocation);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const namedLocation = {
    '@odata.type': '#microsoft.graph.ipNamedLocation',
    displayName: 'Untrusted named location with only IPv4 address',
    isTrusted: false,
    ipRanges: [
        {
            '@odata.type': '#microsoft.graph.iPv4CidrRange',
            cidrAddress: '6.5.4.3/18'
        }

    ]
};

await client.api('/identity/conditionalAccess/namedLocations/0854951d-5fc0-4eb1-b392-9b2c9d7949c2')
	.update(namedLocation);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\IpNamedLocation;
use Microsoft\Graph\Generated\Models\IpRange;
use Microsoft\Graph\Generated\Models\IPv4CidrRange;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new IpNamedLocation();
$requestBody->setOdataType('#microsoft.graph.ipNamedLocation');
$requestBody->setDisplayName('Untrusted named location with only IPv4 address');
$requestBody->setIsTrusted(false);
$ipRangesIpRange1 = new IPv4CidrRange();
$ipRangesIpRange1->setOdataType('#microsoft.graph.iPv4CidrRange');
$ipRangesIpRange1->setCidrAddress('6.5.4.3/18');
$ipRangesArray []= $ipRangesIpRange1;
$requestBody->setIpRanges($ipRangesArray);


$result = $graphServiceClient->identity()->conditionalAccess()->namedLocations()->byNamedLocationId('namedLocation-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	"@odata.type" = "#microsoft.graph.ipNamedLocation"
	displayName = "Untrusted named location with only IPv4 address"
	isTrusted = $false
	ipRanges = @(
		@{
			"@odata.type" = "#microsoft.graph.iPv4CidrRange"
			cidrAddress = "6.5.4.3/18"
		}
	)
}

Update-MgIdentityConditionalAccessNamedLocation -NamedLocationId $namedLocationId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.ip_named_location import IpNamedLocation
from msgraph.generated.models.ip_range import IpRange
from msgraph.generated.models.i_pv4_cidr_range import IPv4CidrRange
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = IpNamedLocation(
	odata_type = "#microsoft.graph.ipNamedLocation",
	display_name = "Untrusted named location with only IPv4 address",
	is_trusted = False,
	ip_ranges = [
		IPv4CidrRange(
			odata_type = "#microsoft.graph.iPv4CidrRange",
			cidr_address = "6.5.4.3/18",
		),
	],
)

result = await graph_client.identity.conditional_access.named_locations.by_named_location_id('namedLocation-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 204 No Content
```
