<!-- Source: https://learn.microsoft.com/en-us/graph/api/simulation-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Update simulation

Namespace: microsoft.graph

Update an [attack simulation campaign](https://learn.microsoft.com/en-us/graph/api/resources/simulation?view=graph-rest-1.0) for a tenant. You can only update simulations that are in `draft` status.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AttackSimulation.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | AttackSimulation.ReadWrite.All | Not available. |

## HTTP request

```http
PATCH /security/attackSimulation/simulations/{simulationId}
```

## Request headers

| Header | Value |
| --- | --- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| attackTechnique | [simulationAttackTechnique](https://learn.microsoft.com/en-us/graph/api/resources/simulation?view=graph-rest-1.0#simulationattacktechnique-values) | The social engineering technique used in the attack simulation and training campaign. Supports `$filter` and `$orderby`. The possible values are: `unknown`, `credentialHarvesting`, `attachmentMalware`, `driveByUrl`, `linkInAttachment`, `linkToMalwareFile`, `unknownFutureValue`, `oAuthConsentGrant`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `oAuthConsentGrant`. For more information about the types of social engineering attack techniques, see [simulations](https://learn.microsoft.com/en-us/microsoft-365/security/office-365-security/attack-simulation-training-get-started?view=o365-worldwide&preserve-view=true#simulations). |
| attackType | [simulationAttackType](https://learn.microsoft.com/en-us/graph/api/resources/simulation?view=graph-rest-1.0#simulationattacktype-values) | Attack type of the attack simulation and training campaign. The possible values are: `unknown`, `social`, `cloud`, `endpoint`, `unknownFutureValue`. |
| displayName | String | Display name of the attack simulation and training campaign. Supports `$filter` and `$orderby`. |
| durationInDays | Int32 | Simulation duration in days. |
| excludedAccountTarget | [accountTargetContent](https://learn.microsoft.com/en-us/graph/api/resources/accounttargetcontent?view=graph-rest-1.0) | Users excluded from the simulation. |
| includedAccountTarget | [accountTargetContent](https://learn.microsoft.com/en-us/graph/api/resources/accounttargetcontent?view=graph-rest-1.0) | Users targeted in the simulation. |
| payload | [payload](https://learn.microsoft.com/en-us/graph/api/resources/payload?view=graph-rest-1.0) | Payload associated with the simulation. Required. |
| status | [simulationStatus](https://learn.microsoft.com/en-us/graph/api/resources/simulation?view=graph-rest-1.0#simulationstatus-values) | Status of the attack simulation and training campaign. The possible values are: `unknown`, `draft`, `running`, `scheduled`, `succeeded`, `failed`, `cancelled`, `excluded`, `unknownFutureValue`. |

## Response

This method returns a `202 Accepted` response code and a tracking header named `location` in the response that you should poll to determine the outcome of the operation.

## Examples

### Example 1: Update an attack simulation campaign

The following example shows how to update an attack simulation campaign for a tenant.

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
PATCH https://graph.microsoft.com/v1.0/security/attackSimulation/simulations/2f5548d1-0dd8-4cc8-9de0-e0d6ec7ea3dc
Content-type: application/json

{
  "@odata.etag": "\"0100aa9b-0000-0100-0000-6396fa270000\"",
  "displayName": "Graph Simulation",
  "payload@odata.bind":"https://graph.microsoft.com/v1.0/security/attacksimulation/payloads/12345678-9abc-def0-123456789a",
  "durationInDays": 7,
  "attackTechnique": "credentialHarvesting",
  "attackType": "social",
  "status": "scheduled",
  "includedAccountTarget": {
    "@odata.type": "#microsoft.graph.addressBookAccountTargetContent",
    "type" : "addressBook",
    "accountTargetEmails" : [
        "faiza@contoso.com"
    ]
  },
  "excludedAccountTarget": {
    "@odata.type": "#microsoft.graph.addressBookAccountTargetContent",
    "type" : "addressBook",
    "accountTargetEmails" : [
        "sam@contoso.com"
    ]
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Simulation
{
	DisplayName = "Graph Simulation",
	DurationInDays = 7,
	AttackTechnique = SimulationAttackTechnique.CredentialHarvesting,
	AttackType = SimulationAttackType.Social,
	Status = SimulationStatus.Scheduled,
	IncludedAccountTarget = new AddressBookAccountTargetContent
	{
		OdataType = "#microsoft.graph.addressBookAccountTargetContent",
		Type = AccountTargetContentType.AddressBook,
		AccountTargetEmails = new List<string>
		{
			"faiza@contoso.com",
		},
	},
	ExcludedAccountTarget = new AddressBookAccountTargetContent
	{
		OdataType = "#microsoft.graph.addressBookAccountTargetContent",
		Type = AccountTargetContentType.AddressBook,
		AccountTargetEmails = new List<string>
		{
			"sam@contoso.com",
		},
	},
	AdditionalData = new Dictionary<string, object>
	{
		{
			"@odata.etag" , "\"0100aa9b-0000-0100-0000-6396fa270000\""
		},
		{
			"payload@odata.bind" , "https://graph.microsoft.com/v1.0/security/attacksimulation/payloads/12345678-9abc-def0-123456789a"
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.AttackSimulation.Simulations["{simulation-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewSimulation()
displayName := "Graph Simulation"
requestBody.SetDisplayName(&displayName) 
durationInDays := int32(7)
requestBody.SetDurationInDays(&durationInDays) 
attackTechnique := graphmodels.CREDENTIALHARVESTING_SIMULATIONATTACKTECHNIQUE 
requestBody.SetAttackTechnique(&attackTechnique) 
attackType := graphmodels.SOCIAL_SIMULATIONATTACKTYPE 
requestBody.SetAttackType(&attackType) 
status := graphmodels.SCHEDULED_SIMULATIONSTATUS 
requestBody.SetStatus(&status) 
includedAccountTarget := graphmodels.NewAddressBookAccountTargetContent()
type := graphmodels.ADDRESSBOOK_ACCOUNTTARGETCONTENTTYPE 
includedAccountTarget.SetType(&type) 
accountTargetEmails := []string {
	"faiza@contoso.com",
}
includedAccountTarget.SetAccountTargetEmails(accountTargetEmails)
requestBody.SetIncludedAccountTarget(includedAccountTarget)
excludedAccountTarget := graphmodels.NewAddressBookAccountTargetContent()
type := graphmodels.ADDRESSBOOK_ACCOUNTTARGETCONTENTTYPE 
excludedAccountTarget.SetType(&type) 
accountTargetEmails := []string {
	"sam@contoso.com",
}
excludedAccountTarget.SetAccountTargetEmails(accountTargetEmails)
requestBody.SetExcludedAccountTarget(excludedAccountTarget)
additionalData := map[string]interface{}{
	"@odata.etag" : "\"0100aa9b-0000-0100-0000-6396fa270000\"", 
	"payload@odata.bind" : "https://graph.microsoft.com/v1.0/security/attacksimulation/payloads/12345678-9abc-def0-123456789a", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
simulations, err := graphClient.Security().AttackSimulation().Simulations().BySimulationId("simulation-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Simulation simulation = new Simulation();
simulation.setDisplayName("Graph Simulation");
simulation.setDurationInDays(7);
simulation.setAttackTechnique(SimulationAttackTechnique.CredentialHarvesting);
simulation.setAttackType(SimulationAttackType.Social);
simulation.setStatus(SimulationStatus.Scheduled);
AddressBookAccountTargetContent includedAccountTarget = new AddressBookAccountTargetContent();
includedAccountTarget.setOdataType("#microsoft.graph.addressBookAccountTargetContent");
includedAccountTarget.setType(AccountTargetContentType.AddressBook);
LinkedList<String> accountTargetEmails = new LinkedList<String>();
accountTargetEmails.add("faiza@contoso.com");
includedAccountTarget.setAccountTargetEmails(accountTargetEmails);
simulation.setIncludedAccountTarget(includedAccountTarget);
AddressBookAccountTargetContent excludedAccountTarget = new AddressBookAccountTargetContent();
excludedAccountTarget.setOdataType("#microsoft.graph.addressBookAccountTargetContent");
excludedAccountTarget.setType(AccountTargetContentType.AddressBook);
LinkedList<String> accountTargetEmails1 = new LinkedList<String>();
accountTargetEmails1.add("sam@contoso.com");
excludedAccountTarget.setAccountTargetEmails(accountTargetEmails1);
simulation.setExcludedAccountTarget(excludedAccountTarget);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("@odata.etag", "\"0100aa9b-0000-0100-0000-6396fa270000\"");
additionalData.put("payload@odata.bind", "https://graph.microsoft.com/v1.0/security/attacksimulation/payloads/12345678-9abc-def0-123456789a");
simulation.setAdditionalData(additionalData);
Simulation result = graphClient.security().attackSimulation().simulations().bySimulationId("{simulation-id}").patch(simulation);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const simulation = {
  '@odata.etag': '\"0100aa9b-0000-0100-0000-6396fa270000\"',
  displayName: 'Graph Simulation',
  'payload@odata.bind':'https://graph.microsoft.com/v1.0/security/attacksimulation/payloads/12345678-9abc-def0-123456789a',
  durationInDays: 7,
  attackTechnique: 'credentialHarvesting',
  attackType: 'social',
  status: 'scheduled',
  includedAccountTarget: {
    '@odata.type': '#microsoft.graph.addressBookAccountTargetContent',
    type: 'addressBook',
    accountTargetEmails: [
        'faiza@contoso.com'
    ]
  },
  excludedAccountTarget: {
    '@odata.type': '#microsoft.graph.addressBookAccountTargetContent',
    type: 'addressBook',
    accountTargetEmails: [
        'sam@contoso.com'
    ]
  }
};

await client.api('/security/attackSimulation/simulations/2f5548d1-0dd8-4cc8-9de0-e0d6ec7ea3dc')
	.update(simulation);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Simulation;
use Microsoft\Graph\Generated\Models\SimulationAttackTechnique;
use Microsoft\Graph\Generated\Models\SimulationAttackType;
use Microsoft\Graph\Generated\Models\SimulationStatus;
use Microsoft\Graph\Generated\Models\AddressBookAccountTargetContent;
use Microsoft\Graph\Generated\Models\AccountTargetContentType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Simulation();
$requestBody->setDisplayName('Graph Simulation');
$requestBody->setDurationInDays(7);
$requestBody->setAttackTechnique(new SimulationAttackTechnique('credentialHarvesting'));
$requestBody->setAttackType(new SimulationAttackType('social'));
$requestBody->setStatus(new SimulationStatus('scheduled'));
$includedAccountTarget = new AddressBookAccountTargetContent();
$includedAccountTarget->setOdataType('#microsoft.graph.addressBookAccountTargetContent');
$includedAccountTarget->setType(new AccountTargetContentType('addressBook'));
$includedAccountTarget->setAccountTargetEmails(['faiza@contoso.com', 	]);
$requestBody->setIncludedAccountTarget($includedAccountTarget);
$excludedAccountTarget = new AddressBookAccountTargetContent();
$excludedAccountTarget->setOdataType('#microsoft.graph.addressBookAccountTargetContent');
$excludedAccountTarget->setType(new AccountTargetContentType('addressBook'));
$excludedAccountTarget->setAccountTargetEmails(['sam@contoso.com', 	]);
$requestBody->setExcludedAccountTarget($excludedAccountTarget);
$additionalData = [
	'@odata.etag' => '\"0100aa9b-0000-0100-0000-6396fa270000\"',
	'payload@odata.bind' => 'https://graph.microsoft.com/v1.0/security/attacksimulation/payloads/12345678-9abc-def0-123456789a',
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->security()->attackSimulation()->simulations()->bySimulationId('simulation-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.simulation import Simulation
from msgraph.generated.models.simulation_attack_technique import SimulationAttackTechnique
from msgraph.generated.models.simulation_attack_type import SimulationAttackType
from msgraph.generated.models.simulation_status import SimulationStatus
from msgraph.generated.models.address_book_account_target_content import AddressBookAccountTargetContent
from msgraph.generated.models.account_target_content_type import AccountTargetContentType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Simulation(
	display_name = "Graph Simulation",
	duration_in_days = 7,
	attack_technique = SimulationAttackTechnique.CredentialHarvesting,
	attack_type = SimulationAttackType.Social,
	status = SimulationStatus.Scheduled,
	included_account_target = AddressBookAccountTargetContent(
		odata_type = "#microsoft.graph.addressBookAccountTargetContent",
		type = AccountTargetContentType.AddressBook,
		account_target_emails = [
			"faiza@contoso.com",
		],
	),
	excluded_account_target = AddressBookAccountTargetContent(
		odata_type = "#microsoft.graph.addressBookAccountTargetContent",
		type = AccountTargetContentType.AddressBook,
		account_target_emails = [
			"sam@contoso.com",
		],
	),
	additional_data = {
			"@odata_etag" : "\"0100aa9b-0000-0100-0000-6396fa270000\"",
			"payload@odata_bind" : "https://graph.microsoft.com/v1.0/security/attacksimulation/payloads/12345678-9abc-def0-123456789a",
	}
)

result = await graph_client.security.attack_simulation.simulations.by_simulation_id('simulation-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 202 Accepted
```

### Example 2: Update an attack simulation campaign from draft to scheduled

The following example shows how to schedule an attack simulation campaign. The simulation request is validated when scheduling a simulation. All the required parameters need to be propagated in such request.

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
PATCH https://graph.microsoft.com/v1.0/security/attackSimulation/simulations/2f5548d1-0dd8-4cc8-9de0-e0d6ec7ea3dc
Content-type: application/json

{
  "@odata.etag": "\"0100aa9b-0000-0100-0000-6396fa270000\"",
  "id": "2f5548d1-0dd8-4cc8-9de0-e0d6ec7ea3dc",
  "displayName": "Graph Simulation",
  "payload@odata.bind":"https://graph.microsoft.com/v1.0/security/attacksimulation/payloads/12345678-9abc-def0-123456789a",
  "durationInDays": 7,
  "attackTechnique": "credentialHarvesting",
  "attackType": "social",
  "status": "scheduled",
  "includedAccountTarget": {
    "@odata.type": "#microsoft.graph.addressBookAccountTargetContent",
    "type" : "addressBook",
    "accountTargetEmails" : [
        "faiza@contoso.com"
    ]
  },
  "excludedAccountTarget": {
    "@odata.type": "#microsoft.graph.addressBookAccountTargetContent",
    "type" : "addressBook",
    "accountTargetEmails" : [
        "sam@contoso.com"
    ]
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Simulation
{
	Id = "2f5548d1-0dd8-4cc8-9de0-e0d6ec7ea3dc",
	DisplayName = "Graph Simulation",
	DurationInDays = 7,
	AttackTechnique = SimulationAttackTechnique.CredentialHarvesting,
	AttackType = SimulationAttackType.Social,
	Status = SimulationStatus.Scheduled,
	IncludedAccountTarget = new AddressBookAccountTargetContent
	{
		OdataType = "#microsoft.graph.addressBookAccountTargetContent",
		Type = AccountTargetContentType.AddressBook,
		AccountTargetEmails = new List<string>
		{
			"faiza@contoso.com",
		},
	},
	ExcludedAccountTarget = new AddressBookAccountTargetContent
	{
		OdataType = "#microsoft.graph.addressBookAccountTargetContent",
		Type = AccountTargetContentType.AddressBook,
		AccountTargetEmails = new List<string>
		{
			"sam@contoso.com",
		},
	},
	AdditionalData = new Dictionary<string, object>
	{
		{
			"@odata.etag" , "\"0100aa9b-0000-0100-0000-6396fa270000\""
		},
		{
			"payload@odata.bind" , "https://graph.microsoft.com/v1.0/security/attacksimulation/payloads/12345678-9abc-def0-123456789a"
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.AttackSimulation.Simulations["{simulation-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewSimulation()
id := "2f5548d1-0dd8-4cc8-9de0-e0d6ec7ea3dc"
requestBody.SetId(&id) 
displayName := "Graph Simulation"
requestBody.SetDisplayName(&displayName) 
durationInDays := int32(7)
requestBody.SetDurationInDays(&durationInDays) 
attackTechnique := graphmodels.CREDENTIALHARVESTING_SIMULATIONATTACKTECHNIQUE 
requestBody.SetAttackTechnique(&attackTechnique) 
attackType := graphmodels.SOCIAL_SIMULATIONATTACKTYPE 
requestBody.SetAttackType(&attackType) 
status := graphmodels.SCHEDULED_SIMULATIONSTATUS 
requestBody.SetStatus(&status) 
includedAccountTarget := graphmodels.NewAddressBookAccountTargetContent()
type := graphmodels.ADDRESSBOOK_ACCOUNTTARGETCONTENTTYPE 
includedAccountTarget.SetType(&type) 
accountTargetEmails := []string {
	"faiza@contoso.com",
}
includedAccountTarget.SetAccountTargetEmails(accountTargetEmails)
requestBody.SetIncludedAccountTarget(includedAccountTarget)
excludedAccountTarget := graphmodels.NewAddressBookAccountTargetContent()
type := graphmodels.ADDRESSBOOK_ACCOUNTTARGETCONTENTTYPE 
excludedAccountTarget.SetType(&type) 
accountTargetEmails := []string {
	"sam@contoso.com",
}
excludedAccountTarget.SetAccountTargetEmails(accountTargetEmails)
requestBody.SetExcludedAccountTarget(excludedAccountTarget)
additionalData := map[string]interface{}{
	"@odata.etag" : "\"0100aa9b-0000-0100-0000-6396fa270000\"", 
	"payload@odata.bind" : "https://graph.microsoft.com/v1.0/security/attacksimulation/payloads/12345678-9abc-def0-123456789a", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
simulations, err := graphClient.Security().AttackSimulation().Simulations().BySimulationId("simulation-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Simulation simulation = new Simulation();
simulation.setId("2f5548d1-0dd8-4cc8-9de0-e0d6ec7ea3dc");
simulation.setDisplayName("Graph Simulation");
simulation.setDurationInDays(7);
simulation.setAttackTechnique(SimulationAttackTechnique.CredentialHarvesting);
simulation.setAttackType(SimulationAttackType.Social);
simulation.setStatus(SimulationStatus.Scheduled);
AddressBookAccountTargetContent includedAccountTarget = new AddressBookAccountTargetContent();
includedAccountTarget.setOdataType("#microsoft.graph.addressBookAccountTargetContent");
includedAccountTarget.setType(AccountTargetContentType.AddressBook);
LinkedList<String> accountTargetEmails = new LinkedList<String>();
accountTargetEmails.add("faiza@contoso.com");
includedAccountTarget.setAccountTargetEmails(accountTargetEmails);
simulation.setIncludedAccountTarget(includedAccountTarget);
AddressBookAccountTargetContent excludedAccountTarget = new AddressBookAccountTargetContent();
excludedAccountTarget.setOdataType("#microsoft.graph.addressBookAccountTargetContent");
excludedAccountTarget.setType(AccountTargetContentType.AddressBook);
LinkedList<String> accountTargetEmails1 = new LinkedList<String>();
accountTargetEmails1.add("sam@contoso.com");
excludedAccountTarget.setAccountTargetEmails(accountTargetEmails1);
simulation.setExcludedAccountTarget(excludedAccountTarget);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("@odata.etag", "\"0100aa9b-0000-0100-0000-6396fa270000\"");
additionalData.put("payload@odata.bind", "https://graph.microsoft.com/v1.0/security/attacksimulation/payloads/12345678-9abc-def0-123456789a");
simulation.setAdditionalData(additionalData);
Simulation result = graphClient.security().attackSimulation().simulations().bySimulationId("{simulation-id}").patch(simulation);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const simulation = {
  '@odata.etag': '\"0100aa9b-0000-0100-0000-6396fa270000\"',
  id: '2f5548d1-0dd8-4cc8-9de0-e0d6ec7ea3dc',
  displayName: 'Graph Simulation',
  'payload@odata.bind':'https://graph.microsoft.com/v1.0/security/attacksimulation/payloads/12345678-9abc-def0-123456789a',
  durationInDays: 7,
  attackTechnique: 'credentialHarvesting',
  attackType: 'social',
  status: 'scheduled',
  includedAccountTarget: {
    '@odata.type': '#microsoft.graph.addressBookAccountTargetContent',
    type: 'addressBook',
    accountTargetEmails: [
        'faiza@contoso.com'
    ]
  },
  excludedAccountTarget: {
    '@odata.type': '#microsoft.graph.addressBookAccountTargetContent',
    type: 'addressBook',
    accountTargetEmails: [
        'sam@contoso.com'
    ]
  }
};

await client.api('/security/attackSimulation/simulations/2f5548d1-0dd8-4cc8-9de0-e0d6ec7ea3dc')
	.update(simulation);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Simulation;
use Microsoft\Graph\Generated\Models\SimulationAttackTechnique;
use Microsoft\Graph\Generated\Models\SimulationAttackType;
use Microsoft\Graph\Generated\Models\SimulationStatus;
use Microsoft\Graph\Generated\Models\AddressBookAccountTargetContent;
use Microsoft\Graph\Generated\Models\AccountTargetContentType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Simulation();
$requestBody->setId('2f5548d1-0dd8-4cc8-9de0-e0d6ec7ea3dc');
$requestBody->setDisplayName('Graph Simulation');
$requestBody->setDurationInDays(7);
$requestBody->setAttackTechnique(new SimulationAttackTechnique('credentialHarvesting'));
$requestBody->setAttackType(new SimulationAttackType('social'));
$requestBody->setStatus(new SimulationStatus('scheduled'));
$includedAccountTarget = new AddressBookAccountTargetContent();
$includedAccountTarget->setOdataType('#microsoft.graph.addressBookAccountTargetContent');
$includedAccountTarget->setType(new AccountTargetContentType('addressBook'));
$includedAccountTarget->setAccountTargetEmails(['faiza@contoso.com', 	]);
$requestBody->setIncludedAccountTarget($includedAccountTarget);
$excludedAccountTarget = new AddressBookAccountTargetContent();
$excludedAccountTarget->setOdataType('#microsoft.graph.addressBookAccountTargetContent');
$excludedAccountTarget->setType(new AccountTargetContentType('addressBook'));
$excludedAccountTarget->setAccountTargetEmails(['sam@contoso.com', 	]);
$requestBody->setExcludedAccountTarget($excludedAccountTarget);
$additionalData = [
	'@odata.etag' => '\"0100aa9b-0000-0100-0000-6396fa270000\"',
	'payload@odata.bind' => 'https://graph.microsoft.com/v1.0/security/attacksimulation/payloads/12345678-9abc-def0-123456789a',
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->security()->attackSimulation()->simulations()->bySimulationId('simulation-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.simulation import Simulation
from msgraph.generated.models.simulation_attack_technique import SimulationAttackTechnique
from msgraph.generated.models.simulation_attack_type import SimulationAttackType
from msgraph.generated.models.simulation_status import SimulationStatus
from msgraph.generated.models.address_book_account_target_content import AddressBookAccountTargetContent
from msgraph.generated.models.account_target_content_type import AccountTargetContentType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Simulation(
	id = "2f5548d1-0dd8-4cc8-9de0-e0d6ec7ea3dc",
	display_name = "Graph Simulation",
	duration_in_days = 7,
	attack_technique = SimulationAttackTechnique.CredentialHarvesting,
	attack_type = SimulationAttackType.Social,
	status = SimulationStatus.Scheduled,
	included_account_target = AddressBookAccountTargetContent(
		odata_type = "#microsoft.graph.addressBookAccountTargetContent",
		type = AccountTargetContentType.AddressBook,
		account_target_emails = [
			"faiza@contoso.com",
		],
	),
	excluded_account_target = AddressBookAccountTargetContent(
		odata_type = "#microsoft.graph.addressBookAccountTargetContent",
		type = AccountTargetContentType.AddressBook,
		account_target_emails = [
			"sam@contoso.com",
		],
	),
	additional_data = {
			"@odata_etag" : "\"0100aa9b-0000-0100-0000-6396fa270000\"",
			"payload@odata_bind" : "https://graph.microsoft.com/v1.0/security/attacksimulation/payloads/12345678-9abc-def0-123456789a",
	}
)

result = await graph_client.security.attack_simulation.simulations.by_simulation_id('simulation-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 202 Accepted
```

### Example 3: Cancel an attack simulation campaign

The following example shows how to cancel an attack simulation campaign for a tenant. You can cancel a simulation when its state is either `scheduled` or `running`.

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
PATCH https://graph.microsoft.com/v1.0/security/attackSimulation/simulations/2f5548d1-0dd8-4cc8-9de0-e0d6ec7ea3dc
Content-type: application/json

{
  "@odata.etag": "\"0100aa9b-0000-0100-0000-6396fa270000\"",
  "id": "2f5548d1-0dd8-4cc8-9de0-e0d6ec7ea3dc",
  "status": "cancelled"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Simulation
{
	Id = "2f5548d1-0dd8-4cc8-9de0-e0d6ec7ea3dc",
	Status = SimulationStatus.Cancelled,
	AdditionalData = new Dictionary<string, object>
	{
		{
			"@odata.etag" , "\"0100aa9b-0000-0100-0000-6396fa270000\""
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.AttackSimulation.Simulations["{simulation-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewSimulation()
id := "2f5548d1-0dd8-4cc8-9de0-e0d6ec7ea3dc"
requestBody.SetId(&id) 
status := graphmodels.CANCELLED_SIMULATIONSTATUS 
requestBody.SetStatus(&status) 
additionalData := map[string]interface{}{
	"@odata.etag" : "\"0100aa9b-0000-0100-0000-6396fa270000\"", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
simulations, err := graphClient.Security().AttackSimulation().Simulations().BySimulationId("simulation-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Simulation simulation = new Simulation();
simulation.setId("2f5548d1-0dd8-4cc8-9de0-e0d6ec7ea3dc");
simulation.setStatus(SimulationStatus.Cancelled);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("@odata.etag", "\"0100aa9b-0000-0100-0000-6396fa270000\"");
simulation.setAdditionalData(additionalData);
Simulation result = graphClient.security().attackSimulation().simulations().bySimulationId("{simulation-id}").patch(simulation);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const simulation = {
  '@odata.etag': '\"0100aa9b-0000-0100-0000-6396fa270000\"',
  id: '2f5548d1-0dd8-4cc8-9de0-e0d6ec7ea3dc',
  status: 'cancelled'
};

await client.api('/security/attackSimulation/simulations/2f5548d1-0dd8-4cc8-9de0-e0d6ec7ea3dc')
	.update(simulation);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Simulation;
use Microsoft\Graph\Generated\Models\SimulationStatus;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Simulation();
$requestBody->setId('2f5548d1-0dd8-4cc8-9de0-e0d6ec7ea3dc');
$requestBody->setStatus(new SimulationStatus('cancelled'));
$additionalData = [
	'@odata.etag' => '\"0100aa9b-0000-0100-0000-6396fa270000\"',
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->security()->attackSimulation()->simulations()->bySimulationId('simulation-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.simulation import Simulation
from msgraph.generated.models.simulation_status import SimulationStatus
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Simulation(
	id = "2f5548d1-0dd8-4cc8-9de0-e0d6ec7ea3dc",
	status = SimulationStatus.Cancelled,
	additional_data = {
			"@odata_etag" : "\"0100aa9b-0000-0100-0000-6396fa270000\"",
	}
)

result = await graph_client.security.attack_simulation.simulations.by_simulation_id('simulation-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 202 Accepted
```

### Example 4: Exclude an attack simulation campaign

The following example shows how to exclude an attack simulation campaign for a tenant. You can only exclude a simulation from any reporting when its state is `cancelled`.

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
PATCH https://graph.microsoft.com/v1.0/security/attackSimulation/simulations/2f5548d1-0dd8-4cc8-9de0-e0d6ec7ea3dc
Content-type: application/json

{
  "@odata.etag": "\"0100aa9b-0000-0100-0000-6396fa270000\"",
  "id": "2f5548d1-0dd8-4cc8-9de0-e0d6ec7ea3dc",
  "status": "excluded"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Simulation
{
	Id = "2f5548d1-0dd8-4cc8-9de0-e0d6ec7ea3dc",
	Status = SimulationStatus.Excluded,
	AdditionalData = new Dictionary<string, object>
	{
		{
			"@odata.etag" , "\"0100aa9b-0000-0100-0000-6396fa270000\""
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.AttackSimulation.Simulations["{simulation-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewSimulation()
id := "2f5548d1-0dd8-4cc8-9de0-e0d6ec7ea3dc"
requestBody.SetId(&id) 
status := graphmodels.EXCLUDED_SIMULATIONSTATUS 
requestBody.SetStatus(&status) 
additionalData := map[string]interface{}{
	"@odata.etag" : "\"0100aa9b-0000-0100-0000-6396fa270000\"", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
simulations, err := graphClient.Security().AttackSimulation().Simulations().BySimulationId("simulation-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Simulation simulation = new Simulation();
simulation.setId("2f5548d1-0dd8-4cc8-9de0-e0d6ec7ea3dc");
simulation.setStatus(SimulationStatus.Excluded);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("@odata.etag", "\"0100aa9b-0000-0100-0000-6396fa270000\"");
simulation.setAdditionalData(additionalData);
Simulation result = graphClient.security().attackSimulation().simulations().bySimulationId("{simulation-id}").patch(simulation);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const simulation = {
  '@odata.etag': '\"0100aa9b-0000-0100-0000-6396fa270000\"',
  id: '2f5548d1-0dd8-4cc8-9de0-e0d6ec7ea3dc',
  status: 'excluded'
};

await client.api('/security/attackSimulation/simulations/2f5548d1-0dd8-4cc8-9de0-e0d6ec7ea3dc')
	.update(simulation);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Simulation;
use Microsoft\Graph\Generated\Models\SimulationStatus;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Simulation();
$requestBody->setId('2f5548d1-0dd8-4cc8-9de0-e0d6ec7ea3dc');
$requestBody->setStatus(new SimulationStatus('excluded'));
$additionalData = [
	'@odata.etag' => '\"0100aa9b-0000-0100-0000-6396fa270000\"',
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->security()->attackSimulation()->simulations()->bySimulationId('simulation-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.simulation import Simulation
from msgraph.generated.models.simulation_status import SimulationStatus
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Simulation(
	id = "2f5548d1-0dd8-4cc8-9de0-e0d6ec7ea3dc",
	status = SimulationStatus.Excluded,
	additional_data = {
			"@odata_etag" : "\"0100aa9b-0000-0100-0000-6396fa270000\"",
	}
)

result = await graph_client.security.attack_simulation.simulations.by_simulation_id('simulation-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 202 Accepted
```
