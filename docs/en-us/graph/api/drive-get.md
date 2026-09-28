<!-- Source: https://learn.microsoft.com/en-us/graph/api/drive-get?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-26 -->

# Get Drive

Namespace: microsoft.graph

Retrieve the properties and relationships of a [Drive](https://learn.microsoft.com/en-us/graph/api/resources/drive?view=graph-rest-1.0) resource.

A Drive is the top-level container for a file system, such as OneDrive or SharePoint document libraries.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Files.Read | Files.Read.All, Files.ReadWrite, Files.ReadWrite.All, Sites.Read.All, Sites.ReadWrite.All, User.Read |
| Delegated \(personal Microsoft account\) | Files.Read | Files.Read.All, Files.ReadWrite, Files.ReadWrite.All |
| Application | Not supported. | Not supported. |

## HTTP request

### Get current user's OneDrive

The signed in user's drive \(when using delegated authentication\) can be accessed from the `me` singleton.

If a user's OneDrive isn't provisioned but the user has a license to use OneDrive, this request will automatically provision the user's drive, when using delegated authentication.

```http
GET /me/drive
```

### Get a user's OneDrive

To access a user's OneDrive or OneDrive for Business, your app must request the **drive** relationship on the User resource.

If a user's OneDrive isn't provisioned but the user has a license to use OneDrive, this request will automatically provision the user's drive, when using delegated authentication.

```http
GET /users/{idOrUserPrincipalName}/drive
```

#### Path parameters

| Parameter name | Value | Description |
| :--- | :--- | :--- |
| *idOrUserPrincipalName* | string | Required. The identifier for the user object who owns the OneDrive. |

### Get the document library associated with a group

To access a Group's default document library, your app requests the **drive** relationship on the Group.

```http
GET /groups/{groupId}/drive
```

#### Path parameters

| Parameter name | Value | Description |
| :--- | :--- | :--- |
| *groupId* | string | Required. The identifier for the group that owns the document library. |

### Get the document library for a site

To access a [Site's](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-1.0) default document library, your app requests the **drive** relationship on the Site.

```http
GET /sites/{siteId}/drive
```

#### Path parameters

| Parameter name | Value | Description |
| :--- | :--- | :--- |
| *siteId* | string | Required. The identifier for the site that contains the document library. |

### Get a drive by ID

If you have the unique identifier for a drive, you can access it directly from the top-level drives collection.

```
GET /drives/{driveId}
```

#### Path parameters

| Parameter name | Value | Description |
| :--- | :--- | :--- |
| *driveId* | string | Required. The identifier for the drive requested. |

## Optional query parameters

These methods support the [$select query parameter](https://learn.microsoft.com/en-us/graph/query-parameters) to shape the response.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Response

Each of these methods returns a [Drive resource](https://learn.microsoft.com/en-us/graph/api/resources/drive?view=graph-rest-1.0) for the matching drive in the response body.

### Error response codes

If the drive doesn't exist and can't be provisioned automatically \(when using delegated authentication\) an `HTTP 404` response will be returned.

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

```msgraph
GET /me/drive
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.Drive.GetAsync();
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
drive, err := graphClient.Me().Drive().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Drive result = graphClient.me().drive().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let drive = await client.api('/me/drive')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->me()->drive()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Files

# A UPN can also be used as -UserId.
Get-MgUserDefaultDrive -UserId $userId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.me.drive.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "id": "b!t18F8ybsHUq1z3LTz8xvZqP8zaSWjkFNhsME-Fepo75dTf9vQKfeRblBZjoSQrd7",
    "driveType": "business",
    "owner": {
        "user": {
            "id": "efee1b77-fb3b-4f65-99d6-274c11914d12",
            "displayName": "Ryan Gregg"
        }
    },
    "quota": {
        "deleted": 256938,
        "remaining": 1099447353539,
        "state": "normal",
        "total": 1099511627776
    }
}
```
