<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/test-base/uploadapplication?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-05-21 -->

# Uploading a prebuilt zip package

Important

**Test Base for Microsoft 365 will transition to end-of-life \(EOL\) on May 31, 2024.** We're committed to working closely with each customer to provide support and guidance to make the transition as smooth as possible. If you have any questions, concerns, or need assistance, [submit a support request](https://aka.ms/TestBaseSupport).

This section provides all the steps necessary to edit, upload, and test on Test Base when you already have a prebuilt .zip file.

**Pre-requests**

- Test Base account: If you don't have a **Test Base** account, you'll need to create one before proceeding, as described in [Creating a Test Base account](https://learn.microsoft.com/en-us/microsoft-365/test-base/createaccount?view=o365-worldwide).
- Prebuilt .zip file: A .zip file built offline containing your application binary and test scripts. See [Build a package \| Microsoft Docs](https://learn.microsoft.com/en-us/microsoft-365/test-base/buildpackage?view=o365-worldwide) to prepare your Test Base .zip package from desktop.

## Upload an offline built package

In the [Azure portal](https://portal.azure.com/), go to the **Test Base** account for which you'll be creating and uploading your package and perform the steps that follow.

In the left-hand menu under **Package catalog**, select the **New package**. Then select the third card **'Upload pre-built package'**.

[![Left-hand menu.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/uploadingzip01-new-package.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/uploadingzip01-new-package.png?view=o365-worldwide#lightbox)

### Step 1: Define content

1. In the **Package source** section, select Prebuilt package \(.zip\) in the Package source type.

   [![New package.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/uploadingzip02-define-content.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/uploadingzip02-define-content.png?view=o365-worldwide#lightbox)
2. Upload your prebuilt package \(zip\) file by selecting 'Select file' button.
3. Type in your package's name and version in the **Basic information** section.

   Note

   The combination of package name and version must be unique within your Test Base account.

   ![Basic information.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/uploadingzip03-basic-information.png?view=o365-worldwide)
4. After all the requested information is specified, select the **Next: Configuration test** button.

   ![Next: Configuration test.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/uploadingzip04-next.png?view=o365-worldwide)

### Step 2: Configure test

1. Select the **Type of test** according to your prebuilt package. There are two test types supported:

   - An **Out of Box \(OOB\) test** performs an install, launch, close, and uninstall of your package. After the install, the launch-close routine is repeated 30 times before a single uninstall is run. The OOB test provides you with standardized telemetry on your package to compare across Windows builds.
   - A **Functional test** executes your uploaded test script\(s\) on your package. The scripts are run in the sequence you specified and a failure in a particular script will stop subsequent scripts from executing.


   Note


   Out of Box test is optional now.


   [![Out of Box test option.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/uploadingzip05-configure-test.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/uploadingzip05-configure-test.png?view=o365-worldwide#lightbox)

2. Once all required info is filled out, select the Next button.

### Step 3: Edit package

1. In the Edit package tab, you can:

   - check your package folder and file structure in **Package Preview**.
   - edit your scripts online with the **PowerShell code editor**.


   Note


   Your prebuilt package is extracted to edit. Script tags are added according to the script name, please review these script tags and adjust if need. Script tags indicate the correct script paths that will be used when testing is initiated.


   [![PowerShell code editor.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/uploadingzip06-edit-package.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/uploadingzip06-edit-package.png?view=o365-worldwide#lightbox)

2. In the **Package Preview**, per your need, you can:

   - create a new folder.
   - create a new script.
   - upload a new file.

3. Under **scripts folder**, sample scripts and script tags have been created for you. All script tags are editable. You can reassign them to reference your script paths.

   - If the **Out of Box test** is selected in step 2, you can see the **outofbox** folder under the scripts folder. You can also choose to add **'Reboot after install'** tag for the Install script.


   [![Sample scripts and script tags.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/uploadingzip07-edit-script.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/uploadingzip07-edit-script.png?view=o365-worldwide#lightbox)


   Note


   Install, Launch, and Close script tags are mandatory for the OOB test type. Reassigning tags ensures that the correct script path will be used when testing is initiated.


   [![Scripts missing notification.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/uploadingzip08-required-prompt.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/uploadingzip08-required-prompt.png?view=o365-worldwide#lightbox)


   - If the **Functional test** is selected in step 2, you can see the **functional** folder under the scripts folder. More functional test scripts can be added using the **'Add to functional test list'** button. You need a minimum of one \(1\) script and can add up to eight \(8\) functional test scripts.


   [![Add to functional test list.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/uploadingzip09-add-to-list.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/uploadingzip09-add-to-list.png?view=o365-worldwide#lightbox)


   Note


   At least 1 functional script tag is mandatory for the functional test type.


   Select **Add to functional test list** to add more functional scripts from the action panel. Here are the options:


   - Reorder the script paths by dragging with the left ellipse buttons. The functional scripts run in the sequence they're listed. A failure in a particular script stops subsequent scripts from executing.
   - Set 'Restart after execution' for multiple scripts.
   - Apply update before on specific script path. This update is for users who wish to perform functional tests to indicate when the Windows Update patch should be applied in the sequence of executing their functional test scripts.


   [![Functional test.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/uploadingzip10-functional-test.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/uploadingzip10-functional-test.png?view=o365-worldwide#lightbox)

4. Once all required info is filled out, you can proceed to step 4 by selecting the Next button at the bottom.

### Step 4: Set test matrix

The Test matrix tab is for you to indicate the specific Windows update program or Windows product that you may want your test to execute against.

![Screenshot shows Set test matrix new package.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/settestmatrix01-newpackage.png?view=o365-worldwide)

1. Choose **OS update type**

   - Test Base provides scheduled testing to make sure your applications performance won't break by the latest Windows updates.


   ![Screenshot shows Set test matrix choose osupdate.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/settestmatrix02-chooseosupdate.png?view=o365-worldwide)


   - There are 2 available options:

     - The **Security updates** enable your package to be tested against incremental churns of Windows monthly security updates.
     - The **Feature updates** enable your package to be tested against new features in the latest Windows Insider Preview Builds from the Windows Insider Program.

2. Configure **Security Update** To set up for security updates, you must specify the Windows products you want to test against from the dropdown list of "OS versions to test".

   ![Screenshot shows Set test matrix configure securityupdate.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/settestmatrix03-configuresecurityupdate.png?view=o365-worldwide)

   - Your selection will register your application for automatic test runs against the B release of Windows monthly quality updates of selected products.

     - For customers who have Default Access customers on Test Base, their applications are validated against the final release version of the B release security updates, starting from Patch Tuesday.
     - For customers who have Full Access customers on Test Base, their applications are validated against the prerelease versions of the B release security updates, starting up to 3-weeks before prior to Patch Tuesday. This allows time for the Full Access customers time to take proactive steps in resolving any issues found during testing before in advance of the final release on Patch Tuesday.  
       \(How to become a Full Access customer? Refer to [Request to change access level \| Microsoft Docs](https://learn.microsoft.com/en-us/microsoft-365/test-base/accesslevel?view=o365-worldwide)\)

3. Configure **Feature Update**

   - To set up for feature updates, you must specify the target product and its preview channel from "Insider Channel" dropdown list.


   ![Screenshot shows Set test matrix configure featureupdate.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/settestmatrix04-configurefeatureupdate.png?view=o365-worldwide)


   - Your selection will register your application for automatic test runs against the latest feature updates of your selected product channel and all future new updates in the latest Windows Insider Preview Builds of your selection.
   - You may also set your current OS in "OS baseline for Insight". We would provide you more test insights by regression analysis of your as-is OS environment and the latest target OS.


   ![Screenshot shows Set test matrix set os.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/settestmatrix05-setos.png?view=o365-worldwide)

### Step 5: Review + publish

1. Review all the information for correctness and accuracy of your draft package. To make corrections, you can navigate back to early steps where you specified the settings as needed.

   [![Review and publish.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/uploadingzip12-review.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/uploadingzip12-review.png?view=o365-worldwide#lightbox)
2. You can also check the notification box to receive the email notification of your package for the validation run completion notice.

   ![Notification.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/uploadingzip13-notification.png?view=o365-worldwide)
3. When you're done finalizing the input data configuration, select **Publish** to upload your package to Test Base. The notification that follows displays when the package is successfully published and has entered the Verification process.

   Note

   The package must be verified before it's accepted for future tests. The Verification can take up to 24 hours, as it includes running the package in an actual test environment.

   ![Publish success notification.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/uploadingzip14-success.png?view=o365-worldwide)
4. You'll be redirected to the **Manage Packages** page to check the progress of your newly uploaded package.

   [![Manage Packages.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/uploadingzip15-package-list.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/uploadingzip15-package-list.png?view=o365-worldwide#lightbox)

   Note

   When the Verification process is complete, the Verification status will change to Accepted. At this point, no further actions are required. Your package will be acquired automatically for execution whenever your configured operating systems have new updates available. If the Verification process fails, your package isn't ready for testing. Check the logs and assess whether any errors occurred. You may also need to check your package configuration settings for potential issues.

## Continue package creation

If you have any previous draft packages, you can view the list of your saved draft packages on the **New package** page. You can continue your edit directly to the step you paused last time by selecting the 'edit' pencil icon.

[![New package page.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/uploadingzip16-draft-packages.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/uploadingzip16-draft-packages.png?view=o365-worldwide#lightbox)

Note

The dashboard only shows the working in progress package. For the published package, you can check the Manage Packages page.
