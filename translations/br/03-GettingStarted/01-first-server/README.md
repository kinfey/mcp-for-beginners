<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "4d5b044c0924d393af3066e03d7d89c5",
  "translation_date": "2025-07-16T09:42:31+00:00",
  "source_file": "03-GettingStarted/01-first-server/README.md",
  "language_code": "br"
}
-->
### -2- Criar projeto

Agora que você instalou seu SDK, vamos criar um projeto a seguir:

### -3- Criar arquivos do projeto

### -4- Criar código do servidor

### -5- Adicionando uma ferramenta e um recurso

Adicione uma ferramenta e um recurso adicionando o seguinte código:

### -6 Código final

Vamos adicionar o último código que precisamos para que o servidor possa iniciar:

### -7- Testar o servidor

Inicie o servidor com o seguinte comando:

### -8- Executar usando o inspector

O inspector é uma ótima ferramenta que pode iniciar seu servidor e permite que você interaja com ele para testar se está funcionando. Vamos iniciá-lo:
> [!NOTE]  
> pode parecer diferente no campo "command", pois contém o comando para executar um servidor com seu runtime específico/
Você deve ver a seguinte interface de usuário:

![Connect](/03-GettingStarted/01-first-server/assets/connect.png)

1. Conecte-se ao servidor selecionando o botão Connect  
  Depois de se conectar ao servidor, você deverá ver o seguinte:

  ![Connected](/03-GettingStarted/01-first-server/assets/connected.png)

1. Selecione "Tools" e "listTools", você verá "Add" aparecer, selecione "Add" e preencha os valores dos parâmetros.

  Você verá a seguinte resposta, ou seja, um resultado da ferramenta "add":

  ![Result of running add](/03-GettingStarted/01-first-server/assets/ran-tool.png)

Parabéns, você conseguiu criar e executar seu primeiro servidor!

### SDKs Oficiais

O MCP oferece SDKs oficiais para várias linguagens:

- [C# SDK](https://github.com/modelcontextprotocol/csharp-sdk) - Mantido em colaboração com a Microsoft  
- [Java SDK](https://github.com/modelcontextprotocol/java-sdk) - Mantido em colaboração com a Spring AI  
- [TypeScript SDK](https://github.com/modelcontextprotocol/typescript-sdk) - Implementação oficial em TypeScript  
- [Python SDK](https://github.com/modelcontextprotocol/python-sdk) - Implementação oficial em Python  
- [Kotlin SDK](https://github.com/modelcontextprotocol/kotlin-sdk) - Implementação oficial em Kotlin  
- [Swift SDK](https://github.com/modelcontextprotocol/swift-sdk) - Mantido em colaboração com a Loopwork AI  
- [Rust SDK](https://github.com/modelcontextprotocol/rust-sdk) - Implementação oficial em Rust  

## Principais Pontos

- Configurar um ambiente de desenvolvimento MCP é simples com SDKs específicos para cada linguagem  
- Construir servidores MCP envolve criar e registrar ferramentas com esquemas claros  
- Testar e depurar são essenciais para implementações MCP confiáveis  

## Exemplos

- [Calculadora Java](../samples/java/calculator/README.md)  
- [Calculadora .Net](../../../../03-GettingStarted/samples/csharp)  
- [Calculadora JavaScript](../samples/javascript/README.md)  
- [Calculadora TypeScript](../samples/typescript/README.md)  
- [Calculadora Python](../../../../03-GettingStarted/samples/python)  

## Exercício

Crie um servidor MCP simples com uma ferramenta de sua escolha:

1. Implemente a ferramenta na sua linguagem preferida (.NET, Java, Python ou JavaScript).  
2. Defina os parâmetros de entrada e os valores de retorno.  
3. Execute a ferramenta inspector para garantir que o servidor funcione como esperado.  
4. Teste a implementação com diferentes entradas.  

## Solução

[Solução](./solution/README.md)

## Recursos Adicionais

- [Construindo Agentes usando Model Context Protocol no Azure](https://learn.microsoft.com/azure/developer/ai/intro-agents-mcp)  
- [MCP Remoto com Azure Container Apps (Node.js/TypeScript/JavaScript)](https://learn.microsoft.com/samples/azure-samples/mcp-container-ts/mcp-container-ts/)  
- [Agente MCP OpenAI para .NET](https://learn.microsoft.com/samples/azure-samples/openai-mcp-agent-dotnet/openai-mcp-agent-dotnet/)  

## Próximos passos

Próximo: [Começando com Clientes MCP](../02-client/README.md)

**Aviso Legal**:  
Este documento foi traduzido utilizando o serviço de tradução por IA [Co-op Translator](https://github.com/Azure/co-op-translator). Embora nos esforcemos para garantir a precisão, esteja ciente de que traduções automáticas podem conter erros ou imprecisões. O documento original em seu idioma nativo deve ser considerado a fonte autorizada. Para informações críticas, recomenda-se tradução profissional humana. Não nos responsabilizamos por quaisquer mal-entendidos ou interpretações incorretas decorrentes do uso desta tradução.