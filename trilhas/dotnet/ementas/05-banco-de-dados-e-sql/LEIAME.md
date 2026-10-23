# 05 — Banco de Dados e SQL (SQL Server / T-SQL)

> **Ementa para o assistente gerar perguntas novas.** Nível: **Pleno/Sênior**.

## Tópicos

### Consultas essenciais
- `INNER JOIN` vs `LEFT JOIN`; filtrar no `WHERE` vs no `ON` de um `LEFT JOIN` (pegadinha clássica que transforma em inner).
- `GROUP BY`, `HAVING` vs `WHERE`, funções agregadas (`COUNT(*)` vs `COUNT(coluna)`, comportamento com `NULL`).
- Subconsulta vs `JOIN` vs `EXISTS`; `NOT IN` com `NULL`.
- Funções de janela (`ROW_NUMBER`, `RANK`) em nível básico; encontrar duplicados; "top N por grupo".

### Propriedades ACID (na prática, com T-SQL)
- **Atomicidade:** `BEGIN TRAN`/`COMMIT`/`ROLLBACK`, `TRY/CATCH`, `SET XACT_ABORT ON`.
- **Consistência:** constraints, chaves estrangeiras.
- **Isolamento:** níveis (`READ COMMITTED`, `SNAPSHOT`, `SERIALIZABLE`), leitura suja, não repetível, fantasma; bloqueios e deadlocks de banco.
- **Durabilidade:** log de transações.
- Transação longa: impacto em locks e no log.

### Índices
- **Clustered:** define a ordem física; um por tabela; geralmente a PK.
- **Non-Clustered:** estrutura separada apontando para a chave; vários por tabela.
- **Key Lookup** e como `INCLUDE` cria um índice cobrindo e elimina o lookup.
- Ordem das colunas na chave do índice; seletividade; custo em escrita (INSERT/UPDATE mais lento).
- Funções sobre coluna no `WHERE` (`WHERE YEAR(data) = 2026`) tornam o predicado não-sargável.

### Plano de execução
- **Table/Clustered Index Scan** vs **Index Seek**: o que cada um indica.
- Quando Scan é aceitável (tabela pequena, retorno de grande parte das linhas).
- Operadores a observar: Key Lookup, Sort, Hash Match, estimativa de linhas vs real.
- Parameter sniffing em nível básico.

### Paginação
- `OFFSET ... FETCH NEXT` exige `ORDER BY` determinístico.
- Custo do OFFSET alto (descarta linhas lidas); alternativa com **keyset pagination** (`WHERE Id > @ultimoId`).
- Paginação no EF (`Skip/Take`) e o SQL gerado.

## Sinais de resposta ⭐ (nível Sênior)
- Liga o conceito ao **plano de execução** e ao **custo de I/O**.
- Fala em locks, tamanho da transação e nível de isolamento.
- Propõe a alternativa (keyset, índice cobrindo) com o trade-off de escrita.
