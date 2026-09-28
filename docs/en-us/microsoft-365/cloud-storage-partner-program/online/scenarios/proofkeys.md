<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/proofkeys -->
<!-- Sitemap-Last-Modified: 2025-02-27 -->

# Verify that requests originate from Microsoft 365 for the web by using proof keys

When processing WOPI requests from Microsoft 365 for the web, you must verify that these requests are coming from Microsoft 365 for the web. To do this, you use proof keys.

Microsoft 365 for the web signs every WOPI request with a private key. The corresponding public key is available in the **proof-key** element in the WOPI discovery XML. The signature is sent with every request in the **X-WOPI-Proof** and **X-WOPI-ProofOld** HTTP headers.

The signature is assembled from information that's available to the WOPI host when it processes the incoming WOPI request. To verify that a request came from Microsoft 365 for the web, you:

- Create the expected value of the proof headers.
- Use the public key provided in WOPI discovery to decrypt the proof provided in the **X-WOPI-Proof** header.
- Compare the expected proof to the decrypted proof. If they match, the request originated from Microsoft 365 for the web.
- Ensure that the **X-WOPI-TimeStamp** header is no more than 20 minutes old.

When validating proof keys, if a request isn't signed properly, the host must return a [500 Internal Server Error](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.1).

Note

Requests to the [**FileUrl**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#fileurl) aren't signed. The FileUrl is used exactly as provided by the host, so it doesn't necessarily include the access token, which is required to construct the expected proof.

Tip

The [**Microsoft 365 for the web GitHub repository**](https://github.com/Microsoft/Office-Online-Test-Tools-and-Documentation) contains a set of unit tests that hosts can adapt to verify proof key validation implementations. For more information, see [**Proof key unit tests**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/code-samples#proof-key-unit-tests).

## Constructing the expected proof

To construct the expected proof, you assemble a byte array consisting of the access token, the URL of the request \(in uppercase\), and the value of the **X-WOPI-TimeStamp** HTTP header from the request. Each of these values must be converted to a byte array. In addition, you include the length, in bytes, of each of these values.

To convert the access token and request URL values, which are strings, to byte arrays, ensure the original strings are in UTF-8 first, then convert the UTF-8 strings to byte arrays. Convert the **X-WOPI-TimeStamp** header to a *long* and then into a byte array. Don't treat it as a string.

Then, assemble the data as follows:

- Four bytes that represent the length, in bytes, of the `access_token` on the request.
- The `access_token`.
- Four bytes that represent the length, in bytes, of the full URL of the WOPI request, including any query string parameters.
- The WOPI request URL in uppercase. All query string parameters on the request URL should be included.
- Four bytes that represent the length, in bytes, of the **X-WOPI-TimeStamp** value.
- The **X-WOPI-TimeStamp** value.

The following code samples show the construction of an expected proof in C#, Java, and Python.

***Code sample 3*** - *Constructing the expected in proof in C#*

```C#
public bool Validate(ProofKeyValidationInput testCase)
{
    // Encode values from headers into byte[]
    var accessTokenBytes = Encoding.UTF8.GetBytes(testCase.AccessToken);
    var hostUrlBytes = Encoding.UTF8.GetBytes(testCase.Url.ToUpperInvariant());
    var timeStampBytes = EncodeNumber(testCase.Timestamp);

    // prepare a list that will be used to combine all those arrays together
    List<byte> expectedProof = new List<byte>(
        4 + accessTokenBytes.Length +
        4 + hostUrlBytes.Length +
        4 + timeStampBytes.Length);

    expectedProof.AddRange(EncodeNumber(accessTokenBytes.Length));
    expectedProof.AddRange(accessTokenBytes);
    expectedProof.AddRange(EncodeNumber(hostUrlBytes.Length));
    expectedProof.AddRange(hostUrlBytes);
    expectedProof.AddRange(EncodeNumber(timeStampBytes.Length));
    expectedProof.AddRange(timeStampBytes);

    // create another byte[] from that list
    byte[] expectedProofArray = expectedProof.ToArray();

    // validate it against current and old keys in proper combinations
    bool validationResult =
        TryVerification(expectedProofArray, testCase.Proof, _currentKey.CspBlob) ||
        TryVerification(expectedProofArray, testCase.OldProof, _currentKey.CspBlob) ||
        TryVerification(expectedProofArray, testCase.Proof, _oldKey.CspBlob);

    // TODO:
    // in real code you should also check that TimeStamp header is no more than 20 minutes old
    // but because we're using predefined test cases to validate that the method works
    // we can't do it here.
    return validationResult;
}
```

## Retrieving the public key

Microsoft 365 for the web provides two different public keys as part of the WOPI discovery XML: the current key and the old key. Two keys are necessary because the discovery data is meant to be cached by the host, and Microsoft 365 for the web periodically rotates the keys it uses to sign requests. When the keys are rotated, the current key becomes the old key, and a new current key generates. This helps minimize the risk that a host doesn't have updated key information from WOPI discovery when Microsoft 365 for the web rotates keys.

Both keys are represented in the discovery XML in two different formats. One format is for WOPI hosts that use the .NET framework. The other format can be imported in a variety of different programming languages and platforms.

### Using .NET to retrieve the public key

If your application is built on the .NET framework, use the contents of the `value` and `oldvalue` attributes of the `proof-key` element in the WOPI discovery XML. These two attributes contain the Base64-encoded public keys that are exported by using the [RSACryptoServiceProvider.ExportCspBlob](https://msdn.microsoft.com/library/system.security.cryptography.rsacryptoserviceprovider.exportcspblob\(v=vs.110\).aspx) method of the .NET Framework.

To import this key in your application, decode it from Base64 then import it by using the [RSACryptoServiceProvider.ImportCspBlob](https://msdn.microsoft.com/library/system.security.cryptography.rsacryptoserviceprovider.importcspblob\(v=vs.110\).aspx) method.

### Using the RSA modulus and exponent to retrieve the public key

For hosts that don’t use the .NET framework, Microsoft 365 for the web provides the RSA modulus and exponent directly. The modulus and exponent of the current key are found in the `modulus` and `exponent` attributes of the *proof-key* element in the WOPI discovery XML. The modulus and exponent of the old key are found in the `oldmodulus` and `oldexponent` attributes. All four of these values are Base64-encoded.

The steps to import these values differ based on the language, platform, and cryptography API that you're using.

The following examples show how to import the public key by using the modulus and exponent in both Java and Python \(using the PyCrypto library\).

### Java

***Code sample 4*** - *Generating a public key from a modulus and exponent in Java*

```Java
private static RSAPublicKey getPublicKey( String modulus, String exponent ) throws Exception
{
    BigInteger mod = new BigInteger( 1, DatatypeConverter.parseBase64Binary( modulus ) );
    BigInteger exp = new BigInteger( 1, DatatypeConverter.parseBase64Binary( exponent ) );
    KeyFactory factory = KeyFactory.getInstance( "RSA" );
    KeySpec ks = new RSAPublicKeySpec( mod, exp );

    return (RSAPublicKey) factory.generatePublic( ks );
}
```

### Python

***Code sample 5*** - *Generating a public key from a modulus and exponent in Python*

```Python
def generate_key(modulus_b64, exp_b64):
    """
    Generates an RSA public key given a base64-encoded modulus and exponent
    :param modulus_b64: base64-encoded modulus
    :param exp_b64: base64-encoded exponent
    :return: an RSA public key
    """
    mod = int(b64decode(modulus_b64).encode('hex'), 16)
    exp = int(b64decode(exp_b64).encode('hex'), 16)
    seq = asn1.DerSequence()
    seq.append(mod)
    seq.append(exp)
    der = seq.encode()
    return RSA.importKey(der)
```

## Verifying the proof keys

After you import the key, you can use a verification method provided by your cryptography library to verify incoming requests are signed by Microsoft 365 for the web. Because Microsoft 365 for the web rotates the current and old proof keys periodically, you have to check three combinations of proof key values:

- The **X-WOPI-Proof** value using the current public key
- The **X-WOPI-ProofOld** value using the current public key
- The **X-WOPI-Proof** value using the old public key

If any one of the values is valid, the request is signed by Microsoft 365 for the web.

The following examples show how to verify one of these combinations in C#, Java, and Python.

### Verification in C#

***Code sample 6*** - *Sample proof key validation code in C#*

```C#
private static bool TryVerification(byte[] expectedProof,
    string signedProof,
    string publicKeyCspBlob)
{
    using(RSACryptoServiceProvider rsaAlg = new RSACryptoServiceProvider())
    {
        byte[] publicKey = Convert.FromBase64String(publicKeyCspBlob);
        byte[] signedProofBytes = Convert.FromBase64String(signedProof);
        try
        {
            rsaAlg.ImportCspBlob(publicKey);
            return rsaAlg.VerifyData(expectedProof, "SHA256", signedProofBytes);
        }
        catch(FormatException)
        {
            return false;
        }
        catch(CryptographicException)
        {
            return false;
        }
    }
}
```

### Verification in Java

***Code sample 7*** - *Sample proof key validation code in Java*

```Java
public static boolean verifyProofKey( String strModulus, String strExponent,
    String strWopiProofKey, byte[] expectedProofArray ) throws Exception
{
    PublicKey publicKey = getPublicKey( strModulus, strExponent );

    Signature verifier = Signature.getInstance( "SHA256withRSA" );
    verifier.initVerify( publicKey );
    verifier.update( expectedProofArray ); // Or whatever interface specifies.

    final byte[] signedProof = DatatypeConverter.parseBase64Binary( strWopiProofKey );

    return verifier.verify( signedProof );
}
```

### Verification in Python

***Code sample 8*** - *Sample proof key validation code in Python*

```Python
def try_verification(expected_proof, signed_proof_b64, public_key):
    """
    Verifies the signature of a signed WOPI request using a public key provided in
    WOPI discovery.
    :param expected_proof: a bytearray of the expected proof data
    :param signed_proof_b64: the signed proof key provided in the X-WOPI-Proof or
    X-WOPI-ProofOld headers. Note that the header values are base64-encoded, but
    will be decoded in this method
    :param public_key: the public key provided in WOPI discovery
    :return: True if the request was signed with the private key corresponding to
    the public key; otherwise, False
    """
    signed_proof = b64decode(signed_proof_b64)
    verifier = PKCS1_v1_5.new(public_key)
    h = SHA256.new(expected_proof)
    v = verifier.verify(h, signed_proof)
    return v
```

## Proof key tests in the WOPI validator

The WOPI validator includes several tests that help verify proof key implementations.

### ProofKeys.CurrentValid.OldValid

Tests that hosts accept requests where the **X-WOPI-Proof** value is correctly signed with the current proof key, and the **X-WOPI-ProofOld** value is signed with the old proof key.

### ProofKeys.CurrentValid.OldInvalid

Tests that hosts accept with requests where the **X-WOPI-Proof** value is correctly signed with the current proof key, but the **X-WOPI-ProofOld** value is invalid. This scenario is unusual and shouldn't happen in a production environment, but since the **X-WOPI-Proof** value is signed with the current public key, the request should be accepted.

### ProofKeys.CurrentInvalid.OldValidSignedWithCurrentKey

Tests that hosts accept with requests where the **X-WOPI-Proof** value is invalid but the **X-WOPI-ProofOld** value is signed with *current* public key. This can happen when a WOPI client such as Microsoft 365 for the web has rotated proof keys but the host hasn’t re-run [WOPI discovery](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/discovery) yet.

#### ProofKeys.CurrentValidSignedWithOldKey.OldInvalid

Tests that hosts accept with requests where the **X-WOPI-ProofOld** value is invalid but the **X-WOPI-Proof** value is signed with *old* public key. This can happen when a WOPI client has rotated proof keys, the host has re-run [WOPI discovery](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/discovery) and has the updated keys, but the datacenter machine making the WOPI request doesn't yet have the updated keys.

### ProofKeys.CurrentInvalid.OldValidSignedWithOldKey

Tests that hosts reject with requests where the **X-WOPI-Proof** value is invalid, and the **X-WOPI-ProofOld** value is signed with the *old* public key. This scenario is unusual and shouldn't happen in a production environment; such requests should be rejected.

### ProofKeys.CurrentInvalid.OldInvalid

Tests that hosts reject that contain requests with invalid current and old proof keys.

### ProofKeys.TimestampOlderThan20Min

Tests that hosts reject that contain requests with an **X-WOPI-Timestamp** value, which represents a time more than 20 minutes old.

## Troubleshooting proof key implementations

If you're having difficulty with your proof key verification implementation, following are common issues to investigate:

- Verify you’re converting the URL to uppercase.
- Verify you’re including any query string parameters on the URL when transforming it for the purposes of building the expected proof value.
- Verify you’re using the same encoding for any special characters that may be in the URL.
- Verify you’re using an HTTPS URL if your WOPI endpoints are HTTPS. This is especially important if you have SSL termination in your network prior to your WOPI request handlers. In this case, the URL Microsoft 365 for the web uses to sign the requests will be HTTPS, but the URL your WOPI handlers ultimately receive will be HTTP. If you simply use the incoming request URL your expected proof won't match the signature provided by Microsoft 365 for the web.

In addition, use the Proof key unit tests to verify your implementation with sample data.
