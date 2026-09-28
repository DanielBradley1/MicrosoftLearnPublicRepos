<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-categorytemplate-post-subcategories?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-03 -->

# Create subcategoryTemplate

Namespace: microsoft.graph.security

Create a new [subcategoryTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-subcategorytemplate?view=graph-rest-1.0) object.

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
POST /security/labels/categories/{categoryTemplateId}/subcategories
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [microsoft.graph.security.subcategoryTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-subcategorytemplate?view=graph-rest-1.0) object.

You can specify the following properties when creating a **subcategoryTemplate**.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Unique string that defines a sub-category name. Inherited from [microsoft.graph.security.filePlanDescriptorTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplandescriptor?view=graph-rest-1.0). Optional. |

## Response

If successful, this method returns a `201 Created` response code and a [microsoft.graph.security.subcategoryTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-subcategorytemplate?view=graph-rest-1.0) object in the response body.

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
POST https://graph.microsoft.com/v1.0/security/labels/categories/{categoryTemplateId}/subcategories
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.security.subcategoryTemplate",
  "displayName": "Vendor Invoice",
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models.Security;

var requestBody = new SubcategoryTemplate
{
	OdataType = "#microsoft.graph.security.subcategoryTemplate",
	DisplayName = "Vendor Invoice",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.Labels.Categories["{categoryTemplate-id}"].Subcategories.PostAsync(requestBody);
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

requestBody := graphmodelssecurity.NewSubcategoryTemplate()
displayName := "Vendor Invoice"
requestBody.SetDisplayName(&displayName) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
subcategories, err := graphClient.Security().Labels().Categories().ByCategoryTemplateId("categoryTemplate-id").Subcategories().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.security.SubcategoryTemplate subcategoryTemplate = new com.microsoft.graph.models.security.SubcategoryTemplate();
subcategoryTemplate.setOdataType("#microsoft.graph.security.subcategoryTemplate");
subcategoryTemplate.setDisplayName("Vendor Invoice");
com.microsoft.graph.models.security.SubcategoryTemplate result = graphClient.security().labels().categories().byCategoryTemplateId("{categoryTemplate-id}").subcategories().post(subcategoryTemplate);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const subcategoryTemplate = {
  '@odata.type': '#microsoft.graph.security.subcategoryTemplate',
  displayName: 'Vendor Invoice',
};

await client.api('/security/labels/categories/{categoryTemplateId}/subcategories')
	.post(subcategoryTemplate);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Security\SubcategoryTemplate;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SubcategoryTemplate();
$requestBody->setOdataType('#microsoft.graph.security.subcategoryTemplate');
$requestBody->setDisplayName('Vendor Invoice');

$result = $graphServiceClient->security()->labels()->categories()->byCategoryTemplateId('categoryTemplate-id')->subcategories()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

$params = @{
	"@odata.type" = "#microsoft.graph.security.subcategoryTemplate"
	displayName = "Vendor Invoice"
}

New-MgSecurityLabelCategorySubcategory -CategoryTemplateId $categoryTemplateId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.security.subcategory_template import SubcategoryTemplate
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SubcategoryTemplate(
	odata_type = "#microsoft.graph.security.subcategoryTemplate",
	display_name = "Vendor Invoice",
)

result = await graph_client.security.labels.categories.by_category_template_id('categoryTemplate-id').subcategories.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.security.subcategoryTemplate",
  "id": "2ac39915-dbeb-e933-82e2-92b981835fa0",
  "displayName": "Vendor Invoice",
  "createdBy":  {
        "user": {
          "id": "efee1b77-fb3b-4f65-99d6-274c11914d12",
          "displayName": "Admin"
        }
      },
      "createdDateTime": "2021-03-24T02:09:08Z"
    }
```
