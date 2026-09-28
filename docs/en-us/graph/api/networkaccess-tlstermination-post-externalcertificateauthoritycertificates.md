<!-- Source: https://learn.microsoft.com/en-us/graph/api/networkaccess-tlstermination-post-externalcertificateauthoritycertificates?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-08-20 -->

# Create externalCertificateAuthorityCertificate

Namespace: microsoft.graph.networkaccess

Create a new [externalCertificateAuthorityCertificate](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-externalcertificateauthoritycertificate?view=graph-rest-beta) object. This request generates the Certificate Signing Request \(CSR\) that you download to sign and generate a certificate that you upload to the service using the [Update externalCertificateAuthorityCertificate operation](https://learn.microsoft.com/en-us/graph/api/networkaccess-externalcertificateauthoritycertificate-update?view=graph-rest-beta).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | NetworkAccess.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | NetworkAccess.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Global Secure Access Administrator
- Security Administrator

## HTTP request

```http
POST /networkAccess/tls/externalCertificateAuthorityCertificates
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [microsoft.graph.networkaccess.externalCertificateAuthorityCertificate](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-externalcertificateauthoritycertificate?view=graph-rest-beta) object.

You can specify the following properties when creating a **externalCertificateAuthorityCertificate**.

| Property | Type | Description |
| :--- | :--- | :--- |
| name | String | The display name of the certificate authority. Required. |
| commonName | String | The common name \(CN\) field of the certificate. Required. |
| organizationName | String | The organization name \(O\) field of the certificate. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [microsoft.graph.networkaccess.externalCertificateAuthorityCertificate](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-externalcertificateauthoritycertificate?view=graph-rest-beta) object in the response body.

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
POST https://graph.microsoft.com/beta/networkAccess/tls/externalCertificateAuthorityCertificates
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.networkaccess.externalCertificateAuthorityCertificate",
  "name": "Contoso Enterprise CA",
  "commonName": "Contoso Enterprise Root CA",
  "organizationName": "Contoso Ltd"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.Networkaccess;

var requestBody = new ExternalCertificateAuthorityCertificate
{
	OdataType = "#microsoft.graph.networkaccess.externalCertificateAuthorityCertificate",
	Name = "Contoso Enterprise CA",
	CommonName = "Contoso Enterprise Root CA",
	OrganizationName = "Contoso Ltd",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.NetworkAccess.Tls.ExternalCertificateAuthorityCertificates.PostAsync(requestBody);
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
	  graphmodelsnetworkaccess "github.com/microsoftgraph/msgraph-beta-sdk-go/models/networkaccess"
	  //other-imports
)

requestBody := graphmodelsnetworkaccess.NewExternalCertificateAuthorityCertificate()
name := "Contoso Enterprise CA"
requestBody.SetName(&name) 
commonName := "Contoso Enterprise Root CA"
requestBody.SetCommonName(&commonName) 
organizationName := "Contoso Ltd"
requestBody.SetOrganizationName(&organizationName) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
externalCertificateAuthorityCertificates, err := graphClient.NetworkAccess().Tls().ExternalCertificateAuthorityCertificates().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.networkaccess.ExternalCertificateAuthorityCertificate externalCertificateAuthorityCertificate = new com.microsoft.graph.beta.models.networkaccess.ExternalCertificateAuthorityCertificate();
externalCertificateAuthorityCertificate.setOdataType("#microsoft.graph.networkaccess.externalCertificateAuthorityCertificate");
externalCertificateAuthorityCertificate.setName("Contoso Enterprise CA");
externalCertificateAuthorityCertificate.setCommonName("Contoso Enterprise Root CA");
externalCertificateAuthorityCertificate.setOrganizationName("Contoso Ltd");
com.microsoft.graph.models.networkaccess.ExternalCertificateAuthorityCertificate result = graphClient.networkAccess().tls().externalCertificateAuthorityCertificates().post(externalCertificateAuthorityCertificate);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const externalCertificateAuthorityCertificate = {
  '@odata.type': '#microsoft.graph.networkaccess.externalCertificateAuthorityCertificate',
  name: 'Contoso Enterprise CA',
  commonName: 'Contoso Enterprise Root CA',
  organizationName: 'Contoso Ltd'
};

await client.api('/networkAccess/tls/externalCertificateAuthorityCertificates')
	.version('beta')
	.post(externalCertificateAuthorityCertificate);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\ExternalCertificateAuthorityCertificate;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ExternalCertificateAuthorityCertificate();
$requestBody->setOdataType('#microsoft.graph.networkaccess.externalCertificateAuthorityCertificate');
$requestBody->setName('Contoso Enterprise CA');
$requestBody->setCommonName('Contoso Enterprise Root CA');
$requestBody->setOrganizationName('Contoso Ltd');

$result = $graphServiceClient->networkAccess()->tls()->externalCertificateAuthorityCertificates()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.NetworkAccess

$params = @{
	"@odata.type" = "#microsoft.graph.networkaccess.externalCertificateAuthorityCertificate"
	name = "Contoso Enterprise CA"
	commonName = "Contoso Enterprise Root CA"
	organizationName = "Contoso Ltd"
}

New-MgBetaNetworkAccessTlExternalCertificateAuthorityCertificate -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.networkaccess.external_certificate_authority_certificate import ExternalCertificateAuthorityCertificate
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ExternalCertificateAuthorityCertificate(
	odata_type = "#microsoft.graph.networkaccess.externalCertificateAuthorityCertificate",
	name = "Contoso Enterprise CA",
	common_name = "Contoso Enterprise Root CA",
	organization_name = "Contoso Ltd",
)

result = await graph_client.network_access.tls.external_certificate_authority_certificates.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.networkaccess.externalCertificateAuthorityCertificate",
  "id": "365da4f6-6194-401d-b787-b09815be36e3",
  "name": "Contoso Enterprise CA",
  "commonName": "Contoso Enterprise Root CA",
  "organizationName": "Contoso Ltd",
  "validity": {
    "@odata.type": "microsoft.graph.networkaccess.validityDate",
    "startDateTime": "2025-02-10T00:00:00Z",
    "endDateTime": "2026-02-10T00:00:00Z"
  },
  "status": "csrGenerated"
}
```
