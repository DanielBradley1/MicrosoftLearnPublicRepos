<!-- Source: https://learn.microsoft.com/en-us/graph/applications-how-to-add-certificate -->
<!-- Sitemap-Last-Modified: 2025-08-29 -->

# Add a certificate to an app by using Microsoft Graph

The Microsoft identity platform supports three types of credentials to authenticate apps and service principals: *passwords* \(app secrets\), *certificates*, and *federated identity credentials*. If you can't use federated identity credentials for your app, use certificates instead of secrets.

You can [add or remove certificates by using the Microsoft Entra admin center](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app?tabs=certificate#add-credentials). However, you might need to automate adding certificate credentials for your app or service principal.

This article provides guidance for using Microsoft Graph and PowerShell scripts to update certificate credentials programmatically for an app registration.

## Prerequisites

To complete this tutorial, you need the following resources and privileges:

- An active Microsoft Entra tenant.
- An API client such as [Graph Explorer](https://aka.ms/ge). Sign in as a user who is allowed to create and manage applications in the tenant. The *Application Developer* \(of an app they own\) and *Application Administrator* roles are the least privileged roles that can perform this operation.
- A signed certificate to use to authenticate the app. This article uses a self-signed certificate for demonstration purposes. To generate one, see [Create a self-signed public certificate to authenticate your application](https://learn.microsoft.com/en-us/azure/active-directory/develop/howto-create-self-signed-certificate).

Caution

Use certificates over secrets; however, don't use self-signed certificates. They can reduce the security of your application due to various factors like use of an outdated hash and cipher suites or lack of validation. Get certificates from a well-known trusted certificate authority.

## Step 1: Read the certificate details

To add a certificate programmatically by using Microsoft Graph, you need the certificate's key. You can optionally add the certificate's thumbprint.

### \[Optional\] Get the certificate thumbprint

You can optionally add the certificate thumbprint to the request payload. To add the thumbprint, run the following PowerShell request to read the certificate's thumbprint. This request assumes that you generated and exported the certificate to your local drive.

#### Request

```powershell
## Replace the file path with the source of your certificate and output path with the location where you want to save the thumprint details

Get-PfxCertificate -Filepath "C:\Users\admin\Desktop\20230112.cer" | Out-File -FilePath "C:\Users\admin\Desktop\20230112.cer.thumbprint.txt"
```

#### Response

The output in the *.txt* file can be similar to the following example.

```powershell
Thumbprint                                Subject
----------                                -------
5A126608ED1A1366F714A4A62B7015F3262840F1  CN=20230112
```

### Get the certificate key

To read the certificate's key and save it to a *.txt* file by using PowerShell, run the following request.

#### Request

**PowerShell < 6**:

```powershell
## Replace the file path with the location of your certificate

[convert]::ToBase64String((Get-Content C:\Users\admin\Desktop\20230112.cer -Encoding byte)) | Out-File -FilePath "C:\Users\admin\Desktop\20230112.key.txt"
```

**PowerShell >= 6**:

```powershell
## Replace the file path with the location of your certificate

[convert]::ToBase64String((Get-Content C:\Users\admin\Desktop\20230112.cer -AsByteStream))  | Out-File -FilePath "C:\Users\admin\Desktop\20230112.key.txt"
```

#### Response

The output in the *.txt* file can be similar to the following example.

> **Note:** The key shown here is shortened for readability.

```powershell
MIIDADCCAeigAwIBAgIQP6HEGDdZ65xJTcK4dCBvZzANBgkqhkiG9w0BAQsFADATMREwDwYDVQQDDAgyMDIzMDExMjAeFw0yMzAxMTIwODExNTZaFw0yNDAxMTIwODMxNTZaMBMxETAPBgNVBAMMCDIwMjMwMTEyMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAseKf1weEacJ67D6/...dG+7WMIBsIUy0xz6MmyvfSohz3oNP4jHt7pJ9TyxnvDlaxQPUbuIL+DaXVkKRm1V3GgIpKTBqMzTf4tCpy7rpUZbhcwAFw6h9A==
```

## Step 2: Add the certificate details using Microsoft Graph

### Request

The following request adds the certificate details to an app. The settings are as follows:

- The **startDateTime** is the date when or after the certificate was created.
- The **endDateTime** can be a maximum of one year from the **startDateTime**. If you don't specify it, the system automatically assigns a date one year after the **startDateTime**.
- The **type** and **usage** must be `AsymmetricX509Cert` and `Verify`, respectively.
- Assign the certificate subject name to the **displayName** property.
- The **key** is the Base64 encoded value that you generated in the previous step. The thumbprint is included in the encoded key. Adding the key also adds the thumbprint.

Note

If your app has an existing valid certificate that you want to continue using for authentication, include both the current and new certificate details in the app's **keyCredentials** object. Because this is a PATCH call, which by protocol replaces the contents of the property with the new values, including only the new certificate replaces the existing certificates with the new one.

The following example adds a new certificate and replaces any existing certificates.

> **Note:** The key shown here is shortened for readability.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
PATCH https://graph.microsoft.com/v1.0/applications/bb77f42f-dacb-4ece-b3e6-285e63c24d52
Content-type: application/json

{
    "keyCredentials": [
        {
            "endDateTime": "2024-01-11T15:31:26Z",
            "startDateTime": "2023-01-12T15:31:26Z",
            "type": "AsymmetricX509Cert",
            "usage": "Verify",
            "key": "base64MIIDADCCAeigAwIBAgIQP6HEGDdZ65xJTcK4dCBvZzANBgkqhkiG9w0BAQsFADATMREwDwYDVQQDDAgyMDIzMDExMjAeFw0yMzAxMTIwODExNTZaFw0yNDAxMTIwODMxNTZaMBMxETAPBgNVBAMMCDIwMjMwMTEyMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAseKf1weEacJ67D6/...laxQPUbuIL+DaXVkKRm1V3GgIpKTBqMzTf4tCpy7rpUZbhcwAFw6h9A==",
            "displayName": "CN=20230112"
        }
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Application
{
	KeyCredentials = new List<KeyCredential>
	{
		new KeyCredential
		{
			EndDateTime = DateTimeOffset.Parse("2024-01-11T15:31:26Z"),
			StartDateTime = DateTimeOffset.Parse("2023-01-12T15:31:26Z"),
			Type = "AsymmetricX509Cert",
			Usage = "Verify",
			Key = Convert.FromBase64String("base64MIIDADCCAeigAwIBAgIQP6HEGDdZ65xJTcK4dCBvZzANBgkqhkiG9w0BAQsFADATMREwDwYDVQQDDAgyMDIzMDExMjAeFw0yMzAxMTIwODExNTZaFw0yNDAxMTIwODMxNTZaMBMxETAPBgNVBAMMCDIwMjMwMTEyMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAseKf1weEacJ67D6/...laxQPUbuIL+DaXVkKRm1V3GgIpKTBqMzTf4tCpy7rpUZbhcwAFw6h9A=="),
			DisplayName = "CN=20230112",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Applications["{application-id}"].PatchAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewApplication()


keyCredential := graphmodels.NewKeyCredential()
endDateTime , err := time.Parse(time.RFC3339, "2024-01-11T15:31:26Z")
keyCredential.SetEndDateTime(&endDateTime) 
startDateTime , err := time.Parse(time.RFC3339, "2023-01-12T15:31:26Z")
keyCredential.SetStartDateTime(&startDateTime) 
type := "AsymmetricX509Cert"
keyCredential.SetType(&type) 
usage := "Verify"
keyCredential.SetUsage(&usage) 
key := []byte("base64MIIDADCCAeigAwIBAgIQP6HEGDdZ65xJTcK4dCBvZzANBgkqhkiG9w0BAQsFADATMREwDwYDVQQDDAgyMDIzMDExMjAeFw0yMzAxMTIwODExNTZaFw0yNDAxMTIwODMxNTZaMBMxETAPBgNVBAMMCDIwMjMwMTEyMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAseKf1weEacJ67D6/...laxQPUbuIL+DaXVkKRm1V3GgIpKTBqMzTf4tCpy7rpUZbhcwAFw6h9A==")
keyCredential.SetKey(&key) 
displayName := "CN=20230112"
keyCredential.SetDisplayName(&displayName) 

keyCredentials := []graphmodels.KeyCredentialable {
	keyCredential,
}
requestBody.SetKeyCredentials(keyCredentials)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
applications, err := graphClient.Applications().ByApplicationId("application-id").Patch(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Application application = new Application();
LinkedList<KeyCredential> keyCredentials = new LinkedList<KeyCredential>();
KeyCredential keyCredential = new KeyCredential();
OffsetDateTime endDateTime = OffsetDateTime.parse("2024-01-11T15:31:26Z");
keyCredential.setEndDateTime(endDateTime);
OffsetDateTime startDateTime = OffsetDateTime.parse("2023-01-12T15:31:26Z");
keyCredential.setStartDateTime(startDateTime);
keyCredential.setType("AsymmetricX509Cert");
keyCredential.setUsage("Verify");
byte[] key = Base64.getDecoder().decode("base64MIIDADCCAeigAwIBAgIQP6HEGDdZ65xJTcK4dCBvZzANBgkqhkiG9w0BAQsFADATMREwDwYDVQQDDAgyMDIzMDExMjAeFw0yMzAxMTIwODExNTZaFw0yNDAxMTIwODMxNTZaMBMxETAPBgNVBAMMCDIwMjMwMTEyMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAseKf1weEacJ67D6/...laxQPUbuIL+DaXVkKRm1V3GgIpKTBqMzTf4tCpy7rpUZbhcwAFw6h9A==");
keyCredential.setKey(key);
keyCredential.setDisplayName("CN=20230112");
keyCredentials.add(keyCredential);
application.setKeyCredentials(keyCredentials);
Application result = graphClient.applications().byApplicationId("{application-id}").patch(application);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const application = {
    keyCredentials: [
        {
            endDateTime: '2024-01-11T15:31:26Z',
            startDateTime: '2023-01-12T15:31:26Z',
            type: 'AsymmetricX509Cert',
            usage: 'Verify',
            key: 'base64MIIDADCCAeigAwIBAgIQP6HEGDdZ65xJTcK4dCBvZzANBgkqhkiG9w0BAQsFADATMREwDwYDVQQDDAgyMDIzMDExMjAeFw0yMzAxMTIwODExNTZaFw0yNDAxMTIwODMxNTZaMBMxETAPBgNVBAMMCDIwMjMwMTEyMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAseKf1weEacJ67D6/...laxQPUbuIL+DaXVkKRm1V3GgIpKTBqMzTf4tCpy7rpUZbhcwAFw6h9A==',
            displayName: 'CN=20230112'
        }
    ]
};

await client.api('/applications/bb77f42f-dacb-4ece-b3e6-285e63c24d52')
	.update(application);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Application;
use Microsoft\Graph\Generated\Models\KeyCredential;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Application();
$keyCredentialsKeyCredential1 = new KeyCredential();
$keyCredentialsKeyCredential1->setEndDateTime(new \DateTime('2024-01-11T15:31:26Z'));
$keyCredentialsKeyCredential1->setStartDateTime(new \DateTime('2023-01-12T15:31:26Z'));
$keyCredentialsKeyCredential1->setType('AsymmetricX509Cert');
$keyCredentialsKeyCredential1->setUsage('Verify');
$keyCredentialsKeyCredential1->setKey(\GuzzleHttp\Psr7\Utils::streamFor(base64_decode('base64MIIDADCCAeigAwIBAgIQP6HEGDdZ65xJTcK4dCBvZzANBgkqhkiG9w0BAQsFADATMREwDwYDVQQDDAgyMDIzMDExMjAeFw0yMzAxMTIwODExNTZaFw0yNDAxMTIwODMxNTZaMBMxETAPBgNVBAMMCDIwMjMwMTEyMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAseKf1weEacJ67D6/...laxQPUbuIL+DaXVkKRm1V3GgIpKTBqMzTf4tCpy7rpUZbhcwAFw6h9A==')));
$keyCredentialsKeyCredential1->setDisplayName('CN=20230112');
$keyCredentialsArray []= $keyCredentialsKeyCredential1;
$requestBody->setKeyCredentials($keyCredentialsArray);


$result = $graphServiceClient->applications()->byApplicationId('application-id')->patch($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Applications

$params = @{
	keyCredentials = @(
		@{
			endDateTime = [System.DateTime]::Parse("2024-01-11T15:31:26Z")
			startDateTime = [System.DateTime]::Parse("2023-01-12T15:31:26Z")
			type = "AsymmetricX509Cert"
			usage = "Verify"
			key = [System.Text.Encoding]::ASCII.GetBytes("base64MIIDADCCAeigAwIBAgIQP6HEGDdZ65xJTcK4dCBvZzANBgkqhkiG9w0BAQsFADATMREwDwYDVQQDDAgyMDIzMDExMjAeFw0yMzAxMTIwODExNTZaFw0yNDAxMTIwODMxNTZaMBMxETAPBgNVBAMMCDIwMjMwMTEyMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAseKf1weEacJ67D6/...laxQPUbuIL+DaXVkKRm1V3GgIpKTBqMzTf4tCpy7rpUZbhcwAFw6h9A==")
			displayName = "CN=20230112"
		}
	)
}

Update-MgApplication -ApplicationId $applicationId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.application import Application
from msgraph.generated.models.key_credential import KeyCredential
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Application(
	key_credentials = [
		KeyCredential(
			end_date_time = "2024-01-11T15:31:26Z",
			start_date_time = "2023-01-12T15:31:26Z",
			type = "AsymmetricX509Cert",
			usage = "Verify",
			key = base64.urlsafe_b64decode("base64MIIDADCCAeigAwIBAgIQP6HEGDdZ65xJTcK4dCBvZzANBgkqhkiG9w0BAQsFADATMREwDwYDVQQDDAgyMDIzMDExMjAeFw0yMzAxMTIwODExNTZaFw0yNDAxMTIwODMxNTZaMBMxETAPBgNVBAMMCDIwMjMwMTEyMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAseKf1weEacJ67D6/...laxQPUbuIL+DaXVkKRm1V3GgIpKTBqMzTf4tCpy7rpUZbhcwAFw6h9A=="),
			display_name = "CN=20230112",
		),
	],
)

result = await graph_client.applications.by_application_id('application-id').patch(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

The following example adds a new certificate without replacing the existing certificate with thumbprint `52ED9B5038A47B9E2E2190715CC238359D4F8F73`.

> **Note:** The key shown here is shortened for readability.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
PATCH https://graph.microsoft.com/v1.0/applications/bb77f42f-dacb-4ece-b3e6-285e63c24d52
Content-type: application/json

{
    "keyCredentials": [
        {
            "endDateTime": "2024-01-11T15:31:26Z",
            "startDateTime": "2023-01-12T09:31:26Z",
            "type": "AsymmetricX509Cert",
            "usage": "Verify",
            "key": "base64MIIDADCCAeigAwIBAgIQejfrj3S974xI//npv7hFHTANBgkqhkiG9w0BAQsFADATMREwDwYDVQQDDAgyMDIzMDExNDAeFw0yMzAxMTIwOTA4NThaFw0yNDAxMTIwOTI4NThaMBMxETAPBgNVBAMMCDIwMjMwMTE0MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAt5vEj6j1l5wOVHR4eDGe77HWslaIVJ1NqxrXPm/...+R+U7sboj+kUvmFzXI+Ge73Liu8egL2NzOHHpO43calWgq36a9YW1yhBQR1ioEchu6jmudW3rF6ktmVqQ==",
            "displayName": "CN=20230114"
        },
        {
            "customKeyIdentifier": "52ED9B5038A47B9E2E2190715CC238359D4F8F73",
            "type": "AsymmetricX509Cert",
            "usage": "Verify",
            "key": "base64MIIDADCCAeigAwIBAgIQfoIvchhpToxKEPI4iMrU1TANBgkqhkiG9w0BAQsFADATMREwDwYDVQQDDAgyMDIzMDExMzAeFw0yMzAxMTIwODI3NTJaFw0yNDAxMTIwODQ3NTJaMBMxETAPBgNVBAMMCDIwMjMwMTEzMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAw+iqg1nMjYmFcFJh/.../S5X6qoEOyJBgtfpSBANWAdA==",
            "displayName": "CN=20230113"
        }
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Application
{
	KeyCredentials = new List<KeyCredential>
	{
		new KeyCredential
		{
			EndDateTime = DateTimeOffset.Parse("2024-01-11T15:31:26Z"),
			StartDateTime = DateTimeOffset.Parse("2023-01-12T09:31:26Z"),
			Type = "AsymmetricX509Cert",
			Usage = "Verify",
			Key = Convert.FromBase64String("base64MIIDADCCAeigAwIBAgIQejfrj3S974xI//npv7hFHTANBgkqhkiG9w0BAQsFADATMREwDwYDVQQDDAgyMDIzMDExNDAeFw0yMzAxMTIwOTA4NThaFw0yNDAxMTIwOTI4NThaMBMxETAPBgNVBAMMCDIwMjMwMTE0MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAt5vEj6j1l5wOVHR4eDGe77HWslaIVJ1NqxrXPm/...+R+U7sboj+kUvmFzXI+Ge73Liu8egL2NzOHHpO43calWgq36a9YW1yhBQR1ioEchu6jmudW3rF6ktmVqQ=="),
			DisplayName = "CN=20230114",
		},
		new KeyCredential
		{
			CustomKeyIdentifier = Convert.FromBase64String("52ED9B5038A47B9E2E2190715CC238359D4F8F73"),
			Type = "AsymmetricX509Cert",
			Usage = "Verify",
			Key = Convert.FromBase64String("base64MIIDADCCAeigAwIBAgIQfoIvchhpToxKEPI4iMrU1TANBgkqhkiG9w0BAQsFADATMREwDwYDVQQDDAgyMDIzMDExMzAeFw0yMzAxMTIwODI3NTJaFw0yNDAxMTIwODQ3NTJaMBMxETAPBgNVBAMMCDIwMjMwMTEzMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAw+iqg1nMjYmFcFJh/.../S5X6qoEOyJBgtfpSBANWAdA=="),
			DisplayName = "CN=20230113",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Applications["{application-id}"].PatchAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewApplication()


keyCredential := graphmodels.NewKeyCredential()
endDateTime , err := time.Parse(time.RFC3339, "2024-01-11T15:31:26Z")
keyCredential.SetEndDateTime(&endDateTime) 
startDateTime , err := time.Parse(time.RFC3339, "2023-01-12T09:31:26Z")
keyCredential.SetStartDateTime(&startDateTime) 
type := "AsymmetricX509Cert"
keyCredential.SetType(&type) 
usage := "Verify"
keyCredential.SetUsage(&usage) 
key := []byte("base64MIIDADCCAeigAwIBAgIQejfrj3S974xI//npv7hFHTANBgkqhkiG9w0BAQsFADATMREwDwYDVQQDDAgyMDIzMDExNDAeFw0yMzAxMTIwOTA4NThaFw0yNDAxMTIwOTI4NThaMBMxETAPBgNVBAMMCDIwMjMwMTE0MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAt5vEj6j1l5wOVHR4eDGe77HWslaIVJ1NqxrXPm/...+R+U7sboj+kUvmFzXI+Ge73Liu8egL2NzOHHpO43calWgq36a9YW1yhBQR1ioEchu6jmudW3rF6ktmVqQ==")
keyCredential.SetKey(&key) 
displayName := "CN=20230114"
keyCredential.SetDisplayName(&displayName) 
keyCredential1 := graphmodels.NewKeyCredential()
customKeyIdentifier := []byte("52ED9B5038A47B9E2E2190715CC238359D4F8F73")
keyCredential1.SetCustomKeyIdentifier(&customKeyIdentifier) 
type := "AsymmetricX509Cert"
keyCredential1.SetType(&type) 
usage := "Verify"
keyCredential1.SetUsage(&usage) 
key := []byte("base64MIIDADCCAeigAwIBAgIQfoIvchhpToxKEPI4iMrU1TANBgkqhkiG9w0BAQsFADATMREwDwYDVQQDDAgyMDIzMDExMzAeFw0yMzAxMTIwODI3NTJaFw0yNDAxMTIwODQ3NTJaMBMxETAPBgNVBAMMCDIwMjMwMTEzMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAw+iqg1nMjYmFcFJh/.../S5X6qoEOyJBgtfpSBANWAdA==")
keyCredential1.SetKey(&key) 
displayName := "CN=20230113"
keyCredential1.SetDisplayName(&displayName) 

keyCredentials := []graphmodels.KeyCredentialable {
	keyCredential,
	keyCredential1,
}
requestBody.SetKeyCredentials(keyCredentials)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
applications, err := graphClient.Applications().ByApplicationId("application-id").Patch(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Application application = new Application();
LinkedList<KeyCredential> keyCredentials = new LinkedList<KeyCredential>();
KeyCredential keyCredential = new KeyCredential();
OffsetDateTime endDateTime = OffsetDateTime.parse("2024-01-11T15:31:26Z");
keyCredential.setEndDateTime(endDateTime);
OffsetDateTime startDateTime = OffsetDateTime.parse("2023-01-12T09:31:26Z");
keyCredential.setStartDateTime(startDateTime);
keyCredential.setType("AsymmetricX509Cert");
keyCredential.setUsage("Verify");
byte[] key = Base64.getDecoder().decode("base64MIIDADCCAeigAwIBAgIQejfrj3S974xI//npv7hFHTANBgkqhkiG9w0BAQsFADATMREwDwYDVQQDDAgyMDIzMDExNDAeFw0yMzAxMTIwOTA4NThaFw0yNDAxMTIwOTI4NThaMBMxETAPBgNVBAMMCDIwMjMwMTE0MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAt5vEj6j1l5wOVHR4eDGe77HWslaIVJ1NqxrXPm/...+R+U7sboj+kUvmFzXI+Ge73Liu8egL2NzOHHpO43calWgq36a9YW1yhBQR1ioEchu6jmudW3rF6ktmVqQ==");
keyCredential.setKey(key);
keyCredential.setDisplayName("CN=20230114");
keyCredentials.add(keyCredential);
KeyCredential keyCredential1 = new KeyCredential();
byte[] customKeyIdentifier = Base64.getDecoder().decode("52ED9B5038A47B9E2E2190715CC238359D4F8F73");
keyCredential1.setCustomKeyIdentifier(customKeyIdentifier);
keyCredential1.setType("AsymmetricX509Cert");
keyCredential1.setUsage("Verify");
byte[] key1 = Base64.getDecoder().decode("base64MIIDADCCAeigAwIBAgIQfoIvchhpToxKEPI4iMrU1TANBgkqhkiG9w0BAQsFADATMREwDwYDVQQDDAgyMDIzMDExMzAeFw0yMzAxMTIwODI3NTJaFw0yNDAxMTIwODQ3NTJaMBMxETAPBgNVBAMMCDIwMjMwMTEzMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAw+iqg1nMjYmFcFJh/.../S5X6qoEOyJBgtfpSBANWAdA==");
keyCredential1.setKey(key1);
keyCredential1.setDisplayName("CN=20230113");
keyCredentials.add(keyCredential1);
application.setKeyCredentials(keyCredentials);
Application result = graphClient.applications().byApplicationId("{application-id}").patch(application);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const application = {
    keyCredentials: [
        {
            endDateTime: '2024-01-11T15:31:26Z',
            startDateTime: '2023-01-12T09:31:26Z',
            type: 'AsymmetricX509Cert',
            usage: 'Verify',
            key: 'base64MIIDADCCAeigAwIBAgIQejfrj3S974xI//npv7hFHTANBgkqhkiG9w0BAQsFADATMREwDwYDVQQDDAgyMDIzMDExNDAeFw0yMzAxMTIwOTA4NThaFw0yNDAxMTIwOTI4NThaMBMxETAPBgNVBAMMCDIwMjMwMTE0MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAt5vEj6j1l5wOVHR4eDGe77HWslaIVJ1NqxrXPm/...+R+U7sboj+kUvmFzXI+Ge73Liu8egL2NzOHHpO43calWgq36a9YW1yhBQR1ioEchu6jmudW3rF6ktmVqQ==',
            displayName: 'CN=20230114'
        },
        {
            customKeyIdentifier: '52ED9B5038A47B9E2E2190715CC238359D4F8F73',
            type: 'AsymmetricX509Cert',
            usage: 'Verify',
            key: 'base64MIIDADCCAeigAwIBAgIQfoIvchhpToxKEPI4iMrU1TANBgkqhkiG9w0BAQsFADATMREwDwYDVQQDDAgyMDIzMDExMzAeFw0yMzAxMTIwODI3NTJaFw0yNDAxMTIwODQ3NTJaMBMxETAPBgNVBAMMCDIwMjMwMTEzMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAw+iqg1nMjYmFcFJh/.../S5X6qoEOyJBgtfpSBANWAdA==',
            displayName: 'CN=20230113'
        }
    ]
};

await client.api('/applications/bb77f42f-dacb-4ece-b3e6-285e63c24d52')
	.update(application);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Application;
use Microsoft\Graph\Generated\Models\KeyCredential;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Application();
$keyCredentialsKeyCredential1 = new KeyCredential();
$keyCredentialsKeyCredential1->setEndDateTime(new \DateTime('2024-01-11T15:31:26Z'));
$keyCredentialsKeyCredential1->setStartDateTime(new \DateTime('2023-01-12T09:31:26Z'));
$keyCredentialsKeyCredential1->setType('AsymmetricX509Cert');
$keyCredentialsKeyCredential1->setUsage('Verify');
$keyCredentialsKeyCredential1->setKey(\GuzzleHttp\Psr7\Utils::streamFor(base64_decode('base64MIIDADCCAeigAwIBAgIQejfrj3S974xI//npv7hFHTANBgkqhkiG9w0BAQsFADATMREwDwYDVQQDDAgyMDIzMDExNDAeFw0yMzAxMTIwOTA4NThaFw0yNDAxMTIwOTI4NThaMBMxETAPBgNVBAMMCDIwMjMwMTE0MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAt5vEj6j1l5wOVHR4eDGe77HWslaIVJ1NqxrXPm/...+R+U7sboj+kUvmFzXI+Ge73Liu8egL2NzOHHpO43calWgq36a9YW1yhBQR1ioEchu6jmudW3rF6ktmVqQ==')));
$keyCredentialsKeyCredential1->setDisplayName('CN=20230114');
$keyCredentialsArray []= $keyCredentialsKeyCredential1;
$keyCredentialsKeyCredential2 = new KeyCredential();
$keyCredentialsKeyCredential2->setCustomKeyIdentifier(\GuzzleHttp\Psr7\Utils::streamFor(base64_decode('52ED9B5038A47B9E2E2190715CC238359D4F8F73')));
$keyCredentialsKeyCredential2->setType('AsymmetricX509Cert');
$keyCredentialsKeyCredential2->setUsage('Verify');
$keyCredentialsKeyCredential2->setKey(\GuzzleHttp\Psr7\Utils::streamFor(base64_decode('base64MIIDADCCAeigAwIBAgIQfoIvchhpToxKEPI4iMrU1TANBgkqhkiG9w0BAQsFADATMREwDwYDVQQDDAgyMDIzMDExMzAeFw0yMzAxMTIwODI3NTJaFw0yNDAxMTIwODQ3NTJaMBMxETAPBgNVBAMMCDIwMjMwMTEzMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAw+iqg1nMjYmFcFJh/.../S5X6qoEOyJBgtfpSBANWAdA==')));
$keyCredentialsKeyCredential2->setDisplayName('CN=20230113');
$keyCredentialsArray []= $keyCredentialsKeyCredential2;
$requestBody->setKeyCredentials($keyCredentialsArray);


$result = $graphServiceClient->applications()->byApplicationId('application-id')->patch($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Applications

$params = @{
	keyCredentials = @(
		@{
			endDateTime = [System.DateTime]::Parse("2024-01-11T15:31:26Z")
			startDateTime = [System.DateTime]::Parse("2023-01-12T09:31:26Z")
			type = "AsymmetricX509Cert"
			usage = "Verify"
			key = [System.Text.Encoding]::ASCII.GetBytes("base64MIIDADCCAeigAwIBAgIQejfrj3S974xI//npv7hFHTANBgkqhkiG9w0BAQsFADATMREwDwYDVQQDDAgyMDIzMDExNDAeFw0yMzAxMTIwOTA4NThaFw0yNDAxMTIwOTI4NThaMBMxETAPBgNVBAMMCDIwMjMwMTE0MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAt5vEj6j1l5wOVHR4eDGe77HWslaIVJ1NqxrXPm/...+R+U7sboj+kUvmFzXI+Ge73Liu8egL2NzOHHpO43calWgq36a9YW1yhBQR1ioEchu6jmudW3rF6ktmVqQ==")
			displayName = "CN=20230114"
		}
		@{
			customKeyIdentifier = [System.Text.Encoding]::ASCII.GetBytes("52ED9B5038A47B9E2E2190715CC238359D4F8F73")
			type = "AsymmetricX509Cert"
			usage = "Verify"
			key = [System.Text.Encoding]::ASCII.GetBytes("base64MIIDADCCAeigAwIBAgIQfoIvchhpToxKEPI4iMrU1TANBgkqhkiG9w0BAQsFADATMREwDwYDVQQDDAgyMDIzMDExMzAeFw0yMzAxMTIwODI3NTJaFw0yNDAxMTIwODQ3NTJaMBMxETAPBgNVBAMMCDIwMjMwMTEzMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAw+iqg1nMjYmFcFJh/.../S5X6qoEOyJBgtfpSBANWAdA==")
			displayName = "CN=20230113"
		}
	)
}

Update-MgApplication -ApplicationId $applicationId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.application import Application
from msgraph.generated.models.key_credential import KeyCredential
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Application(
	key_credentials = [
		KeyCredential(
			end_date_time = "2024-01-11T15:31:26Z",
			start_date_time = "2023-01-12T09:31:26Z",
			type = "AsymmetricX509Cert",
			usage = "Verify",
			key = base64.urlsafe_b64decode("base64MIIDADCCAeigAwIBAgIQejfrj3S974xI//npv7hFHTANBgkqhkiG9w0BAQsFADATMREwDwYDVQQDDAgyMDIzMDExNDAeFw0yMzAxMTIwOTA4NThaFw0yNDAxMTIwOTI4NThaMBMxETAPBgNVBAMMCDIwMjMwMTE0MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAt5vEj6j1l5wOVHR4eDGe77HWslaIVJ1NqxrXPm/...+R+U7sboj+kUvmFzXI+Ge73Liu8egL2NzOHHpO43calWgq36a9YW1yhBQR1ioEchu6jmudW3rF6ktmVqQ=="),
			display_name = "CN=20230114",
		),
		KeyCredential(
			custom_key_identifier = base64.urlsafe_b64decode("52ED9B5038A47B9E2E2190715CC238359D4F8F73"),
			type = "AsymmetricX509Cert",
			usage = "Verify",
			key = base64.urlsafe_b64decode("base64MIIDADCCAeigAwIBAgIQfoIvchhpToxKEPI4iMrU1TANBgkqhkiG9w0BAQsFADATMREwDwYDVQQDDAgyMDIzMDExMzAeFw0yMzAxMTIwODI3NTJaFw0yNDAxMTIwODQ3NTJaMBMxETAPBgNVBAMMCDIwMjMwMTEzMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAw+iqg1nMjYmFcFJh/.../S5X6qoEOyJBgtfpSBANWAdA=="),
			display_name = "CN=20230113",
		),
	],
)

result = await graph_client.applications.by_application_id('application-id').patch(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Response

```http
HTTP/1.1 204 No Content
```

## Step 3: Test app-only authentication

You can test the app-only authentication with Microsoft Graph PowerShell, as shown in the following example.

### Request

```powershell
## Authenticate using the certificate thumbprint
Connect-MgGraph -ClientID cf34b10f-50fd-4167-acf6-4f08ddd4561b -TenantId 38d49456-54d4-455d-a8d6-c383c71e0a6d -CertificateThumbprint 52ED9B5038A47B9E2E2190715CC238359D4F8F73

## Authenticate using the certificate subject name
Connect-MgGraph -ClientID 588028ea-22c2-490e-8c6b-80cd06985e8c -TenantId 38d49456-54d4-455d-a8d6-c383c71e0a6d -CertificateName CN=20230113
```

### Response

```powershell
Welcome To Microsoft Graph!
```

To confirm that you're running the [Microsoft Graph PowerShell](https://learn.microsoft.com/en-us/powershell/microsoftgraph/) session without a signed-in user, run the following request.

```powershell
Get-MgContext
```

The response is similar to the following.

```powershell


ClientId              : cf34b10f-50fd-4167-acf6-4f08ddd4561b
TenantId              : 38d49456-54d4-455d-a8d6-c383c71e0a6d
CertificateThumbprint :
Scopes                :
AuthType              : AppOnly
AuthProviderType      : ClientCredentialProvider
CertificateName       : CN=20230113
Account               :
AppName               : testApp
ContextScope          : Process
Certificate           :
PSHostVersion         : 5.1.22621.963
ClientTimeout         : 00:05:00
```

## Conclusion

You used Microsoft Graph to update certificate credentials for an app object. This process is a programmatic alternative to using the Microsoft Entra admin center. You can also update certificate credentials for a service principal by following a similar process and calling the `https://graph.microsoft.com/v1.0/servicePrincipals/` endpoint.
