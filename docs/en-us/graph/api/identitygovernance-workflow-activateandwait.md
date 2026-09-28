<!-- Source: https://learn.microsoft.com/en-us/graph/api/identitygovernance-workflow-activateandwait?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-05 -->

# workflow: activateAndWait

Namespace: microsoft.graph.identityGovernance

Activate a [lifecycle workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) for a specified subject and synchronously wait for execution to complete. This action returns an [awaitedWorkflowProcessingResult](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-awaitedworkflowprocessingresult?view=graph-rest-1.0) with the execution outcome. Use this action when you need immediate confirmation of workflow completion, for example when provisioning a non-user subject.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | LifecycleWorkflows-Workflow.Activate | LifecycleWorkflows-Workflow.ReadWrite.All, LifecycleWorkflows.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | LifecycleWorkflows-Workflow.Activate | LifecycleWorkflows-Workflow.ReadWrite.All, LifecycleWorkflows.ReadWrite.All |

## HTTP request

```http
POST /identityGovernance/lifecycleWorkflows/workflows/{workflowId}/activateAndWait
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table lists the parameters that are required when you call this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| subject | [microsoft.graph.identityGovernance.workflowSubject](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowsubject?view=graph-rest-1.0) | The subject for which to activate the workflow. Must include the `@odata.type` property to specify the derived type \(for example, `#microsoft.graph.identityGovernance.provisioningObjectWorkflowSubject`\). Required. |

## Response

If successful, this action returns a `200 OK` response code and an [awaitedWorkflowProcessingResult](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-awaitedworkflowprocessingresult?view=graph-rest-1.0) in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/identityGovernance/lifecycleWorkflows/workflows/14879a93-6b91-4153-b7e6-5df4a7b7c5c8/activateAndWait
Content-Type: application/json

{
  "subject": {
    "@odata.type": "#microsoft.graph.identityGovernance.provisioningObjectWorkflowSubject",
    "id": "b74f0fae-b1f3-4c96-9bf0-d4d8a8e37cbe",
    "attributeSetEntries": [
      {
        "name": "department",
        "value": "Engineering"
      },
      {
        "name": "jobTitle",
        "value": "Software Engineer"
      }
    ]
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.IdentityGovernance.LifecycleWorkflows.Workflows.Item.MicrosoftGraphIdentityGovernanceActivateAndWait;
using Microsoft.Graph.Models.IdentityGovernance;

var requestBody = new ActivateAndWaitPostRequestBody
{
	Subject = new ProvisioningObjectWorkflowSubject
	{
		OdataType = "#microsoft.graph.identityGovernance.provisioningObjectWorkflowSubject",
		Id = "b74f0fae-b1f3-4c96-9bf0-d4d8a8e37cbe",
		AttributeSetEntries = new List<AttributeSetEntry>
		{
			new AttributeSetEntry
			{
				Name = "department",
				Value = "Engineering",
			},
			new AttributeSetEntry
			{
				Name = "jobTitle",
				Value = "Software Engineer",
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.LifecycleWorkflows.Workflows["{workflow-id}"].MicrosoftGraphIdentityGovernanceActivateAndWait.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphidentitygovernance "github.com/microsoftgraph/msgraph-sdk-go/identitygovernance"
	  graphmodelsidentitygovernance "github.com/microsoftgraph/msgraph-sdk-go/models/identitygovernance"
	  //other-imports
)

requestBody := graphidentitygovernance.NewActivateAndWaitPostRequestBody()
subject := graphmodelsidentitygovernance.NewProvisioningObjectWorkflowSubject()
id := "b74f0fae-b1f3-4c96-9bf0-d4d8a8e37cbe"
subject.SetId(&id) 


attributeSetEntry := graphmodelsidentitygovernance.NewAttributeSetEntry()
name := "department"
attributeSetEntry.SetName(&name) 
value := "Engineering"
attributeSetEntry.SetValue(&value) 
attributeSetEntry1 := graphmodelsidentitygovernance.NewAttributeSetEntry()
name := "jobTitle"
attributeSetEntry1.SetName(&name) 
value := "Software Engineer"
attributeSetEntry1.SetValue(&value) 

attributeSetEntries := []graphmodelsidentitygovernance.AttributeSetEntryable {
	attributeSetEntry,
	attributeSetEntry1,
}
subject.SetAttributeSetEntries(attributeSetEntries)
requestBody.SetSubject(subject)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
microsoftGraphIdentityGovernanceActivateAndWait, err := graphClient.IdentityGovernance().LifecycleWorkflows().Workflows().ByWorkflowId("workflow-id").MicrosoftGraphIdentityGovernanceActivateAndWait().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.identitygovernance.lifecycleworkflows.workflows.item.microsoftgraphidentitygovernanceactivateandwait.ActivateAndWaitPostRequestBody activateAndWaitPostRequestBody = new com.microsoft.graph.identitygovernance.lifecycleworkflows.workflows.item.microsoftgraphidentitygovernanceactivateandwait.ActivateAndWaitPostRequestBody();
com.microsoft.graph.models.identitygovernance.ProvisioningObjectWorkflowSubject subject = new com.microsoft.graph.models.identitygovernance.ProvisioningObjectWorkflowSubject();
subject.setOdataType("#microsoft.graph.identityGovernance.provisioningObjectWorkflowSubject");
subject.setId("b74f0fae-b1f3-4c96-9bf0-d4d8a8e37cbe");
LinkedList<com.microsoft.graph.models.identitygovernance.AttributeSetEntry> attributeSetEntries = new LinkedList<com.microsoft.graph.models.identitygovernance.AttributeSetEntry>();
com.microsoft.graph.models.identitygovernance.AttributeSetEntry attributeSetEntry = new com.microsoft.graph.models.identitygovernance.AttributeSetEntry();
attributeSetEntry.setName("department");
attributeSetEntry.setValue("Engineering");
attributeSetEntries.add(attributeSetEntry);
com.microsoft.graph.models.identitygovernance.AttributeSetEntry attributeSetEntry1 = new com.microsoft.graph.models.identitygovernance.AttributeSetEntry();
attributeSetEntry1.setName("jobTitle");
attributeSetEntry1.setValue("Software Engineer");
attributeSetEntries.add(attributeSetEntry1);
subject.setAttributeSetEntries(attributeSetEntries);
activateAndWaitPostRequestBody.setSubject(subject);
var result = graphClient.identityGovernance().lifecycleWorkflows().workflows().byWorkflowId("{workflow-id}").microsoftGraphIdentityGovernanceActivateAndWait().post(activateAndWaitPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const awaitedWorkflowProcessingResult = {
  subject: {
    '@odata.type': '#microsoft.graph.identityGovernance.provisioningObjectWorkflowSubject',
    id: 'b74f0fae-b1f3-4c96-9bf0-d4d8a8e37cbe',
    attributeSetEntries: [
      {
        name: 'department',
        value: 'Engineering'
      },
      {
        name: 'jobTitle',
        value: 'Software Engineer'
      }
    ]
  }
};

await client.api('/identityGovernance/lifecycleWorkflows/workflows/14879a93-6b91-4153-b7e6-5df4a7b7c5c8/activateAndWait')
	.post(awaitedWorkflowProcessingResult);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\IdentityGovernance\LifecycleWorkflows\Workflows\Item\MicrosoftGraphIdentityGovernanceActivateAndWait\ActivateAndWaitPostRequestBody;
use Microsoft\Graph\Generated\Models\IdentityGovernance\ProvisioningObjectWorkflowSubject;
use Microsoft\Graph\Generated\Models\IdentityGovernance\AttributeSetEntry;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ActivateAndWaitPostRequestBody();
$subject = new ProvisioningObjectWorkflowSubject();
$subject->setOdataType('#microsoft.graph.identityGovernance.provisioningObjectWorkflowSubject');
$subject->setId('b74f0fae-b1f3-4c96-9bf0-d4d8a8e37cbe');
$attributeSetEntriesAttributeSetEntry1 = new AttributeSetEntry();
$attributeSetEntriesAttributeSetEntry1->setName('department');
$attributeSetEntriesAttributeSetEntry1->setValue('Engineering');
$attributeSetEntriesArray []= $attributeSetEntriesAttributeSetEntry1;
$attributeSetEntriesAttributeSetEntry2 = new AttributeSetEntry();
$attributeSetEntriesAttributeSetEntry2->setName('jobTitle');
$attributeSetEntriesAttributeSetEntry2->setValue('Software Engineer');
$attributeSetEntriesArray []= $attributeSetEntriesAttributeSetEntry2;
$subject->setAttributeSetEntries($attributeSetEntriesArray);

$requestBody->setSubject($subject);

$result = $graphServiceClient->identityGovernance()->lifecycleWorkflows()->workflows()->byWorkflowId('workflow-id')->microsoftGraphIdentityGovernanceActivateAndWait()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.identitygovernance.lifecycleworkflows.workflows.item.microsoft_graph_identity_governance_activate_and_wait.activate_and_wait_post_request_body import ActivateAndWaitPostRequestBody
from msgraph.generated.models.identity_governance.provisioning_object_workflow_subject import ProvisioningObjectWorkflowSubject
from msgraph.generated.models.identity_governance.attribute_set_entry import AttributeSetEntry
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ActivateAndWaitPostRequestBody(
	subject = ProvisioningObjectWorkflowSubject(
		odata_type = "#microsoft.graph.identityGovernance.provisioningObjectWorkflowSubject",
		id = "b74f0fae-b1f3-4c96-9bf0-d4d8a8e37cbe",
		attribute_set_entries = [
			AttributeSetEntry(
				name = "department",
				value = "Engineering",
			),
			AttributeSetEntry(
				name = "jobTitle",
				value = "Software Engineer",
			),
		],
	),
)

result = await graph_client.identity_governance.lifecycle_workflows.workflows.by_workflow_id('workflow-id').microsoft_graph_identity_governance_activate_and_wait.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

Note

The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#microsoft.graph.identityGovernance.awaitedWorkflowProcessingResult",
  "processingStatus": "completed",
  "statusReasons": [],
  "subject": {
    "@odata.type": "#microsoft.graph.identityGovernance.provisioningObjectWorkflowSubject",
    "id": "b74f0fae-b1f3-4c96-9bf0-d4d8a8e37cbe",
    "attributeSetEntries": [
      {
        "name": "department",
        "value": "Engineering"
      },
      {
        "name": "jobTitle",
        "value": "Software Engineer"
      }
    ]
  }
}
```
