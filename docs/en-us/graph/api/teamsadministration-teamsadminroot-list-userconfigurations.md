<!-- Source: https://learn.microsoft.com/en-us/graph/api/teamsadministration-teamsadminroot-list-userconfigurations?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# List userConfigurations

Namespace: microsoft.graph.teamsAdministration

Get [user configurations](https://learn.microsoft.com/en-us/graph/api/resources/teamsadministration-teamsuserconfiguration?view=graph-rest-1.0) for all Teams users who belong to a tenant.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | TeamsUserConfiguration.Read.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | TeamsUserConfiguration.Read.All | Not available. |

## HTTP request

```http
GET /admin/teams/userConfigurations
```

## Optional query parameters

This method supports the `$select`, `$filter`, `$top`, `$expand`, and `$orderBy` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [microsoft.graph.teamsAdministration.teamsUserConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/teamsadministration-teamsuserconfiguration?view=graph-rest-1.0) objects in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
GET https://graph.microsoft.com/v1.0/admin/teams/userConfigurations
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Admin.Teams.UserConfigurations.GetAsync();
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
userConfigurations, err := graphClient.Admin().Teams().UserConfigurations().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.teamsadministration.TeamsUserConfigurationCollectionResponse result = graphClient.admin().teams().userConfigurations().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let userConfigurations = await client.api('/admin/teams/userConfigurations')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->admin()->teams()->userConfigurations()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.admin.teams.user_configurations.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#admin/teams/userConfigurations",
      "id": "5c802b19-3600-83f1-1767-7b9edc7f38ab",
      "userPrincipalName": "AdeleV@contoso.com",
      "tenantId": "87d349ed-44d7-43e1-9a83-5f2406dee5bd",
      "effectivePolicyAssignments": [
        {
          "policyType": "TeamsCallingPolicy",
          "policyAssignment": {
            "displayName": "AllOn",
            "assignmentType": "group",
            "policyId": "f7593e81-772a-4455-88a3-fc9e5ebc1e4a",
            "groupId": "75ae6229-35fe-4b01-ae7f-7c50439d239c"
          }
        },
        {
          "policyType": "TeamsMeetingPolicy",
          "policyAssignment": {
            "displayName": "CustomPolicy",
            "assignmentType": "direct",
            "policyId": "J93PmFHwFcLZhWfYcBlv9pn-hG-kUWkcxmkDvpwgacw"
          }
        }
      ],
      "telephoneNumbers": [
        {
          "telephoneNumber": "+13235533696",
          "assignmentCategory": "primary"
        }
      ],
      "isEnterpriseVoiceEnabled": false,
      "featureTypes": [
        "Teams",
        "CallingPlan"
      ],
      "accountType": "user",
      "createdDateTime": "2025-01-07T09:08:50.9115993Z",
      "modifiedDateTime": "2025-01-07T09:08:50.9115993Z"
    }
  ]
}
```
