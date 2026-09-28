<!-- Source: https://learn.microsoft.com/en-us/graph/api/accesspackageresource-post-uploadsessions?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-12 -->

# Create customDataProvidedResourceUploadSession

Namespace: microsoft.graph

Create a [customDataProvidedResourceUploadSession](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourceuploadsession?view=graph-rest-1.0) object. Only one upload session is allowed per reference instance \(for example, access review instance\) and [accessPackageResource](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresource?view=graph-rest-1.0) pair. Once you create an upload session, upload files, and complete the session, the data is processed and you cannot create another upload session for that same pair. If you encounter errors with files uploaded or need to start fresh, you can [delete the active upload session](https://learn.microsoft.com/en-us/graph/api/accesspackageresource-delete-uploadsessions?view=graph-rest-1.0) to create a new one.

The following table lists the derived types of [customDataProvidedResourceUploadSession](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourceuploadsession?view=graph-rest-1.0) that can be created. Specify the `@odata.type` in the request body to indicate the derived type.

| Derived type | Description |
| :--- | :--- |
| [customDataProvidedResourceAccessReviewUploadSession](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourceaccessreviewuploadsession?view=graph-rest-1.0) | An upload session for access review scenarios. |

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | EntitlementManagement.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | EntitlementManagement.ReadWrite.All | Not available. |

Tip

For delegated access using work or school accounts, the signed-in user must be assigned an administrator role with supported role permissions through one of the following options:

- A [role in the Entitlement Management system](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-delegate) where the least privileged role is *Catalog owner*. **This is the least privileged option**.
- More privileged [Microsoft Entra roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) supported for this operation:

  - Identity Governance Administrator

In app-only scenarios, the calling app can be assigned one of the preceding supported roles instead of the `EntitlementManagement.ReadWrite.All` application permission. The *Catalog owner* role is less privileged than the `EntitlementManagement.ReadWrite.All` application permission.

For more information, see [Delegation and roles in entitlement management](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-delegate) and [how to delegate access governance to access package managers in entitlement management](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-delegate-managers).

Tip

For delegated access using work or school accounts, the signed-in user must be assigned an administrator role with supported role permissions through one of the following options:

- A [role in the Entitlement Management system](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-delegate) where the least privileged role is *Catalog owner*. **This is the least privileged option**.
- More privileged [Microsoft Entra roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) supported for this operation:

  - Identity Governance Administrator

In app-only scenarios, the calling app can be assigned one of the preceding supported roles instead of the `EntitlementManagement.ReadWrite.All` application permission. The *Catalog owner* role is less privileged than the `EntitlementManagement.ReadWrite.All` application permission.

For more information, see [Delegation and roles in entitlement management](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-delegate) and [how to delegate access governance to access package managers in entitlement management](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-delegate-managers).

## HTTP request

```http
POST /identityGovernance/entitlementManagement/catalogs/{accessPackageCatalogId}/resources/{accessPackageResourceId}/uploadSessions
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of a [customDataProvidedResourceUploadSessionRequest](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourceuploadsessionrequest?view=graph-rest-1.0) object, and set the `@odata.type` property to the [customDataProvidedResourceUploadSession](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourceuploadsession?view=graph-rest-1.0) derived type that you want to create. For access review scenarios, set `@odata.type` to `#microsoft.graph.customDataProvidedResourceAccessReviewUploadSession`.

You can specify the following properties when creating a **customDataProvidedResourceUploadSession**.

| Property | Type | Description |
| :--- | :--- | :--- |
| data | [microsoft.graph.customDataProvidedResourcePayloads.data](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourcepayloads-data?view=graph-rest-1.0) | Contains information about the context for which data is being uploaded. For access review scenarios, use [microsoft.graph.customDataProvidedResourcePayloads.accessReviewContextData](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourcepayloads-accessreviewcontextdata?view=graph-rest-1.0). Required. |

## Response

If successful, this method returns a `201 Created` response code and a [customDataProvidedResourceUploadSession](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourceuploadsession?view=graph-rest-1.0) object in the response body.

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
POST https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/catalogs/{accessPackageCatalogId}/resources/{accessPackageResourceId}/uploadSessions
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.customDataProvidedResourceAccessReviewUploadSession",
  "data": {
    "@odata.type": "#microsoft.graph.customDataProvidedResourcePayloads.accessReviewContextData",
    "reviewDefinitionId": "9e4b1c6f-2a3d-4f8e-9b7a-5c1e2d3f4a6b",
    "reviewInstanceId": "15eeb4df-8a4d-4f8e-9b7a-6b3e1c7f5a9d"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;
using Microsoft.Graph.Models.CustomDataProvidedResourcePayloads;

var requestBody = new CustomDataProvidedResourceAccessReviewUploadSession
{
	OdataType = "#microsoft.graph.customDataProvidedResourceAccessReviewUploadSession",
	Data = new AccessReviewContextData
	{
		OdataType = "#microsoft.graph.customDataProvidedResourcePayloads.accessReviewContextData",
		ReviewDefinitionId = "9e4b1c6f-2a3d-4f8e-9b7a-5c1e2d3f4a6b",
		ReviewInstanceId = "15eeb4df-8a4d-4f8e-9b7a-6b3e1c7f5a9d",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.Catalogs["{accessPackageCatalog-id}"].Resources["{accessPackageResource-id}"].UploadSessions.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  graphmodelscustomdataprovidedresourcepayloads "github.com/microsoftgraph/msgraph-sdk-go/models/customdataprovidedresourcepayloads"
	  //other-imports
)

requestBody := graphmodels.NewCustomDataProvidedResourceUploadSession()
data := graphmodelscustomdataprovidedresourcepayloads.NewAccessReviewContextData()
reviewDefinitionId := "9e4b1c6f-2a3d-4f8e-9b7a-5c1e2d3f4a6b"
data.SetReviewDefinitionId(&reviewDefinitionId) 
reviewInstanceId := "15eeb4df-8a4d-4f8e-9b7a-6b3e1c7f5a9d"
data.SetReviewInstanceId(&reviewInstanceId) 
requestBody.SetData(data)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
uploadSessions, err := graphClient.IdentityGovernance().EntitlementManagement().Catalogs().ByAccessPackageCatalogId("accessPackageCatalog-id").Resources().ByAccessPackageResourceId("accessPackageResource-id").UploadSessions().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

CustomDataProvidedResourceAccessReviewUploadSession customDataProvidedResourceUploadSession = new CustomDataProvidedResourceAccessReviewUploadSession();
customDataProvidedResourceUploadSession.setOdataType("#microsoft.graph.customDataProvidedResourceAccessReviewUploadSession");
com.microsoft.graph.models.customdataprovidedresourcepayloads.AccessReviewContextData data = new com.microsoft.graph.models.customdataprovidedresourcepayloads.AccessReviewContextData();
data.setOdataType("#microsoft.graph.customDataProvidedResourcePayloads.accessReviewContextData");
data.setReviewDefinitionId("9e4b1c6f-2a3d-4f8e-9b7a-5c1e2d3f4a6b");
data.setReviewInstanceId("15eeb4df-8a4d-4f8e-9b7a-6b3e1c7f5a9d");
customDataProvidedResourceUploadSession.setData(data);
CustomDataProvidedResourceUploadSession result = graphClient.identityGovernance().entitlementManagement().catalogs().byAccessPackageCatalogId("{accessPackageCatalog-id}").resources().byAccessPackageResourceId("{accessPackageResource-id}").uploadSessions().post(customDataProvidedResourceUploadSession);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const customDataProvidedResourceUploadSession = {
  '@odata.type': '#microsoft.graph.customDataProvidedResourceAccessReviewUploadSession',
  data: {
    '@odata.type': '#microsoft.graph.customDataProvidedResourcePayloads.accessReviewContextData',
    reviewDefinitionId: '9e4b1c6f-2a3d-4f8e-9b7a-5c1e2d3f4a6b',
    reviewInstanceId: '15eeb4df-8a4d-4f8e-9b7a-6b3e1c7f5a9d'
  }
};

await client.api('/identityGovernance/entitlementManagement/catalogs/{accessPackageCatalogId}/resources/{accessPackageResourceId}/uploadSessions')
	.post(customDataProvidedResourceUploadSession);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\CustomDataProvidedResourceAccessReviewUploadSession;
use Microsoft\Graph\Generated\Models\CustomDataProvidedResourcePayloads\AccessReviewContextData;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CustomDataProvidedResourceAccessReviewUploadSession();
$requestBody->setOdataType('#microsoft.graph.customDataProvidedResourceAccessReviewUploadSession');
$data = new AccessReviewContextData();
$data->setOdataType('#microsoft.graph.customDataProvidedResourcePayloads.accessReviewContextData');
$data->setReviewDefinitionId('9e4b1c6f-2a3d-4f8e-9b7a-5c1e2d3f4a6b');
$data->setReviewInstanceId('15eeb4df-8a4d-4f8e-9b7a-6b3e1c7f5a9d');
$requestBody->setData($data);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->catalogs()->byAccessPackageCatalogId('accessPackageCatalog-id')->resources()->byAccessPackageResourceId('accessPackageResource-id')->uploadSessions()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	"@odata.type" = "#microsoft.graph.customDataProvidedResourceAccessReviewUploadSession"
	data = @{
		"@odata.type" = "#microsoft.graph.customDataProvidedResourcePayloads.accessReviewContextData"
		reviewDefinitionId = "9e4b1c6f-2a3d-4f8e-9b7a-5c1e2d3f4a6b"
		reviewInstanceId = "15eeb4df-8a4d-4f8e-9b7a-6b3e1c7f5a9d"
	}
}

New-MgEntitlementManagementCatalogResourceUploadSession -AccessPackageCatalogId $accessPackageCatalogId -AccessPackageResourceId $accessPackageResourceId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.custom_data_provided_resource_access_review_upload_session import CustomDataProvidedResourceAccessReviewUploadSession
from msgraph.generated.models.custom_data_provided_resource_payloads.access_review_context_data import AccessReviewContextData
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CustomDataProvidedResourceAccessReviewUploadSession(
	odata_type = "#microsoft.graph.customDataProvidedResourceAccessReviewUploadSession",
	data = AccessReviewContextData(
		odata_type = "#microsoft.graph.customDataProvidedResourcePayloads.accessReviewContextData",
		review_definition_id = "9e4b1c6f-2a3d-4f8e-9b7a-5c1e2d3f4a6b",
		review_instance_id = "15eeb4df-8a4d-4f8e-9b7a-6b3e1c7f5a9d",
	),
)

result = await graph_client.identity_governance.entitlement_management.catalogs.by_access_package_catalog_id('accessPackageCatalog-id').resources.by_access_package_resource_id('accessPackageResource-id').upload_sessions.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/entitlementManagement/catalogs('3c9f2b1e-8a4d-4e7f-9d2a-6b3e1c7f5a9d')/resources('15eeb4df-bd15-4d8b-9679-e75791dbc1d9')/uploadSessions/$entity",
  "@odata.type": "#microsoft.graph.customDataProvidedResourceAccessReviewUploadSession",
  "id": "0b64df22-1a83-472c-9556-6c3dc41742b9",
  "referenceId": "ca24f9b9-5917-4971-9b5b-07aae0aa74e8",
  "status": "active",
  "isUploadDone": false,
  "createdDateTime": "2026-04-01T18:24:07.148406Z",
  "stats": {
    "filesUploaded": 0,
    "totalBytesUploaded": 0
  },
  "data": {
    "@odata.type": "#microsoft.graph.customDataProvidedResourcePayloads.accessReviewContextData",
    "reviewDefinitionId": "f5744a40-bca0-4506-a286-a8afac513d1c",
    "reviewInstanceId": "ca24f9b9-5917-4971-9b5b-07aae0aa74e8"
  },
  "files": []
}
```
