<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-pilot-ring-deployment-group-policy-wsus -->
<!-- Sitemap-Last-Modified: 2025-10-20 -->

# Microsoft Defender Antivirus pilot ring deployment using Group Policy and Windows Server Update Services

Microsoft Defender for Endpoint is an enterprise endpoint security platform designed to help enterprise networks prevent, detect, investigate, and respond to advanced threats.

Tip

Microsoft Defender for Endpoint is available in two plans, Defender for Endpoint Plan 1 and Plan 2. A new Microsoft Defender Vulnerability Management add-on is now available for Plan 2.

## Prerequisites

### Supported operating systems

- Windows
- Windows Server

### Resources

The following resources provide information for using and managing Windows Server Update Services \(WSUS\).

- [Deploy Windows Defender definition updates using WSUS - Configuration Manager](https://learn.microsoft.com/en-us/troubleshoot/mem/configmgr/update-management/deploy-definition-updates-using-wsus)
- [Windows Server Update Services Help](https://learn.microsoft.com/en-us/previous-versions/orphan-topics/ws.11/dn343567\(v=ws.11\)?redirectedfrom=MSDN)

## Setting up the pilot environment

This section provides information about setting up the pilot \(UAT/Test/QA\) environment using Group Policy and Windows Server Update Services \(WSUS\).

[![Screenshot that shows an example ring deployment schedule for Group Policy with WSUS environments.](https://learn.microsoft.com/en-us/defender-endpoint/media/microsoft-defender-antivirus-deploy-ring-group-policy-wsus.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/microsoft-defender-antivirus-deploy-ring-group-policy-wsus.png#lightbox)

Note

Security intelligence update \(SIU\) is equivalent to signature updates, which is the same as definition updates.

On about 10-500\* Windows and/or Windows Server systems, depending on how many total systems that you all have.

Note

If you have a Citrix environment, include at least one Citrix VM \(non-persistent\) and/or \(persistent\)

1. Launch the **Windows Server Update Services Configuration Wizard**.
2. On the **Before You Begin** page, review the preliminary information and attend to any configuration or credential matters, and then select **Next**.
3. On the **Microsoft Update Improvement Program** page, if you would like to participate in the program, select **Yes, I would like to join the Microsoft Update Improvement Program**. Select **Next**.
4. On the **Choose Upstream Server** page, select **Synchronize from Microsoft Update** and then select **Next**.
5. On the **Specify Proxy Server** page, select **Next**.
6. On the **Choose Languages** page, select **Download updates only in these languages**. Select the update languages that you want to download, and then select **Next**
7. On the **Choose Products** page, scroll down to **Forefront**, select **Forefront Client Security** and **System Center Endpoint Protection** This is shown in the following figure.

   [![Screenshot that shows a screen capture of the WSUS configuration wizard Choose Products page.](https://learn.microsoft.com/en-us/defender-endpoint/media/microsoft-defender-antivirus-deploy-ring-group-policy-wsus-choose-products-av.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/microsoft-defender-antivirus-deploy-ring-group-policy-wsus-choose-products-av.png#lightbox)

   While still on the **Choose Products** page, scroll down to **Windows** and select **Microsoft Defender Antivirus**.
8. Select **Next**. On the **Choose Classification** page, select: **critical Updates**, **Definition Updates**, and **Security Updates**, and then select **Next**.
9. On the **Configure Sync Schedule** page, do the following:
   | In: | Change: |
   | :--- | :--- |
   | **Synchronize automatically** | select \(enable\) |
   | **First synchronization** | Set time to *5:00:00 AM* |
   | **Synchronizations per day** | Set to *1* |
10. Select **Next**. On the **Finished** page, select **Next**.
11. On the **What's next** page, select **Finish**.

    The Windows Server Update Services Configuration Wizard is complete.
12. Open the **Update Services** snap-in console, and navigate to **YR2K19**. The console is shown in the following figure.

    [![Screenshot that shows a screen capture of the Update Services snap-in console with YR2K19 shown.](https://learn.microsoft.com/en-us/defender-endpoint/media/microsoft-defender-antivirus-deploy-ring-group-policy-wsus-update-service-synch.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/microsoft-defender-antivirus-deploy-ring-group-policy-wsus-update-service-synch.png#lightbox)
13. When synchronization is complete, you can see how many products and classifications have been added in the last 30 days. Check to ensure the status for **Last synchronization result** indicates *Succeeded*. You may see a warning indicating **"Your WSUS server currently shows that no computers are registered to receive updates"**. This warning is normal at this point of the deployment configuration process.

#### View update details

1. In the **Update Services** console, in the navigation tree, go to > **Update Services** > **YR2K19** > **Updates** > **All Updates**.
2. In the **Actions** column, select **Search**. **Search** opens. In **Text**, type *defender*, and press *ENTER*. The results field under **Update Title** lists updates that include the word **Defender** in the title. For example *Windows Defender* and *Microsoft Defender Antivirus* updates for *Platform*, *Engine*, and *Intelligence*. Example results are shown in the next image.

   See [Viewing and Managing Updates](https://learn.microsoft.com/en-us/windows-server/administration/windows-server-update-services/manage/viewing-and-managing-updates).

   [![Screenshot that shows a screen capture of the Update Services for Microsoft Defender Antivirus.](https://learn.microsoft.com/en-us/defender-endpoint/media/microsoft-defender-antivirus-deploy-ring-group-policy-wsus-update-service-search-defender.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/microsoft-defender-antivirus-deploy-ring-group-policy-wsus-update-service-search-defender.png#lightbox)
3. In the **Search** dialog, under **Update Title**, double-click one of the listed KB items. One of two things happens:

   - If you don't have **Microsoft Report Viewer 2012 Redistributable** installed, the following error message appears:

     [![Screenshot that shows a screen capture of an error message indicating the Microsoft Report Viewer 2012 Redistributable isn't installed.](https://learn.microsoft.com/en-us/defender-endpoint/media/microsoft-defender-antivirus-deploy-ring-group-policy-wsus-report-viewer-error.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/microsoft-defender-antivirus-deploy-ring-group-policy-wsus-report-viewer-error.png#lightbox)

     Follow the link in the error message to install the Microsoft Report Viewer 2012 Redistributable before proceeding to the next numbered step of this procedure.
   - If **Microsoft Report Viewer 2012 Redistributable** is installed, the **Update Report for YR2k19** opens, presenting a report with information related to the KB you previously selected. An example report is shown in the following image:

     [![Screenshot that shows a screen capture with details about a KB update reported in Update Report for Yr2k19.](https://learn.microsoft.com/en-us/defender-endpoint/media/microsoft-defender-antivirus-deploy-ring-group-policy-wsus-report-viewer-kb-update-info.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/microsoft-defender-antivirus-deploy-ring-group-policy-wsus-report-viewer-kb-update-info.png#lightbox)


   To learn more about the different Microsoft Defender Antivirus Update channels, see [Manage the gradual rollout process for Microsoft Defender updates](https://learn.microsoft.com/en-us/defender-endpoint/manage-gradual-rollout)

#### To find out which Platform Update version is the Current Channel \(Broad\)

1. Go to the [Microsoft Update Catalog](https://www.catalog.update.microsoft.com/Search.aspx?q=KB4052623). \(*This link automatically loads a search filtered to KB4052623*\)
2. Search for a KB by name. For example, In the search box, type *KB4052623*, and then select **Search**.

   For example, on April 11, 2023, the latest production version is **4.18.2302.7**, where **23** == *2023*, **02** == *February*, and **.7** is the *minor revision*.

   [![Screenshot that shows a screen capture of the results from a Microsoft Update Catalog search for KB4052623.](https://learn.microsoft.com/en-us/defender-endpoint/media/microsoft-defender-antivirus-deploy-ring-group-policy-wsus-report-viewer-kb-search.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/microsoft-defender-antivirus-deploy-ring-group-policy-wsus-report-viewer-kb-search.png#lightbox)

#### To determine if updates are synchronized

1. In the **Update Services** console, go > **Update Services** > **YR2K19** > **Updates** > **All Updates**.
2. In **Approval**, select **Any Except Declined**, and then select **Refresh**.

   The **All Updates** view lists "Platform Updates" and "Security Intelligence Updates" \(also known as signatures/definitions\). For example, KB4052623 platform updates. KB4052623 platform update is shown in the following figure:

   [![Screenshot that shows a screen capture of the results from a Microsoft Update Catalog search for KB4052623 platform updates.](https://learn.microsoft.com/en-us/defender-endpoint/media/microsoft-defender-antivirus-deploy-ring-group-policy-wsus-report-view-signature-platform-updates.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/microsoft-defender-antivirus-deploy-ring-group-policy-wsus-report-view-signature-platform-updates.png#lightbox)
3. Select **KB4052623** version **4.18.2302.7** to see the synchronization status.

   Note

   For the "Security Intelligence Updates", please see [Appendix A](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-ring-deployment-group-policy-wsus-appendices). For the "Engine Updates", please see [Appendix B](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-ring-deployment-group-policy-wsus-appendices). For the "Platform Updates", please see [Appendix C](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-ring-deployment-group-policy-wsus-appendices).

#### Approve and deploy updates in WSUS

1. In the **Update Services** console, go to **Update Services** > **YR2K19** > **Computers** > **Options**. The **Options** window opens.
2. Select **Automatic Approvals** to launch the **Automatic Approvals** configuration wizard.
3. In **Automatic Approvals** page, on the **Update Rules** tab, select **OK**.
4. On the **Add Rule** page, is **Step 1**, select **When an update is in a specific classification** and **When an update is in a specific product**.
5. In **Choose Products**, scroll to **Forefront**, and then select **Forefront Client Security**. Scroll to **Windows**, and then select **Microsoft Defender Antivirus**, and then select **OK**. The workflow returns you to the **Add Rule** page.
6. On the **Add Rule** page, in **Step 1: Select Properties**, ensure the following are selected:

   - **When an update is in a specific classification**
   - **When an updates is in a specific product**
   - **Set a deadline for the approval**


   In **Step 2: Edit the properties**:


   - In **When an update is in**, ensure **Forefront Client Security, System Center Endpoint Protection, Microsoft Defender Antivirus** are listed.
   - In **Set a deadline for**, select **The same day as the approval at 5:00 AM**.


   In **Step 3: Specify a name**, type a name for your rule. For example, type *Microsoft Defender Antivirus updates*. These settings are shown in the following figure:


   [![Screenshot that shows a screen capture of an example name for a rule.](https://learn.microsoft.com/en-us/defender-endpoint/media/microsoft-defender-antivirus-deploy-ring-group-policy-wsus-updates-add-rule.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/microsoft-defender-antivirus-deploy-ring-group-policy-wsus-updates-add-rule.png#lightbox)

7. Select **OK**. The work flow returns to the **Update Rules** page. Select your new rule, For example, select **Microsoft Defender Antivirus updates**.
8. In **Rule Properties**, verify the information is correct, and then select **OK**.

#### Define the order of sources for downloading security intelligence updates

1. On your Group Policy management computer, open the **Group Policy Management Console**, right-click the *Group Policy Object* you want to configure and select **Edit**.
2. In the **Group Policy Management Editor**, go to **Computer configuration**, select **Policies**, then select **Administrative templates**.
3. Expand the tree to **Windows components** > **Windows Defender** > **Signature updates**.

   - Double-click the **Define the order of sources for downloading security intelligence updates** setting and set the option to **Enabled**.
   - In **Options**, type *InternalDefinitionUpdateServer*, and then select **OK**. The configured **Define the order of sources for downloading security intelligence updates** page is shown in the following figure.


   [![Screenshot that shows a screen capture of how to define the order of sources for downloading security intelligence updates.](https://learn.microsoft.com/en-us/defender-endpoint/media/microsoft-defender-antivirus-deploy-ring-group-policy-wsus-gp-download-order.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/microsoft-defender-antivirus-deploy-ring-group-policy-wsus-gp-download-order.png#lightbox)

For more information, see [Manage how and where Microsoft Defender Antivirus receives updates](https://learn.microsoft.com/en-us/defender-endpoint/manage-protection-updates-microsoft-defender-antivirus).

## See also

[Microsoft Defender Antivirus ring deployment](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-ring-deployment)

[Microsoft Defender Antivirus production ring deployment using Group Policy and Windows Server Update Services](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-production-ring-deployment-group-policy-wsus)
