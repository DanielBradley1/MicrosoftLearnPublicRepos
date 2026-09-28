<!-- Source: https://learn.microsoft.com/en-us/graph/api/educationassignment-get-rubric?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-01 -->

# Get educationRubric attached to educationAssignment

Namespace: microsoft.graph

Get the [educationRubric](https://learn.microsoft.com/en-us/graph/api/resources/educationrubric?view=graph-rest-1.0) object attached to an [educationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/educationassignment?view=graph-rest-1.0), if one exists. Only teachers, students, and applications with application permissions can perform this operation.

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
| Application | EduAssignments.ReadBasic.All | EduAssignments.Read.All, EduAssignments.ReadWrite.All, EduAssignments.ReadWriteBasic.All |

## HTTP request

```http
GET /education/classes/{id}/assignments/{id}/rubric
```

## Optional query parameters

This method supports the `$select` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and an [educationRubric](https://learn.microsoft.com/en-us/graph/api/resources/educationrubric?view=graph-rest-1.0) object in the response body. Otherwise, it returns a `404 Not Found` response code.

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
GET https://graph.microsoft.com/v1.0/education/classes/f1e03281-acd7-4fb0-84c3-902b3d30104c/assignments/09e2e94f-c701-45f5-98a8-cb5000195d2b/rubric
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Education.Classes["{educationClass-id}"].Assignments["{educationAssignment-id}"].Rubric.GetAsync();
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
rubric, err := graphClient.Education().Classes().ByEducationClassId("educationClass-id").Assignments().ByEducationAssignmentId("educationAssignment-id").Rubric().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

EducationRubric result = graphClient.education().classes().byEducationClassId("{educationClass-id}").assignments().byEducationAssignmentId("{educationAssignment-id}").rubric().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let educationRubric = await client.api('/education/classes/f1e03281-acd7-4fb0-84c3-902b3d30104c/assignments/09e2e94f-c701-45f5-98a8-cb5000195d2b/rubric')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->education()->classes()->byEducationClassId('educationClass-id')->assignments()->byEducationAssignmentId('educationAssignment-id')->rubric()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Education

Get-MgEducationClassAssignmentRubric -EducationClassId $educationClassId -EducationAssignmentId $educationAssignmentId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.education.classes.by_education_class_id('educationClass-id').assignments.by_education_assignment_id('educationAssignment-id').rubric.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#education/classes('f1e03281-acd7-4fb0-84c3-902b3d30104c')/assignments('09e2e94f-c701-45f5-98a8-cb5000195d2b')/rubric/$entity",
    "@microsoft.graph.tips": "Use $select to choose only the properties your app needs, as this can lead to performance improvements. For example: GET education/classes('<guid>')/assignments('<guid>')/rubric?$select=createdBy,createdDateTime",
    "displayName": "Rubric4896",
    "createdDateTime": "2024-07-11T11:20:54.1905879Z",
    "lastModifiedDateTime": "2024-07-11T11:20:54.2012531Z",
    "id": "3214c3c7-fb76-4b58-831f-82bd28b68dfd",
    "description": {
        "content": "This is the rubric we use on postman testing",
        "contentType": "text"
    },
    "qualities": [
        {
            "qualityId": "53bd0640-8210-450f-b74c-a2cc50a9b120",
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
            "qualityId": "2ebd6515-4b48-45ea-bfc2-2b8b8938ac26",
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
            "qualityId": "a4a338b7-96f0-4600-a85a-4a3b606d5960",
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
            "levelId": "83a40aa7-f34a-44ad-a337-143997bcdc44",
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
            "levelId": "ba3ea5ed-33f8-4e04-8a6b-ac67c3a39d65",
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
            "levelId": "61763a58-d253-4a53-a017-92c01f6441f8",
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
            "levelId": "afc660ea-1040-4420-a27e-dbbf118aaa6c",
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
            "id": null,
            "displayName": null
        }
    },
    "lastModifiedBy": {
        "application": null,
        "device": null,
        "user": {
            "id": null,
            "displayName": null
        }
    }
}
```
