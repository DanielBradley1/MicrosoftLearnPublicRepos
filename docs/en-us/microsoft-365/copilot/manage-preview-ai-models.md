<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/manage-preview-ai-models -->
<!-- Sitemap-Last-Modified: 2026-09-02 -->

# Manage preview AI models in Microsoft Online Services

Preview AI models \(also referred to as experimental models\) are early-stage AI models that enable organizations to explore new capabilities. These models are optional and intended for evaluation, testing, and experimentation.

## What are preview AI models?

Preview AI models provide access to advanced capabilities ahead of general availability. These models help organizations evaluate emerging functionality, but they may have limitations in availability, reliability, performance, and support.

Preview and experimental models:

- Might be released before full general availability
- May change frequently
- May be removed or updated without notice

Important

Preview and experimental models are intended for exploration and testing and are not recommended for production use.

Note

"Preview" describes a model's release readiness; it doesn't, by itself, describe how the model handles your data. Preview models may include models hosted and operated by Microsoft, and models provided by AI subprocessors or independent processors.

- When a preview model is hosted and operated by Microsoft, it remains covered by the [Microsoft Product Terms](https://www.microsoft.com/licensing/terms), the [Microsoft Data Protection Addendum \(DPA\)](https://www.microsoft.com/licensing/docs/view/Microsoft-Products-and-Services-Data-Protection-Addendum-DPA), and applicable enterprise commitments including the [EU Data Boundary](https://learn.microsoft.com/en-us/privacy/eudb/eu-data-boundary-learn). Your data doesn't leave Microsoft.
- When a preview model is provided by an AI Subprocessor, the [Microsoft Product Terms](https://www.microsoft.com/licensing/terms) and [Microsoft Data Protection Addendum \(DPA\)](https://www.microsoft.com/licensing/docs/view/Microsoft-Products-and-Services-Data-Protection-Addendum-DPA) apply.
- When a preview model is provided by an independent processor, contractual commitments may vary depending on the AI provider and the terms for that specific model. For example, some models may require data retention by the AI model provider.

For more information about types of AI functionalities and models, see [Understanding AI functionality and models in Microsoft Online Services](https://learn.microsoft.com/en-us/microsoft-365/copilot/ai-models-overview).

## Model release types

AI models available in Microsoft Online Services can be categorized by release type:

- **Experimental**

  - Designed for early experimentation
  - Not intended for production use
  - May have significant limitations in availability, reliability, or performance

- **Preview**

  - Early access models that may evolve into generally available models
  - Not yet production-ready

- **Generally available \(GA\)**

  - Fully released models intended for production scenarios
  - Provide established reliability, support, and performance

- **Default**

  - The standard model selected for most scenarios
  - Typically the recommended GA model

Important

A model's release type reflects readiness. It doesn't, by itself, describe how the model handles data.

## Limitations of preview and experimental models

Preview and experimental models provide early access to new capabilities, but they also have important limitations:

- Performance can vary, including response quality and latency
- Models may be unavailable or experience interruptions
- Features and behavior may change without notice
- Availability may vary by region

Note

Use preview and experimental models only in test or evaluation scenarios.

## Data handling considerations for models with Data Retention by the AI provider

Some preview and experimental models require data retention by the model provider.

When these models are enabled:

- Prompts and responses may be processed and stored by the model provider
- Data handling is governed by the model provider's terms and policies
- Data may be processed outside your organization's geographic boundaries

Important

When a model requires data retention, the model provider, not Microsoft, controls how data is stored and processed.

Before enabling these models, review the provider's documentation and policies.

For example, [Anthropic Claude Fable 5](https://www-cdn.anthropic.com/d00db56fa754a1b115b6dd7cb2e3c342ee809620.pdf) is a Mythos-class model available as an optional Anthropic model with Data Retention in Microsoft Copilot. Tenant admins can opt-in to enable access to this model from the Microsoft 365 admin center. Your organization's use of Claude Fable 5 and other Anthropic models with Data Retention is subject to [Anthropic's Commercial Terms of Service](https://www.anthropic.com/legal/commercial-terms), [Anthropic's Data Protection Addendum](https://www.anthropic.com/legal/data-processing-addendum), and [data retention practices for Mythos-class models](https://support.claude.com/articles/15425996-data-retention-practices-for-mythos-class-models). For more information, see [Anthropic models in Microsoft Online Services](https://learn.microsoft.com/en-us/microsoft-365/copilot/connect-to-ai-subprocessor).

## Admin controls for preview AI models

Administrators manage access to preview and experimental models using settings in the Microsoft 365 admin center.

Admins can:

- Enable or disable preview models
- Restrict access to specific users or groups
- Configure access based on organizational requirements

Some models may require additional configuration, such as enabling access to external AI providers.

### Models disabled by default

Some preview models are disabled by default, including:

- Models with data retention by the provider
- Certain models hosted and operated by Microsoft to preserve customer choice around available models

## Best practices

To safely, evaluate preview AI models:

- Enable preview models only for targeted users or test groups
- Avoid using preview models in production workloads
- Communicate data handling expectations to users
- Review model provider documentation before enabling models with data retention
- Monitor usage and adjust access as needed

## Related articles

- [Understanding AI functionality and models in Microsoft Online Services](https://learn.microsoft.com/en-us/microsoft-365/copilot/ai-models-overview)
- [Data, Privacy, and Security for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-privacy)
- [Anthropic models in Microsoft Online Services](https://learn.microsoft.com/en-us/microsoft-365/copilot/connect-to-ai-subprocessor)
- [Assign AI provider access to users and groups](https://learn.microsoft.com/en-us/microsoft-365/copilot/copilot-ai-provider-user-sec-group-access)
- [Manage Copilot settings in Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-page)
- [About admin roles in Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles)
