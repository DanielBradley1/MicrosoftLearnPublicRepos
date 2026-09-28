<!-- Source: https://learn.microsoft.com/en-us/graph/api/synchronization-synchronizationjob-provisionondemand?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# synchronizationJob: provisionOnDemand

Namespace: microsoft.graph

Select a user and provision the account on-demand for a [synchronizationJob](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationjob?view=graph-rest-1.0). The rate limit for this API is 5 requests per 10 seconds.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Synchronization.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Application.ReadWrite.OwnedBy | Synchronization.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be an owner or member of the group or be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Application Administrator
- Cloud Application Administrator
- Hybrid Identity Administrator - to configure Microsoft Entra Cloud Sync

## HTTP request

```http
POST /servicePrincipals/{servicePrincipalsId}/synchronization/jobs/{synchronizationJobId}/provisionOnDemand
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply JSON representation of the parameters.

The following table shows the parameters that can be used with this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| parameters | [synchronizationJobApplicationParameters](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationjobapplicationparameters?view=graph-rest-1.0) collection | Represents the objects that will be provisioned and the synchronization rules executed. The resource is primarily used for on-demand provisioning. |

## Response

If successful, this method returns a `200 OK` response code and a stringKeyStringValuePair.

## Examples

### Example 1: Provision users from Microsoft Entra ID to third-party applications

#### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/servicePrincipals/c8c95753-f628-48e1-9fab-76c2d4cf624c/synchronization/jobs/3f7565a3-fde6-4e4d-bda8-1bb70aba3612/provisionOnDemand
Content-Type: application/json

{
  "parameters": [
    {
      "subjects": [
        {
          "objectId": "9bb0f679-a883-4a6f-8260-35b491b8b8c8",
          "objectTypeName": "User"
        }
      ],
      "ruleId": "ea807875-5618-4f0a-9125-0b46a05298ca"
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.ServicePrincipals.Item.Synchronization.Jobs.Item.ProvisionOnDemand;
using Microsoft.Graph.Models;

var requestBody = new ProvisionOnDemandPostRequestBody
{
	Parameters = new List<SynchronizationJobApplicationParameters>
	{
		new SynchronizationJobApplicationParameters
		{
			Subjects = new List<SynchronizationJobSubject>
			{
				new SynchronizationJobSubject
				{
					ObjectId = "9bb0f679-a883-4a6f-8260-35b491b8b8c8",
					ObjectTypeName = "User",
				},
			},
			RuleId = "ea807875-5618-4f0a-9125-0b46a05298ca",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.ServicePrincipals["{servicePrincipal-id}"].Synchronization.Jobs["{synchronizationJob-id}"].ProvisionOnDemand.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphserviceprincipals "github.com/microsoftgraph/msgraph-sdk-go/serviceprincipals"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphserviceprincipals.NewProvisionOnDemandPostRequestBody()


synchronizationJobApplicationParameters := graphmodels.NewSynchronizationJobApplicationParameters()


synchronizationJobSubject := graphmodels.NewSynchronizationJobSubject()
objectId := "9bb0f679-a883-4a6f-8260-35b491b8b8c8"
synchronizationJobSubject.SetObjectId(&objectId) 
objectTypeName := "User"
synchronizationJobSubject.SetObjectTypeName(&objectTypeName) 

subjects := []graphmodels.SynchronizationJobSubjectable {
	synchronizationJobSubject,
}
synchronizationJobApplicationParameters.SetSubjects(subjects)
ruleId := "ea807875-5618-4f0a-9125-0b46a05298ca"
synchronizationJobApplicationParameters.SetRuleId(&ruleId) 

parameters := []graphmodels.SynchronizationJobApplicationParametersable {
	synchronizationJobApplicationParameters,
}
requestBody.SetParameters(parameters)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
provisionOnDemand, err := graphClient.ServicePrincipals().ByServicePrincipalId("servicePrincipal-id").Synchronization().Jobs().BySynchronizationJobId("synchronizationJob-id").ProvisionOnDemand().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.serviceprincipals.item.synchronization.jobs.item.provisionondemand.ProvisionOnDemandPostRequestBody provisionOnDemandPostRequestBody = new com.microsoft.graph.serviceprincipals.item.synchronization.jobs.item.provisionondemand.ProvisionOnDemandPostRequestBody();
LinkedList<SynchronizationJobApplicationParameters> parameters = new LinkedList<SynchronizationJobApplicationParameters>();
SynchronizationJobApplicationParameters synchronizationJobApplicationParameters = new SynchronizationJobApplicationParameters();
LinkedList<SynchronizationJobSubject> subjects = new LinkedList<SynchronizationJobSubject>();
SynchronizationJobSubject synchronizationJobSubject = new SynchronizationJobSubject();
synchronizationJobSubject.setObjectId("9bb0f679-a883-4a6f-8260-35b491b8b8c8");
synchronizationJobSubject.setObjectTypeName("User");
subjects.add(synchronizationJobSubject);
synchronizationJobApplicationParameters.setSubjects(subjects);
synchronizationJobApplicationParameters.setRuleId("ea807875-5618-4f0a-9125-0b46a05298ca");
parameters.add(synchronizationJobApplicationParameters);
provisionOnDemandPostRequestBody.setParameters(parameters);
StringKeyStringValuePair result = graphClient.servicePrincipals().byServicePrincipalId("{servicePrincipal-id}").synchronization().jobs().bySynchronizationJobId("{synchronizationJob-id}").provisionOnDemand().post(provisionOnDemandPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const stringKeyStringValuePair = {
  parameters: [
    {
      subjects: [
        {
          objectId: '9bb0f679-a883-4a6f-8260-35b491b8b8c8',
          objectTypeName: 'User'
        }
      ],
      ruleId: 'ea807875-5618-4f0a-9125-0b46a05298ca'
    }
  ]
};

await client.api('/servicePrincipals/c8c95753-f628-48e1-9fab-76c2d4cf624c/synchronization/jobs/3f7565a3-fde6-4e4d-bda8-1bb70aba3612/provisionOnDemand')
	.post(stringKeyStringValuePair);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\ServicePrincipals\Item\Synchronization\Jobs\Item\ProvisionOnDemand\ProvisionOnDemandPostRequestBody;
use Microsoft\Graph\Generated\Models\SynchronizationJobApplicationParameters;
use Microsoft\Graph\Generated\Models\SynchronizationJobSubject;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ProvisionOnDemandPostRequestBody();
$parametersSynchronizationJobApplicationParameters1 = new SynchronizationJobApplicationParameters();
$subjectsSynchronizationJobSubject1 = new SynchronizationJobSubject();
$subjectsSynchronizationJobSubject1->setObjectId('9bb0f679-a883-4a6f-8260-35b491b8b8c8');
$subjectsSynchronizationJobSubject1->setObjectTypeName('User');
$subjectsArray []= $subjectsSynchronizationJobSubject1;
$parametersSynchronizationJobApplicationParameters1->setSubjects($subjectsArray);

$parametersSynchronizationJobApplicationParameters1->setRuleId('ea807875-5618-4f0a-9125-0b46a05298ca');
$parametersArray []= $parametersSynchronizationJobApplicationParameters1;
$requestBody->setParameters($parametersArray);


$result = $graphServiceClient->servicePrincipals()->byServicePrincipalId('servicePrincipal-id')->synchronization()->jobs()->bySynchronizationJobId('synchronizationJob-id')->provisionOnDemand()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Applications

$params = @{
	parameters = @(
		@{
			subjects = @(
				@{
					objectId = "9bb0f679-a883-4a6f-8260-35b491b8b8c8"
					objectTypeName = "User"
				}
			)
			ruleId = "ea807875-5618-4f0a-9125-0b46a05298ca"
		}
	)
}

New-MgServicePrincipalSynchronizationJobOnDemand -ServicePrincipalId $servicePrincipalId -SynchronizationJobId $synchronizationJobId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.serviceprincipals.item.synchronization.jobs.item.provision_on_demand.provision_on_demand_post_request_body import ProvisionOnDemandPostRequestBody
from msgraph.generated.models.synchronization_job_application_parameters import SynchronizationJobApplicationParameters
from msgraph.generated.models.synchronization_job_subject import SynchronizationJobSubject
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ProvisionOnDemandPostRequestBody(
	parameters = [
		SynchronizationJobApplicationParameters(
			subjects = [
				SynchronizationJobSubject(
					object_id = "9bb0f679-a883-4a6f-8260-35b491b8b8c8",
					object_type_name = "User",
				),
			],
			rule_id = "ea807875-5618-4f0a-9125-0b46a05298ca",
		),
	],
)

result = await graph_client.service_principals.by_service_principal_id('servicePrincipal-id').synchronization.jobs.by_synchronization_job_id('synchronizationJob-id').provision_on_demand.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

> **Note:** The response object shown here might be shortened for readability.

```
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#microsoft.graph.stringKeyStringValuePair",
    "key": "{\"result\":\"Skipped\",\"details\":{\"errorCode\":\"RedundantExport\",\"errorMessage\":\"The state of the user in both the source and target systems already match.\"}}",
    "value": "{\"action\":\"Other\",\"changeId\":\"g8ba3be8-1d7f-4a60-ae31-a8980da0a389\",\"endTime\":\"2020-06-26T13:58:24.7682084Z\",\"modifiedProperties\":[{\"displayName\":\"objectId\",\"oldValue\":null,\"newValue\":\"52cf7b7a-52be-4a9b-9c69-e4d4a4a14f76\"},{\"displayName\":\"accountEnabled\",\"oldValue\":null,\"newValue\":\"True\"},{\"displayName\":\"displayName\",\"oldValue\":null,\"newValue\":\"Bill Bob\"},{\"displayName\":\"mailNickname\",\"oldValue\":null,\"newValue\":\"Bill\"},{\"displayName\":\"userPrincipalName\",\"oldValue\":null,\"newValue\":\"BillBob@contoso.com\"},{\"displayName\":\"IsSoftDeleted\",\"oldValue\":null,\"newValue\":\"False\"},{\"displayName\":\"appRoleAssignments\",\"oldValue\":null,\"newValue\":\"User\"}],\"provisioningSteps\":[{\"name\":\"EntryImport\",\"type\":\"Import\",\"status\":\"Success\",\"description\":\"Retrieved User 'BillBob@contoso.com' from Azure Active Directory\",\"timestamp\":\"2020-06-26T13:58:24.5494971Z\",\"details\":{\"objectId\":\"52cf7b7a-52be-4a9b-9c69-e4d4a4a14f76\",\"accountEnabled\":\"True\",\"displayName\":\"Fill Bob\",\"mailNickname\":\"Bill\",\"userPrincipalName\":\"BillBob@contoso.com\",\"IsSoftDeleted\":\"False\",\"appRoleAssignments\":\"User\"}},{\"name\":\"EntryImport\",\"type\":\"Matching\",\"status\":\"Success\",\"description\":\"Retrieved  'BillBob@contoso.com' from customappsso\",\"timestamp\":\"2020-06-26T13:58:24.7214072Z\",\"details\":{\"active\":\"True\",\"displayName\":\"Bill Bob\",\"externalId\":\"Bill\",\"id\":\"52507a19-96ec-4e73-9250-3e65ffd2d926\",\"userName\":\"BillBob@contoso.com\"}},{\"name\":\"EntrySynchronizationScoping\",\"type\":\"Scoping\",\"status\":\"Success\",\"description\":\"Determine if User in scope by evaluating against each scoping filter\",\"timestamp\":\"2020-06-26T13:58:24.7526181Z\",\"details\":{\"IsActive\":\"True\",\"Assigned\":\"True\",\"IsEffectivelyEntitledForProvisioning\":\"True\",\"IsInProvisioningScopeDisplayName\":\"True\",\"ScopeEvaluationResult\":\"{}\"}},{\"name\":\"EntrySynchronizationSkip\",\"type\":\"Export\",\"status\":\"Skipped\",\"description\":\"The state of the user in both the source and target systems already match. No change to the User 'BillBob@contoso.com' currently needs to be made.\",\"timestamp\":\"2020-06-26T13:58:24.7682084Z\",\"details\":{\"SkipReason\":\"RedundantExport\"}}],\"reportableIdentifier\":\"BillBob@contoso.com\",\"startTime\":\"2020-06-26T13:58:24.5494971Z\",\"statusInfo\":{\"status\":\"Skipped\",\"errorCode\":null,\"reason\":null,\"additionalDetails\":null,\"errorCategory\":null,\"recommendedAction\":null},\"sourceIdentity\":{\"id\":\"62cf7b7a-52be-4a9b-9c69-e5d4a4a14f67\",\"type\":\"User\",\"displayName\":null,\"details\":null},\"sourceSystem\":{\"id\":null,\"name\":\"Azure Active Directory\",\"details\":null},\"targetIdentity\":{\"id\":\"52507a19-96ec-4e73-9250-3e65ffd2d926\",\"type\":\"urn:ietf:params:scim:schemas:extension:enterprise:2.0:User\",\"displayName\":null,\"details\":null},\"targetSystem\":{\"id\":null,\"name\":\"customappsso\",\"details\":null}}"
}
```

### Example 2: Sync on-demand from Active Directory to Microsoft Entra ID \(Microsoft Entra Cloud Sync\)

#### Request

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/servicePrincipals/3e916d82-dd59-4944-824d-93092908fd8d/synchronization/jobs/264ea562-28cd-42b1-93e0-8de1f0560581/provisionOnDemand
Content-Type: application/json

{
  "parameters": [
    {
      "ruleId": "6c409270-f78a-4bc6-af23-7cf3ab6482fe",
      "subjects": [
        {
          "objectId": "CN=AdeleV,CN=Users,DC=corp,DC=chicago,DC=com",
          "objectTypeName": "user"
        }
      ]
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.ServicePrincipals.Item.Synchronization.Jobs.Item.ProvisionOnDemand;
using Microsoft.Graph.Models;

var requestBody = new ProvisionOnDemandPostRequestBody
{
	Parameters = new List<SynchronizationJobApplicationParameters>
	{
		new SynchronizationJobApplicationParameters
		{
			RuleId = "6c409270-f78a-4bc6-af23-7cf3ab6482fe",
			Subjects = new List<SynchronizationJobSubject>
			{
				new SynchronizationJobSubject
				{
					ObjectId = "CN=AdeleV,CN=Users,DC=corp,DC=chicago,DC=com",
					ObjectTypeName = "user",
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.ServicePrincipals["{servicePrincipal-id}"].Synchronization.Jobs["{synchronizationJob-id}"].ProvisionOnDemand.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphserviceprincipals "github.com/microsoftgraph/msgraph-sdk-go/serviceprincipals"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphserviceprincipals.NewProvisionOnDemandPostRequestBody()


synchronizationJobApplicationParameters := graphmodels.NewSynchronizationJobApplicationParameters()
ruleId := "6c409270-f78a-4bc6-af23-7cf3ab6482fe"
synchronizationJobApplicationParameters.SetRuleId(&ruleId) 


synchronizationJobSubject := graphmodels.NewSynchronizationJobSubject()
objectId := "CN=AdeleV,CN=Users,DC=corp,DC=chicago,DC=com"
synchronizationJobSubject.SetObjectId(&objectId) 
objectTypeName := "user"
synchronizationJobSubject.SetObjectTypeName(&objectTypeName) 

subjects := []graphmodels.SynchronizationJobSubjectable {
	synchronizationJobSubject,
}
synchronizationJobApplicationParameters.SetSubjects(subjects)

parameters := []graphmodels.SynchronizationJobApplicationParametersable {
	synchronizationJobApplicationParameters,
}
requestBody.SetParameters(parameters)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
provisionOnDemand, err := graphClient.ServicePrincipals().ByServicePrincipalId("servicePrincipal-id").Synchronization().Jobs().BySynchronizationJobId("synchronizationJob-id").ProvisionOnDemand().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.serviceprincipals.item.synchronization.jobs.item.provisionondemand.ProvisionOnDemandPostRequestBody provisionOnDemandPostRequestBody = new com.microsoft.graph.serviceprincipals.item.synchronization.jobs.item.provisionondemand.ProvisionOnDemandPostRequestBody();
LinkedList<SynchronizationJobApplicationParameters> parameters = new LinkedList<SynchronizationJobApplicationParameters>();
SynchronizationJobApplicationParameters synchronizationJobApplicationParameters = new SynchronizationJobApplicationParameters();
synchronizationJobApplicationParameters.setRuleId("6c409270-f78a-4bc6-af23-7cf3ab6482fe");
LinkedList<SynchronizationJobSubject> subjects = new LinkedList<SynchronizationJobSubject>();
SynchronizationJobSubject synchronizationJobSubject = new SynchronizationJobSubject();
synchronizationJobSubject.setObjectId("CN=AdeleV,CN=Users,DC=corp,DC=chicago,DC=com");
synchronizationJobSubject.setObjectTypeName("user");
subjects.add(synchronizationJobSubject);
synchronizationJobApplicationParameters.setSubjects(subjects);
parameters.add(synchronizationJobApplicationParameters);
provisionOnDemandPostRequestBody.setParameters(parameters);
StringKeyStringValuePair result = graphClient.servicePrincipals().byServicePrincipalId("{servicePrincipal-id}").synchronization().jobs().bySynchronizationJobId("{synchronizationJob-id}").provisionOnDemand().post(provisionOnDemandPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const stringKeyStringValuePair = {
  parameters: [
    {
      ruleId: '6c409270-f78a-4bc6-af23-7cf3ab6482fe',
      subjects: [
        {
          objectId: 'CN=AdeleV,CN=Users,DC=corp,DC=chicago,DC=com',
          objectTypeName: 'user'
        }
      ]
    }
  ]
};

await client.api('/servicePrincipals/3e916d82-dd59-4944-824d-93092908fd8d/synchronization/jobs/264ea562-28cd-42b1-93e0-8de1f0560581/provisionOnDemand')
	.post(stringKeyStringValuePair);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\ServicePrincipals\Item\Synchronization\Jobs\Item\ProvisionOnDemand\ProvisionOnDemandPostRequestBody;
use Microsoft\Graph\Generated\Models\SynchronizationJobApplicationParameters;
use Microsoft\Graph\Generated\Models\SynchronizationJobSubject;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ProvisionOnDemandPostRequestBody();
$parametersSynchronizationJobApplicationParameters1 = new SynchronizationJobApplicationParameters();
$parametersSynchronizationJobApplicationParameters1->setRuleId('6c409270-f78a-4bc6-af23-7cf3ab6482fe');
$subjectsSynchronizationJobSubject1 = new SynchronizationJobSubject();
$subjectsSynchronizationJobSubject1->setObjectId('CN=AdeleV,CN=Users,DC=corp,DC=chicago,DC=com');
$subjectsSynchronizationJobSubject1->setObjectTypeName('user');
$subjectsArray []= $subjectsSynchronizationJobSubject1;
$parametersSynchronizationJobApplicationParameters1->setSubjects($subjectsArray);

$parametersArray []= $parametersSynchronizationJobApplicationParameters1;
$requestBody->setParameters($parametersArray);


$result = $graphServiceClient->servicePrincipals()->byServicePrincipalId('servicePrincipal-id')->synchronization()->jobs()->bySynchronizationJobId('synchronizationJob-id')->provisionOnDemand()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Applications

$params = @{
	parameters = @(
		@{
			ruleId = "6c409270-f78a-4bc6-af23-7cf3ab6482fe"
			subjects = @(
				@{
					objectId = "CN=AdeleV,CN=Users,DC=corp,DC=chicago,DC=com"
					objectTypeName = "user"
				}
			)
		}
	)
}

New-MgServicePrincipalSynchronizationJobOnDemand -ServicePrincipalId $servicePrincipalId -SynchronizationJobId $synchronizationJobId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.serviceprincipals.item.synchronization.jobs.item.provision_on_demand.provision_on_demand_post_request_body import ProvisionOnDemandPostRequestBody
from msgraph.generated.models.synchronization_job_application_parameters import SynchronizationJobApplicationParameters
from msgraph.generated.models.synchronization_job_subject import SynchronizationJobSubject
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ProvisionOnDemandPostRequestBody(
	parameters = [
		SynchronizationJobApplicationParameters(
			rule_id = "6c409270-f78a-4bc6-af23-7cf3ab6482fe",
			subjects = [
				SynchronizationJobSubject(
					object_id = "CN=AdeleV,CN=Users,DC=corp,DC=chicago,DC=com",
					object_type_name = "user",
				),
			],
		),
	],
)

result = await graph_client.service_principals.by_service_principal_id('servicePrincipal-id').synchronization.jobs.by_synchronization_job_id('synchronizationJob-id').provision_on_demand.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

> **Note:** The response object shown here might be shortened for readability.

```
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://syncfabric.windowsazure.com/api/$metadata#microsoft.synchronization.stringKeyStringValuePair",
    "key": "{\"result\":\"Success\",\"details\":{}}",
    "value": "{\"provisioningSteps\":[{\"name\":\"EntryImportAdd\",\"type\":\"Import\",\"status\":\"Success\",\"description\":\"Received user 'adelev@chicago.com' change of type (Add) from Active Directory\",\"timestamp\":\"2022-04-21T18:40:07.8465145Z\",\"details\":{\"distinguishedName\":\"CN=AdeleV,CN=Users,DC=corp,DC=chicago,DC=com\",\"cn\":\"Adele Vest\",\"originatingReplicaToken\":\"{\\\"InvocationId\\\":\\\"6cbd7b45-b262-4dad-94a3-620503ea1f25\\\",\\\"Name\\\":\\\"DC01.esf.edu\\\"}\",\"sAMAccountName\":\"adelev\",\"targetAddress\":\"SMTP:adelev@contoso.com\",\"givenName\":\"Adele\",\"objectSid\":\"AQUAAAAAAAUVAAAAXAMNf/YJ8nmaUZofGG4BAA==\",\"displayName\":\"Adele Vest\",\"msExchMailboxGuid\":\"+klu7DM5yE+9tOs6MuGxsw==\",\"msExchELCMailboxFlags\":\"2\",\"pwdLastSet\":\"132772253564048004\",\"initials\":\"S\",\"msExchRecipientDisplayType\":\"-2147483642\",\"streetAddress\":\"One Microsoft Way\",\"mail\":\"adelev@chicago.com\",\"sn\":\"AdeleV\",\"msExchSafeSendersHash\":\"gny5JQ==\",\"proxyAddresses\":\"X, 5, 0,  ... X400:C=US;A= ;P=ESF;O=MAIL;S=AdeleV;G=Adele;I=S; (5)\",\"objectGUID\":\"xxxxxxxLIUuBM8qK5Sxxxx\",\"legacyExchangeDN\":\"/o=ESF/ou=External (FYDIBOHF25SPDLT)/cn=Recipients/cn=b499521b46264967a6de75f1a08add7a\",\"msExchRecipientTypeDetails\":\"2147483648\",\"userAccountControl\":\"66048\",\"accountDisabled\":\"False\",\"countryCode\":\"840\",\"co\":\"United States\",\"l\":\"Chicago\",\"extensionAttribute10\":\"839153607\",\"c\":\"US\",\"mS-DS-ConsistencyGuid\":\"xxxxxxxLIUuBM8qK5Sxxxx\",\"mailNickname\":\"adelev\",\"st\":\"NY\",\"extensionAttribute15\":\"C1EA2EA6EC56F3D94D2D89D95D70E4D0\",\"extensionAttribute14\":\"F00177677\",\"postalCode\":\"13210\",\"extensionAttribute6\":\"A5\",\"msExchRemoteRecipientType\":\"4\",\"extensionAttribute5\":\"11\",\"userPrincipalName\":\"adelev@chicago.com\",\"adminDescription\":\"\",\"company\":\"\",\"department\":\"\",\"description\":\"\",\"employeeID\":\"\",\"employeeNumber\":\"\",\"employeeType\":\"\",\"errors\":\"\",\"extensionAttribute1\":\"\",\"extensionAttribute11\":\"\",\"extensionAttribute12\":\"\",\"extensionAttribute13\":\"\",\"extensionAttribute2\":\"\",\"extensionAttribute3\":\"\",\"extensionAttribute4\":\"\",\"extensionAttribute7\":\"\",\"extensionAttribute8\":\"\",\"extensionAttribute9\":\"\",\"facsimileTelephoneNumber\":\"\",\"homePhone\":\"\",\"info\":\"\",\"ipPhone\":\"\",\"isCriticalSystemObject\":\"\",\"logs\":\"\",\"middleName\":\"\",\"mobile\":\"\",\"msDS-HABSeniorityIndex\":\"\",\"msDS-InclusionTrigger\":\"\",\"msDS-PhoneticDisplayName\":\"\",\"msDS-preferredDataLocation\":\"\",\"msExchArchiveGUID\":\"\",\"msExchArchiveName\":\"\",\"msExchAssistantName\":\"\",\"msExchAuditAdmin\":\"\",\"msExchAuditDelegate\":\"\",\"msExchAuditDelegateAdmin\":\"\",\"msExchAuditOwner\":\"\",\"msExchBlockedSendersHash\":\"\",\"msExchBypassAudit\":\"\",\"msExchELCExpirySuspensionEnd\":\"\",\"msExchELCExpirySuspensionStart\":\"\",\"msExchEnableModeration\":\"\",\"msExchExtensionCustomAttribute1\":\"\",\"msExchExtensionCustomAttribute2\":\"\",\"msExchExtensionCustomAttribute3\":\"\",\"msExchExtensionCustomAttribute4\":\"\",\"msExchExtensionCustomAttribute5\":\"\",\"msExchHideFromAddressLists\":\"\",\"msExchImmutableId\":\"\",\"msExchLitigationHoldDate\":\"\",\"msExchLitigationHoldOwner\":\"\",\"msExchMailboxAuditEnable\":\"\",\"msExchMailboxAuditLogAgeLimit\":\"\",\"msExchModerationFlags\":\"\",\"msExchRequireAuthToSendTo\":\"\",\"msExchResourceCapacity\":\"\",\"msExchResourceDisplay\":\"\",\"msExchResourceMetaData\":\"\",\"msExchResourceSearchProperties\":\"\",\"msExchRetentionComment\":\"\",\"msExchRetentionURL\":\"\",\"msExchSafeRecipientsHash\":\"\",\"msExchSenderHintTranslations\":\"\",\"msExchTeamMailboxExpiration\":\"\",\"msExchTeamMailboxSharePointUrl\":\"\",\"msExchUsageLocation\":\"\",\"msExchUserHoldPolicies\":\"\",\"msRTCSIP-ApplicationOptions\":\"\",\"mSRTCSIP-DeploymentLocator\":\"\",\"msRTCSIP-Line\":\"\",\"msRTCSIP-OptionFlags\":\"\",\"msRTCSIP-OwnerUrn\":\"\",\"msRTCSIP-PrimaryUserAddress\":\"\",\"msRTCSIP-UserEnabled\":\"\",\"objectClass\":\"\",\"otherFacsimileTelephoneNumber\":\"\",\"otherHomePhone\":\"\",\"otherIpPhone\":\"\",\"otherMobile\":\"\",\"otherPager\":\"\",\"otherTelephone\":\"\",\"pager\":\"\",\"physicalDeliveryOfficeName\":\"\",\"postOfficeBox\":\"\",\"preferredLanguage\":\"\",\"telephoneAssistant\":\"\",\"telephoneNumber\":\"\",\"thumbnailPhoto\":\"\",\"title\":\"\",\"url\":\"\",\"userCertificate\":\"\",\"userSMIMECertificate\":\"\",\"whenChanged\":\"\",\"wWWHomePage\":\"\"}},{\"name\":\"EntryImport\",\"type\":\"Import\",\"status\":\"Success\",\"description\":\"Retrieved user 'adelev@chicago.com' from Active Directory\",\"timestamp\":\"2022-04-21T18:40:07.8778004Z\",\"details\":{\"distinguishedName\":\"CN=AdeleV,CN=Users,DC=corp,DC=chicago,DC=com\",\"cn\":\"Adele Vest\",\"originatingReplicaToken\":\"{\\\"InvocationId\\\":\\\"6cbd7b45-b262-4dad-94a3-620503ea1f25\\\",\\\"Name\\\":\\\"DC01.esf.edu\\\"}\",\"sAMAccountName\":\"adelev\",\"targetAddress\":\"SMTP:adelev@contoso.com\",\"givenName\":\"Adele\",\"objectSid\":\"AQUAAAAAAAUVAAAAXAMNf/YJ8nmaUZofGG4BAA==\",\"displayName\":\"Adele Vest\",\"msExchMailboxGuid\":\"+klu7DM5yE+9tOs6MuGxsw==\",\"msExchELCMailboxFlags\":\"2\",\"pwdLastSet\":\"132772253564048004\",\"initials\":\"S\",\"msExchRecipientDisplayType\":\"-2147483642\",\"streetAddress\":\"One Microsoft Way\",\"mail\":\"adelev@chicago.com\",\"sn\":\"AdeleV\",\"msExchSafeSendersHash\":\"gny5JQ==\",\"proxyAddresses\":\"X, 5, 0,  ... X400:C=US;A= ;P=ESF;O=MAIL;S=AdeleV;G=Adele;I=S; (5)\",\"objectGUID\":\"xxxxxxxLIUuBM8qK5Sxxxx\",\"legacyExchangeDN\":\"/o=ESF/ou=External (FYDIBOHF25SPDLT)/cn=Recipients/cn=b499521b46264967a6de75f1a08add7a\",\"msExchRecipientTypeDetails\":\"2147483648\",\"userAccountControl\":\"66048\",\"accountDisabled\":\"False\",\"countryCode\":\"840\",\"co\":\"United States\",\"l\":\"Chicago\",\"extensionAttribute10\":\"839153607\",\"c\":\"US\",\"mS-DS-ConsistencyGuid\":\"xxxxxxxLIUuBM8qK5Sxxxx\",\"mailNickname\":\"adelev\",\"st\":\"NY\",\"extensionAttribute15\":\"C1EA2EA6EC56F3D94D2D89D95D70E4D0\",\"extensionAttribute14\":\"F00177677\",\"postalCode\":\"13210\",\"extensionAttribute6\":\"A5\",\"msExchRemoteRecipientType\":\"4\",\"extensionAttribute5\":\"11\",\"userPrincipalName\":\"adelev@chicago.com\",\"adminDescription\":\"\",\"company\":\"\",\"department\":\"\",\"description\":\"\",\"employeeID\":\"\",\"employeeNumber\":\"\",\"employeeType\":\"\",\"errors\":\"\",\"extensionAttribute1\":\"\",\"extensionAttribute11\":\"\",\"extensionAttribute12\":\"\",\"extensionAttribute13\":\"\",\"extensionAttribute2\":\"\",\"extensionAttribute3\":\"\",\"extensionAttribute4\":\"\",\"extensionAttribute7\":\"\",\"extensionAttribute8\":\"\",\"extensionAttribute9\":\"\",\"facsimileTelephoneNumber\":\"\",\"homePhone\":\"\",\"info\":\"\",\"ipPhone\":\"\",\"isCriticalSystemObject\":\"\",\"logs\":\"\",\"middleName\":\"\",\"mobile\":\"\",\"msDS-HABSeniorityIndex\":\"\",\"msDS-InclusionTrigger\":\"\",\"msDS-PhoneticDisplayName\":\"\",\"msDS-preferredDataLocation\":\"\",\"msExchArchiveGUID\":\"\",\"msExchArchiveName\":\"\",\"msExchAssistantName\":\"\",\"msExchAuditAdmin\":\"\",\"msExchAuditDelegate\":\"\",\"msExchAuditDelegateAdmin\":\"\",\"msExchAuditOwner\":\"\",\"msExchBlockedSendersHash\":\"\",\"msExchBypassAudit\":\"\",\"msExchELCExpirySuspensionEnd\":\"\",\"msExchELCExpirySuspensionStart\":\"\",\"msExchEnableModeration\":\"\",\"msExchExtensionCustomAttribute1\":\"\",\"msExchExtensionCustomAttribute2\":\"\",\"msExchExtensionCustomAttribute3\":\"\",\"msExchExtensionCustomAttribute4\":\"\",\"msExchExtensionCustomAttribute5\":\"\",\"msExchHideFromAddressLists\":\"\",\"msExchImmutableId\":\"\",\"msExchLitigationHoldDate\":\"\",\"msExchLitigationHoldOwner\":\"\",\"msExchMailboxAuditEnable\":\"\",\"msExchMailboxAuditLogAgeLimit\":\"\",\"msExchModerationFlags\":\"\",\"msExchRequireAuthToSendTo\":\"\",\"msExchResourceCapacity\":\"\",\"msExchResourceDisplay\":\"\",\"msExchResourceMetaData\":\"\",\"msExchResourceSearchProperties\":\"\",\"msExchRetentionComment\":\"\",\"msExchRetentionURL\":\"\",\"msExchSafeRecipientsHash\":\"\",\"msExchSenderHintTranslations\":\"\",\"msExchTeamMailboxExpiration\":\"\",\"msExchTeamMailboxSharePointUrl\":\"\",\"msExchUsageLocation\":\"\",\"msExchUserHoldPolicies\":\"\",\"msRTCSIP-ApplicationOptions\":\"\",\"mSRTCSIP-DeploymentLocator\":\"\",\"msRTCSIP-Line\":\"\",\"msRTCSIP-OptionFlags\":\"\",\"msRTCSIP-OwnerUrn\":\"\",\"msRTCSIP-PrimaryUserAddress\":\"\",\"msRTCSIP-UserEnabled\":\"\",\"objectClass\":\"\",\"otherFacsimileTelephoneNumber\":\"\",\"otherHomePhone\":\"\",\"otherIpPhone\":\"\",\"otherMobile\":\"\",\"otherPager\":\"\",\"otherTelephone\":\"\",\"pager\":\"\",\"physicalDeliveryOfficeName\":\"\",\"postOfficeBox\":\"\",\"preferredLanguage\":\"\",\"telephoneAssistant\":\"\",\"telephoneNumber\":\"\",\"thumbnailPhoto\":\"\",\"title\":\"\",\"url\":\"\",\"userCertificate\":\"\",\"userSMIMECertificate\":\"\",\"whenChanged\":\"\",\"wWWHomePage\":\"\"}},{\"name\":\"EntrySynchronizationScoping\",\"type\":\"Scoping\",\"status\":\"Success\",\"description\":\"Determine if user in scope by evaluating against each scoping filter\",\"timestamp\":\"2022-04-21T18:40:08.1590133Z\",\"details\":{\"Active in the source system\":\"True\",\"Scoping filter evaluation passed\":\"True\"}},{\"name\":\"EntryExportUpdate\",\"type\":\"Export\",\"status\":\"Success\",\"description\":\"User 'adelev@chicago.com' was updated in Azure Active Directory\",\"timestamp\":\"2022-04-21T18:40:09.5184649Z\",\"details\":{}}],\"modifiedProperties\":[{\"displayName\":\"AccountEnabled\",\"newValue\":\"True\"},{\"displayName\":\"Alias\",\"newValue\":\"adelev\"},{\"displayName\":\"City\",\"newValue\":\"Chicago\"},{\"displayName\":\"CommonName\",\"newValue\":\"Adele Vest\"},{\"displayName\":\"Country\",\"newValue\":\"United States\"},{\"displayName\":\"CountryCode\",\"newValue\":\"840\"},{\"displayName\":\"CountryLetterCode\",\"newValue\":\"US\"},{\"displayName\":\"DisplayName\",\"newValue\":\"Adele Vest\"},{\"displayName\":\"DnsDomainName\",\"newValue\":\"esf.edu\"},{\"displayName\":\"ExtensionAttribute10\",\"newValue\":\"839153607\"},{\"displayName\":\"ExtensionAttribute14\",\"newValue\":\"F00177677\"},{\"displayName\":\"ExtensionAttribute15\",\"newValue\":\"C1EA2EA6EC56F3D94D2D89D95D70E4D0\"},{\"displayName\":\"ExtensionAttribute5\",\"newValue\":\"11\"},{\"displayName\":\"ExtensionAttribute6\",\"newValue\":\"A5\"},{\"displayName\":\"GivenName\",\"newValue\":\"Adele\"},{\"displayName\":\"Initials\",\"newValue\":\"S\"},{\"displayName\":\"LastPasswordChangeTimestamp\",\"newValue\":\"20210927140916.0Z\"},{\"displayName\":\"LegacyExchangeDN\",\"newValue\":\"/o=ESF/ou=External (FYDIBOHF25SPDLT)/cn=Recipients/cn=b499521b46264967a6de75f1a08add7a\"},{\"displayName\":\"Mail\",\"newValue\":\"adelev@chicago.com\"},{\"displayName\":\"MSExchElcMailboxFlags\",\"newValue\":\"2\"},{\"displayName\":\"MSExchMailboxGuid\",\"newValue\":\"+klu7DM5yE+9tOs6MuGxsw==\"},{\"displayName\":\"MSExchRecipientDisplayType\",\"newValue\":\"-2147483642\"},{\"displayName\":\"MSExchRecipientTypeDetails\",\"newValue\":\"2147483648\"},{\"displayName\":\"MSExchRemoteRecipientType\",\"newValue\":\"4\"},{\"displayName\":\"MSExchSafeSendersHash\",\"newValue\":\"gny5JQ==\"},{\"displayName\":\"NetBiosName\",\"newValue\":\"ESF\"},{\"displayName\":\"OnPremisesDistinguishedName\",\"newValue\":\"CN=AdeleV,CN=Users,DC=corp,DC=chicago,DC=com\"},{\"displayName\":\"OnPremiseSecurityIdentifier\",\"newValue\":\"AQUAAAAAAAUVAAAAXAMNf/YJ8nmaUZofGG4BAA==\"},{\"displayName\":\"OnPremisesSamAccountName\",\"newValue\":\"adelev\"},{\"displayName\":\"OnPremisesUserPrincipalName\",\"newValue\":\"adelev@chicago.com\"},{\"displayName\":\"PostalCode\",\"newValue\":\"13210\"},{\"displayName\":\"ProxyAddresses\",\"newValue\":\"X, 5, 0,  ... X400:C=US;A= ;P=ESF;O=MAIL;S=AdeleV;G=Adele;I=S; (5)\"},{\"displayName\":\"State\",\"newValue\":\"NY\"},{\"displayName\":\"StreetAddress\",\"newValue\":\"One Microsoft Way\"},{\"displayName\":\"Surname\",\"newValue\":\"AdeleV\"},{\"displayName\":\"TargetAddress\",\"newValue\":\"SMTP:adelev@contoso.com\"},{\"displayName\":\"UserPrincipalName\",\"newValue\":\"adelev@chicago.com\"}],\"action\":\"Update\",\"changeId\":\"582595f3-53be-4843-bf0c-f57dbf8fae96\",\"endTime\":\"2022-04-21T18:40:09.5496702Z\",\"reportableIdentifier\":\"adelev@chicago.com\",\"sourceIdentity\":{\"id\":\"38a2171b-8b04-4b21-8133-ca8ae52250f3\",\"type\":\"user\"},\"sourceSystem\":{\"name\":\"Active Directory\"},\"startTime\":\"2022-04-21T18:40:07.8309453Z\",\"statusInfo\":{\"status\":\"Success\"},\"targetIdentity\":{\"id\":\"87cb2512-8e7f-4543-a9c9-e7cf8756a3ad\",\"type\":\"User\"},\"targetSystem\":{\"name\":\"Azure Active Directory\"}}"
}
```

### Example 3: Provision a group and two of its members on demand

#### Request

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```http
POST https://graph.microsoft.com/v1.0/servicePrincipals/4e116d82-dd59-4944-824d-93091408fd8d/synchronization/jobs/664ea562-18cd-42bb-33e0-8de1f0560581/provisionOnDemand
Content-Type: application/json

{
  "parameters": [
    {
      "ruleId": "33f7c90d-bf71-41b1-bda6-aaf0ddbee5d8#V2",
      "subjects": [
        {
          "objectId": "8213fd99-d6b6-417b-8e13-af6334856215",
          "objectTypeName": "Group",
          "links": {
            "members": [
              {
                "objectId": "cbc86211-6ada-4803-b73f-8039cf56d8a2",
                "objectTypeName": "User"
              },
              {
                "objectId": "2bc86211-6ada-4803-b73f-8039cf56d8a2",
                "objectTypeName": "User"
              }
            ]
          }
        }
      ]
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.ServicePrincipals.Item.Synchronization.Jobs.Item.ProvisionOnDemand;
using Microsoft.Graph.Models;

var requestBody = new ProvisionOnDemandPostRequestBody
{
	Parameters = new List<SynchronizationJobApplicationParameters>
	{
		new SynchronizationJobApplicationParameters
		{
			RuleId = "33f7c90d-bf71-41b1-bda6-aaf0ddbee5d8#V2",
			Subjects = new List<SynchronizationJobSubject>
			{
				new SynchronizationJobSubject
				{
					ObjectId = "8213fd99-d6b6-417b-8e13-af6334856215",
					ObjectTypeName = "Group",
					Links = new SynchronizationLinkedObjects
					{
						Members = new List<SynchronizationJobSubject>
						{
							new SynchronizationJobSubject
							{
								ObjectId = "cbc86211-6ada-4803-b73f-8039cf56d8a2",
								ObjectTypeName = "User",
							},
							new SynchronizationJobSubject
							{
								ObjectId = "2bc86211-6ada-4803-b73f-8039cf56d8a2",
								ObjectTypeName = "User",
							},
						},
					},
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.ServicePrincipals["{servicePrincipal-id}"].Synchronization.Jobs["{synchronizationJob-id}"].ProvisionOnDemand.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphserviceprincipals "github.com/microsoftgraph/msgraph-sdk-go/serviceprincipals"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphserviceprincipals.NewProvisionOnDemandPostRequestBody()


synchronizationJobApplicationParameters := graphmodels.NewSynchronizationJobApplicationParameters()
ruleId := "33f7c90d-bf71-41b1-bda6-aaf0ddbee5d8#V2"
synchronizationJobApplicationParameters.SetRuleId(&ruleId) 


synchronizationJobSubject := graphmodels.NewSynchronizationJobSubject()
objectId := "8213fd99-d6b6-417b-8e13-af6334856215"
synchronizationJobSubject.SetObjectId(&objectId) 
objectTypeName := "Group"
synchronizationJobSubject.SetObjectTypeName(&objectTypeName) 
links := graphmodels.NewSynchronizationLinkedObjects()


synchronizationJobSubject := graphmodels.NewSynchronizationJobSubject()
objectId := "cbc86211-6ada-4803-b73f-8039cf56d8a2"
synchronizationJobSubject.SetObjectId(&objectId) 
objectTypeName := "User"
synchronizationJobSubject.SetObjectTypeName(&objectTypeName) 
synchronizationJobSubject1 := graphmodels.NewSynchronizationJobSubject()
objectId := "2bc86211-6ada-4803-b73f-8039cf56d8a2"
synchronizationJobSubject1.SetObjectId(&objectId) 
objectTypeName := "User"
synchronizationJobSubject1.SetObjectTypeName(&objectTypeName) 

members := []graphmodels.SynchronizationJobSubjectable {
	synchronizationJobSubject,
	synchronizationJobSubject1,
}
links.SetMembers(members)
synchronizationJobSubject.SetLinks(links)

subjects := []graphmodels.SynchronizationJobSubjectable {
	synchronizationJobSubject,
}
synchronizationJobApplicationParameters.SetSubjects(subjects)

parameters := []graphmodels.SynchronizationJobApplicationParametersable {
	synchronizationJobApplicationParameters,
}
requestBody.SetParameters(parameters)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
provisionOnDemand, err := graphClient.ServicePrincipals().ByServicePrincipalId("servicePrincipal-id").Synchronization().Jobs().BySynchronizationJobId("synchronizationJob-id").ProvisionOnDemand().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.serviceprincipals.item.synchronization.jobs.item.provisionondemand.ProvisionOnDemandPostRequestBody provisionOnDemandPostRequestBody = new com.microsoft.graph.serviceprincipals.item.synchronization.jobs.item.provisionondemand.ProvisionOnDemandPostRequestBody();
LinkedList<SynchronizationJobApplicationParameters> parameters = new LinkedList<SynchronizationJobApplicationParameters>();
SynchronizationJobApplicationParameters synchronizationJobApplicationParameters = new SynchronizationJobApplicationParameters();
synchronizationJobApplicationParameters.setRuleId("33f7c90d-bf71-41b1-bda6-aaf0ddbee5d8#V2");
LinkedList<SynchronizationJobSubject> subjects = new LinkedList<SynchronizationJobSubject>();
SynchronizationJobSubject synchronizationJobSubject = new SynchronizationJobSubject();
synchronizationJobSubject.setObjectId("8213fd99-d6b6-417b-8e13-af6334856215");
synchronizationJobSubject.setObjectTypeName("Group");
SynchronizationLinkedObjects links = new SynchronizationLinkedObjects();
LinkedList<SynchronizationJobSubject> members = new LinkedList<SynchronizationJobSubject>();
SynchronizationJobSubject synchronizationJobSubject1 = new SynchronizationJobSubject();
synchronizationJobSubject1.setObjectId("cbc86211-6ada-4803-b73f-8039cf56d8a2");
synchronizationJobSubject1.setObjectTypeName("User");
members.add(synchronizationJobSubject1);
SynchronizationJobSubject synchronizationJobSubject2 = new SynchronizationJobSubject();
synchronizationJobSubject2.setObjectId("2bc86211-6ada-4803-b73f-8039cf56d8a2");
synchronizationJobSubject2.setObjectTypeName("User");
members.add(synchronizationJobSubject2);
links.setMembers(members);
synchronizationJobSubject.setLinks(links);
subjects.add(synchronizationJobSubject);
synchronizationJobApplicationParameters.setSubjects(subjects);
parameters.add(synchronizationJobApplicationParameters);
provisionOnDemandPostRequestBody.setParameters(parameters);
StringKeyStringValuePair result = graphClient.servicePrincipals().byServicePrincipalId("{servicePrincipal-id}").synchronization().jobs().bySynchronizationJobId("{synchronizationJob-id}").provisionOnDemand().post(provisionOnDemandPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const stringKeyStringValuePair = {
  parameters: [
    {
      ruleId: '33f7c90d-bf71-41b1-bda6-aaf0ddbee5d8#V2',
      subjects: [
        {
          objectId: '8213fd99-d6b6-417b-8e13-af6334856215',
          objectTypeName: 'Group',
          links: {
            members: [
              {
                objectId: 'cbc86211-6ada-4803-b73f-8039cf56d8a2',
                objectTypeName: 'User'
              },
              {
                objectId: '2bc86211-6ada-4803-b73f-8039cf56d8a2',
                objectTypeName: 'User'
              }
            ]
          }
        }
      ]
    }
  ]
};

await client.api('/servicePrincipals/4e116d82-dd59-4944-824d-93091408fd8d/synchronization/jobs/664ea562-18cd-42bb-33e0-8de1f0560581/provisionOnDemand')
	.post(stringKeyStringValuePair);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\ServicePrincipals\Item\Synchronization\Jobs\Item\ProvisionOnDemand\ProvisionOnDemandPostRequestBody;
use Microsoft\Graph\Generated\Models\SynchronizationJobApplicationParameters;
use Microsoft\Graph\Generated\Models\SynchronizationJobSubject;
use Microsoft\Graph\Generated\Models\SynchronizationLinkedObjects;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ProvisionOnDemandPostRequestBody();
$parametersSynchronizationJobApplicationParameters1 = new SynchronizationJobApplicationParameters();
$parametersSynchronizationJobApplicationParameters1->setRuleId('33f7c90d-bf71-41b1-bda6-aaf0ddbee5d8#V2');
$subjectsSynchronizationJobSubject1 = new SynchronizationJobSubject();
$subjectsSynchronizationJobSubject1->setObjectId('8213fd99-d6b6-417b-8e13-af6334856215');
$subjectsSynchronizationJobSubject1->setObjectTypeName('Group');
$subjectsSynchronizationJobSubject1Links = new SynchronizationLinkedObjects();
$membersSynchronizationJobSubject1 = new SynchronizationJobSubject();
$membersSynchronizationJobSubject1->setObjectId('cbc86211-6ada-4803-b73f-8039cf56d8a2');
$membersSynchronizationJobSubject1->setObjectTypeName('User');
$membersArray []= $membersSynchronizationJobSubject1;
$membersSynchronizationJobSubject2 = new SynchronizationJobSubject();
$membersSynchronizationJobSubject2->setObjectId('2bc86211-6ada-4803-b73f-8039cf56d8a2');
$membersSynchronizationJobSubject2->setObjectTypeName('User');
$membersArray []= $membersSynchronizationJobSubject2;
$subjectsSynchronizationJobSubject1Links->setMembers($membersArray);

$subjectsSynchronizationJobSubject1->setLinks($subjectsSynchronizationJobSubject1Links);
$subjectsArray []= $subjectsSynchronizationJobSubject1;
$parametersSynchronizationJobApplicationParameters1->setSubjects($subjectsArray);

$parametersArray []= $parametersSynchronizationJobApplicationParameters1;
$requestBody->setParameters($parametersArray);


$result = $graphServiceClient->servicePrincipals()->byServicePrincipalId('servicePrincipal-id')->synchronization()->jobs()->bySynchronizationJobId('synchronizationJob-id')->provisionOnDemand()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Applications

$params = @{
	parameters = @(
		@{
			ruleId = "33f7c90d-bf71-41b1-bda6-aaf0ddbee5d8#V2"
			subjects = @(
				@{
					objectId = "8213fd99-d6b6-417b-8e13-af6334856215"
					objectTypeName = "Group"
					links = @{
						members = @(
							@{
								objectId = "cbc86211-6ada-4803-b73f-8039cf56d8a2"
								objectTypeName = "User"
							}
							@{
								objectId = "2bc86211-6ada-4803-b73f-8039cf56d8a2"
								objectTypeName = "User"
							}
						)
					}
				}
			)
		}
	)
}

New-MgServicePrincipalSynchronizationJobOnDemand -ServicePrincipalId $servicePrincipalId -SynchronizationJobId $synchronizationJobId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.serviceprincipals.item.synchronization.jobs.item.provision_on_demand.provision_on_demand_post_request_body import ProvisionOnDemandPostRequestBody
from msgraph.generated.models.synchronization_job_application_parameters import SynchronizationJobApplicationParameters
from msgraph.generated.models.synchronization_job_subject import SynchronizationJobSubject
from msgraph.generated.models.synchronization_linked_objects import SynchronizationLinkedObjects
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ProvisionOnDemandPostRequestBody(
	parameters = [
		SynchronizationJobApplicationParameters(
			rule_id = "33f7c90d-bf71-41b1-bda6-aaf0ddbee5d8#V2",
			subjects = [
				SynchronizationJobSubject(
					object_id = "8213fd99-d6b6-417b-8e13-af6334856215",
					object_type_name = "Group",
					links = SynchronizationLinkedObjects(
						members = [
							SynchronizationJobSubject(
								object_id = "cbc86211-6ada-4803-b73f-8039cf56d8a2",
								object_type_name = "User",
							),
							SynchronizationJobSubject(
								object_id = "2bc86211-6ada-4803-b73f-8039cf56d8a2",
								object_type_name = "User",
							),
						],
					),
				),
			],
		),
	],
)

result = await graph_client.service_principals.by_service_principal_id('servicePrincipal-id').synchronization.jobs.by_synchronization_job_id('synchronizationJob-id').provision_on_demand.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

> **Note:** The response object shown here might be shortened for readability.

```
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://syncfabric.windowsazure.com/api/$metadata#microsoft.synchronization.stringKeyStringValuePair",
    "key": "{\"result\":\"Success\",\"details\":{}}",
    "value": "{}"
}
```
