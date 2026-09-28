<!-- Source: https://learn.microsoft.com/en-us/graph/api/certificatebasedauthpki-post-certificateauthorities?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-16 -->

# Create certificateAuthorityDetail

Namespace: microsoft.graph

Create a new [certificateAuthorityDetail](https://learn.microsoft.com/en-us/graph/api/resources/certificateauthoritydetail?view=graph-rest-1.0) object.

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
POST /directory/publicKeyInfrastructure/certificateBasedAuthConfigurations/{certificateBasedAuthPkiId}/certificateAuthorities
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [certificateAuthorityDetail](https://learn.microsoft.com/en-us/graph/api/resources/certificateauthoritydetail?view=graph-rest-1.0) object.

You can specify the following properties when creating a **certificateAuthorityDetail**.

| Property | Type | Description |
| :--- | :--- | :--- |
| certificateAuthorityType | certificateAuthorityType | The type of certificate authority. The possible values are: `root`, `intermediate`, and `unknownFutureValue`. Optional. Supports `$filter` \(`eq`\). |
| certificate | Binary | The public key of the certificate authority. Required. |
| displayName | String | The display name of the certificate authority. Optional. |
| issuer | String | The issuer of the certificate authority. Optional. |
| issuerSubjectKeyIdentifier | String | The subject key identifier of certificate authority. Optional. |
| expirationDateTime | DateTimeOffset | The date and time when the certificate authority expires. Required. Supports `$filter` \(`eq`\) and `$orderby`. |
| thumbprint | String | The thumbprint of certificate authority certificate. Required. Supports `$filter` \(`eq`, `startswith`\). |
| certificateRevocationListUrl | String | The URL to check if the certificate is revoked. Optional. |
| deltacertificateRevocationListUrl | String | The list of certificates that have been revoked since the last Certificate Revocation List \(CRL\) or Delta CRL was published, depending on which is most recent. Optional. |
| isIssuerHintEnabled | Boolean | Indicates whether the certificate picker presents the certificate authority to the user to use for authentication. Default value is `false`. Optional. |

## Response

If successful, this method returns a `201 Created` response code and a [certificateAuthorityDetail](https://learn.microsoft.com/en-us/graph/api/resources/certificateauthoritydetail?view=graph-rest-1.0) object in the response body.

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
POST https://graph.microsoft.com/v1.0/directory/publicKeyInfrastructure/certificateBasedAuthConfigurations/{certificateBasedAuthPkiId}/certificateAuthorities
Content-Type: application/json

{
 
  "certificateAuthorityType": "intermediate",
 
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new CertificateAuthorityDetail
{
	CertificateAuthorityType = CertificateAuthorityType.Intermediate,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Directory.PublicKeyInfrastructure.CertificateBasedAuthConfigurations["{certificateBasedAuthPki-id}"].CertificateAuthorities.PostAsync(requestBody);
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
certificateAuthorityType := graphmodels.INTERMEDIATE_CERTIFICATEAUTHORITYTYPE 
requestBody.SetCertificateAuthorityType(&certificateAuthorityType) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
certificateAuthorities, err := graphClient.Directory().PublicKeyInfrastructure().CertificateBasedAuthConfigurations().ByCertificateBasedAuthPkiId("certificateBasedAuthPki-id").CertificateAuthorities().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

CertificateAuthorityDetail certificateAuthorityDetail = new CertificateAuthorityDetail();
certificateAuthorityDetail.setCertificateAuthorityType(CertificateAuthorityType.Intermediate);
CertificateAuthorityDetail result = graphClient.directory().publicKeyInfrastructure().certificateBasedAuthConfigurations().byCertificateBasedAuthPkiId("{certificateBasedAuthPki-id}").certificateAuthorities().post(certificateAuthorityDetail);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const certificateAuthorityDetail = {
 
  certificateAuthorityType: 'intermediate',
 
};

await client.api('/directory/publicKeyInfrastructure/certificateBasedAuthConfigurations/{certificateBasedAuthPkiId}/certificateAuthorities')
	.post(certificateAuthorityDetail);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\CertificateAuthorityDetail;
use Microsoft\Graph\Generated\Models\CertificateAuthorityType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CertificateAuthorityDetail();
$requestBody->setCertificateAuthorityType(new CertificateAuthorityType('intermediate'));

$result = $graphServiceClient->directory()->publicKeyInfrastructure()->certificateBasedAuthConfigurations()->byCertificateBasedAuthPkiId('certificateBasedAuthPki-id')->certificateAuthorities()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.DirectoryManagement

$params = @{
	certificateAuthorityType = "intermediate"
}

New-MgDirectoryPublicKeyInfrastructureCertificateBasedAuthConfigurationCertificateAuthority -CertificateBasedAuthPkiId $certificateBasedAuthPkiId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.certificate_authority_detail import CertificateAuthorityDetail
from msgraph.generated.models.certificate_authority_type import CertificateAuthorityType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CertificateAuthorityDetail(
	certificate_authority_type = CertificateAuthorityType.Intermediate,
)

result = await graph_client.directory.public_key_infrastructure.certificate_based_auth_configurations.by_certificate_based_auth_pki_id('certificateBasedAuthPki-id').certificate_authorities.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.certificateAuthorityDetail",
  "id": "90777c92-2eb3-4a68-931d-4a3e1e1c741f",
  "deletedDateTime": null,
  "certificateAuthorityType": "intermediate",
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
