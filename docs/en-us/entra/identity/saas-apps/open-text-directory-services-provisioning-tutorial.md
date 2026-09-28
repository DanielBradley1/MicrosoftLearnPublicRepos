<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/open-text-directory-services-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-06-15 -->

# Configure OpenText Directory Services for automatic user provisioning with Microsoft Entra ID

This article describes the steps you need to perform in both OpenText Directory Services and Microsoft Entra ID to configure automatic user provisioning. When configured, Microsoft Entra ID automatically provisions and de-provisions users and groups to OpenText Directory Services using the Microsoft Entra provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Capabilities supported

- Create users in OpenText Directory Services
- Remove users in OpenText Directory Services when they don't require access anymore
- Keep user attributes synchronized between Microsoft Entra ID and OpenText Directory Services
- Provision groups and group memberships in OpenText Directory Services
- [Single sign-on](https://learn.microsoft.com/en-us/entra/identity/saas-apps/directory-services-tutorial) to OpenText Directory Services \(recommended\)
- Client Credentials authentication supported.
- Long lived bearer token authentication supported.

OpenText Directory Services is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government | China operated by 21Vianet |
| :---: | :---: | :---: |
| ✅ | ✅ |  |

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- An OTDS installation accessible by Microsoft Entra ID.

## Step 1: Plan your provisioning deployment

1. Learn about [how the provisioning service works](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).
2. Determine who's in [scope for provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
3. Determine what data to [map between Microsoft Entra ID and OpenText Directory Services](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes).

## Step 2: Configure OpenText Directory Services to support provisioning with Microsoft Entra ID

Note

The below steps apply to an OpenText Directory Services installation. They don't apply for OpenText CoreShare or OpenText OT2 tenants.

1. Create a dedicated confidential **OAuth client**.
2. Don't specify any redirect URLs. They aren't required.
3. OTDS will generate and display the **client secret**. Save the **client id** and **client secret** in a secure location.

   ![Client Secret](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/open-text-directory-services-provisioning-tutorial/client-secret.png)

4. Create a partition for the users and groups to be synchronized from Microsoft Entra ID.

   ![Partition page](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/open-text-directory-services-provisioning-tutorial/partition.png)

5. Grant administrative rights to the OAuth client you created on the partition you use for the Microsoft Entra users and groups being synchronized.

   - Partition -> Actions -> Edit Administrators


   ![Administrator page](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/open-text-directory-services-provisioning-tutorial/administrator.png)

## Step 3: Add OpenText Directory Services from the Microsoft Entra application gallery

Add OpenText Directory Services from the Microsoft Entra application gallery to start managing provisioning to OpenText Directory Services. If you have previously setup OpenText Directory Services for SSO, you can use the same application. However, we recommend that you create a separate app when testing out the integration initially. Learn more about adding an application from the gallery [here](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

## Step 4: Define who is in scope for provisioning

The Microsoft Entra provisioning service allows you to scope who is provisioned based on assignment to the application, or based on attributes of the user or group. If you choose to scope who is provisioned to your app based on assignment, you can use the [steps to assign users and groups to the application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal). If you choose to scope who is provisioned based solely on attributes of the user or group, you can [use a scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).

- Start small. Test with a small set of users and groups before rolling out to everyone. When scope for provisioning is set to assigned users and groups, you can control this by assigning one or two users or groups to the app. When scope is set to all users and groups, you can specify an [attribute based scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
- If you need extra roles, you can [update the application manifest](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps) to add new roles.

## Step 5: Configure automatic user provisioning to OpenText Directory Services

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in TestApp based on user and/or group assignments in Microsoft Entra ID.

### To configure automatic user provisioning for OpenText Directory Services in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**.

   ![Enterprise applications blade](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **OpenText Directory Services**.

   ![The OpenText Directory Services link in the Applications list](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Provisioning tab](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Select **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. Under the **Admin Credentials** section, input your OpenText Directory Services Tenant URL.

   - Non-specific tenant URL : `{OTDS URL}/scim/{partitionName}`
   - Specific tenant URL : `{OTDS URL}/otdstenant/{tenantID}/scim/{partitionName}`

7. Select **OAuth2 Client Credentials Grant** as the Authentication Method.

   1. Enter the **Client ID** and **Client Secret** retrieved from Step 2.
   2. Select **Test Connection** to ensure Microsoft Entra ID can connect to OpenText Directory Services.
   3. If the connection fails, ensure your OpenText Directory Services account has Admin permissions and try again.

      ![Screenshot of Token.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/open-text-directory-services-provisioning-tutorial/oauth2-entra-config.png)

8. Select **Create** to create your configuration.
9. Select **Properties** on the **Overview** page.
10. Select the **Edit** icon to edit the properties. Enable notification emails and provide an email to receive quarantine emails. Enable accidental deletions prevention. Select **Apply** to save the changes.

    ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

11. Select **Attribute Mapping** in the left panel and select **users**.
12. Review the user attributes that are synchronized from Microsoft Entra ID to OpenText Directory Services in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in OpenText Directory Services for update operations. If you choose to change the [matching target attribute](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes), you need to ensure that the OpenText Directory Services API supports filtering users based on that attribute. Select the **Save** button to commit any changes.

| Attribute | Type |
| --- | --- |
| userName | String |
| active | Boolean |
| displayName | String |
| title | String |
| emails\[type eq "work"\].value | String |
| preferredLanguage | String |
| name.givenName | String |
| name.familyName | String |
| name.formatted | String |
| addresses\[type eq "work"\].formatted | String |
| addresses\[type eq "work"\].streetAddress | String |
| addresses\[type eq "work"\].locality | String |
| addresses\[type eq "work"\].region | String |
| addresses\[type eq "work"\].postalCode | String |
| addresses\[type eq "work"\].country | String |
| phoneNumbers\[type eq "work"\].value | String |
| phoneNumbers\[type eq "mobile"\].value | String |
| phoneNumbers\[type eq "fax"\].value | String |
| externalId | String |
| urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:employeeNumber | String |
| urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:department | String |
| urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:manager | Reference |

12. Select **Groups**.
13. Review the group attributes that are synchronized from Microsoft Entra ID to OpenText Directory Services in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the groups in OpenText Directory Services for update operations. Select the **Save** button to commit any changes.
    | Attribute | Type |
    | --- | --- |
    | displayName | String |
    | externalId | String |
    | members | Reference |
14. To configure scoping filters, refer to the following instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
15. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
16. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Step 6: Monitor your deployment

Once you configure provisioning, use the following resources to monitor your deployment:

1. Use the [provisioning logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs) to determine which users are provisioned successfully or unsuccessfully
2. Check the [progress bar](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user) to see the status of the provisioning cycle and how close it's to completion
3. If the provisioning configuration seems to be in an unhealthy state, the application goes into quarantine. Learn more about quarantine states the [application provisioning quarantine status](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-quarantine-status) article.

## Additional resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
