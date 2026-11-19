<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/deploy-content-integrated-security-operations -->
<!-- Sitemap-Last-Modified: 2026-09-23 -->

# Deploy content as code with ISOC in Microsoft Defender

Use repositories with Integrated Security Operations Center \(ISOC\) in Microsoft Defender to manage and deploy security content by using continuous integration and continuous delivery \(CI/CD\).

Repository connections support a target-based deployment model. Depending on your tenant configuration, you can deploy content to a workspace, either ISOC or Microsoft Sentinel, or deploy supported Defender-level content to Microsoft Defender XDR at tenant scope.

Workspace-targeted connections support existing workspace content types and supported Defender-level content. Tenant-targeted connections support Defender workbooks and custom detections.

You can manage content from the Microsoft Defender portal or a supported external source control repository. Updates made in your repository are automatically deployed to the selected target.

## Prerequisites

Before you begin, make sure the following requirements are met:

- Your tenant is [eligible for ISOC](https://learn.microsoft.com/en-us/defender-xdr/isoc-overview).
- For workspace-targeted connections, you have an [ISOC workspace](https://learn.microsoft.com/en-us/defender-xdr/onboard-isoc-workspace) or an existing Microsoft Sentinel workspace in a resource group where you have the **Owner** role. A workspace isn't required for tenant-targeted connections.
- You have the **Global Administrator** role in Microsoft Entra ID for the initial CI/CD setup.
- Custom content files that you want to deploy are in a supported format for the selected deployment target. For supported formats, see [Plan your repository content](https://learn.microsoft.com/en-us/azure/sentinel/ci-cd-custom-content#plan-your-repository-content).
- The account you use to create the connection is in your home tenant. External identities such as B2B guest accounts and delegated access aren't supported.
- **\(Custom detections and Defender workbooks\)** You have an ISOC-eligible license or an equivalent license that includes Microsoft Defender XDR. For more information, see [Deploy custom detection rules as code](https://learn.microsoft.com/en-us/azure/sentinel/ci-cd-custom-content#deploy-custom-detection-rules-as-code-preview).

### GitHub prerequisites

Before connecting to GitHub, make sure that:

- You have **Collaborator** access to your GitHub repository.
- GitHub Actions is enabled.

### Azure DevOps prerequisites \(workspace only\)

Before connecting to Azure DevOps, make sure that:

- You have **Project Administrator** access to your Azure DevOps repository.
- Third-party application access through OAuth is enabled for Azure DevOps [application connection policies](https://learn.microsoft.com/en-us/azure/devops/organizations/accounts/change-application-access-policies#manage-a-policy).
- Your Azure DevOps connection is in the same tenant as your ISOC workspace.

For more information about deployable content types, see [Plan your repository content](https://learn.microsoft.com/en-us/azure/sentinel/ci-cd-custom-content#plan-your-repository-content).

## Supported deployment targets and content types

When you create a repository connection, select the target where you want to deploy content.

| Deployment target | Supported content |
| --- | --- |
| **Workspace** | Existing supported Microsoft Sentinel workspace content, custom detections, and Defender workbooks |
| **Defender XDR** | Custom detections and Defender workbooks |

The available content types are filtered based on the selected deployment target and tenant eligibility.

### Workspace-targeted connections

Use a workspace-targeted connection to deploy content to an ISOC workspace or an existing Microsoft Sentinel workspace.

Workspace-targeted connections support existing Microsoft Sentinel repository content types and Defender-level content.

### Tenant-targeted connections

Use a Defender XDR target to deploy supported content at tenant scope.

Tenant-targeted connections support Defender workbooks and custom detections. An ISOC or Microsoft Sentinel workspace isn't required for this deployment target.

For eligible tenants without a workspace, Defender XDR is the only available deployment target.

## Connect a repository

Use this procedure to create a repository connection for a workspace or Microsoft Defender XDR deployment target. The available targets depend on your tenant configuration.

Each connection can deploy the content types supported by its selected target. Workspace-targeted connections support existing workspace content types, including analytics rules, automation rules, custom detection rules, hunting queries, parsers, playbooks, and workbooks. Tenant-targeted connections support Defender workbooks and custom detections.

For more information, see [About Microsoft Sentinel content and solutions](https://learn.microsoft.com/en-us/azure/sentinel/sentinel-solutions).

You can't create duplicate connections with the same repository and branch in a single workspace.

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com/).
2. Make sure that you're signed in to your source control application with the credentials you want to use for the connection.
3. In the Defender portal, select **Content management** > **Repositories**.
4. Select **Add new**.
5. On the **Create new deployment connection** page, enter a name for the connection.
6. Enter a description for the connection.
7. From **Source Control**, select the repository type that you want to connect.
8. Select **Authorize**.
9. Complete the steps for your source control provider:

   - [GitHub](#tabpanel_1_github)
   - [Azure DevOps \(workspace only\)](#tabpanel_1_azure-devops)


   1. Enter your GitHub credentials when prompted.

      The first time you add a connection, you're prompted to authorize the connection to Microsoft Sentinel. If you're already signed in to your GitHub account in the same browser, your GitHub credentials are populated automatically.
   2. In **Repository**, select the repository that you want to connect.
   3. Select **Add repository**.

      The first time you connect to a repository, a new browser window or tab opens and prompts you to install the **Azure-Sentinel** app.
   4. In GitHub, select the repository where you want to install the **Azure-Sentinel** app.
   5. Install the **Azure-Sentinel** app.
   6. Return to the **Create new deployment connection** page.
   7. From **Branch**, select the branch that you want to connect.
   8. From **Target**, select the deployment target:

      - **Workspace** to deploy content to an ISOC or Microsoft Sentinel workspace.
      - **Defender XDR** to deploy supported Defender-level content at tenant scope.


      If your tenant doesn't have an ISOC or Microsoft Sentinel workspace, only the Defender XDR target is available, provided your tenant is eligible for ISOC.

   9. From **Content Types**, select the types of content that you want to deploy. Available content types are filtered based on the selected target.

      Both parsers and hunting queries use the **Saved Searches** API to deploy content. If you select one of these content types and your branch contains the other type, both content types are deployed.

      For other content types, only the content types that you select are deployed.
   10. Select **Create**.

       For example:

       ![Screenshot of a new GitHub repository connection.](https://learn.microsoft.com/en-us/defender-xdr/media/ci-cd/create-new-connection-github.png)


   Azure DevOps automatically authorizes you by using your current Azure credentials.


   1. Make sure that you're authorized to the same Azure DevOps tenant that you're connecting to from Microsoft Defender.
   2. From **Organization**, select your Azure DevOps organization.
   3. From **Project**, select your project.
   4. From **Repository**, select your repository.
   5. From **Branch**, select the branch that you want to connect to your ISOC workspace.
   6. From **Content Types**, select the content that you want to deploy.

      Both parsers and hunting queries use the **Saved Searches** API to deploy content. If you select one of these content types and your branch contains the other type, both content types are deployed.

      For other content types, only the content types that you select are deployed.
   7. Select **Create**.

      For example:

      ![Screenshot of a new Azure DevOps repository connection.](https://learn.microsoft.com/en-us/defender-xdr/media/ci-cd/create-new-connection-devops.png)

After you create the connection, a new workflow or pipeline is generated in your repository. Supported content from your repository is deployed to the selected workspace or Defender XDR tenant-level target.

Deployment time might vary depending on the amount of content that you're deploying.

## View the deployment status

To view the deployment status in GitHub:

1. Open your repository in GitHub.
2. Select the **Actions** tab.
3. Select the workflow `.yaml` file to view deployment logs and error messages.

To view the deployment status in Azure DevOps:

1. Open your repository in Azure DevOps.
2. Select the **Pipelines** tab.

After deployment is complete:

- Workspace-level content appears in the corresponding Microsoft Sentinel experiences in the Defender portal.
- Defender-level content appears in the corresponding Microsoft Defender experiences.
- The connection details on the **Repositories** page show deployment status, time of the last deployment, and a link to deployment logs.

The Repositories page provides a unified view of repository deployment status for workspaces you have access to. You can review deployment status without selecting each workspace separately.

For example:

![Screenshot of a repository connection showing deployment logs and status.](https://learn.microsoft.com/en-us/defender-xdr/media/ci-cd/deployment-logs-status.png)

By default, the workflow deploys only content modified since the previous deployment. You can customize this behavior by changing deployment triggers, turning off smart deployments, or limiting deployments to a specific root folder.

For more information, see [Customize repository deployments](https://learn.microsoft.com/en-us/azure/sentinel/ci-cd-custom-deploy).

## Edit content

After you create a repository connection, edit connected content in the repository instead of editing it directly in Microsoft Defender.

If you edit deployed content in Microsoft Defender, export the updated content back to your source control repository. Otherwise, your changes might be overwritten the next time content is deployed from the repository.

## Delete content

Deleting content from your repository doesn't automatically delete content previously deployed to the selected target.

To remove content that was deployed through a repository:

1. Delete the content from your repository.
2. Delete the corresponding deployed content from the relevant Microsoft Sentinel or Microsoft Defender experience.

You can filter content by its source name to help identify content deployed from repositories.

[![Screenshot of analytics rules filtered by the source name of a repository.](https://learn.microsoft.com/en-us/defender-xdr/media/ci-cd/delete-repo-content.png)](https://learn.microsoft.com/en-us/defender-xdr/media/ci-cd/delete-repo-content.png#lightbox)

## Remove a repository connection

Removing a repository connection stops future content deployments to the selected target. Previously deployed content remains at its deployment target.

To use Bicep files, your repository connection must be newer than November 1, 2024. Remove and recreate an older connection to update it.

To remove a repository connection:

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com/).
2. Select **Content management** > **Repositories**.
3. Select the connection that you want to remove.
4. Select **Delete**.
5. Select **Yes** to confirm the deletion.

After you remove the connection, previously deployed content remains in the corresponding workspace or Microsoft Defender experience. Content added to the repository after you remove the connection isn't deployed.

If you encounter an error when removing a connection, check your source control repository and confirm that the associated GitHub workflow or Azure DevOps pipeline is deleted.

### Remove the Microsoft Sentinel app from your GitHub repository

Before you remove the Microsoft Sentinel app from a GitHub repository, remove all associated connections from the **Repositories** page in Microsoft Defender.

Each Microsoft Sentinel app installation has a unique ID that's used when adding and removing the connection. If the ID is missing or changed, remove the connection from the **Repositories** page and manually remove the workflow from your GitHub repository to prevent future content deployments.

## Related content

- [ISOC in Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/isoc-overview)
- [Create an ISOC workspace in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/onboard-isoc-workspace)
- [Plan your repository content](https://learn.microsoft.com/en-us/azure/sentinel/ci-cd-custom-content#plan-your-repository-content)
- [Customize repository deployments](https://learn.microsoft.com/en-us/azure/sentinel/ci-cd-custom-deploy)
