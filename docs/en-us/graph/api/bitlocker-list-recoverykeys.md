<!-- Source: https://learn.microsoft.com/en-us/graph/api/bitlocker-list-recoverykeys?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# List recoveryKeys

Namespace: microsoft.graph

Get a list of the [bitlockerRecoveryKey](https://learn.microsoft.com/en-us/graph/api/resources/bitlockerrecoverykey?view=graph-rest-1.0) objects and their properties.

This operation doesn't return the **key** property. For information about how to read the **key** property, see [Get bitlockerRecoveryKey](https://learn.microsoft.com/en-us/graph/api/bitlockerrecoverykey-get?view=graph-rest-1.0).

You can use this API to programmatically iterate through the list of recovery keys in the tenant and identify devices with BitLocker enabled. For more information, see the sample PowerShell code in [BitLocker recovery process](https://learn.microsoft.com/en-us/windows/security/operating-system-security/data-protection/bitlocker/recovery-process#helpdesk-recovery-in-microsoft-entra-id).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | BitlockerKey.ReadBasic.All | BitlockerKey.Read.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | BitlockerKey.ReadBasic.All | BitlockerKey.Read.All |

Important

For delegated permissions, the calling user must be the registered owner of the device that the BitLocker recovery key was originally backed up from, or they must be assigned a supported [Microsoft Entra roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json).The following least privileged roles are supported for this operation.

- Cloud device administrator
- Helpdesk administrator
- Intune service administrator
- Security administrator
- Security reader
- Global reader

## HTTP request

To get a list of BitLocker keys within the tenant:

```http
GET /informationProtection/bitlocker/recoveryKeys
```

## Optional query parameters

This method supports the `$filter` OData query parameter to filter results by the **deviceId** of the device that the key was most recently backed up to. This method doesn't support `$top`. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

The response might also contain an `odata.nextLink`, which you can use to page through the result set. For details, see [Paging Microsoft Graph data](https://learn.microsoft.com/en-us/graph/paging).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| User-Agent | The identifier for the calling application. This value contains information about the operating system and the browser used. Required. |
| ocp-client-name | The name of the client application performing the API call. This header is used for debugging purposes. Optional. |
| ocp-client-version | The version of the client application performing the API call. This header is used for debugging purposes. Optional. |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [bitlockerRecoveryKey](https://learn.microsoft.com/en-us/graph/api/resources/bitlockerrecoverykey?view=graph-rest-1.0) objects in the response body.

## Examples

### Example 1: Retrieve a list of BitLocker keys in the tenant.

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
GET https://graph.microsoft.com/v1.0/informationProtection/bitlocker/recoveryKeys
User-Agent: Dsreg/10.0 (Windows 10.0.19043.1466)
ocp-client-name: My Friendly Client
ocp-client-version: 1.2
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.InformationProtection.Bitlocker.RecoveryKeys.GetAsync((requestConfiguration) =>
{
	requestConfiguration.Headers.Add("User-Agent", "Dsreg/10.0");
	requestConfiguration.Headers.Add("ocp-client-name", "My Friendly Client");
	requestConfiguration.Headers.Add("ocp-client-version", "1.2");
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  abstractions "github.com/microsoft/kiota-abstractions-go"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphinformationprotection "github.com/microsoftgraph/msgraph-sdk-go/informationprotection"
	  //other-imports
)

headers := abstractions.NewRequestHeaders()
headers.Add("User-Agent", "Dsreg/10.0")
headers.Add("ocp-client-name", "My Friendly Client")
headers.Add("ocp-client-version", "1.2")

configuration := &graphinformationprotection.BitlockerRecoveryKeysRequestBuilderGetRequestConfiguration{
	Headers: headers,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
recoveryKeys, err := graphClient.InformationProtection().Bitlocker().RecoveryKeys().Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

BitlockerRecoveryKeyCollectionResponse result = graphClient.informationProtection().bitlocker().recoveryKeys().get(requestConfiguration -> {
	requestConfiguration.headers.add("User-Agent", "Dsreg/10.0");
	requestConfiguration.headers.add("ocp-client-name", "My Friendly Client");
	requestConfiguration.headers.add("ocp-client-version", "1.2");
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let recoveryKeys = await client.api('/informationProtection/bitlocker/recoveryKeys')
	.header('User-Agent','Dsreg/10.0')
	.header('ocp-client-name','My Friendly Client')
	.header('ocp-client-version','1.2')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\InformationProtection\Bitlocker\RecoveryKeys\RecoveryKeysRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new RecoveryKeysRequestBuilderGetRequestConfiguration();
$headers = [
		'User-Agent' => 'Dsreg/10.0',
		'ocp-client-name' => 'My Friendly Client',
		'ocp-client-version' => '1.2',
	];
$requestConfiguration->headers = $headers;


$result = $graphServiceClient->informationProtection()->bitlocker()->recoveryKeys()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

Get-MgInformationProtectionBitlockerRecoveryKey
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.information_protection.bitlocker.recovery_keys.recovery_keys_request_builder import RecoveryKeysRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

request_configuration = RequestConfiguration()
request_configuration.headers.add("User-Agent", "Dsreg/10.0")
request_configuration.headers.add("ocp-client-name", "My Friendly Client")
request_configuration.headers.add("ocp-client-version", "1.2")


result = await graph_client.information_protection.bitlocker.recovery_keys.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.bitlockerRecoveryKey",
      "id": "b465e4e8-e4e8-b465-e8e4-65b4e8e465b4",
      "createdDateTime": "2020-06-15T13:45:30.0000000Z",
      "volumeType": "1",
      "deviceId": "2ef04ef1-23b0-2e00-a3a5-ab345e567ab6"
    },
    {
      "@odata.type": "#microsoft.graph.bitlockerRecoveryKey",
      "id": "6a30ed7b-247b-4d26-86b5-2f405e55ea42",
      "createdDateTime": "2020-06-15T13:45:30.0000000Z",
      "volumeType": "1",
      "deviceId": "1ab40ab2-32a8-4b00-b6b5-ba724e407de9"
    }
  ]
}
```

### Example 2: Retrieve a list of BitLocker keys filtered by **deviceId**

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
GET https://graph.microsoft.com/v1.0/informationProtection/bitlocker/recoveryKeys?$filter=deviceId eq '1ab40ab2-32a8-4b00-b6b5-ba724e407de9'
User-Agent: Dsreg/10.0 (Windows 10.0.19043.1466)
ocp-client-name: My Friendly Client
ocp-client-version: 1.2
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.InformationProtection.Bitlocker.RecoveryKeys.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "deviceId eq '1ab40ab2-32a8-4b00-b6b5-ba724e407de9'";
	requestConfiguration.Headers.Add("User-Agent", "Dsreg/10.0");
	requestConfiguration.Headers.Add("ocp-client-name", "My Friendly Client");
	requestConfiguration.Headers.Add("ocp-client-version", "1.2");
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  abstractions "github.com/microsoft/kiota-abstractions-go"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphinformationprotection "github.com/microsoftgraph/msgraph-sdk-go/informationprotection"
	  //other-imports
)

headers := abstractions.NewRequestHeaders()
headers.Add("User-Agent", "Dsreg/10.0")
headers.Add("ocp-client-name", "My Friendly Client")
headers.Add("ocp-client-version", "1.2")


requestFilter := "deviceId eq '1ab40ab2-32a8-4b00-b6b5-ba724e407de9'"

requestParameters := &graphinformationprotection.BitlockerRecoveryKeysRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
}
configuration := &graphinformationprotection.BitlockerRecoveryKeysRequestBuilderGetRequestConfiguration{
	Headers: headers,
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
recoveryKeys, err := graphClient.InformationProtection().Bitlocker().RecoveryKeys().Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

BitlockerRecoveryKeyCollectionResponse result = graphClient.informationProtection().bitlocker().recoveryKeys().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "deviceId eq '1ab40ab2-32a8-4b00-b6b5-ba724e407de9'";
	requestConfiguration.headers.add("User-Agent", "Dsreg/10.0");
	requestConfiguration.headers.add("ocp-client-name", "My Friendly Client");
	requestConfiguration.headers.add("ocp-client-version", "1.2");
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let recoveryKeys = await client.api('/informationProtection/bitlocker/recoveryKeys')
	.header('User-Agent','Dsreg/10.0')
	.header('ocp-client-name','My Friendly Client')
	.header('ocp-client-version','1.2')
	.filter('deviceId eq \'1ab40ab2-32a8-4b00-b6b5-ba724e407de9\'')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\InformationProtection\Bitlocker\RecoveryKeys\RecoveryKeysRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new RecoveryKeysRequestBuilderGetRequestConfiguration();
$headers = [
		'User-Agent' => 'Dsreg/10.0',
		'ocp-client-name' => 'My Friendly Client',
		'ocp-client-version' => '1.2',
	];
$requestConfiguration->headers = $headers;

$queryParameters = RecoveryKeysRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "deviceId eq '1ab40ab2-32a8-4b00-b6b5-ba724e407de9'";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->informationProtection()->bitlocker()->recoveryKeys()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

Get-MgInformationProtectionBitlockerRecoveryKey -Filter "deviceId eq '1ab40ab2-32a8-4b00-b6b5-ba724e407de9'" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.information_protection.bitlocker.recovery_keys.recovery_keys_request_builder import RecoveryKeysRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = RecoveryKeysRequestBuilder.RecoveryKeysRequestBuilderGetQueryParameters(
		filter = "deviceId eq '1ab40ab2-32a8-4b00-b6b5-ba724e407de9'",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)
request_configuration.headers.add("User-Agent", "Dsreg/10.0")
request_configuration.headers.add("ocp-client-name", "My Friendly Client")
request_configuration.headers.add("ocp-client-version", "1.2")


result = await graph_client.information_protection.bitlocker.recovery_keys.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.bitlockerRecoveryKey",
      "id": "b465e4e8-e4e8-b465-e8e4-65b4e8e465b4",
      "createdDateTime": "2020-06-15T13:45:30.0000000Z",
      "volumeType": "1",
      "deviceId": "1ab40ab2-32a8-4b00-b6b5-ba724e407de9"
    }
  ]
}
```
