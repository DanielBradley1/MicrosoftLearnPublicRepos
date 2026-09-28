<!-- Source: https://learn.microsoft.com/en-us/graph/api/certificatebasedauthpki-upload?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-16 -->

# certificateBasedAuthPki: upload

Namespace: microsoft.graph

Append additional certificate authority details to a [certificateBasedAuthPki](https://learn.microsoft.com/en-us/graph/api/resources/certificatebasedauthpki?view=graph-rest-1.0) resource. Only one operation can run at a time and this operation can take up to 30 minutes to complete. To know whether another upload is in progress, call the [Get certificateBasedAuthPki](https://learn.microsoft.com/en-us/graph/api/certificatebasedauthpki-get?view=graph-rest-1.0). The **status** property will have the value `running`.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | PublicKeyInfrastructure.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | PublicKeyInfrastructure.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts where the signed-in user is acting on another user, they must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Privileged Authentication Administrator
- Authentication Administrator

## HTTP request

```http
POST /directory/publicKeyInfrastructure/certificateBasedAuthConfigurations/{certificateBasedAuthPkiId}/upload
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table lists the parameters that are required when you call this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| uploadUrl | String | The URL where the service can download the PKI file and populate the certificateAuthorities. This can be any http or https publicly accessible internet facing URL. |
| sha256FileHash | String | A sequence of numbers and letters to check that your copy of a downloaded update file is identical to the original. This can be computed using the [Get\_FileHash cmdlet](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-filehash). |

## Response

If successful, this action returns a `204 No Content` response code. If another upload is currently in progress, this API returns a 400 Bad Request error message. Attempting to upload a duplicate certificate results in a 400 Bad Request error code with a Duplicate Certificate exists" error message.

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
POST https://graph.microsoft.com/v1.0/directory/publicKeyInfrastructure/certificateBasedAuthConfigurations/{certificateBasedAuthPkiId}/upload
Content-Type: application/json

{
  "uploadUrl": "https://microsoft.sharepoint.com/CBA/demo/CBARootPKI.p7b",
  "sha256FileHash": "D7F9....61E6F"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.DirectoryNamespace.PublicKeyInfrastructure.CertificateBasedAuthConfigurations.Item.Upload;

var requestBody = new UploadPostRequestBody
{
	UploadUrl = "https://microsoft.sharepoint.com/CBA/demo/CBARootPKI.p7b",
	Sha256FileHash = "D7F9....61E6F",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Directory.PublicKeyInfrastructure.CertificateBasedAuthConfigurations["{certificateBasedAuthPki-id}"].Upload.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphdirectory "github.com/microsoftgraph/msgraph-sdk-go/directory"
	  //other-imports
)

requestBody := graphdirectory.NewUploadPostRequestBody()
uploadUrl := "https://microsoft.sharepoint.com/CBA/demo/CBARootPKI.p7b"
requestBody.SetUploadUrl(&uploadUrl) 
sha256FileHash := "D7F9....61E6F"
requestBody.SetSha256FileHash(&sha256FileHash) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Directory().PublicKeyInfrastructure().CertificateBasedAuthConfigurations().ByCertificateBasedAuthPkiId("certificateBasedAuthPki-id").Upload().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.directory.publickeyinfrastructure.certificatebasedauthconfigurations.item.upload.UploadPostRequestBody uploadPostRequestBody = new com.microsoft.graph.directory.publickeyinfrastructure.certificatebasedauthconfigurations.item.upload.UploadPostRequestBody();
uploadPostRequestBody.setUploadUrl("https://microsoft.sharepoint.com/CBA/demo/CBARootPKI.p7b");
uploadPostRequestBody.setSha256FileHash("D7F9....61E6F");
graphClient.directory().publicKeyInfrastructure().certificateBasedAuthConfigurations().byCertificateBasedAuthPkiId("{certificateBasedAuthPki-id}").upload().post(uploadPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const upload = {
  uploadUrl: 'https://microsoft.sharepoint.com/CBA/demo/CBARootPKI.p7b',
  sha256FileHash: 'D7F9....61E6F'
};

await client.api('/directory/publicKeyInfrastructure/certificateBasedAuthConfigurations/{certificateBasedAuthPkiId}/upload')
	.post(upload);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Directory\PublicKeyInfrastructure\CertificateBasedAuthConfigurations\Item\Upload\UploadPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new UploadPostRequestBody();
$requestBody->setUploadUrl('https://microsoft.sharepoint.com/CBA/demo/CBARootPKI.p7b');
$requestBody->setSha256FileHash('D7F9....61E6F');

$graphServiceClient->directory()->publicKeyInfrastructure()->certificateBasedAuthConfigurations()->byCertificateBasedAuthPkiId('certificateBasedAuthPki-id')->upload()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.DirectoryManagement

$params = @{
	uploadUrl = "https://microsoft.sharepoint.com/CBA/demo/CBARootPKI.p7b"
	sha256FileHash = "D7F9....61E6F"
}

Invoke-MgUploadDirectoryPublicKeyInfrastructureCertificateBasedAuthConfiguration -CertificateBasedAuthPkiId $certificateBasedAuthPkiId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.directory.publickeyinfrastructure.certificatebasedauthconfigurations.item.upload.upload_post_request_body import UploadPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = UploadPostRequestBody(
	upload_url = "https://microsoft.sharepoint.com/CBA/demo/CBARootPKI.p7b",
	sha256_file_hash = "D7F9....61E6F",
)

await graph_client.directory.public_key_infrastructure.certificate_based_auth_configurations.by_certificate_based_auth_pki_id('certificateBasedAuthPki-id').upload.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
