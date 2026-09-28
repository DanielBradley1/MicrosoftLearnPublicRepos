<!-- Source: https://learn.microsoft.com/en-us/graph/api/managedtenants-managementactiontenantdeploymentstatus-changedeploymentstatus?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# managementActionTenantDeploymentStatus: changeDeploymentStatus

Namespace: microsoft.graph.managedTenants

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Changes the tenant level deployment status for the management action. This information is used to provide insights into what management actions are in a specific state. As example there might be a plan to apply the require multi-factor authentication for admins, so it would be ideal to change the status to planned to reflect the appropriate status.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | ManagedTenants.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /tenantRelationships/managedTenants/managementActionTenantDeploymentStatuses/changeDeploymentStatus
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply JSON representation of the parameters.

The following table shows the parameters that can be used with this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| tenantGroupId | String | The identifier for the tenant group. |
| tenantId | String | The Microsoft Entra tenant identifier for the [managed tenant](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenant?view=graph-rest-beta). |
| managementActionId | String | The identifier for the [management action](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-managementaction?view=graph-rest-beta). |
| managementTemplateId | String | The identifier for the [management template](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-managementtemplate?view=graph-rest-beta). |
| status | String | The new status for the [management action](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-managementaction?view=graph-rest-beta) tenant deployment. |

## Response

If successful, this action returns a `200 OK` response code and a [managementActionDeploymentStatus](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-managementactiondeploymentstatus?view=graph-rest-beta) in the response body.

## Examples

### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/beta/tenantRelationships/managedTenants/managementActionTenantDeploymentStatuses/changeDeploymentStatus
Content-Type: application/json

{
  "tenantGroupId": "String",
  "tenantId": "String",
  "managementActionId": "String",
  "managementTemplateId": "String",
  "status": "String"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.TenantRelationships.ManagedTenants.ManagementActionTenantDeploymentStatuses.MicrosoftGraphManagedTenantsChangeDeploymentStatus;

var requestBody = new ChangeDeploymentStatusPostRequestBody
{
	TenantGroupId = "String",
	TenantId = "String",
	ManagementActionId = "String",
	ManagementTemplateId = "String",
	Status = "String",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.TenantRelationships.ManagedTenants.ManagementActionTenantDeploymentStatuses.MicrosoftGraphManagedTenantsChangeDeploymentStatus.PostAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphtenantrelationships "github.com/microsoftgraph/msgraph-beta-sdk-go/tenantrelationships"
	  //other-imports
)

requestBody := graphtenantrelationships.NewChangeDeploymentStatusPostRequestBody()
tenantGroupId := "String"
requestBody.SetTenantGroupId(&tenantGroupId) 
tenantId := "String"
requestBody.SetTenantId(&tenantId) 
managementActionId := "String"
requestBody.SetManagementActionId(&managementActionId) 
managementTemplateId := "String"
requestBody.SetManagementTemplateId(&managementTemplateId) 
status := "String"
requestBody.SetStatus(&status) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
microsoftGraphManagedTenantsChangeDeploymentStatus, err := graphClient.TenantRelationships().ManagedTenants().ManagementActionTenantDeploymentStatuses().MicrosoftGraphManagedTenantsChangeDeploymentStatus().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.tenantrelationships.managedtenants.managementactiontenantdeploymentstatuses.microsoftgraphmanagedtenantschangedeploymentstatus.ChangeDeploymentStatusPostRequestBody changeDeploymentStatusPostRequestBody = new com.microsoft.graph.beta.tenantrelationships.managedtenants.managementactiontenantdeploymentstatuses.microsoftgraphmanagedtenantschangedeploymentstatus.ChangeDeploymentStatusPostRequestBody();
changeDeploymentStatusPostRequestBody.setTenantGroupId("String");
changeDeploymentStatusPostRequestBody.setTenantId("String");
changeDeploymentStatusPostRequestBody.setManagementActionId("String");
changeDeploymentStatusPostRequestBody.setManagementTemplateId("String");
changeDeploymentStatusPostRequestBody.setStatus("String");
var result = graphClient.tenantRelationships().managedTenants().managementActionTenantDeploymentStatuses().microsoftGraphManagedTenantsChangeDeploymentStatus().post(changeDeploymentStatusPostRequestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const managementActionDeploymentStatus = {
  tenantGroupId: 'String',
  tenantId: 'String',
  managementActionId: 'String',
  managementTemplateId: 'String',
  status: 'String'
};

await client.api('/tenantRelationships/managedTenants/managementActionTenantDeploymentStatuses/changeDeploymentStatus')
	.version('beta')
	.post(managementActionDeploymentStatus);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\TenantRelationships\ManagedTenants\ManagementActionTenantDeploymentStatuses\MicrosoftGraphManagedTenantsChangeDeploymentStatus\ChangeDeploymentStatusPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ChangeDeploymentStatusPostRequestBody();
$requestBody->setTenantGroupId('String');
$requestBody->setTenantId('String');
$requestBody->setManagementActionId('String');
$requestBody->setManagementTemplateId('String');
$requestBody->setStatus('String');

$result = $graphServiceClient->tenantRelationships()->managedTenants()->managementActionTenantDeploymentStatuses()->microsoftGraphManagedTenantsChangeDeploymentStatus()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.tenantrelationships.managedtenants.managementactiontenantdeploymentstatuses.microsoft_graph_managed_tenants_change_deployment_status.change_deployment_status_post_request_body import ChangeDeploymentStatusPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ChangeDeploymentStatusPostRequestBody(
	tenant_group_id = "String",
	tenant_id = "String",
	management_action_id = "String",
	management_template_id = "String",
	status = "String",
)

result = await graph_client.tenant_relationships.managed_tenants.management_action_tenant_deployment_statuses.microsoft_graph_managed_tenants_change_deployment_status.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#microsoft.graph.managedTenants.ManagementActionDeploymentStatus",
  "managementTemplateId": "e5834405-43d2-4815-867d-3dd600308d1c",
  "managementActionId": "e96a8cdb-0435-4808-9956-cf6b8ae77aa6",
  "status": "planned",
  "workloadActionDeploymentStatuses": []
}
```
