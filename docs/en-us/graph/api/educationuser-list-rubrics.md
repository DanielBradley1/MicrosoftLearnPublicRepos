<!-- Source: https://learn.microsoft.com/en-us/graph/api/educationuser-list-rubrics?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-24 -->

# List rubrics

Namespace: microsoft.graph

Retrieve a list of [educationRubric](https://learn.microsoft.com/en-us/graph/api/resources/educationrubric?view=graph-rest-1.0) objects.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | EduAssignments.ReadBasic | EduAssignments.Read, EduAssignments.ReadWrite, EduAssignments.ReadWriteBasic |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
GET /education/me/rubrics
```

## Optional query parameters

This method supports the `$top`, `$filter`, `$orderby`, and `$select` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [educationRubric](https://learn.microsoft.com/en-us/graph/api/resources/educationrubric?view=graph-rest-1.0) objects in the response body.

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
GET https://graph.microsoft.com/v1.0/education/me/rubrics
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Education.Me.Rubrics.GetAsync();
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
rubrics, err := graphClient.Education().Me().Rubrics().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

EducationRubricCollectionResponse result = graphClient.education().me().rubrics().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let rubrics = await client.api('/education/me/rubrics')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->education()->me()->rubrics()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Education

Get-MgEducationMeRubric
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.education.me.rubrics.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#education/me/rubrics",
    "@odata.nextLink": "https://graph.microsoft.com/v1.0/education/me/rubrics?$skiptoken=MyZRVkZCUVVGQlFVRkVXakJCUVVGQlFVRkJRWGxCUVVGQlNrcFZWMFpHTXpaTFJVZHNhbU5zVTFCUGNFMDBaejA5",
    "@microsoft.graph.tips": "Use $select to choose only the properties your app needs, as this can lead to performance improvements. For example: GET education/me/rubrics?$select=createdBy,createdDateTime",
    "value": [
        {
            "displayName": "Example Credit Rubric after display name patch",
            "createdDateTime": "2024-07-17T00:21:14.4479093Z",
            "lastModifiedDateTime": "2024-07-17T15:00:08.5062776Z",
            "id": "5f650796-a600-4d20-87ef-c46ae34da3bb",
            "description": {
                "content": "New Rubric",
                "contentType": "text"
            },
            "qualities": [
                {
                    "qualityId": "bdde7fc5-9a0b-4db7-9103-aeb6d4d20fbd",
                    "displayName": null,
                    "weight": 33.33,
                    "description": {
                        "content": "First quality",
                        "contentType": "text"
                    },
                    "criteria": [
                        {
                            "description": {
                                "content": "First quality is excellent",
                                "contentType": "text"
                            }
                        },
                        {
                            "description": {
                                "content": "First quality is good",
                                "contentType": "text"
                            }
                        },
                        {
                            "description": {
                                "content": "First quality is fair",
                                "contentType": "text"
                            }
                        },
                        {
                            "description": {
                                "content": "First quality is poor",
                                "contentType": "text"
                            }
                        }
                    ]
                }                
            ],
            "levels": [
                {
                    "levelId": "f0b16138-3ab2-4712-bbe0-b0a2653017a1",
                    "displayName": "Excellent",
                    "description": {
                        "content": "",
                        "contentType": "text"
                    },
                    "grading": {
                        "@odata.type": "#microsoft.graph.educationAssignmentPointsGradeType",
                        "maxPoints": 4
                    }
                },
                {
                    "levelId": "f5b1cc98-a22e-44d6-8e20-a29fb7de4860",
                    "displayName": "Good",
                    "description": {
                        "content": "",
                        "contentType": "text"
                    },
                    "grading": {
                        "@odata.type": "#microsoft.graph.educationAssignmentPointsGradeType",
                        "maxPoints": 3
                    }
                },
                {
                    "levelId": "352dfa9f-0ad3-42c5-a7b7-843dc78d83f9",
                    "displayName": "Fair",
                    "description": {
                        "content": "",
                        "contentType": "text"
                    },
                    "grading": {
                        "@odata.type": "#microsoft.graph.educationAssignmentPointsGradeType",
                        "maxPoints": 2
                    }
                },
                {
                    "levelId": "b1d9ac8f-fb57-4172-9863-4a4994bc31fa",
                    "displayName": "Poor",
                    "description": {
                        "content": "",
                        "contentType": "text"
                    },
                    "grading": {
                        "@odata.type": "#microsoft.graph.educationAssignmentPointsGradeType",
                        "maxPoints": 1
                    }
                }
            ],
            "grading": {
                "@odata.type": "#microsoft.graph.educationAssignmentPointsGradeType",
                "maxPoints": 100
            },
            "createdBy": {
                "application": null,
                "device": null,
                "user": {
                    "id": "fffafb29-e8bc-4de3-8106-be76ed2ad499",
                    "displayName": null
                }
            },
            "lastModifiedBy": {
                "application": null,
                "device": null,
                "user": {
                    "id": "fffafb29-e8bc-4de3-8106-be76ed2ad499",
                    "displayName": null
                }
            }
        }
    ]
}
```
