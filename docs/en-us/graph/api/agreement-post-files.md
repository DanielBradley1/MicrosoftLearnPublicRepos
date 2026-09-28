<!-- Source: https://learn.microsoft.com/en-us/graph/api/agreement-post-files?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-08 -->

# Create agreementFileLocalization

Namespace: microsoft.graph

Create a new localized agreement file.

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
POST /agreements/{agreementsId}/files
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [agreementFileLocalization](https://learn.microsoft.com/en-us/graph/api/resources/agreementfilelocalization?view=graph-rest-1.0) object.

You can specify the following properties when creating an **agreementFileLocalization**.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Localized display name of the policy file of an agreement. The localized display name is shown to end users who view the agreement. |
| fileData | [agreementFileData](https://learn.microsoft.com/en-us/graph/api/resources/agreementfiledata?view=graph-rest-1.0) | Data that represents the terms of use PDF document. |
| fileName | String | Name of the agreement file \(for example, TOU.pdf\). |
| isDefault | Boolean | If none of the languages matches the client preference, indicates whether this is the default agreement file . If none of the files are marked as default, the first one is treated as the default. Read-only. |
| isMajorVersion | Boolean | Indicates whether the agreement file is a major version update. Major version updates invalidate the agreement's acceptances on the corresponding language. |
| language | String | The language of the agreement file in the format "languagecode2-country/regioncode2". "languagecode2" is a lowercase two-letter code derived from ISO 639-1, while "country/regioncode2" is derived from ISO 3166 and usually consists of two uppercase letters, or a BCP-47 language tag. For example, U.S. English is `en-US`. |

## Response

If successful, this method returns a `200 OK` response code and an [agreementFileLocalization](https://learn.microsoft.com/en-us/graph/api/resources/agreementfilelocalization?view=graph-rest-1.0) object in the response body.

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
POST https://graph.microsoft.com/v1.0/identityGovernance/termsOfUse/agreements/94410bbf-3d3e-4683-8149-f034e55c39dd/files
Content-Type: application/json

{
    "fileName": "Contoso ToU for guest users (French)",
    "language": "fr-FR",
    "isDefault": false,
    "isMajorVersion": false,
    "displayName": "Contoso ToU for guest users (French)",
    "fileData": {
        "data": "base64JVBERi0xLjUKJb/3ov4KNCAwIG9iago8PCAvTGluZWFyaX//truncated-binary-data"
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AgreementFileLocalization
{
	FileName = "Contoso ToU for guest users (French)",
	Language = "fr-FR",
	IsDefault = false,
	IsMajorVersion = false,
	DisplayName = "Contoso ToU for guest users (French)",
	FileData = new AgreementFileData
	{
		Data = Convert.FromBase64String("base64JVBERi0xLjUKJb/3ov4KNCAwIG9iago8PCAvTGluZWFyaX//truncated-binary-data"),
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.TermsOfUse.Agreements["{agreement-id}"].Files.PostAsync(requestBody);
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

requestBody := graphmodels.NewAgreementFileLocalization()
fileName := "Contoso ToU for guest users (French)"
requestBody.SetFileName(&fileName) 
language := "fr-FR"
requestBody.SetLanguage(&language) 
isDefault := false
requestBody.SetIsDefault(&isDefault) 
isMajorVersion := false
requestBody.SetIsMajorVersion(&isMajorVersion) 
displayName := "Contoso ToU for guest users (French)"
requestBody.SetDisplayName(&displayName) 
fileData := graphmodels.NewAgreementFileData()
data := []byte("base64JVBERi0xLjUKJb/3ov4KNCAwIG9iago8PCAvTGluZWFyaX//truncated-binary-data")
fileData.SetData(&data) 
requestBody.SetFileData(fileData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
files, err := graphClient.IdentityGovernance().TermsOfUse().Agreements().ByAgreementId("agreement-id").Files().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AgreementFileLocalization agreementFileLocalization = new AgreementFileLocalization();
agreementFileLocalization.setFileName("Contoso ToU for guest users (French)");
agreementFileLocalization.setLanguage("fr-FR");
agreementFileLocalization.setIsDefault(false);
agreementFileLocalization.setIsMajorVersion(false);
agreementFileLocalization.setDisplayName("Contoso ToU for guest users (French)");
AgreementFileData fileData = new AgreementFileData();
byte[] data = Base64.getDecoder().decode("base64JVBERi0xLjUKJb/3ov4KNCAwIG9iago8PCAvTGluZWFyaX//truncated-binary-data");
fileData.setData(data);
agreementFileLocalization.setFileData(fileData);
AgreementFileLocalization result = graphClient.identityGovernance().termsOfUse().agreements().byAgreementId("{agreement-id}").files().post(agreementFileLocalization);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const agreementFileLocalization = {
    fileName: 'Contoso ToU for guest users (French)',
    language: 'fr-FR',
    isDefault: false,
    isMajorVersion: false,
    displayName: 'Contoso ToU for guest users (French)',
    fileData: {
        data: 'base64JVBERi0xLjUKJb/3ov4KNCAwIG9iago8PCAvTGluZWFyaX//truncated-binary-data'
    }
};

await client.api('/identityGovernance/termsOfUse/agreements/94410bbf-3d3e-4683-8149-f034e55c39dd/files')
	.post(agreementFileLocalization);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AgreementFileLocalization;
use Microsoft\Graph\Generated\Models\AgreementFileData;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AgreementFileLocalization();
$requestBody->setFileName('Contoso ToU for guest users (French)');
$requestBody->setLanguage('fr-FR');
$requestBody->setIsDefault(false);
$requestBody->setIsMajorVersion(false);
$requestBody->setDisplayName('Contoso ToU for guest users (French)');
$fileData = new AgreementFileData();
$fileData->setData(\GuzzleHttp\Psr7\Utils::streamFor(base64_decode('base64JVBERi0xLjUKJb/3ov4KNCAwIG9iago8PCAvTGluZWFyaX//truncated-binary-data')));
$requestBody->setFileData($fileData);

$result = $graphServiceClient->identityGovernance()->termsOfUse()->agreements()->byAgreementId('agreement-id')->files()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	fileName = "Contoso ToU for guest users (French)"
	language = "fr-FR"
	isDefault = $false
	isMajorVersion = $false
	displayName = "Contoso ToU for guest users (French)"
	fileData = @{
		data = [System.Text.Encoding]::ASCII.GetBytes("base64JVBERi0xLjUKJb/3ov4KNCAwIG9iago8PCAvTGluZWFyaX//truncated-binary-data")
	}
}

New-MgIdentityGovernanceTermsOfUseAgreementFile -AgreementId $agreementId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.agreement_file_localization import AgreementFileLocalization
from msgraph.generated.models.agreement_file_data import AgreementFileData
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AgreementFileLocalization(
	file_name = "Contoso ToU for guest users (French)",
	language = "fr-FR",
	is_default = False,
	is_major_version = False,
	display_name = "Contoso ToU for guest users (French)",
	file_data = AgreementFileData(
		data = base64.urlsafe_b64decode("base64JVBERi0xLjUKJb/3ov4KNCAwIG9iago8PCAvTGluZWFyaX//truncated-binary-data"),
	),
)

result = await graph_client.identity_governance.terms_of_use.agreements.by_agreement_id('agreement-id').files.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/termsOfUse/agreements('94410bbf-3d3e-4683-8149-f034e55c39dd')/files/$entity",
    "id": "90d1723c-52c1-40e3-a51a-da99a82c0327",
    "fileName": "Contoso ToU for guest users (French)",
    "displayName": "Contoso ToU for guest users (French)",
    "language": "fr-FR",
    "isDefault": false,
    "isMajorVersion": false,
    "createdDateTime": "2022-03-04T14:38:22.8292386Z",
    "fileData": {
        "data": "base64JVBERi0xLjUKJb/"
    }
}
```
