# 04 — Injeção de Dependência

> **Ementa para o assistente gerar perguntas novas.** Nível: **Pleno/Sênior**.

## Tópicos

### Ciclos de vida
- **Transient:** nova instância a cada resolução. Casos reais: serviços leves e sem estado, validadores, mappers.
- **Scoped:** uma instância por escopo (por requisição HTTP). Casos reais: `DbContext`, unit of work, contexto do usuário logado.
- **Singleton:** uma instância na vida da aplicação. Casos reais: cache em memória, `HttpClient` via factory, configuração, clients de mensageria.
- Thread-safety: Singleton precisa ser seguro para concorrência.
- `IDisposable` e o container: quem descarta o quê; criar manualmente com `new` x resolver.

### Dependência cativa (Captive Dependency)
- Scoped (ou Transient) injetado em Singleton: a instância fica "presa" pela vida da aplicação.
- Efeitos: `DbContext` compartilhado entre requisições (não é thread-safe, dados obsoletos, vazamento de memória pelo change tracker), usuário errado em contexto.
- Como detectar: `ValidateScopes` e `ValidateOnBuild` no desenvolvimento.
- Soluções: `IServiceScopeFactory` para criar escopo dentro do Singleton, `IDbContextFactory`, repensar o ciclo de vida.
- `BackgroundService` (Singleton) que precisa de serviços Scoped.

### Outros pontos de entrevista
- Registro por interface vs classe concreta; múltiplas implementações (`IEnumerable<T>`).
- Service Locator como anti-pattern (`IServiceProvider` injetado).
- Injeção por construtor vs propriedade; construtor com excesso de dependências como sinal de violação do SRP.
- `HttpClient`: `new` por requisição (esgota sockets) vs `IHttpClientFactory`.

## Sinais de resposta ⭐ (nível Sênior)
- Cita o **efeito concreto** (dados misturados entre usuários, exceção de concorrência, memória crescendo).
- Conhece `ValidateScopes` e a solução com `IServiceScopeFactory`.
- Sabe escolher o ciclo de vida com base em estado e thread-safety.
