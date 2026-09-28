<!-- Source: https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecyclemanagementsettings-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Update lifecycleManagementSettings

Namespace: microsoft.graph.identityGovernance

Update the properties of a [lifecycleManagementSettings](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclemanagementsettings?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | LifecycleWorkflows.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | LifecycleWorkflows.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Lifecycle Workflows Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
PATCH /identityGovernance/lifecycleWorkflows/settings
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
| workflowScheduleIntervalInHours | Int32 | The workflow schedule interval. Required. |
| emailSettings | [microsoft.graph.emailSettings](https://learn.microsoft.com/en-us/graph/api/resources/emailsettings?view=graph-rest-1.0) | The settings for emails sent from email-specific tasks within a workflow. Required. |

## Response

If successful, this action returns a `204 No Content` response code.

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

```http
PATCH https://graph.microsoft.com/v1.0/identityGovernance/lifecycleWorkflows/settings
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/lifecycleWorkflows/settings/$entity",
    "workflowScheduleIntervalInHours": 3,
    "emailSettings": {
        "senderDomain": "ContosoIndustries.net",
        "useCompanyBranding": true
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models.IdentityGovernance;
using Microsoft.Graph.Models;

var requestBody = new LifecycleManagementSettings
{
	WorkflowScheduleIntervalInHours = 3,
	EmailSettings = new EmailSettings
	{
		SenderDomain = "ContosoIndustries.net",
		UseCompanyBranding = true,
	},
	AdditionalData = new Dictionary<string, object>
	{
		{
			"@odata.context" , "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/lifecycleWorkflows/settings/$entity"
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.LifecycleWorkflows.Settings.PatchAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodelsidentitygovernance "github.com/microsoftgraph/msgraph-sdk-go/models/identitygovernance"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodelsidentitygovernance.NewLifecycleManagementSettings()
workflowScheduleIntervalInHours := int32(3)
requestBody.SetWorkflowScheduleIntervalInHours(&workflowScheduleIntervalInHours) 
emailSettings := graphmodels.NewEmailSettings()
senderDomain := "ContosoIndustries.net"
emailSettings.SetSenderDomain(&senderDomain) 
useCompanyBranding := true
emailSettings.SetUseCompanyBranding(&useCompanyBranding) 
requestBody.SetEmailSettings(emailSettings)
additionalData := map[string]interface{}{
	"@odata.context" : "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/lifecycleWorkflows/settings/$entity", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
settings, err := graphClient.IdentityGovernance().LifecycleWorkflows().Settings().Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.identitygovernance.LifecycleManagementSettings lifecycleManagementSettings = new com.microsoft.graph.models.identitygovernance.LifecycleManagementSettings();
lifecycleManagementSettings.setWorkflowScheduleIntervalInHours(3);
EmailSettings emailSettings = new EmailSettings();
emailSettings.setSenderDomain("ContosoIndustries.net");
emailSettings.setUseCompanyBranding(true);
lifecycleManagementSettings.setEmailSettings(emailSettings);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("@odata.context", "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/lifecycleWorkflows/settings/$entity");
lifecycleManagementSettings.setAdditionalData(additionalData);
com.microsoft.graph.models.identitygovernance.LifecycleManagementSettings result = graphClient.identityGovernance().lifecycleWorkflows().settings().patch(lifecycleManagementSettings);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const lifecycleManagementSettings = {
    '@odata.context': 'https://graph.microsoft.com/v1.0/$metadata#identityGovernance/lifecycleWorkflows/settings/$entity',
    workflowScheduleIntervalInHours: 3,
    emailSettings: {
        senderDomain: 'ContosoIndustries.net',
        useCompanyBranding: true
  }
};

await client.api('/identityGovernance/lifecycleWorkflows/settings')
	.update(lifecycleManagementSettings);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\IdentityGovernance\LifecycleManagementSettings;
use Microsoft\Graph\Generated\Models\EmailSettings;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new LifecycleManagementSettings();
$requestBody->setWorkflowScheduleIntervalInHours(3);
$emailSettings = new EmailSettings();
$emailSettings->setSenderDomain('ContosoIndustries.net');
$emailSettings->setUseCompanyBranding(true);
$requestBody->setEmailSettings($emailSettings);
$additionalData = [
	'@odata.context' => 'https://graph.microsoft.com/v1.0/$metadata#identityGovernance/lifecycleWorkflows/settings/$entity',
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->identityGovernance()->lifecycleWorkflows()->settings()->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	"@odata.context" = "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/lifecycleWorkflows/settings/$entity"
	workflowScheduleIntervalInHours = 3
	emailSettings = @{
		senderDomain = "ContosoIndustries.net"
		useCompanyBranding = $true
	}
}

Update-MgIdentityGovernanceLifecycleWorkflowSetting -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.identity_governance.lifecycle_management_settings import LifecycleManagementSettings
from msgraph.generated.models.email_settings import EmailSettings
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = LifecycleManagementSettings(
	workflow_schedule_interval_in_hours = 3,
	email_settings = EmailSettings(
		sender_domain = "ContosoIndustries.net",
		use_company_branding = True,
	),
	additional_data = {
			"@odata_context" : "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/lifecycleWorkflows/settings/$entity",
	}
)

result = await graph_client.identity_governance.lifecycle_workflows.settings.patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

```http
HTTP/1.1 204 No Content
```
