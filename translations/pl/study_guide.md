<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "a607d4febc94caee9a12b77795f7fc9a",
  "translation_date": "2025-07-13T15:14:00+00:00",
  "source_file": "study_guide.md",
  "language_code": "pl"
}
-->
# Model Context Protocol (MCP) dla początkujących - przewodnik nauki

Ten przewodnik nauki przedstawia przegląd struktury i zawartości repozytorium dla kursu „Model Context Protocol (MCP) dla początkujących”. Skorzystaj z tego przewodnika, aby efektywnie poruszać się po repozytorium i w pełni wykorzystać dostępne zasoby.

## Przegląd repozytorium

Model Context Protocol (MCP) to ustandaryzowane ramy do interakcji między modelami AI a aplikacjami klienckimi. To repozytorium oferuje kompleksowy program nauczania z praktycznymi przykładami kodu w C#, Java, JavaScript, Python oraz TypeScript, przeznaczony dla deweloperów AI, architektów systemów i inżynierów oprogramowania.

## Wizualna mapa programu nauczania

```mermaid
mindmap
  root((MCP for Beginners))
    00. Introduction
      ::icon(fa fa-book)
      (Protocol Overview)
      (Standardization)
      (Use Cases)
    01. Core Concepts
      ::icon(fa fa-puzzle-piece)
      (Client-Server Architecture)
      (Protocol Components)
      (Messaging Patterns)
    02. Security
      ::icon(fa fa-shield)
      (Threat Models)
      (Best Practices)
      (Auth Strategies)
    03. Getting Started
      ::icon(fa fa-rocket)
      (First Server)
      (First Client)
      (LLM Client)
      (VS Code Integration)
      (SSE Server)
      (AI Toolkit)
      (Testing)
      (Deployment)
    04. Practical Implementation
      ::icon(fa fa-code)
      (SDKs)
      (Testing/Debugging)
      (Prompt Templates)
      (Sample Projects)
    05. Advanced Topics
      ::icon(fa fa-graduation-cap)
      (Multi-modal AI)
      (Scaling)
      (Enterprise Integration)
      (Azure Integration)
      (OAuth2)
      (Root Contexts)
    06. Community
      ::icon(fa fa-users)
      (Code Contributions)
      (Documentation)
      (Feedback)
    07. Early Adoption
      ::icon(fa fa-lightbulb)
      (Real-world Examples)
      (Deployment Stories)
      (Future Roadmap)
    08. Best Practices
      ::icon(fa fa-check)
      (Performance)
      (Fault Tolerance)
      (Resilience)
    09. Case Studies
      ::icon(fa fa-file-text)
      (Solution Architectures)
      (Deployment Blueprints)
      (Project Walkthroughs)
    10. Hands-on Workshop
      ::icon(fa fa-laptop)
      (AI Toolkit Integration)
      (Custom Server Development)
      (Production Deployment)
```

## Struktura repozytorium

Repozytorium jest podzielone na dziesięć głównych sekcji, z których każda skupia się na innym aspekcie MCP:

1. **Wprowadzenie (00-Introduction/)**
   - Przegląd Model Context Protocol
   - Dlaczego standaryzacja jest ważna w pipeline’ach AI
   - Praktyczne zastosowania i korzyści

2. **Podstawowe pojęcia (01-CoreConcepts/)**
   - Architektura klient-serwer
   - Kluczowe elementy protokołu
   - Wzorce komunikacji w MCP

3. **Bezpieczeństwo (02-Security/)**
   - Zagrożenia bezpieczeństwa w systemach opartych na MCP
   - Najlepsze praktyki zabezpieczania implementacji
   - Strategie uwierzytelniania i autoryzacji

4. **Pierwsze kroki (03-GettingStarted/)**
   - Konfiguracja środowiska i ustawienia
   - Tworzenie podstawowych serwerów i klientów MCP
   - Integracja z istniejącymi aplikacjami
   - Podsekcje dotyczące pierwszego serwera, pierwszego klienta, klienta LLM, integracji z VS Code, serwera SSE, AI Toolkit, testowania i wdrażania

5. **Praktyczna implementacja (04-PracticalImplementation/)**
   - Korzystanie z SDK w różnych językach programowania
   - Techniki debugowania, testowania i walidacji
   - Tworzenie wielokrotnego użytku szablonów promptów i workflowów
   - Przykładowe projekty z przykładami implementacji

6. **Zaawansowane tematy (05-AdvancedTopics/)**
   - Wielomodalne workflowy AI i rozszerzalność
   - Bezpieczne strategie skalowania
   - MCP w ekosystemach korporacyjnych
   - Tematy specjalistyczne, w tym integracja z Azure, multimodalność, OAuth2, root contexts, routing, sampling, skalowanie, bezpieczeństwo, integracja z wyszukiwarką internetową i streaming

7. **Wkład społeczności (06-CommunityContributions/)**
   - Jak wnosić kod i dokumentację
   - Współpraca przez GitHub
   - Ulepszenia i opinie napędzane przez społeczność

8. **Wnioski z wczesnej adopcji (07-LessonsfromEarlyAdoption/)**
   - Realne wdrożenia i historie sukcesu
   - Budowa i wdrażanie rozwiązań opartych na MCP
   - Trendy i przyszła mapa drogowa

9. **Najlepsze praktyki (08-BestPractices/)**
   - Optymalizacja wydajności i tuning
   - Projektowanie odpornych na błędy systemów MCP
   - Strategie testowania i odporności

10. **Studia przypadków (09-CaseStudy/)**
    - Dogłębne analizy architektur rozwiązań MCP
    - Plany wdrożeniowe i wskazówki integracyjne
    - Oznaczone diagramy i omówienia projektów

11. **Warsztaty praktyczne (10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/)**
    - Kompleksowy warsztat praktyczny łączący MCP z Microsoft AI Toolkit dla VS Code
    - Budowa inteligentnych aplikacji łączących modele AI z narzędziami rzeczywistymi
    - Praktyczne moduły obejmujące podstawy, tworzenie niestandardowego serwera i strategie wdrożenia produkcyjnego

## Przykładowe projekty

Repozytorium zawiera wiele przykładowych projektów demonstrujących implementację MCP w różnych językach programowania:

### Podstawowe przykłady kalkulatora MCP
- Przykład serwera MCP w C#
- Kalkulator MCP w Javie
- Demo MCP w JavaScript
- Serwer MCP w Pythonie
- Przykład MCP w TypeScript

### Zaawansowane projekty kalkulatora MCP
- Zaawansowany przykład w C#
- Przykład aplikacji kontenerowej w Javie
- Zaawansowany przykład w JavaScript
- Złożona implementacja w Pythonie
- Przykład kontenera w TypeScript

## Dodatkowe zasoby

Repozytorium zawiera materiały wspierające:

- **Folder Images**: Zawiera diagramy i ilustracje używane w całym kursie
- **Tłumaczenia**: Wsparcie wielojęzyczne z automatycznymi tłumaczeniami dokumentacji
- **Oficjalne zasoby MCP**:
  - [MCP Documentation](https://modelcontextprotocol.io/)
  - [MCP Specification](https://spec.modelcontextprotocol.io/)
  - [MCP GitHub Repository](https://github.com/modelcontextprotocol)

## Jak korzystać z tego repozytorium

1. **Nauka krok po kroku**: Przechodź przez rozdziały po kolei (od 00 do 10), aby uzyskać uporządkowaną ścieżkę nauki.
2. **Skupienie na konkretnym języku**: Jeśli interesuje Cię konkretny język programowania, przeglądaj katalogi z przykładami w wybranym języku.
3. **Praktyczna implementacja**: Zacznij od sekcji „Pierwsze kroki”, aby skonfigurować środowisko i stworzyć swój pierwszy serwer i klient MCP.
4. **Zaawansowane zagadnienia**: Gdy opanujesz podstawy, zagłęb się w tematy zaawansowane, aby poszerzyć wiedzę.
5. **Zaangażowanie społeczności**: Dołącz do [Azure AI Foundry Discord](https://discord.com/invite/ByRwuEEgH4), aby połączyć się z ekspertami i innymi deweloperami.

## Wkład w projekt

To repozytorium zachęca do wkładu ze strony społeczności. Zobacz sekcję Wkład społeczności, aby dowiedzieć się, jak możesz pomóc.

---

*Ten przewodnik nauki został stworzony 11 czerwca 2025 roku i przedstawia stan repozytorium na ten dzień. Zawartość repozytorium mogła ulec zmianie od tego czasu.*

**Zastrzeżenie**:  
Niniejszy dokument został przetłumaczony przy użyciu usługi tłumaczenia AI [Co-op Translator](https://github.com/Azure/co-op-translator). Mimo że dążymy do dokładności, prosimy mieć na uwadze, że automatyczne tłumaczenia mogą zawierać błędy lub nieścisłości. Oryginalny dokument w języku źródłowym powinien być uznawany za źródło autorytatywne. W przypadku informacji krytycznych zalecane jest skorzystanie z profesjonalnego tłumaczenia wykonanego przez człowieka. Nie ponosimy odpowiedzialności za jakiekolwiek nieporozumienia lub błędne interpretacje wynikające z korzystania z tego tłumaczenia.