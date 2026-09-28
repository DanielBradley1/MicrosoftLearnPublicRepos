<!-- Source: https://learn.microsoft.com/en-us/graph/api/groupsetting-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-15 -->

# Update groupSetting

Namespace: microsoft.graph

Update the properties of a [groupSetting](https://learn.microsoft.com/en-us/graph/api/resources/groupsetting?view=graph-rest-1.0) object for tenant-wide [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) settings or a specific group setting.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

The following tables show the least privileged permission or permissions required to call this API on each supported resource type. Follow [best practices](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions) to request least privileged permissions. For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

### For all settings *except* the Consent Policy Settings object

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | GroupSettings.ReadWrite.All | Directory.ReadWrite.All, Policy.ReadWrite.Authorization |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | GroupSettings.ReadWrite.All | Directory.ReadWrite.All, Policy.ReadWrite.Authorization |

### For the Consent Policy Settings object

The following permissions are required to update the "Consent Policy Settings" **directorySetting** object.

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | GroupSettings.ReadWrite.All | Directory.ReadWrite.All, Policy.ReadWrite.Authorization |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | GroupSettings.ReadWrite.All | Directory.ReadWrite.All, Policy.ReadWrite.Authorization |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Read basic properties on setting templates and settings - *Microsoft Entra Joined Device Local Administrator*, *Directory Readers*, *Global Reader*
- Manage all group/directory settings - *Directory Writers*
- Manage global and local settings for groups; manage `Group.Unified.Guest` and `Group.Unified` settings - *Groups Administrator*
- Update `Password Rule Settings` - *Authentication Policy Administrator*
- Update settings, Read basic properties on setting templates and settings - *User Administrator*

When an app is granted delegated *Directory.Read.All* or *Directory.ReadWrite.All* permissions, the signed-in user only needs the default member role. No additional Microsoft Entra role is required. The Microsoft Entra roles listed above are required only when the calling app is granted a more limited delegated permission, such as *GroupSettings.Read.All*. In that case, the signed-in user must hold one of the listed roles.

## HTTP request

Update a tenant-wide setting.

```http
PATCH /groupSettings/{groupSettingId}
```

Update a group-specific setting.

```http
PATCH /groups/{groupId}/settings/{groupSettingId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | {token}. Required. |
| Content-Type | application/json |

## Request body

In the request body, supply the values for relevant fields that should be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| values | [settingValue](https://learn.microsoft.com/en-us/graph/api/resources/settingvalue?view=graph-rest-1.0) collection | The updated set of values. You must include the entire collection set. You cannot update a single set of values. |

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

### Example 1: Update a tenant-wide group setting

In this example, `84af2ca5-c274-41bf-86e4-6e374ec4def6` is the identifier of the tenant-wide **groupSetting** object.

#### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
PATCH https://graph.microsoft.com/v1.0/groupSettings/84af2ca5-c274-41bf-86e4-6e374ec4def6
Content-type: application/json

{
    "values": [
        {
            "name": "AllowToAddGuests",
            "value": "false"
        }
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new GroupSetting
{
	Values = new List<SettingValue>
	{
		new SettingValue
		{
			Name = "AllowToAddGuests",
			Value = "false",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.GroupSettings["{groupSetting-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewGroupSetting()


settingValue := graphmodels.NewSettingValue()
name := "AllowToAddGuests"
settingValue.SetName(&name) 
value := "false"
settingValue.SetValue(&value) 

values := []graphmodels.SettingValueable {
	settingValue,
}
requestBody.SetValues(values)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
groupSettings, err := graphClient.GroupSettings().ByGroupSettingId("groupSetting-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

GroupSetting groupSetting = new GroupSetting();
LinkedList<SettingValue> values = new LinkedList<SettingValue>();
SettingValue settingValue = new SettingValue();
settingValue.setName("AllowToAddGuests");
settingValue.setValue("false");
values.add(settingValue);
groupSetting.setValues(values);
GroupSetting result = graphClient.groupSettings().byGroupSettingId("{groupSetting-id}").patch(groupSetting);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const groupSetting = {
    values: [
        {
            name: 'AllowToAddGuests',
            value: 'false'
        }
    ]
};

await client.api('/groupSettings/84af2ca5-c274-41bf-86e4-6e374ec4def6')
	.update(groupSetting);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\GroupSetting;
use Microsoft\Graph\Generated\Models\SettingValue;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new GroupSetting();
$valuesSettingValue1 = new SettingValue();
$valuesSettingValue1->setName('AllowToAddGuests');
$valuesSettingValue1->setValue('false');
$valuesArray []= $valuesSettingValue1;
$requestBody->setValues($valuesArray);


$result = $graphServiceClient->groupSettings()->byGroupSettingId('groupSetting-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```
Snippet not available
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.group_setting import GroupSetting
from msgraph.generated.models.setting_value import SettingValue
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = GroupSetting(
	values = [
		SettingValue(
			name = "AllowToAddGuests",
			value = "false",
		),
	],
)

result = await graph_client.group_settings.by_group_setting_id('groupSetting-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

```http
HTTP/1.1 204 No Content
```

### Example 2: Update a specific group setting

In this example, `0167b5af-f3d1-4910-82d2-398747fa381c` is the identifier of the group, and `fa6df613-159b-4f94-add2-7093f961900b` is the identifier of the groupSetting object.

#### Request

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```msgraph
PATCH https://graph.microsoft.com/v1.0/groups/0167b5af-f3d1-4910-82d2-398747fa381c/settings/fa6df613-159b-4f94-add2-7093f961900b
Content-type: application/json

{
  "values": [
    {
      "name": "AllowToAddGuests",
      "value": "true"
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new GroupSetting
{
	Values = new List<SettingValue>
	{
		new SettingValue
		{
			Name = "AllowToAddGuests",
			Value = "true",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Groups["{group-id}"].Settings["{groupSetting-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewGroupSetting()


settingValue := graphmodels.NewSettingValue()
name := "AllowToAddGuests"
settingValue.SetName(&name) 
value := "true"
settingValue.SetValue(&value) 

values := []graphmodels.SettingValueable {
	settingValue,
}
requestBody.SetValues(values)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
settings, err := graphClient.Groups().ByGroupId("group-id").Settings().ByGroupSettingId("groupSetting-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

GroupSetting groupSetting = new GroupSetting();
LinkedList<SettingValue> values = new LinkedList<SettingValue>();
SettingValue settingValue = new SettingValue();
settingValue.setName("AllowToAddGuests");
settingValue.setValue("true");
values.add(settingValue);
groupSetting.setValues(values);
GroupSetting result = graphClient.groups().byGroupId("{group-id}").settings().byGroupSettingId("{groupSetting-id}").patch(groupSetting);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const groupSetting = {
  values: [
    {
      name: 'AllowToAddGuests',
      value: 'true'
    }
  ]
};

await client.api('/groups/0167b5af-f3d1-4910-82d2-398747fa381c/settings/fa6df613-159b-4f94-add2-7093f961900b')
	.update(groupSetting);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\GroupSetting;
use Microsoft\Graph\Generated\Models\SettingValue;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new GroupSetting();
$valuesSettingValue1 = new SettingValue();
$valuesSettingValue1->setName('AllowToAddGuests');
$valuesSettingValue1->setValue('true');
$valuesArray []= $valuesSettingValue1;
$requestBody->setValues($valuesArray);


$result = $graphServiceClient->groups()->byGroupId('group-id')->settings()->byGroupSettingId('groupSetting-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Groups

$params = @{
	values = @(
		@{
			name = "AllowToAddGuests"
			value = "true"
		}
	)
}

Update-MgGroupSetting -GroupId $groupId -GroupSettingId $groupSettingId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.group_setting import GroupSetting
from msgraph.generated.models.setting_value import SettingValue
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = GroupSetting(
	values = [
		SettingValue(
			name = "AllowToAddGuests",
			value = "true",
		),
	],
)

result = await graph_client.groups.by_group_id('group-id').settings.by_group_setting_id('groupSetting-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

```http
HTTP/1.1 204 No Content
```

Use the `Group.Security` template \(`d209f6fa-3839-4d70-b83f-60b1c64d0e8f`\) to enable MIP sensitivity labels for all cloud security groups and keep the preexisting setting for `AllowToAddGuests`. You must have already [created a **groupSetting** object](https://learn.microsoft.com/en-us/graph/api/group-post-settings?view=graph-rest-1.0) from this template; replace the identifier in the URL with the ID of the existing **groupSetting** object.

Note

This feature requires a Microsoft Entra ID P1 license.

#### Request

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```msgraph
PATCH https://graph.microsoft.com/v1.0/groupSettings/{groupSettingId}
Content-type: application/json

{
    "values": [
        {
            "name": "EnableMIPLabels",
            "value": "true"
        }
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new GroupSetting
{
	Values = new List<SettingValue>
	{
		new SettingValue
		{
			Name = "EnableMIPLabels",
			Value = "true",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.GroupSettings["{groupSetting-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewGroupSetting()


settingValue := graphmodels.NewSettingValue()
name := "EnableMIPLabels"
settingValue.SetName(&name) 
value := "true"
settingValue.SetValue(&value) 

values := []graphmodels.SettingValueable {
	settingValue,
}
requestBody.SetValues(values)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
groupSettings, err := graphClient.GroupSettings().ByGroupSettingId("groupSetting-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

GroupSetting groupSetting = new GroupSetting();
LinkedList<SettingValue> values = new LinkedList<SettingValue>();
SettingValue settingValue = new SettingValue();
settingValue.setName("EnableMIPLabels");
settingValue.setValue("true");
values.add(settingValue);
groupSetting.setValues(values);
GroupSetting result = graphClient.groupSettings().byGroupSettingId("{groupSetting-id}").patch(groupSetting);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const groupSetting = {
    values: [
        {
            name: 'EnableMIPLabels',
            value: 'true'
        }
    ]
};

await client.api('/groupSettings/{groupSettingId}')
	.update(groupSetting);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\GroupSetting;
use Microsoft\Graph\Generated\Models\SettingValue;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new GroupSetting();
$valuesSettingValue1 = new SettingValue();
$valuesSettingValue1->setName('EnableMIPLabels');
$valuesSettingValue1->setValue('true');
$valuesArray []= $valuesSettingValue1;
$requestBody->setValues($valuesArray);


$result = $graphServiceClient->groupSettings()->byGroupSettingId('groupSetting-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```
Snippet not available
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.group_setting import GroupSetting
from msgraph.generated.models.setting_value import SettingValue
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = GroupSetting(
	values = [
		SettingValue(
			name = "EnableMIPLabels",
			value = "true",
		),
	],
)

result = await graph_client.group_settings.by_group_setting_id('groupSetting-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

```http
HTTP/1.1 204 No Content
```
