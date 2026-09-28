<!-- Source: https://learn.microsoft.com/en-us/graph/api/trustframework-post-keysets?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create trustFrameworkKeySet

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [trustFrameworkKeySet](https://learn.microsoft.com/en-us/graph/api/resources/trustframeworkkeyset?view=graph-rest-beta). The ID of the **trustFrameworkKeySet** is expected in the create request; however, it can be modified by the service. The modified ID will be available in the response and in the location header.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | TrustFrameworkKeySet.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | TrustFrameworkKeySet.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the admin must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *B2C IEF Keyset Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
POST /trustFramework/keySets
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of a [trustFrameworkKeySet](https://learn.microsoft.com/en-us/graph/api/resources/trustframeworkkeyset?view=graph-rest-beta) object.

## Response

If successful, this method returns a `201 Created` response code, a location header for the newly created object, and a new [trustFrameworkKeySet](https://learn.microsoft.com/en-us/graph/api/resources/trustframeworkkeyset?view=graph-rest-beta) object in the response body.

## Examples

### Example 1: Create an empty keyset

This is one of the most useful operations. First, you create an empty keyset. Then, in the new keyset, you can generate a key, upload a manual secret, and upload a certificate or a PKCS12 key.

#### Request

The following example shows the request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/beta/trustFramework/keySets
Content-type: application/json

{
  "id": "keyset1"  
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new TrustFrameworkKeySet
{
	Id = "keyset1",
	Keys = new List<TrustFrameworkKey>
	{
		new TrustFrameworkKey
		{
			K = "k-value",
			X5c = new List<string>
			{
				"x5c-value",
			},
			X5t = "x5t-value",
			Kty = "kty-value",
			Use = "use-value",
			Exp = 99L,
			Nbf = 99L,
			Kid = "kid-value",
			E = "e-value",
			N = "n-value",
			D = "d-value",
			P = "p-value",
			Q = "q-value",
			Dp = "dp-value",
			Dq = "dq-value",
			Qi = "qi-value",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.TrustFramework.KeySets.PostAsync(requestBody);
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
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewTrustFrameworkKeySet()
id := "keyset1"
requestBody.SetId(&id) 


trustFrameworkKey := graphmodels.NewTrustFrameworkKey()
k := "k-value"
trustFrameworkKey.SetK(&k) 
x5c := []string {
	"x5c-value",
}
trustFrameworkKey.SetX5c(x5c)
x5t := "x5t-value"
trustFrameworkKey.SetX5t(&x5t) 
kty := "kty-value"
trustFrameworkKey.SetKty(&kty) 
use := "use-value"
trustFrameworkKey.SetUse(&use) 
exp := int64(99)
trustFrameworkKey.SetExp(&exp) 
nbf := int64(99)
trustFrameworkKey.SetNbf(&nbf) 
kid := "kid-value"
trustFrameworkKey.SetKid(&kid) 
e := "e-value"
trustFrameworkKey.SetE(&e) 
n := "n-value"
trustFrameworkKey.SetN(&n) 
d := "d-value"
trustFrameworkKey.SetD(&d) 
p := "p-value"
trustFrameworkKey.SetP(&p) 
q := "q-value"
trustFrameworkKey.SetQ(&q) 
dp := "dp-value"
trustFrameworkKey.SetDp(&dp) 
dq := "dq-value"
trustFrameworkKey.SetDq(&dq) 
qi := "qi-value"
trustFrameworkKey.SetQi(&qi) 

keys := []graphmodels.TrustFrameworkKeyable {
	trustFrameworkKey,
}
requestBody.SetKeys(keys)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
keySets, err := graphClient.TrustFramework().KeySets().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

TrustFrameworkKeySet trustFrameworkKeySet = new TrustFrameworkKeySet();
trustFrameworkKeySet.setId("keyset1");
LinkedList<TrustFrameworkKey> keys = new LinkedList<TrustFrameworkKey>();
TrustFrameworkKey trustFrameworkKey = new TrustFrameworkKey();
trustFrameworkKey.setK("k-value");
LinkedList<String> x5c = new LinkedList<String>();
x5c.add("x5c-value");
trustFrameworkKey.setX5c(x5c);
trustFrameworkKey.setX5t("x5t-value");
trustFrameworkKey.setKty("kty-value");
trustFrameworkKey.setUse("use-value");
trustFrameworkKey.setExp(99L);
trustFrameworkKey.setNbf(99L);
trustFrameworkKey.setKid("kid-value");
trustFrameworkKey.setE("e-value");
trustFrameworkKey.setN("n-value");
trustFrameworkKey.setD("d-value");
trustFrameworkKey.setP("p-value");
trustFrameworkKey.setQ("q-value");
trustFrameworkKey.setDp("dp-value");
trustFrameworkKey.setDq("dq-value");
trustFrameworkKey.setQi("qi-value");
keys.add(trustFrameworkKey);
trustFrameworkKeySet.setKeys(keys);
TrustFrameworkKeySet result = graphClient.trustFramework().keySets().post(trustFrameworkKeySet);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const trustFrameworkKeySet = {
  id: 'keyset1',
  keys: [
    {
      k: 'k-value',
      x5c: [
        'x5c-value'
      ],
      x5t: 'x5t-value',
      kty: 'kty-value',
      use: 'use-value',
      exp: 99,
      nbf: 99,
      kid: 'kid-value',
      e: 'e-value',
      n: 'n-value',
      d: 'd-value',
      p: 'p-value',
      q: 'q-value',
      dp: 'dp-value',
      dq: 'dq-value',
      qi: 'qi-value'
    }
  ]
};

await client.api('/trustFramework/keySets')
	.version('beta')
	.post(trustFrameworkKeySet);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\TrustFrameworkKeySet;
use Microsoft\Graph\Beta\Generated\Models\TrustFrameworkKey;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new TrustFrameworkKeySet();
$requestBody->setId('keyset1');
$keysTrustFrameworkKey1 = new TrustFrameworkKey();
$keysTrustFrameworkKey1->setK('k-value');
$keysTrustFrameworkKey1->setX5c(['x5c-value', 	]);
$keysTrustFrameworkKey1->setX5t('x5t-value');
$keysTrustFrameworkKey1->setKty('kty-value');
$keysTrustFrameworkKey1->setEscapedUse('use-value');
$keysTrustFrameworkKey1->setExp(99);
$keysTrustFrameworkKey1->setNbf(99);
$keysTrustFrameworkKey1->setKid('kid-value');
$keysTrustFrameworkKey1->setE('e-value');
$keysTrustFrameworkKey1->setN('n-value');
$keysTrustFrameworkKey1->setD('d-value');
$keysTrustFrameworkKey1->setP('p-value');
$keysTrustFrameworkKey1->setQ('q-value');
$keysTrustFrameworkKey1->setDp('dp-value');
$keysTrustFrameworkKey1->setDq('dq-value');
$keysTrustFrameworkKey1->setQi('qi-value');
$keysArray []= $keysTrustFrameworkKey1;
$requestBody->setKeys($keysArray);


$result = $graphServiceClient->trustFramework()->keySets()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.SignIns

$params = @{
	id = "keyset1"
	keys = @(
		@{
			k = "k-value"
			x5c = @(
			"x5c-value"
		)
		x5t = "x5t-value"
		kty = "kty-value"
		use = "use-value"
		exp = 99
		nbf = 99
		kid = "kid-value"
		e = "e-value"
		n = "n-value"
		d = "d-value"
		p = "p-value"
		q = "q-value"
		dp = "dp-value"
		dq = "dq-value"
		qi = "qi-value"
	}
)
}

New-MgBetaTrustFrameworkKeySet -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.trust_framework_key_set import TrustFrameworkKeySet
from msgraph_beta.generated.models.trust_framework_key import TrustFrameworkKey
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = TrustFrameworkKeySet(
	id = "keyset1",
	keys = [
		TrustFrameworkKey(
			k = "k-value",
			x5c = [
				"x5c-value",
			],
			x5t = "x5t-value",
			kty = "kty-value",
			use = "use-value",
			exp = 99,
			nbf = 99,
			kid = "kid-value",
			e = "e-value",
			n = "n-value",
			d = "d-value",
			p = "p-value",
			q = "q-value",
			dp = "dp-value",
			dq = "dq-value",
			qi = "qi-value",
		),
	],
)

result = await graph_client.trust_framework.key_sets.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json
Location: /trustFramework/keySets('B2C_1A_keyset1')

{
  "id": "B2C_1A_keyset1",
  "keys": []
}
```

### Example 2: Create a keyset with a key

This is an advanced scenario where you need to know the [RFC 7517](https://tools.ietf.org/html/rfc7517#section-5) compliant JSON Web Key format of the key.

#### Request

The following example shows the request.

```http
POST https://graph.microsoft.com/beta/trustFramework/keySets
Content-type: application/json

{
  "id": "keyset1",
  "keys": [
    {
      "k": "k-value",
      "x5c": [
        "x5c-value"
      ],
      "x5t": "x5t-value",
      "kty": "kty-value",
      "use": "use-value",
      "exp": 99,
      "nbf": 99,
      "kid": "kid-value",
      "e": "e-value",
      "n": "n-value",
      "d": "d-value",
      "p": "p-value",
      "q": "q-value",
      "dp": "dp-value",
      "dq": "dq-value",
      "qi": "qi-value"
    }
  ]
}
```

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json
Location: /trustFramework/keySets('B2C_1A_keyset1')

{
  "id": "B2C_1A_keyset1",
  "keys": [
    {
      "k": "k-value",
      "x5c": [
        "x5c-value"
      ],
      "x5t": "x5t-value",
      "kty": "kty-value",
      "use": "use-value",
      "exp": 99,
      "nbf": 99,
      "kid": "kid-value",
      "e": "e-value",
      "n": "n-value",
      "d": "d-value",
      "p": "p-value",
      "q": "q-value",
      "dp": "dp-value",
      "dq": "dq-value",
      "qi": "qi-value"
    }
  ]
}
```
