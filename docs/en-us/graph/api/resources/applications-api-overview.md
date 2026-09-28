<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/applications-api-overview?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-04-30 -->

# Manage Microsoft Entra applications and service principals by using Microsoft Graph

This guide provides an overview of key concepts, API use cases, and resources to help you automate the lifecycle management of Microsoft Entra applications.

## Applications and service principals

In Microsoft Entra, an application is defined by an **application** object and a **service principal** object. There's only one application object for your application across Microsoft Entra, but there can be multiple service principal objects for your application.

The application object is located in the tenant where the app is registered. A service principal is created in the tenant where the app is registered, and in every tenant where it's installed and used. For more information, see [Application and service principal objects in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity-platform/app-objects-and-service-principals).

In Microsoft Graph, an application is represented by the [application resource type](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0), and a service principal is represented by the [servicePrincipal resource type](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0). The details of the two objects can be accessed on the Microsoft Entra admin center through the **Entra ID** > **App registrations** and **Entra ID** > **Enterprise applications** menus respectively.

Service principals inherit specific properties from their associated app registrations. These properties are synchronized from the app registration, but the synchronization isn't immediate or continuous. Sometimes, updating a service principal may prompt the directory to refresh properties from the app registration, causing updates that weren't part of the original request.

## API use cases for managing applications

The following API use cases are supported for managing applications through the [application resource type](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0) in Microsoft Graph.

| Use cases | API operations |
| --- | --- |
| Register an application and configure its basic properties | [Create application](https://learn.microsoft.com/en-us/graph/api/application-post-applications?view=graph-rest-1.0) |
| Configure properties for a registered application including:<br><br>- Basic properties such as display name, logo, and tags<br>- Permissions<br>- Assign apps to users<br>- Set the basic identifier URIs<br>- The Microsoft accounts that the app supports<br>- App roles | [Update application](https://learn.microsoft.com/en-us/graph/api/application-update?view=graph-rest-1.0) |
| Delete an application | [Delete application](https://learn.microsoft.com/en-us/graph/api/application-delete?view=graph-rest-1.0) |
| Manage deleted applications | - [List deletedItems](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-list?view=graph-rest-1.0)<br>- [List deletedItems owners by a user](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-getuserownedobjects?view=graph-rest-1.0)<br>- [Get deleted item](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-get?view=graph-rest-1.0)<br>- [Permanently delete item](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-delete?view=graph-rest-1.0)<br>- [Restore deleted item](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-restore?view=graph-rest-1.0) |
| Manage password credentials for an application | - [application: addPassword](https://learn.microsoft.com/en-us/graph/api/application-addpassword?view=graph-rest-1.0)<br>- [application: removePassword](https://learn.microsoft.com/en-us/graph/api/application-removepassword?view=graph-rest-1.0) |
| Manage federated identity credentials for an application | [Start managing federated identity credentials using Microsoft Graph](https://learn.microsoft.com/en-us/graph/api/resources/federatedidentitycredentials-overview?view=graph-rest-1.0) |
| Manage certificate-based credentials for an application | - [application: addKey](https://learn.microsoft.com/en-us/graph/api/application-addkey?view=graph-rest-1.0)<br>- [application: removeKey](https://learn.microsoft.com/en-us/graph/api/application-removekey?view=graph-rest-1.0)<br>- Update the **keyCredentials** property through the [update application](https://learn.microsoft.com/en-us/graph/api/application-update?view=graph-rest-1.0) API operation. |
| Manage directory extensions on applications | - [extensionProperty resource type](https://learn.microsoft.com/en-us/graph/api/resources/extensionproperty?view=graph-rest-1.0) and its associated methods. For more information, see [Add custom data to resources using extensions](https://learn.microsoft.com/en-us/graph/extensibility-overview). |
| Track changes to an application | - [application: delta](https://learn.microsoft.com/en-us/graph/api/application-delta?view=graph-rest-1.0)<br>- [directoryObject: delta](https://learn.microsoft.com/en-us/graph/api/directoryobject-delta?view=graph-rest-1.0) with the following filter: `..?$filter=isof('microsoft.graph.application')` |
| Manage owners | - [List owners](https://learn.microsoft.com/en-us/graph/api/application-list-owners?view=graph-rest-1.0)<br>- [Add owner](https://learn.microsoft.com/en-us/graph/api/application-post-owners?view=graph-rest-1.0)<br>- [Remove owner](https://learn.microsoft.com/en-us/graph/api/application-delete-owners?view=graph-rest-1.0) |
| Manage publisher verification | - [Set verifiedPublisher](https://learn.microsoft.com/en-us/graph/api/application-setverifiedpublisher?view=graph-rest-1.0)<br>- [Unset verifiedPublisher](https://learn.microsoft.com/en-us/graph/api/application-unsetverifiedpublisher?view=graph-rest-1.0) |

## API use cases for managing service principals

The following API use cases are supported for managing service principals through the [servicePrincipal resource type](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0) in Microsoft Graph.

| Use cases | API operations |
| --- | --- |
| Register service principal | [Create servicePrincipal](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-post-serviceprincipals?view=graph-rest-1.0) |
| Configure properties for a service principal including:  <br>- Basic properties such as display name and logo  <br>- Permissions  <br>- Configure SSO mode | [Update servicePrincipal](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-update?view=graph-rest-1.0) |
| Delete a service principal | [Delete servicePrincipal](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-delete?view=graph-rest-1.0) |
| Manage deleted service principals: view, restore, or permanently delete |   <br>- [List deletedItems](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-list?view=graph-rest-1.0)  <br>- [List deletedItems owned by a user](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-getuserownedobjects?view=graph-rest-1.0)  <br>- [Get deleted item](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-get?view=graph-rest-1.0)  <br>- [Permanently delete item](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-delete?view=graph-rest-1.0)  <br>- [Restore deleted item](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-restore?view=graph-rest-1.0) |
| Manage password credentials for a service principal |   <br>- [servicePrincipal: addPassword](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-addpassword?view=graph-rest-1.0)  <br>- [servicePrincipal: removePassword](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-removepassword?view=graph-rest-1.0) |
| Manage certificate-based credentials for a service principal |   <br>- [servicePrincipal: addKey](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-addkey?view=graph-rest-1.0)  <br>- [servicePrincipal: removeKey](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-removekey?view=graph-rest-1.0) |
| Add a SAML token signing certificate | [servicePrincipal: addTokenSigningCertificate](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-addtokensigningcertificate?view=graph-rest-1.0) |
| Track changes to a service principal |   <br>- [servicePrincipal: delta](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-delta?view=graph-rest-1.0)  <br>- [directoryObject: delta](https://learn.microsoft.com/en-us/graph/api/directoryobject-delta?view=graph-rest-1.0) with the following filter: `..?$filter=isof('microsoft.graph.servicePrincipal')` |
| Manage owners |   <br>- [List owners](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-list-owners?view=graph-rest-1.0)  <br>- [Add owner](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-post-owners?view=graph-rest-1.0)  <br>- [Remove owner](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-delete-owners?view=graph-rest-1.0) |

## Application templates

Application templates are apps available in the [Microsoft Entra app gallery](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/overview-application-gallery). Use the [applicationTemplate resource type and its associated methods](https://learn.microsoft.com/en-us/graph/api/resources/applicationtemplate?view=graph-rest-1.0) to:

- Identify apps from the application gallery.
- Identify apps by the SSO mode they support.
- Instantiate an app and service principal from an application gallery.

## Policies applicable to applications and service principals

| Policy description | API operations | Applies to |
| --- | --- | --- |
| Manage Microsoft Entra ID Remote Desktop Services \(RDS\) authentication protocol | [remoteDesktopSecurityConfiguration resource type and its associated methods](https://learn.microsoft.com/en-us/graph/api/resources/remotedesktopsecurityconfiguration?view=graph-rest-1.0) | Service principals |
| Configure SAML tokens policy | [tokenIssuancePolicy resource type and its associated methods](https://learn.microsoft.com/en-us/graph/api/resources/tokenissuancepolicy?view=graph-rest-1.0) | Applications  <br>Service principals |
| Configure policies for access, SAML, and ID tokens | Token lifetime policy - [tokenLifetimePolicy resource type and its associated methods](https://learn.microsoft.com/en-us/graph/api/resources/tokenlifetimepolicy?view=graph-rest-1.0)  <br>Token issuance policy - [tokenIssuancePolicy resource type and its associated methods](https://learn.microsoft.com/en-us/graph/api/resources/tokenissuancepolicy?view=graph-rest-1.0) | Applications  <br>Service principals |
| Manage idle session time-out for Microsoft 365 web apps, for all device types  <br>**Note:** To trigger the policy only for unmanaged devices, you also need to add a Conditional Access policy. | [activityBasedTimeoutPolicy resource type and its associated methods](https://learn.microsoft.com/en-us/graph/api/resources/activitybasedtimeoutpolicy?view=graph-rest-1.0) | Microsoft 365 web apps |
| Manage policies for how certificates and password secrets can be used in your organization. Create tenant-wide policies or app-specific policies such as blocking the use of or restricting the lifetime of password secrets or symmetric keys and enforcing trusted certificate authorities | [Application authentication methods policies](https://learn.microsoft.com/en-us/graph/api/resources/applicationauthenticationmethodpolicy?view=graph-rest-1.0) | Applications |
| Manage claims mapping policies for WS-Fed, SAML, OAuth 2.0, and OpenID Connect protocols, and the applications the policies apply to | [claimsMappingPolicy resource type and its associated methods](https://learn.microsoft.com/en-us/graph/api/resources/claimsmappingpolicy?view=graph-rest-1.0) | Service principals |
| Manage Home Realm Discovery \(HRD\) for the tenant and assignment of the policy to a service principal | [homeRealmDiscoveryPolicy resource type and its associated methods](https://learn.microsoft.com/en-us/graph/api/resources/homerealmdiscoverypolicy?view=graph-rest-1.0) | Service principals |

## Identity synchronization \(provisioning\)

Provisioning APIs in Microsoft Graph let you automate and manage the provisioning and deprovisioning of identities in these scenarios:

- From your on-premises Active Directory to Microsoft Entra ID
- From other cloud directories to Microsoft Entra ID
- From Microsoft Entra ID to cloud applications like Dropbox, Salesforce, ServiceNow, and more

For more information, see [Microsoft Entra synchronization API overview](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-overview?view=graph-rest-1.0).

## Related content

- [Quick reference guide: API operations for managing applications](https://learn.microsoft.com/en-us/graph/tutorial-applications-basics)
- [Application management in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-application-management)
- [Tutorials for integrating applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/saas-apps/tutorial-list)
- [What is the Microsoft identity platform?](https://learn.microsoft.com/en-us/entra/identity-platform/v2-overview)
