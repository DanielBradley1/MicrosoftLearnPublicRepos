<!-- Source: https://learn.microsoft.com/en-us/graph/api/educationuser-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# Update educationUser

Namespace: microsoft.graph

Update the properties of an [educationUser](https://learn.microsoft.com/en-us/graph/api/resources/educationuser?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | EduRoster.ReadWrite.All | Not available. |

## HTTP request

```http
PATCH /education/me
PATCH /education/users/{id}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json |

## Request body

In the request body, supply the values for relevant fields that should be updated. Existing properties that aren't included in the request body maintains their previous values or be recalculated based on changes to other property values. For best performance, don't include existing values that haven't changed.

| Property | Type | Description |
| :--- | :--- | :--- |
| accountEnabled | Boolean | **True** if the account is enabled; otherwise, **false**. This property is required when a user is created. Supports $filter. |
| assignedLicenses | [assignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/assignedlicense?view=graph-rest-1.0) collection | The licenses that are assigned to the user. Not nullable. |
| assignedPlans | [assignedPlan](https://learn.microsoft.com/en-us/graph/api/resources/assignedplan?view=graph-rest-1.0) collection | The plans that are assigned to the user. Read-only. Not nullable. |
| businessPhones | String collection | The telephone numbers for the user. **Note:** Although this is a string collection, only one number can be set for this property. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Entity who created the user. |
| department | String | The name for the department in which the user works. Supports $filter. |
| displayName | String | The name displayed in the address book for the user. This is usually the combination of the user's first name, middle initial, and last name. This property is required when a user is created and it can't be cleared during updates. Supports $filter and $orderby. |
| externalSource | educationExternalSource | Where this user was created from. The possible values are: `sis`, `manual`. |
| externalSourceDetail | String | The name of the external source from which this resource was generated from. |
| givenName | String | The given name \(first name\) of the user. Supports $filter. |
| mail | String | The SMTP address for the user; for example, "jeff@contoso.com". Read-Only. Supports $filter. |
| mailingAddress | [physicalAddress](https://learn.microsoft.com/en-us/graph/api/resources/physicaladdress?view=graph-rest-1.0) | Mail address of user. |
| mailNickname | String | The mail alias for the user. This property must be specified when a user is created. Supports $filter. |
| middleName | String | The middle name of user. |
| mobilePhone | String | The primary cellular telephone number for the user. |
| onPremisesInfo | [educationOnPremisesInfo](https://learn.microsoft.com/en-us/graph/api/resources/educationonpremisesinfo?view=graph-rest-1.0) | Additional information used to associate the AAD user with its Active Directory counterpart. |
| passwordPolicies | String | Specifies password policies for the user. This value is an enumeration with one possible value being "DisableStrongPassword", which allows weaker passwords than the default policy to be specified. "DisablePasswordExpiration" can also be specified. The two can be specified together; for example: "DisablePasswordExpiration, DisableStrongPassword". |
| passwordProfile | [passwordProfile](https://learn.microsoft.com/en-us/graph/api/resources/passwordprofile?view=graph-rest-1.0) | Specifies the password profile for the user. The profile contains the user's password. This property is required when a user is created. The password in the profile must satisfy minimum requirements as specified by the **passwordPolicies** property. By default, a strong password is required. |
| preferredLanguage | String | The preferred language for the user. Should follow ISO 639-1 Code; for example, "en-US". |
| primaryRole | educationUserRole | Default role for a user. The user's role might be different in an individual class. The possible values are: `student`, `teacher`, `none`, `unknownFutureValue`. |
| provisionedPlans | [provisionedPlan](https://learn.microsoft.com/en-us/graph/api/resources/provisionedplan?view=graph-rest-1.0) collection | The plans that are provisioned for the user. Read-only. Not nullable. |
| residenceAddress | [physicalAddress](https://learn.microsoft.com/en-us/graph/api/resources/physicaladdress?view=graph-rest-1.0) | Address where user lives. |
| student | [educationStudent](https://learn.microsoft.com/en-us/graph/api/resources/educationstudent?view=graph-rest-1.0) | If the primary role is student, this block contains student specific data. |
| surname | String | The user's surname \(family name or last name\). Supports $filter. |
| teacher | [educationTeacher](https://learn.microsoft.com/en-us/graph/api/resources/educationteacher?view=graph-rest-1.0) | If the primary role is teacher, this block contains teacher specific data. |
| usageLocation | String | A two-letter country code \(ISO standard 3166\). Required for users who will be assigned licenses due to a legal requirement to check for availability of services in countries or regions. Examples include: "US", "JP", and "GB". Not nullable. Supports $filter. |
| userPrincipalName | String | The user principal name \(UPN\) of the user. |
| userType | String | A string value that can be used to classify user types in your directory, such as "Member" and "Guest". Supports $filter. |

## Response

If successful, this method returns a `200 OK` response code and updated [educationUser](https://learn.microsoft.com/en-us/graph/api/resources/educationuser?view=graph-rest-1.0) object in the response body.

## Example

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
PATCH https://graph.microsoft.com/v1.0/education/users/{user-id}
Content-type: application/json

{
  "displayName": "Rogelio Cazares",
  "givenName": "Rogelio",
  "middleName": "Fernando",
  "surname": "Cazares",
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new EducationUser
{
	DisplayName = "Rogelio Cazares",
	GivenName = "Rogelio",
	MiddleName = "Fernando",
	Surname = "Cazares",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Education.Users["{educationUser-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewEducationUser()
displayName := "Rogelio Cazares"
requestBody.SetDisplayName(&displayName) 
givenName := "Rogelio"
requestBody.SetGivenName(&givenName) 
middleName := "Fernando"
requestBody.SetMiddleName(&middleName) 
surname := "Cazares"
requestBody.SetSurname(&surname) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
users, err := graphClient.Education().Users().ByEducationUserId("educationUser-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

EducationUser educationUser = new EducationUser();
educationUser.setDisplayName("Rogelio Cazares");
educationUser.setGivenName("Rogelio");
educationUser.setMiddleName("Fernando");
educationUser.setSurname("Cazares");
EducationUser result = graphClient.education().users().byEducationUserId("{educationUser-id}").patch(educationUser);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const educationUser = {
  displayName: 'Rogelio Cazares',
  givenName: 'Rogelio',
  middleName: 'Fernando',
  surname: 'Cazares',
};

await client.api('/education/users/{user-id}')
	.update(educationUser);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\EducationUser;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EducationUser();
$requestBody->setDisplayName('Rogelio Cazares');
$requestBody->setGivenName('Rogelio');
$requestBody->setMiddleName('Fernando');
$requestBody->setSurname('Cazares');

$result = $graphServiceClient->education()->users()->byEducationUserId('educationUser-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Education

$params = @{
	displayName = "Rogelio Cazares"
	givenName = "Rogelio"
	middleName = "Fernando"
	surname = "Cazares"
}

Update-MgEducationUser -EducationUserId $educationUserId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.education_user import EducationUser
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EducationUser(
	display_name = "Rogelio Cazares",
	given_name = "Rogelio",
	middle_name = "Fernando",
	surname = "Cazares",
)

result = await graph_client.education.users.by_education_user_id('educationUser-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "id": "13020",
  "displayName": "Rogelio Cazares",
  "givenName": "Rogelio",
  "middleName": "Fernando",
  "surname": "Cazares",
  "mail": "rogelioC@contoso.com",
  "mobilePhone": "+1 (253) 555-0101",
  "createdBy": {
        "user": {
          "displayName": "Susana Rocha",
          "id": "14012",
        }
  },
  "externalSource": "sis",
  "mailingAddress": {
        "city": "Los Angeles",
        "countryOrRegion": "United States",
        "postalCode": "98055",
        "state": "CA",
        "street": "12345 Main St."
      },
  "primaryRole": "string",
  "residenceAddress": {
        "city": "Los Angeles",
        "countryOrRegion": "United States",
        "postalCode": "98055",
        "state": "CA",
        "street": "12345 Main St."
      },
  "student": {
      "primaryRole": "student",
      "externalId": "13005",
      "birthDate": "2001-01-01T00:00:00Z"
    }
}
```
