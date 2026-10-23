# 02 — LINQ e Coleções

> **Ementa para o assistente gerar perguntas novas.** Nível: **Pleno/Sênior**.

## Tópicos

### Execução tardia (Deferred Execution)
- `Where`, `Select`, `OrderBy` só definem a consulta; executam na enumeração.
- Operadores que **materializam**: `ToList`, `ToArray`, `Count`, `First`, `Any`, `ToDictionary`.
- Perigos: enumerar a mesma consulta várias vezes (várias idas ao banco), capturar variável que muda antes de enumerar, retornar consulta com `using` já descartado.
- Pegadinha de ordem: modificar a coleção de origem durante a enumeração (`InvalidOperationException`).

### IEnumerable vs IQueryable
- `IEnumerable<T>`: filtro executa **em memória** (LINQ to Objects).
- `IQueryable<T>`: a expressão é traduzida para SQL e executa **no banco**.
- Erro clássico: chamar `.AsEnumerable()`/`.ToList()` antes do `Where` e trazer a tabela inteira.
- Métodos C# que o EF não traduz e a consequência (exceção ou avaliação no cliente).
- Repositório que devolve `IQueryable` vs `IEnumerable`: vazamento de abstração.

### Problema N+1 no Entity Framework
- Como ocorre (lazy loading, loop com acesso à navegação).
- Soluções: `Include`/`ThenInclude`, projeção com `Select` (traz só o necessário), `AsSplitQuery`.
- `Include` vs projeção: quando cada um é melhor; explosão cartesiana.
- `AsNoTracking` em leitura: impacto em memória e CPU.

### Coleções
- `List<T>`, `Dictionary<K,V>`, `HashSet<T>`, `Queue/Stack`, `ConcurrentDictionary`: custo de busca e inserção.
- `IEnumerable` vs `IReadOnlyList` vs `ICollection` como retorno/parâmetro.
- Contains em `List` (O(n)) vs `HashSet` (O(1)) em volume alto.

## Sinais de resposta ⭐ (nível Sênior)
- Fala em **quantas idas ao banco** e **quanto vem pela rede**, não só em "performance".
- Sabe onde a consulta executa (cliente vs banco) em cada trecho.
- Conhece o custo em memória do tracking e da materialização.
