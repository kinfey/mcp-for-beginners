<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "50d9cd44fa74ad04f716fe31daf0c850",
  "translation_date": "2025-07-14T02:39:20+00:00",
  "source_file": "05-AdvancedTopics/mcp-security/README.md",
  "language_code": "pl"
}
-->
# Najlepsze praktyki bezpieczeństwa

Bezpieczeństwo jest kluczowe dla implementacji MCP, zwłaszcza w środowiskach korporacyjnych. Ważne jest, aby narzędzia i dane były chronione przed nieautoryzowanym dostępem, wyciekami danych oraz innymi zagrożeniami bezpieczeństwa.

## Wprowadzenie

W tej lekcji omówimy najlepsze praktyki bezpieczeństwa dla implementacji MCP. Poruszymy tematy związane z uwierzytelnianiem i autoryzacją, ochroną danych, bezpiecznym uruchamianiem narzędzi oraz zgodnością z przepisami dotyczącymi prywatności danych.

## Cele nauki

Po zakończeniu tej lekcji będziesz potrafił:

- Wdrażać bezpieczne mechanizmy uwierzytelniania i autoryzacji dla serwerów MCP.
- Chronić wrażliwe dane za pomocą szyfrowania i bezpiecznego przechowywania.
- Zapewnić bezpieczne uruchamianie narzędzi z odpowiednią kontrolą dostępu.
- Stosować najlepsze praktyki dotyczące ochrony danych i zgodności z przepisami o prywatności.

## Uwierzytelnianie i autoryzacja

Uwierzytelnianie i autoryzacja są niezbędne do zabezpieczenia serwerów MCP. Uwierzytelnianie odpowiada na pytanie „Kim jesteś?”, natomiast autoryzacja na „Co możesz zrobić?”.

Przyjrzyjmy się przykładom implementacji bezpiecznego uwierzytelniania i autoryzacji w serwerach MCP z użyciem .NET i Java.

### Integracja .NET Identity

ASP .NET Core Identity oferuje solidne ramy do zarządzania uwierzytelnianiem i autoryzacją użytkowników. Możemy zintegrować je z serwerami MCP, aby zabezpieczyć dostęp do narzędzi i zasobów.

Istnieje kilka kluczowych pojęć, które musimy zrozumieć podczas integracji ASP.NET Core Identity z serwerami MCP, mianowicie:

- **Konfiguracja Identity**: Ustawienie ASP.NET Core Identity z rolami użytkowników i roszczeniami (claims). Roszczenie to informacja o użytkowniku, na przykład jego rola lub uprawnienia, takie jak „Admin” lub „User”.
- **Uwierzytelnianie JWT**: Wykorzystanie JSON Web Tokens (JWT) do bezpiecznego dostępu do API. JWT to standard bezpiecznego przesyłania informacji między stronami w formacie JSON, który można zweryfikować i zaufać mu, ponieważ jest cyfrowo podpisany.
- **Polityki autoryzacji**: Definiowanie polityk kontrolujących dostęp do konkretnych narzędzi na podstawie ról użytkowników. MCP używa polityk autoryzacji, aby określić, którzy użytkownicy mogą korzystać z których narzędzi na podstawie ich ról i roszczeń.

```csharp
public class SecureMcpStartup
{
    public void ConfigureServices(IServiceCollection services)
    {
        // Add ASP.NET Core Identity
        services.AddIdentity<ApplicationUser, IdentityRole>()
            .AddEntityFrameworkStores<ApplicationDbContext>()
            .AddDefaultTokenProviders();
        
        // Configure JWT authentication
        services.AddAuthentication(options =>
        {
            options.DefaultAuthenticateScheme = JwtBearerDefaults.AuthenticationScheme;
            options.DefaultChallengeScheme = JwtBearerDefaults.AuthenticationScheme;
        })
        .AddJwtBearer(options =>
        {
            options.TokenValidationParameters = new TokenValidationParameters
            {
                ValidateIssuer = true,
                ValidateAudience = true,
                ValidateLifetime = true,
                ValidateIssuerSigningKey = true,
                ValidIssuer = Configuration["Jwt:Issuer"],
                ValidAudience = Configuration["Jwt:Audience"],
                IssuerSigningKey = new SymmetricSecurityKey(
                    Encoding.UTF8.GetBytes(Configuration["Jwt:Key"]))
            };
        });
        
        // Add authorization policies
        services.AddAuthorization(options =>
        {
            options.AddPolicy("CanUseAdminTools", policy =>
                policy.RequireRole("Admin"));
                
            options.AddPolicy("CanUseBasicTools", policy =>
                policy.RequireAuthenticatedUser());
        });
        
        // Configure MCP server with security
        services.AddMcpServer(options =>
        {
            options.ServerName = "Secure MCP Server";
            options.ServerVersion = "1.0.0";
            options.RequireAuthentication = true;
        });
        
        // Register tools with authorization requirements
        services.AddMcpTool<BasicTool>(options => 
            options.RequirePolicy("CanUseBasicTools"));
            
        services.AddMcpTool<AdminTool>(options => 
            options.RequirePolicy("CanUseAdminTools"));
    }
    
    public void Configure(IApplicationBuilder app)
    {
        // Use authentication and authorization
        app.UseAuthentication();
        app.UseAuthorization();
        
        // Use MCP server middleware
        app.UseMcpServer();
    }
}
```

W powyższym kodzie:

- Skonfigurowaliśmy ASP.NET Core Identity do zarządzania użytkownikami.
- Ustawiliśmy uwierzytelnianie JWT dla bezpiecznego dostępu do API. Określiliśmy parametry walidacji tokena, w tym wydawcę, odbiorcę i klucz podpisu.
- Zdefiniowaliśmy polityki autoryzacji kontrolujące dostęp do narzędzi na podstawie ról użytkowników. Na przykład polityka „CanUseAdminTools” wymaga, aby użytkownik miał rolę „Admin”, natomiast polityka „CanUseBasic” wymaga, aby użytkownik był uwierzytelniony.
- Zarejestrowaliśmy narzędzia MCP z określonymi wymaganiami autoryzacyjnymi, zapewniając, że tylko użytkownicy z odpowiednimi rolami mają do nich dostęp.

### Integracja Java Spring Security

Dla Javy użyjemy Spring Security do implementacji bezpiecznego uwierzytelniania i autoryzacji dla serwerów MCP. Spring Security oferuje kompleksowe ramy bezpieczeństwa, które integrują się bezproblemowo z aplikacjami Spring.

Kluczowe pojęcia to:

- **Konfiguracja Spring Security**: Ustawienie konfiguracji bezpieczeństwa dla uwierzytelniania i autoryzacji.
- **OAuth2 Resource Server**: Wykorzystanie OAuth2 do bezpiecznego dostępu do narzędzi MCP. OAuth2 to framework autoryzacji, który pozwala usługom trzecim wymieniać tokeny dostępu dla bezpiecznego dostępu do API.
- **Interceptory bezpieczeństwa**: Implementacja interceptorów bezpieczeństwa do egzekwowania kontroli dostępu podczas uruchamiania narzędzi.
- **Kontrola dostępu oparta na rolach**: Wykorzystanie ról do kontrolowania dostępu do konkretnych narzędzi i zasobów.
- **Adnotacje bezpieczeństwa**: Użycie adnotacji do zabezpieczania metod i punktów końcowych.

```java
@Configuration
@EnableWebSecurity
public class SecurityConfig extends WebSecurityConfigurerAdapter {

    @Override
    protected void configure(HttpSecurity http) throws Exception {
        http
            .csrf().disable()
            .authorizeRequests()
                .antMatchers("/mcp/discovery").permitAll() // Allow tool discovery
                .antMatchers("/mcp/tools/**").hasAnyRole("USER", "ADMIN") // Require authentication for tools
                .antMatchers("/mcp/admin/**").hasRole("ADMIN") // Admin-only endpoints
                .anyRequest().authenticated()
            .and()
            .oauth2ResourceServer().jwt();
    }
    
    @Bean
    public McpSecurityInterceptor mcpSecurityInterceptor() {
        return new McpSecurityInterceptor();
    }
}

// MCP Security Interceptor for tool authorization
public class McpSecurityInterceptor implements ToolExecutionInterceptor {
    @Autowired
    private JwtDecoder jwtDecoder;
    
    @Override
    public void beforeToolExecution(ToolRequest request, Authentication authentication) {
        String toolName = request.getToolName();
        
        // Check if user has permissions for this tool
        if (toolName.startsWith("admin") && !authentication.getAuthorities().contains("ROLE_ADMIN")) {
            throw new AccessDeniedException("You don't have permission to use this tool");
        }
        
        // Additional security checks based on tool or parameters
        if ("sensitiveDataAccess".equals(toolName)) {
            validateDataAccessPermissions(request, authentication);
        }
    }
    
    private void validateDataAccessPermissions(ToolRequest request, Authentication auth) {
        // Implementation to check fine-grained data access permissions
    }
}
```

W powyższym kodzie:

- Skonfigurowaliśmy Spring Security, aby zabezpieczyć punkty końcowe MCP, umożliwiając publiczny dostęp do wykrywania narzędzi, a wymagając uwierzytelnienia do ich uruchamiania.
- Użyliśmy OAuth2 jako resource server do obsługi bezpiecznego dostępu do narzędzi MCP.
- Wdrożyliśmy interceptor bezpieczeństwa, który egzekwuje kontrolę dostępu podczas uruchamiania narzędzi, sprawdzając role i uprawnienia użytkownika przed udzieleniem dostępu do konkretnych narzędzi.
- Zdefiniowaliśmy kontrolę dostępu opartą na rolach, aby ograniczyć dostęp do narzędzi administracyjnych i wrażliwych danych na podstawie ról użytkowników.

## Ochrona danych i prywatność

Ochrona danych jest kluczowa, aby zapewnić, że wrażliwe informacje są przetwarzane w sposób bezpieczny. Obejmuje to ochronę danych osobowych (PII), danych finansowych oraz innych wrażliwych informacji przed nieautoryzowanym dostępem i wyciekami.

### Przykład ochrony danych w Pythonie

Spójrzmy na przykład implementacji ochrony danych w Pythonie z użyciem szyfrowania i wykrywania PII.

```python
from mcp_server import McpServer
from mcp_tools import Tool, ToolRequest, ToolResponse
from cryptography.fernet import Fernet
import os
import json
from functools import wraps

# PII Detector - identifies and protects sensitive information
class PiiDetector:
    def __init__(self):
        # Load patterns for different types of PII
        with open("pii_patterns.json", "r") as f:
            self.patterns = json.load(f)
    
    def scan_text(self, text):
        """Scans text for PII and returns detected PII types"""
        detected_pii = []
        # Implementation to detect PII using regex or ML models
        return detected_pii
    
    def scan_parameters(self, parameters):
        """Scans request parameters for PII"""
        detected_pii = []
        for key, value in parameters.items():
            if isinstance(value, str):
                pii_in_value = self.scan_text(value)
                if pii_in_value:
                    detected_pii.append((key, pii_in_value))
        return detected_pii

# Encryption Service for protecting sensitive data
class EncryptionService:
    def __init__(self, key_path=None):
        if key_path and os.path.exists(key_path):
            with open(key_path, "rb") as key_file:
                self.key = key_file.read()
        else:
            self.key = Fernet.generate_key()
            if key_path:
                with open(key_path, "wb") as key_file:
                    key_file.write(self.key)
        
        self.cipher = Fernet(self.key)
    
    def encrypt(self, data):
        """Encrypt data"""
        if isinstance(data, str):
            return self.cipher.encrypt(data.encode()).decode()
        else:
            return self.cipher.encrypt(json.dumps(data).encode()).decode()
    
    def decrypt(self, encrypted_data):
        """Decrypt data"""
        if encrypted_data is None:
            return None
        
        decrypted = self.cipher.decrypt(encrypted_data.encode())
        try:
            return json.loads(decrypted)
        except:
            return decrypted.decode()

# Security decorator for tools
def secure_tool(requires_encryption=False, log_access=True):
    def decorator(cls):
        original_execute = cls.execute_async if hasattr(cls, 'execute_async') else cls.execute
        
        @wraps(original_execute)
        async def secure_execute(self, request):
            # Check for PII in request
            pii_detector = PiiDetector()
            pii_found = pii_detector.scan_parameters(request.parameters)
            
            # Log access if required
            if log_access:
                tool_name = self.get_name()
                user_id = request.context.get("user_id", "anonymous")
                log_entry = {
                    "timestamp": datetime.now().isoformat(),
                    "tool": tool_name,
                    "user": user_id,
                    "contains_pii": bool(pii_found),
                    "parameters": {k: "***" for k in request.parameters.keys()}  # Don't log actual values
                }
                logging.info(f"Tool access: {json.dumps(log_entry)}")
            
            # Handle detected PII
            if pii_found:
                # Either encrypt sensitive data or reject the request
                if requires_encryption:
                    encryption_service = EncryptionService("keys/tool_key.key")
                    for param_name, pii_types in pii_found:
                        # Encrypt the sensitive parameter
                        request.parameters[param_name] = encryption_service.encrypt(
                            request.parameters[param_name]
                        )
                else:
                    # If encryption not available but PII found, you might reject the request
                    raise ToolExecutionException(
                        "Request contains sensitive data that cannot be processed securely"
                    )
            
            # Execute the original method
            return await original_execute(self, request)
        
        # Replace the execute method
        if hasattr(cls, 'execute_async'):
            cls.execute_async = secure_execute
        else:
            cls.execute = secure_execute
        return cls
    
    return decorator

# Example of a secure tool with the decorator
@secure_tool(requires_encryption=True, log_access=True)
class SecureCustomerDataTool(Tool):
    def get_name(self):
        return "customerData"
    
    def get_description(self):
        return "Accesses customer data securely"
    
    def get_schema(self):
        # Schema definition
        return {}
    
    async def execute_async(self, request):
        # Implementation would access customer data securely
        # Since we used the decorator, PII is already detected and encrypted
        return ToolResponse(result={"status": "success"})
```

W powyższym kodzie:

- Zaimplementowaliśmy klasę `PiiDetector`, która skanuje tekst i parametry pod kątem danych osobowych (PII).
- Stworzyliśmy klasę `EncryptionService` do obsługi szyfrowania i odszyfrowywania wrażliwych danych z użyciem biblioteki `cryptography`.
- Zdefiniowaliśmy dekorator `secure_tool`, który otacza wykonanie narzędzia, sprawdzając obecność PII, logując dostęp oraz szyfrując wrażliwe dane, jeśli jest to wymagane.
- Zastosowaliśmy dekorator `secure_tool` do przykładowego narzędzia (`SecureCustomerDataTool`), aby zapewnić bezpieczne przetwarzanie danych wrażliwych.

## Co dalej

- [5.9 Web search](../web-search-mcp/README.md)

**Zastrzeżenie**:  
Niniejszy dokument został przetłumaczony za pomocą usługi tłumaczenia AI [Co-op Translator](https://github.com/Azure/co-op-translator). Mimo że dokładamy starań, aby tłumaczenie było jak najbardziej precyzyjne, prosimy mieć na uwadze, że automatyczne tłumaczenia mogą zawierać błędy lub nieścisłości. Oryginalny dokument w języku źródłowym należy traktować jako źródło wiążące. W przypadku informacji o kluczowym znaczeniu zalecane jest skorzystanie z profesjonalnego tłumaczenia wykonanego przez człowieka. Nie ponosimy odpowiedzialności za jakiekolwiek nieporozumienia lub błędne interpretacje wynikające z korzystania z tego tłumaczenia.