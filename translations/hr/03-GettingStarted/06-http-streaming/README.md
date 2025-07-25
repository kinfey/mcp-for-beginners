<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "fbe345ba124324648cfb3aef9a9120b8",
  "translation_date": "2025-07-13T20:54:30+00:00",
  "source_file": "03-GettingStarted/06-http-streaming/README.md",
  "language_code": "hr"
}
-->
# HTTPS Streaming s Model Context Protocolom (MCP)

Ovo poglavlje pruža sveobuhvatan vodič za implementaciju sigurnog, skalabilnog i real-time streaminga koristeći Model Context Protocol (MCP) preko HTTPS-a. Obuhvaća motivaciju za streaming, dostupne transportne mehanizme, kako implementirati streamable HTTP u MCP-u, najbolje sigurnosne prakse, migraciju sa SSE-a te praktične upute za izgradnju vlastitih streaming MCP aplikacija.

## Transportni mehanizmi i streaming u MCP-u

Ovaj odjeljak istražuje različite transportne mehanizme dostupne u MCP-u i njihovu ulogu u omogućavanju streaming mogućnosti za real-time komunikaciju između klijenata i servera.

### Što je transportni mehanizam?

Transportni mehanizam definira kako se podaci razmjenjuju između klijenta i servera. MCP podržava više tipova transporta kako bi odgovorio različitim okruženjima i zahtjevima:

- **stdio**: Standardni ulaz/izlaz, pogodan za lokalne i CLI alate. Jednostavan, ali nije prikladan za web ili cloud.
- **SSE (Server-Sent Events)**: Omogućuje serverima da šalju real-time ažuriranja klijentima preko HTTP-a. Dobar za web sučelja, ali ograničen u skalabilnosti i fleksibilnosti.
- **Streamable HTTP**: Moderni HTTP-based streaming transport, podržava notifikacije i bolju skalabilnost. Preporuča se za većinu produkcijskih i cloud scenarija.

### Usporedna tablica

Pogledajte usporednu tablicu ispod kako biste razumjeli razlike između ovih transportnih mehanizama:

| Transport         | Real-time ažuriranja | Streaming | Skalabilnost | Primjena                |
|-------------------|---------------------|-----------|--------------|-------------------------|
| stdio             | Ne                  | Ne        | Niska        | Lokalni CLI alati        |
| SSE               | Da                  | Da        | Srednja      | Web, real-time ažuriranja|
| Streamable HTTP   | Da                  | Da        | Visoka       | Cloud, višekorisnički   |

> [!TIP] Odabir pravog transporta utječe na performanse, skalabilnost i korisničko iskustvo. **Streamable HTTP** se preporučuje za moderne, skalabilne i cloud-ready aplikacije.

Primijetite transportne mehanizme stdio i SSE koje ste vidjeli u prethodnim poglavljima te kako je streamable HTTP transport obrađen u ovom poglavlju.

## Streaming: Koncepti i motivacija

Razumijevanje osnovnih koncepata i motivacije iza streaminga ključno je za implementaciju učinkovitih sustava za real-time komunikaciju.

**Streaming** je tehnika u mrežnom programiranju koja omogućuje slanje i primanje podataka u malim, upravljivim dijelovima ili kao niz događaja, umjesto da se čeka da cijeli odgovor bude spreman. Ovo je posebno korisno za:

- Velike datoteke ili skupove podataka.
- Real-time ažuriranja (npr. chat, trake napretka).
- Dugotrajne izračune gdje želite korisnika stalno informirati.

Evo što trebate znati o streamingu na visokoj razini:

- Podaci se isporučuju postupno, ne odjednom.
- Klijent može obrađivati podatke čim stignu.
- Smanjuje percipiranu latenciju i poboljšava korisničko iskustvo.

### Zašto koristiti streaming?

Razlozi za korištenje streaminga su sljedeći:

- Korisnici odmah dobivaju povratnu informaciju, ne samo na kraju
- Omogućuje real-time aplikacije i responzivna sučelja
- Efikasnije korištenje mrežnih i računalnih resursa

### Jednostavan primjer: HTTP streaming server i klijent

Evo jednostavnog primjera kako se streaming može implementirati:

<details>
<summary>Python</summary>

**Server (Python, koristeći FastAPI i StreamingResponse):**
<details>
<summary>Python</summary>

```python
from fastapi import FastAPI
from fastapi.responses import StreamingResponse
import time

app = FastAPI()

async def event_stream():
    for i in range(1, 6):
        yield f"data: Message {i}\n\n"
        time.sleep(1)

@app.get("/stream")
def stream():
    return StreamingResponse(event_stream(), media_type="text/event-stream")
```

</details>

**Klijent (Python, koristeći requests):**
<details>
<summary>Python</summary>

```python
import requests

with requests.get("http://localhost:8000/stream", stream=True) as r:
    for line in r.iter_lines():
        if line:
            print(line.decode())
```

</details>

Ovaj primjer pokazuje server koji šalje niz poruka klijentu čim postanu dostupne, umjesto da čeka da sve poruke budu spremne.

**Kako radi:**
- Server šalje svaku poruku čim je spremna.
- Klijent prima i ispisuje svaki dio čim stigne.

**Zahtjevi:**
- Server mora koristiti streaming odgovor (npr. `StreamingResponse` u FastAPI).
- Klijent mora obrađivati odgovor kao stream (`stream=True` u requests).
- Content-Type je obično `text/event-stream` ili `application/octet-stream`.

</details>

<details>
<summary>Java</summary>

**Server (Java, koristeći Spring Boot i Server-Sent Events):**

```java
@RestController
public class CalculatorController {

    @GetMapping(value = "/calculate", produces = MediaType.TEXT_EVENT_STREAM_VALUE)
    public Flux<ServerSentEvent<String>> calculate(@RequestParam double a,
                                                   @RequestParam double b,
                                                   @RequestParam String op) {
        
        double result;
        switch (op) {
            case "add": result = a + b; break;
            case "sub": result = a - b; break;
            case "mul": result = a * b; break;
            case "div": result = b != 0 ? a / b : Double.NaN; break;
            default: result = Double.NaN;
        }

        return Flux.<ServerSentEvent<String>>just(
                    ServerSentEvent.<String>builder()
                        .event("info")
                        .data("Calculating: " + a + " " + op + " " + b)
                        .build(),
                    ServerSentEvent.<String>builder()
                        .event("result")
                        .data(String.valueOf(result))
                        .build()
                )
                .delayElements(Duration.ofSeconds(1));
    }
}
```

**Klijent (Java, koristeći Spring WebFlux WebClient):**

```java
@SpringBootApplication
public class CalculatorClientApplication implements CommandLineRunner {

    private final WebClient client = WebClient.builder()
            .baseUrl("http://localhost:8080")
            .build();

    @Override
    public void run(String... args) {
        client.get()
                .uri(uriBuilder -> uriBuilder
                        .path("/calculate")
                        .queryParam("a", 7)
                        .queryParam("b", 5)
                        .queryParam("op", "mul")
                        .build())
                .accept(MediaType.TEXT_EVENT_STREAM)
                .retrieve()
                .bodyToFlux(String.class)
                .doOnNext(System.out::println)
                .blockLast();
    }
}
```

**Napomene o Java implementaciji:**
- Koristi Spring Boot reaktivni stack s `Flux` za streaming
- `ServerSentEvent` pruža strukturirani streaming događaja s tipovima događaja
- `WebClient` s `bodyToFlux()` omogućuje reaktivnu potrošnju streama
- `delayElements()` simulira vrijeme obrade između događaja
- Događaji mogu imati tipove (`info`, `result`) za bolju obradu na klijentu

</details>

### Usporedba: Klasični streaming vs MCP streaming

Razlike između klasičnog streaminga i MCP streaminga mogu se prikazati ovako:

| Značajka               | Klasični HTTP streaming        | MCP streaming (notifikacije)       |
|------------------------|-------------------------------|-----------------------------------|
| Glavni odgovor         | Podijeljen na dijelove (chunked) | Jedan, na kraju                   |
| Ažuriranja napretka    | Šalju se kao dijelovi podataka | Šalju se kao notifikacije         |
| Zahtjevi klijenta      | Mora obrađivati stream         | Mora implementirati handler poruka|
| Primjena               | Velike datoteke, AI token streami | Napredak, logovi, real-time povratne informacije |

### Ključne uočene razlike

Dodatno, evo nekoliko ključnih razlika:

- **Obrazac komunikacije:**
   - Klasični HTTP streaming: koristi jednostavan chunked transfer encoding za slanje podataka u dijelovima
   - MCP streaming: koristi strukturirani sustav notifikacija s JSON-RPC protokolom

- **Format poruke:**
   - Klasični HTTP: običan tekst s novim redovima
   - MCP: strukturirani LoggingMessageNotification objekti s metapodacima

- **Implementacija klijenta:**
   - Klasični HTTP: jednostavan klijent koji obrađuje streaming odgovore
   - MCP: sofisticiraniji klijent s handlerom poruka za obradu različitih tipova poruka

- **Ažuriranja napretka:**
   - Klasični HTTP: napredak je dio glavnog streama odgovora
   - MCP: napredak se šalje putem zasebnih notifikacijskih poruka dok glavni odgovor dolazi na kraju

### Preporuke

Preporučujemo sljedeće prilikom odabira između klasičnog streaminga (kao što je endpoint `/stream` prikazan gore) i streaminga putem MCP-a:

- **Za jednostavne potrebe streaminga:** Klasični HTTP streaming je jednostavniji za implementaciju i dovoljan za osnovne potrebe.

- **Za složene, interaktivne aplikacije:** MCP streaming pruža strukturiraniji pristup s bogatijim metapodacima i razdvajanjem notifikacija i konačnih rezultata.

- **Za AI aplikacije:** MCP-ov sustav notifikacija posebno je koristan za dugotrajne AI zadatke gdje želite korisnike stalno informirati o napretku.

## Streaming u MCP-u

Dakle, vidjeli ste neke preporuke i usporedbe do sada o razlikama između klasičnog streaminga i streaminga u MCP-u. Sada ćemo detaljnije objasniti kako točno možete iskoristiti streaming u MCP-u.

Razumijevanje kako streaming funkcionira unutar MCP okvira ključno je za izgradnju responzivnih aplikacija koje pružaju real-time povratne informacije korisnicima tijekom dugotrajnih operacija.

U MCP-u, streaming nije slanje glavnog odgovora u dijelovima, već slanje **notifikacija** klijentu dok alat obrađuje zahtjev. Te notifikacije mogu uključivati ažuriranja napretka, logove ili druge događaje.

### Kako to radi

Glavni rezultat se i dalje šalje kao jedan odgovor. Međutim, notifikacije se mogu slati kao zasebne poruke tijekom obrade i na taj način ažurirati klijenta u realnom vremenu. Klijent mora biti sposoban obraditi i prikazati te notifikacije.

## Što je notifikacija?

Rekli smo "notifikacija", što to znači u kontekstu MCP-a?

Notifikacija je poruka poslana sa servera klijentu koja informira o napretku, statusu ili drugim događajima tijekom dugotrajne operacije. Notifikacije poboljšavaju transparentnost i korisničko iskustvo.

Na primjer, klijent bi trebao poslati notifikaciju čim je uspostavljena početna veza sa serverom.

Notifikacija izgleda ovako kao JSON poruka:

```json
{
  jsonrpc: "2.0";
  method: string;
  params?: {
    [key: string]: unknown;
  };
}
```

Notifikacije pripadaju temi u MCP-u nazvanoj ["Logging"](https://modelcontextprotocol.io/specification/draft/server/utilities/logging).

Da bi logging radio, server mora omogućiti tu značajku/kapacitet ovako:

```json
{
  "capabilities": {
    "logging": {}
  }
}
```

> [!NOTE]
> Ovisno o korištenom SDK-u, logging može biti omogućen po defaultu ili ga je potrebno eksplicitno uključiti u konfiguraciji servera.

Postoje različite vrste notifikacija:

| Razina    | Opis                          | Primjer upotrebe              |
|-----------|-------------------------------|------------------------------|
| debug     | Detaljne informacije za debug | Ulaz/izlaz funkcija          |
| info      | Opće informativne poruke       | Ažuriranja napretka operacije|
| notice    | Normalni, ali značajni događaji| Promjene konfiguracije       |
| warning   | Upozorenja                    | Korištenje zastarjele funkcije|
| error     | Greške                       | Neuspjesi operacija          |
| critical  | Kritični uvjeti              | Kvarovi sustavnih komponenti |
| alert     | Potrebna je hitna akcija     | Otkrivena korupcija podataka |
| emergency | Sustav neupotrebljiv         | Potpuni kvar sustava         |

## Implementacija notifikacija u MCP-u

Za implementaciju notifikacija u MCP-u, potrebno je postaviti i server i klijenta da podrže real-time ažuriranja. To omogućuje vašoj aplikaciji da korisnicima pruži trenutne povratne informacije tijekom dugotrajnih operacija.

### Server: Slanje notifikacija

Počnimo sa serverom. U MCP-u definirate alate koji mogu slati notifikacije tijekom obrade zahtjeva. Server koristi kontekst objekt (obično `ctx`) za slanje poruka klijentu.

<details>
<summary>Python</summary>

<details>
<summary>Python</summary>

```python
@mcp.tool(description="A tool that sends progress notifications")
async def process_files(message: str, ctx: Context) -> TextContent:
    await ctx.info("Processing file 1/3...")
    await ctx.info("Processing file 2/3...")
    await ctx.info("Processing file 3/3...")
    return TextContent(type="text", text=f"Done: {message}")
```

U prethodnom primjeru, alat `process_files` šalje tri notifikacije klijentu dok obrađuje svaku datoteku. Metoda `ctx.info()` koristi se za slanje informativnih poruka.

</details>

Također, da biste omogućili notifikacije, osigurajte da vaš server koristi streaming transport (kao `streamable-http`) i da klijent implementira handler poruka za obradu notifikacija. Evo kako postaviti server da koristi `streamable-http` transport:

```python
mcp.run(transport="streamable-http")
```

</details>

<details>
<summary>.NET</summary>

```csharp
[Tool("A tool that sends progress notifications")]
public async Task<TextContent> ProcessFiles(string message, ToolContext ctx)
{
    await ctx.Info("Processing file 1/3...");
    await ctx.Info("Processing file 2/3...");
    await ctx.Info("Processing file 3/3...");
    return new TextContent
    {
        Type = "text",
        Text = $"Done: {message}"
    };
}
```

U ovom .NET primjeru, alat `ProcessFiles` je označen atributom `Tool` i šalje tri notifikacije klijentu dok obrađuje svaku datoteku. Metoda `ctx.Info()` koristi se za slanje informativnih poruka.

Da biste omogućili notifikacije u vašem .NET MCP serveru, osigurajte da koristite streaming transport:

```csharp
var builder = McpBuilder.Create();
await builder
    .UseStreamableHttp() // Enable streamable HTTP transport
    .Build()
    .RunAsync();
```

</details>

### Klijent: Primanje notifikacija

Klijent mora implementirati handler poruka koji obrađuje i prikazuje notifikacije čim stignu.

<details>
<summary>Python</summary>

```python
async def message_handler(message):
    if isinstance(message, types.ServerNotification):
        print("NOTIFICATION:", message)
    else:
        print("SERVER MESSAGE:", message)

async with ClientSession(
   read_stream, 
   write_stream,
   logging_callback=logging_collector,
   message_handler=message_handler,
) as session:
```

U prethodnom kodu, funkcija `message_handler` provjerava je li dolazna poruka notifikacija. Ako jest, ispisuje notifikaciju; inače je obrađuje kao redovitu server poruku. Također, primijetite kako je `ClientSession` inicijaliziran s `message_handler` za obradu dolaznih notifikacija.

</details>

<details>
<summary>.NET</summary>

```csharp
// Define a message handler
void MessageHandler(IJsonRpcMessage message)
{
    if (message is ServerNotification notification)
    {
        Console.WriteLine($"NOTIFICATION: {notification}");
    }
    else
    {
        Console.WriteLine($"SERVER MESSAGE: {message}");
    }
}

// Create and use a client session with the message handler
var clientOptions = new ClientSessionOptions
{
    MessageHandler = MessageHandler,
    LoggingCallback = (level, message) => Console.WriteLine($"[{level}] {message}")
};

using var client = new ClientSession(readStream, writeStream, clientOptions);
await client.InitializeAsync();

// Now the client will process notifications through the MessageHandler
```

U ovom .NET primjeru, funkcija `MessageHandler` provjerava je li dolazna poruka notifikacija. Ako jest, ispisuje notifikaciju; inače je obrađuje kao redovitu server poruku. `ClientSession` je inicijaliziran s handlerom poruka putem `ClientSessionOptions`.

</details>

Da biste omogućili notifikacije, osigurajte da vaš server koristi streaming transport (kao `streamable-http`) i da klijent implementira handler poruka za obradu notifikacija.

## Notifikacije napretka i scenariji

Ovaj odjeljak objašnjava koncept notifikacija napretka u MCP-u, zašto su važne i kako ih implementirati koristeći Streamable HTTP. Također ćete pronaći praktični zadatak za jačanje razumijevanja.

Notifikacije napretka su real-time poruke koje server šalje klijentu tijekom dugotrajnih operacija. Umjesto da se čeka da cijeli proces završi, server stalno obavještava klijenta o trenutnom statusu. To poboljšava transparentnost, korisničko iskustvo i olakšava debugiranje.

**Primjer:**

```text

"Processing document 1/10"
"Processing document 2/10"
...
"Processing complete!"

```

### Zašto koristiti notifikacije napretka?

Notifikacije napretka su važne iz nekoliko razloga:

- **Bolje korisničko iskustvo:** Korisnici vide ažuriranja tijekom rada, ne samo na kraju.
- **Real-time povratne informacije:** Klijenti mogu prikazivati trake napretka ili logove, čineći aplikaciju responzivnijom.
- **Lakše debugiranje i nadzor:** Programeri i korisnici mogu vidjeti gdje proces može biti spor ili zapeti.

### Kako implementirati notifikacije napretka

Evo kako možete implementirati notifikacije napretka u MCP-u:

- **Na serveru:** Koristite `ctx.info()` ili `ctx.log()` za slanje notifikacija dok se svaki element obrađuje. Time se šalje poruka klijentu prije nego što je glavni rezultat spreman.
- **Na klijentu:** Implementirajte handler poruka koji sluša i prikazuje notifikacije čim stignu. Taj handler razlikuje notifikacije od konačnog rezultata.

**Primjer servera:**

<summary>Python</summary>

```python
@mcp.tool(description="A tool that sends progress notifications")
async def process_files(message: str, ctx: Context) -> TextContent:
    for i in range(1, 11):
        await ctx.info(f"Processing document {i}/10")
    await ctx.info("Processing complete!")
    return TextContent(type="text", text=f"Done: {message}")
```

</details>

**Primjer klijenta:**

<details>
<summary>Python</summary>

```python
async def message_handler(message):
    if isinstance(message, types.ServerNotification):
        print("NOTIFICATION:", message)
    else:
        print("SERVER MESSAGE:", message)
```

</details>

## Sigurnosne napomene

Kod implementacije MCP servera s HTTP transportima, sigurnost postaje ključna tema koja zahtijeva pažnju na različite napade i mehanizme zaštite.

### Pregled

Sigurnost je presudna pri izlaganju MCP servera preko HTTP-a. Streamable HTTP donosi nove ranjivosti i zahtijeva pažljivu konfiguraciju.

### Ključne točke
- **Provjera Origin zaglavlja**: Uvijek provjeravajte `Origin` zaglavlje kako biste spriječili DNS rebinding napade.
- **Veza na localhost**: Za lokalni razvoj vežite server na `localhost` kako ne biste izložili server javnom internetu.
- **Autentikacija**: Implementirajte autentikaciju (npr. API ključeve, OAuth) za produkcijska okruženja.
- **CORS**: Konfigurirajte politike Cross-Origin Resource Sharing (CORS) za ograničavanje pristupa.
- **HTTPS**: U produkciji koristite HTTPS za enkripciju prometa.

### Najbolje prakse
- Nikada ne vjerujte dolaznim zahtjevima bez provjere.
- Bilježite i pratite sav pristup i greške.
- Redovito ažurirajte ovisnosti kako biste zakrpali sigurnosne propuste.

### Izazovi
- Uravnotežiti sigurnost i jednostavnost razvoja
- Osigurati kompatibilnost s različitim klijentskim okruženjima


## Nadogradnja sa SSE na Streamable HTTP

Za aplikacije koje trenutno koriste Server-Sent Events (SSE), prelazak na Streamable HTTP donosi bolje mogućnosti i dugoročnu održivost MCP implementacija.

### Zašto nadograditi?

Postoje dva glavna razloga za prelazak sa SSE na Streamable HTTP:

- Streamable HTTP nudi bolju skalabilnost, kompatibilnost i bogatiju podršku za notifikacije u odnosu na SSE.
- To je preporučeni transport za nove MCP aplikacije.

### Koraci migracije

Evo kako možete migrirati sa SSE na Streamable HTTP u svojim MCP aplikacijama:

- **Ažurirajte kod servera** da koristi `transport="streamable-http"` u `mcp.run()`.
- **Ažurirajte kod klijenta** da koristi `streamablehttp_client` umjesto SSE klijenta.
- **Implementirajte handler poruka** u klijentu za obradu notifikacija.
- **Testirajte kompatibilnost** s postojećim alatima i radnim tokovima.

### Održavanje kompatibilnosti

Preporučuje se održavati kompatibilnost s postojećim SSE klijentima tijekom migracije. Evo nekoliko strategija:

- Možete podržavati oba transporta, SSE i Streamable HTTP, na različitim endpointima.
- Postupno migrirajte klijente na novi transport.

### Izazovi

Tijekom migracije obratite pažnju na sljedeće izazove:

- Osigurati da su svi klijenti ažurirani
- Rukovati razlikama u isporuci notifikacija

## Sigurnosne napomene

Sigurnost treba biti prioritet kod implementacije bilo kojeg servera, posebno pri korištenju HTTP transporta poput Streamable HTTP u MCP-u.

Kod implementacije MCP servera s HTTP transportima, sigurnost postaje ključna tema koja zahtijeva pažnju na različite napade i mehanizme zaštite.

### Pregled

Sigurnost je presudna pri izlaganju MCP servera preko HTTP-a. Streamable HTTP donosi nove ranjivosti i zahtijeva pažljivu konfiguraciju.

Evo nekoliko ključnih sigurnosnih napomena:

- **Provjera Origin zaglavlja**: Uvijek provjeravajte `Origin` zaglavlje kako biste spriječili DNS rebinding napade.
- **Veza na localhost**: Za lokalni razvoj vežite server na `localhost` kako ne biste izložili server javnom internetu.
- **Autentikacija**: Implementirajte autentikaciju (npr. API ključeve, OAuth) za produkcijska okruženja.
- **CORS**: Konfigurirajte politike Cross-Origin Resource Sharing (CORS) za ograničavanje pristupa.
- **HTTPS**: U produkciji koristite HTTPS za enkripciju prometa.

### Najbolje prakse

Također, evo nekoliko preporučenih praksi za sigurnu implementaciju MCP streaming servera:

- Nikada ne vjerujte dolaznim zahtjevima bez provjere.
- Bilježite i pratite sav pristup i greške.
- Redovito ažurirajte ovisnosti kako biste zakrpali sigurnosne propuste.

### Izazovi

Prilikom implementacije sigurnosti u MCP streaming serverima suočit ćete se s nekim izazovima:

- Uravnotežiti sigurnost i jednostavnost razvoja
- Osigurati kompatibilnost s različitim klijentskim okruženjima

### Zadatak: Izradite vlastitu streaming MCP aplikaciju

**Scenarij:**
Izradite MCP server i klijenta gdje server obrađuje popis stavki (npr. datoteka ili dokumenata) i šalje notifikaciju za svaku obrađenu stavku. Klijent treba prikazivati svaku notifikaciju čim stigne.

**Koraci:**

1. Implementirajte server koji obrađuje popis i šalje notifikacije za svaku stavku.
2. Implementirajte klijenta s handlerom poruka koji prikazuje notifikacije u stvarnom vremenu.
3. Testirajte implementaciju pokretanjem servera i klijenta te pratite notifikacije.

[Rješenje](./solution/README.md)

## Dodatno čitanje i što dalje?

Za nastavak učenja o MCP streamingu i proširenje znanja, ovaj odjeljak nudi dodatne izvore i prijedloge za daljnji razvoj naprednijih aplikacija.

### Dodatno čitanje

- [Microsoft: Uvod u HTTP streaming](https://learn.microsoft.com/aspnet/core/fundamentals/http-requests?view=aspnetcore-8.0&WT.mc_id=%3Fwt.mc_id%3DMVP_452430#streaming)
- [Microsoft: Server-Sent Events (SSE)](https://learn.microsoft.com/azure/application-gateway/for-containers/server-sent-events?tabs=server-sent-events-gateway-api&WT.mc_id=%3Fwt.mc_id%3DMVP_452430)
- [Microsoft: CORS u ASP.NET Core](https://learn.microsoft.com/en-us/aspnet/core/security/cors?view=aspnetcore-8.0&WT.mc_id=%3Fwt.mc_id%3DMVP_452430)
- [Python requests: Streaming Requests](https://requests.readthedocs.io/en/latest/user/advanced/#streaming-requests)

### Što dalje?

- Isprobajte izradu naprednijih MCP alata koji koriste streaming za analitiku u stvarnom vremenu, chat ili suradničko uređivanje.
- Istražite integraciju MCP streaminga s frontend frameworkima (React, Vue itd.) za live ažuriranja korisničkog sučelja.
- Sljedeće: [Korištenje AI Toolkit za VSCode](../07-aitk/README.md)

**Odricanje od odgovornosti**:  
Ovaj dokument je preveden korištenjem AI usluge za prevođenje [Co-op Translator](https://github.com/Azure/co-op-translator). Iako težimo točnosti, imajte na umu da automatski prijevodi mogu sadržavati pogreške ili netočnosti. Izvorni dokument na izvornom jeziku treba smatrati autoritativnim izvorom. Za kritične informacije preporučuje se profesionalni ljudski prijevod. Ne snosimo odgovornost za bilo kakva nesporazume ili pogrešna tumačenja koja proizlaze iz korištenja ovog prijevoda.