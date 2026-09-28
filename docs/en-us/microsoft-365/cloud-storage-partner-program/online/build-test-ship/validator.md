<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/validator -->
<!-- Sitemap-Last-Modified: 2025-02-10 -->

# WOPI Validator

Important

Current status: Operational

Tip

The WOPI Validator is also available as an open-source tool. See [https://github.com/Microsoft/wopi-validator-core](https://github.com/Microsoft/wopi-validator-core) for more information.

To assist hosts in verifying their WOPI implementation, Microsoft 365 for the web provides a WOPI Validator that executes a test suite against a host’s WOPI implementation. The test suite verifies a variety of things, including that the semantics for all of the WOPI operations \([CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo), [GetFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/getfile#getfile), [PutFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putfile), etc.\) are correct and that request/response headers are set properly. New tests are added regularly.

The WOPI Validator is an Microsoft 365 for the web application similar to Word for the web or PowerPoint for the web. It uses the `.wopitest` file extension. The WOPI Validator is included in the [WOPI discovery](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/discovery) XML just like all other Microsoft 365 for the web applications.

Important

WOPI hosts should use the [**Test environment**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/environments#test-environment) to ensure that they are running the latest version of the WOPI Validator.

```xml
<app name="WopiTest" checkLicense="true">
    <action name="view" urlsrc="https://onenote.officeapps-df.live.com/hosting/WopiTestFrame.aspx" ext="wopitest"/>
    <action name="getinfo" urlsrc="https://onenote.officeapps-df.live.com/hosting/GetWopiTestInfo.ashx" ext="wopitest"/>
</app>
```

The Validator provides two [WOPI actions](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/discovery#wopi-actions), `view` and `getinfo`, which can be used to trigger the test suite.

Warning

The test suite will test operations like [PutFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putfile), so the contents of the `.wopitest` file will be destroyed.

In addition, some tests create new files or containers using the [PutRelativeFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putrelativefile), [CreateChildFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/createchildfile#createchildfile), and [CreateChildContainer](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/createchildcontainer) operations. While the Validator attempts to clean up these files, if there are errors in the WOPI implementation, these clean up actions may fail, leaving behind these test files.

If that should happen, you must clean up these test files manually. If you don’t, subsequent test runs may fail.

## Interactive WOPI validation

The simplest way to use the Validator is to use the *view* action. To use the *view* action hosts should treat `.wopitest` files the same way other Microsoft 365 documents are treated. In other words, hosts should do the following:

1. Launch a [host page](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/glossary#host-page) pointed at the `.wopitest` file. Ideally, this should be the same host page used to host regular Microsoft 365 for the web sessions. This will allow the Validator to test things like PostMessage and do some validation on the way the Microsoft 365 for the web iframe was loaded.
2. The host page will create and navigate the Microsoft 365 for the web iframe to the *view* action URL provided in [WOPI discovery](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/discovery#wopi-discovery). The [WOPIsrc](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#wopisrc) and [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token) should be provided just like with all other actions.
3. The WOPI Validator will load and display a number of test groups. Each test group can be expanded to reveal the individual tests that it contains. You can run tests individually, by test group, or run all tests using the `Run All` button.

   ![Figure 6 WOPI Validator UI](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/validator.png)


   ***Figure 6 -** WOPI Validator UI*

Tests can either pass, fail, or be skipped. Before executing any tests, Microsoft 365 for the web will do some basic validation \(e.g. confirm the file really has the `.wopitest` file extension\) and check any applicable pre-requisites. Any test whose pre-requisites are not met will simply be skipped. For example, the tests in the `EditFlows` test group require the [SupportsUpdate](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#supportsupdate) property to be set to `true`. If it is not, the tests in that group will all be skipped.

![Figure 7 Tests can pass, fail, or be skipped](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/validator-used.png)

***Figure 7 -** Tests can pass, fail, or be skipped*

Once a test has been run, you can click on it to see the each request that was issued by the test and the response data. If the test failed or was skipped, the reason will be displayed just under the test name. You can click on the specific request that failed and see more information about what the test was expecting. For [proof key validation](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/proofkeys), you can use the `Current Proof Key Data` and `Old Proof Key Data` buttons to see the intermediate data on how the request was signed, which is extremely useful when debugging proof key validation implementation.

![Figure 8 Example WOPI validation results](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/validator-error.png)

***Figure 8 -** Example WOPI validation results*

Tip

For ease of testing, we strongly recommend that hosts support the `.wopitest` file extension just like all other file extensions supported by Microsoft 365 for the web and included in [**WOPI discovery**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/discovery#wopi-discovery). This is especially important while testing, since it provides any user a quick and easy way to run the validation test suite.

## Automated WOPI validation

The WOPI Validator exposes a second action, `getinfo`. The `getinfo` action is designed to be used server-to-server. Instead of launching a [host page](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/glossary#host-page), the host can simply do the following:

1. Issue a [GET](https://tools.ietf.org/html/rfc7231#section-4.3.1) request to the *getinfo* action URL provided in WOPI discovery. The [WOPIsrc](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#wopisrc), [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token), and [access\_token\_ttl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#the-access_token_ttl-property) should be provided just like with all other actions.

   Note

   The `getinfo` action only supports [**GET**](https://tools.ietf.org/html/rfc7231#section-4.3.1) requests, so the [**access token**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token), an [**access\_token\_ttl**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#the-access_token_ttl-property) values must be appended to the URL instead of being passed as [**POST**](https://tools.ietf.org/html/rfc7231#section-4.3.3) parameters.
2. Microsoft 365 for the web will do some basic validation \(e.g. confirm the file really has the `.wopitest` extension\) and then return a JSON-formatted array of test URLs.
3. Hosts should then make a [GET](https://tools.ietf.org/html/rfc7231#section-4.3.1) request to each test URL. Microsoft 365 for the web will run the specified test and return results in a simple JSON object. No changes to the URL are needed; the necessary parameters are included already on the URL returned from the Validator.

This is intended for automated use. For example, a host may wish to run this validation as part of rolling out new versions of their WOPI host.

### Automated WOPI validation using a command-line tool

There are two options to automate WOPI validation. The first is to use the open-source validation tool at [https://github.com/Microsoft/wopi-validator-core](https://github.com/Microsoft/wopi-validator-core). This tool runs the same test suite as the hosted validator, but does not rely on any Microsoft 365 for the web server infrastructure. This make it ideal for use in automated testing or for testing servers that are not connected to the internet.

The second option is to use the Python-based command-line tool at [https://github.com/Microsoft/wopi-validator-cli-python](https://github.com/Microsoft/wopi-validator-cli-python) instead of launching a [host page](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/glossary#host-page). This tool uses the `getinfo` action URL provided in [WOPI discovery](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/discovery#wopi-discovery) to execute the WOPI Validator, so it is simply an alternative way of executing the test cases in the hosted Validator.
