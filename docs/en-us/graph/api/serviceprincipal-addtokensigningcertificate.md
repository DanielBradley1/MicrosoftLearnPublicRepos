<!-- Source: https://learn.microsoft.com/en-us/graph/api/serviceprincipal-addtokensigningcertificate?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-19 -->

# servicePrincipal: addTokenSigningCertificate

Namespace: microsoft.graph

Create a self-signed signing certificate and return a [selfSignedCertificate](https://learn.microsoft.com/en-us/graph/api/resources/selfsignedcertificate?view=graph-rest-1.0) object, which is the public part of the generated certificate.

The self-signed signing certificate is composed of the following objects, which are added to the [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0):

- The [keyCredentials](https://learn.microsoft.com/en-us/graph/api/resources/keycredential?view=graph-rest-1.0) object with the following objects:

  - A private key object with **usage** set to `Sign`.
  - A public key object with **usage** set to `Verify`.

- The [passwordCredentials](https://learn.microsoft.com/en-us/graph/api/resources/passwordcredential?view=graph-rest-1.0) object.

All the objects have the same value of **customKeyIdentifier**.

The **passwordCredential** is used to open the PFX file \(private key\). It and the associated private key object have the same value of **keyId**. When set during creation through the **displayName** property, the subject of the certificate cannot be updated. The **startDateTime** is set to the same time the certificate is created using the action. The **endDateTime** can be up to three years after the certificate is created.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Application.ReadWrite.All | Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Application.ReadWrite.OwnedBy | Application.ReadWrite.All, Directory.ReadWrite.All |

## HTTP request

You can address the service principal using either its **id** or **appId**. **id** and **appId** are referred to as the **Object ID** and **Application \(Client\) ID**, respectively, in app registrations in the Microsoft Entra admin center.

```http
POST /servicePrincipals/{id}/addTokenSigningCertificate
POST /servicePrincipals(appId='{appId}')/addTokenSigningCertificate
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, provide the following required properties.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | string | Friendly name for the key. It must start with `CN=`. |
| endDateTime | DateTimeOffset | The date and time when the credential expires. It can be up to 3 years from the date the certificate is created. If not supplied, the default is three years from the time of creation. The timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |

## Response

If successful, this method returns a `200 OK` response code and a new [selfSignedCertificate](https://learn.microsoft.com/en-us/graph/api/resources/selfsignedcertificate?view=graph-rest-1.0) object in the response body.

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
POST https://graph.microsoft.com/v1.0/servicePrincipals/004375c5-6e2e-4dec-95e3-626838cb9f80/addTokenSigningCertificate
Content-type: application/json

{
    "displayName":"CN=customDisplayName",
    "endDateTime":"2024-01-25T00:00:00Z"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.ServicePrincipals.Item.AddTokenSigningCertificate;

var requestBody = new AddTokenSigningCertificatePostRequestBody
{
	DisplayName = "CN=customDisplayName",
	EndDateTime = DateTimeOffset.Parse("2024-01-25T00:00:00Z"),
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.ServicePrincipals["{servicePrincipal-id}"].AddTokenSigningCertificate.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  "time"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphserviceprincipals "github.com/microsoftgraph/msgraph-sdk-go/serviceprincipals"
	  //other-imports
)

requestBody := graphserviceprincipals.NewAddTokenSigningCertificatePostRequestBody()
displayName := "CN=customDisplayName"
requestBody.SetDisplayName(&displayName) 
endDateTime , err := time.Parse(time.RFC3339, "2024-01-25T00:00:00Z")
requestBody.SetEndDateTime(&endDateTime) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
addTokenSigningCertificate, err := graphClient.ServicePrincipals().ByServicePrincipalId("servicePrincipal-id").AddTokenSigningCertificate().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.serviceprincipals.item.addtokensigningcertificate.AddTokenSigningCertificatePostRequestBody addTokenSigningCertificatePostRequestBody = new com.microsoft.graph.serviceprincipals.item.addtokensigningcertificate.AddTokenSigningCertificatePostRequestBody();
addTokenSigningCertificatePostRequestBody.setDisplayName("CN=customDisplayName");
OffsetDateTime endDateTime = OffsetDateTime.parse("2024-01-25T00:00:00Z");
addTokenSigningCertificatePostRequestBody.setEndDateTime(endDateTime);
SelfSignedCertificate result = graphClient.servicePrincipals().byServicePrincipalId("{servicePrincipal-id}").addTokenSigningCertificate().post(addTokenSigningCertificatePostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const selfSignedCertificate = {
    displayName: 'CN=customDisplayName',
    endDateTime: '2024-01-25T00:00:00Z'
};

await client.api('/servicePrincipals/004375c5-6e2e-4dec-95e3-626838cb9f80/addTokenSigningCertificate')
	.post(selfSignedCertificate);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\ServicePrincipals\Item\AddTokenSigningCertificate\AddTokenSigningCertificatePostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AddTokenSigningCertificatePostRequestBody();
$requestBody->setDisplayName('CN=customDisplayName');
$requestBody->setEndDateTime(new \DateTime('2024-01-25T00:00:00Z'));

$result = $graphServiceClient->servicePrincipals()->byServicePrincipalId('servicePrincipal-id')->addTokenSigningCertificate()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Applications

$params = @{
	displayName = "CN=customDisplayName"
	endDateTime = [System.DateTime]::Parse("2024-01-25T00:00:00Z")
}

Add-MgServicePrincipalTokenSigningCertificate -ServicePrincipalId $servicePrincipalId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.serviceprincipals.item.add_token_signing_certificate.add_token_signing_certificate_post_request_body import AddTokenSigningCertificatePostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AddTokenSigningCertificatePostRequestBody(
	display_name = "CN=customDisplayName",
	end_date_time = "2024-01-25T00:00:00Z",
)

result = await graph_client.service_principals.by_service_principal_id('servicePrincipal-id').add_token_signing_certificate.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#microsoft.graph.selfSignedCertificate",
  "customKeyIdentifier": "2iD8ppbE+D6Kmu1ZvjM2jtQh88E=",
  "displayName": "CN=customDisplayName",
  "endDateTime": "2024-01-25T00:00:00Z",
  "key": "MIICuDCCAaCgAwIBAgIIYXJsNtL4oUMwDQYJKoZIhvcNAQEL...StP8s/w==",
  "keyId": "93bc223f-7235-4b9c-beea-d66847531c49",
  "startDateTime": "2021-05-05T18:38:51.8100763Z",
  "thumbprint": "DA20FCA696C4F83E8A9AED59BE33368ED421F3C1",
  "type": "AsymmetricX509Cert",
  "usage": "Verify"
}
```
