<!-- Source: https://learn.microsoft.com/en-us/graph/api/group-post-settings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-15 -->

# Create settings

Namespace: microsoft.graph

Create a new [group setting](https://learn.microsoft.com/en-us/graph/api/resources/groupsetting?view=graph-rest-1.0) based on the templates available in [groupSettingTemplates](https://learn.microsoft.com/en-us/graph/api/resources/groupsettingtemplate?view=graph-rest-1.0). These settings can be at the tenant-level or at the group level.

The following group setting templates are available for groups:

- `Group.Unified`: Configure settings for all or specific Microsoft 365 groups.
- `Group.Unified.Guest`: Configure guest access settings for a specific Microsoft 365 group.
- `Group.Security`: Configure settings for all or specific cloud security groups, such as enabling MIP sensitivity labels. Requires a Microsoft Entra ID P1 license.
- `Group.Security.Policies`: Configure settings for a specific cloud security group. Requires a Microsoft Entra ID P1 license.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

### Create tenant-wide settings

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | GroupSettings.ReadWrite.All | Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | GroupSettings.ReadWrite.All | Directory.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Read basic properties on setting templates and settings - *Microsoft Entra Joined Device Local Administrator*, *Directory Readers*, *Global Reader*
- Manage all group/directory settings - *Directory Writers*
- Manage global and local settings for groups; manage `Group.Unified.Guest` and `Group.Unified` settings - *Groups Administrator*
- Update `Password Rule Settings` - *Authentication Policy Administrator*
- Update settings, Read basic properties on setting templates and settings - *User Administrator*

When an app is granted delegated *Directory.Read.All* or *Directory.ReadWrite.All* permissions, the signed-in user only needs the default member role. No additional Microsoft Entra role is required. The Microsoft Entra roles listed above are required only when the calling app is granted a more limited delegated permission, such as *GroupSettings.Read.All*. In that case, the signed-in user must hold one of the listed roles.

### Create group-specific settings

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | GroupSettings.ReadWrite.All | Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | GroupSettings.ReadWrite.All | Directory.ReadWrite.All |

## HTTP request

Create a tenant-wide setting.

```http
POST /groupSettings
```

Create a group-specific setting.

```http
POST /groups/{id}/settings
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json |

## Request body

In the request body, supply a JSON representation of [groupSetting](https://learn.microsoft.com/en-us/graph/api/resources/groupsetting?view=graph-rest-1.0) object. The display name, templateId, and description are inherited from the referenced [groupSettingTemplates](https://learn.microsoft.com/en-us/graph/api/resources/groupsettingtemplate?view=graph-rest-1.0) object. Only the value property can be changed from the default value.

The following properties are required when creating the [groupSetting](https://learn.microsoft.com/en-us/graph/api/resources/groupsetting?view=graph-rest-1.0) object.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| templateId | String | Unique identifier for the tenant-level [groupSettingTemplates](https://learn.microsoft.com/en-us/graph/api/resources/groupsettingtemplate?view=graph-rest-1.0) object used to create this group-level settings object. Read-only. |
| values | [settingValue](https://learn.microsoft.com/en-us/graph/api/resources/settingvalue?view=graph-rest-1.0) collection | Collection of name-value pairs corresponding to the **name** and **defaultValue** properties in the referenced [groupSettingTemplates](https://learn.microsoft.com/en-us/graph/api/resources/groupsettingtemplate?view=graph-rest-1.0) object. |

## Response

If successful, this method returns `201 Created` response code and [groupSetting](https://learn.microsoft.com/en-us/graph/api/resources/groupsetting?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Create a new setting for all Microsoft 365 groups in the tenant

#### Request

Only the [groupSettingTemplates](https://learn.microsoft.com/en-us/graph/api/resources/groupsettingtemplate?view=graph-rest-1.0) object named `Group.Unified` can be applied to all Microsoft 365 groups at the tenant-level.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/groupSettings
Content-type: application/json

{
    "templateId": "62375ab9-6b52-47ed-826b-58e47e0e304b",
    "values": [
        {
            "name": "GuestUsageGuidelinesUrl",
            "value": "https://privacy.contoso.com/privacystatement"
        },
        {
            "name": "EnableMSStandardBlockedWords",
            "value": "true"
        },
        {
            "name": "EnableMIPLabels",
            "value": "true"
        },
        {
            "name": "PrefixSuffixNamingRequirement",
            "value": "[Contoso-][GroupName]"
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
	TemplateId = "62375ab9-6b52-47ed-826b-58e47e0e304b",
	Values = new List<SettingValue>
	{
		new SettingValue
		{
			Name = "GuestUsageGuidelinesUrl",
			Value = "https://privacy.contoso.com/privacystatement",
		},
		new SettingValue
		{
			Name = "EnableMSStandardBlockedWords",
			Value = "true",
		},
		new SettingValue
		{
			Name = "EnableMIPLabels",
			Value = "true",
		},
		new SettingValue
		{
			Name = "PrefixSuffixNamingRequirement",
			Value = "[Contoso-][GroupName]",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.GroupSettings.PostAsync(requestBody);
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
templateId := "62375ab9-6b52-47ed-826b-58e47e0e304b"
requestBody.SetTemplateId(&templateId) 


settingValue := graphmodels.NewSettingValue()
name := "GuestUsageGuidelinesUrl"
settingValue.SetName(&name) 
value := "https://privacy.contoso.com/privacystatement"
settingValue.SetValue(&value) 
settingValue1 := graphmodels.NewSettingValue()
name := "EnableMSStandardBlockedWords"
settingValue1.SetName(&name) 
value := "true"
settingValue1.SetValue(&value) 
settingValue2 := graphmodels.NewSettingValue()
name := "EnableMIPLabels"
settingValue2.SetName(&name) 
value := "true"
settingValue2.SetValue(&value) 
settingValue3 := graphmodels.NewSettingValue()
name := "PrefixSuffixNamingRequirement"
settingValue3.SetName(&name) 
value := "[Contoso-][GroupName]"
settingValue3.SetValue(&value) 

values := []graphmodels.SettingValueable {
	settingValue,
	settingValue1,
	settingValue2,
	settingValue3,
}
requestBody.SetValues(values)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
groupSettings, err := graphClient.GroupSettings().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

GroupSetting groupSetting = new GroupSetting();
groupSetting.setTemplateId("62375ab9-6b52-47ed-826b-58e47e0e304b");
LinkedList<SettingValue> values = new LinkedList<SettingValue>();
SettingValue settingValue = new SettingValue();
settingValue.setName("GuestUsageGuidelinesUrl");
settingValue.setValue("https://privacy.contoso.com/privacystatement");
values.add(settingValue);
SettingValue settingValue1 = new SettingValue();
settingValue1.setName("EnableMSStandardBlockedWords");
settingValue1.setValue("true");
values.add(settingValue1);
SettingValue settingValue2 = new SettingValue();
settingValue2.setName("EnableMIPLabels");
settingValue2.setValue("true");
values.add(settingValue2);
SettingValue settingValue3 = new SettingValue();
settingValue3.setName("PrefixSuffixNamingRequirement");
settingValue3.setValue("[Contoso-][GroupName]");
values.add(settingValue3);
groupSetting.setValues(values);
GroupSetting result = graphClient.groupSettings().post(groupSetting);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const groupSetting = {
    templateId: '62375ab9-6b52-47ed-826b-58e47e0e304b',
    values: [
        {
            name: 'GuestUsageGuidelinesUrl',
            value: 'https://privacy.contoso.com/privacystatement'
        },
        {
            name: 'EnableMSStandardBlockedWords',
            value: 'true'
        },
        {
            name: 'EnableMIPLabels',
            value: 'true'
        },
        {
            name: 'PrefixSuffixNamingRequirement',
            value: '[Contoso-][GroupName]'
        }
    ]
};

await client.api('/groupSettings')
	.post(groupSetting);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\GroupSetting;
use Microsoft\Graph\Generated\Models\SettingValue;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new GroupSetting();
$requestBody->setTemplateId('62375ab9-6b52-47ed-826b-58e47e0e304b');
$valuesSettingValue1 = new SettingValue();
$valuesSettingValue1->setName('GuestUsageGuidelinesUrl');
$valuesSettingValue1->setValue('https://privacy.contoso.com/privacystatement');
$valuesArray []= $valuesSettingValue1;
$valuesSettingValue2 = new SettingValue();
$valuesSettingValue2->setName('EnableMSStandardBlockedWords');
$valuesSettingValue2->setValue('true');
$valuesArray []= $valuesSettingValue2;
$valuesSettingValue3 = new SettingValue();
$valuesSettingValue3->setName('EnableMIPLabels');
$valuesSettingValue3->setValue('true');
$valuesArray []= $valuesSettingValue3;
$valuesSettingValue4 = new SettingValue();
$valuesSettingValue4->setName('PrefixSuffixNamingRequirement');
$valuesSettingValue4->setValue('[Contoso-][GroupName]');
$valuesArray []= $valuesSettingValue4;
$requestBody->setValues($valuesArray);


$result = $graphServiceClient->groupSettings()->post($requestBody)->wait();
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
	template_id = "62375ab9-6b52-47ed-826b-58e47e0e304b",
	values = [
		SettingValue(
			name = "GuestUsageGuidelinesUrl",
			value = "https://privacy.contoso.com/privacystatement",
		),
		SettingValue(
			name = "EnableMSStandardBlockedWords",
			value = "true",
		),
		SettingValue(
			name = "EnableMIPLabels",
			value = "true",
		),
		SettingValue(
			name = "PrefixSuffixNamingRequirement",
			value = "[Contoso-][GroupName]",
		),
	],
)

result = await graph_client.group_settings.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#groupSettings/$entity",
    "id": "844d252c-4de2-43eb-a784-96df77231aae",
    "displayName": null,
    "templateId": "62375ab9-6b52-47ed-826b-58e47e0e304b",
    "values": [
        {
            "name": "GuestUsageGuidelinesUrl",
            "value": "https://privacy.contoso.com/privacystatement"
        },
        {
            "name": "EnableMSStandardBlockedWords",
            "value": "true"
        },
        {
            "name": "EnableMIPLabels",
            "value": "true"
        },
        {
            "name": "PrefixSuffixNamingRequirement",
            "value": "[Contoso-][GroupName]"
        }
    ]
}
```

The **displayName** property and other name-value pairs will be populated with the default values from the [groupSettingTemplates](https://learn.microsoft.com/en-us/graph/api/resources/groupsettingtemplate?view=graph-rest-1.0) object that matches the **templateId**.

### Example 2: Create a setting to block guests for a specific Microsoft 365 group

#### Request

Only the [groupSettingTemplates](https://learn.microsoft.com/en-us/graph/api/resources/groupsettingtemplate?view=graph-rest-1.0) object named `Group.Unified.Guest` can be applied to specific Microsoft 365 groups.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/groups/055a5d18-a3a9-4338-b9c5-de92559b7ebf/settings
Content-type: application/json

{
    "templateId": "08d542b9-071f-4e16-94b0-74abb372e3d9",
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
	TemplateId = "08d542b9-071f-4e16-94b0-74abb372e3d9",
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
var result = await graphClient.Groups["{group-id}"].Settings.PostAsync(requestBody);
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
templateId := "08d542b9-071f-4e16-94b0-74abb372e3d9"
requestBody.SetTemplateId(&templateId) 


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
settings, err := graphClient.Groups().ByGroupId("group-id").Settings().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

GroupSetting groupSetting = new GroupSetting();
groupSetting.setTemplateId("08d542b9-071f-4e16-94b0-74abb372e3d9");
LinkedList<SettingValue> values = new LinkedList<SettingValue>();
SettingValue settingValue = new SettingValue();
settingValue.setName("AllowToAddGuests");
settingValue.setValue("false");
values.add(settingValue);
groupSetting.setValues(values);
GroupSetting result = graphClient.groups().byGroupId("{group-id}").settings().post(groupSetting);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const groupSetting = {
    templateId: '08d542b9-071f-4e16-94b0-74abb372e3d9',
    values: [
        {
            name: 'AllowToAddGuests',
            value: 'false'
        }
    ]
};

await client.api('/groups/055a5d18-a3a9-4338-b9c5-de92559b7ebf/settings')
	.post(groupSetting);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\GroupSetting;
use Microsoft\Graph\Generated\Models\SettingValue;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new GroupSetting();
$requestBody->setTemplateId('08d542b9-071f-4e16-94b0-74abb372e3d9');
$valuesSettingValue1 = new SettingValue();
$valuesSettingValue1->setName('AllowToAddGuests');
$valuesSettingValue1->setValue('false');
$valuesArray []= $valuesSettingValue1;
$requestBody->setValues($valuesArray);


$result = $graphServiceClient->groups()->byGroupId('group-id')->settings()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Groups

$params = @{
	templateId = "08d542b9-071f-4e16-94b0-74abb372e3d9"
	values = @(
		@{
			name = "AllowToAddGuests"
			value = "false"
		}
	)
}

New-MgGroupSetting -GroupId $groupId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.group_setting import GroupSetting
from msgraph.generated.models.setting_value import SettingValue
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = GroupSetting(
	template_id = "08d542b9-071f-4e16-94b0-74abb372e3d9",
	values = [
		SettingValue(
			name = "AllowToAddGuests",
			value = "false",
		),
	],
)

result = await graph_client.groups.by_group_id('group-id').settings.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

In the request body, supply a JSON representation of [groupSetting](https://learn.microsoft.com/en-us/graph/api/resources/groupsetting?view=graph-rest-1.0) object.

#### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#groupSettings/$entity",
    "id": "a06fa228-3042-4662-bd09-33e298da1afe",
    "displayName": null,
    "templateId": "08d542b9-071f-4e16-94b0-74abb372e3d9",
    "values": [
        {
            "name": "AllowToAddGuests",
            "value": "false"
        }
    ]
}
```

### Example 3: Enable sensitivity labels for all cloud security groups in the tenant

Only the [groupSettingTemplates](https://learn.microsoft.com/en-us/graph/api/resources/groupsettingtemplate?view=graph-rest-1.0) object named `Group.Security` can be applied to all cloud security groups at the tenant-level.

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

```http
POST https://graph.microsoft.com/v1.0/groupSettings
Content-type: application/json

{
    "templateId": "d209f6fa-3839-4d70-b83f-60b1c64d0e8f",
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
	TemplateId = "d209f6fa-3839-4d70-b83f-60b1c64d0e8f",
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
var result = await graphClient.GroupSettings.PostAsync(requestBody);
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
templateId := "d209f6fa-3839-4d70-b83f-60b1c64d0e8f"
requestBody.SetTemplateId(&templateId) 


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
groupSettings, err := graphClient.GroupSettings().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

GroupSetting groupSetting = new GroupSetting();
groupSetting.setTemplateId("d209f6fa-3839-4d70-b83f-60b1c64d0e8f");
LinkedList<SettingValue> values = new LinkedList<SettingValue>();
SettingValue settingValue = new SettingValue();
settingValue.setName("EnableMIPLabels");
settingValue.setValue("true");
values.add(settingValue);
groupSetting.setValues(values);
GroupSetting result = graphClient.groupSettings().post(groupSetting);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const groupSetting = {
    templateId: 'd209f6fa-3839-4d70-b83f-60b1c64d0e8f',
    values: [
        {
            name: 'EnableMIPLabels',
            value: 'true'
        }
    ]
};

await client.api('/groupSettings')
	.post(groupSetting);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\GroupSetting;
use Microsoft\Graph\Generated\Models\SettingValue;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new GroupSetting();
$requestBody->setTemplateId('d209f6fa-3839-4d70-b83f-60b1c64d0e8f');
$valuesSettingValue1 = new SettingValue();
$valuesSettingValue1->setName('EnableMIPLabels');
$valuesSettingValue1->setValue('true');
$valuesArray []= $valuesSettingValue1;
$requestBody->setValues($valuesArray);


$result = $graphServiceClient->groupSettings()->post($requestBody)->wait();
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
	template_id = "d209f6fa-3839-4d70-b83f-60b1c64d0e8f",
	values = [
		SettingValue(
			name = "EnableMIPLabels",
			value = "true",
		),
	],
)

result = await graph_client.group_settings.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#groupSettings/$entity",
    "id": "3e4a9b9d-1234-5678-abcd-1234567890ab",
    "displayName": null,
    "templateId": "d209f6fa-3839-4d70-b83f-60b1c64d0e8f",
    "values": [
        {
            "name": "EnableMIPLabels",
            "value": "true"
        }
    ]
}
```

### Example 4: Block guests for a specific cloud security group

Only the [groupSettingTemplates](https://learn.microsoft.com/en-us/graph/api/resources/groupsettingtemplate?view=graph-rest-1.0) object named `Group.Security.Policies` can be applied to specific cloud security groups.

Note

This feature requires a Microsoft Entra ID P1 license.

#### Request

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```http
POST https://graph.microsoft.com/v1.0/groups/{securityGroupId}/settings
Content-type: application/json

{
    "templateId": "7e0abea2-5c20-405f-9658-bfc9a523fd49",
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
	TemplateId = "7e0abea2-5c20-405f-9658-bfc9a523fd49",
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
var result = await graphClient.Groups["{group-id}"].Settings.PostAsync(requestBody);
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
templateId := "7e0abea2-5c20-405f-9658-bfc9a523fd49"
requestBody.SetTemplateId(&templateId) 


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
settings, err := graphClient.Groups().ByGroupId("group-id").Settings().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

GroupSetting groupSetting = new GroupSetting();
groupSetting.setTemplateId("7e0abea2-5c20-405f-9658-bfc9a523fd49");
LinkedList<SettingValue> values = new LinkedList<SettingValue>();
SettingValue settingValue = new SettingValue();
settingValue.setName("AllowToAddGuests");
settingValue.setValue("false");
values.add(settingValue);
groupSetting.setValues(values);
GroupSetting result = graphClient.groups().byGroupId("{group-id}").settings().post(groupSetting);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const groupSetting = {
    templateId: '7e0abea2-5c20-405f-9658-bfc9a523fd49',
    values: [
        {
            name: 'AllowToAddGuests',
            value: 'false'
        }
    ]
};

await client.api('/groups/{securityGroupId}/settings')
	.post(groupSetting);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\GroupSetting;
use Microsoft\Graph\Generated\Models\SettingValue;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new GroupSetting();
$requestBody->setTemplateId('7e0abea2-5c20-405f-9658-bfc9a523fd49');
$valuesSettingValue1 = new SettingValue();
$valuesSettingValue1->setName('AllowToAddGuests');
$valuesSettingValue1->setValue('false');
$valuesArray []= $valuesSettingValue1;
$requestBody->setValues($valuesArray);


$result = $graphServiceClient->groups()->byGroupId('group-id')->settings()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Groups

$params = @{
	templateId = "7e0abea2-5c20-405f-9658-bfc9a523fd49"
	values = @(
		@{
			name = "AllowToAddGuests"
			value = "false"
		}
	)
}

New-MgGroupSetting -GroupId $groupId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.group_setting import GroupSetting
from msgraph.generated.models.setting_value import SettingValue
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = GroupSetting(
	template_id = "7e0abea2-5c20-405f-9658-bfc9a523fd49",
	values = [
		SettingValue(
			name = "AllowToAddGuests",
			value = "false",
		),
	],
)

result = await graph_client.groups.by_group_id('group-id').settings.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#groupSettings/$entity",
    "id": "fa6df613-abcd-1234-add2-1234567890ab",
    "displayName": null,
    "templateId": "7e0abea2-5c20-405f-9658-bfc9a523fd49",
    "values": [
        {
            "name": "AllowToAddGuests",
            "value": "false"
        }
    ]
}
```
