<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "748c61250d4a326206b72b28f6154615",
  "translation_date": "2025-07-13T23:42:29+00:00",
  "source_file": "05-AdvancedTopics/README.md",
  "language_code": "mr"
}
-->
# MCP मधील प्रगत विषय

हा अध्याय Model Context Protocol (MCP) अंमलबजावणीतील प्रगत विषयांचा आढावा घेण्यासाठी आहे, ज्यात मल्टी-मोडल एकत्रीकरण, स्केलेबिलिटी, सुरक्षा सर्वोत्तम पद्धती आणि एंटरप्राइझ एकत्रीकरण यांचा समावेश आहे. हे विषय आधुनिक AI प्रणालींच्या गरजा पूर्ण करणाऱ्या मजबूत आणि उत्पादनासाठी तयार MCP अनुप्रयोगांच्या निर्मितीसाठी अत्यंत महत्त्वाचे आहेत.

## आढावा

हा धडा Model Context Protocol अंमलबजावणीतील प्रगत संकल्पनांचा अभ्यास करतो, ज्यामध्ये मल्टी-मोडल एकत्रीकरण, स्केलेबिलिटी, सुरक्षा सर्वोत्तम पद्धती आणि एंटरप्राइझ एकत्रीकरण यावर लक्ष केंद्रित केले आहे. हे विषय उत्पादन-स्तरीय MCP अनुप्रयोग तयार करण्यासाठी आवश्यक आहेत जे एंटरप्राइझ वातावरणातील जटिल गरजा हाताळू शकतात.

## शिकण्याचे उद्दिष्टे

या धड्याच्या शेवटी, तुम्ही सक्षम असाल:

- MCP फ्रेमवर्कमध्ये मल्टी-मोडल क्षमता अंमलात आणणे
- उच्च मागणीच्या परिस्थितीसाठी स्केलेबल MCP आर्किटेक्चर डिझाइन करणे
- MCP च्या सुरक्षा तत्त्वांशी सुसंगत सुरक्षा सर्वोत्तम पद्धती लागू करणे
- MCP चे एंटरप्राइझ AI प्रणाली आणि फ्रेमवर्कसह एकत्रीकरण करणे
- उत्पादन वातावरणात कार्यक्षमता आणि विश्वासार्हता सुधारित करणे

## धडे आणि नमुना प्रकल्प

| लिंक | शीर्षक | वर्णन |
|------|-------|-------------|
| [5.1 Integration with Azure](./mcp-integration/README.md) | Azure सह एकत्रीकरण | Azure वर तुमचा MCP Server कसा एकत्रित करायचा ते शिका |
| [5.2 Multi modal sample](./mcp-multi-modality/README.md) | MCP मल्टी मोडल नमुने | ऑडिओ, प्रतिमा आणि मल्टी मोडल प्रतिसादांसाठी नमुने |
| [5.3 MCP OAuth2 sample](../../../05-AdvancedTopics/mcp-oauth2-demo) | MCP OAuth2 डेमो | OAuth2 सह MCP चे मिनिमल Spring Boot अॅप, जे Authorization आणि Resource Server दोन्ही दाखवते. सुरक्षित टोकन जारी करणे, संरक्षित एंडपॉइंट्स, Azure Container Apps तैनाती, आणि API Management एकत्रीकरण यांचे प्रदर्शन करते. |
| [5.4 Root Contexts](./mcp-root-contexts/README.md) | Root contexts | Root context बद्दल अधिक जाणून घ्या आणि त्याची अंमलबजावणी कशी करायची ते शिका |
| [5.5 Routing](./mcp-routing/README.md) | Routing | विविध प्रकारच्या routing बद्दल शिका |
| [5.6 Sampling](./mcp-sampling/README.md) | Sampling | Sampling कसे करायचे ते शिका |
| [5.7 Scaling](./mcp-scaling/README.md) | Scaling | स्केलिंग बद्दल शिका |
| [5.8 Security](./mcp-security/README.md) | Security | तुमचा MCP Server सुरक्षित करा |
| [5.9 Web Search sample](./web-search-mcp/README.md) | Web Search MCP | Python MCP सर्व्हर आणि क्लायंट जे SerpAPI सह रिअल-टाइम वेब, न्यूज, प्रॉडक्ट सर्च आणि Q&A साठी एकत्रित आहेत. मल्टी-टूल ऑर्केस्ट्रेशन, बाह्य API एकत्रीकरण, आणि मजबूत त्रुटी हाताळणी दाखवते. |
| [5.10 Realtime Streaming](./mcp-realtimestreaming/README.md) | Streaming | आजच्या डेटा-चालित जगात रिअल-टाइम डेटा स्ट्रीमिंग अत्यावश्यक झाले आहे, जिथे व्यवसाय आणि अनुप्रयोगांना त्वरित माहिती मिळणे आवश्यक आहे जेणेकरून ते वेळेवर निर्णय घेऊ शकतील. |
| [5.11 Realtime Web Search](./mcp-realtimesearch/README.md) | Web Search | रिअल-टाइम वेब सर्च कसे MCP द्वारे बदलते, जे AI मॉडेल्स, सर्च इंजिन्स आणि अनुप्रयोगांमध्ये संदर्भ व्यवस्थापनासाठी एक प्रमाणित दृष्टिकोन प्रदान करते. |
| [5.12  Entra ID Authentication for Model Context Protocol Servers](./mcp-security-entra/README.md) | Entra ID Authentication | Microsoft Entra ID एक मजबूत क्लाउड-आधारित ओळख आणि प्रवेश व्यवस्थापन उपाय प्रदान करते, ज्यामुळे फक्त अधिकृत वापरकर्ते आणि अनुप्रयोग तुमच्या MCP सर्व्हरशी संवाद साधू शकतात याची खात्री होते. |
| [5.13 Azure AI Foundry Agent Integration](./mcp-foundry-agent-integration/README.md) | Azure AI Foundry Integration | Model Context Protocol सर्व्हरना Azure AI Foundry एजंट्ससह कसे एकत्रित करायचे ते शिका, ज्यामुळे शक्तिशाली टूल ऑर्केस्ट्रेशन आणि एंटरप्राइझ AI क्षमता प्रमाणित बाह्य डेटा स्रोत कनेक्शन्ससह सक्षम होतात. |

## अतिरिक्त संदर्भ

प्रगत MCP विषयांवरील सर्वात अद्ययावत माहितीसाठी, खालील पहा:
- [MCP Documentation](https://modelcontextprotocol.io/)
- [MCP Specification](https://spec.modelcontextprotocol.io/)
- [GitHub Repository](https://github.com/modelcontextprotocol)

## मुख्य मुद्दे

- मल्टी-मोडल MCP अंमलबजावणी AI क्षमतांना फक्त मजकूर प्रक्रिया पलीकडे वाढवते
- स्केलेबिलिटी एंटरप्राइझ तैनातीसाठी आवश्यक आहे आणि ते आडवे व उभे स्केलिंगद्वारे हाताळले जाऊ शकते
- सर्वसमावेशक सुरक्षा उपाय डेटा संरक्षण करतात आणि योग्य प्रवेश नियंत्रण सुनिश्चित करतात
- Azure OpenAI आणि Microsoft AI Foundry सारख्या प्लॅटफॉर्मसह एंटरप्राइझ एकत्रीकरण MCP क्षमतांना वाढवते
- प्रगत MCP अंमलबजावणींना ऑप्टिमाइझ्ड आर्किटेक्चर आणि काळजीपूर्वक संसाधन व्यवस्थापनाचा फायदा होतो

## सराव

विशिष्ट वापर प्रकरणासाठी एंटरप्राइझ-ग्रेड MCP अंमलबजावणी डिझाइन करा:

1. तुमच्या वापर प्रकरणासाठी मल्टी-मोडल गरजा ओळखा
2. संवेदनशील डेटा संरक्षित करण्यासाठी आवश्यक सुरक्षा नियंत्रणांची रूपरेषा तयार करा
3. वेगवेगळ्या लोडसाठी हाताळू शकणारे स्केलेबल आर्किटेक्चर डिझाइन करा
4. एंटरप्राइझ AI प्रणालींसह एकत्रीकरणाचे बिंदू नियोजित करा
5. संभाव्य कार्यक्षमता अडथळे आणि त्यांचे निराकरण धोरणे दस्तऐवजीकरण करा

## अतिरिक्त संसाधने

- [Azure OpenAI Documentation](https://learn.microsoft.com/en-us/azure/ai-services/openai/)
- [Microsoft AI Foundry Documentation](https://learn.microsoft.com/en-us/ai-services/)

---

## पुढे काय

- [5.1 MCP Integration](./mcp-integration/README.md)

**अस्वीकरण**:  
हा दस्तऐवज AI अनुवाद सेवा [Co-op Translator](https://github.com/Azure/co-op-translator) वापरून अनुवादित केला आहे. आम्ही अचूकतेसाठी प्रयत्नशील असलो तरी, कृपया लक्षात घ्या की स्वयंचलित अनुवादांमध्ये चुका किंवा अचूकतेची कमतरता असू शकते. मूळ दस्तऐवज त्याच्या स्थानिक भाषेत अधिकृत स्रोत मानला जावा. महत्त्वाच्या माहितीसाठी व्यावसायिक मानवी अनुवाद करण्याची शिफारस केली जाते. या अनुवादाच्या वापरामुळे उद्भवणाऱ्या कोणत्याही गैरसमजुती किंवा चुकीच्या अर्थलागी आम्ही जबाबदार नाही.