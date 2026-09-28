<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-identitycontainer-list-healthissues?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# List healthIssues

Namespace: microsoft.graph.security

Get a list of [healthIssue](https://learn.microsoft.com/en-us/graph/api/resources/security-healthissue?view=graph-rest-1.0) objects and their properties.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | SecurityIdentitiesHealth.Read.All | SecurityIdentitiesHealth.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | SecurityIdentitiesHealth.Read.All | SecurityIdentitiesHealth.ReadWrite.All |

## HTTP request

```http
GET /security/identities/healthIssues
```

## Optional query parameters

This method supports the `$count`, `$filter`, `$skip`, `$top`, and `$select` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

The following examples show how to use optional query parameters.

### Get all open health alerts

```http
GET /security/identities/healthIssues?$filter=Status eq 'open'
```

### Get the top five open health alerts

```http
GET /security/identities/healthIssues?$filter=Status eq 'open'&$top=5
```

### Get open health alerts based on issue type

```http
GET /security/identities/healthIssues?$filter=Status eq 'open' and healthIssueType eq 'global'
GET /security/identities/healthIssues?$filter=Status eq 'open' and healthIssueType eq 'sensor'
```

### Get open health alerts based on severity

```http
GET /security/identities/healthIssues?$filter=Status eq 'open' and severity eq 'medium'
GET /security/identities/healthIssues?$filter=Status eq 'open' and severity eq 'low'
```

### Get open global health alerts where the domain name or sensor DNS name ends with a specific value

The following example shows how to get global health alerts where the domain name or sensor DNS name ends with a specific value, for example, `contoso.com`.

```http
GET /security/identities/healthissues?$filter=Status eq 'open' and healthIssueType eq 'global' and domainNames/any(s:endswith(s,'contoso.com'))
GET /security/identities/healthissues?$filter=Status eq 'open' and healthIssueType eq 'global' and sensorDNSNames/any(s:endswith(s,'contoso.com'))
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [microsoft.graph.security.healthIssue](https://learn.microsoft.com/en-us/graph/api/resources/security-healthissue?view=graph-rest-1.0) objects in the response body.

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

```msgraph
GET https://graph.microsoft.com/v1.0/security/identities/healthIssues
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.Identities.HealthIssues.GetAsync();
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
healthIssues, err := graphClient.Security().Identities().HealthIssues().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.security.HealthIssueCollectionResponse result = graphClient.security().identities().healthIssues().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let healthIssues = await client.api('/security/identities/healthIssues')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->security()->identities()->healthIssues()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

Get-MgSecurityIdentityHealthIssue
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.security.identities.health_issues.get()
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
      "@odata.type": "#microsoft.graph.security.healthIssue",
      "additionalInformation": ["Descendant User Objects (Schema-Id-Guid: bf967aba-0de6-11d0-a285-00aa003049e2)"],
      "createdDateTime": "2022-07-15T12:19:27.7211305Z",
      "description": "Directory Services Object Auditing isn't configured as required on domain1.contoso.com",
      "displayName": "Directory Services Object Auditing isn't configured as required",
      "domainNames": ["domain1.contoso.com", "domain2.contoso.com"],
      "healthIssueType": "Global",
      "id": "b3c1b5fc-828c-45fa-a1e1-10d74f6d6e9c",
      "issueTypeId": "1031",
      "lastModifiedDateTime": "2022-07-15T12:19:27.7211305Z",
      "recommendations": ["Please configure the Directory Services Object Auditing events according to the guidance as described in https://aka.ms/mdi/objectauditing"],
      "recommendedActionCommands": ["Import-Module DefenderForIdentity"],
      "sensorDNSNames": ["DC1.domain1.contoso.com", "DC2.domain2.contoso.com"],
      "severity": "medium",
      "status": "open"
    }
  ]
}
```
