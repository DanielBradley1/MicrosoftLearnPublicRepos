<!-- Source: https://learn.microsoft.com/en-us/graph/api/customdataprovidedresourceuploadsession-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-26 -->

# Update customDataProvidedResourceUploadSession

Namespace: microsoft.graph

Update the properties of a [customDataProvidedResourceUploadSession](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourceuploadsession?view=graph-rest-1.0) created for an [accessPackageResource](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresource?view=graph-rest-1.0) object.

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
PATCH /identityGovernance/entitlementManagement/catalogs/{accessPackageCatalogId}/resources/{accessPackageResourceId}/uploadSessions/{customDataProvidedResourceUploadSessionId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| isUploadDone | Boolean | Whether the upload session is completed. Required. |

## Response

If successful, this method returns a `200 OK` response code and an updated [customDataProvidedResourceUploadSession](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourceuploadsession?view=graph-rest-1.0) object in the response body. The only allowed update is to set **isUploadDone** to `true`.

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
PATCH https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/catalogs/{accessPackageCatalogId}/resources/{accessPackageResourceId}/uploadSessions/{customDataProvidedResourceUploadSessionId}
Content-Type: application/json

{
  "isUploadDone": true
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new CustomDataProvidedResourceUploadSession
{
	IsUploadDone = true,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.Catalogs["{accessPackageCatalog-id}"].Resources["{accessPackageResource-id}"].UploadSessions["{customDataProvidedResourceUploadSession-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewCustomDataProvidedResourceUploadSession()
isUploadDone := true
requestBody.SetIsUploadDone(&isUploadDone) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
uploadSessions, err := graphClient.IdentityGovernance().EntitlementManagement().Catalogs().ByAccessPackageCatalogId("accessPackageCatalog-id").Resources().ByAccessPackageResourceId("accessPackageResource-id").UploadSessions().ByCustomDataProvidedResourceUploadSessionId("customDataProvidedResourceUploadSession-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

CustomDataProvidedResourceUploadSession customDataProvidedResourceUploadSession = new CustomDataProvidedResourceUploadSession();
customDataProvidedResourceUploadSession.setIsUploadDone(true);
CustomDataProvidedResourceUploadSession result = graphClient.identityGovernance().entitlementManagement().catalogs().byAccessPackageCatalogId("{accessPackageCatalog-id}").resources().byAccessPackageResourceId("{accessPackageResource-id}").uploadSessions().byCustomDataProvidedResourceUploadSessionId("{customDataProvidedResourceUploadSession-id}").patch(customDataProvidedResourceUploadSession);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const customDataProvidedResourceUploadSession = {
  isUploadDone: true
};

await client.api('/identityGovernance/entitlementManagement/catalogs/{accessPackageCatalogId}/resources/{accessPackageResourceId}/uploadSessions/{customDataProvidedResourceUploadSessionId}')
	.update(customDataProvidedResourceUploadSession);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\CustomDataProvidedResourceUploadSession;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CustomDataProvidedResourceUploadSession();
$requestBody->setIsUploadDone(true);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->catalogs()->byAccessPackageCatalogId('accessPackageCatalog-id')->resources()->byAccessPackageResourceId('accessPackageResource-id')->uploadSessions()->byCustomDataProvidedResourceUploadSessionId('customDataProvidedResourceUploadSession-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	isUploadDone = $true
}

Update-MgEntitlementManagementCatalogResourceUploadSession -AccessPackageCatalogId $accessPackageCatalogId -AccessPackageResourceId $accessPackageResourceId -CustomDataProvidedResourceUploadSessionId $customDataProvidedResourceUploadSessionId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.custom_data_provided_resource_upload_session import CustomDataProvidedResourceUploadSession
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CustomDataProvidedResourceUploadSession(
	is_upload_done = True,
)

result = await graph_client.identity_governance.entitlement_management.catalogs.by_access_package_catalog_id('accessPackageCatalog-id').resources.by_access_package_resource_id('accessPackageResource-id').upload_sessions.by_custom_data_provided_resource_upload_session_id('customDataProvidedResourceUploadSession-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/entitlementManagement/catalogs('3c9f2b1e-8a4d-4e7f-9d2a-6b3e1c7f5a9d')/resources('15eeb4df-bd15-4d8b-9679-e75791dbc1d9')/uploadSessions/$entity",
  "@odata.type": "#microsoft.graph.customDataProvidedResourceAccessReviewUploadSession",
  "id": "0b64df22-1a83-472c-9556-6c3dc41742b9",
  "referenceId": "ca24f9b9-5917-4971-9b5b-07aae0aa74e8",
  "status": "complete",
  "isUploadDone": true,
  "createdDateTime": "2026-04-01T18:24:07.1484627Z",
  "stats": {
    "filesUploaded": 1,
    "totalBytesUploaded": 2394
  },
  "data": {
    "@odata.type": "#microsoft.graph.customDataProvidedResourcePayloads.accessReviewContextData",
    "reviewDefinitionId": "f5744a40-bca0-4506-a286-a8afac513d1c",
    "reviewInstanceId": "ca24f9b9-5917-4971-9b5b-07aae0aa74e8"
  },
  "files": [
    {
      "id": "22125c79-b0fe-4553-8229-6556d85b2561",
      "name": "generated_test_data_20.csv",
      "size": 2394,
      "uploadedDateTime": "2026-04-01T18:42:07.7890258Z"
    }
  ]
}
```
