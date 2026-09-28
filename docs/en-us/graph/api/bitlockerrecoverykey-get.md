<!-- Source: https://learn.microsoft.com/en-us/graph/api/bitlockerrecoverykey-get?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Get bitlockerRecoveryKey

Namespace: microsoft.graph

Retrieve the properties and relationships of a [bitlockerRecoveryKey](https://learn.microsoft.com/en-us/graph/api/resources/bitlockerrecoverykey?view=graph-rest-1.0) object.

By default, this operation doesn't return the **key** property that represents the actual recovery key. To include the **key** property in the response, use the `$select` OData query parameter. Including the `$select` query parameter triggers a Microsoft Entra audit of the operation and generates an audit log. For more information on audit logs for bitlocker recovery keys, see the KeyManagement category filter of [Microsoft Entra audit logs](https://learn.microsoft.com/en-us/azure/active-directory/reports-monitoring/concept-audit-logs).

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

To get the specified BitLocker key without returning the **key** property:

```http
GET /informationProtection/bitlocker/recoveryKeys/{bitlockeryRecoveryKeyId}
```

To get the specified BitLocker key including its **key** property:

```http
GET /informationProtection/bitlocker/recoveryKeys/{bitlockeryRecoveryKeyId}?$select=key
```

## Optional query parameters

This method supports the `$select` OData query parameter to return the **key** property. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

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

If successful, this method returns a `200 OK` response code and a [bitlockerRecoveryKey](https://learn.microsoft.com/en-us/graph/api/resources/bitlockerrecoverykey?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Get the BitLocker key by specifying the key id

#### Request

The following example shows a request. This example doesn't return the **key** property.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/v1.0/informationProtection/bitlocker/recoveryKeys/b465e4e8-e4e8-b465-e8e4-65b4e8e465b4
User-Agent: Dsreg/10.0 (Windows 10.0.19043.1466)
ocp-client-name: My Friendly Client
ocp-client-version: 1.2
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.InformationProtection.Bitlocker.RecoveryKeys["{bitlockerRecoveryKey-id}"].GetAsync((requestConfiguration) =>
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

configuration := &graphinformationprotection.BitlockerRecoveryKeysItemRequestBuilderGetRequestConfiguration{
	Headers: headers,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
recoveryKeys, err := graphClient.InformationProtection().Bitlocker().RecoveryKeys().ByBitlockerRecoveryKeyId("bitlockerRecoveryKey-id").Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

BitlockerRecoveryKey result = graphClient.informationProtection().bitlocker().recoveryKeys().byBitlockerRecoveryKeyId("{bitlockerRecoveryKey-id}").get(requestConfiguration -> {
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

let bitlockerRecoveryKey = await client.api('/informationProtection/bitlocker/recoveryKeys/b465e4e8-e4e8-b465-e8e4-65b4e8e465b4')
	.header('User-Agent','Dsreg/10.0')
	.header('ocp-client-name','My Friendly Client')
	.header('ocp-client-version','1.2')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\InformationProtection\Bitlocker\RecoveryKeys\Item\BitlockerRecoveryKeyItemRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new BitlockerRecoveryKeyItemRequestBuilderGetRequestConfiguration();
$headers = [
		'User-Agent' => 'Dsreg/10.0',
		'ocp-client-name' => 'My Friendly Client',
		'ocp-client-version' => '1.2',
	];
$requestConfiguration->headers = $headers;


$result = $graphServiceClient->informationProtection()->bitlocker()->recoveryKeys()->byBitlockerRecoveryKeyId('bitlockerRecoveryKey-id')->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

Get-MgInformationProtectionBitlockerRecoveryKey -BitlockerRecoveryKeyId $bitlockerRecoveryKeyId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.information_protection.bitlocker.recovery_keys.item.bitlocker_recovery_key_item_request_builder import BitlockerRecoveryKeyItemRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

request_configuration = RequestConfiguration()
request_configuration.headers.add("User-Agent", "Dsreg/10.0")
request_configuration.headers.add("ocp-client-name", "My Friendly Client")
request_configuration.headers.add("ocp-client-version", "1.2")


result = await graph_client.information_protection.bitlocker.recovery_keys.by_bitlocker_recovery_key_id('bitlockerRecoveryKey-id').get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "value": {
    "@odata.type": "#microsoft.graph.bitlockerRecoveryKey",
    "id": "b465e4e8-e4e8-b465-e8e4-65b4e8e465b4",
    "createdDateTime": "2020-06-15T13:45:30.0000000Z",
    "volumeType": "1",
    "deviceId": "1ab40ab2-32a8-4b00-b6b5-ba724e407de9"
  }
}
```

### Example 2: Get the BitLocker key with the **key** property

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
GET https://graph.microsoft.com/v1.0/informationProtection/bitlocker/recoveryKeys/b465e4e8-e4e8-b465-e8e4-65b4e8e465b4?$select=key
User-Agent: Dsreg/10.0 (Windows 10.0.19043.1466)
ocp-client-name: My Friendly Client
ocp-client-version: 1.2
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.InformationProtection.Bitlocker.RecoveryKeys["{bitlockerRecoveryKey-id}"].GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Select = new string []{ "key" };
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

requestParameters := &graphinformationprotection.BitlockerRecoveryKeysItemRequestBuilderGetQueryParameters{
	Select: [] string {"key"},
}
configuration := &graphinformationprotection.BitlockerRecoveryKeysItemRequestBuilderGetRequestConfiguration{
	Headers: headers,
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
recoveryKeys, err := graphClient.InformationProtection().Bitlocker().RecoveryKeys().ByBitlockerRecoveryKeyId("bitlockerRecoveryKey-id").Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

BitlockerRecoveryKey result = graphClient.informationProtection().bitlocker().recoveryKeys().byBitlockerRecoveryKeyId("{bitlockerRecoveryKey-id}").get(requestConfiguration -> {
	requestConfiguration.queryParameters.select = new String []{"key"};
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

let bitlockerRecoveryKey = await client.api('/informationProtection/bitlocker/recoveryKeys/b465e4e8-e4e8-b465-e8e4-65b4e8e465b4')
	.header('User-Agent','Dsreg/10.0')
	.header('ocp-client-name','My Friendly Client')
	.header('ocp-client-version','1.2')
	.select('key')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\InformationProtection\Bitlocker\RecoveryKeys\Item\BitlockerRecoveryKeyItemRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new BitlockerRecoveryKeyItemRequestBuilderGetRequestConfiguration();
$headers = [
		'User-Agent' => 'Dsreg/10.0',
		'ocp-client-name' => 'My Friendly Client',
		'ocp-client-version' => '1.2',
	];
$requestConfiguration->headers = $headers;

$queryParameters = BitlockerRecoveryKeyItemRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->select = ["key"];
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->informationProtection()->bitlocker()->recoveryKeys()->byBitlockerRecoveryKeyId('bitlockerRecoveryKey-id')->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

Get-MgInformationProtectionBitlockerRecoveryKey -BitlockerRecoveryKeyId $bitlockerRecoveryKeyId -Property "key" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.information_protection.bitlocker.recovery_keys.item.bitlocker_recovery_key_item_request_builder import BitlockerRecoveryKeyItemRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = BitlockerRecoveryKeyItemRequestBuilder.BitlockerRecoveryKeyItemRequestBuilderGetQueryParameters(
		select = ["key"],
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)
request_configuration.headers.add("User-Agent", "Dsreg/10.0")
request_configuration.headers.add("ocp-client-name", "My Friendly Client")
request_configuration.headers.add("ocp-client-version", "1.2")


result = await graph_client.information_protection.bitlocker.recovery_keys.by_bitlocker_recovery_key_id('bitlockerRecoveryKey-id').get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "value": {
    "@odata.type": "#microsoft.graph.bitlockerRecoveryKey",
    "id": "b465e4e8-e4e8-b465-e8e4-65b4e8e465b4",
    "createdDateTime": "String (timestamp)",
    "volumeType": "1",
    "deviceId": "1ab40ab2-32a8-4b00-b6b5-ba724e407de9",
    "key": "123456-231453-873456-213546-654678-765689-123456-324565"
  }
}
```
