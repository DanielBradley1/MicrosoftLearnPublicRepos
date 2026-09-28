<!-- Source: https://learn.microsoft.com/en-us/graph/api/educationclass-list-members?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# List members of an educationClass

Namespace: microsoft.graph

Retrieves the [educationUser](https://learn.microsoft.com/en-us/graph/api/resources/educationuser?view=graph-rest-1.0) members of an [educationClass](https://learn.microsoft.com/en-us/graph/api/resources/educationclass?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | EduRoster.ReadBasic | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | EduRoster.Read.All | EduRoster.ReadWrite.All, Member.Read.Hidden |

Note

Note that if the delegated token is used, members can only see information about their own classes.

## HTTP request

```http
GET /education/classes/{id}/members
```

## Optional query parameters

This method supports the [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response, including `$search`, `$count`, and `$filter`.

When items are added or updated for this resource, they are specially indexed for use with the `$count` and `$search` query parameters. There can be a slight delay between when an item is added or updated and when it is available in the index.

For more information on OData query options, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [educationUser](https://learn.microsoft.com/en-us/graph/api/resources/educationuser?view=graph-rest-1.0) objects in the response body.

## Example

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
GET https://graph.microsoft.com/v1.0/education/classes/7e4ec76c-8276-43ef-ba10-9aaa197cb212/members
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Education.Classes["{educationClass-id}"].Members.GetAsync();
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
members, err := graphClient.Education().Classes().ByEducationClassId("educationClass-id").Members().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

EducationUserCollectionResponse result = graphClient.education().classes().byEducationClassId("{educationClass-id}").members().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let members = await client.api('/education/classes/7e4ec76c-8276-43ef-ba10-9aaa197cb212/members')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->education()->classes()->byEducationClassId('educationClass-id')->members()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Education

Get-MgEducationClassMember -EducationClassId $educationClassId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.education.classes.by_education_class_id('educationClass-id').members.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Collection(microsoft.graph.educationUser)",
  "value": [
    {
      "id": "87d349ed-44d7-43e1-9a83-5f2406dee5bd",
      "accountEnabled": true,
      "displayName": "Adele Vance",
      "givenName": "Adele",
      "surname": "Vance",
      "userPrincipalName": "AdeleV@contoso.com",
      "userType": "Member",
      "primaryRole": "teacher",
      "onPremisesInfo": {
        "immutableId": null
      },
      "teacher": {}
    },
    {
      "id": "b66ecf79-a093-4d51-86e0-efcc4531f37a",
      "accountEnabled": true,
      "displayName": "Christie Cline",
      "givenName": "Christie",
      "surname": "Cline",
      "userPrincipalName": "ChristieC@contoso.com",
      "userType": "Member",
      "primaryRole": "student",
      "onPremisesInfo": {
        "immutableId": null
      },
      "student": {}
    },
    {
      "id": "f5289423-7233-4d60-831a-fe107a8551cc",
      "accountEnabled": true,
      "displayName": "Ben Walters",
      "givenName": "Ben",
      "surname": "Walters",
      "userPrincipalName": "BenW@contoso.com",
      "userType": "Member",
      "primaryRole": "student",
      "onPremisesInfo": {
        "immutableId": null
      },
      "student": {}
    },
    {
      "id": "48d31887-5fad-4d73-a9f5-3c356e68a038",
      "accountEnabled": true,
      "displayName": "Megan Bowen",
      "givenName": "Megan",
      "surname": "Bowen",
      "userPrincipalName": "MeganB@contoso.com",
      "userType": "Member",
      "primaryRole": "teacher",
      "onPremisesInfo": {
        "immutableId": null
      },
      "teacher": {}
    },
    {
      "id": "c03e6eaa-b6ab-46d7-905b-73ec7ea1f755",
      "accountEnabled": true,
      "displayName": "Allan Deyoung",
      "givenName": "Allan",
      "surname": "Deyoung",
      "userPrincipalName": "AllanD@contoso.com",
      "userType": "Member",
      "primaryRole": "student",
      "onPremisesInfo": {
        "immutableId": null
      },
      "student": {}
    }
  ]
}
```
