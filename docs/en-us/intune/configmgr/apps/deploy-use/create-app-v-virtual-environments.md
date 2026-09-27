<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/apps/deploy-use/create-app-v-virtual-environments -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# Create App-V virtual environments in Configuration Manager

*Applies to: Configuration Manager \(current branch\)*

In a Microsoft Application Virtualization \(App-V\) virtual environment in Configuration Manager, deployed virtual applications can share the same file system and registry on client Windows PCs. Unlike standard virtual applications, these applications can share data with each other. Virtual environments are created or modified on client PCs when the application is installed or when clients next evaluate their installed applications. You can order these applications so that when multiple applications try to modify a file system or registry value, the application with the highest order takes priority.

Important

Do not rely on App-V virtual environments to provide security protection, such as from malware.

Use the following procedure to create an App-V virtual environment in Configuration Manager.

## Create an App-V virtual environment

1. In the Configuration Manager console, choose **Software Library** > **Application Management** > **App-V Virtual Environments**.
2. On the **Home** tab, in the **Create** group, choose **Create Virtual Environment**.
3. In the **Create Virtual Environment** dialog box, enter the following information:

   - **Name**. Enter a unique name for the virtual environment \(maximum 128 characters\).
   - **Description**. \(Optional\) Enter a description for the virtual environment.

4. To add a new deployment type to the virtual environment, choose **Add**. You must add at least one deployment type.
5. In the **Add Applications** dialog box, specify a **Group name** \(maximum 128 characters\). You'll use this name to refer to the group of applications that you add to the virtual environment.
6. Choose **Add**, select the App-V 5 applications and deployment types that you want to add to the group, and then choose **OK**.
7. In the **Add Applications** dialog box, you can select **Increase Order** or **Decrease Order** to set the application that takes priority if multiple applications attempt to modify file system or registry settings in the same virtual environment.
8. To return to the **Create Virtual Environment** dialog box, choose **OK**.
9. When you're done adding groups, choose **OK** to create the virtual environment. The new virtual environment is displayed in the **App-V Virtual Environments** node of the Configuration Manager console. You can monitor the status of your virtual environments by using the App-V Virtual Environment Status report.

   Note

   The virtual environment is added or modified on client PCs when the application is installed or when the client next evaluates installed applications.
