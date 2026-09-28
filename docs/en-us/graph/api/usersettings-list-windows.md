<!-- Source: https://learn.microsoft.com/en-us/graph/api/usersettings-list-windows?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# List Windows settings

Namespace: microsoft.graph

Get a list of [windowsSetting](https://learn.microsoft.com/en-us/graph/api/resources/windowssetting?view=graph-rest-1.0) objects and their properties for the signed in user.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | UserWindowsSettings.Read | Not available. |
| Delegated \(personal Microsoft account\) | UserWindowsSettings.Read | Not available. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
GET /me/settings/windows
```

## Optional query parameters

This method supports the `$filter` OData query parameter to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

You can filter the results by the following properties:

- **windowsDeviceId**: A string value that represents the unique identifier of a Windows device. This identifier can be found in the response body. When you filter on **windowsDeviceId**, you can get a list of settings specific to that device. Only the equality \(`eq`\) comparison is supported for this parameter.
- **settingType**: An enumeration with the following valid values: `roaming` and `backup`. The **settingType** property allows you to narrow down the results to settings related to either roaming or backup. Only the equality \(`eq`\) comparison is supported for this parameter. For more information, see [windowsSettingType](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-1.0#windowssettingtype-values).

For more details about how to use this query parameter, see the [Examples](https://learn.microsoft.com/en-us/graph/api/usersettings-list-windows?view=graph-rest-1.0#examples) section.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Prefer | Optional. This API supports the *odata.maxpagesize* parameter through this header for pagination purposes. The minimum and maximum valid values for *odata.maxpagesize* are **1** and **200** respectively. If no value is passed, the default value is **110**. |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [windowsSetting](https://learn.microsoft.com/en-us/graph/api/resources/windowssetting?view=graph-rest-1.0) objects in the response body.

If the response contains more than one page of data, the response body will contain an `@odata.nextLink` property. This property will contain a URL that can be used to request the next page of data. The URL should be used without any modification.

## Examples

### Example 1: Request without any filter

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
GET https://graph.microsoft.com/v1.0/me/settings/windows
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.Settings.Windows.GetAsync();
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
windows, err := graphClient.Me().Settings().Windows().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

WindowsSettingCollectionResponse result = graphClient.me().settings().windows().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let windows = await client.api('/me/settings/windows')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->me()->settings()->windows()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Users

# A UPN can also be used as -UserId.
Get-MgUserSettingWindows -UserId $userId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.me.settings.windows.get()
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
      "@odata.type": "#microsoft.graph.windowsSetting",
      "id": "default$windows.data.fileexplorerclassic.searchsettings",
      "windowsDeviceId": "c9e0f7d8-2b1a-4f6e-9b7c-8e3a1a3e5b0d",
      "settingType": "backup",
      "payloadType": "windows.data.fileexplorerclassic.searchsettings",
      "instances": [
                {
                    "id": "9715f1d9-49d1-4b94-041b-443ac419d417",
                    "payload": "VGhpcyBpcyBqdXN0IGFuIGV4YW1wbGUh",
                    "lastModifiedDateTime": "2024-10-31T23:30:41Z",
                    "createdDateTime": "2024-02-12T19:34:35.223Z",
                    "expirationDateTime": "2034-02-09T19:34:33.771Z"
                }
            ]
    },
    {
      "@odata.type": "#microsoft.graph.windowsSetting",
      "id": "default$windows.data.input.devices.pensyncedsettings",
      "windowsDeviceId": "a4b9d6e7-8f3c-4d2a-b1e0-6c5f0e9a7d8b",
      "settingType": "backup",
      "payloadType": "windows.data.input.devices.pensyncedsettings",
      "instances": [
                {
                    "id": "666dcb9b-49d1-4b94-041b-443ac419d417",
                    "payload": "VGhpcyBpcyBhbm90aGVyIGp1c3QgYW4gZXhhbXBsZSE=",
                    "lastModifiedDateTime": "2024-10-31T23:30:41Z",
                    "createdDateTime": "2024-02-12T19:34:35.223Z",
                    "expirationDateTime": "2034-02-09T19:34:33.771Z"
                }
            ]
    }
  ],
  "@odata.nextLink": "https://graph.microsoft.com/v1.0/me/settings/windows?$skiptoken=eyJzZXRhZyI6ImJmY2I2ZjQwLWM5ZGQtMTFlZS05MTE3LTAxMDIwMzA1MDcwZCIsImlldGFnIjoiMDAwMDAwMDAtMDAwMC0wMDAwLTAwMDAtMDAwMDAwMDAwMDAwIiwiZW5kRVRhZyI6IjEwMDJkOGYwLWM2NTItMTRkYy05MTE3LTAxMDIwMzA1MDcwZCIsImV0YWciOiJjMDMzZjUxMC1jOWRkLTExZWUtOTExNy0wMTAyMDMwNTA3MGQiLCJsdHNsIjoiYzAzM2Y1MTAtYzlkZC0xMWVlLTkxMTctMDEwMjAzMDUwNzBkIiwibmV4dCI6dHJ1ZX0%3d"
}
```

### Example 2: Request with filter by `roaming` settingType

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
GET https://graph.microsoft.com/v1.0/me/settings/windows?$filter=settingType eq 'roaming'
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.Settings.Windows.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "settingType eq 'roaming'";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphusers "github.com/microsoftgraph/msgraph-sdk-go/users"
	  //other-imports
)


requestFilter := "settingType eq 'roaming'"

requestParameters := &graphusers.SettingsWindowsRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
}
configuration := &graphusers.SettingsWindowsRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
windows, err := graphClient.Me().Settings().Windows().Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

WindowsSettingCollectionResponse result = graphClient.me().settings().windows().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "settingType eq 'roaming'";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let windows = await client.api('/me/settings/windows')
	.filter('settingType eq \'roaming\'')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\Item\Settings\Windows\WindowsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new WindowsRequestBuilderGetRequestConfiguration();
$queryParameters = WindowsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "settingType eq 'roaming'";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->me()->settings()->windows()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Users

# A UPN can also be used as -UserId.
Get-MgUserSettingWindows -UserId $userId -Filter "settingType eq 'roaming'" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.item.settings.windows.windows_request_builder import WindowsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = WindowsRequestBuilder.WindowsRequestBuilderGetQueryParameters(
		filter = "settingType eq 'roaming'",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.me.settings.windows.get(request_configuration = request_configuration)
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
      "@odata.type": "#microsoft.graph.windowsSetting",
      "id": "default$windows.data.fileexplorerclassic.shellstatesettings",
      "settingType": "roaming",
      "payloadType": "windows.data.fileexplorerclassic.shellstatesettings",
      "instances": [
                {
                    "id": "0b3af867-49d1-4b94-041b-443ac419d417",
                    "payload": "VGhpcyBpcyBqdXN0IGFuIGV4YW1wbGUh",
                    "lastModifiedDateTime": "2024-10-31T23:30:41Z",
                    "createdDateTime": "2024-02-12T19:34:35.223Z",
                    "expirationDateTime": "2034-02-09T19:34:33.771Z"
                }
            ]
    },
    {
      "@odata.type": "#microsoft.graph.windowsSetting",
      "id": "default$windows.data.fileexplorerclassic.cabinetstatesettings",
      "settingType": "roaming",
      "payloadType": "windows.data.fileexplorerclassic.cabinetstatesettings",
      "instances": [
                {
                    "id": "5038fa1b-49d1-4b94-041b-443ac419d417",
                    "payload": "VGhpcyBpcyBhbm90aGVyIGp1c3QgYW4gZXhhbXBsZSE=",
                    "lastModifiedDateTime": "2024-10-31T23:30:41Z",
                    "createdDateTime": "2024-02-12T19:34:35.223Z",
                    "expirationDateTime": "2034-02-09T19:34:33.771Z"
                }
            ]
    }
  ]
}
```

### Example 3: Request with filter by `backup` settingType

#### Request

The following example shows a request.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```msgraph
GET https://graph.microsoft.com/v1.0/me/settings/windows?$filter=settingType eq 'backup'
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.Settings.Windows.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "settingType eq 'backup'";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphusers "github.com/microsoftgraph/msgraph-sdk-go/users"
	  //other-imports
)


requestFilter := "settingType eq 'backup'"

requestParameters := &graphusers.SettingsWindowsRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
}
configuration := &graphusers.SettingsWindowsRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
windows, err := graphClient.Me().Settings().Windows().Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

WindowsSettingCollectionResponse result = graphClient.me().settings().windows().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "settingType eq 'backup'";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let windows = await client.api('/me/settings/windows')
	.filter('settingType eq \'backup\'')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\Item\Settings\Windows\WindowsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new WindowsRequestBuilderGetRequestConfiguration();
$queryParameters = WindowsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "settingType eq 'backup'";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->me()->settings()->windows()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Users

# A UPN can also be used as -UserId.
Get-MgUserSettingWindows -UserId $userId -Filter "settingType eq 'backup'" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.item.settings.windows.windows_request_builder import WindowsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = WindowsRequestBuilder.WindowsRequestBuilderGetQueryParameters(
		filter = "settingType eq 'backup'",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.me.settings.windows.get(request_configuration = request_configuration)
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
      "@odata.type": "#microsoft.graph.windowsSetting",
      "id": "{67585f9f-ee4b-4dd8-808e-d88375d66ef7}$windows.data.apps.devicemetadata",
      "windowsDeviceId": "67585f9f-ee4b-4dd8-808e-d88375d66ef7",
      "settingType": "backup",
      "payloadType": "windows.data.apps.devicemetadata",
      "instances": [
                {
                    "id": "14b50191-10e5-4da5-9099-8c909b8458bd",
                    "payload": "VGhpcyBpcyBhbm90aGVyIGp1c3QgYW4gZXhhbXBsZSE=",
                    "lastModifiedDateTime": "2024-10-31T23:30:41Z",
                    "createdDateTime": "2024-02-12T19:34:35.223Z",
                    "expirationDateTime": "2034-02-09T19:34:33.771Z"
                }
            ]
    },
    {
      "@odata.type": "#microsoft.graph.windowsSetting",
      "id": "{55f26da7-5824-4937-9028-9bba274f049f}$windows.data.apps.devicemetadata",
      "windowsDeviceId": "55f26da7-5824-4937-9028-9bba274f049f",      
      "settingType": "backup",
      "payloadType": "windows.data.apps.devicemetadata",
      "instances": [
                {
                    "id": "da2f0307-2a8d-4242-846f-56abd95f7213",
                    "payload": "VGhpcyBpcyBqdXN0IGFuIGV4YW1wbGUh",
                    "lastModifiedDateTime": "2024-10-31T23:30:41Z",
                    "createdDateTime": "2024-02-12T19:34:35.223Z",
                    "expirationDateTime": "2034-02-09T19:34:33.771Z"
                }
            ]
    }
  ]
}
```

### Example 4: Request with filter by `windowsDeviceId`

#### Request

The following example shows a request.

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```msgraph
GET https://graph.microsoft.com/v1.0/me/settings/windows?$filter=windowsDeviceId eq '67585f9f-ee4b-4dd8-808e-d88375d66ef7'
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.Settings.Windows.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "windowsDeviceId eq '67585f9f-ee4b-4dd8-808e-d88375d66ef7'";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphusers "github.com/microsoftgraph/msgraph-sdk-go/users"
	  //other-imports
)


requestFilter := "windowsDeviceId eq '67585f9f-ee4b-4dd8-808e-d88375d66ef7'"

requestParameters := &graphusers.SettingsWindowsRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
}
configuration := &graphusers.SettingsWindowsRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
windows, err := graphClient.Me().Settings().Windows().Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

WindowsSettingCollectionResponse result = graphClient.me().settings().windows().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "windowsDeviceId eq '67585f9f-ee4b-4dd8-808e-d88375d66ef7'";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let windows = await client.api('/me/settings/windows')
	.filter('windowsDeviceId eq \'67585f9f-ee4b-4dd8-808e-d88375d66ef7\'')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\Item\Settings\Windows\WindowsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new WindowsRequestBuilderGetRequestConfiguration();
$queryParameters = WindowsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "windowsDeviceId eq '67585f9f-ee4b-4dd8-808e-d88375d66ef7'";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->me()->settings()->windows()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Users

# A UPN can also be used as -UserId.
Get-MgUserSettingWindows -UserId $userId -Filter "windowsDeviceId eq '67585f9f-ee4b-4dd8-808e-d88375d66ef7'" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.item.settings.windows.windows_request_builder import WindowsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = WindowsRequestBuilder.WindowsRequestBuilderGetQueryParameters(
		filter = "windowsDeviceId eq '67585f9f-ee4b-4dd8-808e-d88375d66ef7'",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.me.settings.windows.get(request_configuration = request_configuration)
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
      "@odata.type": "#microsoft.graph.windowsSetting",
      "id": "{67585f9f-ee4b-4dd8-808e-d88375d66ef7}$windows.data.apps.devicemetadata",
      "windowsDeviceId": "67585f9f-ee4b-4dd8-808e-d88375d66ef7",
      "settingType": "backup",
      "payloadType": "windows.data.apps.devicemetadata",
      "instances": [
                {
                    "id": "14b50191-10e5-4da5-9099-8c909b8458bd",
                    "payload": "VGhpcyBpcyBqdXN0IGFuIGV4YW1wbGUh",
                    "lastModifiedDateTime": "2024-10-31T23:30:41Z",
                    "createdDateTime": "2024-02-12T19:34:35.223Z",
                    "expirationDateTime": "2034-02-09T19:34:33.771Z"
                }
            ]
    }
  ]
}
```
