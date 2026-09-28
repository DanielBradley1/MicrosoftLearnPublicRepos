<!-- Source: https://learn.microsoft.com/en-us/graph/api/managedtenants-managedtenant-list-managementactiontenantdeploymentstatuses?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-05 -->

# List managementActionTenantDeploymentStatus

Namespace: microsoft.graph.managedTenants

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get a list of the [managementActionTenantDeploymentStatus](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-managementactiontenantdeploymentstatus?view=graph-rest-beta) objects and their properties.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | ManagedTenants.Read.All | ManagedTenants.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
GET /tenantRelationships/managedTenants/managementActionTenantDeploymentStatuses
```

## Optional query parameters

This method supports the [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response, including `$apply`, `$count`, `$filter`, `$orderby`, `$select`, `$skip`, and `$top`.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [managementActionTenantDeploymentStatus](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-managementactiontenantdeploymentstatus?view=graph-rest-beta) objects in the response body.

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

```msgraph
GET https://graph.microsoft.com/beta/tenantRelationships/managedTenants/managementActionTenantDeploymentStatuses
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.TenantRelationships.ManagedTenants.ManagementActionTenantDeploymentStatuses.GetAsync();
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
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
managementActionTenantDeploymentStatuses, err := graphClient.TenantRelationships().ManagedTenants().ManagementActionTenantDeploymentStatuses().Get(context.Background(), nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.managedtenants.ManagementActionTenantDeploymentStatusCollectionResponse result = graphClient.tenantRelationships().managedTenants().managementActionTenantDeploymentStatuses().get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let managementActionTenantDeploymentStatuses = await client.api('/tenantRelationships/managedTenants/managementActionTenantDeploymentStatuses')
	.version('beta')
	.get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->tenantRelationships()->managedTenants()->managementActionTenantDeploymentStatuses()->get()->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.ManagedTenants

Get-MgBetaTenantRelationshipManagedTenantManagementActionTenantDeploymentStatus
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.tenant_relationships.managed_tenants.management_action_tenant_deployment_statuses.get()
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
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#tenantRelationships/managedTenants/managementActionTenantDeploymentStatuses",
    "value": [
        {
            "id": "df7aed9c-c05a-4fc9-b958-64fafaed911d_34298981-4fc8-4974-9486-c8909ed1521b",
            "tenantGroupId": "df7aed9c-c05a-4fc9-b958-64fafaed911d",
            "tenantId": "34298981-4fc8-4974-9486-c8909ed1521b",
            "statuses": [
                {
                    "managementTemplateId": "21230aa5-d5a9-4403-b179-baf2de242aca",
                    "managementActionId": "4274db74-99c4-40be-bbeb-da4351136be2",
                    "status": "completed",
                    "workloadActionDeploymentStatuses": [
                        {
                            "actionId": "fcb7ace7-3ea6-4474-912a-00ee78554445",
                            "status": "completed",
                            "deployedPolicyId": "949e8893-68fb-4c9d-b8a0-13c229a7e397",
                            "lastDeploymentDateTime": "2021-06-22T04:09:20.3054223Z",
                            "error": null
                        }
                    ]
                },
                {
                    "managementTemplateId": "31d57d29-2d54-4074-84bd-51c008c2e6b2",
                    "managementActionId": "f104bb7f-4854-4209-ba09-c3788f9894c5",
                    "status": "completed",
                    "workloadActionDeploymentStatuses": [
                        {
                            "actionId": "00a9a585-f51c-4b68-b4f5-f0c3165df8ac",
                            "status": "completed",
                            "deployedPolicyId": "19a8d6a6-d87e-4059-85b3-c73bfc5cea15",
                            "lastDeploymentDateTime": "2021-06-22T17:01:44.851214Z",
                            "error": null
                        }
                    ]
                }
            ]
        },
        {
            "id": "df7aed9c-c05a-4fc9-b958-64fafaed911d_38227791-a88b-4fcc-81c5-58cf77668320",
            "tenantGroupId": "df7aed9c-c05a-4fc9-b958-64fafaed911d",
            "tenantId": "38227791-a88b-4fcc-81c5-58cf77668320",
            "statuses": [
                {
                    "managementTemplateId": "12524106-036f-457f-b7a6-b003509d29c8",
                    "managementActionId": "eac82706-9f32-4274-ba5b-cf1f8ecf042b",
                    "status": "completed",
                    "workloadActionDeploymentStatuses": [
                        {
                            "actionId": "7fff5ebb-10bd-4493-b0bb-2d0cf6172f16",
                            "status": "completed",
                            "deployedPolicyId": "062107b4-236d-465a-ae62-3bb4bd31f276",
                            "lastDeploymentDateTime": "2021-06-17T13:19:47.3003079Z",
                            "error": null
                        }
                    ]
                },
                {
                    "managementTemplateId": "b2d6d189-ea31-4cf8-b75e-41210c583127",
                    "managementActionId": "55f8da1a-4eec-4fb2-9c58-4c4b3cdf7222",
                    "status": "completed",
                    "workloadActionDeploymentStatuses": [
                        {
                            "actionId": "4a1c5d34-c2f7-4fd5-a7b5-4bedd95bb8f9",
                            "status": "completed",
                            "deployedPolicyId": "606cf367-2075-40c4-a587-7914b6d83dc7",
                            "lastDeploymentDateTime": "2021-06-17T15:21:17.5296126Z",
                            "error": null
                        }
                    ]
                },
                {
                    "managementTemplateId": "31d57d29-2d54-4074-84bd-51c008c2e6b2",
                    "managementActionId": "f104bb7f-4854-4209-ba09-c3788f9894c5",
                    "status": "completed",
                    "workloadActionDeploymentStatuses": [
                        {
                            "actionId": "00a9a585-f51c-4b68-b4f5-f0c3165df8ac",
                            "status": "completed",
                            "deployedPolicyId": "60148b3e-39a2-4c0c-95a6-375a939aa756",
                            "lastDeploymentDateTime": "2021-06-22T05:54:42.7087204Z",
                            "error": null
                        }
                    ]
                },
                {
                    "managementTemplateId": "21230aa5-d5a9-4403-b179-baf2de242aca",
                    "managementActionId": "4274db74-99c4-40be-bbeb-da4351136be2",
                    "status": "riskAccepted",
                    "workloadActionDeploymentStatuses": []
                },
                {
                    "managementTemplateId": "e5834405-43d2-4815-867d-3dd600308d1c",
                    "managementActionId": "e96a8cdb-0435-4808-9956-cf6b8ae77aa6",
                    "status": "toAddress",
                    "workloadActionDeploymentStatuses": []
                }
            ]
        },
        {
            "id": "df7aed9c-c05a-4fc9-b958-64fafaed911d_4d262a25-c70a-430b-9e8e-46c31dec116b",
            "tenantGroupId": "df7aed9c-c05a-4fc9-b958-64fafaed911d",
            "tenantId": "4d262a25-c70a-430b-9e8e-46c31dec116b",
            "statuses": [
                {
                    "managementTemplateId": "31d57d29-2d54-4074-84bd-51c008c2e6b2",
                    "managementActionId": "f104bb7f-4854-4209-ba09-c3788f9894c5",
                    "status": "completed",
                    "workloadActionDeploymentStatuses": [
                        {
                            "actionId": "00a9a585-f51c-4b68-b4f5-f0c3165df8ac",
                            "status": "completed",
                            "deployedPolicyId": "aee50adb-9445-44a8-baaf-7d16b388d708",
                            "lastDeploymentDateTime": "2021-06-18T20:21:00.0934112Z",
                            "error": null
                        }
                    ]
                },
                {
                    "managementTemplateId": "12524106-036f-457f-b7a6-b003509d29c8",
                    "managementActionId": "eac82706-9f32-4274-ba5b-cf1f8ecf042b",
                    "status": "completed",
                    "workloadActionDeploymentStatuses": [
                        {
                            "actionId": "7fff5ebb-10bd-4493-b0bb-2d0cf6172f16",
                            "status": "completed",
                            "deployedPolicyId": "67635cbb-6519-44dd-bf7f-fd8752d1339b",
                            "lastDeploymentDateTime": "2021-07-09T18:53:07.113328Z",
                            "error": null
                        }
                    ]
                },
                {
                    "managementTemplateId": "21230aa5-d5a9-4403-b179-baf2de242aca",
                    "managementActionId": "4274db74-99c4-40be-bbeb-da4351136be2",
                    "status": "completed",
                    "workloadActionDeploymentStatuses": [
                        {
                            "actionId": "fcb7ace7-3ea6-4474-912a-00ee78554445",
                            "status": "completed",
                            "deployedPolicyId": "f296e4d5-7b4a-4c7b-977f-cd4e5bbbc0ea",
                            "lastDeploymentDateTime": "2021-07-09T20:12:33.6197104Z",
                            "error": null
                        }
                    ]
                }
            ]
        },
        {
            "id": "df7aed9c-c05a-4fc9-b958-64fafaed911d_791fae7d-ffda-4187-ba69-14ed55bdb026",
            "tenantGroupId": "df7aed9c-c05a-4fc9-b958-64fafaed911d",
            "tenantId": "791fae7d-ffda-4187-ba69-14ed55bdb026",
            "statuses": [
                {
                    "managementTemplateId": "12524106-036f-457f-b7a6-b003509d29c8",
                    "managementActionId": "eac82706-9f32-4274-ba5b-cf1f8ecf042b",
                    "status": "completed",
                    "workloadActionDeploymentStatuses": [
                        {
                            "actionId": "7fff5ebb-10bd-4493-b0bb-2d0cf6172f16",
                            "status": "completed",
                            "deployedPolicyId": "2e628607-5908-4dea-89c3-61438dd77805",
                            "lastDeploymentDateTime": "2021-06-17T05:14:12.671197Z",
                            "error": null
                        }
                    ]
                },
                {
                    "managementTemplateId": "21230aa5-d5a9-4403-b179-baf2de242aca",
                    "managementActionId": "4274db74-99c4-40be-bbeb-da4351136be2",
                    "status": "completed",
                    "workloadActionDeploymentStatuses": [
                        {
                            "actionId": "fcb7ace7-3ea6-4474-912a-00ee78554445",
                            "status": "completed",
                            "deployedPolicyId": "deebefee-f378-4d2e-ab1a-a7f2bf1a010e",
                            "lastDeploymentDateTime": "2021-06-17T05:15:08.801992Z",
                            "error": null
                        }
                    ]
                },
                {
                    "managementTemplateId": "e5834405-43d2-4815-867d-3dd600308d1c",
                    "managementActionId": "e96a8cdb-0435-4808-9956-cf6b8ae77aa6",
                    "status": "completed",
                    "workloadActionDeploymentStatuses": [
                        {
                            "actionId": "6a3ad0bc-5d7e-4a49-a105-c559aa4633e1",
                            "status": "completed",
                            "deployedPolicyId": "e14428f4-9890-4f6b-8416-ec40d9a59646",
                            "lastDeploymentDateTime": "2021-06-17T05:15:57.5564366Z",
                            "error": null
                        }
                    ]
                },
                {
                    "managementTemplateId": "b2d6d189-ea31-4cf8-b75e-41210c583127",
                    "managementActionId": "55f8da1a-4eec-4fb2-9c58-4c4b3cdf7222",
                    "status": "completed",
                    "workloadActionDeploymentStatuses": [
                        {
                            "actionId": "4a1c5d34-c2f7-4fd5-a7b5-4bedd95bb8f9",
                            "status": "completed",
                            "deployedPolicyId": "220bbe5d-2167-4ba1-8c7d-67bd56b0e068",
                            "lastDeploymentDateTime": "2021-06-17T05:16:35.1968434Z",
                            "error": null
                        }
                    ]
                },
                {
                    "managementTemplateId": "31d57d29-2d54-4074-84bd-51c008c2e6b2",
                    "managementActionId": "f104bb7f-4854-4209-ba09-c3788f9894c5",
                    "status": "completed",
                    "workloadActionDeploymentStatuses": [
                        {
                            "actionId": "00a9a585-f51c-4b68-b4f5-f0c3165df8ac",
                            "status": "completed",
                            "deployedPolicyId": "50553bd7-560e-4c0e-9c80-78f4ae9560e5",
                            "lastDeploymentDateTime": "2021-06-17T05:17:46.2079328Z",
                            "error": null
                        }
                    ]
                },
                {
                    "managementTemplateId": "e2cadc41-a08f-45e7-8eb1-942d224dfb9a",
                    "managementActionId": "b22a4713-8428-4952-8cac-d48962ecbdc9",
                    "status": "completed",
                    "workloadActionDeploymentStatuses": [
                        {
                            "actionId": "46b80b42-06c7-45b4-b6fb-aa0aecace87b",
                            "status": "completed",
                            "deployedPolicyId": null,
                            "lastDeploymentDateTime": "2021-06-17T05:18:16.7581968Z",
                            "error": null
                        }
                    ]
                }
            ]
        }
    ]
}
```
