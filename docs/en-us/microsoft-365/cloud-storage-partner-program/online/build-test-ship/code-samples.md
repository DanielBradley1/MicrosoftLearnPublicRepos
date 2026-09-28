<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/code-samples -->
<!-- Sitemap-Last-Modified: 2025-02-27 -->

# Example code

## Sample WOPI host

The [Microsoft 365 for the web GitHub repository](https://github.com/Microsoft/Office-Online-Test-Tools-and-Documentation) contains a [sample implementation of a WOPI host](https://github.com/Microsoft/Office-Online-Test-Tools-and-Documentation/tree/master/samples/SampleWopiHandler) written in C#. This sample implementation illustrates many of the concepts necessary to implement a WOPI server, including:

- Handling requests at particular [WOPI REST endpoints](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/endpoints)
- Handling WOPI operations such as [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo), [GetFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/getfile#getfile), and [PutFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putfile)
- Example [proof key verification](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/proofkeys) \(also see [Proof key unit tests](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/code-samples#proof-key-unit-tests)\)

## Proof key unit tests

Example test cases and data that can be used to validate proof key verification implementations can be found here: \[https://github.com/Microsoft/Office-Online-Test-Tools-and-Documentation/blob/master/samples/SampleWopiHandler/SampleWopiHandler.UnitTests/ProofKeyTests.cs\]\([https://github.com/Microsoft/Microsoft](https://github.com/Microsoft/Microsoft) 365-Test-Tools-and-Documentation/blob/master/samples/SampleWopiHandler/SampleWopiHandler.UnitTests/ProofKeyTests.cs\)

While these tests are written in C#, they can be adapted to any language. If you are having difficulties implementing proof keys, these test cases can be a useful tool for troubleshooting. See also the Troubleshooting proof key implementations section.

These same test cases along with basic proof key validation implementations are available in both Java and Python:

- Java: [https://github.com/Microsoft/Office-Online-Test-Tools-and-Documentation/blob/master/samples/java/ProofKeyTester.java](https://github.com/Microsoft/Office-Online-Test-Tools-and-Documentation/blob/master/samples/java/ProofKeyTester.java)
- Python: [https://github.com/Microsoft/Office-Online-Test-Tools-and-Documentation/blob/master/samples/python/proof\_keys/tests.py](https://github.com/Microsoft/Office-Online-Test-Tools-and-Documentation/blob/master/samples/python/proof_keys/tests.py)

Note that the Python samples depend on PyCrypto being installed.
