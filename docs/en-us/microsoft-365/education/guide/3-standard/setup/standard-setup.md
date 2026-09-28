<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/3-standard/setup/standard-setup -->
<!-- Sitemap-Last-Modified: 2025-08-22 -->

# Step 1: Standard operations and setup

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/sections/standardsm.png)

This article provides instructions and best practices for setting up and configuring Microsoft 365 services in educational organizations in the Standard \(A3 license\) for education.

## Requirements

- Microsoft A3 license

## Roles and responsibilities

- IT Admin
- Identity Admin
- OneDrive Admin
- SharePoint Admin
- EXO Admin

## DirectAccess supported \(Deprecated\)

Note

Microsoft formally deprecated DirectAccess. This means that while it's still available in current versions of Windows Server and Windows 11, it will be removed in future releases.

Microsoft recommends migrating to [**Always On VPN**](#always-on-vpn) as a replacement, which offers better integration with cloud services and supports conditional access without requiring domain-joined devices

DirectAccess is a valuable tool for educational institutions, providing seamless and secure remote access to network resources without the need for traditional VPN connections. This technology allows students, faculty, and staff to connect to the school's network from anywhere, ensuring they have continuous access to important applications and data. DirectAccess is beneficial in education because it simplifies the management of remote devices, ensuring they remain updated and secure. For example, administrators can manage Windows-based devices remotely, applying updates and security policies as needed1. Additionally, DirectAccess supports the Windows 10 Education SKU, making it a cost-effective solution for schools using this operating system. By implementing DirectAccess, educational institutions can enhance productivity, improve security, and provide a better user experience for their remote users.

**Key features:**

- **Seamless remote access:** Provides transparent access to internal network resources without the need for traditional VPN connections.
- **Always on:** Ensures that remote devices are always connected to the school's network, allowing continuous access to applications and data.
- **Simplified management:** Allows administrators to manage Windows-based devices remotely, applying updates and security policies as needed.
- **Enhanced security:** Uses certificates and secure tunnels to protect data and maintain a secure connection.
- **Cost-effective:** Supports the Windows 10 Education SKU, making it a budget-friendly solution for schools.
- **Improved user experience:** Eliminates the need for user intervention to connect, providing a smoother and more efficient remote access experience.
- **Scalability:** Can be deployed using existing infrastructure and supports flexible network deployment to ensure high availability.

## Always On VPN

Always On VPN \(AOVPN\) is a critical solution for enhancing security and accessibility in educational institutions. It ensures that all devices, whether on-campus or remote, maintain a secure and seamless connection to the school’s network. This consistent connection is vital for safeguarding sensitive data, such as student records and faculty communications, by encrypting traffic and minimizing exposure to cyber threats. Moreover, Always On VPN supports hybrid learning models by enabling students and educators to access educational resources, applications, and collaboration tools from anywhere without compromising security. By streamlining connectivity and protecting network integrity, Always On VPN fosters a safe and productive digital environment essential for modern education.

**Key features:**

- **Automatic connection**:

  - VPN initiates automatically at system boot-up
  - Eliminates the need for user interaction

- **Persistent security**:

  - Maintains an active encrypted connection at all times
  - Reduces the risk of data breaches and cyberattacks

- **Device and user authentication**:

  - Uses certificates, multifactor authentication \(MFA\), or single sign-on \(SSO\) for secure access

- **Centralized management**:

  - IT administrators can configure and enforce policies remotely.
  - Supports monitoring and logging of connections for compliance

- **Compatibility**:

  - Works with multiple operating systems \(Windows, macOS, iOS, Android\)
  - Supports BYOD \(Bring Your Own Device\) and institution-owned devices

**Benefits in education:**

- **Enhanced security**:

  - Protects sensitive student and staff data
  - Encrypts data traffic over public Wi-Fi networks

- **Improved accessibility**:

  - Seamless access to educational resources, such as LMS platforms, e-books, and research databases
  - Supports remote learning and hybrid education models

- **Compliance**:

  - Meets regulatory standards such as FERPA, GDPR, and CIPA
  - Provides audit trails for security compliance

- **Cost-effectiveness**:

  - Reduces risks and costs associated with data breaches
  - Centralized management minimizes IT overhead

**Implementation steps:**

1. **Needs assessment**:

   - Identify the requirements for students, staff, and faculty.
   - Evaluate network and device compatibility.

2. **VPN solution selection**:

   - Choose a solution that meets security, scalability, and usability needs.
   - Examples: Microsoft Always On VPN, Cisco AnyConnect, OpenVPN.

3. **Policy development**:

   - Define access control policies.
   - Specify which resources are accessible via the VPN.

4. **Deployment**:

   - Configure VPN profiles and distribute to devices.
   - Test connections for stability and performance.

5. **Monitoring and maintenance**:

   - Use analytics and logs to monitor VPN usage.
   - Regularly update software and configurations.

**Challenges:**

- **Performance issues**:

  - High network latency or reduced speed
  - Bandwidth limitations in high-demand scenarios

- **User resistance**:

  - Adapting to enforced VPN usage
  - Training and support may be required

- **Compatibility concerns**:

  - Older devices may face compatibility or performance issues

- **Costs**:

  - Initial setup and licensing fees for enterprise-grade solutions

**Best practices:**

- **Educate users**:

  - Conduct training on the importance of VPN security.
  - Provide easy-to-understand guides for troubleshooting.

- **Optimize performance**:

  - Use split tunneling to route only critical traffic through the VPN.
  - Monitor and upgrade network infrastructure to handle VPN traffic.

- **Regular Audits**:

  - Perform security and compliance audits.
  - Update policies and software as threats evolve.

- **Scalability Planning**:

  - Ensure the VPN solution can scale with the institution’s growth.
  - Plan for peak usage times, such as exam periods.

Always On VPN is a critical tool for modern education institutions to ensure secure, reliable, and seamless access to digital resources. By adopting best practices and addressing challenges, institutions can maximize the benefits of this technology while maintaining robust security and compliance standards.

**Learn more about Always On VPN:**

- [Why Choose Always On VPN](https://techcommunity.microsoft.com/t5/networking-blog/always-on-vpn-design-considerations-and-deployment-guidance/ba-p/1018466)  
  Explore the advantages and key considerations for using Always On VPN.
- [Always On VPN Deployment Guide](https://learn.microsoft.com/en-us/windows-server/remote/remote-access/vpn/always-on-vpn/deploy/always-on-vpn-deploy)  
  Step-by-step instructions for deploying Always On VPN in your environment.
- [Deploying Windows 10 Always On VPN with Microsoft Intune](https://techcommunity.microsoft.com/t5/intune-customer-success/deploying-windows-10-always-on-vpn-with-microsoft-intune/ba-p/337460)  
  A comprehensive guide for deploying Always On VPN using Microsoft Intune.
- [Troubleshooting Always On VPN](https://techcommunity.microsoft.com/t5/windows-it-pro-blog/troubleshooting-always-on-vpn/ba-p/987493)  
  Tips and tools for resolving common Always On VPN issues.
- [Secure Always On VPN Deployments](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/best-practices-for-securing-always-on-vpn/ba-p/1413093)  
  Best practices to ensure the security of your Always On VPN setup.
- [Microsoft Tech Community: Always On VPN Discussions](https://techcommunity.microsoft.com/t5/windows-server-for-it-pro/ct-p/WindowsServer)  
  Join the community to discuss best practices and troubleshoot issues with other IT professionals.

## Microsoft Editor premium features

Microsoft Editor's premium features offer significant benefits for educational settings, enhancing both teaching and learning experiences. With advanced grammar and style suggestions, students can improve their writing skills by receiving real-time feedback on their assignments and essays. The tool also provides clarity and conciseness suggestions, helping students to express their ideas more effectively. For educators, Microsoft Editor can help create clear and professional instructional materials, ensuring that communication with students is precise and error-free. Additionally, the plagiarism detection feature is invaluable in maintaining academic integrity, allowing educators to check for originality in student submissions. By integrating Microsoft Editor's premium features, educational institutions can foster better writing practices, support academic honesty, and enhance overall communication within the learning environment.

**Key features:**

- **Advanced grammar and style suggestions:** Helps students and educators improve their writing with real-time feedback on grammar, punctuation, and style.
- **Clarity and conciseness:** Provides suggestions to make writing clearer and more concise, aiding in effective communication.
- **Plagiarism detection:** Ensures academic integrity by checking for originality in student submissions.
- **Inclusiveness:** Offers suggestions to make writing more inclusive and considerate of diverse audiences.
- **Formal language:** Helps maintain a formal tone in academic and professional writing.
- **Text predictions:** Speeds up writing by predicting the next words or phrases.
- **Sentence rewrites:** Suggests alternative ways to phrase sentences for better readability and impact.
- **Synonyms and definitions:** Provides synonyms and definitions to enhance vocabulary and understanding.

**Learn more about Microsoft Editor premium features:**

- [Microsoft Editor Overview](https://www.microsoft.com/microsoft-365/microsoft-editor)  
  Explore how Microsoft Editor helps improve your writing across documents, emails, and web pages.
