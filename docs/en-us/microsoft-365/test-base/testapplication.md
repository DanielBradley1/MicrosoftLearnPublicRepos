<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/test-base/testapplication?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2024-03-06 -->

# Creating and Testing Binary Files on Test Base

Important

**Test Base for Microsoft 365 will transition to end-of-life \(EOL\) on May 31, 2024.** We're committed to working closely with each customer to provide support and guidance to make the transition as smooth as possible. If you have any questions, concerns, or need assistance, [submit a support request](https://aka.ms/TestBaseSupport).

This section provides all the steps necessary to create a new package containing binary files, for uploading and testing on Test Base. If you already have a prebuilt .zip file, you can see [Uploading prebuilt Zip package](https://learn.microsoft.com/en-us/microsoft-365/test-base/uploadapplication?view=o365-worldwide), to upload your file.

Important

If you don't have a **Test Base** account, you need to create one before proceeding, as described in [Creating a Test Base account](https://learn.microsoft.com/en-us/microsoft-365/test-base/createaccount?view=o365-worldwide).

## Create a new package

In the [Azure portal](https://portal.azure.com/), go to the **Test Base** account for which you are creating and uploading your package and perform the steps that follow.

In the left-hand menu under **Package catalog**, select the **New package**. Then select the first card **'Create new package online'** to build your package online within 5 steps!

![Create a new Package wizard.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/testapplication01.png?view=o365-worldwide)

### Step 1: Define content

1. In the **Package source** section, select Binaries \(for example: .exe, .msi\) in the Package source type.

   ![Choose your package source.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/testapplication02.png?view=o365-worldwide)
2. Then upload your app file by clicking 'Select file' button or checking the box to use the Test Base sample template as a starting point if you don't have your file ready yet.

   ![Select file.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/testapplication03.png?view=o365-worldwide)
3. Type in your package's name and version in the **Basic information** section.

   Note

   The combination of package name and version must be unique within your Test Base account.

   ![Enter basic information.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/testapplication04.png?view=o365-worldwide)
4. After all the requested information is specified, you can proceed to the next phase by clicking the **Next: Configuration test** button.

   ![Next step.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/testapplication05.png?view=o365-worldwide)

### Step 2: Configure test

1. Select the **Type of test**. There are two test types supported:

   - An **Out of Box \(OOB\) test** performs an install, launch, close, and uninstall of your package. After the install, the launch-close routine is repeated 30 times before a single uninstall is run. The OOB test provides you with standardized telemetry on your package to compare across Windows builds.
   - A **Functional test** would execute your uploaded test scripts on your package. The scripts are run in the sequence you specified and a failure in a particular script will stop subsequent scripts from executing.
   - A **Flown Driven test** allows you to arrange your test scripts with enhanced flow control. To help you comprehensively validate the impact of an in-place Windows upgrade, you can use flow driven tests to execute your tests on both the baseline OS and target OS with a side-by-side test result comparison.


   Note


   Users can also select the preinstalled Microsoft apps option. This option will install Microsoft apps, like Office, before the user application is installed.


   Out of Box test is optional now.


   ![Out of Box test is optional.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/testapplication07.png?view=o365-worldwide)

2. Once all required info is filled out, you can move to step 3 by clicking the Next button at the bottom. A notification pops up when the test scripts are generated successfully.

   ![Generate script prompts.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/testapplication08.png?view=o365-worldwide)

### Step 3: Edit package

1. In the Edit package tab, you can

   - Check your package folder and file structure in **Package Preview**.
   - Edit your scripts online with the **PowerShell code editor**.


   Note


   Some sample scripts have been generated for your reference. You need to review each script carefully and replace the command and process name with your own.


   ![edit scripts online.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/testapplication09.png?view=o365-worldwide)

2. In the **Package Preview**, per your need, you can

   - Create a new folder.
   - Create a new script.
   - Upload a new file.


   ![Create resources.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/testapplication10.png?view=o365-worldwide)

3. Under **scripts folder**, sample scripts and script tags have been created for you. All script tags are editable. You can reassign them to reference your script paths.

   - If the **Out of Box test** is selected in step 2, you can see the **outofbox** folder under the scripts folder. You also have the option to add **'Reboot after install'** tag for the Install script.


   ![Reference script.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/testapplication11.png?view=o365-worldwide)


   Note


   Install, Launch, and Close script tags are mandatory for the OOB test type. Reassigning tags ensures that the correct script path will be used when testing is initiated.


   ![Edit package prompt.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/testapplication11-2.png?view=o365-worldwide)


   - If the **Functional test** is selected in step 2, you can see the **functional** folder under the scripts folder. More functional test scripts can be added using the **'Add to functional test list'** button. You need a minimum of one \(1\) script and can add up to eight \(8\) functional test scripts.


   ![Add to functional test list.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/testapplication12.png?view=o365-worldwide)


   Note


   At least 1 functional script tag is mandatory for the functional test type.


   To add more Functional scripts, you can select the **'Add to functional test list'**. Then the action panel pops up, you can:


   - Reorder the script paths by dragging with the left ellipse buttons. The functional scripts run in the sequence they're listed. A failure in a particular script stops subsequent scripts from executing.
   - Set 'Restart after execution' for multiple scripts.
   - Apply update before on specific script path. This is for users who wish to perform functional tests to indicate when the Windows Update patch should be applied in the sequence of executing their functional test scripts.


   ![functional test.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/testapplication13.png?view=o365-worldwide)

4. Once all required info is filled out, you can move to step 4 by clicking the Next button at the bottom.

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

   - Your selection registers your application for automatic test runs against the B release of Windows monthly quality updates of selected product\(s\).

     - For customers who have Default Access customers on Test Base, their applications are validated against the final release version of the B release security updates, starting from Patch Tuesday.
     - For customers who have Full Access customers on Test Base, their applications are validated against the prerelease versions of the B release security updates, starting up to 3-weeks before prior to Patch Tuesday. This allows time for the Full Access customers time to take proactive steps in resolving any issues found during testing before in advance of the final release on Patch Tuesday.  
       \(How to become a Full Access customer? Please refer to [Request to change access level \| Microsoft Docs](https://learn.microsoft.com/en-us/microsoft-365/test-base/accesslevel?view=o365-worldwide)\)

3. Configure **Feature Update**

   - To set up for feature updates, you must specify the target product and its preview channel from "Insider Channel" dropdown list.


   ![Screenshot shows Set test matrix configure featureupdate.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/settestmatrix04-configurefeatureupdate.png?view=o365-worldwide)


   - Your selection will register your application for automatic test runs against the latest feature updates of your selected product channel and all future new updates in the latest Windows Insider Preview Builds of your selection.
   - You may also set your current OS in "OS baseline for Insight". We would provide you more test insights by regression analysis of your as-is OS environment and the latest target OS.


   ![Screenshot shows Set test matrix set os.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/settestmatrix05-setos.png?view=o365-worldwide)

### Step 5: Review + publish

1. Review all the information for correctness and accuracy of your draft package. To make corrections, you can navigate back to early steps where you specified the settings as needed.

   ![Review package.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/testapplication15.png?view=o365-worldwide)
2. You can also check the notification box to receive the email notification of your package for the validation run completion notice.

   ![Notification.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/testapplication16.png?view=o365-worldwide)
3. When you're done finalizing the input data configuration, select **Publish** to upload your package to Test Base. The notification that follows displays when the package is successfully published and has entered the Verification process.

   Note

   The package must be verified before it's accepted for future tests. The Verification can take up to 24 hours, as it includes running the package in an actual test environment.

   ![Package publish prompts.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/testapplication17.png?view=o365-worldwide)
4. You're redirected to the **Manage Packages** page to check the progress of your newly uploaded package.

   ![Manage packages.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/testapplication18.png?view=o365-worldwide)

   Note

   When the Verification process is complete, the Verification status changes to Accepted. At this point, no further actions are required. Your package will be acquired automatically for execution whenever your configured operating systems have new updates available. If the Verification process fails, your package isn't ready for testing. Check the logs and assess whether any errors occurred. You may also need to check your package configuration settings for potential issues.

### Resume creation of a saved draft package

If you have any previous draft packages, you can view the list of your saved draft packages on the **New package** page. By clicking the **'Edit'** pencil icon, you can resume editing the package you selected from where you left off, as described in the **Status** column.

![New package page.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/testapplication19.png?view=o365-worldwide)

Note

The dashboard only shows the saved draft packages. To view published packages, you'll need to go to the Manage Packages page.
