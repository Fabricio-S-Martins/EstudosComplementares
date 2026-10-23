# 01 — Fundamentos de C#

> **Ementa para o assistente gerar perguntas novas.** Não é banco de perguntas.  
> Nível esperado: **Pleno/Sênior**. Cobrar sempre o "por quê" e o impacto em produção.

## Tópicos

### Tipos por valor vs por referência
- Stack vs Heap: o que realmente vai para onde (struct dentro de classe, variável local capturada por closure).
- `struct` vs `class` vs `record` vs `record struct`: igualdade, cópia, mutabilidade.
- Passagem de parâmetros: por valor, `ref`, `out`, `in`; passar uma referência **por valor**.
- Quando usar `struct` (pequena, imutável, ciclo de vida curto) e quando é um erro.

### Gerenciamento de memória
- Garbage Collector: gerações 0/1/2, LOH, custo de promover objetos, por que `GC.Collect()` é quase sempre erro.
- `IDisposable`, `using`, `using var`, `await using`, padrão Dispose e finalizador.
- Vazamento de memória em .NET: eventos não desassinados, cache estático, `HttpClient` mal usado.

### Strings
- Imutabilidade, interning, custo de concatenação em loop.
- `StringBuilder`: quando compensa e quando é exagero.
- Comparação de strings: cultura, `StringComparison`, `==` vs `Equals`.

### Boxing, Unboxing e modificadores
- Onde o boxing acontece sem você ver (interfaces, `object`, coleções não genéricas, interpolação).
- Impacto em GC e CPU.
- `public`, `private`, `protected`, `internal`, `protected internal`, `private protected`, `sealed`, `readonly`, `const`.

## Banco de pegadinhas clássicas
10 pegadinhas com gabarito: [assistente/pegadinhas-gabarito.md](../../assistente/pegadinhas-gabarito.md) (**uso do assistente**).

## Sinais de resposta ⭐ (nível Sênior) neste módulo
- Cita custo real (alocação, GC, cópia) e não só a definição.
- Distingue "onde o valor vive" de "se é tipo de valor".
- Sabe o caso em que a regra geral **não** vale.
