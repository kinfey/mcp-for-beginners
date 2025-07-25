<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "4d5b044c0924d393af3066e03d7d89c5",
  "translation_date": "2025-07-16T09:50:49+00:00",
  "source_file": "03-GettingStarted/01-first-server/README.md",
  "language_code": "cs"
}
-->
### -2- Vytvoření projektu

Nyní, když máte nainstalované SDK, pojďme vytvořit projekt:

### -3- Vytvoření souborů projektu

### -4- Vytvoření kódu serveru

### -5- Přidání nástroje a zdroje

Přidejte nástroj a zdroj přidáním následujícího kódu:

### -6- Konečný kód

Přidejme poslední kód, který potřebujeme, aby se server mohl spustit:

### -7- Testování serveru

Spusťte server pomocí následujícího příkazu:

### -8- Spuštění pomocí inspektoru

Inspektor je skvělý nástroj, který dokáže spustit váš server a umožní vám s ním interagovat, abyste mohli otestovat, že funguje. Pojďme ho spustit:
> [!NOTE]
> může to v poli "command" vypadat jinak, protože obsahuje příkaz pro spuštění serveru s vaším konkrétním runtime/
Měli byste vidět následující uživatelské rozhraní:

![Connect](/03-GettingStarted/01-first-server/assets/connect.png)

1. Připojte se k serveru výběrem tlačítka Connect  
   Po připojení k serveru byste měli vidět následující:

   ![Connected](/03-GettingStarted/01-first-server/assets/connected.png)

1. Vyberte "Tools" a "listTools", měli byste vidět možnost "Add", vyberte "Add" a vyplňte hodnoty parametrů.

   Měli byste vidět následující odpověď, tedy výsledek z nástroje "add":

   ![Result of running add](/03-GettingStarted/01-first-server/assets/ran-tool.png)

Gratulujeme, podařilo se vám vytvořit a spustit váš první server!

### Oficiální SDK

MCP poskytuje oficiální SDK pro více jazyků:

- [C# SDK](https://github.com/modelcontextprotocol/csharp-sdk) - Udržováno ve spolupráci s Microsoftem
- [Java SDK](https://github.com/modelcontextprotocol/java-sdk) - Udržováno ve spolupráci se Spring AI
- [TypeScript SDK](https://github.com/modelcontextprotocol/typescript-sdk) - Oficiální implementace v TypeScriptu
- [Python SDK](https://github.com/modelcontextprotocol/python-sdk) - Oficiální implementace v Pythonu
- [Kotlin SDK](https://github.com/modelcontextprotocol/kotlin-sdk) - Oficiální implementace v Kotlinu
- [Swift SDK](https://github.com/modelcontextprotocol/swift-sdk) - Udržováno ve spolupráci s Loopwork AI
- [Rust SDK](https://github.com/modelcontextprotocol/rust-sdk) - Oficiální implementace v Rustu

## Hlavní poznatky

- Nastavení vývojového prostředí MCP je jednoduché díky SDK specifickým pro jednotlivé jazyky
- Vytváření MCP serverů zahrnuje tvorbu a registraci nástrojů s jasnými schématy
- Testování a ladění jsou nezbytné pro spolehlivé implementace MCP

## Ukázky

- [Java Calculator](../samples/java/calculator/README.md)
- [.Net Calculator](../../../../03-GettingStarted/samples/csharp)
- [JavaScript Calculator](../samples/javascript/README.md)
- [TypeScript Calculator](../samples/typescript/README.md)
- [Python Calculator](../../../../03-GettingStarted/samples/python)

## Zadání

Vytvořte jednoduchý MCP server s nástrojem dle vašeho výběru:

1. Implementujte nástroj ve vámi preferovaném jazyce (.NET, Java, Python nebo JavaScript).
2. Definujte vstupní parametry a návratové hodnoty.
3. Spusťte nástroj inspector, abyste ověřili, že server funguje správně.
4. Otestujte implementaci s různými vstupy.

## Řešení

[Řešení](./solution/README.md)

## Další zdroje

- [Vytváření agentů pomocí Model Context Protocol na Azure](https://learn.microsoft.com/azure/developer/ai/intro-agents-mcp)
- [Vzdálené MCP s Azure Container Apps (Node.js/TypeScript/JavaScript)](https://learn.microsoft.com/samples/azure-samples/mcp-container-ts/mcp-container-ts/)
- [.NET OpenAI MCP Agent](https://learn.microsoft.com/samples/azure-samples/openai-mcp-agent-dotnet/openai-mcp-agent-dotnet/)

## Co dál

Další: [Začínáme s MCP klienty](../02-client/README.md)

**Prohlášení o vyloučení odpovědnosti**:  
Tento dokument byl přeložen pomocí AI překladatelské služby [Co-op Translator](https://github.com/Azure/co-op-translator). I když usilujeme o přesnost, mějte prosím na paměti, že automatizované překlady mohou obsahovat chyby nebo nepřesnosti. Původní dokument v jeho mateřském jazyce by měl být považován za autoritativní zdroj. Pro důležité informace se doporučuje profesionální lidský překlad. Nejsme odpovědní za jakékoliv nedorozumění nebo nesprávné výklady vyplývající z použití tohoto překladu.