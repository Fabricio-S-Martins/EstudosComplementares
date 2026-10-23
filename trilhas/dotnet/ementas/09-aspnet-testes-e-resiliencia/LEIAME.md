# 09 — ASP.NET Core, Testes e Resiliência

> **Ementa complementar** (além do escopo original) com temas que costumam cair em entrevistas de Backend .NET.  
> Nível: **Pleno/Sênior**.

## Tópicos

### Pipeline do ASP.NET Core
- Middleware: ordem importa (`UseRouting`, `UseAuthentication`, `UseAuthorization`, tratamento de exceção).
- Filtros (action, exception, authorization) vs middleware: quando usar cada um.
- Model binding e validação; `ProblemDetails` e tratamento global de exceções.
- `IOptions`, `IOptionsSnapshot`, `IOptionsMonitor`.

### Segurança
- Autenticação vs autorização; JWT (estrutura, expiração, validação, onde **não** guardar segredos).
- Policy-based authorization e claims.
- CORS: o que protege e o que não protege.
- Armadilhas: dados sensíveis em log, exposição de entidades de domínio na API, mass assignment.

### Testes
- Pirâmide: unitário, integração, ponta a ponta.
- xUnit; Arrange-Act-Assert; nome de teste que descreve o comportamento.
- Mock vs Fake vs Stub; o que **não** vale a pena mockar (DbContext, tipos simples).
- Testes de integração com `WebApplicationFactory` e banco real/containerizado.
- Testes frágeis: dependência de ordem, relógio, rede.

### Cache e resiliência
- `IMemoryCache` vs cache distribuído (Redis); expiração, invalidação, cache stampede.
- Retry com backoff exponencial e jitter; circuit breaker; timeout (Polly / `Microsoft.Extensions.Resilience`).
- Retry sem idempotência = duplicação. Ligar com mensageria (módulo 06).
- `IHttpClientFactory` e políticas por cliente.

### Observabilidade básica
- Logs estruturados, níveis de log, correlation id / trace id.
- Métricas e health checks (liveness vs readiness).
- O que **não** logar (PII, tokens).

## Sinais de resposta ⭐ (nível Sênior)
- Cita a **ordem do pipeline** e o efeito de errá-la.
- Liga resiliência a **idempotência** e a risco de tempestade de retries.
- Sabe o custo de cada tipo de teste e onde investir.
