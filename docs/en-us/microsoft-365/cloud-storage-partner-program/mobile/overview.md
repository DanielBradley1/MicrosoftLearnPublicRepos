<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/overview -->
<!-- Sitemap-Last-Modified: 2023-05-02 -->

# Integrate with Microsoft 365 for mobile

You can integrate with Microsoft 365 for mobile to enable your users to view and edit Excel, PowerPoint, and Word files directly on their mobile devices.

If you offer both iOS and Android experience, we recommend integrating both experiences simultaneously. But you can choose to onboard either of the experience first depending on your priority. Once you've onboarded to WOPI APIs for either one experience, Android or iOS, integrating with the other is minimal work.

![Figure 1 Editing a file in Office for iOS](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/images/scenario-edit.png)

***Figure 1 -** Editing a file in Office for iOS*

![Figure 2 Editing a file in Office for Android](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/images/scenario-edit-android.png)

***Figure 2 -** Editing a file in Office for Android*

If you deliver an iOS or Android experience that lets your users store Office files or include Office files as a key part of your solution, you can now integrate Microsoft 365 for mobile into your experience. This integration works directly against files stored by you. Your users won't need a separate storage solution to view and edit Office files.

## Edit and view Office files

When you integrate with Microsoft 365 for mobile, your users can view and edit Excel, PowerPoint, and Word files directly on a mobile device. The level of editing support is determined by the type of user and whether they have an Office 365 subscription.

## Integration process

Use the Web Application Open Platform Interface \(WOPI\) protocol to integrate Microsoft 365 for mobile with your application. The WOPI protocol enables Microsoft 365 for mobile to access and change files that are stored in your service.

To integrate your application with Microsoft 365 for mobile, do the following:

1. Become a member of the Office 365 - Cloud Storage Partner Program. Learn more about the program, as well as how to apply, at the [Office 365 Cloud Storage Partner Program](https://developer.microsoft.com/office/cloud-storage-partner-program) web site.
2. Provide the required on-boarding information as described in the section titled [Onboarding information](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/onboarding/onboarding).
3. Obtain your ProviderId and app store URLs from Microsoft. The app store URLs are the URLs you should use to launch Office on a platform’s app store.
4. Add your domain to the WOPI domain [allow list](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/settings#wopi-domain-allow-list). This is required even if you don't integrate with Office for the web so you can verify your WOPI integration with the [Validator](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/testing/validator).
5. Implement the WOPI protocol. The set of WOPI operations that must be supported is described in [WOPI implementation requirements for mobile integration](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/wopi-requirements).
6. Implement required changes to your app. Contact your Microsoft 365 for mobile integration contacts for directions on running Microsoft 365 for mobile in test mode for testing.
7. Run the [Validator](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/testing/validator) and fix any issues until the Validator reports a 100% pass rate.
8. Complete the manual testing outlined in the [Manual Validation section](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/testing/testcases) to verify the integration works as expected.
9. Once all manual test cases have a 100% pass rate, send your [Manual Validation report](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/testing/testcases) and directions to run your validator.
10. Once the Microsoft 365 for mobile team completes their manual testing, they work with you to schedule your launch date.

### Authentication

Authentication is handled by passing Microsoft 365 for mobile an access token that you generate from a Bootstrapper URL. Assign this token a reasonable expiration date. Also, we recommend that tokens be valid for a single user against a single file to help mitigate the risk of token leaks.

### Requirements

- Ensure that files are represented by a unique ID. See the full list of [File ID requirements](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#file-id).
- Have a mechanism for identifying file versions. See the [Version requirements](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#version).
- In order to integrate with Microsoft 365 for mobile, there are also promotional requirements which include:

  - Promoting Microsoft 365 for mobile integration somewhere within your app.
  - Promoting Microsoft 365 for mobile integration in the context of editing and viewing Office documents.
  - Using Office as the default app for opening Office documents within your app.

### Security considerations

Microsoft 365 for mobile is designed to work for enterprises with strict security requirements. To make your integration as secure as possible, ensure that:

- All traffic is SSL encrypted
- Server supports TLS 1.0+
- OAuth 2.0 is supported

## Interested?

If you’re interested in integrating your solution with Microsoft 365 for mobile, take a moment to register at [Office 365 Cloud Storage Partner Program](https://developer.microsoft.com/office/cloud-storage-partner-program).
