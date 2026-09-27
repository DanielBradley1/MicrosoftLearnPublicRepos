<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/apps/deploy-use/disable-delete-deployments -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# Disable and delete application deployments

*Applies to: Configuration Manager \(current branch\)*

If you want to stop the deployment of an application, you can either disable it temporarily or delete it entirely.

Important

Neither of these actions by themselves cause an instant change on the client. You can use [client notifications](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/client-notification#client-notification) or other automation tools to quickly request that clients refresh policy. But that still doesn't guarantee that a client won't run a deployment.

Make sure you carefully plan app deployments. [Simulate](https://learn.microsoft.com/en-us/intune/configmgr/apps/deploy-use/simulate-application-deployments) more complex deployments. When you deploy to a query-based collection, use [query results preview](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/collections/create-collections#bkmk-query) to make sure you understand the scope of the query.

## Disable

Starting in version 2103, you can disable application deployments. Other objects already have similar behaviors:

- Software update deployments: Disable the deployment
- Phased deployments: Suspend the phase
- Package: Disable the program
- Task sequence: Disable the task sequence
- Configuration baseline: Disable the baseline

For device-based deployments, when you disable the deployment or object, use the client notification action to **Download Computer Policy**. This action immediately tells the client to update its policy from the site. If the deployment hasn't already started, the client receives the updated policy that the object is now disabled.

For user-based deployments, the user needs to sign out of Windows. Policy updates when they sign in to Windows, or every 24 hours by default.

Note

You can't disable an available deployment of an application to a user collection. You can only disable required deployments to user collections, or both type of deployments to device collections. The following table summarizes the supported scenarios to disable app deployments:

| Deployment purpose | Device collection | User collection |
| --- | --- | --- |
| Required | Yes | Yes |
| Available | Yes | No |

1. In the Configuration Manager console, go to the **Software Library** workspace, expand **Application Management**, and select the **Applications** node.
2. Select an app that you've deployed. In the details pane, switch to the **Deployment** tab.
3. Select a deployment. In the ribbon, on the **Deployment** tab, select **Disable**.
4. For a device-based deployment, note the name of the collection in **Collection** field of the deployment.

   Tip

   When you select the deployment, press **CTRL** + **C**. This keyboard shortcut copies the values of the current columns for the selected deployment.
5. Switch to the **Assets and Compliance** workspace, select the **Device Collections** node, and locate the target collection for the deployment. The quickest method is to search for the collection name as previously noted. You may need to select the option in the ribbon to search **All subfolders**.
6. Select the target collection for the deployment. In the ribbon, in the **Collection** group, select **Client Notification** and choose the **Download Computer Policy** action.

To enable the deployment, repeat this process but select the **Enable** action on the application deployment.

Note

When you select a deployment, you can use the **Collection** action to change to the **Assets and Compliance** workspace. But the current collection view doesn't support client notification actions.

## Delete

1. In the Configuration Manager console, go to the **Software Library** workspace, expand **Application Management**, and select either the **Applications** or **Application Groups** node.
2. Select the application or application group that includes the deployment you want to delete.
3. Switch to the **Deployments** tab of the details pane, and select the deployment.
4. In the ribbon, on the **Deployment** tab in the **Deployment** group, select **Delete**.

When you delete an application deployment, any instances of the application that clients have already installed aren't removed. To remove these applications, deploy the application to computers to **Uninstall**. If you delete an application deployment, the application is no longer visible in Software Center. The same behavior happens when you remove a resource from the target collection for the deployment.

When you delete a deployment, you remove the policy that deploys an application to a specific collection. This action doesn't delete the collection, any deployment types, or the application itself.

## Next steps

[Revise and supersede applications](https://learn.microsoft.com/en-us/intune/configmgr/apps/deploy-use/revise-and-supersede-applications)

[Uninstall applications](https://learn.microsoft.com/en-us/intune/configmgr/apps/deploy-use/uninstall-applications)
