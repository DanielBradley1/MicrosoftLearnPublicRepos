<!-- Source: https://learn.microsoft.com/en-us/graph/api/serviceprincipal-post-delegatedpermissionclassifications?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create delegatedPermissionClassification

Namespace: microsoft.graph

Classify a delegated permission by adding a [delegatedPermissionClassification](https://learn.microsoft.com/en-us/graph/api/resources/delegatedpermissionclassification?view=graph-rest-1.0) to the [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0) representing the API.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Policy.ReadWrite.PermissionGrant | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Policy.ReadWrite.PermissionGrant | Not available. |

## HTTP request

You can address the service principal using either its **id** or **appId**. **id** and **appId** are referred to as the **Object ID** and **Application \(Client\) ID**, respectively, in app registrations in the Microsoft Entra admin center.

```http
POST /servicePrincipals/{id}/delegatedPermissionClassifications
POST /servicePrincipals(appId='{appId}')/delegatedPermissionClassifications
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of an [delegatedPermissionClassification](https://learn.microsoft.com/en-us/graph/api/resources/delegatedpermissionclassification?view=graph-rest-1.0) object.

## Response

If successful, this method returns a `201 Created` response code and an [delegatedPermissionClassification](https://learn.microsoft.com/en-us/graph/api/resources/delegatedpermissionclassification?view=graph-rest-1.0) object in the response body.

## Examples

### Request

In the following example, the delegated permission "User.Read" is being classified "low".

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/servicePrincipals/{id}/delegatedPermissionClassifications
Content-Type: application/json

{
  "permissionId": "e1fe6dd8-ba31-4d61-89e7-88639da4683d",
  "permissionName": "User.Read",
  "classification": "low"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new DelegatedPermissionClassification
{
	PermissionId = "e1fe6dd8-ba31-4d61-89e7-88639da4683d",
	PermissionName = "User.Read",
	Classification = PermissionClassificationType.Low,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.ServicePrincipals["{servicePrincipal-id}"].DelegatedPermissionClassifications.PostAsync(requestBody);
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

requestBody := graphmodels.NewDelegatedPermissionClassification()
permissionId := "e1fe6dd8-ba31-4d61-89e7-88639da4683d"
requestBody.SetPermissionId(&permissionId) 
permissionName := "User.Read"
requestBody.SetPermissionName(&permissionName) 
classification := graphmodels.LOW_PERMISSIONCLASSIFICATIONTYPE 
requestBody.SetClassification(&classification) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
delegatedPermissionClassifications, err := graphClient.ServicePrincipals().ByServicePrincipalId("servicePrincipal-id").DelegatedPermissionClassifications().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

DelegatedPermissionClassification delegatedPermissionClassification = new DelegatedPermissionClassification();
delegatedPermissionClassification.setPermissionId("e1fe6dd8-ba31-4d61-89e7-88639da4683d");
delegatedPermissionClassification.setPermissionName("User.Read");
delegatedPermissionClassification.setClassification(PermissionClassificationType.Low);
DelegatedPermissionClassification result = graphClient.servicePrincipals().byServicePrincipalId("{servicePrincipal-id}").delegatedPermissionClassifications().post(delegatedPermissionClassification);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const delegatedPermissionClassification = {
  permissionId: 'e1fe6dd8-ba31-4d61-89e7-88639da4683d',
  permissionName: 'User.Read',
  classification: 'low'
};

await client.api('/servicePrincipals/{id}/delegatedPermissionClassifications')
	.post(delegatedPermissionClassification);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\DelegatedPermissionClassification;
use Microsoft\Graph\Generated\Models\PermissionClassificationType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new DelegatedPermissionClassification();
$requestBody->setPermissionId('e1fe6dd8-ba31-4d61-89e7-88639da4683d');
$requestBody->setPermissionName('User.Read');
$requestBody->setClassification(new PermissionClassificationType('low'));

$result = $graphServiceClient->servicePrincipals()->byServicePrincipalId('servicePrincipal-id')->delegatedPermissionClassifications()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Applications

$params = @{
	permissionId = "e1fe6dd8-ba31-4d61-89e7-88639da4683d"
	permissionName = "User.Read"
	classification = "low"
}

New-MgServicePrincipalDelegatedPermissionClassification -ServicePrincipalId $servicePrincipalId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.delegated_permission_classification import DelegatedPermissionClassification
from msgraph.generated.models.permission_classification_type import PermissionClassificationType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = DelegatedPermissionClassification(
	permission_id = "e1fe6dd8-ba31-4d61-89e7-88639da4683d",
	permission_name = "User.Read",
	classification = PermissionClassificationType.Low,
)

result = await graph_client.service_principals.by_service_principal_id('servicePrincipal-id').delegated_permission_classifications.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "id": "2G3-4TG6YU2J54hjnaRoPQE",
  "permissionId": "e1fe6dd8-ba31-4d61-89e7-88639da4683d",
  "permissionName": "User.Read",
  "classification": "low"
}
```
