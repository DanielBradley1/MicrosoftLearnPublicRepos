<!-- Source: https://learn.microsoft.com/en-us/graph/api/configurationmanagement-post-configurationmonitors?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-04-15 -->

# Create configurationMonitor

Namespace: microsoft.graph

Create a new [configurationMonitor](https://learn.microsoft.com/en-us/graph/api/resources/configurationmonitor?view=graph-rest-1.0) object that runs periodically in the background at a scheduled frequency.

You can create up to 30 **configurationMonitor** objects per tenant. Each monitor runs at a fixed interval of 6 hours and cannot be configured to run at any other frequency. An administrator can monitor up to 800 configuration resources per day per tenant across all monitors.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | ConfigurationMonitoring.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | ConfigurationMonitoring.ReadWrite.All | Not available. |

## HTTP request

```http
POST /admin/configurationManagement/configurationMonitors
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [configurationMonitor](https://learn.microsoft.com/en-us/graph/api/resources/configurationmonitor?view=graph-rest-1.0) object.

You can specify the following properties when you create a **configurationMonitor**.

| Property | Type | Description |
| :--- | :--- | :--- |
| baseline | [configurationBaseline](https://learn.microsoft.com/en-us/graph/api/resources/configurationbaseline?view=graph-rest-1.0) | This relationship defines details of at least one resource and one property associated with the resource to be monitored. Required. |
| description | String | User-friendly description of the monitor given by the user. Optional. |
| displayName | String | User-friendly name given by the user to the monitor. Required. |
| parameters | [openComplexDictionaryType](https://learn.microsoft.com/en-us/graph/api/resources/opencomplexdictionarytype?view=graph-rest-1.0) | Key-value pairs that contain the values of parameters which might be used in the baseline. Optional. |

## Response

If successful, this method returns a `201 Created` response code and a [configurationMonitor](https://learn.microsoft.com/en-us/graph/api/resources/configurationmonitor?view=graph-rest-1.0) object in the response body.

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
POST https://graph.microsoft.com/v1.0/admin/configurationManagement/configurationMonitors
Content-Type: application/json

{
  "displayName": "Demo Monitor",
  "description": "This is a Demo Monitor",
  "baseline": {
    "displayName": "Demo Baseline",
    "description": "This is a baseline with resources SharedMailbox, AcceptedDomain and MailContact",
    "resources": [
      {
        "displayName": "TestSharedMailbox Resource",
        "resourceType": "microsoft.exchange.sharedmailbox",
        "properties": {
          "DisplayName": "TestSharedMailbox",
          "Alias": "testSharedMailbox",
          "Identity": "TestSharedMailbox",
          "Ensure": "Present",
          "PrimarySmtpAddress": "testSharedMailbox@contoso.onmicrosoft.com",
          "EmailAddresses": [
            "abc@contoso.onmicrosoft.com"
          ]
        }
      },
      {
        "displayName": "Accepted Domain",
        "resourceType": "microsoft.exchange.accepteddomain",
        "properties": {
          "Identity": "contoso.onmicrosoft.com",
          "DomainType": "InternalRelay",
          "Ensure": "Present"
        }
      },
      {
        "displayName": "Mail Contact Resource",
        "resourceType": "microsoft.exchange.mailcontact",
        "properties": {
          "Name": "Chris",
          "DisplayName": "Chris",
          "ExternalEmailAddress": "SMTP:chris@fabrikam.com",
          "Alias": "Chrisa",
          "Ensure": "Present"
        }
      }
    ]
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new ConfigurationMonitor
{
	DisplayName = "Demo Monitor",
	Description = "This is a Demo Monitor",
	Baseline = new ConfigurationBaseline
	{
		DisplayName = "Demo Baseline",
		Description = "This is a baseline with resources SharedMailbox, AcceptedDomain and MailContact",
		Resources = new List<BaselineResource>
		{
			new BaselineResource
			{
				DisplayName = "TestSharedMailbox Resource",
				ResourceType = "microsoft.exchange.sharedmailbox",
				Properties = new OpenComplexDictionaryType
				{
					AdditionalData = new Dictionary<string, object>
					{
						{
							"DisplayName" , "TestSharedMailbox"
						},
						{
							"Alias" , "testSharedMailbox"
						},
						{
							"Identity" , "TestSharedMailbox"
						},
						{
							"Ensure" , "Present"
						},
						{
							"PrimarySmtpAddress" , "testSharedMailbox@contoso.onmicrosoft.com"
						},
						{
							"EmailAddresses" , new List<string>
							{
								"abc@contoso.onmicrosoft.com",
							}
						},
					},
				},
			},
			new BaselineResource
			{
				DisplayName = "Accepted Domain",
				ResourceType = "microsoft.exchange.accepteddomain",
				Properties = new OpenComplexDictionaryType
				{
					AdditionalData = new Dictionary<string, object>
					{
						{
							"Identity" , "contoso.onmicrosoft.com"
						},
						{
							"DomainType" , "InternalRelay"
						},
						{
							"Ensure" , "Present"
						},
					},
				},
			},
			new BaselineResource
			{
				DisplayName = "Mail Contact Resource",
				ResourceType = "microsoft.exchange.mailcontact",
				Properties = new OpenComplexDictionaryType
				{
					AdditionalData = new Dictionary<string, object>
					{
						{
							"Name" , "Chris"
						},
						{
							"DisplayName" , "Chris"
						},
						{
							"ExternalEmailAddress" , "SMTP:chris@fabrikam.com"
						},
						{
							"Alias" , "Chrisa"
						},
						{
							"Ensure" , "Present"
						},
					},
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Admin.ConfigurationManagement.ConfigurationMonitors.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewConfigurationMonitor()
displayName := "Demo Monitor"
requestBody.SetDisplayName(&displayName) 
description := "This is a Demo Monitor"
requestBody.SetDescription(&description) 
baseline := graphmodels.NewConfigurationBaseline()
displayName := "Demo Baseline"
baseline.SetDisplayName(&displayName) 
description := "This is a baseline with resources SharedMailbox, AcceptedDomain and MailContact"
baseline.SetDescription(&description) 


baselineResource := graphmodels.NewBaselineResource()
displayName := "TestSharedMailbox Resource"
baselineResource.SetDisplayName(&displayName) 
resourceType := "microsoft.exchange.sharedmailbox"
baselineResource.SetResourceType(&resourceType) 
properties := graphmodels.NewOpenComplexDictionaryType()
additionalData := map[string]interface{}{
	"DisplayName" : "TestSharedMailbox", 
	"Alias" : "testSharedMailbox", 
	"Identity" : "TestSharedMailbox", 
	"Ensure" : "Present", 
	"PrimarySmtpAddress" : "testSharedMailbox@contoso.onmicrosoft.com", 
	emailAddresses := []string {
		"abc@contoso.onmicrosoft.com",
	}
}
properties.SetAdditionalData(additionalData)
baselineResource.SetProperties(properties)
baselineResource1 := graphmodels.NewBaselineResource()
displayName := "Accepted Domain"
baselineResource1.SetDisplayName(&displayName) 
resourceType := "microsoft.exchange.accepteddomain"
baselineResource1.SetResourceType(&resourceType) 
properties := graphmodels.NewOpenComplexDictionaryType()
additionalData := map[string]interface{}{
	"Identity" : "contoso.onmicrosoft.com", 
	"DomainType" : "InternalRelay", 
	"Ensure" : "Present", 
}
properties.SetAdditionalData(additionalData)
baselineResource1.SetProperties(properties)
baselineResource2 := graphmodels.NewBaselineResource()
displayName := "Mail Contact Resource"
baselineResource2.SetDisplayName(&displayName) 
resourceType := "microsoft.exchange.mailcontact"
baselineResource2.SetResourceType(&resourceType) 
properties := graphmodels.NewOpenComplexDictionaryType()
additionalData := map[string]interface{}{
	"Name" : "Chris", 
	"DisplayName" : "Chris", 
	"ExternalEmailAddress" : "SMTP:chris@fabrikam.com", 
	"Alias" : "Chrisa", 
	"Ensure" : "Present", 
}
properties.SetAdditionalData(additionalData)
baselineResource2.SetProperties(properties)

resources := []graphmodels.BaselineResourceable {
	baselineResource,
	baselineResource1,
	baselineResource2,
}
baseline.SetResources(resources)
requestBody.SetBaseline(baseline)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
configurationMonitors, err := graphClient.Admin().ConfigurationManagement().ConfigurationMonitors().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ConfigurationMonitor configurationMonitor = new ConfigurationMonitor();
configurationMonitor.setDisplayName("Demo Monitor");
configurationMonitor.setDescription("This is a Demo Monitor");
ConfigurationBaseline baseline = new ConfigurationBaseline();
baseline.setDisplayName("Demo Baseline");
baseline.setDescription("This is a baseline with resources SharedMailbox, AcceptedDomain and MailContact");
LinkedList<BaselineResource> resources = new LinkedList<BaselineResource>();
BaselineResource baselineResource = new BaselineResource();
baselineResource.setDisplayName("TestSharedMailbox Resource");
baselineResource.setResourceType("microsoft.exchange.sharedmailbox");
OpenComplexDictionaryType properties = new OpenComplexDictionaryType();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("DisplayName", "TestSharedMailbox");
additionalData.put("Alias", "testSharedMailbox");
additionalData.put("Identity", "TestSharedMailbox");
additionalData.put("Ensure", "Present");
additionalData.put("PrimarySmtpAddress", "testSharedMailbox@contoso.onmicrosoft.com");
LinkedList<String> emailAddresses = new LinkedList<String>();
emailAddresses.add("abc@contoso.onmicrosoft.com");
additionalData.put("EmailAddresses", emailAddresses);
properties.setAdditionalData(additionalData);
baselineResource.setProperties(properties);
resources.add(baselineResource);
BaselineResource baselineResource1 = new BaselineResource();
baselineResource1.setDisplayName("Accepted Domain");
baselineResource1.setResourceType("microsoft.exchange.accepteddomain");
OpenComplexDictionaryType properties1 = new OpenComplexDictionaryType();
HashMap<String, Object> additionalData1 = new HashMap<String, Object>();
additionalData1.put("Identity", "contoso.onmicrosoft.com");
additionalData1.put("DomainType", "InternalRelay");
additionalData1.put("Ensure", "Present");
properties1.setAdditionalData(additionalData1);
baselineResource1.setProperties(properties1);
resources.add(baselineResource1);
BaselineResource baselineResource2 = new BaselineResource();
baselineResource2.setDisplayName("Mail Contact Resource");
baselineResource2.setResourceType("microsoft.exchange.mailcontact");
OpenComplexDictionaryType properties2 = new OpenComplexDictionaryType();
HashMap<String, Object> additionalData2 = new HashMap<String, Object>();
additionalData2.put("Name", "Chris");
additionalData2.put("DisplayName", "Chris");
additionalData2.put("ExternalEmailAddress", "SMTP:chris@fabrikam.com");
additionalData2.put("Alias", "Chrisa");
additionalData2.put("Ensure", "Present");
properties2.setAdditionalData(additionalData2);
baselineResource2.setProperties(properties2);
resources.add(baselineResource2);
baseline.setResources(resources);
configurationMonitor.setBaseline(baseline);
ConfigurationMonitor result = graphClient.admin().configurationManagement().configurationMonitors().post(configurationMonitor);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const configurationMonitor = {
  displayName: 'Demo Monitor',
  description: 'This is a Demo Monitor',
  baseline: {
    displayName: 'Demo Baseline',
    description: 'This is a baseline with resources SharedMailbox, AcceptedDomain and MailContact',
    resources: [
      {
        displayName: 'TestSharedMailbox Resource',
        resourceType: 'microsoft.exchange.sharedmailbox',
        properties: {
          DisplayName: 'TestSharedMailbox',
          Alias: 'testSharedMailbox',
          Identity: 'TestSharedMailbox',
          Ensure: 'Present',
          PrimarySmtpAddress: 'testSharedMailbox@contoso.onmicrosoft.com',
          EmailAddresses: [
            'abc@contoso.onmicrosoft.com'
          ]
        }
      },
      {
        displayName: 'Accepted Domain',
        resourceType: 'microsoft.exchange.accepteddomain',
        properties: {
          Identity: 'contoso.onmicrosoft.com',
          DomainType: 'InternalRelay',
          Ensure: 'Present'
        }
      },
      {
        displayName: 'Mail Contact Resource',
        resourceType: 'microsoft.exchange.mailcontact',
        properties: {
          Name: 'Chris',
          DisplayName: 'Chris',
          ExternalEmailAddress: 'SMTP:chris@fabrikam.com',
          Alias: 'Chrisa',
          Ensure: 'Present'
        }
      }
    ]
  }
};

await client.api('/admin/configurationManagement/configurationMonitors')
	.post(configurationMonitor);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ConfigurationMonitor;
use Microsoft\Graph\Generated\Models\ConfigurationBaseline;
use Microsoft\Graph\Generated\Models\BaselineResource;
use Microsoft\Graph\Generated\Models\OpenComplexDictionaryType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ConfigurationMonitor();
$requestBody->setDisplayName('Demo Monitor');
$requestBody->setDescription('This is a Demo Monitor');
$baseline = new ConfigurationBaseline();
$baseline->setDisplayName('Demo Baseline');
$baseline->setDescription('This is a baseline with resources SharedMailbox, AcceptedDomain and MailContact');
$resourcesBaselineResource1 = new BaselineResource();
$resourcesBaselineResource1->setDisplayName('TestSharedMailbox Resource');
$resourcesBaselineResource1->setResourceType('microsoft.exchange.sharedmailbox');
$resourcesBaselineResource1Properties = new OpenComplexDictionaryType();
$additionalData = [
	'DisplayName' => 'TestSharedMailbox',
	'Alias' => 'testSharedMailbox',
	'Identity' => 'TestSharedMailbox',
	'Ensure' => 'Present',
	'PrimarySmtpAddress' => 'testSharedMailbox@contoso.onmicrosoft.com',
	'EmailAddresses' => [
'abc@contoso.onmicrosoft.com', ],
];
$resourcesBaselineResource1Properties->setAdditionalData($additionalData);
$resourcesBaselineResource1->setProperties($resourcesBaselineResource1Properties);
$resourcesArray []= $resourcesBaselineResource1;
$resourcesBaselineResource2 = new BaselineResource();
$resourcesBaselineResource2->setDisplayName('Accepted Domain');
$resourcesBaselineResource2->setResourceType('microsoft.exchange.accepteddomain');
$resourcesBaselineResource2Properties = new OpenComplexDictionaryType();
$additionalData = [
	'Identity' => 'contoso.onmicrosoft.com',
	'DomainType' => 'InternalRelay',
	'Ensure' => 'Present',
];
$resourcesBaselineResource2Properties->setAdditionalData($additionalData);
$resourcesBaselineResource2->setProperties($resourcesBaselineResource2Properties);
$resourcesArray []= $resourcesBaselineResource2;
$resourcesBaselineResource3 = new BaselineResource();
$resourcesBaselineResource3->setDisplayName('Mail Contact Resource');
$resourcesBaselineResource3->setResourceType('microsoft.exchange.mailcontact');
$resourcesBaselineResource3Properties = new OpenComplexDictionaryType();
$additionalData = [
	'Name' => 'Chris',
	'DisplayName' => 'Chris',
	'ExternalEmailAddress' => 'SMTP:chris@fabrikam.com',
	'Alias' => 'Chrisa',
	'Ensure' => 'Present',
];
$resourcesBaselineResource3Properties->setAdditionalData($additionalData);
$resourcesBaselineResource3->setProperties($resourcesBaselineResource3Properties);
$resourcesArray []= $resourcesBaselineResource3;
$baseline->setResources($resourcesArray);

$requestBody->setBaseline($baseline);

$result = $graphServiceClient->admin()->configurationManagement()->configurationMonitors()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.ConfigurationManagement

$params = @{
	displayName = "Demo Monitor"
	description = "This is a Demo Monitor"
	baseline = @{
		displayName = "Demo Baseline"
		description = "This is a baseline with resources SharedMailbox, AcceptedDomain and MailContact"
		resources = @(
			@{
				displayName = "TestSharedMailbox Resource"
				resourceType = "microsoft.exchange.sharedmailbox"
				properties = @{
					DisplayName = "TestSharedMailbox"
					Alias = "testSharedMailbox"
					Identity = "TestSharedMailbox"
					Ensure = "Present"
					PrimarySmtpAddress = "testSharedMailbox@contoso.onmicrosoft.com"
					EmailAddresses = @(
					"abc@contoso.onmicrosoft.com"
				)
			}
		}
		@{
			displayName = "Accepted Domain"
			resourceType = "microsoft.exchange.accepteddomain"
			properties = @{
				Identity = "contoso.onmicrosoft.com"
				DomainType = "InternalRelay"
				Ensure = "Present"
			}
		}
		@{
			displayName = "Mail Contact Resource"
			resourceType = "microsoft.exchange.mailcontact"
			properties = @{
				Name = "Chris"
				DisplayName = "Chris"
				ExternalEmailAddress = "SMTP:chris@fabrikam.com"
				Alias = "Chrisa"
				Ensure = "Present"
			}
		}
	)
}
}

New-MgAdminConfigurationManagementConfigurationMonitor -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.configuration_monitor import ConfigurationMonitor
from msgraph.generated.models.configuration_baseline import ConfigurationBaseline
from msgraph.generated.models.baseline_resource import BaselineResource
from msgraph.generated.models.open_complex_dictionary_type import OpenComplexDictionaryType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ConfigurationMonitor(
	display_name = "Demo Monitor",
	description = "This is a Demo Monitor",
	baseline = ConfigurationBaseline(
		display_name = "Demo Baseline",
		description = "This is a baseline with resources SharedMailbox, AcceptedDomain and MailContact",
		resources = [
			BaselineResource(
				display_name = "TestSharedMailbox Resource",
				resource_type = "microsoft.exchange.sharedmailbox",
				properties = OpenComplexDictionaryType(
					additional_data = {
							"display_name" : "TestSharedMailbox",
							"alias" : "testSharedMailbox",
							"identity" : "TestSharedMailbox",
							"ensure" : "Present",
							"primary_smtp_address" : "testSharedMailbox@contoso.onmicrosoft.com",
							"email_addresses" : [
								"abc@contoso.onmicrosoft.com",
							],
					}
				),
			),
			BaselineResource(
				display_name = "Accepted Domain",
				resource_type = "microsoft.exchange.accepteddomain",
				properties = OpenComplexDictionaryType(
					additional_data = {
							"identity" : "contoso.onmicrosoft.com",
							"domain_type" : "InternalRelay",
							"ensure" : "Present",
					}
				),
			),
			BaselineResource(
				display_name = "Mail Contact Resource",
				resource_type = "microsoft.exchange.mailcontact",
				properties = OpenComplexDictionaryType(
					additional_data = {
							"name" : "Chris",
							"display_name" : "Chris",
							"external_email_address" : "SMTP:chris@fabrikam.com",
							"alias" : "Chrisa",
							"ensure" : "Present",
					}
				),
			),
		],
	),
)

result = await graph_client.admin.configuration_management.configuration_monitors.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#admin/configurationManagement/configurationMonitors/$entity",
  "id": "f1b46220-74af-4347-9ac7-89fe17d57bd7",
  "displayName": "Monitor for EXO100",
  "description": "This is a Monitor with EXO resources",
  "tenantId": "909d5e4a-3d8e-47cf-979a-821619ebaf39",
  "status": "active",
  "monitorRunFrequencyInHours": 6,
  "mode": "monitorOnly",
  "createdDateTime": "2025-03-24T09:00:44.0028541Z",
  "lastModifiedDateTime": "2025-03-24T09:00:44.0398641Z",
  "createdBy": {
    "user": {
      "id": "ad14b3c8-e4db-4896-a963-3f420272d085",
      "displayName": "MOD Administrator"
    },
    "application": {
      "id": null,
      "displayName": null
    }
  },
  "parameters": {}
}
```
