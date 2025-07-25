<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "222e01c3002a33355806d60d558d9429",
  "translation_date": "2025-07-14T09:27:25+00:00",
  "source_file": "03-GettingStarted/04-vscode/README.md",
  "language_code": "ru"
}
-->
Давайте подробнее поговорим о том, как использовать визуальный интерфейс в следующих разделах.

## Подход

Вот как мы должны подойти к этому на высоком уровне:

- Настроить файл для поиска нашего MCP сервера.
- Запустить/подключиться к серверу, чтобы получить список его возможностей.
- Использовать эти возможности через интерфейс GitHub Copilot Chat.

Отлично, теперь, когда мы понимаем общий процесс, давайте попробуем использовать MCP сервер через Visual Studio Code на практике.

## Упражнение: Использование сервера

В этом упражнении мы настроим Visual Studio Code для поиска вашего MCP сервера, чтобы его можно было использовать через интерфейс GitHub Copilot Chat.

### -0- Предварительный шаг, включение обнаружения MCP серверов

Возможно, вам потребуется включить обнаружение MCP серверов.

1. Перейдите в `File -> Preferences -> Settings` в Visual Studio Code.

2. Найдите "MCP" и включите `chat.mcp.discovery.enabled` в файле settings.json.

### -1- Создание конфигурационного файла

Начните с создания конфигурационного файла в корне вашего проекта. Вам понадобится файл с именем MCP.json, который нужно поместить в папку .vscode. Он должен выглядеть примерно так:

```text
.vscode
|-- mcp.json
```

Далее посмотрим, как добавить запись о сервере.

### -2- Настройка сервера

Добавьте следующее содержимое в *mcp.json*:

```json
{
    "inputs": [],
    "servers": {
       "hello-mcp": {
           "command": "node",
           "args": [
               "build/index.js"
           ]
       }
    }
}
```

Приведён простой пример запуска сервера, написанного на Node.js. Для других сред укажите правильную команду запуска сервера с помощью `command` и `args`.

### -3- Запуск сервера

Теперь, когда вы добавили запись, давайте запустим сервер:

1. Найдите вашу запись в *mcp.json* и убедитесь, что видите иконку "play":

  ![Запуск сервера в Visual Studio Code](../../../../translated_images/vscode-start-server.8e3c986612e3555de47e5b1e37b2f3020457eeb6a206568570fd74a17e3796ad.ru.png)  

2. Нажмите на иконку "play", вы должны увидеть, что иконка инструментов в GitHub Copilot Chat увеличит количество доступных инструментов. Если нажать на эту иконку, откроется список зарегистрированных инструментов. Вы можете отмечать или снимать отметки с каждого инструмента, в зависимости от того, хотите ли вы, чтобы GitHub Copilot использовал их в качестве контекста:

  ![Инструменты в Visual Studio Code](../../../../translated_images/vscode-tool.0b3bbea2fb7d8c26ddf573cad15ef654e55302a323267d8ee6bd742fe7df7fed.ru.png)

3. Чтобы запустить инструмент, введите запрос, который, как вы знаете, соответствует описанию одного из ваших инструментов, например, запрос "add 22 to 1":

  ![Запуск инструмента из GitHub Copilot](../../../../translated_images/vscode-agent.d5a0e0b897331060518fe3f13907677ef52b879db98c64d68a38338608f3751e.ru.png)

  Вы должны увидеть ответ с числом 23.

## Задание

Попробуйте добавить запись о сервере в ваш файл *mcp.json* и убедитесь, что вы можете запускать и останавливать сервер. Также убедитесь, что вы можете взаимодействовать с инструментами на вашем сервере через интерфейс GitHub Copilot Chat.

## Решение

[Решение](./solution/README.md)

## Основные выводы

Основные выводы из этой главы:

- Visual Studio Code — отличный клиент, который позволяет использовать несколько MCP серверов и их инструменты.
- Интерфейс GitHub Copilot Chat — это способ взаимодействия с серверами.
- Вы можете запрашивать у пользователя ввод, например, API ключи, которые можно передавать MCP серверу при настройке записи сервера в файле *mcp.json*.

## Примеры

- [Калькулятор на Java](../samples/java/calculator/README.md)
- [Калькулятор на .Net](../../../../03-GettingStarted/samples/csharp)
- [Калькулятор на JavaScript](../samples/javascript/README.md)
- [Калькулятор на TypeScript](../samples/typescript/README.md)
- [Калькулятор на Python](../../../../03-GettingStarted/samples/python)

## Дополнительные ресурсы

- [Документация Visual Studio](https://code.visualstudio.com/docs/copilot/chat/mcp-servers)

## Что дальше

- Далее: [Создание SSE сервера](../05-sse-server/README.md)

**Отказ от ответственности**:  
Этот документ был переведен с помощью сервиса автоматического перевода [Co-op Translator](https://github.com/Azure/co-op-translator). Несмотря на наши усилия по обеспечению точности, просим учитывать, что автоматический перевод может содержать ошибки или неточности. Оригинальный документ на его исходном языке следует считать авторитетным источником. Для получения критически важной информации рекомендуется обращаться к профессиональному переводу, выполненному человеком. Мы не несем ответственности за любые недоразумения или неправильные толкования, возникшие в результате использования данного перевода.