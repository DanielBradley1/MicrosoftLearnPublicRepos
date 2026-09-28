<!-- Source: https://learn.microsoft.com/en-us/graph/api/sensitivitylabel-computerightsandinheritance?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-08-20 -->

# sensitivityLabel: computeRightsAndInheritance

Namespace: microsoft.graph

Computes the rights and inheritance for sensitivity labels based on the input content and labels.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | SensitivityLabel.Evaluate | SensitivityLabel.Evaluate.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | SensitivityLabel.Evaluate | SensitivityLabel.Evaluate.All |

## HTTP request

```http
POST /security/dataSecurityAndGovernance/sensitivityLabels/computeRightsAndInheritance
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
| delegatedUserEmail | String | The upn of the user for whom the rights and inheritance are being computed. |
| locale | String | The localization code \(for example, 'en-US'\) to use for the inherited label content. |
| protectedContents | [protectedContent](https://learn.microsoft.com/en-us/graph/api/resources/protectedcontent?view=graph-rest-1.0) collection | A collection of protected content entities for which rights and inheritance are being computed. |
| supportedContentFormats | String collection | A collection of content formats \(for example, `email`, `file`\) to include in the rights and inheritance calculation. |

## Response

If successful, this action returns a `200 OK` response code and a [computeRightsAndInheritanceResult](https://learn.microsoft.com/en-us/graph/api/resources/computerightsandinheritanceresult?view=graph-rest-1.0) in the response body.

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
POST https://graph.microsoft.com/v1.0/security/dataSecurityAndGovernance/sensitivityLabels/computeRightsAndInheritance
Content-Type: application/json

{
  "delegatedUserEmail": "String",
  "locale": "String",
  "protectedContents": [
    {
      "@odata.type": "microsoft.graph.protectedContent"
    }
  ],
  "supportedContentFormats": [
    "String"
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Security.DataSecurityAndGovernance.SensitivityLabels.ComputeRightsAndInheritance;
using Microsoft.Graph.Models;

var requestBody = new ComputeRightsAndInheritancePostRequestBody
{
	DelegatedUserEmail = "String",
	Locale = "String",
	ProtectedContents = new List<ProtectedContent>
	{
		new ProtectedContent
		{
			OdataType = "microsoft.graph.protectedContent",
		},
	},
	SupportedContentFormats = new List<string>
	{
		"String",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.DataSecurityAndGovernance.SensitivityLabels.ComputeRightsAndInheritance.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphsecurity "github.com/microsoftgraph/msgraph-sdk-go/security"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphsecurity.NewComputeRightsAndInheritancePostRequestBody()
delegatedUserEmail := "String"
requestBody.SetDelegatedUserEmail(&delegatedUserEmail) 
locale := "String"
requestBody.SetLocale(&locale) 


protectedContent := graphmodels.NewProtectedContent()

protectedContents := []graphmodels.ProtectedContentable {
	protectedContent,
}
requestBody.SetProtectedContents(protectedContents)
supportedContentFormats := []string {
	"String",
}
requestBody.SetSupportedContentFormats(supportedContentFormats)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
computeRightsAndInheritance, err := graphClient.Security().DataSecurityAndGovernance().SensitivityLabels().ComputeRightsAndInheritance().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.security.datasecurityandgovernance.sensitivitylabels.computerightsandinheritance.ComputeRightsAndInheritancePostRequestBody computeRightsAndInheritancePostRequestBody = new com.microsoft.graph.security.datasecurityandgovernance.sensitivitylabels.computerightsandinheritance.ComputeRightsAndInheritancePostRequestBody();
computeRightsAndInheritancePostRequestBody.setDelegatedUserEmail("String");
computeRightsAndInheritancePostRequestBody.setLocale("String");
LinkedList<ProtectedContent> protectedContents = new LinkedList<ProtectedContent>();
ProtectedContent protectedContent = new ProtectedContent();
protectedContent.setOdataType("microsoft.graph.protectedContent");
protectedContents.add(protectedContent);
computeRightsAndInheritancePostRequestBody.setProtectedContents(protectedContents);
LinkedList<String> supportedContentFormats = new LinkedList<String>();
supportedContentFormats.add("String");
computeRightsAndInheritancePostRequestBody.setSupportedContentFormats(supportedContentFormats);
var result = graphClient.security().dataSecurityAndGovernance().sensitivityLabels().computeRightsAndInheritance().post(computeRightsAndInheritancePostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const computeRightsAndInheritanceResult = {
  delegatedUserEmail: 'String',
  locale: 'String',
  protectedContents: [
    {
      '@odata.type': 'microsoft.graph.protectedContent'
    }
  ],
  supportedContentFormats: [
    'String'
  ]
};

await client.api('/security/dataSecurityAndGovernance/sensitivityLabels/computeRightsAndInheritance')
	.post(computeRightsAndInheritanceResult);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Security\DataSecurityAndGovernance\SensitivityLabels\ComputeRightsAndInheritance\ComputeRightsAndInheritancePostRequestBody;
use Microsoft\Graph\Generated\Models\ProtectedContent;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ComputeRightsAndInheritancePostRequestBody();
$requestBody->setDelegatedUserEmail('String');
$requestBody->setLocale('String');
$protectedContentsProtectedContent1 = new ProtectedContent();
$protectedContentsProtectedContent1->setOdataType('microsoft.graph.protectedContent');
$protectedContentsArray []= $protectedContentsProtectedContent1;
$requestBody->setProtectedContents($protectedContentsArray);

$requestBody->setSupportedContentFormats(['String', ]);

$result = $graphServiceClient->security()->dataSecurityAndGovernance()->sensitivityLabels()->computeRightsAndInheritance()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

$params = @{
	delegatedUserEmail = "String"
	locale = "String"
	protectedContents = @(
		@{
			"@odata.type" = "microsoft.graph.protectedContent"
		}
	)
	supportedContentFormats = @(
	"String"
)
}

Invoke-MgAndSecurityDataSecurityAndGovernanceSensitivityLabel -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.security.datasecurityandgovernance.sensitivitylabels.compute_rights_and_inheritance.compute_rights_and_inheritance_post_request_body import ComputeRightsAndInheritancePostRequestBody
from msgraph.generated.models.protected_content import ProtectedContent
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ComputeRightsAndInheritancePostRequestBody(
	delegated_user_email = "String",
	locale = "String",
	protected_contents = [
		ProtectedContent(
			odata_type = "microsoft.graph.protectedContent",
		),
	],
	supported_content_formats = [
		"String",
	],
)

result = await graph_client.security.data_security_and_governance.sensitivity_labels.compute_rights_and_inheritance.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": {
    "@odata.type": "microsoft.graph.computeRightsAndInheritanceResult"
  }
}
```
