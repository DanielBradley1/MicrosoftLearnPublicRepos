<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/testing/validator -->
<!-- Sitemap-Last-Modified: 2023-05-02 -->

# Using the validator application to validate your WOPI implementation

Because WOPI is used in both the Office for the web and Microsoft 365 for mobile integrations, you can verify your WOPI implementation by following the instructions in the [WOPI Validator](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/validator) topic.

If you do not integrate with Office for the web, you can still verify your WOPI implementation using the above instructions by building a minimal [host page](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/glossary#host-page) and setting the [VALIDATOR\_TEST\_CATEGORY](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/discovery#validator_test_category) to `OfficeNativeClient`. This will run only the tests that are necessary for Microsoft 365 for mobile integration.

The Validator will not be able to verify the end-user experience entirely, so you must also perform manual validation.

Note

You will not be able to invoke any [WOPI actions](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/discovery#wopi-actions) successfully unless your WOPI domain has been added to the [WOPI domain allow list](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/settings#wopi-domain-allow-list).
