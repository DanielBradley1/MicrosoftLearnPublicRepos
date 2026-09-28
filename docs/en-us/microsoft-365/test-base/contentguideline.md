<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/test-base/contentguideline?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2024-03-06 -->

# Test package guidelines

Important

**Test Base for Microsoft 365 will transition to end-of-life \(EOL\) on May 31, 2024.** We're committed to working closely with each customer to provide support and guidance to make the transition as smooth as possible. If you have any questions, concerns, or need assistance, [submit a support request](https://aka.ms/TestBaseSupport).

## 1. Script referencing

When you upload a .zip file to the portal, we unzip all the content of that file into a root folder. You do not need to write any code to do this initial unzip operation. You also can reference any file within the .zip by using the path relative to the zip file uploaded.

In the example below, we show how you can reference your binaries/scripts from the input field in the Tasks tab. The text in blue should be entered into the **Script path** field **without the quotation marks.**

It is important you are aware of the content within your zip file before uploading it. Often when zipping a folder, your local machine will create a main folder underneath the zip file. In this case, the referencing will be as shown in **bold** below:

**Contoso\_App\_Folder.zip**:

```console
├── Contoso_App_Folder

│   ├── file1.exe

│   ├── ScriptX.ps1

│   ├── folder1

│      ├── file3.exe

│      ├── script.ps1
```

- ScriptX.ps1 - **"Contoso\_App\_Folder/ScriptX.ps1"**
- Script.ps1 - **"Contoso\_App\_Folder/folder1/script.ps1"**

Other times, your zip file may have your files or content right underneath it \(for example, no 2nd-level folder\):

**Zip\_file\_uploaded.zip**:

```console
├── file1.exe

├── ScriptX.ps1

├── folder1

│   ├── file3.exe

│   ├── script.ps1
```

- ScriptX.ps1 - **"ScriptX.ps1"**
- Script.ps1 - **"folder1/script.ps1"**

## 2. Script execution

**Out-of-Box tests:** The application package needs to contain at least three PowerShell scripts. These scripts will execute unattended installing, launching, and closing of the application and its dependencies. Each script should handle checking its own prerequisites, validating its own success, and cleaning up after itself \(if necessary\).

**Functional tests:** The application package needs to contain at least one PowerShell script. Where more than one script is provided, the scripts are run in upload sequence and a failure in a particular script will stop subsequent scripts from executing.

### Script requirements

- PowerShell Version 5.1+
- Unattended execution
- Error return code
- Validate success
- Logging to script specific log folder

Each script needs to run unattended \(no user prompts\) to successfully execute in the test pipeline.

Note

Scripts should return "0" on successful completion and a non-zero error code if any error occurs during execution.

Each script should validate that it ran successfully. For example, the install script should check for the existence of certain binaries and/or registry keys on the system after the installer binary finishes executing. This check helps to ensure with a reasonable degree of confidence that the installation was successful.

Validation is necessary to properly diagnose where errors occur during a test run. For example, if the script is unable to install the application successfully versus being unable to launch it.

Important

**Avoid the following:**

- Scripts should not reboot the machine, if a reboot is necessary please specify this during the upload of your scripts.
- Do not modify the DNS Suffix Search List in Windows IP Configuration.

Important

The maximum disc space available is 127 Gb. Packages that consume more than this amount of space will not be executed.

Important

Packages that interact with the Windows UI must have the Autologon Credentials enabled to execute properly.

Important

Scripts within packages all have an execution time limit of 60 mins. Scripts execution after 60 minutes would time out.

## 3. Log collection

Each script should output any logs it generates into a folder named `logs`. All folders in the directory named `logs` will be copied and presented for download on the `Test Results` page.

For example, the installation script \(which may be located in the **App/scripts/install** directory\) can output its logs to: **logs/install.log**, such that the final log will be at: **Apps/scripts/install/logs/install.log**

The system will pick up the `install.log` file along with other files within other `logs` folders and collate it for download.

## 4. Application binaries

Any binaries and dependencies should be included in the single zip file.

These binaries should include everything necessary for installation of the application \(for example, the application installer\). If the application has a dependency on any frameworks, such as .NET Core/Standard or .NET Framework, these frameworks should be included in the file and referenced correctly in the provided scripts.

Note

The uploaded zip file cannot have any spaces or special characters in its name

## 5. Application/Test rules

In order for your applications/tests to run correctly under the Test Base infrastructure, they need to comply to the rules described in [Application/Test rules](https://learn.microsoft.com/en-us/microsoft-365/test-base/rules?view=o365-worldwide).

## Next steps

Advance to the next article to view some **Frequently Asked Questions \(FAQ\)**

[Next step](https://learn.microsoft.com/en-us/microsoft-365/test-base/faq?view=o365-worldwide)
