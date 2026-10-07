<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/image-generator -->
<!-- Sitemap-Last-Modified: 2026-07-02 -->

# Add the image generator capability to your agent

The image generator capability enables declarative agents for Microsoft 365 Copilot to generate images based on user prompts. Image generator uses the existing [Designer](https://designer.microsoft.com/) functionality to create visually appealing and contextually relevant graphics, and includes the following features:

- **Multiple image generation**: For each user prompt, the agent generates four images.
- **Interactive image options**: Users can select each generated image to view it in full size. They can download, copy, or view content credentials for the full-size image. They can also select the side arrow to scroll through the four images.
- **Image modification**: Users can follow up with subsequent prompts to modify the original images without losing context. For example, first prompt: "Create a photo of a happy puppy running around in a yard." Second prompt: "Include a tennis ball."
- **Feedback mechanism**: Users can provide feedback on the generated images by giving a thumbs up or thumbs down. This feedback helps improve the quality of future image generations.
- **Clipboard and sharing**: Users can copy the generated images to their clipboard to paste into other applications, or they can share the generated images directly from the interface.

The image generator capability is available to Copilot Chat users with no metered usage or Microsoft 365 Copilot license. The availability of the image generator capability depends on the user's license and tenant configuration. For details, see [Agent capabilities and licensing models](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/prerequisites#agent-capabilities-and-licensing-models).

## Image generator examples

The following examples show what users can do with the image generation capability in your agent.

**User prompt**: Create an image of a serene beach at sunset with palm trees and gentle waves. The following image shows the result.

![Beach image response to the user prompt](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/image-gen-beach-prompt.png)

**User prompt**: Design a flyer for a summer music festival and add a date for May 15, 2024. The following image shows the result.

![Festival flyer image response to the user prompt](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/image-gen-flier-prompt.png)

## Enable image generator

### Agents Toolkit

If you're using [Microsoft 365 Agents Toolkit](https://aka.ms/M365AgentsToolkit) to create your agent, to enable image generator in your agent, add the `GraphicArt` value to the **capabilities** property in your manifest file, as shown in the following example.

Note

You must be using [version 1.2](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-manifest-1.2) or later of the declarative agent manifest schema to add the `GraphicArt` capability.

```json
{
  "capabilities": [
    {
      "name": "GraphicArt"
    }
  ]
}
```

### Agent Builder

![Screenshot of the Capabilities section in Agent Builder in Microsoft 365 Copilot.](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/capabilities-toggle.png) Image generator is always enabled in [Agent Builder](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder). This capability is automatically included for all agents.

Note

The image generator capability doesn't currently work in the **Try it** test pane in Agent Builder. Test image generation after publishing your agent.

## Related content

- [Microsoft 365 Copilot extensibility samples](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/samples)
- [Declarative agents overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/overview-declarative-agent)
- [Declarative agent manifest reference](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-manifest-1.8)
- [Add the code interpreter capability to your agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/code-interpreter)
- [Add knowledge sources to your declarative agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/knowledge-sources)
