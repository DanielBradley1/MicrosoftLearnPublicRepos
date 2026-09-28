<!-- Source: https://learn.microsoft.com/en-us/graph/group-directory-settings -->
<!-- Sitemap-Last-Modified: 2026-07-09 -->

# Overview of group settings

Group settings, also known as *directory settings* in `beta`, are a collection of configurations that allow you to manage behaviors for specific Microsoft Entra objects like Microsoft 365 groups. These settings can be applied tenant-wide or to specific objects, enabling you to control various aspects of group functionality.

In this article, we explore the different types of group settings, and deep dive into the settings applicable to Microsoft 365 groups

## Types of group settings

Group settings are organized into templates, each containing a collection of individual settings. These templates are read-only and define the allowed behaviors for specific Microsoft Entra objects. The following groups of setting templates are available:

| Setting template name | Description |
| --- | --- |
| Group.Unified | Includes settings for Microsoft 365 groups. Examples include blocked words for group names, whether a prefix should be appended to a group name, and whether sensitivity labels can be assigned to groups. For more information, see [Group.Unified](#groupunified) |
| Group.Unified.Guest | Includes settings for guest access in a specific Microsoft 365 group. For more information, see [Group.Unified.Guest](#groupunifiedguest). |
| Group.Security | Settings for cloud security groups, such as whether Microsoft Information Protection \(MIP\) sensitivity labels can be assigned to security groups. For more information, see [Group.Security](#groupsecurity). |
| Group.Security.Policies | Settings for cloud security groups, such as whether guests are allowed. For more information, see [Group.Security.Policies](#groupsecuritypolicies). |
| Application | Includes settings for managing tenant-wide application behavior. |
| Custom Policy Settings | Includes the tenant-wide conditional access settings, such as URL. |
| Consent Policy Settings | Includes settings for the tenant-wide consent policy, such as whether user consent is blocked for risky applications and whether users can request for admin consent. |
| Password Rule Settings | Includes settings for managing tenant-wide password rule settings, such as the banned password list, whether banned password check is enabled, and the lockout duration after failed sign-in attempts. For more information, see [Configure custom banned passwords for Microsoft Entra password protection](https://learn.microsoft.com/en-us/entra/identity/authentication/tutorial-configure-custom-password-protection) |
| Prohibited Names Restricted Settings | Includes tenant-wide settings for prohibited names. |
| Prohibited Names Settings | Includes prohibited names for applications. |

The setting templates are available through the [groupSettingTemplates resource type](https://learn.microsoft.com/en-us/graph/api/resources/groupsettingtemplate) in `v1.0` and [directorySettingTemplates](https://learn.microsoft.com/en-us/graph/api/resources/directorysettingtemplate) resource type in `beta`.

Initially, Microsoft Entra ID assigns the default configuration to the tenant and there are no setting objects. To change the default settings, you must create a new settings object from a settings template.

From the setting templates, you can configure tenant-wide settings or settings for individual objects. Use the [groupSettings resource type](https://learn.microsoft.com/en-us/graph/api/resources/groupsetting) in `v1.0` or the [directorySetting resource type](https://learn.microsoft.com/en-us/graph/api/resources/directorysetting) in `beta` and their associated APIs.

For groups, settings are available for Microsoft 365 groups and cloud security groups. Mail-enabled security groups and distribution lists aren't supported.

## Group.Unified

This object specifies Microsoft 365 group settings for your tenant.

Unless otherwise indicated, these features require a Microsoft Entra ID P1 license.

| Setting name | Type | Description |
| --- | --- | --- |
| AllowGuestsToAccessGroups | Boolean | Indicates whether a guest has access to Microsoft 365 groups and their data. This setting doesn't require a Microsoft Entra ID P1 license. |
| AllowGuestsToBeGroupOwner | Boolean | Indicates whether a guest can be a Microsoft 365 group owner. |
| AllowToAddGuests | Boolean | Indicates whether a Microsoft 365 group can have guests as members. This setting can be overridden and become read-only if **EnableMIPLabels** is `true` and a guest policy is associated with the sensitivity label assigned to the group. If this setting is `false` at the tenant-level, it overrides the corresponding group-level setting when it's `true`. To enable guest access for only a few Microsoft 365 groups, set **AllowToAddGuests** to be `true` at the tenant-level, and then selectively disable this setting for individual Microsoft 365 groups to exclude. |
| ClassificationDescriptions | String | A comma-delimited list of classification descriptions. A valid value has the following format: `"Value:Description"` where *Value* matches an entry in the **ClassificationList** setting. This setting doesn't apply when **EnableMIPLabels** is `true`. Maximum character limit is 300 and commas can't be escaped. |
| ClassificationList | String | A comma-delimited list of values that can be applied to classify Microsoft 365 groups. This setting doesn't apply when **EnableMIPLabels** is `true`. For more information, see [SharePoint "modern" sites classification](https://learn.microsoft.com/en-us/sharepoint/dev/solution-guidance/modern-experience-site-classification). |
| CustomBlockedWordsList | String | Comma-separated string of phrases that users aren't permitted to use in group names or aliases. For more information, see [Enforce a naming policy for Microsoft 365 groups](https://learn.microsoft.com/en-us/entra/identity/users/groups-naming-policy). |
| DefaultClassification | String | The default classification for a Microsoft 365 group if none was specified during group creation. This setting doesn't apply when **EnableMIPLabels** is `true`. For more information, see [SharePoint "modern" sites classification](https://learn.microsoft.com/en-us/sharepoint/dev/solution-guidance/modern-experience-site-classification). |
| EnableGroupCreation | Boolean | Indicates whether nonadmin users can create Microsoft 365 groups. The default setting is `true`. This setting doesn't require a Microsoft Entra ID P1 license. This setting corresponds to the *Users can create Microsoft 365 groups in Azure portals, API or PowerShell* setting in the [group settings menu in the Microsoft Entra admin center](https://learn.microsoft.com/en-us/entra/identity/users/groups-self-service-management).  <br>  <br>**Note:** *The Users can create security groups in Azure portals, API or PowerShell* setting is configured through the **allowedToCreateSecurityGroups** property of the [defaultUserRolePermissions](https://learn.microsoft.com/en-us/graph/api/resources/defaultuserrolepermissions) object of the [authorizationPolicy resource type](https://learn.microsoft.com/en-us/graph/api/resources/authorizationpolicy). |
| EnableMSStandardBlockedWords | Boolean | Deprecated and retired. |
| EnableMIPLabels | Boolean | Indicates whether information protection sensitivity labels published in the Microsoft Purview compliance portal can be applied to Microsoft 365 groups. For more information, see [Assign Sensitivity Labels for Microsoft 365 groups](https://learn.microsoft.com/en-us/entra/identity/users/groups-assign-sensitivity-labels). |
| GroupCreationAllowedGroupId | GUID | Identifier of the security group for which the members are allowed to create Microsoft 365 groups even when **EnableGroupCreation** is `false`. This setting doesn't require a Microsoft Entra ID P1 license. |
| GuestUsageGuidelinesUrl | String | The URL of a link to the guest usage guidelines. |
| NewUnifiedGroupWritebackDefault | Boolean | A tenant-wide setting that assigns the default value to the **writebackConfiguration/isEnabled** property of new groups, if the property isn't specified during group creation. This setting is applicable when group writeback is configured in Microsoft Entra Connect. The default value is `true`.  <br>  <br>Updating this setting to `false` changes the default writeback behavior for new Microsoft 365 groups, but doesn't change **writebackConfiguration/isEnabled** property for existing Microsoft 365 groups. For more information about this setting and the group's **writebackConfiguration** property, see [group resource type](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-beta&preserve-view=true) |
| PrefixSuffixNamingRequirement | String | Defines the naming convention for Microsoft 365 group names and mail nicknames. Maximum character limit is 64. For more information, see [Enforce a naming policy for Microsoft 365 groups](https://learn.microsoft.com/en-us/entra/identity/users/groups-naming-policy). |
| UsageGuidelinesUrl | String | A link to the Group Usage Guidelines. The default is an empty value. |

## Group.Unified.Guest

The settings in this object specify whether guests can be added to all or specific Microsoft 365 groups in the tenant. Only one setting is available in this collection.

| Setting name | Type | Description |
| --- | --- | --- |
| AllowToAddGuests | Boolean | Indicates whether guests can be added to all or specific Microsoft 365 groups. The default setting is `true`. This setting can be overwritten when:  <br><br><br><li><strong>EnableMIPLabels</strong> is <code>true</code> and a guest policy is applied when a sensitivity label is assigned to a group </li><br><br><li><strong>AllowToAddGuests</strong> is <code>false</code> at the tenant-level, then the group-level setting is overwritten </li> |

## Group.Security

Note

This feature requires a Microsoft Entra ID P1 license.

Specifies settings for cloud security groups at the tenant-level or for specific groups. For more information about sensitivity labels for security groups, see [Sensitivity labels for Microsoft 365 groups and cloud security groups](https://learn.microsoft.com/en-us/entra/identity/users/groups-sensitivity-labels).

| Setting name | Type | Description |
| --- | --- | --- |
| AllowToAddGuests | Boolean | Indicates whether guests can be added to any cloud security group in the tenant. The default setting is `true`. |
| EnableMIPLabels | Boolean | Indicates whether Microsoft Information Protection sensitivity labels published in the Microsoft Purview compliance portal can be applied to cloud security groups. When set to `true`, users with appropriate roles can assign sensitivity labels to cloud security groups. For more information, see [Sensitivity labels for Microsoft 365 groups and cloud security groups](https://learn.microsoft.com/en-us/entra/identity/users/groups-sensitivity-labels). |

## Group.Security.Policies

Specifies settings for cloud security groups.

Note

This feature requires a Microsoft Entra ID P1 license.

| Setting name | Type | Description |
| --- | --- | --- |
| AllowToAddGuests | Boolean | Indicates whether guests can be added to a specific cloud security group. Default `true`. |

## How to manage a group setting

To manage a group setting:

1. First, retrieve the details of the group setting template you want to use by using the [List groupSettings API](https://learn.microsoft.com/en-us/graph/api/groupsettingtemplate-list).
2. Create the group setting: Use the retrieved template to create a new group setting: [Create groupSetting](https://learn.microsoft.com/en-us/graph/api/group-post-settings) \(v1.0\) or [Create directorySetting](https://learn.microsoft.com/en-us/graph/api/group-post-settings?view=graph-rest-beta&preserve-view=true) \(beta\).
3. Update the Group Setting: If needed, update the group setting with specific values.

### Example: Configure a prefix for Microsoft 365 group names

### Step 1: Retrieve the PrefixSuffixNamingRequirement group setting configuration

You must retrieve all group settings because the API doesn't support filtering. The `PrefixSuffixNamingRequirement` group setting is contained in the `Group.Unified` template.

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
GET https://graph.microsoft.com/v1.0/groupSettingTemplates
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.GroupSettingTemplates.GetAsync();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
groupSettingTemplates, err := graphClient.GroupSettingTemplates().Get(context.Background(), nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

GroupSettingTemplateCollectionResponse result = graphClient.groupSettingTemplates().get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let groupSettingTemplates = await client.api('/groupSettingTemplates')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->groupSettingTemplates()->get()->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Groups

Get-MgGroupSettingTemplateGroupSettingTemplate
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.group_setting_templates.get()
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#groupSettingTemplates",
    "@microsoft.graph.tips": "Use $select to choose only the properties your app needs, as this can lead to performance improvements. For example: GET groupSettingTemplates?$select=description,displayName",
    "value": [
        {
            "id": "62375ab9-6b52-47ed-826b-58e47e0e304b",
            "deletedDateTime": null,
            "displayName": "Group.Unified",
            "description": "\n        Setting templates define the different settings that can be used for the associated ObjectSettings. This template defines\n        settings that can be used for Unified Groups.\n      ",
            "values": [
                {
                    "name": "PrefixSuffixNamingRequirement",
                    "type": "System.String",
                    "defaultValue": "",
                    "description": "A structured string describing how a Unified Group displayName and mailNickname should be structured. Please refer to docs to discover how to structure a valid requirement."
                }
            ]
        }
    ]
}
```

### Step 2: Create the tenant-wide group prefix policy

#### Request

The following request specifies only the `PrefixSuffixNamingRequirement` setting. The request creates the group setting and assigns default values to other settings in the `Group.Unified` template.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```msgraph
POST https://graph.microsoft.com/v1.0/groupSettings

{
    "templateId": "62375ab9-6b52-47ed-826b-58e47e0e304b",
    "values": [
        {
            "name": "PrefixSuffixNamingRequirement",
            "value": "[Contoso-][GroupName]"
        }
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.GroupSettingTemplates.GetAsync();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
groupSettingTemplates, err := graphClient.GroupSettingTemplates().Get(context.Background(), nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

GroupSettingTemplateCollectionResponse result = graphClient.groupSettingTemplates().get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let groupSettingTemplates = await client.api('/groupSettingTemplates')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->groupSettingTemplates()->get()->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Groups

Get-MgGroupSettingTemplateGroupSettingTemplate
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.group_setting_templates.get()
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#groupSettings/$entity",
    "id": "98208f14-04ff-4a4e-9a67-3dcb5fa6fd6f",
    "displayName": null,
    "templateId": "62375ab9-6b52-47ed-826b-58e47e0e304b",
    "values": [
        {
            "name": "PrefixSuffixNamingRequirement",
            "value": "[Contoso-][GroupName]"
        }
    ]
}
```

## Related content

- [groupSettingTemplate resource type](https://learn.microsoft.com/en-us/graph/api/resources/groupsettingtemplate)
- [groupSettings resource type](https://learn.microsoft.com/en-us/graph/api/resources/groupsetting)
