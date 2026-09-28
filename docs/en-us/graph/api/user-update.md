<!-- Source: https://learn.microsoft.com/en-us/graph/api/user-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# Update user

Namespace: microsoft.graph

Update the properties of a [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) object. To use this API to update an [agentUser](https://learn.microsoft.com/en-us/graph/api/resources/agentuser?view=graph-rest-1.0), specify an **@odata.type** property with a value of `#microsoft.graph.agentUser` in the request body.

- Not all properties can be updated by Member or Guest users with their default permissions without administrator roles. [Compare member and guest default permissions](https://learn.microsoft.com/en-us/azure/active-directory/fundamentals/users-default-permissions?context=graph/context#compare-member-and-guest-default-permissions) to see properties they can manage.
- Microsoft Entra External ID in external tenants can also use this API operation to update their details. See [Default user permissions in external tenants](https://learn.microsoft.com/en-us/graph/api/resources/users?view=graph-rest-1.0#default-user-permissions-in-external-tenants) for the list of properties they can update.
- For synced users, the ability to update certain properties is additionally determined by the source of authority and whether synchronization is enabled.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | User.ReadUpdate.All | User.ReadWrite.All, Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | User.ReadWrite | Not available. |
| Application | User.ReadUpdate.All | User.ReadWrite.All, Directory.ReadWrite.All |

### Permissions for specific scenarios

- *User.ReadWrite* is the least privileged permission to update details for the signed-in user.
- Your personal Microsoft account must be tied to a Microsoft Entra tenant to update your profile with the *User.ReadWrite* delegated permission on a personal Microsoft account.
- To update the **employeeLeaveDateTime** property:

  - In delegated scenarios, the admin needs the *Global Administrator* role; the app must be granted the *User.Read.All* and *User-LifeCycleInfo.ReadWrite.All* delegated permissions.
  - In app-only scenarios with Microsoft Graph permissions, the app must be granted the *User.Read.All* and *User-LifeCycleInfo.ReadWrite.All* permissions.

- To update the **customSecurityAttributes** property:

  - In delegated scenarios, the admin must be assigned the *Attribute Assignment Administrator* role and the app granted the *CustomSecAttributeAssignment.ReadWrite.All* permission.
  - In app-only scenarios with Microsoft Graph permissions, the app must be granted the *CustomSecAttributeAssignment.ReadWrite.All* permission.

- *User-Mail.ReadWrite.All* is the least privileged permission to update the **otherMails** property.
- *User-PasswordProfile.ReadWrite.All* is the least privileged permission to update the **passwordProfile** property.
- *User-Phone.ReadWrite.All* is the least privileged permission to update the **businessPhones** and **mobilePhone** properties.
- *User.EnableDisableAccount.All* + *User.Read.All* is the least privileged combination of permissions to update the **accountEnabled** property.
- *User.ManageIdentities.All* is *required* to update the **identities** property.

## HTTP request

Update your own user properties.

Note

Calling the `/me` endpoint requires a signed-in user and therefore a delegated permission. Application permissions aren't supported when using the `/me` endpoint.

```http
PATCH /me
```

Update another user's properties.

```http
PATCH /users/{id | userPrincipalName}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

To use this API to update an [agentUser](https://learn.microsoft.com/en-us/graph/api/resources/agentuser?view=graph-rest-1.0), you must specify the **@odata.type** as `#microsoft.graph.agentUser` in the request body.

| Property | Type | Description |
| :--- | :--- | :--- |
| aboutMe | String | A freeform text entry field for the user to describe themselves. |
| accountEnabled | Boolean | `true` if the account is enabled; otherwise, `false`. This property is required when a user is created.  <br><br><br><li><em>User.EnableDisableAccount.All</em> + <em>User.Read.All</em> is the least privileged combination of permissions required to update this property. </li><br><br><li> In delegated scenarios, <em>Privileged Authentication Administrator</em> is the least privileged role that&#39;s allowed to update this property for <em>all</em> administrators in the tenant. In general, the signed-in user must have a higher privileged administrator role as indicated in <a href="https://learn.microsoft.com/en-us/graph/api/resources/users?view=graph-rest-1.0#who-can-perform-sensitive-actions" data-linktype="relative-path">Who can perform sensitive actions</a>. </li><br><br><li> In app-only scenarios in addition to Microsoft Graph permissions, the app must be assigned a higher privileged administrator role as indicated in <a href="https://learn.microsoft.com/en-us/graph/api/resources/users?view=graph-rest-1.0#who-can-perform-sensitive-actions" data-linktype="relative-path">Who can perform sensitive actions</a>.</li> |
| ageGroup | [ageGroup](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0#agegroup-values) | Sets the age group of the user. Allowed values: `null`, `Minor`, `NotAdult`, and `Adult`. Refer to the [legal age group property definitions](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0#legal-age-group-property-definitions) for further information. |
| birthday | DateTimeOffset | The birthday of the user. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| businessPhones | String collection | The telephone numbers for the user. **NOTE:** Although this is a string collection, only one number can be set for this property. *User-Phone.ReadWrite.All* is the least privileged permission to update this property. |
| city | String | The city in which the user is located. |
| companyName | String | The name of the company that the user is associated. This property can be useful for describing the company that an external user comes from. The maximum length is 64 characters. |
| consentProvidedForMinor | [consentProvidedForMinor](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0#consentprovidedforminor-values) | Sets whether consent has been obtained for minors. Allowed values: `null`, `Granted`, `Denied` and `NotRequired`. Refer to the [legal age group property definitions](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0#legal-age-group-property-definitions) for further information. |
| country | String | The country/region in which the user is located; for example, `US` or `UK`. |
| customSecurityAttributes | [customSecurityAttributeValue](https://learn.microsoft.com/en-us/graph/api/resources/customsecurityattributevalue?view=graph-rest-1.0) | An open complex type that holds the value of a custom security attribute that is assigned to a directory object.  <br><br><br><li>To update this property in delegated scenarios, the calling principal must be assigned the Attribute Assignment Administrator role and the app granted the <em>CustomSecAttributeAssignment.ReadWrite.All</em> delegated permission.</li><br><br><li>To update this property in app-only scenarios with Microsoft Graph permissions, the app must be granted the <em>CustomSecAttributeAssignment.ReadWrite.All</em> application permission.</li> |
| department | String | The name for the department in which the user works. |
| displayName | String | The name displayed in the address book for the user. This is usually the combination of the user's first name, middle initial, and last name. This property is required when a user is created and it can't be cleared during updates. |
| employeeId | String | The employee identifier assigned to the user by the organization. The maximum length is 16 characters. |
| employeeType | String | Captures enterprise worker type. For example, `Employee`, `Contractor`, `Consultant`, or `Vendor`. Returned only on `$select`. |
| givenName | String | The given name \(first name\) of the user. |
| employeeHireDate | DateTimeOffset | The hire date of the user. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| employeeLeaveDateTime | DateTimeOffset | The date and time when the user left or will leave the organization. The timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`.  <br><br><br><li> To update this property, the calling app must be assigned the <em>User-LifeCycleInfo.Read.All</em> and <em>User.Read.All</em> permissions. </li><br><br><li> To update this property in delegated scenarios, the admin needs the Global Administrator role.</li> |
| employeeOrgData | [employeeOrgData](https://learn.microsoft.com/en-us/graph/api/resources/employeeorgdata?view=graph-rest-1.0) | Represents organization data \(for example, division and costCenter\) associated with a user. Include both property values when updating **employeeOrgData**; if you omit any, the system sets them to `null`. |
| identities | [objectIdentity](https://learn.microsoft.com/en-us/graph/api/resources/objectidentity?view=graph-rest-1.0) collection | Represents the identities that can be used to sign in to this user account. An identity can be provided by Microsoft, by organizations, or by social identity providers such as Facebook, Google, and Microsoft, and tied to a user account. Any update to **identities** replaces the entire collection and you must supply the userPrincipalName **signInType** identity in the collection.  <br>  <br>**NOTE:** Adding a [B2C local account](https://learn.microsoft.com/en-us/graph/api/resources/objectidentity?view=graph-rest-1.0) to an existing **user** object isn't allowed, unless the **user** object already contains a local account identity. |
| interests | String collection | A list for the user to describe their interests. |
| jobTitle | String | The user's job title. |
| mail | String | The SMTP address for the user, for example, `jeff@contoso.com`. Changes to this property also update the user's **proxyAddresses** collection to include the value as an SMTP address. For Azure AD B2C accounts, this property can be updated up to only 10 times with unique SMTP addresses. Can't be updated to `null`. |
| mailNickname | String | The mail alias for the user. This property must be specified when a user is created. |
| mobilePhone | String | The primary cellular telephone number for the user.  <br><br><br><li><em>User-Phone.ReadWrite.All</em> is the least privileged permission to update this property. </li><br><br><li> In delegated scenarios, <em>Privileged Authentication Administrator</em> is the least privileged role that&#39;s allowed to update this property for <em>all</em> administrators in the tenant. In general, the signed-in user must have a higher privileged administrator role as indicated in <a href="https://learn.microsoft.com/en-us/graph/api/resources/users?view=graph-rest-1.0#who-can-perform-sensitive-actions" data-linktype="relative-path">Who can perform sensitive actions</a>. </li><br><br><li> In app-only scenarios in addition to Microsoft Graph permissions, the app must be assigned a higher privileged administrator role as indicated in <a href="https://learn.microsoft.com/en-us/graph/api/resources/users?view=graph-rest-1.0#who-can-perform-sensitive-actions" data-linktype="relative-path">Who can perform sensitive actions</a>.</li> |
| mySite | String | The URL for the user's personal site. |
| officeLocation | String | The office location in the user's place of business. |
| onPremisesExtensionAttributes | [onPremisesExtensionAttributes](https://learn.microsoft.com/en-us/graph/api/resources/onpremisesextensionattributes?view=graph-rest-1.0) | Contains extensionAttributes 1-15 for the user. The individual extension attributes aren't selectable or filterable. For an `onPremisesSyncEnabled` user, the source of authority for this set of properties is the on-premises and is read-only. These extension attributes are also known as Exchange custom attributes 1-15. |
| onPremisesImmutableId | String | This property is used to associate an on-premises Active Directory user account to their Microsoft Entra user object. This property must be specified when creating a new user account in the Graph if you're using a federated domain for the user's **userPrincipalName** \(UPN\) property. **Important:** The **$** and **\_** characters can't be used when specifying this property. |
| otherMails | String collection | A list of additional email addresses for the user; for example: `["bob@contoso.com", "Robert@fabrikam.com"]`. To update this property, pass in all the email addresses that you want the user to have; otherwise, existing values get overwritten by the values you specify. Can store up to 250 values, each with a limit of 250 characters.  <br>  <br><br><br><li><em>User-Mail.ReadWrite.All</em> is the least privileged permission to update this property. </li><br><br><li> In delegated scenarios, <em>Privileged Authentication Administrator</em> is the least privileged role that&#39;s allowed to update this property for <em>all</em> administrators in the tenant. In general, the signed-in user must have a higher privileged administrator role as indicated in <a href="https://learn.microsoft.com/en-us/graph/api/resources/users?view=graph-rest-1.0#who-can-perform-sensitive-actions" data-linktype="relative-path">Who can perform sensitive actions</a>. </li><br><br><li> In app-only scenarios in addition to Microsoft Graph permissions, the app must be assigned a higher privileged administrator role as indicated in <a href="https://learn.microsoft.com/en-us/graph/api/resources/users?view=graph-rest-1.0#who-can-perform-sensitive-actions" data-linktype="relative-path">Who can perform sensitive actions</a>.</li> |
| passwordPolicies | String | Specifies password policies for the user. This value is an enumeration with one possible value being `DisableStrongPassword`, which allows weaker passwords than the default policy to be specified. `DisablePasswordExpiration` can also be specified. The two can be specified together; for example: `DisablePasswordExpiration, DisableStrongPassword`. |
| passwordProfile | [passwordProfile](https://learn.microsoft.com/en-us/graph/api/resources/passwordprofile?view=graph-rest-1.0) | Specifies the password profile for the user. The profile contains the user's password. The password in the profile must satisfy minimum requirements as specified by the **passwordPolicies** property. By default, a strong password is required. As a best practice, always set the **forceChangePasswordNextSignIn** to `true`. This can't be used for federated users.  <br><br><br><li> <em>User-PasswordProfile.ReadWrite.All</em> is the least privileged permission to update this property. </li><br><br><li> In delegated scenarios, the <em>User Administrator</em> <a href="https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json" data-linktype="absolute-path">Microsoft Entra role</a> is the least privileged admin role supported to update this property for nonadmin users. <em>Privileged Authentication Administrator</em> is the least privileged role that&#39;s allowed to update this property for <em>all</em> administrators in the tenant. In general, the signed-in user must have a higher privileged administrator role as indicated in <a href="https://learn.microsoft.com/en-us/graph/api/resources/users?view=graph-rest-1.0#who-can-reset-passwords" data-linktype="relative-path">Who can reset passwords</a>.</li><br><br><li> In app-only scenarios, the calling app must be assigned a supported permission <em>and</em> at least the <em>User Administrator</em> <a href="https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json" data-linktype="absolute-path">Microsoft Entra role</a>.</li> |
| pastProjects | String collection | A list for the user to enumerate their past projects. |
| postalCode | String | The postal code for the user's postal address. The postal code is specific to the user's country/region. In the United States of America, this attribute contains the ZIP code. |
| preferredLanguage | String | The preferred language for the user. Should follow ISO 639-1 Code; for example, `en-US`. |
| responsibilities | String collection | A list for the user to enumerate their responsibilities. |
| schools | String collection | A list for the user to enumerate the schools they attended. |
| skills | String collection | A list for the user to enumerate their skills. |
| state | String | The state or province in the user's address. |
| streetAddress | String | The street address of the user's place of business. |
| surname | String | The user's surname \(family name or last name\). |
| usageLocation | String | A two letter country code \(ISO standard 3166\). Required for users that will be assigned licenses due to legal requirement to check for availability of services in countries/regions. Examples include: `US`, `JP`, and `GB`. Not nullable. |
| userPrincipalName | String | The user principal name \(UPN\) of the user. The UPN is an Internet-style sign-in name for the user based on the Internet standard RFC 822. By convention, this should map to the user's email name. The general format is alias@domain, where domain must be present in the tenant's collection of verified domains. The verified domains for the tenant can be accessed from the **verifiedDomains** property of [organization](https://learn.microsoft.com/en-us/graph/api/resources/organization?view=graph-rest-1.0).  <br>NOTE: This property can't contain accent characters. Only the following characters are allowed `A - Z`, `a - z`, `0 - 9`, ` ' . - _ ! # ^ ~`. For the complete list of allowed characters, see [username policies](https://learn.microsoft.com/en-us/azure/active-directory/authentication/concept-sspr-policy#userprincipalname-policies-that-apply-to-all-user-accounts). |
| userType | String | A string value that can be used to classify user types in your directory, such as `Member` and `Guest`. |

Note

- The following properties cannot be updated by an app with only application permissions: **aboutMe**, **birthday**, **employeeHireDate**, **interests**, **mySite**, **pastProjects**, **responsibilities**, **schools**, and **skills**.
- To update the following properties, you must specify them in their own PATCH request, without including the other properties: **aboutMe**, **birthday**, **interests**, **mySite**, **pastProjects**, **responsibilities**, **schools**, and **skills**.

### Manage extensions and associated data

Use this API to manage the directory, schema, and open extensions and their data for users, as follows:

- Add, update, and store data in the extensions for an existing user
- For directory and schema extensions, remove any stored data by setting the value of the custom extension property to `null`. For open extensions, use the [Delete open extension](https://learn.microsoft.com/en-us/graph/api/opentypeextension-delete) API.

## Response

If successful, this method returns a `204 No Content` response code.

## Example

### Example 1: Update properties of the signed-in user

#### Request

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
PATCH https://graph.microsoft.com/v1.0/me
Content-type: application/json

{
  "businessPhones": [
    "+1 425 555 0109"
  ],
  "officeLocation": "18/2111"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new User
{
	BusinessPhones = new List<string>
	{
		"+1 425 555 0109",
	},
	OfficeLocation = "18/2111",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.PatchAsync(requestBody);
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

requestBody := graphmodels.NewUser()
businessPhones := []string {
	"+1 425 555 0109",
}
requestBody.SetBusinessPhones(businessPhones)
officeLocation := "18/2111"
requestBody.SetOfficeLocation(&officeLocation) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
me, err := graphClient.Me().Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

User user = new User();
LinkedList<String> businessPhones = new LinkedList<String>();
businessPhones.add("+1 425 555 0109");
user.setBusinessPhones(businessPhones);
user.setOfficeLocation("18/2111");
User result = graphClient.me().patch(user);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const user = {
  businessPhones: [
    '+1 425 555 0109'
  ],
  officeLocation: '18/2111'
};

await client.api('/me')
	.update(user);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\User;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new User();
$requestBody->setBusinessPhones(['+1 425 555 0109', 	]);
$requestBody->setOfficeLocation('18/2111');

$result = $graphServiceClient->me()->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Users

$params = @{
	businessPhones = @(
	"+1 425 555 0109"
)
officeLocation = "18/2111"
}

# A UPN can also be used as -UserId.
Update-MgUser -UserId $userId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.user import User
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = User(
	business_phones = [
		"+1 425 555 0109",
	],
	office_location = "18/2111",
)

result = await graph_client.me.patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```

### Example 2: Update properties of the specified user

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
PATCH https://graph.microsoft.com/v1.0/users/{id}
Content-type: application/json

{
  "businessPhones": [
    "+1 425 555 0109"
  ],
  "officeLocation": "18/2111"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new User
{
	BusinessPhones = new List<string>
	{
		"+1 425 555 0109",
	},
	OfficeLocation = "18/2111",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewUser()
businessPhones := []string {
	"+1 425 555 0109",
}
requestBody.SetBusinessPhones(businessPhones)
officeLocation := "18/2111"
requestBody.SetOfficeLocation(&officeLocation) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
users, err := graphClient.Users().ByUserId("user-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

User user = new User();
LinkedList<String> businessPhones = new LinkedList<String>();
businessPhones.add("+1 425 555 0109");
user.setBusinessPhones(businessPhones);
user.setOfficeLocation("18/2111");
User result = graphClient.users().byUserId("{user-id}").patch(user);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const user = {
  businessPhones: [
    '+1 425 555 0109'
  ],
  officeLocation: '18/2111'
};

await client.api('/users/{id}')
	.update(user);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\User;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new User();
$requestBody->setBusinessPhones(['+1 425 555 0109', 	]);
$requestBody->setOfficeLocation('18/2111');

$result = $graphServiceClient->users()->byUserId('user-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Users

$params = @{
	businessPhones = @(
	"+1 425 555 0109"
)
officeLocation = "18/2111"
}

Update-MgUser -UserId $userId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.user import User
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = User(
	business_phones = [
		"+1 425 555 0109",
	],
	office_location = "18/2111",
)

result = await graph_client.users.by_user_id('user-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```

### Example 3: Update the passwordProfile of a user and reset their password

The following example shows a request to reset the password of another user. As a best practice, always set the **forceChangePasswordNextSignIn** to `true`.

- *User-PasswordProfile.ReadWrite.All* is the least privileged permission to update the **passwordProfile** property.
- In delegated scenarios, the calling app must be assigned a supported permission *and* the signed in user assigned with supported Microsoft Entra role.

  - *Privileged Authentication Administrator* is the least privileged role that's allowed to update this property for *all* administrators in the tenant.
  - In general, the signed-in user must have a higher privileged administrator role as indicated in [Who can reset passwords](https://learn.microsoft.com/en-us/graph/api/resources/users#who-can-reset-passwords).

- In app-only scenarios using Microsoft Graph application permissions, *User-PasswordProfile.ReadWrite.All* is the least privileged permission.

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
PATCH https://graph.microsoft.com/v1.0/users/{id}
Content-type: application/json

{
  "passwordProfile": {
    "forceChangePasswordNextSignIn": false,
    "password": "xWwvJ]6NMw+bWH-d"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new User
{
	PasswordProfile = new PasswordProfile
	{
		ForceChangePasswordNextSignIn = false,
		Password = "xWwvJ]6NMw+bWH-d",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewUser()
passwordProfile := graphmodels.NewPasswordProfile()
forceChangePasswordNextSignIn := false
passwordProfile.SetForceChangePasswordNextSignIn(&forceChangePasswordNextSignIn) 
password := "xWwvJ]6NMw+bWH-d"
passwordProfile.SetPassword(&password) 
requestBody.SetPasswordProfile(passwordProfile)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
users, err := graphClient.Users().ByUserId("user-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

User user = new User();
PasswordProfile passwordProfile = new PasswordProfile();
passwordProfile.setForceChangePasswordNextSignIn(false);
passwordProfile.setPassword("xWwvJ]6NMw+bWH-d");
user.setPasswordProfile(passwordProfile);
User result = graphClient.users().byUserId("{user-id}").patch(user);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const user = {
  passwordProfile: {
    forceChangePasswordNextSignIn: false,
    password: 'xWwvJ]6NMw+bWH-d'
  }
};

await client.api('/users/{id}')
	.update(user);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\User;
use Microsoft\Graph\Generated\Models\PasswordProfile;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new User();
$passwordProfile = new PasswordProfile();
$passwordProfile->setForceChangePasswordNextSignIn(false);
$passwordProfile->setPassword('xWwvJ]6NMw+bWH-d');
$requestBody->setPasswordProfile($passwordProfile);

$result = $graphServiceClient->users()->byUserId('user-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Users

$params = @{
	passwordProfile = @{
		forceChangePasswordNextSignIn = $false
		password = "xWwvJ]6NMw+bWH-d"
	}
}

Update-MgUser -UserId $userId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.user import User
from msgraph.generated.models.password_profile import PasswordProfile
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = User(
	password_profile = PasswordProfile(
		force_change_password_next_sign_in = False,
		password = "xWwvJ]6NMw+bWH-d",
	),
)

result = await graph_client.users.by_user_id('user-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

```http
HTTP/1.1 204 No Content
```

### Example 4: Add or update the values of a schema extension for a user

You can update or assign a value to a single property or all properties in the extension.

#### Request

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```msgraph
PATCH https://graph.microsoft.com/v1.0/users/4562bcc8-c436-4f95-b7c0-4f8ce89dca5e
Content-type: application/json

{
    "ext55gb1l09_msLearnCourses": {
        "courseType": "Admin"
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new User
{
	AdditionalData = new Dictionary<string, object>
	{
		{
			"ext55gb1l09_msLearnCourses" , new UntypedObject(new Dictionary<string, UntypedNode>
			{
				{
					"courseType", new UntypedString("Admin")
				},
			})
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewUser()
additionalData := map[string]interface{}{
ext55gb1l09_msLearnCourses := graph.New()
courseType := "Admin"
ext55gb1l09_msLearnCourses.SetCourseType(&courseType) 
	requestBody.SetExt55gb1l09_msLearnCourses(ext55gb1l09_msLearnCourses)
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
users, err := graphClient.Users().ByUserId("user-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

User user = new User();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
 ext55gb1l09MsLearnCourses = new ();
ext55gb1l09MsLearnCourses.setCourseType("Admin");
additionalData.put("ext55gb1l09_msLearnCourses", ext55gb1l09MsLearnCourses);
user.setAdditionalData(additionalData);
User result = graphClient.users().byUserId("{user-id}").patch(user);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const user = {
    ext55gb1l09_msLearnCourses: {
        courseType: 'Admin'
    }
};

await client.api('/users/4562bcc8-c436-4f95-b7c0-4f8ce89dca5e')
	.update(user);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\User;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new User();
$additionalData = [
	'ext55gb1l09_msLearnCourses' => [
		'courseType' => 'Admin',
	],
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->users()->byUserId('user-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Users

$params = @{
	ext55gb1l09_msLearnCourses = @{
		courseType = "Admin"
	}
}

Update-MgUser -UserId $userId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.user import User
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = User(
	additional_data = {
			"ext55gb1l09_ms_learn_courses" : {
					"course_type" : "Admin",
			},
	}
)

result = await graph_client.users.by_user_id('user-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

To remove the value of the schema extension from the user object, set the **ext55gb1l09\_msLearnCourses** property to `null`.

#### Response

```http
HTTP/1.1 204 No Content
```

### Example 5: Assign a custom security attribute with a string value to a user

The following example shows how to assign a custom security attribute with a string value to a user.

- Attribute set: `Engineering`
- Attribute: `ProjectDate`
- Attribute data type: String
- Attribute value: `"2022-10-01"`

To assign custom security attributes, the calling principal must be assigned the Attribute Assignment Administrator role and must be granted the *CustomSecAttributeAssignment.ReadWrite.All* permission.

For examples of custom security attribute assignments, see [Examples: Assign, update, list, or remove custom security attribute assignments using the Microsoft Graph API](https://learn.microsoft.com/en-us/graph/custom-security-attributes-examples).

#### Request

- [HTTP](#tabpanel_5_http)
- [C#](#tabpanel_5_csharp)
- [Go](#tabpanel_5_go)
- [Java](#tabpanel_5_java)
- [JavaScript](#tabpanel_5_javascript)
- [PHP](#tabpanel_5_php)
- [PowerShell](#tabpanel_5_powershell)
- [Python](#tabpanel_5_python)

```http
PATCH https://graph.microsoft.com/v1.0/users/{id}
Content-type: application/json

{
    "customSecurityAttributes":
    {
        "Engineering":
        {
            "@odata.type":"#Microsoft.DirectoryServices.CustomSecurityAttributeValue",
            "ProjectDate":"2022-10-01"
        }
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new User
{
	CustomSecurityAttributes = new CustomSecurityAttributeValue
	{
		AdditionalData = new Dictionary<string, object>
		{
			{
				"Engineering" , new UntypedObject(new Dictionary<string, UntypedNode>
				{
					{
						"@odata.type", new UntypedString("#Microsoft.DirectoryServices.CustomSecurityAttributeValue")
					},
					{
						"projectDate", new UntypedString("2022-10-01")
					},
				})
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewUser()
customSecurityAttributes := graphmodels.NewCustomSecurityAttributeValue()
additionalData := map[string]interface{}{
engineering := graph.New()
projectDate := "2022-10-01"
engineering.SetProjectDate(&projectDate) 
	customSecurityAttributes.SetEngineering(engineering)
}
customSecurityAttributes.SetAdditionalData(additionalData)
requestBody.SetCustomSecurityAttributes(customSecurityAttributes)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
users, err := graphClient.Users().ByUserId("user-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

User user = new User();
CustomSecurityAttributeValue customSecurityAttributes = new CustomSecurityAttributeValue();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
 engineering = new ();
engineering.setOdataType("#Microsoft.DirectoryServices.CustomSecurityAttributeValue");
engineering.setProjectDate("2022-10-01");
additionalData.put("Engineering", engineering);
customSecurityAttributes.setAdditionalData(additionalData);
user.setCustomSecurityAttributes(customSecurityAttributes);
User result = graphClient.users().byUserId("{user-id}").patch(user);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const user = {
    customSecurityAttributes: 
    {
        Engineering: 
        {
            '@odata.type':'#Microsoft.DirectoryServices.CustomSecurityAttributeValue',
            ProjectDate: '2022-10-01'
        }
    }
};

await client.api('/users/{id}')
	.update(user);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\User;
use Microsoft\Graph\Generated\Models\CustomSecurityAttributeValue;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new User();
$customSecurityAttributes = new CustomSecurityAttributeValue();
$additionalData = [
	'Engineering' => [
		'@odata.type' => '#Microsoft.DirectoryServices.CustomSecurityAttributeValue',
		'projectDate' => '2022-10-01',
	],
];
$customSecurityAttributes->setAdditionalData($additionalData);
$requestBody->setCustomSecurityAttributes($customSecurityAttributes);

$result = $graphServiceClient->users()->byUserId('user-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Users

$params = @{
	customSecurityAttributes = @{
		Engineering = @{
			"@odata.type" = "#Microsoft.DirectoryServices.CustomSecurityAttributeValue"
			ProjectDate = "2022-10-01"
		}
	}
}

Update-MgUser -UserId $userId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.user import User
from msgraph.generated.models.custom_security_attribute_value import CustomSecurityAttributeValue
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = User(
	custom_security_attributes = CustomSecurityAttributeValue(
		additional_data = {
				"engineering" : {
						"@odata_type" : "#Microsoft.DirectoryServices.CustomSecurityAttributeValue",
						"project_date" : "2022-10-01",
				},
		}
	),
)

result = await graph_client.users.by_user_id('user-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

```http
HTTP/1.1 204 No Content
```

## Related content

- [Add custom data to resources using extensions](https://learn.microsoft.com/en-us/graph/extensibility-overview)
- [Add custom data to users using open extensions \(preview\)](https://learn.microsoft.com/en-us/graph/extensibility-open-users)
- [Add custom data to groups using schema extensions \(preview\)](https://learn.microsoft.com/en-us/graph/extensibility-schema-groups)
