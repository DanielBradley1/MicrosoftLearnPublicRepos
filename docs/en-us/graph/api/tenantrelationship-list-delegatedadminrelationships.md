<!-- Source: https://learn.microsoft.com/en-us/graph/api/tenantrelationship-list-delegatedadminrelationships?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-08-27 -->

# List delegatedAdminRelationships

Namespace: microsoft.graph

Get a list of the [delegatedAdminRelationship](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminrelationship?view=graph-rest-1.0) objects and their properties.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | DelegatedAdminRelationship.Read.All | DelegatedAdminRelationship.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | DelegatedAdminRelationship.Read.All | DelegatedAdminRelationship.ReadWrite.All |

## HTTP request

```http
GET /tenantRelationships/delegatedAdminRelationships
```

## Optional query parameters

This method supports the `$select`, `$filter`, `$top`, `$orderby`, `$count`, and `$skipToken` [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response.

`$top` supports up to 300 objects.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [delegatedAdminRelationship](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminrelationship?view=graph-rest-1.0) objects in the response body. The response collection can also include one or more [resellerDelegatedAdminRelationship](https://learn.microsoft.com/en-us/graph/api/resources/resellerdelegatedadminrelationship?view=graph-rest-1.0) objects.

Each **delegatedAdminRelationship** object contains an **@odata.etag** property as per RFC2616.

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
GET https://graph.microsoft.com/v1.0/tenantRelationships/delegatedAdminRelationships
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.TenantRelationships.DelegatedAdminRelationships.GetAsync();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
delegatedAdminRelationships, err := graphClient.TenantRelationships().DelegatedAdminRelationships().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

DelegatedAdminRelationshipCollectionResponse result = graphClient.tenantRelationships().delegatedAdminRelationships().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let delegatedAdminRelationships = await client.api('/tenantRelationships/delegatedAdminRelationships')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->tenantRelationships()->delegatedAdminRelationships()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Partner

Get-MgTenantRelationshipDelegatedAdminRelationship
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.tenant_relationships.delegated_admin_relationships.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/tenantRelationships/$metadata#delegatedAdminRelationships",
  "value": [
    {
      "@odata.type": "#microsoft.graph.delegatedAdminRelationship",
      "@odata.etag": "W/\"JyIwMzAwZTM0ZS0wMDAwLTAyMDAtMDAwMC02MTRjZjI1YzAwMDAiJw==\"",
      "id": "5d027261-d21f-4aa9-b7db-7fa1f56fb163-8777b240-c6f0-4469-9e98-a3205431b836",
      "displayName": "Contoso admin relationship",
      "duration": "P730D",
      "customer": {
        "tenantId": "52eaad04-13a2-4a2f-9ce8-93a294fadf36",
        "displayName": "Contoso Inc"
      },
      "accessDetails": {
        "unifiedRoles": [
          {
            "roleDefinitionId": "dd4db9a0-cc4a-4213-9f9f-70242232d97e"
          }
        ]
      },
      "status": "active",
      "autoExtendDuration": "P180D",
      "createdDateTime": "2022-02-10T11:24:42.3148266Z",
      "lastModifiedDateTime": "2022-02-10T11:26:44.9941884Z",
      "activatedDateTime": "2022-02-10T11:26:44.9941884Z",
      "endDateTime": "2024-02-10T11:24:42.3148266Z"
    },
    {
      "@odata.type": "#microsoft.graph.delegatedAdminRelationship",
      "@odata.etag": "W/\"JyIwMzAwZTM0ZS0wKklILTAyMDAtMDAwMC02MTRjZjI1YzAwMDAiJw==\"",
      "id": "1041ef52-a99b-4245-a3be-cbd3fa7c5ed1-8777b240-c6f0-4469-9e98-a3205431b836",
      "displayName": "Contoso subsidiary relationship",
      "duration": "P30D",
      "customer": {
        "tenantId": "4b827261-d21f-4aa9-b7db-7fa1f56fb163",
        "displayName": "Contoso subsidiary Inc"
      },
      "accessDetails": {
        "unifiedRoles": [
          {
            "roleDefinitionId": "29232cdf-9323-42fd-ade2-1d097af3e4de"
          },
          {
            "roleDefinitionId": "3a2c62db-5318-420d-8d74-23affee5d9d5"
          }
        ]
      },
      "status": "terminated",
      "autoExtendDuration": "PT0S",
      "createdDateTime": "2021-09-29T16:52:39.6133896Z",
      "lastModifiedDateTime": "2021-10-29T16:57:20.2101088Z",
      "activatedDateTime": "2021-09-29T16:55:20.2101088Z",
      "endDateTime": "2021-10-29T16:57:20.2101088Z"
    },
    {
      "@odata.type": "#microsoft.graph.resellerDelegatedAdminRelationship",
      "@odata.etag": "W/\"JyIwMzAwZTM0ZS0wMDAwLTAyMDAtMDAwMC02MTRjZjI1YzAwMDAiJw==\"",
      "id": "4b227261-d21f-4aa9-b7db-7fa1f56fb163-8777b240-c6f0-4469-9e98-a3205431b836",
      "displayName": "Fabrikam admin relationship",
      "duration": "P180D",
      "customer": {
        "tenantId": "52eaad04-13a2-4a2f-9ce8-93a294fadf36",
        "displayName": "Fabrikam Inc."
      },
      "accessDetails": {
        "unifiedRoles": [
          {
            "roleDefinitionId": "7be44c8a-adaf-4e2a-84d6-ab2649e08a13"
          },
          {
            "roleDefinitionId": "e8611ab8-c189-46e8-94e1-60213ab1f814"
          },
          {
            "roleDefinitionId": "fe930be7-5e62-47db-91af-98c3a49a38b1"
          },
          {
            "roleDefinitionId": "729827e3-9c14-49f7-bb1b-9608f156bbb8"
          },
          {
            "roleDefinitionId": "4d6ac14f-3453-41d0-bef9-a3e0c569773a"
          },
          {
            "roleDefinitionId": "f023fd81-a637-4b56-95fd-791ac0226033"
          },
          {
            "roleDefinitionId": "9360feb5-f418-4baa-8175-e2a00bac4301"
          },
          {
            "roleDefinitionId": "88d8e3e3-8f55-4a1e-953a-9b9898b8876b"
          },
          {
            "roleDefinitionId": "f2ef992c-3afb-46b9-b7cf-a126ee74c451"
          }
        ]
      },
      "status": "approvalPending",
      "autoExtendDuration": "PT0S",
      "createdDateTime": "2022-02-10T11:24:42.3148266Z",
      "lastModifiedDateTime": "2022-02-10T11:26:44.9941884Z",
      "activatedDateTime": null,
      "endDateTime": null,
      "isPartnerConsentPending": true,
      "indirectProviderTenantId": "60ea59db-a506-485e-94c5-d115f369e239"
    }
  ]
}
```
