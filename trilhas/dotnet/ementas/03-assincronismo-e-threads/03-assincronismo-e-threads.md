# 03 — Assincronismo e Threads

> **Ementa para o assistente gerar perguntas novas.** Nível: **Pleno/Sênior**.

## Tópicos

### Como `async/await` funciona
- Máquina de estados gerada pelo compilador; `await` **libera a thread** enquanto a operação de I/O está pendente.
- `async` **não cria thread nova**: I/O assíncrono usa portas de conclusão do SO; `Task.Run` é que usa o ThreadPool.
- CPU-bound vs I/O-bound: quando `Task.Run` ajuda e quando só atrapalha (em ASP.NET).
- `ConfigureAwait(false)`: o que muda e quando importa (bibliotecas vs ASP.NET Core).
- `async void`: por que evitar (exceção não capturável, sem await).
- `ValueTask` vs `Task`.

### Os perigos de `.Result` e `.Wait()` (sync-over-async)
- **Deadlock** com `SynchronizationContext` (UI, ASP.NET clássico): a thread bloqueia esperando a continuação que precisa dela.
- **Esgotamento do ThreadPool** em ASP.NET Core: sem deadlock de contexto, mas threads bloqueadas aguardando I/O derrubam o throughput sob carga.
- `GetAwaiter().GetResult()` não resolve; só muda o tipo da exceção.
- Como migrar: async "até o topo" (controller/handler).

### `Task.WhenAll` e cancelamento
- `Task.WhenAll` vs `await` em sequência: paralelismo de operações independentes.
- Tratamento de exceções no `WhenAll` (só a primeira aparece no `await`).
- Limitar concorrência (`SemaphoreSlim`, `Parallel.ForEachAsync` com `MaxDegreeOfParallelism`).
- `CancellationToken`: propagar do endpoint até o banco/HTTP; cancelamento cooperativo; `OperationCanceledException`; timeout com `CancelAfter`.
- Fire-and-forget: riscos e alternativas (`BackgroundService`, fila).

### Concorrência básica
- Condições de corrida, `lock`, `Interlocked`, `ConcurrentDictionary`.
- Não usar `lock` com `await` dentro (usar `SemaphoreSlim`).

## Sinais de resposta ⭐ (nível Sênior)
- Diferencia **liberar thread** de **criar thread**.
- Explica o impacto do bloqueio em **throughput sob 100 mil requisições**, não só "dá deadlock".
- Menciona propagação do `CancellationToken` e limite de concorrência.
