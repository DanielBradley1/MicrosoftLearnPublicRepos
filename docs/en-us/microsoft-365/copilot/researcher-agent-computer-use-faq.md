<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/researcher-agent-computer-use-faq -->
<!-- Sitemap-Last-Modified: 2026-08-24 -->

# Researcher with Computer Use frequently asked questions

## General functionality

### How can I use Computer use with Researcher agent in Microsoft Copilot?

Researcher agent now provides `Computer Use` option for any prompt. Select the option to use Computer Use. Your admin must allow access to the feature before you can use Computer Use with Researcher. For more details see [Overview of Researcher with Computer Use](https://support.microsoft.com/en-us/topic/1f274537-6648-46e8-8264-052a49b92af4).

### How does Computer Use operate in the virtual machine?

When Computer Use is triggered, a sandbox environment dedicated to the conversation is created. This environment follows strict browser and network policies set by Microsoft. It's isolated from both the intranet and the user's device. Administrators can customize the sandbox by adding specific domains to allow or blocklists. Commands from the Researcher agent are sent securely. The sandbox environment doesn't persist for long-term use and is ephemeral. It can only access the web with enforced policies, and no user credentials are stored or transferred in or out of the Sandbox. The virtual machine runs on [Windows 365 for Agents](https://learn.microsoft.com/en-us/windows-365/agents/introduction-windows-365-for-agents) and hosts containers running Linux.

## Admin controls

### What controls do we have for administrators?

Admins can manage Computer Use settings, including enabling or disabling the feature, access to work content, and configuring allowed sites. For details, see [Researcher Agent with Computer Use admin configuration](https://learn.microsoft.com/en-us/microsoft-365/copilot/researcher-agent-computer-use).

### Can an admin or user restrict Computer Use with Researcher to certain people only \(for example a pilot group\)?

Yes- admins can limit Computer Use with Researcher to specific users or groups from the Microsoft 365 admin center.

## Privacy and security

### Is Researcher agent compliant for enterprise organizations?

Yes. Researcher is designed with enterprise security in mind. It operates within the Microsoft 365 data boundary and follows the same enterprise grade compliance and governance standards as Microsoft 365. Additionally, admins will have granular controls over the feature. For more details see [Researcher Agent with Computer Use admin configuration](https://learn.microsoft.com/en-us/microsoft-365/copilot/researcher-agent-computer-use).

### When are the screenshots taken?

Screenshots of the virtual machine are only taken when the model in control needs helps with navigation, reading content or tool access. Screenshots aren't taken when the user is in control for critical or sensitive action like authentication, confirming captcha, and so on, Users can access them in the conversation history in the Chain of Thought. Users can delete the conversation history to delete all the data associated with that conversation including the screenshots.

### Does Computer Use with Researcher follow the same security, compliance, privacy, and Responsible AI practices as Researcher agent?

Yes, Researcher with Computer Use follows all the security, privacy, compliance and Responsible AI policies. Additionally, we have implemented RAI checks for Computer use to further safeguard the use.

### How does the network proxy work with the safety classifiers?

Researcher's safety stack now goes beyond queries and tool outputs. Every network operation in the sandbox environment is inspected by an enhanced classifier designed to:  


- Check domain safety - ensure outbound web access is secure.
- Validate relevance - confirm the network request aligns with the user's query.
- Analyze content type - distinguish between image, binary data and text.

  
The added layer helps protect against XPIA or Jailbreak attacks that can be driven through web page navigation.

### How is Researcher agent in Microsoft Copilot evaluated?

Researcher agent in Microsoft Copilot was evaluated using extensive manual and automated testing, in addition to Microsoft's internal usage and public data. Further evaluation was conducted using custom datasets for offensive and malicious prompts \(user questions\) and responses.

### What should I do if I see inaccurate, harmful, or inappropriate content?

Copilot includes filters to block offensive language in the prompts and to avoid synthesizing suggestions in sensitive contexts. We continue to work on improving the filter system to more intelligently detect and remove offensive outputs. If you see offensive outputs, kindly submit feedback using the thumbs-up/thumbs-down icons so that we can improve our safeguards. Microsoft takes this feedback seriously and we're committed to addressing it.
