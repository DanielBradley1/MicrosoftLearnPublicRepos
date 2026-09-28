<!-- Source: https://learn.microsoft.com/en-us/graph/templates/terraform/reference/beta/users -->
<!-- Sitemap-Last-Modified: 2025-08-04 -->

# users

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

Note

Permissions for personal Microsoft accounts cannot be used to deploy Microsoft Graph resources declared in Terraform files.

### Read existing resources only

Choose the least privileged permission from the following table to read a `users` resource using the `msgraph_resource` data source.

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | User.Read | User.ReadWrite, User.ReadBasic.All, User.Read.All, User.ReadWrite.All, Directory.Read.All, Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | User.Read | User.ReadWrite |
| Application | User.Read.All | User.ReadWrite.All, Directory.Read.All, Directory.ReadWrite.All |

## Resource format

To create a `users` resource, add the following Terraform configuration to your Terraform configuration.

```terraform
resource "msgraph_resource" "symbolicname" {
  url = "users@beta"
  body = {
    aboutMe = "string"
    accountEnabled = bool
    ageGroup = "string"
    assignedLicenses = [
      {
        disabledPlans = "string"
        skuId = "string"
      }
    ]
    assignedPlans = [
      {
        assignedDateTime = "string"
        capabilityStatus = "string"
        service = "string"
        servicePlanId = "string"
      }
    ]
    authorizationInfo = {
      certificateUserIds = [
        "string"
      ]
    }
    birthday = "string"
    businessPhones = [
      "string"
    ]
    city = "string"
    companyName = "string"
    consentProvidedForMinor = "string"
    country = "string"
    createdDateTime = "string"
    creationType = "string"
    customSecurityAttributes = any
    deletedDateTime = "string"
    department = "string"
    deviceEnrollmentLimit = int
    displayName = "string"
    employeeHireDate = "string"
    employeeId = "string"
    employeeLeaveDateTime = "string"
    employeeOrgData = {
      costCenter = "string"
      division = "string"
    }
    employeeType = "string"
    externalUserState = "string"
    externalUserStateChangeDateTime = "string"
    faxNumber = "string"
    givenName = "string"
    hireDate = "string"
    id = "string"
    identities = [
      {
        issuer = "string"
        issuerAssignedId = "string"
        signInType = "string"
      }
    ]
    imAddresses = [
      "string"
    ]
    interests = [
      "string"
    ]
    isManagementRestricted = bool
    isResourceAccount = bool
    jobTitle = "string"
    lastPasswordChangeDateTime = "string"
    legalAgeGroupClassification = "string"
    licenseAssignmentStates = [
      {
        assignedByGroup = "string"
        disabledPlans = "string"
        error = "string"
        lastUpdatedDateTime = "string"
        skuId = "string"
        state = "string"
      }
    ]
    mail = "string"
    mailboxSettings = {
      archiveFolder = "string"
      automaticRepliesSetting = {
        externalAudience = "string"
        externalReplyMessage = "string"
        internalReplyMessage = "string"
        scheduledEndDateTime = {
          dateTime = "string"
          timeZone = "string"
        }
        scheduledStartDateTime = {
          dateTime = "string"
          timeZone = "string"
        }
        status = "string"
      }
      dateFormat = "string"
      delegateMeetingMessageDeliveryOptions = "string"
      language = {
        displayName = "string"
        locale = "string"
      }
      timeFormat = "string"
      timeZone = "string"
      userPurpose = "string"
      workingHours = {
        daysOfWeek = 'friday'
        endTime = "string"
        startTime = "string"
        timeZone = {
          name = "string"
        }
      }
    }
    mailNickname = "string"
    mobilePhone = "string"
    mySite = "string"
    officeLocation = "string"
    onPremisesDistinguishedName = "string"
    onPremisesDomainName = "string"
    onPremisesExtensionAttributes = {
      extensionAttribute1 = "string"
      extensionAttribute10 = "string"
      extensionAttribute11 = "string"
      extensionAttribute12 = "string"
      extensionAttribute13 = "string"
      extensionAttribute14 = "string"
      extensionAttribute15 = "string"
      extensionAttribute2 = "string"
      extensionAttribute3 = "string"
      extensionAttribute4 = "string"
      extensionAttribute5 = "string"
      extensionAttribute6 = "string"
      extensionAttribute7 = "string"
      extensionAttribute8 = "string"
      extensionAttribute9 = "string"
    }
    onPremisesImmutableId = "string"
    onPremisesLastSyncDateTime = "string"
    onPremisesProvisioningErrors = [
      {
        category = "string"
        occurredDateTime = "string"
        propertyCausingError = "string"
        value = "string"
      }
    ]
    onPremisesSamAccountName = "string"
    onPremisesSecurityIdentifier = "string"
    onPremisesSyncEnabled = bool
    onPremisesUserPrincipalName = "string"
    otherMails = [
      "string"
    ]
    passwordPolicies = "string"
    passwordProfile = {
      forceChangePasswordNextSignIn = bool
      forceChangePasswordNextSignInWithMfa = bool
      password = "string"
    }
    pastProjects = [
      "string"
    ]
    postalCode = "string"
    preferredDataLocation = "string"
    preferredLanguage = "string"
    preferredName = "string"
    print = any
    provisionedPlans = [
      {
        capabilityStatus = "string"
        provisioningStatus = "string"
        service = "string"
      }
    ]
    proxyAddresses = [
      "string"
    ]
    responsibilities = [
      "string"
    ]
    schools = [
      "string"
    ]
    securityIdentifier = "string"
    serviceProvisioningErrors = [
      {
        createdDateTime = "string"
        isResolved = bool
        serviceInstance = "string"
      }
    ]
    showInAddressList = bool
    signInActivity = {
      lastNonInteractiveSignInDateTime = "string"
      lastNonInteractiveSignInRequestId = "string"
      lastSignInDateTime = "string"
      lastSignInRequestId = "string"
      lastSuccessfulSignInDateTime = "string"
      lastSuccessfulSignInRequestId = "string"
    }
    signInSessionsValidFromDateTime = "string"
    skills = [
      "string"
    ]
    state = "string"
    streetAddress = "string"
    surname = "string"
    usageLocation = "string"
    userPrincipalName = "string"
    userType = "string"
  }
}
```

## Property values

### users

| Name | Description | Value |
| --- | --- | --- |
| aboutMe | A freeform text entry field for the user to describe themselves. | string |
| accountEnabled | true if the account is enabled; otherwise, false. This property is required when a user is created. | bool |
| ageGroup | Sets the age group of the user. Allowed values: null, Minor, NotAdult, and Adult. For more information, see legal age group property definitions. | string |
| apiVersion | The resource api version | 'beta' \(ReadOnly\) |
| assignedLicenses | The licenses that are assigned to the user, including inherited \(group-based\) licenses. This property doesn't differentiate between directly assigned and inherited licenses. Use the licenseAssignmentStates property to identify the directly assigned and inherited licenses. Not nullable. | [MicrosoftGraphAssignedLicense](#microsoftgraphassignedlicense)\[\] |
| assignedPlans | The plans that are assigned to the user. Read-only. Not nullable. | [MicrosoftGraphAssignedPlan](#microsoftgraphassignedplan)\[\] |
| authorizationInfo |  | [MicrosoftGraphAuthorizationInfo](#microsoftgraphauthorizationinfo) |
| birthday | The birthday of the user. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014, is 2014-01-01T00:00:00Z. | string |
| businessPhones | The telephone numbers for the user. NOTE: Although it's a string collection, only one number can be set for this property. Read-only for users synced from the on-premises directory. | string\[\] |
| city | The city where the user is located. Maximum length is 128 characters. | string |
| companyName | The name of the company that the user is associated with. This property can be useful for describing the company that a guest comes from. | string |
| consentProvidedForMinor | Sets whether consent was obtained for minors. Allowed values: null, Granted, Denied, and NotRequired. For more information, see legal age group property definitions. | string |
| country | The country or region where the user is located; for example, US or UK. Maximum length is 128 characters. | string |
| createdDateTime | The date and time the user was created, in ISO 8601 format and UTC. The value can't be modified and is automatically populated when the entity is created. Nullable. For on-premises users, the value represents when they were first created in Microsoft Entra ID. Property is null for some users created before June 2018 and on-premises users that were synced to Microsoft Entra ID before June 2018. Read-only. | string |
| creationType | Indicates whether the user account was created through one of the following methods: As a regular school or work account \(null\). As an external account \(Invitation\). As a local account for an Azure Active Directory B2C tenant \(LocalAccount\). Through self-service sign-up by an internal user using email verification \(EmailVerified\). Through self-service sign-up by a guest signing up through a link that is part of a user flow \(SelfServiceSignUp\). | string |
| customSecurityAttributes | An open complex type that holds the value of a custom security attribute that is assigned to a directory object. Nullable. The filter value is case-sensitive. To read this property, the calling app must be assigned the CustomSecAttributeAssignment.Read.All permission. To write this property, the calling app must be assigned the CustomSecAttributeAssignment.ReadWrite.All permissions. To read or write this property in delegated scenarios, the admin must be assigned the Attribute Assignment Administrator role. | any |
| deletedDateTime | Date and time when this object was deleted. Always null when the object hasn't been deleted. | string |
| department | The name of the department in which the user works. Maximum length is 64 characters. | string |
| deviceEnrollmentLimit | The limit on the maximum number of devices that the user is permitted to enroll. Allowed values are 5 or 1000. | int |
| displayName | The name displayed in the address book for the user. This value is usually the combination of the user's first name, middle initial, and family name. This property is required when a user is created and it can't be cleared during updates. Maximum length is 256 characters. | string |
| employeeHireDate | The date and time when the user was hired or will start work in a future hire. | string |
| employeeId | The employee identifier assigned to the user by the organization. The maximum length is 16 characters. | string |
| employeeLeaveDateTime | The date and time when the user left or will leave the organization. To read this property, the calling app must be assigned the User-LifeCycleInfo.Read.All permission. To write this property, the calling app must be assigned the User.Read.All and User-LifeCycleInfo.ReadWrite.All permissions. To read this property in delegated scenarios, the admin needs at least one of the following Microsoft Entra roles: Lifecycle Workflows Administrator \(least privilege\), Global Reader. To write this property in delegated scenarios, the admin needs the Global Administrator role. For more information, see Configure the employeeLeaveDateTime property for a user. | string |
| employeeOrgData | Represents organization data \(for example, division and costCenter\) associated with a user. | [MicrosoftGraphEmployeeOrgData](#microsoftgraphemployeeorgdata) |
| employeeType | Captures enterprise worker type. For example, Employee, Contractor, Consultant, or Vendor. | string |
| externalUserState | For a guest invited to the tenant using the invitation API, this property represents the invited user's invitation status. For invited users, the state can be PendingAcceptance or Accepted, or null for all other users. | string |
| externalUserStateChangeDateTime | Shows the timestamp for the latest change to the externalUserState property. | string |
| faxNumber | The fax number of the user. | string |
| givenName | The given name \(first name\) of the user. Maximum length is 64 characters. | string |
| hireDate | The hire date of the user. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014, is 2014-01-01T00:00:00Z. Note: This property is specific to SharePoint in Microsoft 365. We recommend using the native employeeHireDate property to set and update hire date values using Microsoft Graph APIs. | string |
| id | The unique identifier for an entity. Read-only. | string |
| identities | Represents the identities that can be used to sign in to this user account. Microsoft \(also known as a local account\), organizations, or social identity providers such as Facebook, Google, and Microsoft can provide identity and tie it to a user account. It might contain multiple items with the same signInType value. | [MicrosoftGraphObjectIdentity](#microsoftgraphobjectidentity)\[\] |
| imAddresses | The instant message voice-over IP \(VOIP\) session initiation protocol \(SIP\) addresses for the user. Read-only. | string\[\] |
| interests | A list for the user to describe their interests. | string\[\] |
| isManagementRestricted |  | bool |
| isResourceAccount | Don't use – reserved for future use. | bool |
| jobTitle | The user's job title. Maximum length is 128 characters. | string |
| lastPasswordChangeDateTime | The time when this Microsoft Entra user last changed their password or when their password was created, whichever date the latest action was performed. The date and time information uses ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is 2014-01-01T00:00:00Z. | string |
| legalAgeGroupClassification | Used by enterprise applications to determine the legal age group of the user. This property is read-only and calculated based on ageGroup and consentProvidedForMinor properties. Allowed values: null, Undefined, MinorWithOutParentalConsent, MinorWithParentalConsent, MinorNoParentalConsentRequired, NotAdult, and Adult. For more information, see legal age group property definitions. | string |
| licenseAssignmentStates | State of license assignments for this user. Also indicates licenses that are directly assigned or the user inherited through group memberships. Read-only. | [MicrosoftGraphLicenseAssignmentState](#microsoftgraphlicenseassignmentstate)\[\] |
| mail | The SMTP address for the user, for example, jeff@contoso.com. Changes to this property update the user's proxyAddresses collection to include the value as an SMTP address. This property can't contain accent characters. NOTE: We don't recommend updating this property for Azure AD B2C user profiles. Use the otherMails property instead. | string |
| mailboxSettings | Settings for the primary mailbox of the signed-in user. You can get or update settings for sending automatic replies to incoming messages, locale, and time zone. | [MicrosoftGraphMailboxSettings](#microsoftgraphmailboxsettings) |
| mailNickname | The mail alias for the user. This property must be specified when a user is created. Maximum length is 64 characters. | string |
| mobilePhone | The primary cellular telephone number for the user. Read-only for users synced from the on-premises directory. Maximum length is 64 characters. | string |
| mySite | The URL for the user's site. | string |
| officeLocation | The office location in the user's place of business. | string |
| onPremisesDistinguishedName | Contains the on-premises Active Directory distinguished name or DN. The property is only populated for customers who are synchronizing their on-premises directory to Microsoft Entra ID via Microsoft Entra Connect. Read-only. | string |
| onPremisesDomainName | Contains the on-premises domainFQDN, also called dnsDomainName synchronized from the on-premises directory. The property is only populated for customers who are synchronizing their on-premises directory to Microsoft Entra ID via Microsoft Entra Connect. Read-only. | string |
| onPremisesExtensionAttributes | Contains extensionAttributes1-15 for the user. These extension attributes are also known as Exchange custom attributes 1-15. Each attribute can store up to 1024 characters. For an onPremisesSyncEnabled user, the source of authority for this set of properties is the on-premises and is read-only. For a cloud-only user \(where onPremisesSyncEnabled is false\), these properties can be set during the creation or update of a user object. For a cloud-only user previously synced from on-premises Active Directory, these properties are read-only in Microsoft Graph but can be fully managed through the Exchange Admin Center or the Exchange Online V2 module in PowerShell. | [MicrosoftGraphOnPremisesExtensionAttributes](#microsoftgraphonpremisesextensionattributes) |
| onPremisesImmutableId | This property is used to associate an on-premises Active Directory user account to their Microsoft Entra user object. This property must be specified when creating a new user account in the Graph if you're using a federated domain for the user's userPrincipalName \(UPN\) property. NOTE: The $ and \_ characters can't be used when specifying this property. | string |
| onPremisesLastSyncDateTime | Indicates the last time at which the object was synced with the on-premises directory; for example: 2013-02-16T03:04:54Z. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is 2014-01-01T00:00:00Z. Read-only. | string |
| onPremisesProvisioningErrors | Errors when using Microsoft synchronization product during provisioning. | [MicrosoftGraphOnPremisesProvisioningError](#microsoftgraphonpremisesprovisioningerror)\[\] |
| onPremisesSamAccountName | Contains the on-premises samAccountName synchronized from the on-premises directory. The property is only populated for customers who are synchronizing their on-premises directory to Microsoft Entra ID via Microsoft Entra Connect. Read-only. | string |
| onPremisesSecurityIdentifier | Contains the on-premises security identifier \(SID\) for the user that was synchronized from on-premises to the cloud. Read-only. | string |
| onPremisesSyncEnabled | true if this user object is currently being synced from an on-premises Active Directory \(AD\); otherwise the user isn't being synced and can be managed in Microsoft Entra ID. Read-only. | bool |
| onPremisesUserPrincipalName | Contains the on-premises userPrincipalName synchronized from the on-premises directory. The property is only populated for customers who are synchronizing their on-premises directory to Microsoft Entra ID via Microsoft Entra Connect. Read-only. | string |
| otherMails | A list of other email addresses for the user; for example: \['bob@contoso.com', 'Robert@fabrikam.com'\]. Can store up to 250 values, each with a limit of 250 characters. NOTE: This property can't contain accent characters. | string\[\] |
| passwordPolicies | Specifies password policies for the user. This value is an enumeration with one possible value being DisableStrongPassword, which allows weaker passwords than the default policy to be specified. DisablePasswordExpiration can also be specified. The two might be specified together; for example: DisablePasswordExpiration, DisableStrongPassword. For more information on the default password policies, see Microsoft Entra password policies. | string |
| passwordProfile | Specifies the password profile for the user. The profile contains the user's password. This property is required when a user is created. The password in the profile must satisfy minimum requirements as specified by the passwordPolicies property. By default, a strong password is required. To update this property: User-PasswordProfile.ReadWrite.All is the least privileged permission to update this property. In delegated scenarios, the User Administrator Microsoft Entra role is the least privileged admin role supported to update this property for nonadmin users. Privileged Authentication Administrator is the least privileged role that's allowed to update this property for all administrators in the tenant. In general, the signed-in user must have a higher privileged administrator role as indicated in Who can reset passwords. In app-only scenarios, the calling app must be assigned a supported permission and at least the User Administrator Microsoft Entra role. | [MicrosoftGraphPasswordProfile](#microsoftgraphpasswordprofile) |
| pastProjects | A list for the user to enumerate their past projects. | string\[\] |
| postalCode | The postal code for the user's postal address. The postal code is specific to the user's country or region. In the United States of America, this attribute contains the ZIP code. Maximum length is 40 characters. | string |
| preferredDataLocation | The preferred data location for the user. For more information, see OneDrive Online Multi-Geo. | string |
| preferredLanguage | The preferred language for the user. The preferred language format is based on RFC 4646. The name is a combination of an ISO 639 two-letter lowercase culture code associated with the language, and an ISO 3166 two-letter uppercase subculture code associated with the country or region. Example: 'en-US', or 'es-ES'. | string |
| preferredName | The preferred name for the user. Not Supported. | string |
| print | Any object | any |
| provisionedPlans | The plans that are provisioned for the user. Read-only. Not nullable. | [MicrosoftGraphProvisionedPlan](#microsoftgraphprovisionedplan)\[\] |
| proxyAddresses | For example: \['SMTP: bob@contoso.com', 'smtp: bob@sales.contoso.com'\]. Changes to the mail property update this collection to include the value as an SMTP address. For more information, see mail and proxyAddresses properties. The proxy address prefixed with SMTP \(capitalized\) is the primary proxy address, while those addresses prefixed with smtp are the secondary proxy addresses. For Azure AD B2C accounts, this property has a limit of 10 unique addresses. Read-only in Microsoft Graph; you can update this property only through the Microsoft 365 admin center. Not nullable. | string\[\] |
| responsibilities | A list for the user to enumerate their responsibilities. | string\[\] |
| schools | A list for the user to enumerate the schools they attended. | string\[\] |
| securityIdentifier | Security identifier \(SID\) of the user, used in Windows scenarios. Read-only. | string |
| serviceProvisioningErrors | Errors published by a federated service describing a nontransient, service-specific error regarding the properties or link from a user object. | [MicrosoftGraphServiceProvisioningError](#microsoftgraphserviceprovisioningerror)\[\] |
| showInAddressList | Do not use in Microsoft Graph. Manage this property through the Microsoft 365 admin center instead. Represents whether the user should be included in the Outlook global address list. See Known issue. | bool |
| signInActivity | Get the last signed-in date and request ID of the sign-in for a given user. Note: Details for this property require a Microsoft Entra ID P1 or P2 license and the AuditLog.Read.All permission.This property isn't returned for a user who never signed in or last signed in before April 2020. | [MicrosoftGraphSignInActivity](#microsoftgraphsigninactivity) |
| signInSessionsValidFromDateTime | Any refresh tokens or session tokens \(session cookies\) issued before this time are invalid. Applications get an error when using an invalid refresh or session token to acquire a delegated access token \(to access APIs such as Microsoft Graph\). If this happens, the application needs to acquire a new refresh token by requesting the authorized endpoint. Read-only. Use revokeSignInSessions to reset. | string |
| skills | A list for the user to enumerate their skills. | string\[\] |
| state | The state or province in the user's address. Maximum length is 128 characters. | string |
| streetAddress | The street address of the user's place of business. Maximum length is 1,024 characters. | string |
| surname | The user's surname \(family name or last name\). Maximum length is 64 characters. | string |
| type | The resource type | 'Microsoft.Graph/users' \(ReadOnly\) |
| usageLocation | A two-letter country code \(ISO standard 3166\). Required for users that are assigned licenses due to legal requirements to check for availability of services in countries/regions. Examples include: US, JP, and GB. Not nullable. | string |
| userPrincipalName | The user principal name \(UPN\) of the user. The UPN is an Internet-style sign-in name for the user based on the Internet standard RFC 822. By convention, this value should map to the user's email name. The general format is alias@domain, where the domain must be present in the tenant's collection of verified domains. This property is required when a user is created. The verified domains for the tenant can be accessed from the verifiedDomains property of organization.NOTE: This property can't contain accent characters. Only the following characters are allowed A - Z, a - z, 0 - 9, '. - \_ ! # ^ ~. For the complete list of allowed characters, see username policies. | string \(Required\) |
| userType | A string value that can be used to classify user types in your directory. The possible values are Member and Guest. NOTE: For more information about the permissions for members and guests, see What are the default user permissions in Microsoft Entra ID?. | string |

### MicrosoftGraphAssignedLicense

| Name | Description | Value |
| --- | --- | --- |
| disabledPlans | A collection of the unique identifiers for plans that have been disabled. IDs are available in servicePlans > servicePlanId in the tenant's subscribedSkus or serviceStatus > servicePlanId in the tenant's companySubscription. | string  <br>  <br>Constraints:  <br>Min length = 36  <br>Max length = 36  <br>Pattern = `^[0-9a-fA-F]{8}-([0-9a-fA-F]{4}-){3}[0-9a-fA-F]{12}$`  <br> |
| skuId | The unique identifier for the SKU. Corresponds to the skuId from subscribedSkus or companySubscription. | string  <br>  <br>Constraints:  <br>Min length = 36  <br>Max length = 36  <br>Pattern = `^[0-9a-fA-F]{8}-([0-9a-fA-F]{4}-){3}[0-9a-fA-F]{12}$`  <br> |

### MicrosoftGraphAssignedPlan

| Name | Description | Value |
| --- | --- | --- |
| assignedDateTime | The date and time at which the plan was assigned. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is 2014-01-01T00:00:00Z. | string |
| capabilityStatus | Condition of the capability assignment. The possible values are Enabled, Warning, Suspended, Deleted, LockedOut. See a detailed description of each value. | string |
| service | The name of the service; for example, exchange. | string |
| servicePlanId | A GUID that identifies the service plan. For a complete list of GUIDs and their equivalent friendly service names, see Product names and service plan identifiers for licensing. | string  <br>  <br>Constraints:  <br>Min length = 36  <br>Max length = 36  <br>Pattern = `^[0-9a-fA-F]{8}-([0-9a-fA-F]{4}-){3}[0-9a-fA-F]{12}$`  <br> |

### MicrosoftGraphAuthorizationInfo

| Name | Description | Value |
| --- | --- | --- |
| certificateUserIds |  | string\[\] |

### MicrosoftGraphEmployeeOrgData

| Name | Description | Value |
| --- | --- | --- |
| costCenter | The cost center associated with the user. | string |
| division | The name of the division in which the user works. | string |

### MicrosoftGraphObjectIdentity

| Name | Description | Value |
| --- | --- | --- |
| issuer | Specifies the issuer of the identity, for example facebook.com. 512 character limit. For local accounts \(where signInType isn't federated\), this property is the local default domain name for the tenant, for example contoso.com. For guests from other Microsoft Entra organizations, this is the domain of the federated organization, for example contoso.com. For more information about filtering behavior for this property, see Filtering on the identities property of a user. | string |
| issuerAssignedId | Specifies the unique identifier assigned to the user by the issuer. 64 character limit. The combination of issuer and issuerAssignedId must be unique within the organization. Represents the sign-in name for the user, when signInType is set to emailAddress or userName \(also known as local accounts\).When signInType is set to: emailAddress \(or a custom string that starts with emailAddress like emailAddress1\), issuerAssignedId must be a valid email addressuserName, issuerAssignedId must begin with an alphabetical character or number, and can only contain alphanumeric characters and the following symbols: - or \_ For more information about filtering behavior for this property, see Filtering on the identities property of a user. | string |
| signInType | Specifies the user sign-in types in your directory, such as emailAddress, userName, federated, or userPrincipalName. federated represents a unique identifier for a user from an issuer that can be in any format chosen by the issuer. Setting or updating a userPrincipalName identity updates the value of the userPrincipalName property on the user object. The validations performed on the userPrincipalName property on the user object, for example, verified domains and acceptable characters, are performed when setting or updating a userPrincipalName identity. Extra validation is enforced on issuerAssignedId when the sign-in type is set to emailAddress or userName. This property can also be set to any custom string. For more information about filtering behavior for this property, see Filtering on the identities property of a user. | string |

### MicrosoftGraphLicenseAssignmentState

| Name | Description | Value |
| --- | --- | --- |
| assignedByGroup |  | string |
| disabledPlans |  | string  <br>  <br>Constraints:  <br>Min length = 36  <br>Max length = 36  <br>Pattern = `^[0-9a-fA-F]{8}-([0-9a-fA-F]{4}-){3}[0-9a-fA-F]{12}$`  <br> |
| error |  | string |
| lastUpdatedDateTime |  | string |
| skuId |  | string  <br>  <br>Constraints:  <br>Min length = 36  <br>Max length = 36  <br>Pattern = `^[0-9a-fA-F]{8}-([0-9a-fA-F]{4}-){3}[0-9a-fA-F]{12}$`  <br> |
| state |  | string |

### MicrosoftGraphDateTimeZone

| Name | Description | Value |
| --- | --- | --- |
| dateTime | A single point of time in a combined date and time representation \({date}T{time}; for example, 2017-08-29T04:00:00.0000000\). | string |
| timeZone | Represents a time zone, for example, 'Pacific Standard Time'. See below for more possible values. | string |

### MicrosoftGraphAutomaticRepliesSetting

| Name | Description | Value |
| --- | --- | --- |
| externalAudience | The set of audience external to the signed-in user's organization who will receive the ExternalReplyMessage, if Status is AlwaysEnabled or Scheduled. The possible values are: none, contactsOnly, all. | string |
| externalReplyMessage | The automatic reply to send to the specified external audience, if Status is AlwaysEnabled or Scheduled. | string |
| internalReplyMessage | The automatic reply to send to the audience internal to the signed-in user's organization, if Status is AlwaysEnabled or Scheduled. | string |
| scheduledEndDateTime | The date and time that automatic replies are set to end, if Status is set to Scheduled. | [MicrosoftGraphDateTimeZone](#microsoftgraphdatetimezone) |
| scheduledStartDateTime | The date and time that automatic replies are set to begin, if Status is set to Scheduled. | [MicrosoftGraphDateTimeZone](#microsoftgraphdatetimezone) |
| status | Configurations status for automatic replies. The possible values are: disabled, alwaysEnabled, scheduled. | string |

### MicrosoftGraphLocaleInfo

| Name | Description | Value |
| --- | --- | --- |
| displayName | A name representing the user's locale in natural language, for example, 'English \(United States\)'. | string |
| locale | A locale representation for the user, which includes the user's preferred language and country/region. For example, 'en-us'. The language component follows 2-letter codes as defined in ISO 639-1, and the country component follows 2-letter codes as defined in ISO 3166-1 alpha-2. | string |

### MicrosoftGraphTimeZoneBase

| Name | Description | Value |
| --- | --- | --- |
| name | The name of a time zone. It can be a standard time zone name such as 'Hawaii-Aleutian Standard Time', or 'Customized Time Zone' for a custom time zone. | string |

### MicrosoftGraphWorkingHours

| Name | Description | Value |
| --- | --- | --- |
| daysOfWeek | The days of the week on which the user works. | 'friday' |
| endTime | The time of the day that the user stops working. | string |
| startTime | The time of the day that the user starts working. | string |
| timeZone | The time zone to which the working hours apply. | [MicrosoftGraphTimeZoneBase](#microsoftgraphtimezonebase) |

### MicrosoftGraphMailboxSettings

| Name | Description | Value |
| --- | --- | --- |
| archiveFolder | Folder ID of an archive folder for the user. | string |
| automaticRepliesSetting | Configuration settings to automatically notify the sender of an incoming email with a message from the signed-in user. | [MicrosoftGraphAutomaticRepliesSetting](#microsoftgraphautomaticrepliessetting) |
| dateFormat | The date format for the user's mailbox. | string |
| delegateMeetingMessageDeliveryOptions | If the user has a calendar delegate, this specifies whether the delegate, mailbox owner, or both receive meeting messages and meeting responses. Possible values are: sendToDelegateAndInformationToPrincipal, sendToDelegateAndPrincipal, sendToDelegateOnly. | string |
| language | The locale information for the user, including the preferred language and country/region. | [MicrosoftGraphLocaleInfo](#microsoftgraphlocaleinfo) |
| timeFormat | The time format for the user's mailbox. | string |
| timeZone | The default time zone for the user's mailbox. | string |
| userPurpose | The purpose of the mailbox. Differentiates a mailbox for a single user from a shared mailbox and equipment mailbox in Exchange Online. Possible values are: user, linked, shared, room, equipment, others, unknownFutureValue. Read-only. | string |
| workingHours | The days of the week and hours in a specific time zone that the user works. | [MicrosoftGraphWorkingHours](#microsoftgraphworkinghours) |

### MicrosoftGraphOnPremisesExtensionAttributes

| Name | Description | Value |
| --- | --- | --- |
| extensionAttribute1 | First customizable extension attribute. | string |
| extensionAttribute10 | Tenth customizable extension attribute. | string |
| extensionAttribute11 | Eleventh customizable extension attribute. | string |
| extensionAttribute12 | Twelfth customizable extension attribute. | string |
| extensionAttribute13 | Thirteenth customizable extension attribute. | string |
| extensionAttribute14 | Fourteenth customizable extension attribute. | string |
| extensionAttribute15 | Fifteenth customizable extension attribute. | string |
| extensionAttribute2 | Second customizable extension attribute. | string |
| extensionAttribute3 | Third customizable extension attribute. | string |
| extensionAttribute4 | Fourth customizable extension attribute. | string |
| extensionAttribute5 | Fifth customizable extension attribute. | string |
| extensionAttribute6 | Sixth customizable extension attribute. | string |
| extensionAttribute7 | Seventh customizable extension attribute. | string |
| extensionAttribute8 | Eighth customizable extension attribute. | string |
| extensionAttribute9 | Ninth customizable extension attribute. | string |

### MicrosoftGraphOnPremisesProvisioningError

| Name | Description | Value |
| --- | --- | --- |
| category | Category of the provisioning error. Note: Currently, there is only one possible value. Possible value: PropertyConflict - indicates a property value is not unique. Other objects contain the same value for the property. | string |
| occurredDateTime | The date and time at which the error occurred. | string |
| propertyCausingError | Name of the directory property causing the error. Current possible values: UserPrincipalName or ProxyAddress. | string |
| value | Value of the property causing the error. | string |

### MicrosoftGraphPasswordProfile

| Name | Description | Value |
| --- | --- | --- |
| forceChangePasswordNextSignIn | true if the user must change their password on the next sign-in; otherwise false. | bool |
| forceChangePasswordNextSignInWithMfa | If true, at next sign-in, the user must perform a multifactor authentication \(MFA\) before being forced to change their password. The behavior is identical to forceChangePasswordNextSignIn except that the user is required to first perform a multifactor authentication before password change. After a password change, this property will be automatically reset to false. If not set, default is false. | bool |
| password | The password for the user. This property is required when a user is created. It can be updated, but the user will be required to change the password on the next sign-in. The password must satisfy minimum requirements as specified by the user's passwordPolicies property. By default, a strong password is required. | string |

### MicrosoftGraphProvisionedPlan

| Name | Description | Value |
| --- | --- | --- |
| capabilityStatus | Condition of the capability assignment. The possible values are Enabled, Warning, Suspended, Deleted, LockedOut. See a detailed description of each value. | string |
| provisioningStatus | The possible values are:Success - Service is fully provisioned.Disabled - Service is disabled.Error - The service plan isn't provisioned and is in an error state.PendingInput - The service isn't provisioned and is awaiting service confirmation.PendingActivation - The service is provisioned but requires explicit activation by an administrator \(for example, Intune\_O365 service plan\)PendingProvisioning - Microsoft has added a new service to the product SKU and it isn't activated in the tenant. | string |
| service | The name of the service; for example, 'AccessControlS2S'. | string |

### MicrosoftGraphServiceProvisioningError

| Name | Description | Value |
| --- | --- | --- |
| createdDateTime | The date and time at which the error occurred. | string |
| isResolved | Indicates whether the error has been attended to. | bool |
| serviceInstance | Qualified service instance \(for example, 'SharePoint/Dublin'\) that published the service error information. | string |

### MicrosoftGraphSignInActivity

| Name | Description | Value |
| --- | --- | --- |
| lastNonInteractiveSignInDateTime | The last non-interactive sign-in date for a specific user. You can use this field to calculate the last time a client attempted \(either successfully or unsuccessfully\) to sign in to the directory on behalf of a user. Because some users may use clients to access tenant resources rather than signing into your tenant directly, you can use the non-interactive sign-in date to along with lastSignInDateTime to identify inactive users. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is 2014-01-01T00:00:00Z. Microsoft Entra ID maintains non-interactive sign-ins going back to May 2020. For more information about using the value of this property, see Manage inactive user accounts in Microsoft Entra ID. | string |
| lastNonInteractiveSignInRequestId | Request identifier of the last non-interactive sign-in performed by this user. | string |
| lastSignInDateTime | The last interactive sign-in date and time for a specific user. This property records the last time a user attempted an interactive sign-in to the directory—whether the attempt was successful or not. Note: Since unsuccessful attempts are also logged, this value might not accurately reflect actual system usage. For tracking actual account access, please use the lastSuccessfulSignInDateTime property. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is 2014-01-01T00:00:00Z. | string |
| lastSignInRequestId | Request identifier of the last interactive sign-in performed by this user. | string |
| lastSuccessfulSignInDateTime | The date and time of the user's most recent successful interactive or non-interactive sign-in. Use this property if you need to determine when the account was truly accessed. This field can be used to build reports, such as inactive users. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is 2014-01-01T00:00:00Z. Microsoft Entra ID maintains interactive sign-ins going back to April 2020. For more information about using the value of this property, see Manage inactive user accounts in Microsoft Entra ID. | string |
| lastSuccessfulSignInRequestId | The request ID of the last successful sign-in. | string |
