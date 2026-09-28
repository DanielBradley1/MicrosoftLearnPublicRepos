<!-- Source: https://learn.microsoft.com/en-us/graph/api/educationmodule-list-resources?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-06-21 -->

# List module resources

Namespace: microsoft.graph

Get all the [educationModuleResource](https://learn.microsoft.com/en-us/graph/api/resources/educationmoduleresource?view=graph-rest-1.0) objects associated with a [module](https://learn.microsoft.com/en-us/graph/api/resources/educationmodule?view=graph-rest-1.0). Only teachers, students, and applications with application permissions can perform this operation.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | EduCurricula.Read | EduCurricula.ReadWrite |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | EduCurricula.Read.All | EduCurricula.ReadWrite.All |

## HTTP request

```http
GET /education/classes/{id}/modules/{id}/resources
```

## Optional query parameters

This method supports the `$expand` OData query parameter to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [educationModuleResource](https://learn.microsoft.com/en-us/graph/api/resources/educationmoduleresource?view=graph-rest-1.0) objects in the response body.

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
GET https://graph.microsoft.com/v1.0/education/classes/37d99af7-cfc5-4e3b-8566-f7d40e4a2070/modules/ba8e4215-4fb2-4dba-abe7-a8f2585177d3/resources
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Education.Classes["{educationClass-id}"].Modules["{educationModule-id}"].Resources.GetAsync();
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
resources, err := graphClient.Education().Classes().ByEducationClassId("educationClass-id").Modules().ByEducationModuleId("educationModule-id").Resources().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

EducationModuleResourceCollectionResponse result = graphClient.education().classes().byEducationClassId("{educationClass-id}").modules().byEducationModuleId("{educationModule-id}").resources().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let resources = await client.api('/education/classes/37d99af7-cfc5-4e3b-8566-f7d40e4a2070/modules/ba8e4215-4fb2-4dba-abe7-a8f2585177d3/resources')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->education()->classes()->byEducationClassId('educationClass-id')->modules()->byEducationModuleId('educationModule-id')->resources()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Education

Get-MgEducationClassModuleResource -EducationClassId $educationClassId -EducationModuleId $educationModuleId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.education.classes.by_education_class_id('educationClass-id').modules.by_education_module_id('educationModule-id').resources.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#education/classes('37d99af7-cfc5-4e3b-8566-f7d40e4a2070')/modules('ba8e4215-4fb2-4dba-abe7-a8f2585177d3')/resources",
    "@microsoft.graph.tips": "Use $select to choose only the properties your app needs, as this can lead to performance improvements. For example: GET education/classes('<guid>')/modules('<guid>')/resources?$select=resource",
    "value": [
        {
            "id": "6257a14b-4e09-4af0-b013-cbb468e64f8f",
            "resource": {
                "@odata.type": "#microsoft.graph.educationLinkResource",
                "displayName": "Where the Wonders of Learning Never Cease | Wonderopolis",
                "createdDateTime": "2023-06-23T14:39:27.2137354Z",
                "lastModifiedDateTime": "2023-06-23T14:39:27.213885Z",
                "link": "https://wonderopolis.org/",
                "createdBy": {
                    "application": null,
                    "device": null,
                    "user": {
                        "id": "cb1a4af3-0aba-4679-aa12-9f99bab0b61a",
                        "displayName": null
                    }
                },
                "lastModifiedBy": {
                    "application": null,
                    "device": null,
                    "user": {
                        "id": "cb1a4af3-0aba-4679-aa12-9f99bab0b61a",
                        "displayName": null
                    }
                }
            }
        },
        {
            "id": "445a73e6-a142-4681-87ff-beeff54cdce7",
            "resource": {
                "@odata.type": "#microsoft.graph.educationLinkResource",
                "displayName": "Where the Wonders of Learning Never Cease | Wonderopolis",
                "createdDateTime": "2023-06-23T14:40:41.0020471Z",
                "lastModifiedDateTime": "2023-06-23T14:40:41.002085Z",
                "link": "https://wonderopolis.org/",
                "createdBy": {
                    "application": null,
                    "device": null,
                    "user": {
                        "id": "cb1a4af3-0aba-4679-aa12-9f99bab0b61a",
                        "displayName": null
                    }
                },
                "lastModifiedBy": {
                    "application": null,
                    "device": null,
                    "user": {
                        "id": "cb1a4af3-0aba-4679-aa12-9f99bab0b61a",
                        "displayName": null
                    }
                }
            }
        },
        {
            "id": "a920a29d-1f5c-48d6-b647-85b91dc1dbaf",
            "resource": {
                "@odata.type": "#microsoft.graph.educationLinkResource",
                "displayName": "2023-06-24T17_13_22_819Z",
                "createdDateTime": "2023-06-23T17:49:09.475663Z",
                "lastModifiedDateTime": "2023-06-23T17:49:09.4756658Z",
                "link": "https://www.bing.com",
                "createdBy": {
                    "application": null,
                    "device": null,
                    "user": {
                        "id": "cb1a4af3-0aba-4679-aa12-9f99bab0b61a",
                        "displayName": null
                    }
                },
                "lastModifiedBy": {
                    "application": null,
                    "device": null,
                    "user": {
                        "id": "cb1a4af3-0aba-4679-aa12-9f99bab0b61a",
                        "displayName": null
                    }
                }
            }
        }
    ]
}
```
