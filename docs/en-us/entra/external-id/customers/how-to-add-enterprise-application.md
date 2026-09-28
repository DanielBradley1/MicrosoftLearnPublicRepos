<!-- Source: https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-add-enterprise-application -->
<!-- Sitemap-Last-Modified: 2025-07-29 -->

# Add an enterprise application to your external tenant

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to external tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) External tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

Enterprise applications are software-as-a-service \(SaaS\) apps that are pre-integrated with Microsoft Entra ID. These apps support access management and single sign-on \(SSO\). You can find these apps in the Microsoft Entra application gallery, which includes a wide range of pre-integrated SaaS applications. This article uses the application named **Microsoft Entra SAML Toolkit** as an example, but the concepts apply for most [enterprise applications in the gallery](https://learn.microsoft.com/en-us/entra/identity/saas-apps/tutorial-list).

## Prerequisites

To add an enterprise application to your external tenant, you need:

- A Microsoft Entra user account. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles: [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator).

## Add an enterprise application

To add an enterprise application to your Microsoft Entra external tenant, follow these steps:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **All applications**.
3. Select **New application** > **Create your own application**.
4. Start typing the name of the application you want to add. If the application is already in the gallery, it appears in the list. In this article we use **Microsoft Entra SAML Toolkit** as an example.

   ![Screenshot showing how to add an enterprise application in the external tenant.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-add-enterprise-application/add-enterprise-app.png)
5. Select the application from the list, and then select **Create**.
6. Select **Create**, you're taken to the application that you registered.
7. You should [assign owners to the application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-app-owners?pivots=portal#assign-an-owner) as a best practice at this point.

## Clean up resources

You can keep the application in your tenant for future use, or you can [delete it](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/delete-application-portal?pivots=portal) if you no longer need it. If you delete the application, all associated user assignments and configurations are also deleted.

## Related content

- [Register a SAML app in your external tenant](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-register-saml-app)
