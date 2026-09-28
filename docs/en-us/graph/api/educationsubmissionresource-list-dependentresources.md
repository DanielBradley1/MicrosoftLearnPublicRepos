<!-- Source: https://learn.microsoft.com/en-us/graph/api/educationsubmissionresource-list-dependentresources?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-29 -->

# List dependentResources

Namespace: microsoft.graph

List the dependent [education submission resources](https://learn.microsoft.com/en-us/graph/api/resources/educationsubmissionresource?view=graph-rest-1.0) for a given [education submission resource](https://learn.microsoft.com/en-us/graph/api/resources/educationsubmissionresource?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | EduAssignments.ReadBasic | EduAssignments.ReadWrite, EduAssignments.Read |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | EduAssignments.ReadBasic.All | EduAssignments.Read.All, EduAssignments.ReadWrite.All, EduAssignments.ReadWriteBasic.All |

## HTTP request

```http
GET /education/classes/{class-id}/assignments/{assignment-id}/submissions/{submission-id}/resources/{resource-id}/dependentResources
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Optional query parameters

This method supports the `$top`, `$filter`, `$orderby`, and `$select` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [educationSubmissionResource](https://learn.microsoft.com/en-us/graph/api/resources/educationsubmissionresource?view=graph-rest-1.0) objects in the response body.

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
GET https://graph.microsoft.com/v1.0/education/classes/de45722a-c202-43a9-9dd5-d82c45bcef91/assignments/4d1ecd2d-c913-41ba-be3c-d896b65d09f0/submissions/fd921642-a333-4c4d-9335-2200f36400a9/resources/d927f453-3297-487a-8929-fa1c68f18bf3/dependentResources
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Education.Classes["{educationClass-id}"].Assignments["{educationAssignment-id}"].Submissions["{educationSubmission-id}"].Resources["{educationSubmissionResource-id}"].DependentResources.GetAsync();
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
dependentResources, err := graphClient.Education().Classes().ByEducationClassId("educationClass-id").Assignments().ByEducationAssignmentId("educationAssignment-id").Submissions().ByEducationSubmissionId("educationSubmission-id").Resources().ByEducationSubmissionResourceId("educationSubmissionResource-id").DependentResources().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

EducationSubmissionResourceCollectionResponse result = graphClient.education().classes().byEducationClassId("{educationClass-id}").assignments().byEducationAssignmentId("{educationAssignment-id}").submissions().byEducationSubmissionId("{educationSubmission-id}").resources().byEducationSubmissionResourceId("{educationSubmissionResource-id}").dependentResources().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let dependentResources = await client.api('/education/classes/de45722a-c202-43a9-9dd5-d82c45bcef91/assignments/4d1ecd2d-c913-41ba-be3c-d896b65d09f0/submissions/fd921642-a333-4c4d-9335-2200f36400a9/resources/d927f453-3297-487a-8929-fa1c68f18bf3/dependentResources')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->education()->classes()->byEducationClassId('educationClass-id')->assignments()->byEducationAssignmentId('educationAssignment-id')->submissions()->byEducationSubmissionId('educationSubmission-id')->resources()->byEducationSubmissionResourceId('educationSubmissionResource-id')->dependentResources()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Education

Get-MgEducationClassAssignmentSubmissionResourceDependentResource -EducationClassId $educationClassId -EducationAssignmentId $educationAssignmentId -EducationSubmissionId $educationSubmissionId -EducationSubmissionResourceId $educationSubmissionResourceId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.education.classes.by_education_class_id('educationClass-id').assignments.by_education_assignment_id('educationAssignment-id').submissions.by_education_submission_id('educationSubmission-id').resources.by_education_submission_resource_id('educationSubmissionResource-id').dependent_resources.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#education/classes('de45722a-c202-43a9-9dd5-d82c45bcef91')/assignments('4d1ecd2d-c913-41ba-be3c-d896b65d09f0')/submissions('fd921642-a333-4c4d-9335-2200f36400a9')/resources('d927f453-3297-487a-8929-fa1c68f18bf3')/dependentResources",
  "value": [
    {
      "assignmentResourceUrl": "https://assignments.edu.cloud.microsoft/api/v1.0/edu/classes/de45722a-c202-43a9-9dd5-d82c45bcef91/assignments/4d1ecd2d-c913-41ba-be3c-d896b65d09f0/resources/090d693a-60a1-454e-8bfb-464cea5e796d",
      "id": "d92ad210-15ce-40ba-a216-11c7baffada8",
      "resource": {
        "@odata.type": "#microsoft.graph.educationExternalResource",
        "displayName": "A Baby Polar Bear Grows Up (US History)",
        "createdDateTime": "2025-09-23T23:29:29.7443913Z",
        "lastModifiedDateTime": "2025-09-23T23:29:29.9648707Z",
        "webUrl": "https://forms.office.com/Pages/AssignmentsDesignPage.aspx#TopView=Preview&FormId=kowztj5TbU-jJ5lCY3EjmSpyRd4CwqlDndXYLEW875FUQ1lPUUE2NEk0TEMzVlVNRjhGQlgwRTRPSCQlQCN0PWcu",
        "createdBy": {
          "application": null,
          "device": null,
          "user": {
            "id": "ccb65bcd-04ba-421a-8791-a299a70904b6",
            "displayName": null
          }
        },
        "lastModifiedBy": {
          "application": null,
          "device": null,
          "user": {
            "id": "ccb65bcd-04ba-421a-8791-a299a70904b6",
            "displayName": null
          }
        }
      }
    },
    {
      "assignmentResourceUrl": null,
      "id": "7b7153b4-44d8-40f9-b3de-ad2c3e04902d",
      "resource": {
        "@odata.type": "#microsoft.graph.educationMediaResource",
        "displayName": "v_618c7257-c489-4dd3-9f97-58984184a733.webm",
        "createdDateTime": "2025-09-23T23:37:31.5828888Z",
        "lastModifiedDateTime": "2025-09-23T23:37:31.5828966Z",
        "fileUrl": "https://graph.microsoft.com/v1.0/drives/b!OttVdlohTEOX2TQZemXSranQ4OQ3V_BOoMB0C081JqWpyrOjFml8Qpy1XCbr5JBo/items/01QUVMP7NZMWMPDRSXF5C2DT4SLFS2RCUZ",
        "createdBy": {
          "application": null,
          "device": null,
          "user": {
            "id": "c0eae257-f843-4af3-a307-c698f6ac8f23",
            "displayName": null
          }
        },
        "lastModifiedBy": {
          "application": null,
          "device": null,
          "user": {
            "id": "c0eae257-f843-4af3-a307-c698f6ac8f23",
            "displayName": null
          }
        }
      }
    }
  ]
}
```
