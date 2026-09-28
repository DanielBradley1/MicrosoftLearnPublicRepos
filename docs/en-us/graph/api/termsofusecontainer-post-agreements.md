<!-- Source: https://learn.microsoft.com/en-us/graph/api/termsofusecontainer-post-agreements?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create agreement

Namespace: microsoft.graph

Create a new [agreement](https://learn.microsoft.com/en-us/graph/api/resources/agreement?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Agreement.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json). The following least privileged roles are supported for this operation.

- Conditional Access Administrator - least privileged
- Security Administrator

## HTTP request

```http
POST /identityGovernance/termsOfUse/agreements
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of an [agreement](https://learn.microsoft.com/en-us/graph/api/resources/agreement?view=graph-rest-1.0) object.

The following table shows the properties that are required when you create an agreement.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Display name of the agreement. |
| isViewingBeforeAcceptanceRequired | Boolean | Indicates whether the user has to expand and view the agreement before accepting. |
| fileName | String | Name of the agreement file \(for example, TOU.pdf\). |
| isDefault | Boolean | Indicates whether this is the default agreement file if the language matches the client preference. If none of the files are marked as default, the first one is treated as default. |
| language | String | The language of the agreement file in the format "languagecode2-country/regioncode2". "languagecode2" is a lowercase two-letter code derived from ISO 639-1, while "country/regioncode2" is derived from ISO 3166 and usually consists of two uppercase letters, or a BCP-47 language tag. For example, U.S. English is `en-US`. |
| data | Binary | Data that represents the terms of use for the PDF document. |

## Response

If successful, this method returns a `201, Created` response code and an [agreement](https://learn.microsoft.com/en-us/graph/api/resources/agreement?view=graph-rest-1.0) object in the response body.

## Example

### Request

In the request body, supply a JSON representation of the [agreement](https://learn.microsoft.com/en-us/graph/api/resources/agreement?view=graph-rest-1.0) object.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/identityGovernance/termsOfUse/agreements
Content-type: application/json

{
  "displayName": "Contoso ToU for guest users",
  "isViewingBeforeAcceptanceRequired": true,
  "files": [
    {
      "fileName": "TOU.pdf",
      "language": "en",
      "isDefault": true,
      "fileData": {
        "data": "SGVsbG8gd29ybGQ=//truncated-binary"
      }
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Agreement
{
	DisplayName = "Contoso ToU for guest users",
	IsViewingBeforeAcceptanceRequired = true,
	Files = new List<AgreementFileLocalization>
	{
		new AgreementFileLocalization
		{
			FileName = "TOU.pdf",
			Language = "en",
			IsDefault = true,
			FileData = new AgreementFileData
			{
				Data = Convert.FromBase64String("SGVsbG8gd29ybGQ=//truncated-binary"),
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.TermsOfUse.Agreements.PostAsync(requestBody);
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

requestBody := graphmodels.NewAgreement()
displayName := "Contoso ToU for guest users"
requestBody.SetDisplayName(&displayName) 
isViewingBeforeAcceptanceRequired := true
requestBody.SetIsViewingBeforeAcceptanceRequired(&isViewingBeforeAcceptanceRequired) 


agreementFileLocalization := graphmodels.NewAgreementFileLocalization()
fileName := "TOU.pdf"
agreementFileLocalization.SetFileName(&fileName) 
language := "en"
agreementFileLocalization.SetLanguage(&language) 
isDefault := true
agreementFileLocalization.SetIsDefault(&isDefault) 
fileData := graphmodels.NewAgreementFileData()
data := []byte("sGVsbG8gd29ybGQ=//truncated-binary")
fileData.SetData(&data) 
agreementFileLocalization.SetFileData(fileData)

files := []graphmodels.AgreementFileLocalizationable {
	agreementFileLocalization,
}
requestBody.SetFiles(files)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
agreements, err := graphClient.IdentityGovernance().TermsOfUse().Agreements().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Agreement agreement = new Agreement();
agreement.setDisplayName("Contoso ToU for guest users");
agreement.setIsViewingBeforeAcceptanceRequired(true);
LinkedList<AgreementFileLocalization> files = new LinkedList<AgreementFileLocalization>();
AgreementFileLocalization agreementFileLocalization = new AgreementFileLocalization();
agreementFileLocalization.setFileName("TOU.pdf");
agreementFileLocalization.setLanguage("en");
agreementFileLocalization.setIsDefault(true);
AgreementFileData fileData = new AgreementFileData();
byte[] data = Base64.getDecoder().decode("SGVsbG8gd29ybGQ=//truncated-binary");
fileData.setData(data);
agreementFileLocalization.setFileData(fileData);
files.add(agreementFileLocalization);
agreement.setFiles(files);
Agreement result = graphClient.identityGovernance().termsOfUse().agreements().post(agreement);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const agreement = {
  displayName: 'Contoso ToU for guest users',
  isViewingBeforeAcceptanceRequired: true,
  files: [
    {
      fileName: 'TOU.pdf',
      language: 'en',
      isDefault: true,
      fileData: {
        data: 'SGVsbG8gd29ybGQ=//truncated-binary'
      }
    }
  ]
};

await client.api('/identityGovernance/termsOfUse/agreements')
	.post(agreement);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Agreement;
use Microsoft\Graph\Generated\Models\AgreementFileLocalization;
use Microsoft\Graph\Generated\Models\AgreementFileData;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Agreement();
$requestBody->setDisplayName('Contoso ToU for guest users');
$requestBody->setIsViewingBeforeAcceptanceRequired(true);
$filesAgreementFileLocalization1 = new AgreementFileLocalization();
$filesAgreementFileLocalization1->setFileName('TOU.pdf');
$filesAgreementFileLocalization1->setLanguage('en');
$filesAgreementFileLocalization1->setIsDefault(true);
$filesAgreementFileLocalization1FileData = new AgreementFileData();
$filesAgreementFileLocalization1FileData->setData(\GuzzleHttp\Psr7\Utils::streamFor(base64_decode('SGVsbG8gd29ybGQ=//truncated-binary')));
$filesAgreementFileLocalization1->setFileData($filesAgreementFileLocalization1FileData);
$filesArray []= $filesAgreementFileLocalization1;
$requestBody->setFiles($filesArray);


$result = $graphServiceClient->identityGovernance()->termsOfUse()->agreements()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	displayName = "Contoso ToU for guest users"
	isViewingBeforeAcceptanceRequired = $true
	files = @(
		@{
			fileName = "TOU.pdf"
			language = "en"
			isDefault = $true
			fileData = @{
				data = [System.Text.Encoding]::ASCII.GetBytes("SGVsbG8gd29ybGQ=//truncated-binary")
			}
		}
	)
}

New-MgIdentityGovernanceTermsOfUseAgreement -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.agreement import Agreement
from msgraph.generated.models.agreement_file_localization import AgreementFileLocalization
from msgraph.generated.models.agreement_file_data import AgreementFileData
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Agreement(
	display_name = "Contoso ToU for guest users",
	is_viewing_before_acceptance_required = True,
	files = [
		AgreementFileLocalization(
			file_name = "TOU.pdf",
			language = "en",
			is_default = True,
			file_data = AgreementFileData(
				data = base64.urlsafe_b64decode("SGVsbG8gd29ybGQ=//truncated-binary"),
			),
		),
	],
)

result = await graph_client.identity_governance.terms_of_use.agreements.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "displayName": "MSGraph Sample",
  "isViewingBeforeAcceptanceRequired": true,
  "id": "093b947f-8363-4979-a47d-4c52b33ee1be"
}
```
