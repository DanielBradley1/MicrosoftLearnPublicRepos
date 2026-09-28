<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/shipping -->
<!-- Sitemap-Last-Modified: 2025-02-27 -->

# Launch your Microsoft 365 for the web integration

Once you believe you are ready to launch your integration, you need to submit your solution for verification testing by Microsoft to begin the launch process.

To enable your WOPI host to use the Microsoft 365 for the web [production environment](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/environments#production-environment), Microsoft will perform a verification of your WOPI implementation and Microsoft 365 for the web integration.

Important

Be sure that you have thoroughly reviewed all the information here before you start the launch process!

The launch process consists of two phases:

1. **Verification** - The Microsoft test team will review your WOPI solution's protocol and user experience implementation to ensure compliance with all requirements as outlined in the CSPP WOPI documentation and the Microsoft Cloud Storage Partner Program Integration Terms. The duration of the verification testing process will vary based on the number of issues our test team discovers with your solution and the speed with which you are able to resolve these issues. Each verification pass will take up to 10 days for the Microsoft test team to complete.

Important

You can avoid delays in verification by ensuring that your implementation is consistent with this documentation and that you've done manual testing using our [**testing guide**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/testing) and that the [**WOPI Validation application**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/validator) tests are passing before beginning the launch process.

  


Important

A large percentage of verification failures are a result of the partner not following the [**UI guidelines**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/ui-guidelines). Be sure that your solution is in complete compliance before you submit your solution for testing.

  


2. **Sign off and roll out** - Once Microsoft has signed off on your integration, your final domain configuration information will be entered into the WOPI production environment, which will take 4-5 weeks to deploy. When deployment is complete you can begin to roll out your WOPI solution to end-users. Depending on your traffic estimates, Microsoft may request that you roll out over a period of several days to ensure you do not overload Microsoft 365 for the web or your WOPI servers.

Use the [CSPP Verification Testing Submission form](https://aka.ms/cspp-verify) to begin the verification testing process.

Before starting the launch process, you should read the below sections for an overview of the types of questions and issues that you may need to address during the process.

## Preparing for the launch process

### WOPI verification

As part of the verification testing process, Microsoft will test your WOPI implementation using the [WOPI Validator](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/validator). To initiate verification testing you will need to provide a screen shot of the WOPI Validator showing that all of the tests in the following categories are passing:

- HostFrameIntegration \(ValidLanguagePlaceholderValues might be skipped if the host isn't using the [UI\_LLCC](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/discovery#ui_llcc) or [DC\_LLCC](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/discovery#dc_llcc) placeholder values\)
- BaseWopiViewing
- CheckFileInfoSchema
- EditFlows
- Locks
- PutRelativeFile **or** PutRelativeFileUnsupported
- RenameFileIfCreateChildFileIsNotSupported **or** RenameFileIfCreateChildFileIsSupported \(applicable only if the host supports [RenameFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/renamefile)\)
- FileVersion
- ProofKeys \([proof key validation](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/proofkeys)\)
- PutUserInfo \(applicable only if the host supports [PutUserInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putuserinfo#putuserinfo)\)

Important

*All* of the applicable tests listed above must pass in order to go to start verification testing. Do not submit your solution for verification testing until these tests are passing in the WOPI Validator.

Tip

Hosts are *not* required to support [RenameFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/renamefile), or [PutRelativeFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putrelativefile). However, hosts that do support these operations, or use application features that rely on them, must pass.

For example, [binary file conversion](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/conversion) requires the [PutRelativeFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putrelativefile) operation be implemented, so hosts that support conversion must also pass the PutRelativeFile tests.

### Manual testing

In addition to checking the WOPI Validator results, Microsoft does some manual verification of scenarios that can't currently be tested using the WOPI validator. You should follow the steps in the [testing guide](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/testing) and fully test these scenarios prior to starting the launch process.

Important

Even if you do not plan to use it in your current implementation, multi-user co-authoring must be implemented in all CSPP WOPI hosts. Your solution will not pass verification testing if we are unable to successfully complete multi-user co-authoring scenarios.

### Test accounts and video

In order to perform verification testing, the Microsoft verification test team needs to sign in to your WOPI solution. Our test team requires that you provide Microsoft **test accounts** in addition to **a video demonstrating the testing.**

#### Requirements

You must provide the following information when submitting your integration for verification:

- The Microsoft CSPP Test Team must have **two accounts in your WOPI solution.** They should be associated with the email addresses:

  - **[csppverify1@microsoft.com](mailto:csppverify1@microsoft.com)**
  - **[csppverify2@microsoft.com](mailto:csppverify2@microsoft.com)**
  - **Each of the test accounts you provide must:**

    - **Upload new files** of any file type you open with Microsoft 365 for the web, including `.wopitest` and `.wopitestx` files used by the WOPI Validator
    - **Open .wopitest files in the WOPI Validator**
    - The accounts **must be capable of testing multi-user co-authoring;** co-authoring with a single user account is not sufficient

- A login URL to use to sign in to your test system
- A video \(or several videos\) demonstrating the following scenarios **using the test accounts provided**

  - Upload a new `.wopitest` file and open it in the WOPI validator

    - Run all the WOPI Validator tests and capture the passing results in your video; [all tests listed in the documentation](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/testing) must be passing

  - Demonstrate your integration with **Word** by uploading a new Word document and editing it in Word on the web
  - Demonstrate your integration with **PowerPoint** by uploading a new PowerPoint document and editing it in PowerPoint for the web
  - Demonstrate your integration with **Excel** by uploading a new Excel document and editing it in Excel for the web
  - Open a document as two different user accounts and demonstrate multi-user coauthoring \([test details](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/testing#co-authoring)\)

    - If an explicit "share" action is needed to share a document between two users, demonstrate how to do this in your video

Important

Before you submit your WOPI solution for verification testing, ensure that you have thoroughly reviewed all the information here and that you are ready to provide [test accounts and videos](#test-accounts-and-video).

### WOPI implementation questionnaire

There are some aspects of your WOPI implementation that are particularly critical to the success of your integration. In order to verify these parts of your implementation, Microsoft asks you to answer some questions regarding your specific WOPI implementation. These questions are included below.

Note

This list of questions is subject to change.

1. Confirm that your File IDs meet the [criteria listed in the documentation](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#file-id). Microsoft 365 for the web expects file IDs to be unique and consistent over time, as well as when accessed by different users or via different UI paths \(for example, a given file might be available in two different parts of your UI, such as in a typical folder and also in search results. If the document is meant to be the same, then the file IDs should match. Otherwise, users will see unexpected behavior when they access the same file via different UI paths\).
2. Confirm you’re providing a user ID using the [UserId](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#userid) field and that the ID is unique and consistent over time [as described here](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#requirements-for-user-identity-properties).
3. Confirm that the value in the [OwnerId](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#ownerid) field represents the user who owns the document and is unique and consistent over time [as described here](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#requirements-for-user-identity-properties).
4. Are you sending the [SHA256](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-other#sha256) value in [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo)?
5. Are you using the [business user flow](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/business)?
6. What [WOPI host capabilities properties](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#wopi-host-capabilities-properties) are you passing in [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response)?
7. Do you use IPv6 in your datacenters?

### Production settings check

Prior to enabling your integration in the [production environment](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/environments#production-environment), Microsoft asks you to verify your current [Microsoft-configured settings](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/settings), including your entries in the [WOPI domain allow list](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/settings#wopi-domain-allow-list) and [Redirect domain allow list](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/settings#redirect-domain-allow-list).

Important

Changes to settings require time to make.

Any changes to Microsoft-configured settings **will take 4-5 weeks to fully roll out**. This includes changes to the [**WOPI domain allow list**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/settings#wopi-domain-allow-list), and applies to both the production and test environments.

### Service management contacts

Microsoft 365 for the web is a worldwide cloud service, and is thus monitored at all times. As part of the launch process, Microsoft provides you with information regarding how to escalate service quality issues with the Microsoft 365 for the web on-call engineers.

In order to use the [production environment](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/environments#production-environment), you must also provide a contact for Microsoft’s on-call engineers to reach if Microsoft 365 for the web detects an issue that we suspect is due to a problem on the host side. For example, Microsoft 365 for the web monitoring systems might detect error rates for sessions spiking, and the on-call engineer would contact the host to see if it's a known issue on the host side. Ideally this emergency contact can be reached 24x7, either by phone or email.

### Rollout schedule and traffic estimates

Typically, Microsoft asks partners to roll out over a period of time - between a few days to two weeks - depending on the anticipated traffic. For smaller hosts this is not always necessary. If you're already planning on doing this, you should communicate the schedule to Microsoft \(that is 10% day 1, 50% day 2, and so on.\). If you're not, you must coordinate with Microsoft to ensure this is appropriate given your traffic estimates.

In order to best plan the rollout, be prepared to provide Microsoft with updated traffic estimates. Ideally, these estimates are broken down by view and edit, file type, and geography, but provide whatever you can.

### Production access

Once you and Microsoft have agreed on a rollout plan and Microsoft has signed off on your WOPI implementation, your WOPI host is enabled in the [production environment](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/environments#production-environment). Plan to do some basic testing against the production environment prior to rollout to ensure there are no unique issues using that environment. Once you've completed that testing, you can roll your integration out to users according the agreed-upon rollout schedule.
