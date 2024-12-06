# What's New

### Advanced Filtering for Enhanced Precision  

The **Advanced Filtering** feature enhances FortiSOAR's search capabilities by allowing users to apply specific criteria to filter records. Whether it's filtering by severity, status, or priority, this functionality ensures that users can retrieve exactly the data they need, improving operational efficiency and decision-making.

### Voice Recognition for Hands-Free Interaction  

The **Voice Recognition** feature transforms the way users interact with FortiSOAR by enabling hands-free control. This innovation streamlines SOC tasks, offering users greater flexibility to issue commands and retrieve data efficiently using natural language.  

> [!Note]
> The *Voice Recognition* feature is currently unsupported on the Firefox browser as the webkit `SpeechRecognition` is not compatible with Mozilla Firefox. Hence, the mic button is not available when the FortiSOAR&trade; environment is accessed using the Firefox browser.

**Conversation Thread Management**

Previously, conversation threads were deleted from OpenAI whenever *Clear Conversation* was clicked, and a new thread was started with each new prompt.

Now, threads are retained within OpenAI, enabling improved historical reference and continuity. Each new prompt, after clearing the conversation. still initiates a fresh thread, and the *Clear Conversation* option within the user interface continues to clear conversation history, ensuring a clean workspace.