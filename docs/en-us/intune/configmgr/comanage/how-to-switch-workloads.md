<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/comanage/how-to-switch-workloads -->
<!-- Sitemap-Last-Modified: 2023-03-21 -->

# How to switch Configuration Manager workloads to Intune

One of the benefits of co-management is switching workloads from Configuration Manager to Microsoft Intune. When a Windows 10 or later device has the Configuration Manager client and is enrolled to Intune, you get the benefits of both services. You control which workloads, if any, you switch the authority from Configuration Manager to Intune. Configuration Manager continues to manage all other workloads, including those workloads that you don't switch to Intune, and all other features of Configuration Manager that co-management doesn't support.

If you switch a workload to Intune, but later change your mind, you can switch it back to Configuration Manager.

For more information on the supported workloads, see [Workloads](https://learn.microsoft.com/en-us/intune/configmgr/comanage/workloads).

## Switch workloads

You can configure different pilot collections for each of the co-management workloads. Being able to use different pilot collections allows you to take a more granular approach when shifting workloads. You can switch workloads when you enable co-management, or later when you're ready. If you haven't already enabled co-management, do that first. For more information, see [How to enable co-management](https://learn.microsoft.com/en-us/intune/configmgr/comanage/how-to-enable). After you enable co-management, modify the settings in the co-management properties.

1. In the Configuration Manager console, go to the **Administration** workspace, expand **Cloud Services**, and select the **Cloud Attach** node. For version 2103 and earlier, select the **Co-management** node.
2. Select the co-management object, and then choose **Properties** in the ribbon.
3. Switch to the **Workloads** tab. By default, all workloads are set to the **Configuration Manager** setting. To switch a workload, move the slider control for that workload to the desired setting.

   ![Screenshot of Workloads tab on co-management properties page](https://learn.microsoft.com/en-us/intune/configmgr/comanage/media/3555750-co-management-workloads-tab.png)


   - **Configuration Manager**: Configuration Manager continues to manage this workload.
   - **Pilot Intune**: Switch this workload only for the devices in the pilot collection. You can change the **Pilot collections** on the **Staging** tab of the co-management properties page.
   - **Intune**: Switch this workload for all Windows devices enrolled in co-management.

Note

When Pilot Intune is selected for Endpoint Protection and Device Configuration Policies, Intune only deploys the policies and doesn't perform policy removal upon unassignment. For policy removal from the device when the policy is unassigned, the workload must be switched to Intune.

4. Go to the **Staging** tab and change the **Pilot collection** for any of the workloads if needed.

   ![Screenshot of Staging tab on co-management properties page](https://learn.microsoft.com/en-us/intune/configmgr/comanage/media/3555750-co-management-staging-tab.png)

Important

Before you switch any workloads, make sure you properly configure and deploy the corresponding workload in Intune. Make sure that workloads are always managed by one of the management tools for your devices. When you switch a co-management workload, the co-managed devices automatically synchronize MDM policy from Microsoft Intune.

## Next steps

[Monitor co-management](https://learn.microsoft.com/en-us/intune/configmgr/comanage/how-to-monitor)
