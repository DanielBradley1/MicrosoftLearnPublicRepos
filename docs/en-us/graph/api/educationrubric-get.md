<!-- Source: https://learn.microsoft.com/en-us/graph/api/educationrubric-get?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Get educationRubric

Namespace: microsoft.graph

Retrieve the properties and relationships of an [educationRubric](https://learn.microsoft.com/en-us/graph/api/resources/educationrubric?view=graph-rest-1.0) object. Only teachers and students can perform this operation.

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
GET /education/me/rubrics/{id}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and the requested [educationRubric](https://learn.microsoft.com/en-us/graph/api/resources/educationrubric?view=graph-rest-1.0) object in the response body.

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
GET https://graph.microsoft.com/v1.0/education/me/rubrics/199816a3-bd27-4134-bffa-b3928e8ab3a5
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Education.Me.Rubrics["{educationRubric-id}"].GetAsync();
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
rubrics, err := graphClient.Education().Me().Rubrics().ByEducationRubricId("educationRubric-id").Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

EducationRubric result = graphClient.education().me().rubrics().byEducationRubricId("{educationRubric-id}").get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let educationRubric = await client.api('/education/me/rubrics/199816a3-bd27-4134-bffa-b3928e8ab3a5')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->education()->me()->rubrics()->byEducationRubricId('educationRubric-id')->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Education

Get-MgEducationMeRubric -EducationRubricId $educationRubricId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.education.me.rubrics.by_education_rubric_id('educationRubric-id').get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#education/me/rubrics/$entity",
    "@microsoft.graph.tips": "Use $select to choose only the properties your app needs, as this can lead to performance improvements. For example: GET education/me/rubrics('<guid>')?$select=createdBy,createdDateTime",
    "displayName": "Rubric6468",
    "createdDateTime": "2024-07-11T14:03:36.5435838Z",
    "lastModifiedDateTime": "2024-07-11T14:03:55.6961018Z",
    "id": "199816a3-bd27-4134-bffa-b3928e8ab3a5",
    "description": {
        "content": "New Rubric",
        "contentType": "text"
    },
    "qualities": [
        {
            "qualityId": "93b651aa-1167-43dd-9971-fab0e242b396",
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
        },
        {
            "qualityId": "89e767f0-f66a-42f6-94f5-5b084bb17dad",
            "displayName": null,
            "weight": 33.33,
            "description": {
                "content": "Second quality",
                "contentType": "text"
            },
            "criteria": [
                {
                    "description": {
                        "content": "Second quality is excellent",
                        "contentType": "text"
                    }
                },
                {
                    "description": {
                        "content": "Second quality is good",
                        "contentType": "text"
                    }
                },
                {
                    "description": {
                        "content": "Second quality is fair",
                        "contentType": "text"
                    }
                },
                {
                    "description": {
                        "content": "Second quality is poor",
                        "contentType": "text"
                    }
                }
            ]
        },
        {
            "qualityId": "6c0e77ee-6bf5-4639-9602-3075d4774aa9",
            "displayName": null,
            "weight": 33.33,
            "description": {
                "content": "Third quality",
                "contentType": "text"
            },
            "criteria": [
                {
                    "description": {
                        "content": "Third quality is excellent",
                        "contentType": "text"
                    }
                },
                {
                    "description": {
                        "content": "Third quality is good",
                        "contentType": "text"
                    }
                },
                {
                    "description": {
                        "content": "Third quality is fair",
                        "contentType": "text"
                    }
                },
                {
                    "description": {
                        "content": "This quality is poor",
                        "contentType": "text"
                    }
                }
            ]
        }
    ],
    "levels": [
        {
            "levelId": "df3a03e2-a222-4515-aaaf-adbba692917d",
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
            "levelId": "a2f90a11-a565-4904-aaa2-c2be1c0c71f9",
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
            "levelId": "53023e26-1f8e-437a-a1fa-163683e0619a",
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
            "levelId": "7afc81dc-8ecf-4889-aa59-5bfe20c8e755",
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
            "id": "96134727-5b49-4f67-9a6b-68e133681d2a",
            "displayName": null
        }
    }
}
```
