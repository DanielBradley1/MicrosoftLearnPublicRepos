<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-labelsroot-post-citations?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-21 -->

# Create citationTemplate

Namespace: microsoft.graph.security

Create a new [citationTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-citationtemplate?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | RecordsManagement.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | RecordsManagement.ReadWrite.All | Not available. |

## HTTP request

```http
POST /security/labels/citations
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [microsoft.graph.security.citationTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-citationtemplate?view=graph-rest-1.0) object.

You can specify the following properties when creating a **citationTemplate**.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Unique string that defines a citation name. Inherited from [microsoft.graph.security.filePlanDescriptorTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplandescriptor?view=graph-rest-1.0). |
| citationUrl | String | Represents the URL to the published citation. Optional. |
| citationJurisdiction | String | Represents the jurisdiction or agency that published the citation. Optional. |

## Response

If successful, this method returns a `201 Created` response code and a [microsoft.graph.security.citationTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-citationtemplate?view=graph-rest-1.0) object in the response body.

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
POST https://graph.microsoft.com/v1.0/security/labels/citations
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.security.citationTemplate",
 "displayName": "Contoso Company Policy",
  "citationUrl": "www.citationUrl.com",
  "citationJurisdiction": "Contoso"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models.Security;

var requestBody = new CitationTemplate
{
	OdataType = "#microsoft.graph.security.citationTemplate",
	DisplayName = "Contoso Company Policy",
	CitationUrl = "www.citationUrl.com",
	CitationJurisdiction = "Contoso",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.Labels.Citations.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodelssecurity "github.com/microsoftgraph/msgraph-sdk-go/models/security"
	  //other-imports
)

requestBody := graphmodelssecurity.NewCitationTemplate()
displayName := "Contoso Company Policy"
requestBody.SetDisplayName(&displayName) 
citationUrl := "www.citationUrl.com"
requestBody.SetCitationUrl(&citationUrl) 
citationJurisdiction := "Contoso"
requestBody.SetCitationJurisdiction(&citationJurisdiction) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
citations, err := graphClient.Security().Labels().Citations().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.security.CitationTemplate citationTemplate = new com.microsoft.graph.models.security.CitationTemplate();
citationTemplate.setOdataType("#microsoft.graph.security.citationTemplate");
citationTemplate.setDisplayName("Contoso Company Policy");
citationTemplate.setCitationUrl("www.citationUrl.com");
citationTemplate.setCitationJurisdiction("Contoso");
com.microsoft.graph.models.security.CitationTemplate result = graphClient.security().labels().citations().post(citationTemplate);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const citationTemplate = {
  '@odata.type': '#microsoft.graph.security.citationTemplate',
 displayName: 'Contoso Company Policy',
  citationUrl: 'www.citationUrl.com',
  citationJurisdiction: 'Contoso'
};

await client.api('/security/labels/citations')
	.post(citationTemplate);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Security\CitationTemplate;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CitationTemplate();
$requestBody->setOdataType('#microsoft.graph.security.citationTemplate');
$requestBody->setDisplayName('Contoso Company Policy');
$requestBody->setCitationUrl('www.citationUrl.com');
$requestBody->setCitationJurisdiction('Contoso');

$result = $graphServiceClient->security()->labels()->citations()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

$params = @{
	"@odata.type" = "#microsoft.graph.security.citationTemplate"
	displayName = "Contoso Company Policy"
	citationUrl = "www.citationUrl.com"
	citationJurisdiction = "Contoso"
}

New-MgSecurityLabelCitation -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.security.citation_template import CitationTemplate
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CitationTemplate(
	odata_type = "#microsoft.graph.security.citationTemplate",
	display_name = "Contoso Company Policy",
	citation_url = "www.citationUrl.com",
	citation_jurisdiction = "Contoso",
)

result = await graph_client.security.labels.citations.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.security.citationTemplate",
  "id": "c0475d01-d532-8a53-6e26-14ea58c640bf",
  "displayName": "Contoso Company Policy",
  "createdBy":  {
    "user": {
      "id": "efee1b77-fb3b-4f65-99d6-274c11914d12",
      "displayName": "Admin"
    }
  },
  "createdDateTime" : "2021-03-24T02:09:08Z",
  "createdDateTime": "String (timestamp)",
  "citationUrl": "www.citationUrl.com",
  "citationJurisdiction": "String"
}
```
