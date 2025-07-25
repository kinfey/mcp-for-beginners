<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "4d5b044c0924d393af3066e03d7d89c5",
  "translation_date": "2025-07-16T09:40:37+00:00",
  "source_file": "03-GettingStarted/01-first-server/README.md",
  "language_code": "mr"
}
-->
### -2- प्रोजेक्ट तयार करा

आता तुमच्याकडे SDK इन्स्टॉल झाले आहे, तर पुढे प्रोजेक्ट तयार करूया:

### -3- प्रोजेक्ट फाइल्स तयार करा

### -4- सर्व्हर कोड तयार करा

### -5- एक टूल आणि एक रिसोर्स जोडा

खालील कोड जोडून एक टूल आणि एक रिसोर्स जोडा:

### -6 अंतिम कोड

सर्व्हर सुरू होण्यासाठी आवश्यक शेवटचा कोड जोडूया:

### -7- सर्व्हरची चाचणी करा

खालील कमांड वापरून सर्व्हर सुरू करा:

### -8- इन्स्पेक्टर वापरून चालवा

इन्स्पेक्टर हा एक उत्कृष्ट टूल आहे जो तुमचा सर्व्हर सुरू करतो आणि तुम्हाला त्याच्याशी संवाद साधण्याची परवानगी देतो, ज्यामुळे तुम्ही त्याचा कार्यप्रदर्शन तपासू शकता. चला ते सुरू करूया:
> [!NOTE]
> "command" फील्डमध्ये ते वेगळं दिसू शकतं कारण त्यात तुमच्या विशिष्ट runtime सह सर्व्हर चालवण्यासाठीचा कमांड असतो/
तुम्हाला खालील वापरकर्ता इंटरफेस दिसेल:

![Connect](/03-GettingStarted/01-first-server/assets/connect.png)

1. Connect बटण निवडून सर्व्हरशी कनेक्ट व्हा  
  एकदा तुम्ही सर्व्हरशी कनेक्ट झाल्यावर, तुम्हाला खालील दिसेल:

  ![Connected](/03-GettingStarted/01-first-server/assets/connected.png)

1. "Tools" आणि "listTools" निवडा, तुम्हाला "Add" दिसेल, "Add" निवडा आणि पॅरामीटर मूल्ये भरा.

  तुम्हाला खालील प्रतिसाद दिसेल, म्हणजे "add" टूलचा निकाल:

  ![Result of running add](/03-GettingStarted/01-first-server/assets/ran-tool.png)

अभिनंदन, तुम्ही तुमचा पहिला सर्व्हर तयार करून चालवला आहे!

### अधिकृत SDKs

MCP अनेक भाषांसाठी अधिकृत SDKs प्रदान करते:

- [C# SDK](https://github.com/modelcontextprotocol/csharp-sdk) - Microsoft सह सहयोगाने देखभाल केली जाते
- [Java SDK](https://github.com/modelcontextprotocol/java-sdk) - Spring AI सह सहयोगाने देखभाल केली जाते
- [TypeScript SDK](https://github.com/modelcontextprotocol/typescript-sdk) - अधिकृत TypeScript अंमलबजावणी
- [Python SDK](https://github.com/modelcontextprotocol/python-sdk) - अधिकृत Python अंमलबजावणी
- [Kotlin SDK](https://github.com/modelcontextprotocol/kotlin-sdk) - अधिकृत Kotlin अंमलबजावणी
- [Swift SDK](https://github.com/modelcontextprotocol/swift-sdk) - Loopwork AI सह सहयोगाने देखभाल केली जाते
- [Rust SDK](https://github.com/modelcontextprotocol/rust-sdk) - अधिकृत Rust अंमलबजावणी

## मुख्य मुद्दे

- भाषा-विशिष्ट SDKs सह MCP विकास वातावरण सेट करणे सोपे आहे
- MCP सर्व्हर तयार करणे म्हणजे स्पष्ट स्कीमांसह टूल्स तयार करणे आणि नोंदणी करणे
- विश्वसनीय MCP अंमलबजावणीसाठी चाचणी आणि डिबगिंग आवश्यक आहे

## नमुने

- [Java Calculator](../samples/java/calculator/README.md)
- [.Net Calculator](../../../../03-GettingStarted/samples/csharp)
- [JavaScript Calculator](../samples/javascript/README.md)
- [TypeScript Calculator](../samples/typescript/README.md)
- [Python Calculator](../../../../03-GettingStarted/samples/python)

## असाइनमेंट

तुमच्या पसंतीच्या टूलसह एक सोपा MCP सर्व्हर तयार करा:

1. तुमच्या आवडत्या भाषेत टूल अंमलात आणा (.NET, Java, Python, किंवा JavaScript).
2. इनपुट पॅरामीटर्स आणि रिटर्न मूल्ये परिभाषित करा.
3. सर्व्हर योग्यरित्या कार्य करत असल्याची खात्री करण्यासाठी inspector टूल चालवा.
4. विविध इनपुटसह अंमलबजावणीची चाचणी करा.

## सोल्यूशन

[Solution](./solution/README.md)

## अतिरिक्त संसाधने

- [Azure वर Model Context Protocol वापरून एजंट तयार करा](https://learn.microsoft.com/azure/developer/ai/intro-agents-mcp)
- [Azure Container Apps सह Remote MCP (Node.js/TypeScript/JavaScript)](https://learn.microsoft.com/samples/azure-samples/mcp-container-ts/mcp-container-ts/)
- [.NET OpenAI MCP Agent](https://learn.microsoft.com/samples/azure-samples/openai-mcp-agent-dotnet/openai-mcp-agent-dotnet/)

## पुढे काय

पुढे: [MCP Clients सह सुरुवात](../02-client/README.md)

**अस्वीकरण**:  
हा दस्तऐवज AI अनुवाद सेवा [Co-op Translator](https://github.com/Azure/co-op-translator) वापरून अनुवादित केला आहे. आम्ही अचूकतेसाठी प्रयत्नशील असलो तरी, कृपया लक्षात घ्या की स्वयंचलित अनुवादांमध्ये चुका किंवा अचूकतेची कमतरता असू शकते. मूळ दस्तऐवज त्याच्या स्थानिक भाषेत अधिकृत स्रोत मानला जावा. महत्त्वाच्या माहितीसाठी व्यावसायिक मानवी अनुवाद करण्याची शिफारस केली जाते. या अनुवादाच्या वापरामुळे उद्भवणाऱ्या कोणत्याही गैरसमजुती किंवा चुकीच्या अर्थलागी आम्ही जबाबदार नाही.