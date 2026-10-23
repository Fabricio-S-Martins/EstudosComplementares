# 07 — Encontre o Erro

> **Ementa para o assistente gerar trechos novos.** Nível: **Pleno/Sênior**.  
> Formato: bloco de ~5 linhas de C# ou SQL com **um** erro oculto. O usuário aponta o erro e a **consequência em produção** em até 2 minutos.

## Catálogo de erros (para variar a origem)

### C#
- **Falta de `await`:** tarefa "esquecida", exceção engolida, resultado usado antes de concluir; `async void`.
- **Vazamento de conexão/recurso:** `SqlConnection`/`StreamReader` sem `using`; `HttpClient` criado por requisição.
- **Referência nula:** `FirstOrDefault()` sem checagem; encadeamento sem `?.`; `Nullable` ignorado.
- **`throw ex;`** em vez de `throw;` (perde o stack trace).
- **Closure em loop** capturando a variável.
- **Execução tardia** retornada após descartar o contexto.
- **`.Result`/`.Wait()`** em endpoint.
- **`DateTime.Now`** em vez de UTC; comparação de datas com fuso.
- **Exceção engolida:** `catch { }`.
- **Concorrência:** campo estático mutável sem sincronização; `Dictionary` em múltiplas threads.
- **N+1** escondido em loop com acesso à navegação.
- **Dependência cativa:** `DbContext` em Singleton.

### SQL
- **SQL injection:** concatenação de string em comando; solução com parâmetros.
- **`SELECT *`** em tabela larga; impacto em I/O e em índices cobrindo.
- **`NOT IN` com `NULL`:** resultado vazio inesperado.
- **Função na coluna do `WHERE`:** índice ignorado.
- **`LEFT JOIN` + filtro no `WHERE`:** vira inner join.
- **`UPDATE`/`DELETE` sem `WHERE`.**
- **Transação sem `COMMIT`/`ROLLBACK` em caminho de erro:** lock preso.
- **Paginação sem `ORDER BY` determinístico.**
- **`COUNT(coluna)` vs `COUNT(*)`** com NULL.

## Regras de geração
- Um único erro "principal" por bloco; sem poluir com outros problemas.
- O código deve **parecer plausível** (como em produção), não didático demais.
- Pedir sempre: **qual é o erro, qual o sintoma em produção, como corrigir**.
- Variar entidades (pedido, cliente, fatura, entrega…) e o contexto (API, job, consumidor de fila).
