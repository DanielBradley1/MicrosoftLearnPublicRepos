<!-- Source: https://learn.microsoft.com/en-us/graph/api/directoryobject-getavailableextensionproperties?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-09-09 -->

# directoryObject: getAvailableExtensionProperties

Namespace: microsoft.graph

Return all directory extension definitions that are registered in a directory, including through multitenant apps. The following entities support extension properties:

- [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0)
- [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0)
- [administrativeUnit](https://learn.microsoft.com/en-us/graph/api/resources/administrativeunit?view=graph-rest-1.0)
- [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0)
- [device](https://learn.microsoft.com/en-us/graph/api/resources/device?view=graph-rest-1.0)
- [organization](https://learn.microsoft.com/en-us/graph/api/resources/organization?view=graph-rest-1.0)

Important

This API has a known issue and only processes results for tenants with up to 1,000 service principals; otherwise, it returns an empty response. Use [List extensionProperties \(directory extensions\)](https://learn.microsoft.com/en-us/graph/api/application-list-extensionproperty) instead.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Directory.Read.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Directory.Read.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Directory Writers
- Cloud Application Administrator
- Application Administrator

## HTTP request

```http
POST /directoryObjects/getAvailableExtensionProperties
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply JSON representation of the parameters.

The following table shows the parameters that can be used with this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| isSyncedFromOnPremises | Boolean | `true` to specify that only extension properties that are synced from the on-premises directory should be returned; `false` to specify that only extension properties that aren't synced from the on-premises directory should be returned. If the parameter is omitted, all extension properties \(both synced and nonsynced\) are returned. Optional. |

## Response

If successful, this action returns a `200 OK` response code and an [extensionProperty](https://learn.microsoft.com/en-us/graph/api/resources/extensionproperty?view=graph-rest-1.0) collection in the response body.

## Examples

### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/directoryObjects/getAvailableExtensionProperties

{

}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.DirectoryObjects.GetAvailableExtensionProperties;

var requestBody = new GetAvailableExtensionPropertiesPostRequestBody
{
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.DirectoryObjects.GetAvailableExtensionProperties.PostAsGetAvailableExtensionPropertiesPostResponseAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphdirectoryobjects "github.com/microsoftgraph/msgraph-sdk-go/directoryobjects"
	  //other-imports
)

requestBody := graphdirectoryobjects.NewGetAvailableExtensionPropertiesPostRequestBody()

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
getAvailableExtensionProperties, err := graphClient.DirectoryObjects().GetAvailableExtensionProperties().PostAsGetAvailableExtensionPropertiesPostResponse(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.directoryobjects.getavailableextensionproperties.GetAvailableExtensionPropertiesPostRequestBody getAvailableExtensionPropertiesPostRequestBody = new com.microsoft.graph.directoryobjects.getavailableextensionproperties.GetAvailableExtensionPropertiesPostRequestBody();
var result = graphClient.directoryObjects().getAvailableExtensionProperties().post(getAvailableExtensionPropertiesPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const extensionProperty = {

};

await client.api('/directoryObjects/getAvailableExtensionProperties')
	.post(extensionProperty);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\DirectoryObjects\GetAvailableExtensionProperties\GetAvailableExtensionPropertiesPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new GetAvailableExtensionPropertiesPostRequestBody();

$result = $graphServiceClient->directoryObjects()->getAvailableExtensionProperties()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.DirectoryObjects

$params = @{
}

Get-MgDirectoryObjectAvailableExtensionProperty -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.directoryobjects.get_available_extension_properties.get_available_extension_properties_post_request_body import GetAvailableExtensionPropertiesPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = GetAvailableExtensionPropertiesPostRequestBody(
)

result = await graph_client.directory_objects.get_available_extension_properties.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Collection(extensionProperty)",
  "value": [
    {
      "@odata.type": "#microsoft.graph.extensionProperty",
      "id": "d6a8bfec-893d-46e4-88fd-7db5fcc0fa62",
      "deletedDateTime": null,
      "appDisplayName": "SampleApp",
      "name": "extension_4d405aa8baa04fb494d3e0571fd9fd71_skypeId",
      "dataType": "String",
      "isSyncedFromOnPremises": false,
      "targetObjects": [
        "User"
      ]
    }
  ]
}
```
