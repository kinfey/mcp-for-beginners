<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "07863f50601f395c3bdfce30f555f11a",
  "translation_date": "2025-07-13T17:49:29+00:00",
  "source_file": "03-GettingStarted/01-first-server/solution/dotnet/README.md",
  "language_code": "no"
}
-->
# Kjøre dette eksempelet

## -1- Installer avhengighetene

```bash
dotnet restore
```

## -3- Kjør eksempelet


```bash
dotnet run
```

## -4- Test eksempelet

Med serveren kjørende i ett terminalvindu, åpne et nytt terminalvindu og kjør følgende kommando:

```bash
npx @modelcontextprotocol/inspector dotnet run
```

Dette skal starte en webserver med et visuelt grensesnitt som lar deg teste eksempelet.

Når serveren er tilkoblet:

- prøv å liste opp verktøy og kjør `add` med argumentene 2 og 4, du skal se 6 som resultat.
- gå til resources og resource template og kall "greeting", skriv inn et navn og du skal se en hilsen med navnet du oppga.

### Testing i CLI-modus

Du kan starte det direkte i CLI-modus ved å kjøre følgende kommando:

```bash
npx @modelcontextprotocol/inspector --cli dotnet run --method tools/list
```

Dette vil liste opp alle verktøyene som er tilgjengelige på serveren. Du skal se følgende output:

```text
{
  "tools": [
    {
      "name": "Add",
      "description": "Adds two numbers",
      "inputSchema": {
        "type": "object",
        "properties": {
          "a": {
            "type": "integer"
          },
          "b": {
            "type": "integer"
          }
        },
        "title": "Add",
        "description": "Adds two numbers",
        "required": [
          "a",
          "b"
        ]
      }
    }
  ]
}
```

For å kalle et verktøy, skriv:

```bash
npx @modelcontextprotocol/inspector --cli dotnet run --method tools/call --tool-name Add --tool-arg a=1 --tool-arg b=2
```

Du skal se følgende output:

```text
{
  "content": [
    {
      "type": "text",
      "text": "Sum 3"
    }
  ],
  "isError": false
}
```

> ![!TIP]
> Det er vanligvis mye raskere å kjøre inspektøren i CLI-modus enn i nettleseren.
> Les mer om inspektøren [her](https://github.com/modelcontextprotocol/inspector).

**Ansvarsfraskrivelse**:  
Dette dokumentet er oversatt ved hjelp av AI-oversettelsestjenesten [Co-op Translator](https://github.com/Azure/co-op-translator). Selv om vi streber etter nøyaktighet, vennligst vær oppmerksom på at automatiske oversettelser kan inneholde feil eller unøyaktigheter. Det opprinnelige dokumentet på originalspråket skal anses som den autoritative kilden. For kritisk informasjon anbefales profesjonell menneskelig oversettelse. Vi er ikke ansvarlige for eventuelle misforståelser eller feiltolkninger som oppstår ved bruk av denne oversettelsen.