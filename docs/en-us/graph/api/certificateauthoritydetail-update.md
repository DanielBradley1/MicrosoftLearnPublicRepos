<!-- Source: https://learn.microsoft.com/en-us/graph/api/certificateauthoritydetail-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-16 -->

# Update certificateAuthorityDetail

Namespace: microsoft.graph Update the properties of a [certificateAuthorityDetail](https://learn.microsoft.com/en-us/graph/api/resources/certificateauthoritydetail?view=graph-rest-1.0) object.

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
PATCH /directory/publicKeyInfrastructure/certificateBasedAuthConfigurations/{certificateBasedAuthPkiId}/certificateAuthorities/{certificateAuthorityDetailId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| certificateAuthorityType | certificateAuthorityType | The type of certificate authority. The possible values are: `root`, `intermediate`, `unknownFutureValue`. |
| certificate | Binary | The type of certificate authority. The possible values are: `root`, `intermediate`. |
| displayName | String | The name of the certificate authority. |
| issuer | String | The issuer of the certificate authority. |
| issuerSubjectKeyIdentifier | String | The subject key identifier of certificate authority. |
| createdDateTime | DateTimeOffset | The date and time when the certificate authority was created. |
| expirationDateTime | DateTimeOffset | The date and time when the certificate authority expires. Required. |
| thumbprint | String | The thumbprint of certificate authority certificate. Required. |
| certificateRevocationListUrl | String | The URL to check if the certificate is revoked. |
| deltacertificateRevocationListUrl | String | The URL to check if the certificate is revoked. |
| isIssuerHintEnabled | Boolean | Indicates whether the certificate picker presents the certificate authority to the user to use for authentication. Default value is `false`. |

## Response

If successful, this method returns a `200 OK` response code and an updated [certificateAuthorityDetail](https://learn.microsoft.com/en-us/graph/api/resources/certificateauthoritydetail?view=graph-rest-1.0) object in the response body.

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
PATCH https://graph.microsoft.com/v1.0/directory/publicKeyInfrastructure/certificateBasedAuthConfigurations/{certificateBasedAuthPkiId}/certificateAuthorities/{certificateAuthorityDetailId}
Content-Type: application/json

{

   "isIssuerHintEnabled": true
   
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new CertificateAuthorityDetail
{
	IsIssuerHintEnabled = true,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Directory.PublicKeyInfrastructure.CertificateBasedAuthConfigurations["{certificateBasedAuthPki-id}"].CertificateAuthorities["{certificateAuthorityDetail-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewCertificateAuthorityDetail()
isIssuerHintEnabled := true
requestBody.SetIsIssuerHintEnabled(&isIssuerHintEnabled) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
certificateAuthorities, err := graphClient.Directory().PublicKeyInfrastructure().CertificateBasedAuthConfigurations().ByCertificateBasedAuthPkiId("certificateBasedAuthPki-id").CertificateAuthorities().ByCertificateAuthorityDetailId("certificateAuthorityDetail-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

CertificateAuthorityDetail certificateAuthorityDetail = new CertificateAuthorityDetail();
certificateAuthorityDetail.setIsIssuerHintEnabled(true);
CertificateAuthorityDetail result = graphClient.directory().publicKeyInfrastructure().certificateBasedAuthConfigurations().byCertificateBasedAuthPkiId("{certificateBasedAuthPki-id}").certificateAuthorities().byCertificateAuthorityDetailId("{certificateAuthorityDetail-id}").patch(certificateAuthorityDetail);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const certificateAuthorityDetail = {

   isIssuerHintEnabled: true
   
};

await client.api('/directory/publicKeyInfrastructure/certificateBasedAuthConfigurations/{certificateBasedAuthPkiId}/certificateAuthorities/{certificateAuthorityDetailId}')
	.update(certificateAuthorityDetail);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\CertificateAuthorityDetail;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CertificateAuthorityDetail();
$requestBody->setIsIssuerHintEnabled(true);

$result = $graphServiceClient->directory()->publicKeyInfrastructure()->certificateBasedAuthConfigurations()->byCertificateBasedAuthPkiId('certificateBasedAuthPki-id')->certificateAuthorities()->byCertificateAuthorityDetailId('certificateAuthorityDetail-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.DirectoryManagement

$params = @{
	isIssuerHintEnabled = $true
}

Update-MgDirectoryPublicKeyInfrastructureCertificateBasedAuthConfigurationCertificateAuthority -CertificateBasedAuthPkiId $certificateBasedAuthPkiId -CertificateAuthorityDetailId $certificateAuthorityDetailId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.certificate_authority_detail import CertificateAuthorityDetail
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CertificateAuthorityDetail(
	is_issuer_hint_enabled = True,
)

result = await graph_client.directory.public_key_infrastructure.certificate_based_auth_configurations.by_certificate_based_auth_pki_id('certificateBasedAuthPki-id').certificate_authorities.by_certificate_authority_detail_id('certificateAuthorityDetail-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.certificateAuthorityDetail",
  "id": "90777c92-2eb3-4a68-931d-4a3e1e1c741f",
  "deletedDateTime": null,
  "certificateAuthorityType": "root",
  "certificate": "Binary",
  "displayName": "Contoso2 CA1",
  "issuer": "Contoso2",
  "issuerSubjectKeyIdentifier": "C0E9....711A",
  "createdDateTime": "2024-10-25T18:05:28Z",
  "expirationDateTime": "2027-08-29T02:05:57Z",
  "thumbprint": "C6FA....4E9CF2",
  "certificateRevocationListUrl": null,
  "deltacertificateRevocationListUrl": null,
  "isIssuerHintEnabled": true

}
```
