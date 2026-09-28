<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/3-standard/security/standard-security-info-protection -->
<!-- Sitemap-Last-Modified: 2026-04-28 -->

# Step 3: Information protection

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/sections/standardsm.png)

Information protection is a critical aspect of managing sensitive data within educational institutions. This guide provides an overview of the information protection features available with an A3 educational license, including sensitivity labels, personal data encryption, and best practices for ensuring compliance with regulatory requirements.

## Requirements

- Microsoft 365 A3 license

## Roles and responsibilities

- IT Admin
- Identity Admin
- OneDrive Admin
- SharePoint Admin
- EXO Admin

## Manual default and mandatory sensitivity labels in Microsoft 365

In Microsoft 365, you can configure manual default and mandatory sensitivity labels to ensure that all documents and emails are appropriately classified and protected. These labels are useful in educational settings where sensitive information needs to be managed carefully.

- **Manual default sensitivity labels** allow users to apply a default label to new documents and emails. This setting ensures that all new content starts with a baseline level of protection, which users can then adjust as needed.
- **Mandatory sensitivity labels** require users to apply a label before they can save or send a document or email. This setting ensures that all content is classified and protected according to your institution's policies.

**Benefits in education:**

- **Consistent protection:** Ensures that all sensitive information is consistently classified and protected.
- **Compliance:** Helps meet regulatory requirements such as Family Educational Rights and Privacy Act \(FERPA\) by ensuring that student data is properly managed.
- **User awareness:** Increases user awareness of data protection policies and practices.

**To configure these labels:**

1. **Define sensitivity labels:** Create and configure sensitivity labels in the Microsoft Purview portal. Define the protection settings for each label, such as encryption, content marking, and access controls.
2. **Publish sensitivity labels:** Publish the labels to users by creating a label policy. You can specify which users or groups the policy applies to and configure settings like default labels and mandatory labeling.
3. **Set default labels:** In the label policy, you can specify a default label for new documents and emails. This label is applied automatically unless the user selects a different one.
4. **Enforce mandatory labeling:** To enforce mandatory labeling, configure the label policy to require users to apply a label before they can save or send content. This labeling can be enforced for specific types of content or across all content types.

## Sensitivity labels for containers in Microsoft 365

Sensitivity labels in Microsoft 365 can be applied to containers such as Microsoft Teams, Microsoft 365 Groups, and SharePoint sites. These labels help manage and protect sensitive information within educational institutions by controlling access and sharing settings.

Here are some key features of sensitivity labels for containers:

- **Privacy settings:** You can set the privacy level of Teams sites and Microsoft 365 Groups to either public or private.
- **External user access:** Control whether external users can access the content within these containers.
- **External sharing:** Manage external sharing settings for SharePoint sites.
- **Access from unmanaged devices:** Restrict access to content from unmanaged devices.
- **Authentication contexts:** Use authentication contexts to enforce additional security measures.
- **Discovery and sharing:** Prevent the discovery of private teams and control shared channels for team invitations.

These settings ensure that sensitive information is protected while still allowing for collaboration and productivity within the educational environment.

**Learn more:**

- [Use sensitivity labels to protect content in Microsoft Teams, Microsoft 365 groups, and SharePoint sites](https://learn.microsoft.com/en-us/purview/sensitivity-labels-teams-groups-sites)

## Personal data encryption

Personal data encryption is crucial in educational settings to protect sensitive information such as student records, grades, and personal details. Here are some key aspects of personal data encryption in education:

- **Compliance with regulations:** Educational institutions must comply with regulations like FERPA in the U.S., which mandates the protection of student education records.
- **Data encryption:** Encrypting data both at rest and in transit ensures that sensitive information is protected from unauthorized access. This includes encrypting databases, emails, and files stored on servers or cloud services.
- **Access controls:** Implementing strict access controls ensures that only authorized personnel can access sensitive data. This includes using multifactor authentication and role-based access controls.
- **Training and awareness:** Regular training for staff and students on data protection practices helps in maintaining a secure environment. This includes understanding the importance of encryption and how to handle sensitive information.
- **Use of secure platforms:** Utilizing secure online learning platforms that offer built-in encryption and privacy features can help protect personal data during online learning.

### Microsoft personal data encryption

Microsoft offers robust personal data encryption solutions to help educational institutions protect sensitive information. Here are some key aspects:

- **Personal data encryption \(PDE\):** Available in Windows 11, PDE provides file-based encryption using AES-CBC with a 256-bit key. It links encryption keys with user credentials through Windows Hello for Business, ensuring that data is only accessible when the user is signed in.
- **Microsoft 365 Security Controls:** Microsoft 365 includes various security features to protect personal data, such as encryption for emails and files, data loss prevention \(DLP\), and advanced threat protection.
- **Compliance and privacy:** Microsoft 365 helps educational institutions meet compliance standards like FERPA by providing tools to manage and protect student data effectively.
- **Configuration and management:** Personal Data Encryption can be configured using **Microsoft Intune** or Configuration Service Providers \(CSP\), allowing IT administrators to set policies and manage encryption settings across devices.

These features ensure that personal data within educational environments is secure and compliant with relevant regulations.

## BitLocker and BitLocker To Go

BitLocker and BitLocker To Go are powerful encryption tools provided by Microsoft to help protect data on devices and removable drives. They're useful in educational settings where safeguarding sensitive information is crucial.

**BitLocker** is a full disk encryption feature that helps protect the data on fixed drives \(like your computer's internal hard drive\). Here are some key points:

- **Encryption:** It encrypts the entire drive, making the data inaccessible without proper authentication.
- **Compatibility:** Available on Windows Pro, Enterprise, and Education editions.
- **Management:** Managed through the Control Panel or Group Policy. IT administrators can enforce encryption policies across the organization.

**BitLocker To Go** is designed specifically for encrypting removable drives such as USB flash drives and external hard drives. Key features include:

- **Encryption:** Encrypts data on removable drives, ensuring it remains secure even if the drive is lost or stolen.
- **User-friendly:** Easily accessible through the right-click menu in Windows Explorer, making it convenient for users to encrypt and decrypt data.
- **Compatibility:** Works with Windows 7 and later versions.

**Benefits in education:**

- **Data protection:** Ensures that sensitive educational data, such as student records and research data, is protected from unauthorized access.
- **Compliance:** Helps educational institutions comply with data protection regulations and policies.
- **Ease of use:** Both tools are integrated into the Windows operating system, making them easy to deploy and manage across multiple devices.

**Learn more:**

- [BitLocker Drive Encryption](https://support.microsoft.com/windows/bitlocker-drive-encryption-76b92ac9-1040-48d6-9f5f-d14b3c5fa178)

### Managing BitLocker in school

Managing BitLocker in schools involves setting up and maintaining encryption policies to protect sensitive data on both fixed and removable drives.

**To set up BitLocker:**

- Enable BitLocker:

  1. Go to **Control Panel > BitLocker Drive Encryption**.
  2. Select the drive you want to encrypt and select **Turn on BitLocker**.
  3. Choose an unlock method \(password or smart card\) and back up the recovery key.
  4. Complete the encryption process.

- Enable BitLocker To Go for removable drives:

  1. Insert the removable drive.
  2. Right-click the drive in Windows Explorer and select **Turn on BitLocker**.
  3. Follow the prompts to set up encryption and save the recovery key.

**To manage BitLocker policies:**

- Using Group Policy:

  1. Open the Group Policy Management Console \(GPMC\).
  2. Navigate to **Computer Configuration > Administrative Templates > Windows Components > BitLocker Drive Encryption**.
  3. Configure policies for operating system drives, fixed data drives, and removable data drives.

- Using Microsoft Intune:

  1. Sign in to the Microsoft Endpoint Manager admin center.
  2. Go to *Devices > Configuration profiles > Create profile*.
  3. Select **Windows 10 and later** and **Endpoint protection**.
  4. Configure BitLocker settings and assign the profile to the appropriate groups.

**Monitoring and recovery:**

1. Monitor BitLocker status:

   - Use the BitLocker Management Console or PowerShell to check the encryption status of drives.
   - Example PowerShell command: `Get-BitLockerVolume`

2. Manage recovery keys:

   - Store recovery keys securely in Active Directory or Microsoft Entra ID.
   - Use the BitLocker Recovery Password Viewer tool to retrieve recovery keys if needed.

**Training and support:**

1. Educate staff and students:

   - Provide training on how to use BitLocker and BitLocker To Go.
   - Ensure they understand the importance of encryption and how to handle recovery keys.

2. Provide support:

   - Set up a helpdesk to assist with BitLocker-related issues.
   - Ensure IT staff is trained to manage and troubleshoot BitLocker.

**Learn more:**

- [BitLocker operations guide](https://learn.microsoft.com/en-us/windows/security/operating-system-security/data-protection/bitlocker/operations-guide?tabs=powershell)
