<!-- Source: https://learn.microsoft.com/en-us/graph/api/educationuser-post?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# Create educationUser

Namespace: microsoft.graph

Create a new [educationUser](https://learn.microsoft.com/en-us/graph/api/resources/educationuser?view=graph-rest-1.0) object.

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
POST /education/users
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [educationUser](https://learn.microsoft.com/en-us/graph/api/resources/educationuser?view=graph-rest-1.0) object.

The following table lists the properties that are required when you create the [educationUser](https://learn.microsoft.com/en-us/graph/api/resources/educationuser?view=graph-rest-1.0).

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
| externalSourceDetail | String | The name of the external source this resource was generated from. |
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
| primaryRole | educationUserRole | Default role for a user. The user's role might be different in an individual class. The possible values are: `student`, `teacher`, `none`. |
| provisionedPlans | [provisionedPlan](https://learn.microsoft.com/en-us/graph/api/resources/provisionedplan?view=graph-rest-1.0) collection | The plans that are provisioned for the user. Read-only. Not nullable. |
| residenceAddress | [physicalAddress](https://learn.microsoft.com/en-us/graph/api/resources/physicaladdress?view=graph-rest-1.0) | Address where user lives. |
| student | [educationStudent](https://learn.microsoft.com/en-us/graph/api/resources/educationstudent?view=graph-rest-1.0) | If the primary role is student, this block contains student specific data. |
| surname | String | The user's surname \(family name or last name\). Supports $filter. |
| teacher | [educationTeacher](https://learn.microsoft.com/en-us/graph/api/resources/educationteacher?view=graph-rest-1.0) | If the primary role is teacher, this block contains teacher specific data. |
| usageLocation | String | A two-letter country code \(ISO standard 3166\). Required for users who will be assigned licenses due to a legal requirement to check for availability of services in countries or regions. Examples include: "US", "JP", and "GB". Not nullable. Supports $filter. |
| userPrincipalName | String | The user principal name \(UPN\) of the user. |
| userType | String | A string value that can be used to classify user types in your directory, such as "Member" and "Guest". Supports $filter. |

## Response

If successful, this method returns a `201 Created` response code and an [educationUser](https://learn.microsoft.com/en-us/graph/api/resources/educationuser?view=graph-rest-1.0) object in the response body.

## Examples

### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/education/users
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.educationUser",
  "primaryRole": "String",
  "middleName": "String",
  "externalSource": "String",
  "externalSourceDetail": "String",
  "residenceAddress": {
    "@odata.type": "microsoft.graph.physicalAddress"
  },
  "mailingAddress": {
    "@odata.type": "microsoft.graph.physicalAddress"
  },
  "student": {
    "@odata.type": "microsoft.graph.educationStudent"
  },
  "teacher": {
    "@odata.type": "microsoft.graph.educationTeacher"
  },
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "accountEnabled": "Boolean",
  "assignedLicenses": [
    {
      "@odata.type": "microsoft.graph.assignedLicense"
    }
  ],
  "assignedPlans": [
    {
      "@odata.type": "microsoft.graph.assignedPlan"
    }
  ],
  "businessPhones": [
    "String"
  ],
  "department": "String",
  "displayName": "String",
  "givenName": "String",
  "mail": "String",
  "mailNickname": "String",
  "mobilePhone": "String",
  "passwordPolicies": "String",
  "passwordProfile": {
    "@odata.type": "microsoft.graph.passwordProfile"
  },
  "officeLocation": "String",
  "preferredLanguage": "String",
  "provisionedPlans": [
    {
      "@odata.type": "microsoft.graph.provisionedPlan"
    }
  ],
  "refreshTokensValidFromDateTime": "String (timestamp)",
  "showInAddressList": "Boolean",
  "surname": "String",
  "usageLocation": "String",
  "userPrincipalName": "String",
  "userType": "String",
  "onPremisesInfo": {
    "@odata.type": "microsoft.graph.educationOnPremisesInfo"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new EducationUser
{
	OdataType = "#microsoft.graph.educationUser",
	PrimaryRole = EducationUserRole.Student,
	MiddleName = "String",
	ExternalSource = EducationExternalSource.Sis,
	ExternalSourceDetail = "String",
	ResidenceAddress = new PhysicalAddress
	{
		OdataType = "microsoft.graph.physicalAddress",
	},
	MailingAddress = new PhysicalAddress
	{
		OdataType = "microsoft.graph.physicalAddress",
	},
	Student = new EducationStudent
	{
		OdataType = "microsoft.graph.educationStudent",
	},
	Teacher = new EducationTeacher
	{
		OdataType = "microsoft.graph.educationTeacher",
	},
	CreatedBy = new IdentitySet
	{
		OdataType = "microsoft.graph.identitySet",
	},
	AccountEnabled = boolean,
	AssignedLicenses = new List<AssignedLicense>
	{
		new AssignedLicense
		{
			OdataType = "microsoft.graph.assignedLicense",
		},
	},
	AssignedPlans = new List<AssignedPlan>
	{
		new AssignedPlan
		{
			OdataType = "microsoft.graph.assignedPlan",
		},
	},
	BusinessPhones = new List<string>
	{
		"String",
	},
	Department = "String",
	DisplayName = "String",
	GivenName = "String",
	Mail = "String",
	MailNickname = "String",
	MobilePhone = "String",
	PasswordPolicies = "String",
	PasswordProfile = new PasswordProfile
	{
		OdataType = "microsoft.graph.passwordProfile",
	},
	OfficeLocation = "String",
	PreferredLanguage = "String",
	ProvisionedPlans = new List<ProvisionedPlan>
	{
		new ProvisionedPlan
		{
			OdataType = "microsoft.graph.provisionedPlan",
		},
	},
	RefreshTokensValidFromDateTime = DateTimeOffset.Parse("String (timestamp)"),
	ShowInAddressList = boolean,
	Surname = "String",
	UsageLocation = "String",
	UserPrincipalName = "String",
	UserType = "String",
	OnPremisesInfo = new EducationOnPremisesInfo
	{
		OdataType = "microsoft.graph.educationOnPremisesInfo",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Education.Users.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  "time"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewEducationUser()
primaryRole := graphmodels.STRING_EDUCATIONUSERROLE 
requestBody.SetPrimaryRole(&primaryRole) 
middleName := "String"
requestBody.SetMiddleName(&middleName) 
externalSource := graphmodels.STRING_EDUCATIONEXTERNALSOURCE 
requestBody.SetExternalSource(&externalSource) 
externalSourceDetail := "String"
requestBody.SetExternalSourceDetail(&externalSourceDetail) 
residenceAddress := graphmodels.NewPhysicalAddress()
requestBody.SetResidenceAddress(residenceAddress)
mailingAddress := graphmodels.NewPhysicalAddress()
requestBody.SetMailingAddress(mailingAddress)
student := graphmodels.NewEducationStudent()
requestBody.SetStudent(student)
teacher := graphmodels.NewEducationTeacher()
requestBody.SetTeacher(teacher)
createdBy := graphmodels.NewIdentitySet()
requestBody.SetCreatedBy(createdBy)
accountEnabled := boolean
requestBody.SetAccountEnabled(&accountEnabled) 


assignedLicense := graphmodels.NewAssignedLicense()

assignedLicenses := []graphmodels.AssignedLicenseable {
	assignedLicense,
}
requestBody.SetAssignedLicenses(assignedLicenses)


assignedPlan := graphmodels.NewAssignedPlan()

assignedPlans := []graphmodels.AssignedPlanable {
	assignedPlan,
}
requestBody.SetAssignedPlans(assignedPlans)
businessPhones := []string {
	"String",
}
requestBody.SetBusinessPhones(businessPhones)
department := "String"
requestBody.SetDepartment(&department) 
displayName := "String"
requestBody.SetDisplayName(&displayName) 
givenName := "String"
requestBody.SetGivenName(&givenName) 
mail := "String"
requestBody.SetMail(&mail) 
mailNickname := "String"
requestBody.SetMailNickname(&mailNickname) 
mobilePhone := "String"
requestBody.SetMobilePhone(&mobilePhone) 
passwordPolicies := "String"
requestBody.SetPasswordPolicies(&passwordPolicies) 
passwordProfile := graphmodels.NewPasswordProfile()
requestBody.SetPasswordProfile(passwordProfile)
officeLocation := "String"
requestBody.SetOfficeLocation(&officeLocation) 
preferredLanguage := "String"
requestBody.SetPreferredLanguage(&preferredLanguage) 


provisionedPlan := graphmodels.NewProvisionedPlan()

provisionedPlans := []graphmodels.ProvisionedPlanable {
	provisionedPlan,
}
requestBody.SetProvisionedPlans(provisionedPlans)
refreshTokensValidFromDateTime , err := time.Parse(time.RFC3339, "String (timestamp)")
requestBody.SetRefreshTokensValidFromDateTime(&refreshTokensValidFromDateTime) 
showInAddressList := boolean
requestBody.SetShowInAddressList(&showInAddressList) 
surname := "String"
requestBody.SetSurname(&surname) 
usageLocation := "String"
requestBody.SetUsageLocation(&usageLocation) 
userPrincipalName := "String"
requestBody.SetUserPrincipalName(&userPrincipalName) 
userType := "String"
requestBody.SetUserType(&userType) 
onPremisesInfo := graphmodels.NewEducationOnPremisesInfo()
requestBody.SetOnPremisesInfo(onPremisesInfo)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
users, err := graphClient.Education().Users().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

EducationUser educationUser = new EducationUser();
educationUser.setOdataType("#microsoft.graph.educationUser");
educationUser.setPrimaryRole(EducationUserRole.Student);
educationUser.setMiddleName("String");
educationUser.setExternalSource(EducationExternalSource.Sis);
educationUser.setExternalSourceDetail("String");
PhysicalAddress residenceAddress = new PhysicalAddress();
residenceAddress.setOdataType("microsoft.graph.physicalAddress");
educationUser.setResidenceAddress(residenceAddress);
PhysicalAddress mailingAddress = new PhysicalAddress();
mailingAddress.setOdataType("microsoft.graph.physicalAddress");
educationUser.setMailingAddress(mailingAddress);
EducationStudent student = new EducationStudent();
student.setOdataType("microsoft.graph.educationStudent");
educationUser.setStudent(student);
EducationTeacher teacher = new EducationTeacher();
teacher.setOdataType("microsoft.graph.educationTeacher");
educationUser.setTeacher(teacher);
IdentitySet createdBy = new IdentitySet();
createdBy.setOdataType("microsoft.graph.identitySet");
educationUser.setCreatedBy(createdBy);
educationUser.setAccountEnabled(boolean);
LinkedList<AssignedLicense> assignedLicenses = new LinkedList<AssignedLicense>();
AssignedLicense assignedLicense = new AssignedLicense();
assignedLicense.setOdataType("microsoft.graph.assignedLicense");
assignedLicenses.add(assignedLicense);
educationUser.setAssignedLicenses(assignedLicenses);
LinkedList<AssignedPlan> assignedPlans = new LinkedList<AssignedPlan>();
AssignedPlan assignedPlan = new AssignedPlan();
assignedPlan.setOdataType("microsoft.graph.assignedPlan");
assignedPlans.add(assignedPlan);
educationUser.setAssignedPlans(assignedPlans);
LinkedList<String> businessPhones = new LinkedList<String>();
businessPhones.add("String");
educationUser.setBusinessPhones(businessPhones);
educationUser.setDepartment("String");
educationUser.setDisplayName("String");
educationUser.setGivenName("String");
educationUser.setMail("String");
educationUser.setMailNickname("String");
educationUser.setMobilePhone("String");
educationUser.setPasswordPolicies("String");
PasswordProfile passwordProfile = new PasswordProfile();
passwordProfile.setOdataType("microsoft.graph.passwordProfile");
educationUser.setPasswordProfile(passwordProfile);
educationUser.setOfficeLocation("String");
educationUser.setPreferredLanguage("String");
LinkedList<ProvisionedPlan> provisionedPlans = new LinkedList<ProvisionedPlan>();
ProvisionedPlan provisionedPlan = new ProvisionedPlan();
provisionedPlan.setOdataType("microsoft.graph.provisionedPlan");
provisionedPlans.add(provisionedPlan);
educationUser.setProvisionedPlans(provisionedPlans);
OffsetDateTime refreshTokensValidFromDateTime = OffsetDateTime.parse("String (timestamp)");
educationUser.setRefreshTokensValidFromDateTime(refreshTokensValidFromDateTime);
educationUser.setShowInAddressList(boolean);
educationUser.setSurname("String");
educationUser.setUsageLocation("String");
educationUser.setUserPrincipalName("String");
educationUser.setUserType("String");
EducationOnPremisesInfo onPremisesInfo = new EducationOnPremisesInfo();
onPremisesInfo.setOdataType("microsoft.graph.educationOnPremisesInfo");
educationUser.setOnPremisesInfo(onPremisesInfo);
EducationUser result = graphClient.education().users().post(educationUser);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const educationUser = {
  '@odata.type': '#microsoft.graph.educationUser',
  primaryRole: 'String',
  middleName: 'String',
  externalSource: 'String',
  externalSourceDetail: 'String',
  residenceAddress: {
    '@odata.type': 'microsoft.graph.physicalAddress'
  },
  mailingAddress: {
    '@odata.type': 'microsoft.graph.physicalAddress'
  },
  student: {
    '@odata.type': 'microsoft.graph.educationStudent'
  },
  teacher: {
    '@odata.type': 'microsoft.graph.educationTeacher'
  },
  createdBy: {
    '@odata.type': 'microsoft.graph.identitySet'
  },
  accountEnabled: 'Boolean',
  assignedLicenses: [
    {
      '@odata.type': 'microsoft.graph.assignedLicense'
    }
  ],
  assignedPlans: [
    {
      '@odata.type': 'microsoft.graph.assignedPlan'
    }
  ],
  businessPhones: [
    'String'
  ],
  department: 'String',
  displayName: 'String',
  givenName: 'String',
  mail: 'String',
  mailNickname: 'String',
  mobilePhone: 'String',
  passwordPolicies: 'String',
  passwordProfile: {
    '@odata.type': 'microsoft.graph.passwordProfile'
  },
  officeLocation: 'String',
  preferredLanguage: 'String',
  provisionedPlans: [
    {
      '@odata.type': 'microsoft.graph.provisionedPlan'
    }
  ],
  refreshTokensValidFromDateTime: 'String (timestamp)',
  showInAddressList: 'Boolean',
  surname: 'String',
  usageLocation: 'String',
  userPrincipalName: 'String',
  userType: 'String',
  onPremisesInfo: {
    '@odata.type': 'microsoft.graph.educationOnPremisesInfo'
  }
};

await client.api('/education/users')
	.post(educationUser);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\EducationUser;
use Microsoft\Graph\Generated\Models\EducationUserRole;
use Microsoft\Graph\Generated\Models\EducationExternalSource;
use Microsoft\Graph\Generated\Models\PhysicalAddress;
use Microsoft\Graph\Generated\Models\EducationStudent;
use Microsoft\Graph\Generated\Models\EducationTeacher;
use Microsoft\Graph\Generated\Models\IdentitySet;
use Microsoft\Graph\Generated\Models\AssignedLicense;
use Microsoft\Graph\Generated\Models\AssignedPlan;
use Microsoft\Graph\Generated\Models\PasswordProfile;
use Microsoft\Graph\Generated\Models\ProvisionedPlan;
use Microsoft\Graph\Generated\Models\EducationOnPremisesInfo;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EducationUser();
$requestBody->setOdataType('#microsoft.graph.educationUser');
$requestBody->setPrimaryRole(new EducationUserRole('string'));
$requestBody->setMiddleName('String');
$requestBody->setExternalSource(new EducationExternalSource('string'));
$requestBody->setExternalSourceDetail('String');
$residenceAddress = new PhysicalAddress();
$residenceAddress->setOdataType('microsoft.graph.physicalAddress');
$requestBody->setResidenceAddress($residenceAddress);
$mailingAddress = new PhysicalAddress();
$mailingAddress->setOdataType('microsoft.graph.physicalAddress');
$requestBody->setMailingAddress($mailingAddress);
$student = new EducationStudent();
$student->setOdataType('microsoft.graph.educationStudent');
$requestBody->setStudent($student);
$teacher = new EducationTeacher();
$teacher->setOdataType('microsoft.graph.educationTeacher');
$requestBody->setTeacher($teacher);
$createdBy = new IdentitySet();
$createdBy->setOdataType('microsoft.graph.identitySet');
$requestBody->setCreatedBy($createdBy);
$requestBody->setAccountEnabled(boolean);
$assignedLicensesAssignedLicense1 = new AssignedLicense();
$assignedLicensesAssignedLicense1->setOdataType('microsoft.graph.assignedLicense');
$assignedLicensesArray []= $assignedLicensesAssignedLicense1;
$requestBody->setAssignedLicenses($assignedLicensesArray);

$assignedPlansAssignedPlan1 = new AssignedPlan();
$assignedPlansAssignedPlan1->setOdataType('microsoft.graph.assignedPlan');
$assignedPlansArray []= $assignedPlansAssignedPlan1;
$requestBody->setAssignedPlans($assignedPlansArray);

$requestBody->setBusinessPhones(['String', ]);
$requestBody->setDepartment('String');
$requestBody->setDisplayName('String');
$requestBody->setGivenName('String');
$requestBody->setMail('String');
$requestBody->setMailNickname('String');
$requestBody->setMobilePhone('String');
$requestBody->setPasswordPolicies('String');
$passwordProfile = new PasswordProfile();
$passwordProfile->setOdataType('microsoft.graph.passwordProfile');
$requestBody->setPasswordProfile($passwordProfile);
$requestBody->setOfficeLocation('String');
$requestBody->setPreferredLanguage('String');
$provisionedPlansProvisionedPlan1 = new ProvisionedPlan();
$provisionedPlansProvisionedPlan1->setOdataType('microsoft.graph.provisionedPlan');
$provisionedPlansArray []= $provisionedPlansProvisionedPlan1;
$requestBody->setProvisionedPlans($provisionedPlansArray);

$requestBody->setRefreshTokensValidFromDateTime(new \DateTime('String (timestamp)'));
$requestBody->setShowInAddressList(boolean);
$requestBody->setSurname('String');
$requestBody->setUsageLocation('String');
$requestBody->setUserPrincipalName('String');
$requestBody->setUserType('String');
$onPremisesInfo = new EducationOnPremisesInfo();
$onPremisesInfo->setOdataType('microsoft.graph.educationOnPremisesInfo');
$requestBody->setOnPremisesInfo($onPremisesInfo);

$result = $graphServiceClient->education()->users()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Education

$params = @{
	"@odata.type" = "#microsoft.graph.educationUser"
	primaryRole = "String"
	middleName = "String"
	externalSource = "String"
	externalSourceDetail = "String"
	residenceAddress = @{
		"@odata.type" = "microsoft.graph.physicalAddress"
	}
	mailingAddress = @{
		"@odata.type" = "microsoft.graph.physicalAddress"
	}
	student = @{
		"@odata.type" = "microsoft.graph.educationStudent"
	}
	teacher = @{
		"@odata.type" = "microsoft.graph.educationTeacher"
	}
	createdBy = @{
		"@odata.type" = "microsoft.graph.identitySet"
	}
	accountEnabled = "Boolean"
	assignedLicenses = @(
		@{
			"@odata.type" = "microsoft.graph.assignedLicense"
		}
	)
	assignedPlans = @(
		@{
			"@odata.type" = "microsoft.graph.assignedPlan"
		}
	)
	businessPhones = @(
	"String"
)
department = "String"
displayName = "String"
givenName = "String"
mail = "String"
mailNickname = "String"
mobilePhone = "String"
passwordPolicies = "String"
passwordProfile = @{
	"@odata.type" = "microsoft.graph.passwordProfile"
}
officeLocation = "String"
preferredLanguage = "String"
provisionedPlans = @(
	@{
		"@odata.type" = "microsoft.graph.provisionedPlan"
	}
)
refreshTokensValidFromDateTime = [System.DateTime]::Parse("String (timestamp)")
showInAddressList = "Boolean"
surname = "String"
usageLocation = "String"
userPrincipalName = "String"
userType = "String"
onPremisesInfo = @{
	"@odata.type" = "microsoft.graph.educationOnPremisesInfo"
}
}

New-MgEducationUser -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.education_user import EducationUser
from msgraph.generated.models.education_user_role import EducationUserRole
from msgraph.generated.models.education_external_source import EducationExternalSource
from msgraph.generated.models.physical_address import PhysicalAddress
from msgraph.generated.models.education_student import EducationStudent
from msgraph.generated.models.education_teacher import EducationTeacher
from msgraph.generated.models.identity_set import IdentitySet
from msgraph.generated.models.assigned_license import AssignedLicense
from msgraph.generated.models.assigned_plan import AssignedPlan
from msgraph.generated.models.password_profile import PasswordProfile
from msgraph.generated.models.provisioned_plan import ProvisionedPlan
from msgraph.generated.models.education_on_premises_info import EducationOnPremisesInfo
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EducationUser(
	odata_type = "#microsoft.graph.educationUser",
	primary_role = EducationUserRole.Student,
	middle_name = "String",
	external_source = EducationExternalSource.Sis,
	external_source_detail = "String",
	residence_address = PhysicalAddress(
		odata_type = "microsoft.graph.physicalAddress",
	),
	mailing_address = PhysicalAddress(
		odata_type = "microsoft.graph.physicalAddress",
	),
	student = EducationStudent(
		odata_type = "microsoft.graph.educationStudent",
	),
	teacher = EducationTeacher(
		odata_type = "microsoft.graph.educationTeacher",
	),
	created_by = IdentitySet(
		odata_type = "microsoft.graph.identitySet",
	),
	account_enabled = Boolean,
	assigned_licenses = [
		AssignedLicense(
			odata_type = "microsoft.graph.assignedLicense",
		),
	],
	assigned_plans = [
		AssignedPlan(
			odata_type = "microsoft.graph.assignedPlan",
		),
	],
	business_phones = [
		"String",
	],
	department = "String",
	display_name = "String",
	given_name = "String",
	mail = "String",
	mail_nickname = "String",
	mobile_phone = "String",
	password_policies = "String",
	password_profile = PasswordProfile(
		odata_type = "microsoft.graph.passwordProfile",
	),
	office_location = "String",
	preferred_language = "String",
	provisioned_plans = [
		ProvisionedPlan(
			odata_type = "microsoft.graph.provisionedPlan",
		),
	],
	refresh_tokens_valid_from_date_time = "String (timestamp)",
	show_in_address_list = Boolean,
	surname = "String",
	usage_location = "String",
	user_principal_name = "String",
	user_type = "String",
	on_premises_info = EducationOnPremisesInfo(
		odata_type = "microsoft.graph.educationOnPremisesInfo",
	),
)

result = await graph_client.education.users.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.educationUser",
  "id": "90eedea1-dea1-90ee-a1de-ee90a1deee90",
  "primaryRole": "String",
  "middleName": "String",
  "externalSource": "String",
  "externalSourceDetail": "String",
  "residenceAddress": {
    "@odata.type": "microsoft.graph.physicalAddress"
  },
  "mailingAddress": {
    "@odata.type": "microsoft.graph.physicalAddress"
  },
  "student": {
    "@odata.type": "microsoft.graph.educationStudent"
  },
  "teacher": {
    "@odata.type": "microsoft.graph.educationTeacher"
  },
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "accountEnabled": "Boolean",
  "assignedLicenses": [
    {
      "@odata.type": "microsoft.graph.assignedLicense"
    }
  ],
  "assignedPlans": [
    {
      "@odata.type": "microsoft.graph.assignedPlan"
    }
  ],
  "businessPhones": [
    "String"
  ],
  "department": "String",
  "displayName": "String",
  "givenName": "String",
  "mail": "String",
  "mailNickname": "String",
  "mobilePhone": "String",
  "passwordPolicies": "String",
  "passwordProfile": {
    "@odata.type": "microsoft.graph.passwordProfile"
  },
  "officeLocation": "String",
  "preferredLanguage": "String",
  "provisionedPlans": [
    {
      "@odata.type": "microsoft.graph.provisionedPlan"
    }
  ],
  "refreshTokensValidFromDateTime": "String (timestamp)",
  "showInAddressList": "Boolean",
  "surname": "String",
  "usageLocation": "String",
  "userPrincipalName": "String",
  "userType": "String",
  "onPremisesInfo": {
    "@odata.type": "microsoft.graph.educationOnPremisesInfo"
  }
}
```
