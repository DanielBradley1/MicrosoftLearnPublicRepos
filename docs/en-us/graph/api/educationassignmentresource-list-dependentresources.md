<!-- Source: https://learn.microsoft.com/en-us/graph/api/educationassignmentresource-list-dependentresources?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-29 -->

# List dependentResources

Namespace: microsoft.graph

List the dependent [education assignment resources](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentresource?view=graph-rest-1.0) for a given [education assignment resource](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentresource?view=graph-rest-1.0).

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
GET /education/classes/{class-id}/assignments/{assignment-id}/resources/{resource-id}/dependentResources
```

## Optional query parameters

This method supports the `$top`, `$filter`, `$orderby`, and `$select` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [educationAssignmentResource](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentresource?view=graph-rest-1.0) objects in the response body.

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
GET https://graph.microsoft.com/v1.0/education/classes/de45722a-c202-43a9-9dd5-d82c45bcef91/assignments/4d1ecd2d-c913-41ba-be3c-d896b65d09f0/resources/ae7beedb-488d-4534-9307-3fbc2fac29b4/dependentResources 
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Education.Classes["{educationClass-id}"].Assignments["{educationAssignment-id}"].Resources["{educationAssignmentResource-id}"].DependentResources.GetAsync();
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
dependentResources, err := graphClient.Education().Classes().ByEducationClassId("educationClass-id").Assignments().ByEducationAssignmentId("educationAssignment-id").Resources().ByEducationAssignmentResourceId("educationAssignmentResource-id").DependentResources().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

EducationAssignmentResourceCollectionResponse result = graphClient.education().classes().byEducationClassId("{educationClass-id}").assignments().byEducationAssignmentId("{educationAssignment-id}").resources().byEducationAssignmentResourceId("{educationAssignmentResource-id}").dependentResources().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let dependentResources = await client.api('/education/classes/de45722a-c202-43a9-9dd5-d82c45bcef91/assignments/4d1ecd2d-c913-41ba-be3c-d896b65d09f0/resources/ae7beedb-488d-4534-9307-3fbc2fac29b4/dependentResources')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->education()->classes()->byEducationClassId('educationClass-id')->assignments()->byEducationAssignmentId('educationAssignment-id')->resources()->byEducationAssignmentResourceId('educationAssignmentResource-id')->dependentResources()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Education

Get-MgEducationClassAssignmentResourceDependentResource -EducationClassId $educationClassId -EducationAssignmentId $educationAssignmentId -EducationAssignmentResourceId $educationAssignmentResourceId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.education.classes.by_education_class_id('educationClass-id').assignments.by_education_assignment_id('educationAssignment-id').resources.by_education_assignment_resource_id('educationAssignmentResource-id').dependent_resources.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#education/classes('de45722a-c202-43a9-9dd5-d82c45bcef91')/assignments('4d1ecd2d-c913-41ba-be3c-d896b65d09f0')/resources('ae7beedb-488d-4534-9307-3fbc2fac29b4')/dependentResources",
  "value": [
    {
      "distributeForStudentWork": true,
      "id": "090d693a-60a1-454e-8bfb-464cea5e796d",
      "resource": {
        "@odata.type": "#microsoft.graph.educationExternalResource",
        "displayName": "A Baby Polar Bear Grows Up (US History)",
        "createdDateTime": "2025-09-23T23:28:58.0188865Z",
        "lastModifiedDateTime": "2025-09-23T23:28:58.0188956Z",
        "webUrl": "https://forms.office.com/Pages/AssignmentsDesignPage.aspx#TopView=Preview&FormId=kowztj5TbU-jJ5lCY3EjmSpyRd4CwqlDndXYLEW875FUQ1lPUUE2NEk0TEMzVlVNRjhGQlgwRTRPSCQlQCN0PWcu",
        "createdBy": {
          "application": null,
          "device": null,
          "user": {
            "id": "7313562f-6ac1-43c0-803e-f345a1792f7b",
            "displayName": null
          }
        },
        "lastModifiedBy": {
          "application": null,
          "device": null,
          "user": {
            "id": "7313562f-6ac1-43c0-803e-f345a1792f7b",
            "displayName": null
          }
        }
      }
    }
  ]
}
```
