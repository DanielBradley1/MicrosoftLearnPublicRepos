<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/testing/testcases -->
<!-- Sitemap-Last-Modified: 2022-07-06 -->

# Microsoft 365 for mobile Manual Validation

Important

Contact [csppteam@microsoft.com](mailto:csppteam@microsoft.com) for instructions on how to access your mobile app in the QA environment.

You can test your WOPI Mobile integration using the steps outlined in [using the Validator to validate your WOPI implementation](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/testing/validator). However, the Validator will not be able to test the complete end-to-end experience. You must run the following tests manually to verify the integration works correctly.

After all manual and validator tests have passed, you're ready for Microsoft to validate that your app is ready for the production environment. You will need to provide Microsoft with the following so that we can perform verification testing:

1. A screenshot of your Validator results showing that all tests have passed
2. Test account information for use by Microsoft verification testers
3. The completed WOPI Mobile Testing Report
4. The exact name of your app as it appears in the Android and/or iOS stores

Email this information to [csppteam@microsoft.com](mailto:csppteam@microsoft.com).

Note

- *Company app/application* refers to your app.
- *Company service* refers to your service.
- Where you see a reference to *Microsoft 365*, please substitute Word, Excel and PowerPoint app. The tests should be re-run against each Microsoft 365 application.
- Please note the version of the Microsoft 365 app against which you tested.

## 1. Open from Company app: first install

*This test verifies the flow of using Microsoft 365 for the first time from the Company app. Repeat for each supported file type and each Microsoft 365 app.*

1. Start with a fresh install of Company app. Ensure Microsoft 365 is not installed.
2. Boot up Company app and log in.

**RESULT: General promotion for Microsoft 365 should be shown the first time after upgrading the company app.**

1. Browse to a supported file type.

**RESULT: “Open with Microsoft \[app\]” promotion, drawing attention to control and enabling open with Office once per first open for each supported file type. “Open with Microsoft \[app\]” should be the top choice if multiple choices are available. If a list is not shown, Microsoft 365 should be the default app for opening the file.**

1. Activate control to open in Microsoft 365.

**RESULT: The user should be sent to the app store page for the corresponding app.**

1. Install the Microsoft 365 app.
2. After installation, go back to the Company app and activate the control to open in Microsoft 365 again.

**RESULT: Microsoft 365 should start. The user should be prompted for credentials to Company service.**

1. Enter credentials for the company service.

**RESULT: File should open in read-only mode.**

1. Select `Sign In` and sign in with a free Microsoft Account.

**RESULT: File should open in edit mode if the user is a consumer and read-only mode if the user is a commercial user.**

1. Make changes \(you will need to sign in with a subscription account for testing a commercial user\).
2. Select `Back (<-)`.
3. Select `Open`.

**RESULT: Confirm that the company service is shown as a place.**

## 2. Open from Microsoft 365 for mobile: fresh install

*This test verifies the flow of using the Company service for the first time from Microsoft 365.*

1. Launch a fresh install of Microsoft 365.
2. Go through the First Run Experience.
3. Skip `Sign In`.
4. Go to `Open` > `Add a Place`.

**RESULT: The Company service shows up. Verify the name and icon of your service.**

1. Select your Company service.
2. Enter your credentials.

**RESULT: The root folder should show.**

1. Browse around the folder structure in your service.

**RESULT: Browse works as expected.**

1. Open a file from `Browse`.

**RESULT: The file should open in read-only mode.**

1. Select `Sign In` and sign in with a free Microsoft Account.

**RESULT: The file should open in edit mode if the user is a consumer and read-only mode if the user is a commercial user.**

1. Make changes \(you will need to sign in with a subscription account for testing a commercial user\).
2. Select `Back (<-)`.
3. Select `Open`.

**RESULT: The file should have the previously saved changes. Ensure changes are being saved on Company service.**

## 3. Open from Company app: repeat usage

Repeat test 1, except with the Company service already added \(from previous usage\).

## 4. Open from Office for Mobile: repeat usage

Repeat test 2, except with the Company service already added \(from previous usage\).

## 5. Save as/duplicate

Verify the ability to duplicate a file to the Company service, both by adding a new place and by using an existing place.

## 6. Create new \[name\]

Verify the ability to create a new file saved to the Company service, both by adding a new place and by using an existing place.

## 7. Verify licensing

Verify that editing a file for a commercial user requires O365 subscription or else it opens read only.

Important

Go to *Settings > \[Microsoft App\] > Reset Word > Delete Sign-In Credentials* and restart Microsoft 365 before doing this test.

## 8. OAuth login page

Verify there is a link to the company’s privacy statement on the company’s login page when the user adds the Company service as a place.

Verify that the login page fits in the window of supported devices.

## 9. Verify file properties

Verify file properties from `Recent` and from an opened file. When opening the properties from the `Recent` tab or the `Open` tab, the *Author*, *Created*, *Modified By*, and *Company* fields will be empty.

## 10. Change passwords

*This test verifies the flow of using the Company service after the user changes passwords.*

Note

This test changes based on how the Company service handles authentication and refresh/access tokens. If you invalidate the access and refresh token after the user changes their password, run this test. You can adapt this test to ensure the Microsoft 365 app is handling refresh and access tokens correctly.

1. Launch a fresh install of Microsoft 365.
2. Go through the First Run Experience.
3. Skip `Sign In`.
4. Go to `Open` > `Add a Place`.
5. Select your Company service.
6. Enter your credentials.
7. Browse around the folder structure in your service.
8. Open a file from `Browse`.
9. Select `Sign in` and sign in with a free Microsoft Account.
10. Make changes \(you will need to sign in with a subscription account for testing a commercial user\).
11. Select `Back`.
12. On the Company service app, change the user's password.
13. Open the Microsoft 365 for mobile app, browse to the Company service, and open a file.

**RESULT: You should be prompted to enter credentials again.**
