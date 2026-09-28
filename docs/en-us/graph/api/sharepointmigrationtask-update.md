<!-- Source: https://learn.microsoft.com/en-us/graph/api/sharepointmigrationtask-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# Create or update sharePointMigrationTask

Create or update a [sharePointMigrationTask](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationtask?view=graph-rest-beta) to migrate a resource from the source organization to the target organization, using the sharePointMigrationTaskParameters. The resource can be a user, a group, or a site.

> **Note:** Based on the OData standard, the entire **sharePointMigrationTask** structure must be included in the request body, although only **sharePointMigrationTaskParameters** are used to instantiate the task. For required properties such as **id** and **status**, empty or default values can be provided because they're ignored during initial task creation.

When an existing **sharePointMigrationTask** is retrieved, it might contain not only the specifics of the source and target organizations and resources, but also the status of the migration and errors encountered during the migration operation.

The API calls occur on the source site and only add list items to the my site root web, for example, `contoso-my.sharepoint.com`. Then, it triggers a multi-geo site move job in the backend to enqueue and orchestrate several tenant workflow jobs, such as backup, restore, and cleanup, supported by TJ infrastructure.

The OData type of **sharePointResourceMigrationParameters** differentiates user migration from site migration, rather than using different subpaths. For a user's OneDrive migration, specify **sharePointUserMigrationParameters**. If this migration task is a regular SharePoint site migration, specify **sharePointSiteMigrationParameters**. If this migration task is a group-connected site migration, specify **sharePointGroupMigrationParameters**.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | SharePointCrossTenantMigration.Manage.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | SharePointCrossTenantMigration.Manage.All | Not available. |

## HTTP request

```http
POST /solutions/sharePoint/migrations/crossOrganizationMigrationTasks
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| parameters | [sharePointMigrationTaskParameters](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationtaskparameters?view=graph-rest-beta) | Encapsulates the parameters necessary to migrate a specific source resource. |

## Response

If successful, this method returns a `200 OK` response code and an updated [sharePointMigrationTask](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationtask?view=graph-rest-beta) object in the response body.

## Examples

### Example 1: Create a user migration task by using the user principal name

The following example shows how to create a user migration task by **userPrincipalName**.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/beta/solutions/sharePoint/migrations/crossOrganizationMigrationTasks
Content-Type: application/json

{
  "parameters": {
    "@odata.type": "#microsoft.graph.sharePointUserMigrationTaskParameters",
    "targetOrganizationHost": "https://fabrico-my.sharepoint.com",
    "sourceUserIdentity": {
      "userPrincipalName": "source-user@contoso.onmicrosoft.com"
    },
    "targetUserIdentity": {
      "userPrincipalName": "target-user@fabrico.onmicrosoft.com"
    }
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new SharePointMigrationTask
{
	Parameters = new SharePointUserMigrationTaskParameters
	{
		OdataType = "#microsoft.graph.sharePointUserMigrationTaskParameters",
		TargetOrganizationHost = "https://fabrico-my.sharepoint.com",
		SourceUserIdentity = new UserIdentity
		{
			UserPrincipalName = "source-user@contoso.onmicrosoft.com",
		},
		TargetUserIdentity = new UserIdentity
		{
			UserPrincipalName = "target-user@fabrico.onmicrosoft.com",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.SharePoint.Migrations.CrossOrganizationMigrationTasks.PostAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewSharePointMigrationTask()
parameters := graphmodels.NewSharePointUserMigrationTaskParameters()
targetOrganizationHost := "https://fabrico-my.sharepoint.com"
parameters.SetTargetOrganizationHost(&targetOrganizationHost) 
sourceUserIdentity := graphmodels.NewUserIdentity()
userPrincipalName := "source-user@contoso.onmicrosoft.com"
sourceUserIdentity.SetUserPrincipalName(&userPrincipalName) 
parameters.SetSourceUserIdentity(sourceUserIdentity)
targetUserIdentity := graphmodels.NewUserIdentity()
userPrincipalName := "target-user@fabrico.onmicrosoft.com"
targetUserIdentity.SetUserPrincipalName(&userPrincipalName) 
parameters.SetTargetUserIdentity(targetUserIdentity)
requestBody.SetParameters(parameters)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
crossOrganizationMigrationTasks, err := graphClient.Solutions().SharePoint().Migrations().CrossOrganizationMigrationTasks().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

SharePointMigrationTask sharePointMigrationTask = new SharePointMigrationTask();
SharePointUserMigrationTaskParameters parameters = new SharePointUserMigrationTaskParameters();
parameters.setOdataType("#microsoft.graph.sharePointUserMigrationTaskParameters");
parameters.setTargetOrganizationHost("https://fabrico-my.sharepoint.com");
UserIdentity sourceUserIdentity = new UserIdentity();
sourceUserIdentity.setUserPrincipalName("source-user@contoso.onmicrosoft.com");
parameters.setSourceUserIdentity(sourceUserIdentity);
UserIdentity targetUserIdentity = new UserIdentity();
targetUserIdentity.setUserPrincipalName("target-user@fabrico.onmicrosoft.com");
parameters.setTargetUserIdentity(targetUserIdentity);
sharePointMigrationTask.setParameters(parameters);
SharePointMigrationTask result = graphClient.solutions().sharePoint().migrations().crossOrganizationMigrationTasks().post(sharePointMigrationTask);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const sharePointMigrationTask = {
  parameters: {
    '@odata.type': '#microsoft.graph.sharePointUserMigrationTaskParameters',
    targetOrganizationHost: 'https://fabrico-my.sharepoint.com',
    sourceUserIdentity: {
      userPrincipalName: 'source-user@contoso.onmicrosoft.com'
    },
    targetUserIdentity: {
      userPrincipalName: 'target-user@fabrico.onmicrosoft.com'
    }
  }
};

await client.api('/solutions/sharePoint/migrations/crossOrganizationMigrationTasks')
	.version('beta')
	.post(sharePointMigrationTask);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\SharePointMigrationTask;
use Microsoft\Graph\Beta\Generated\Models\SharePointUserMigrationTaskParameters;
use Microsoft\Graph\Beta\Generated\Models\UserIdentity;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SharePointMigrationTask();
$parameters = new SharePointUserMigrationTaskParameters();
$parameters->setOdataType('#microsoft.graph.sharePointUserMigrationTaskParameters');
$parameters->setTargetOrganizationHost('https://fabrico-my.sharepoint.com');
$parametersSourceUserIdentity = new UserIdentity();
$parametersSourceUserIdentity->setUserPrincipalName('source-user@contoso.onmicrosoft.com');
$parameters->setSourceUserIdentity($parametersSourceUserIdentity);
$parametersTargetUserIdentity = new UserIdentity();
$parametersTargetUserIdentity->setUserPrincipalName('target-user@fabrico.onmicrosoft.com');
$parameters->setTargetUserIdentity($parametersTargetUserIdentity);
$requestBody->setParameters($parameters);

$result = $graphServiceClient->solutions()->sharePoint()->migrations()->crossOrganizationMigrationTasks()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.share_point_migration_task import SharePointMigrationTask
from msgraph_beta.generated.models.share_point_user_migration_task_parameters import SharePointUserMigrationTaskParameters
from msgraph_beta.generated.models.user_identity import UserIdentity
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SharePointMigrationTask(
	parameters = SharePointUserMigrationTaskParameters(
		odata_type = "#microsoft.graph.sharePointUserMigrationTaskParameters",
		target_organization_host = "https://fabrico-my.sharepoint.com",
		source_user_identity = UserIdentity(
			user_principal_name = "source-user@contoso.onmicrosoft.com",
		),
		target_user_identity = UserIdentity(
			user_principal_name = "target-user@fabrico.onmicrosoft.com",
		),
	),
)

result = await graph_client.solutions.share_point.migrations.cross_organization_migration_tasks.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "3ed6d46d-13a3-4995-b6ea-a74a20b1fac0",
  "status": "notStarted",
  "parameters": {
    "@odata.type": "#microsoft.graph.sharePointUserMigrationTaskParameters",
    "targetOrganizationHost": "https://fabrico-my.sharepoint.com",
    "sourceUserIdentity": {
      "userPrincipalName": "source-user@contoso.onmicrosoft.com"
    },
    "targetUserIdentity": {
      "userPrincipalName": "target-user@fabrico.onmicrosoft.com"
    }
  }
}
```

### Example 2: Create a user migration task by using the user object ID

The following example shows how to create a user migration task by **userObjectId**.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/beta/solutions/sharePoint/migrations/crossOrganizationMigrationTasks
Content-Type: application/json

{
  "parameters": {
    "@odata.type": "#microsoft.graph.sharePointUserMigrationTaskParameters",
    "targetOrganizationHost": "https://fabrico-my.sharepoint.com",
    "sourceUserIdentity": {
      "id": "da157a29-f793-4dd6-9c73-41d2c73c2546"
    },
    "targetUserIdentity": {
      "id": "cb53ea98-6151-44cc-9c21-098a3c3e3988"
    }
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new SharePointMigrationTask
{
	Parameters = new SharePointUserMigrationTaskParameters
	{
		OdataType = "#microsoft.graph.sharePointUserMigrationTaskParameters",
		TargetOrganizationHost = "https://fabrico-my.sharepoint.com",
		SourceUserIdentity = new UserIdentity
		{
			Id = "da157a29-f793-4dd6-9c73-41d2c73c2546",
		},
		TargetUserIdentity = new UserIdentity
		{
			Id = "cb53ea98-6151-44cc-9c21-098a3c3e3988",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.SharePoint.Migrations.CrossOrganizationMigrationTasks.PostAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewSharePointMigrationTask()
parameters := graphmodels.NewSharePointUserMigrationTaskParameters()
targetOrganizationHost := "https://fabrico-my.sharepoint.com"
parameters.SetTargetOrganizationHost(&targetOrganizationHost) 
sourceUserIdentity := graphmodels.NewUserIdentity()
id := "da157a29-f793-4dd6-9c73-41d2c73c2546"
sourceUserIdentity.SetId(&id) 
parameters.SetSourceUserIdentity(sourceUserIdentity)
targetUserIdentity := graphmodels.NewUserIdentity()
id := "cb53ea98-6151-44cc-9c21-098a3c3e3988"
targetUserIdentity.SetId(&id) 
parameters.SetTargetUserIdentity(targetUserIdentity)
requestBody.SetParameters(parameters)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
crossOrganizationMigrationTasks, err := graphClient.Solutions().SharePoint().Migrations().CrossOrganizationMigrationTasks().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

SharePointMigrationTask sharePointMigrationTask = new SharePointMigrationTask();
SharePointUserMigrationTaskParameters parameters = new SharePointUserMigrationTaskParameters();
parameters.setOdataType("#microsoft.graph.sharePointUserMigrationTaskParameters");
parameters.setTargetOrganizationHost("https://fabrico-my.sharepoint.com");
UserIdentity sourceUserIdentity = new UserIdentity();
sourceUserIdentity.setId("da157a29-f793-4dd6-9c73-41d2c73c2546");
parameters.setSourceUserIdentity(sourceUserIdentity);
UserIdentity targetUserIdentity = new UserIdentity();
targetUserIdentity.setId("cb53ea98-6151-44cc-9c21-098a3c3e3988");
parameters.setTargetUserIdentity(targetUserIdentity);
sharePointMigrationTask.setParameters(parameters);
SharePointMigrationTask result = graphClient.solutions().sharePoint().migrations().crossOrganizationMigrationTasks().post(sharePointMigrationTask);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const sharePointMigrationTask = {
  parameters: {
    '@odata.type': '#microsoft.graph.sharePointUserMigrationTaskParameters',
    targetOrganizationHost: 'https://fabrico-my.sharepoint.com',
    sourceUserIdentity: {
      id: 'da157a29-f793-4dd6-9c73-41d2c73c2546'
    },
    targetUserIdentity: {
      id: 'cb53ea98-6151-44cc-9c21-098a3c3e3988'
    }
  }
};

await client.api('/solutions/sharePoint/migrations/crossOrganizationMigrationTasks')
	.version('beta')
	.post(sharePointMigrationTask);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\SharePointMigrationTask;
use Microsoft\Graph\Beta\Generated\Models\SharePointUserMigrationTaskParameters;
use Microsoft\Graph\Beta\Generated\Models\UserIdentity;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SharePointMigrationTask();
$parameters = new SharePointUserMigrationTaskParameters();
$parameters->setOdataType('#microsoft.graph.sharePointUserMigrationTaskParameters');
$parameters->setTargetOrganizationHost('https://fabrico-my.sharepoint.com');
$parametersSourceUserIdentity = new UserIdentity();
$parametersSourceUserIdentity->setId('da157a29-f793-4dd6-9c73-41d2c73c2546');
$parameters->setSourceUserIdentity($parametersSourceUserIdentity);
$parametersTargetUserIdentity = new UserIdentity();
$parametersTargetUserIdentity->setId('cb53ea98-6151-44cc-9c21-098a3c3e3988');
$parameters->setTargetUserIdentity($parametersTargetUserIdentity);
$requestBody->setParameters($parameters);

$result = $graphServiceClient->solutions()->sharePoint()->migrations()->crossOrganizationMigrationTasks()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.share_point_migration_task import SharePointMigrationTask
from msgraph_beta.generated.models.share_point_user_migration_task_parameters import SharePointUserMigrationTaskParameters
from msgraph_beta.generated.models.user_identity import UserIdentity
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SharePointMigrationTask(
	parameters = SharePointUserMigrationTaskParameters(
		odata_type = "#microsoft.graph.sharePointUserMigrationTaskParameters",
		target_organization_host = "https://fabrico-my.sharepoint.com",
		source_user_identity = UserIdentity(
			id = "da157a29-f793-4dd6-9c73-41d2c73c2546",
		),
		target_user_identity = UserIdentity(
			id = "cb53ea98-6151-44cc-9c21-098a3c3e3988",
		),
	),
)

result = await graph_client.solutions.share_point.migrations.cross_organization_migration_tasks.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "3ed6d46d-13a3-4995-b6ea-a74a20b1fac0",
  "status": "notStarted",
  "parameters": {
    "@odata.type": "#microsoft.graph.sharePointUserMigrationTaskParameters",
    "targetOrganizationHost": "https://fabrico-my.sharepoint.com",
    "sourceUserIdentity": {
      "id": "da157a29-f793-4dd6-9c73-41d2c73c2546"
    },
    "targetUserIdentity": {
      "id": "cb53ea98-6151-44cc-9c21-098a3c3e3988"
    }
  }
}
```

### Example 3: Create a user migration task by using the user object ID and the target data location code

The following example shows how to create a user migration task by **userObjectId** and with specific **targetDataLocationCode**.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [Python](#tabpanel_3_python)

```http
POST https://graph.microsoft.com/beta/solutions/sharePoint/migrations/crossOrganizationMigrationTasks
Content-Type: application/json

{
  "parameters": {
    "@odata.type": "#microsoft.graph.sharePointUserMigrationTaskParameters",
    "targetOrganizationId": "78d010af-72cb-412f-8779-18ce9b5f553b",
    "targetDataLocationCode": null,
    "sourceUserIdentity": {
      "id": "da157a29-f793-4dd6-9c73-41d2c73c2546"
    },
    "targetUserIdentity": {
      "id": "cb53ea98-6151-44cc-9c21-098a3c3e3988"
    }
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new SharePointMigrationTask
{
	Parameters = new SharePointUserMigrationTaskParameters
	{
		OdataType = "#microsoft.graph.sharePointUserMigrationTaskParameters",
		TargetOrganizationId = Guid.Parse("78d010af-72cb-412f-8779-18ce9b5f553b"),
		TargetDataLocationCode = null,
		SourceUserIdentity = new UserIdentity
		{
			Id = "da157a29-f793-4dd6-9c73-41d2c73c2546",
		},
		TargetUserIdentity = new UserIdentity
		{
			Id = "cb53ea98-6151-44cc-9c21-098a3c3e3988",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.SharePoint.Migrations.CrossOrganizationMigrationTasks.PostAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewSharePointMigrationTask()
parameters := graphmodels.NewSharePointUserMigrationTaskParameters()
targetOrganizationId := uuid.MustParse("78d010af-72cb-412f-8779-18ce9b5f553b")
parameters.SetTargetOrganizationId(&targetOrganizationId) 
targetDataLocationCode := null
parameters.SetTargetDataLocationCode(&targetDataLocationCode) 
sourceUserIdentity := graphmodels.NewUserIdentity()
id := "da157a29-f793-4dd6-9c73-41d2c73c2546"
sourceUserIdentity.SetId(&id) 
parameters.SetSourceUserIdentity(sourceUserIdentity)
targetUserIdentity := graphmodels.NewUserIdentity()
id := "cb53ea98-6151-44cc-9c21-098a3c3e3988"
targetUserIdentity.SetId(&id) 
parameters.SetTargetUserIdentity(targetUserIdentity)
requestBody.SetParameters(parameters)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
crossOrganizationMigrationTasks, err := graphClient.Solutions().SharePoint().Migrations().CrossOrganizationMigrationTasks().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

SharePointMigrationTask sharePointMigrationTask = new SharePointMigrationTask();
SharePointUserMigrationTaskParameters parameters = new SharePointUserMigrationTaskParameters();
parameters.setOdataType("#microsoft.graph.sharePointUserMigrationTaskParameters");
parameters.setTargetOrganizationId(UUID.fromString("78d010af-72cb-412f-8779-18ce9b5f553b"));
parameters.setTargetDataLocationCode(null);
UserIdentity sourceUserIdentity = new UserIdentity();
sourceUserIdentity.setId("da157a29-f793-4dd6-9c73-41d2c73c2546");
parameters.setSourceUserIdentity(sourceUserIdentity);
UserIdentity targetUserIdentity = new UserIdentity();
targetUserIdentity.setId("cb53ea98-6151-44cc-9c21-098a3c3e3988");
parameters.setTargetUserIdentity(targetUserIdentity);
sharePointMigrationTask.setParameters(parameters);
SharePointMigrationTask result = graphClient.solutions().sharePoint().migrations().crossOrganizationMigrationTasks().post(sharePointMigrationTask);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const sharePointMigrationTask = {
  parameters: {
    '@odata.type': '#microsoft.graph.sharePointUserMigrationTaskParameters',
    targetOrganizationId: '78d010af-72cb-412f-8779-18ce9b5f553b',
    targetDataLocationCode: null,
    sourceUserIdentity: {
      id: 'da157a29-f793-4dd6-9c73-41d2c73c2546'
    },
    targetUserIdentity: {
      id: 'cb53ea98-6151-44cc-9c21-098a3c3e3988'
    }
  }
};

await client.api('/solutions/sharePoint/migrations/crossOrganizationMigrationTasks')
	.version('beta')
	.post(sharePointMigrationTask);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\SharePointMigrationTask;
use Microsoft\Graph\Beta\Generated\Models\SharePointUserMigrationTaskParameters;
use Microsoft\Graph\Beta\Generated\Models\UserIdentity;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SharePointMigrationTask();
$parameters = new SharePointUserMigrationTaskParameters();
$parameters->setOdataType('#microsoft.graph.sharePointUserMigrationTaskParameters');
$parameters->setTargetOrganizationId('78d010af-72cb-412f-8779-18ce9b5f553b');
$parameters->setTargetDataLocationCode(null);
$parametersSourceUserIdentity = new UserIdentity();
$parametersSourceUserIdentity->setId('da157a29-f793-4dd6-9c73-41d2c73c2546');
$parameters->setSourceUserIdentity($parametersSourceUserIdentity);
$parametersTargetUserIdentity = new UserIdentity();
$parametersTargetUserIdentity->setId('cb53ea98-6151-44cc-9c21-098a3c3e3988');
$parameters->setTargetUserIdentity($parametersTargetUserIdentity);
$requestBody->setParameters($parameters);

$result = $graphServiceClient->solutions()->sharePoint()->migrations()->crossOrganizationMigrationTasks()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.share_point_migration_task import SharePointMigrationTask
from msgraph_beta.generated.models.share_point_user_migration_task_parameters import SharePointUserMigrationTaskParameters
from msgraph_beta.generated.models.user_identity import UserIdentity
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SharePointMigrationTask(
	parameters = SharePointUserMigrationTaskParameters(
		odata_type = "#microsoft.graph.sharePointUserMigrationTaskParameters",
		target_organization_id = UUID("78d010af-72cb-412f-8779-18ce9b5f553b"),
		target_data_location_code = None,
		source_user_identity = UserIdentity(
			id = "da157a29-f793-4dd6-9c73-41d2c73c2546",
		),
		target_user_identity = UserIdentity(
			id = "cb53ea98-6151-44cc-9c21-098a3c3e3988",
		),
	),
)

result = await graph_client.solutions.share_point.migrations.cross_organization_migration_tasks.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "3ed6d46d-13a3-4995-b6ea-a74a20b1fac0",
  "status": "notStarted",
  "parameters": {
    "@odata.type": "#microsoft.graph.sharePointUserMigrationTaskParameters",
    "targetOrganizationId": "78d010af-72cb-412f-8779-18ce9b5f553b",
    "targetDataLocationCode": "FRA",
    "sourceUserIdentity": {
      "id": "da157a29-f793-4dd6-9c73-41d2c73c2546",
      "userPrincipalName": "source-user@contoso.onmicrosoft.com"
    },
    "targetUserIdentity": {
      "id": "cb53ea98-6151-44cc-9c21-098a3c3e3988",
      "userPrincipalName": "target-user@fabrico.onmicrosoft.com"
    }
  }
}
```

### Example 4: Create a site migration task

The following example shows how to create a regular site migration task.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [Python](#tabpanel_4_python)

```http
POST https://graph.microsoft.com/beta/solutions/sharePoint/migrations/crossOrganizationMigrationTasks
Content-Type: application/json

{
  "parameters": {
    "@odata.type": "#microsoft.graph.sharePointSiteMigrationTaskParameters",
    "targetOrganizationHost": "https://fabrico-my.sharepoint.com",
    "sourceSiteUrl": "https://contoso.sharepoint.com/sites/IT",
    "targetSiteUrl": "https://fabrico.sharepoint.com/sites/IT"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new SharePointMigrationTask
{
	Parameters = new SharePointSiteMigrationTaskParameters
	{
		OdataType = "#microsoft.graph.sharePointSiteMigrationTaskParameters",
		TargetOrganizationHost = "https://fabrico-my.sharepoint.com",
		SourceSiteUrl = "https://contoso.sharepoint.com/sites/IT",
		TargetSiteUrl = "https://fabrico.sharepoint.com/sites/IT",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.SharePoint.Migrations.CrossOrganizationMigrationTasks.PostAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewSharePointMigrationTask()
parameters := graphmodels.NewSharePointSiteMigrationTaskParameters()
targetOrganizationHost := "https://fabrico-my.sharepoint.com"
parameters.SetTargetOrganizationHost(&targetOrganizationHost) 
sourceSiteUrl := "https://contoso.sharepoint.com/sites/IT"
parameters.SetSourceSiteUrl(&sourceSiteUrl) 
targetSiteUrl := "https://fabrico.sharepoint.com/sites/IT"
parameters.SetTargetSiteUrl(&targetSiteUrl) 
requestBody.SetParameters(parameters)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
crossOrganizationMigrationTasks, err := graphClient.Solutions().SharePoint().Migrations().CrossOrganizationMigrationTasks().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

SharePointMigrationTask sharePointMigrationTask = new SharePointMigrationTask();
SharePointSiteMigrationTaskParameters parameters = new SharePointSiteMigrationTaskParameters();
parameters.setOdataType("#microsoft.graph.sharePointSiteMigrationTaskParameters");
parameters.setTargetOrganizationHost("https://fabrico-my.sharepoint.com");
parameters.setSourceSiteUrl("https://contoso.sharepoint.com/sites/IT");
parameters.setTargetSiteUrl("https://fabrico.sharepoint.com/sites/IT");
sharePointMigrationTask.setParameters(parameters);
SharePointMigrationTask result = graphClient.solutions().sharePoint().migrations().crossOrganizationMigrationTasks().post(sharePointMigrationTask);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const sharePointMigrationTask = {
  parameters: {
    '@odata.type': '#microsoft.graph.sharePointSiteMigrationTaskParameters',
    targetOrganizationHost: 'https://fabrico-my.sharepoint.com',
    sourceSiteUrl: 'https://contoso.sharepoint.com/sites/IT',
    targetSiteUrl: 'https://fabrico.sharepoint.com/sites/IT'
  }
};

await client.api('/solutions/sharePoint/migrations/crossOrganizationMigrationTasks')
	.version('beta')
	.post(sharePointMigrationTask);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\SharePointMigrationTask;
use Microsoft\Graph\Beta\Generated\Models\SharePointSiteMigrationTaskParameters;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SharePointMigrationTask();
$parameters = new SharePointSiteMigrationTaskParameters();
$parameters->setOdataType('#microsoft.graph.sharePointSiteMigrationTaskParameters');
$parameters->setTargetOrganizationHost('https://fabrico-my.sharepoint.com');
$parameters->setSourceSiteUrl('https://contoso.sharepoint.com/sites/IT');
$parameters->setTargetSiteUrl('https://fabrico.sharepoint.com/sites/IT');
$requestBody->setParameters($parameters);

$result = $graphServiceClient->solutions()->sharePoint()->migrations()->crossOrganizationMigrationTasks()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.share_point_migration_task import SharePointMigrationTask
from msgraph_beta.generated.models.share_point_site_migration_task_parameters import SharePointSiteMigrationTaskParameters
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SharePointMigrationTask(
	parameters = SharePointSiteMigrationTaskParameters(
		odata_type = "#microsoft.graph.sharePointSiteMigrationTaskParameters",
		target_organization_host = "https://fabrico-my.sharepoint.com",
		source_site_url = "https://contoso.sharepoint.com/sites/IT",
		target_site_url = "https://fabrico.sharepoint.com/sites/IT",
	),
)

result = await graph_client.solutions.share_point.migrations.cross_organization_migration_tasks.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "3ed6d46d-13a3-4995-b6ea-a74a20b1fac0",
  "status": "notStarted",
  "parameters": {
    "@odata.type": "#microsoft.graph.sharePointSiteMigrationTaskParameters",
    "targetOrganizationHost": "https://fabrico-my.sharepoint.com",
    "sourceSiteUrl": "https://contoso.sharepoint.com/sites/IT",
    "targetSiteUrl": "https://fabrico.sharepoint.com/sites/IT"
  }
}
```

### Example 5: Create a group migration task

The following example shows how to create a group-connected site migration task by **mailNickname**.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_5_http)
- [C#](#tabpanel_5_csharp)
- [Go](#tabpanel_5_go)
- [Java](#tabpanel_5_java)
- [JavaScript](#tabpanel_5_javascript)
- [PHP](#tabpanel_5_php)
- [Python](#tabpanel_5_python)

```http
POST https://graph.microsoft.com/beta/solutions/sharePoint/migrations/crossOrganizationMigrationTasks
Content-Type: application/json

{
  "parameters": {
    "@odata.type": "#microsoft.graph.sharePointGroupMigrationTaskParameters",
    "targetOrganizationHost": "https://fabrico-my.sharepoint.com",
    "sourceGroupIdentity": {
      "mailNickname": "source-group"
    },
    "targetGroupIdentity": {
      "mailNickname": "target-group"
    }
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new SharePointMigrationTask
{
	Parameters = new SharePointGroupMigrationTaskParameters
	{
		OdataType = "#microsoft.graph.sharePointGroupMigrationTaskParameters",
		TargetOrganizationHost = "https://fabrico-my.sharepoint.com",
		SourceGroupIdentity = new GroupIdentity
		{
			MailNickname = "source-group",
		},
		TargetGroupIdentity = new GroupIdentity
		{
			MailNickname = "target-group",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.SharePoint.Migrations.CrossOrganizationMigrationTasks.PostAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewSharePointMigrationTask()
parameters := graphmodels.NewSharePointGroupMigrationTaskParameters()
targetOrganizationHost := "https://fabrico-my.sharepoint.com"
parameters.SetTargetOrganizationHost(&targetOrganizationHost) 
sourceGroupIdentity := graphmodels.NewGroupIdentity()
mailNickname := "source-group"
sourceGroupIdentity.SetMailNickname(&mailNickname) 
parameters.SetSourceGroupIdentity(sourceGroupIdentity)
targetGroupIdentity := graphmodels.NewGroupIdentity()
mailNickname := "target-group"
targetGroupIdentity.SetMailNickname(&mailNickname) 
parameters.SetTargetGroupIdentity(targetGroupIdentity)
requestBody.SetParameters(parameters)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
crossOrganizationMigrationTasks, err := graphClient.Solutions().SharePoint().Migrations().CrossOrganizationMigrationTasks().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

SharePointMigrationTask sharePointMigrationTask = new SharePointMigrationTask();
SharePointGroupMigrationTaskParameters parameters = new SharePointGroupMigrationTaskParameters();
parameters.setOdataType("#microsoft.graph.sharePointGroupMigrationTaskParameters");
parameters.setTargetOrganizationHost("https://fabrico-my.sharepoint.com");
GroupIdentity sourceGroupIdentity = new GroupIdentity();
sourceGroupIdentity.setMailNickname("source-group");
parameters.setSourceGroupIdentity(sourceGroupIdentity);
GroupIdentity targetGroupIdentity = new GroupIdentity();
targetGroupIdentity.setMailNickname("target-group");
parameters.setTargetGroupIdentity(targetGroupIdentity);
sharePointMigrationTask.setParameters(parameters);
SharePointMigrationTask result = graphClient.solutions().sharePoint().migrations().crossOrganizationMigrationTasks().post(sharePointMigrationTask);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const sharePointMigrationTask = {
  parameters: {
    '@odata.type': '#microsoft.graph.sharePointGroupMigrationTaskParameters',
    targetOrganizationHost: 'https://fabrico-my.sharepoint.com',
    sourceGroupIdentity: {
      mailNickname: 'source-group'
    },
    targetGroupIdentity: {
      mailNickname: 'target-group'
    }
  }
};

await client.api('/solutions/sharePoint/migrations/crossOrganizationMigrationTasks')
	.version('beta')
	.post(sharePointMigrationTask);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\SharePointMigrationTask;
use Microsoft\Graph\Beta\Generated\Models\SharePointGroupMigrationTaskParameters;
use Microsoft\Graph\Beta\Generated\Models\GroupIdentity;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SharePointMigrationTask();
$parameters = new SharePointGroupMigrationTaskParameters();
$parameters->setOdataType('#microsoft.graph.sharePointGroupMigrationTaskParameters');
$parameters->setTargetOrganizationHost('https://fabrico-my.sharepoint.com');
$parametersSourceGroupIdentity = new GroupIdentity();
$parametersSourceGroupIdentity->setMailNickname('source-group');
$parameters->setSourceGroupIdentity($parametersSourceGroupIdentity);
$parametersTargetGroupIdentity = new GroupIdentity();
$parametersTargetGroupIdentity->setMailNickname('target-group');
$parameters->setTargetGroupIdentity($parametersTargetGroupIdentity);
$requestBody->setParameters($parameters);

$result = $graphServiceClient->solutions()->sharePoint()->migrations()->crossOrganizationMigrationTasks()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.share_point_migration_task import SharePointMigrationTask
from msgraph_beta.generated.models.share_point_group_migration_task_parameters import SharePointGroupMigrationTaskParameters
from msgraph_beta.generated.models.group_identity import GroupIdentity
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SharePointMigrationTask(
	parameters = SharePointGroupMigrationTaskParameters(
		odata_type = "#microsoft.graph.sharePointGroupMigrationTaskParameters",
		target_organization_host = "https://fabrico-my.sharepoint.com",
		source_group_identity = GroupIdentity(
			mail_nickname = "source-group",
		),
		target_group_identity = GroupIdentity(
			mail_nickname = "target-group",
		),
	),
)

result = await graph_client.solutions.share_point.migrations.cross_organization_migration_tasks.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "3ed6d46d-13a3-4995-b6ea-a74a20b1fac0",
  "status": "notStarted",
  "parameters": {
    "@odata.type": "#microsoft.graph.sharePointGroupMigrationTaskParameters",
    "targetOrganizationHost": "https://fabrico-my.sharepoint.com",
    "sourceGroupIdentity": {
      "mailNickname": "source-group"
    },
    "targetGroupIdentity": {
      "mailNickname": "target-group"
    }
  }
}
```

### Example 6: Create a user migration task with a preferred start date and time

The following example shows how to create a user migration task with the **preferredStartDateTime** parameter.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_6_http)
- [C#](#tabpanel_6_csharp)
- [Go](#tabpanel_6_go)
- [Java](#tabpanel_6_java)
- [JavaScript](#tabpanel_6_javascript)
- [PHP](#tabpanel_6_php)
- [Python](#tabpanel_6_python)

```http
POST https://graph.microsoft.com/beta/solutions/sharePoint/migrations/crossOrganizationMigrationTasks
Content-Type: application/json

{
  "parameters": {
    "@odata.type": "#microsoft.graph.sharePointUserMigrationTaskParameters",
    "targetOrganizationHost": "https://fabrico-my.sharepoint.com",
    "sourceUserIdentity": {
      "userPrincipalName": "source-user@contoso.onmicrosoft.com"
    },
    "targetUserIdentity": {
      "userPrincipalName": "target-user@fabrico.onmicrosoft.com"
    },
    "preferredStartDateTime": "2024-08-31T16:00:00Z"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new SharePointMigrationTask
{
	Parameters = new SharePointUserMigrationTaskParameters
	{
		OdataType = "#microsoft.graph.sharePointUserMigrationTaskParameters",
		TargetOrganizationHost = "https://fabrico-my.sharepoint.com",
		SourceUserIdentity = new UserIdentity
		{
			UserPrincipalName = "source-user@contoso.onmicrosoft.com",
		},
		TargetUserIdentity = new UserIdentity
		{
			UserPrincipalName = "target-user@fabrico.onmicrosoft.com",
		},
		PreferredStartDateTime = DateTimeOffset.Parse("2024-08-31T16:00:00Z"),
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.SharePoint.Migrations.CrossOrganizationMigrationTasks.PostAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewSharePointMigrationTask()
parameters := graphmodels.NewSharePointUserMigrationTaskParameters()
targetOrganizationHost := "https://fabrico-my.sharepoint.com"
parameters.SetTargetOrganizationHost(&targetOrganizationHost) 
sourceUserIdentity := graphmodels.NewUserIdentity()
userPrincipalName := "source-user@contoso.onmicrosoft.com"
sourceUserIdentity.SetUserPrincipalName(&userPrincipalName) 
parameters.SetSourceUserIdentity(sourceUserIdentity)
targetUserIdentity := graphmodels.NewUserIdentity()
userPrincipalName := "target-user@fabrico.onmicrosoft.com"
targetUserIdentity.SetUserPrincipalName(&userPrincipalName) 
parameters.SetTargetUserIdentity(targetUserIdentity)
preferredStartDateTime , err := time.Parse(time.RFC3339, "2024-08-31T16:00:00Z")
parameters.SetPreferredStartDateTime(&preferredStartDateTime) 
requestBody.SetParameters(parameters)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
crossOrganizationMigrationTasks, err := graphClient.Solutions().SharePoint().Migrations().CrossOrganizationMigrationTasks().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

SharePointMigrationTask sharePointMigrationTask = new SharePointMigrationTask();
SharePointUserMigrationTaskParameters parameters = new SharePointUserMigrationTaskParameters();
parameters.setOdataType("#microsoft.graph.sharePointUserMigrationTaskParameters");
parameters.setTargetOrganizationHost("https://fabrico-my.sharepoint.com");
UserIdentity sourceUserIdentity = new UserIdentity();
sourceUserIdentity.setUserPrincipalName("source-user@contoso.onmicrosoft.com");
parameters.setSourceUserIdentity(sourceUserIdentity);
UserIdentity targetUserIdentity = new UserIdentity();
targetUserIdentity.setUserPrincipalName("target-user@fabrico.onmicrosoft.com");
parameters.setTargetUserIdentity(targetUserIdentity);
OffsetDateTime preferredStartDateTime = OffsetDateTime.parse("2024-08-31T16:00:00Z");
parameters.setPreferredStartDateTime(preferredStartDateTime);
sharePointMigrationTask.setParameters(parameters);
SharePointMigrationTask result = graphClient.solutions().sharePoint().migrations().crossOrganizationMigrationTasks().post(sharePointMigrationTask);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const sharePointMigrationTask = {
  parameters: {
    '@odata.type': '#microsoft.graph.sharePointUserMigrationTaskParameters',
    targetOrganizationHost: 'https://fabrico-my.sharepoint.com',
    sourceUserIdentity: {
      userPrincipalName: 'source-user@contoso.onmicrosoft.com'
    },
    targetUserIdentity: {
      userPrincipalName: 'target-user@fabrico.onmicrosoft.com'
    },
    preferredStartDateTime: '2024-08-31T16:00:00Z'
  }
};

await client.api('/solutions/sharePoint/migrations/crossOrganizationMigrationTasks')
	.version('beta')
	.post(sharePointMigrationTask);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\SharePointMigrationTask;
use Microsoft\Graph\Beta\Generated\Models\SharePointUserMigrationTaskParameters;
use Microsoft\Graph\Beta\Generated\Models\UserIdentity;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SharePointMigrationTask();
$parameters = new SharePointUserMigrationTaskParameters();
$parameters->setOdataType('#microsoft.graph.sharePointUserMigrationTaskParameters');
$parameters->setTargetOrganizationHost('https://fabrico-my.sharepoint.com');
$parametersSourceUserIdentity = new UserIdentity();
$parametersSourceUserIdentity->setUserPrincipalName('source-user@contoso.onmicrosoft.com');
$parameters->setSourceUserIdentity($parametersSourceUserIdentity);
$parametersTargetUserIdentity = new UserIdentity();
$parametersTargetUserIdentity->setUserPrincipalName('target-user@fabrico.onmicrosoft.com');
$parameters->setTargetUserIdentity($parametersTargetUserIdentity);
$parameters->setPreferredStartDateTime(new \DateTime('2024-08-31T16:00:00Z'));
$requestBody->setParameters($parameters);

$result = $graphServiceClient->solutions()->sharePoint()->migrations()->crossOrganizationMigrationTasks()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.share_point_migration_task import SharePointMigrationTask
from msgraph_beta.generated.models.share_point_user_migration_task_parameters import SharePointUserMigrationTaskParameters
from msgraph_beta.generated.models.user_identity import UserIdentity
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SharePointMigrationTask(
	parameters = SharePointUserMigrationTaskParameters(
		odata_type = "#microsoft.graph.sharePointUserMigrationTaskParameters",
		target_organization_host = "https://fabrico-my.sharepoint.com",
		source_user_identity = UserIdentity(
			user_principal_name = "source-user@contoso.onmicrosoft.com",
		),
		target_user_identity = UserIdentity(
			user_principal_name = "target-user@fabrico.onmicrosoft.com",
		),
		preferred_start_date_time = "2024-08-31T16:00:00Z",
	),
)

result = await graph_client.solutions.share_point.migrations.cross_organization_migration_tasks.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "3ed6d46d-13a3-4995-b6ea-a74a20b1fac0",
  "status": "notStarted",
  "parameters": {
    "@odata.type": "#microsoft.graph.sharePointUserMigrationTaskParameters",
    "targetOrganizationHost": "https://fabrico-my.sharepoint.com",
    "sourceUserIdentity": {
      "userPrincipalName": "source-user@contoso.onmicrosoft.com"
    },
    "targetUserIdentity": {
      "userPrincipalName": "target-user@fabrico.onmicrosoft.com"
    },
    "preferredStartDateTime": "2024-08-31T16:00:00Z"
  }
}
```

### Example 7: Create user migration task with validateOnly

The following example shows how to create a user migration task with `"validateOnly": true` parameter.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_7_http)
- [C#](#tabpanel_7_csharp)
- [Go](#tabpanel_7_go)
- [Java](#tabpanel_7_java)
- [JavaScript](#tabpanel_7_javascript)
- [PHP](#tabpanel_7_php)
- [Python](#tabpanel_7_python)

```http
POST https://graph.microsoft.com/beta/solutions/sharePoint/migrations/crossOrganizationMigrationTasks
Content-Type: application/json

{
  "parameters": {
    "@odata.type": "#microsoft.graph.sharePointUserMigrationTaskParameters",
    "targetOrganizationHost": "https://fabrico-my.sharepoint.com",
    "validateOnly": true,
    "sourceUserIdentity": {
      "userPrincipalName": "source-user@contoso.onmicrosoft.com"
    },
    "targetUserIdentity": {
      "userPrincipalName": "target-user@fabrico.onmicrosoft.com"
    }
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new SharePointMigrationTask
{
	Parameters = new SharePointUserMigrationTaskParameters
	{
		OdataType = "#microsoft.graph.sharePointUserMigrationTaskParameters",
		TargetOrganizationHost = "https://fabrico-my.sharepoint.com",
		ValidateOnly = true,
		SourceUserIdentity = new UserIdentity
		{
			UserPrincipalName = "source-user@contoso.onmicrosoft.com",
		},
		TargetUserIdentity = new UserIdentity
		{
			UserPrincipalName = "target-user@fabrico.onmicrosoft.com",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.SharePoint.Migrations.CrossOrganizationMigrationTasks.PostAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewSharePointMigrationTask()
parameters := graphmodels.NewSharePointUserMigrationTaskParameters()
targetOrganizationHost := "https://fabrico-my.sharepoint.com"
parameters.SetTargetOrganizationHost(&targetOrganizationHost) 
validateOnly := true
parameters.SetValidateOnly(&validateOnly) 
sourceUserIdentity := graphmodels.NewUserIdentity()
userPrincipalName := "source-user@contoso.onmicrosoft.com"
sourceUserIdentity.SetUserPrincipalName(&userPrincipalName) 
parameters.SetSourceUserIdentity(sourceUserIdentity)
targetUserIdentity := graphmodels.NewUserIdentity()
userPrincipalName := "target-user@fabrico.onmicrosoft.com"
targetUserIdentity.SetUserPrincipalName(&userPrincipalName) 
parameters.SetTargetUserIdentity(targetUserIdentity)
requestBody.SetParameters(parameters)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
crossOrganizationMigrationTasks, err := graphClient.Solutions().SharePoint().Migrations().CrossOrganizationMigrationTasks().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

SharePointMigrationTask sharePointMigrationTask = new SharePointMigrationTask();
SharePointUserMigrationTaskParameters parameters = new SharePointUserMigrationTaskParameters();
parameters.setOdataType("#microsoft.graph.sharePointUserMigrationTaskParameters");
parameters.setTargetOrganizationHost("https://fabrico-my.sharepoint.com");
parameters.setValidateOnly(true);
UserIdentity sourceUserIdentity = new UserIdentity();
sourceUserIdentity.setUserPrincipalName("source-user@contoso.onmicrosoft.com");
parameters.setSourceUserIdentity(sourceUserIdentity);
UserIdentity targetUserIdentity = new UserIdentity();
targetUserIdentity.setUserPrincipalName("target-user@fabrico.onmicrosoft.com");
parameters.setTargetUserIdentity(targetUserIdentity);
sharePointMigrationTask.setParameters(parameters);
SharePointMigrationTask result = graphClient.solutions().sharePoint().migrations().crossOrganizationMigrationTasks().post(sharePointMigrationTask);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const sharePointMigrationTask = {
  parameters: {
    '@odata.type': '#microsoft.graph.sharePointUserMigrationTaskParameters',
    targetOrganizationHost: 'https://fabrico-my.sharepoint.com',
    validateOnly: true,
    sourceUserIdentity: {
      userPrincipalName: 'source-user@contoso.onmicrosoft.com'
    },
    targetUserIdentity: {
      userPrincipalName: 'target-user@fabrico.onmicrosoft.com'
    }
  }
};

await client.api('/solutions/sharePoint/migrations/crossOrganizationMigrationTasks')
	.version('beta')
	.post(sharePointMigrationTask);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\SharePointMigrationTask;
use Microsoft\Graph\Beta\Generated\Models\SharePointUserMigrationTaskParameters;
use Microsoft\Graph\Beta\Generated\Models\UserIdentity;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SharePointMigrationTask();
$parameters = new SharePointUserMigrationTaskParameters();
$parameters->setOdataType('#microsoft.graph.sharePointUserMigrationTaskParameters');
$parameters->setTargetOrganizationHost('https://fabrico-my.sharepoint.com');
$parameters->setValidateOnly(true);
$parametersSourceUserIdentity = new UserIdentity();
$parametersSourceUserIdentity->setUserPrincipalName('source-user@contoso.onmicrosoft.com');
$parameters->setSourceUserIdentity($parametersSourceUserIdentity);
$parametersTargetUserIdentity = new UserIdentity();
$parametersTargetUserIdentity->setUserPrincipalName('target-user@fabrico.onmicrosoft.com');
$parameters->setTargetUserIdentity($parametersTargetUserIdentity);
$requestBody->setParameters($parameters);

$result = $graphServiceClient->solutions()->sharePoint()->migrations()->crossOrganizationMigrationTasks()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.share_point_migration_task import SharePointMigrationTask
from msgraph_beta.generated.models.share_point_user_migration_task_parameters import SharePointUserMigrationTaskParameters
from msgraph_beta.generated.models.user_identity import UserIdentity
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SharePointMigrationTask(
	parameters = SharePointUserMigrationTaskParameters(
		odata_type = "#microsoft.graph.sharePointUserMigrationTaskParameters",
		target_organization_host = "https://fabrico-my.sharepoint.com",
		validate_only = True,
		source_user_identity = UserIdentity(
			user_principal_name = "source-user@contoso.onmicrosoft.com",
		),
		target_user_identity = UserIdentity(
			user_principal_name = "target-user@fabrico.onmicrosoft.com",
		),
	),
)

result = await graph_client.solutions.share_point.migrations.cross_organization_migration_tasks.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "status": "completed",
  "parameters": {
    "@odata.type": "#microsoft.graph.sharePointUserMigrationTaskParameters",
    "targetOrganizationHost": "https://fabrico-my.sharepoint.com",
    "validateOnly": true,
    "sourceUserIdentity": {
      "userPrincipalName": "source-user@contoso.onmicrosoft.com"
    },
    "targetUserIdentity": {
      "userPrincipalName": "target-user@fabrico.onmicrosoft.com"
    }
  }
}
```
