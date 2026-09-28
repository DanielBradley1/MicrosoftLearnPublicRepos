<!-- Source: https://learn.microsoft.com/en-us/entra/standards/nist-authenticator-assurance-level-1 -->
<!-- Sitemap-Last-Modified: 2024-11-21 -->

# NIST authenticator assurance level 1 with Microsoft Entra ID

The National Institute of Standards and Technology \(NIST\) develops technical requirements for US federal agencies implementing identity solutions. Organizations must meet these requirements when working with federal agencies.

Before you begin authenticator assurance level 1 \(AAL1\), you can review the following resources:

- [NIST overview](https://learn.microsoft.com/en-us/entra/standards/nist-overview): Understand AAL levels
- [Authentication basics](https://learn.microsoft.com/en-us/entra/standards/nist-authentication-basics): Terminology and authentication types
- [NIST authenticator types](https://learn.microsoft.com/en-us/entra/standards/nist-authenticator-types): Authenticator types
- [NIST AALs](https://learn.microsoft.com/en-us/entra/standards/nist-about-authenticator-assurance-levels): AAL components, Microsoft Entra authentication methods, and Trusted Platform Modules \(TPMs\).

## Permitted authenticator types

To achieve AAL1, you can use any NIST single-factor or multifactor [permitted authenticator](https://learn.microsoft.com/en-us/entra/standards/nist-authenticator-types).

| Microsoft Entra authentication method | NIST authenticator type |
| --- | --- |
| Password  <br>QR Code \(PIN\) | Memorized Secret |
| Phone \(SMS\): Not recommended | Single-factor out-of-band |
| Microsoft Authenticator app \(Phone Sign-In\) | Multi-factor out-of-band |
| Single-factor software certificate | Single-factor crypto software |
| Multi-factor software certificate  <br>Windows Hello for Business with software TPM  <br> | Multi-factor crypto software |
| Multi-factor hardware protected certificate  <br>FIDO 2 security key  <br>Platform SSO for macOS \(Secure Enclave\)  <br>Windows Hello for Business with hardware TPM  <br>Passkey in Microsoft Authenticator | Multi-factor crypto hardware |

Tip

We recommend you select at a minimum phishing resistant AAL2 authenticators. Select AAL3 authenticators as necessary for business reasons, industry standards, or compliance requirements.

## FIPS 140 validation

### Verifier requirements

Microsoft Entra ID uses the Windows FIPS 140 Level 1 cryptographic module for its authentication cryptographic operations. It's therefore a FIPS 140-compliant verifier required by government agencies.

## Man-in-the-middle resistance

Communications between the claimant and Microsoft Entra ID are over an authenticated, protected channel, to resist man-in-the-middle \(MitM\) attacks. This configuration satisfies the MitM-resistance requirements for AAL1, AAL2, and AAL3.

## Next steps

[NIST overview](https://learn.microsoft.com/en-us/entra/standards/nist-overview)

[Learn about AALs](https://learn.microsoft.com/en-us/entra/standards/nist-about-authenticator-assurance-levels)

[Authentication basics](https://learn.microsoft.com/en-us/entra/standards/nist-authentication-basics)

[NIST authenticator types](https://learn.microsoft.com/en-us/entra/standards/nist-authenticator-types)

[Achieve NIST AAL1 with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/standards/nist-authenticator-assurance-level-1)

[Achieve NIST AAL2 with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/standards/nist-authenticator-assurance-level-2)

[Achieve NIST AAL3 with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/standards/nist-authenticator-assurance-level-3)
