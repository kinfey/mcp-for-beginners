<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "748c61250d4a326206b72b28f6154615",
  "translation_date": "2025-07-13T23:48:11+00:00",
  "source_file": "05-AdvancedTopics/README.md",
  "language_code": "bg"
}
-->
# Разширени теми в MCP

Тази глава е предназначена да обхване серия от разширени теми в имплементацията на Model Context Protocol (MCP), включително мултимодална интеграция, мащабируемост, най-добри практики за сигурност и интеграция в корпоративна среда. Тези теми са от съществено значение за изграждането на стабилни и готови за продукция MCP приложения, които могат да отговорят на изискванията на съвременните AI системи.

## Преглед

Този урок разглежда разширени концепции в имплементацията на Model Context Protocol, с фокус върху мултимодална интеграция, мащабируемост, най-добри практики за сигурност и корпоративна интеграция. Тези теми са ключови за създаването на MCP приложения от производствен клас, които могат да се справят със сложни изисквания в корпоративна среда.

## Учебни цели

След края на този урок ще можете да:

- Имплементирате мултимодални възможности в рамките на MCP
- Проектирате мащабируеми MCP архитектури за сценарии с високо натоварване
- Прилагате най-добрите практики за сигурност, съобразени с принципите на сигурност на MCP
- Интегрирате MCP с корпоративни AI системи и рамки
- Оптимизирате производителността и надеждността в продукционна среда

## Уроци и примерни проекти

| Връзка | Заглавие | Описание |
|--------|----------|----------|
| [5.1 Integration with Azure](./mcp-integration/README.md) | Интеграция с Azure | Научете как да интегрирате вашия MCP сървър в Azure |
| [5.2 Multi modal sample](./mcp-multi-modality/README.md) | MCP мултимодални примери | Примери за аудио, изображения и мултимодални отговори |
| [5.3 MCP OAuth2 sample](../../../05-AdvancedTopics/mcp-oauth2-demo) | MCP OAuth2 Демонстрация | Минимално Spring Boot приложение, показващо OAuth2 с MCP, както като Authorization, така и като Resource Server. Демонстрира сигурно издаване на токени, защитени крайни точки, разгръщане в Azure Container Apps и интеграция с API Management. |
| [5.4 Root Contexts](./mcp-root-contexts/README.md) | Root контексти | Научете повече за root контекста и как да го имплементирате |
| [5.5 Routing](./mcp-routing/README.md) | Рутинг | Научете различните видове маршрутизиране |
| [5.6 Sampling](./mcp-sampling/README.md) | Семплиране | Научете как да работите със семплиране |
| [5.7 Scaling](./mcp-scaling/README.md) | Мащабиране | Научете за мащабирането |
| [5.8 Security](./mcp-security/README.md) | Сигурност | Осигурете своя MCP сървър |
| [5.9 Web Search sample](./web-search-mcp/README.md) | Уеб търсене MCP | Python MCP сървър и клиент, интегриращи се със SerpAPI за търсене в реално време в уеб, новини, продукти и въпроси и отговори. Демонстрира мулти-инструментна оркестрация, интеграция с външни API и надеждно обработване на грешки. |
| [5.10 Realtime Streaming](./mcp-realtimestreaming/README.md) | Поточно предаване | Поточното предаване на данни в реално време се превърна в съществено в днешния свят, ориентиран към данни, където бизнесите и приложенията изискват незабавен достъп до информация за вземане на навременни решения. |
| [5.11 Realtime Web Search](./mcp-realtimesearch/README.md) | Уеб търсене | Как MCP трансформира търсенето в реално време, като предоставя стандартизиран подход за управление на контекста между AI модели, търсачки и приложения. |
| [5.12  Entra ID Authentication for Model Context Protocol Servers](./mcp-security-entra/README.md) | Entra ID удостоверяване | Microsoft Entra ID предлага стабилно облачно решение за управление на идентичности и достъп, което гарантира, че само упълномощени потребители и приложения могат да взаимодействат с вашия MCP сървър. |
| [5.13 Azure AI Foundry Agent Integration](./mcp-foundry-agent-integration/README.md) | Интеграция с Azure AI Foundry | Научете как да интегрирате MCP сървъри с Azure AI Foundry агенти, позволявайки мощна оркестрация на инструменти и корпоративни AI възможности с стандартизирани връзки към външни източници на данни. |

## Допълнителни препратки

За най-актуална информация относно разширените теми в MCP, вижте:
- [MCP Documentation](https://modelcontextprotocol.io/)
- [MCP Specification](https://spec.modelcontextprotocol.io/)
- [GitHub Repository](https://github.com/modelcontextprotocol)

## Основни изводи

- Мултимодалните имплементации на MCP разширяват AI възможностите отвъд обработката на текст
- Мащабируемостта е ключова за корпоративни внедрявания и може да се постигне чрез хоризонтално и вертикално мащабиране
- Комплексните мерки за сигурност защитават данните и осигуряват правилен контрол на достъпа
- Корпоративната интеграция с платформи като Azure OpenAI и Microsoft AI Foundry подобрява възможностите на MCP
- Разширените имплементации на MCP се възползват от оптимизирани архитектури и внимателно управление на ресурсите

## Упражнение

Проектирайте MCP имплементация от корпоративен клас за конкретен случай на употреба:

1. Идентифицирайте мултимодалните изисквания за вашия случай
2. Опишете необходимите мерки за сигурност за защита на чувствителните данни
3. Проектирайте мащабируема архитектура, която може да се справи с променливо натоварване
4. Планирайте интеграционни точки с корпоративни AI системи
5. Документирайте потенциални проблеми с производителността и стратегии за тяхното преодоляване

## Допълнителни ресурси

- [Azure OpenAI Documentation](https://learn.microsoft.com/en-us/azure/ai-services/openai/)
- [Microsoft AI Foundry Documentation](https://learn.microsoft.com/en-us/ai-services/)

---

## Какво следва

- [5.1 MCP Integration](./mcp-integration/README.md)

**Отказ от отговорност**:  
Този документ е преведен с помощта на AI преводаческа услуга [Co-op Translator](https://github.com/Azure/co-op-translator). Въпреки че се стремим към точност, моля, имайте предвид, че автоматизираните преводи могат да съдържат грешки или неточности. Оригиналният документ на неговия роден език трябва да се счита за авторитетен източник. За критична информация се препоръчва професионален човешки превод. Ние не носим отговорност за каквито и да е недоразумения или неправилни тълкувания, произтичащи от използването на този превод.