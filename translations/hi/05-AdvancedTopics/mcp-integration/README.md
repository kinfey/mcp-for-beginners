<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "33daea2e41ef7635cf13c41d6a3ea773",
  "translation_date": "2025-07-14T00:04:53+00:00",
  "source_file": "05-AdvancedTopics/mcp-integration/README.md",
  "language_code": "hi"
}
-->
## Microsoft AI Foundry एकीकरण

Azure AI Foundry एक ऐसा प्लेटफ़ॉर्म प्रदान करता है जो AI एजेंट बनाने और तैनात करने के लिए उपयोग किया जाता है। MCP को AI Foundry के साथ एकीकृत करने से आप इसकी क्षमताओं का लाभ उठा सकते हैं, साथ ही MCP की लचीलापन भी बनाए रख सकते हैं।

नीचे दिए गए कोड में, हम एक एजेंट एकीकरण विकसित करते हैं जो अनुरोधों को संसाधित करता है और MCP का उपयोग करके टूल कॉल्स को संभालता है।

## MCP को Azure ML के साथ एकीकृत करना

MCP को Azure Machine Learning (ML) के साथ एकीकृत करने से आप Azure की शक्तिशाली ML क्षमताओं का लाभ उठा सकते हैं, साथ ही MCP की लचीलापन भी बनाए रख सकते हैं। इस एकीकरण का उपयोग ML पाइपलाइनों को निष्पादित करने, मॉडलों को टूल के रूप में पंजीकृत करने, और कंप्यूट संसाधनों का प्रबंधन करने के लिए किया जा सकता है।

## आगे क्या है

- [5.2 मल्टी मोडैलिटी](../mcp-multi-modality/README.md)

**अस्वीकरण**:  
यह दस्तावेज़ AI अनुवाद सेवा [Co-op Translator](https://github.com/Azure/co-op-translator) का उपयोग करके अनुवादित किया गया है। जबकि हम सटीकता के लिए प्रयासरत हैं, कृपया ध्यान दें कि स्वचालित अनुवादों में त्रुटियाँ या अशुद्धियाँ हो सकती हैं। मूल दस्तावेज़ अपनी मूल भाषा में ही अधिकारिक स्रोत माना जाना चाहिए। महत्वपूर्ण जानकारी के लिए, पेशेवर मानव अनुवाद की सलाह दी जाती है। इस अनुवाद के उपयोग से उत्पन्न किसी भी गलतफहमी या गलत व्याख्या के लिए हम जिम्मेदार नहीं हैं।