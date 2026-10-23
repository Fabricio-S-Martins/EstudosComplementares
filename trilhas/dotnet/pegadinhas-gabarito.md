# 01 — Pegadinhas Clássicas (GABARITO DO ASSISTENTE)

> ⚠️ **Uso exclusivo do assistente.** Não abra antes de responder.  
> O assistente gera as perguntas a partir destas pegadinhas **variando o cenário**, e só revela o gabarito depois da resposta.

---

## 1. Struct em coleção: modificar a cópia
**Armadilha:** `foreach (var p in listaDeStructs) p.X = 10;` ou `lista[0].X = 10;`
**Gabarito:** structs são copiadas ao serem lidas. No `foreach` a variável é readonly (não compila); com indexador de `List<T>` o retorno é uma cópia (erro de compilação CS1612). Mesmo quando compila (via variável local), a alteração afeta só a cópia.
**Impacto:** bug silencioso de estado não persistido; em hot paths, cópias extras de structs grandes.

## 2. String imutável: ignorar o retorno
**Armadilha:** `nome.ToUpper();` ou `texto.Replace("a", "b");` sem atribuir.
**Gabarito:** strings são imutáveis; todo método devolve uma **nova** string. O original não muda.
**Impacto:** lógica silenciosamente errada; concatenação em loop gera O(n²) de alocações, pressionando o GC (usar `StringBuilder`).

## 3. Boxing escondido em loop
**Armadilha:** `ArrayList` ou `List<object>` com `int`; ou `string.Format("{0}", valor)`; ou struct convertida para interface.
**Gabarito:** valor vira objeto no heap (boxing); cada acesso exige unboxing com checagem de tipo.
**Impacto:** alocações em massa → mais GC gen0, mais CPU. Usar genéricos (`List<int>`) e evitar `object` em hot paths.

## 4. `==` com tipo estático `object`
**Armadilha:** `object a = "oi"; object b = new string("oi".ToCharArray()); a == b`.
**Gabarito:** `==` é resolvido pelo **tipo estático**. Com `object`, compara **referência**, não conteúdo. Resulta em `false`, enquanto `a.Equals(b)` é `true`.
**Impacto:** comparações de chave/ID falham de forma intermitente (depende de interning).

## 5. Closure em `for` captura a variável
**Armadilha:** `for (int i = 0; i < 3; i++) acoes.Add(() => Console.Write(i));` e executa depois.
**Gabarito:** a lambda captura a **variável `i`**, não o valor. Ao executar, `i` já vale 3 → imprime `333`. No `foreach` (C# 5+) cada iteração tem variável própria, então não ocorre. Correção: copiar para uma variável local dentro do loop.
**Impacto:** bugs em `Task.Run`/callbacks no loop (todas as tasks processam o mesmo item).

## 6. `using` + execução tardia (yield/IEnumerable)
**Armadilha:** `using var ctx = new Ctx(); return ctx.Itens.Where(...);` (retorno `IEnumerable`/`IQueryable` sem materializar).
**Gabarito:** o `using` descarta o contexto ao sair do método; a consulta só executa quando enumerada, depois do `Dispose` → `ObjectDisposedException`.
**Impacto:** erro em produção só no caminho de enumeração; mistura de ciclo de vida com execução tardia. Materializar (`ToList`) dentro do escopo.

## 7. `record` e igualdade por valor
**Armadilha:** achar que `record` é imutável por padrão e que `==` compara referência.
**Gabarito:** `record` tem igualdade **por valor** gerada (compara propriedades). Com `{ get; set; }` ele continua **mutável**; só `init`/posicional garante imutabilidade rasa. Propriedades de referência dentro dele são comparadas pelo seu próprio `Equals`.
**Impacto:** mutar um record usado como chave de `Dictionary`/`HashSet` quebra a busca (hash muda).

## 8. `GC.Collect()` e finalizador como "limpeza"
**Armadilha:** "chamo `GC.Collect()` ou confio no finalizador para liberar a conexão/arquivo".
**Gabarito:** o GC é **não determinístico**; finalizador roda tarde e custa promoção de geração (objeto sobrevive ao menos um ciclo extra). Recursos não gerenciados exigem `IDisposable`/`using`, e `GC.SuppressFinalize` ao descartar.
**Impacto:** esgotamento de conexões/handles; pausas de GC mais longas.

## 9. `const` vs `static readonly`
**Armadilha:** mudar um `const` em uma biblioteca e achar que os consumidores recebem o novo valor sem recompilar.
**Gabarito:** `const` é **substituído em tempo de compilação** nos assemblies que o usam. `static readonly` é lido em tempo de execução.
**Impacto:** deploy parcial deixa serviços com valores antigos embutidos; use `static readonly` para valores que podem mudar entre versões.

## 10. Referência passada por valor
**Armadilha:** `void Trocar(Pessoa p) { p = new Pessoa("Ana"); }` e o chamador espera ver "Ana".
**Gabarito:** a **referência** é copiada. Mudar propriedades via `p` afeta o objeto original; **reatribuir** `p` só altera a cópia local. Para trocar o objeto do chamador é preciso `ref`.
**Impacto:** confusão entre "mutar o objeto" e "trocar a referência" gera bugs em métodos auxiliares e em factories.

---

## Como cobrar
- Sempre pedir: **resultado + por quê + impacto em produção**.
- Variar entidade e contexto (não repetir "Pessoa" e "lista de int").
- Cenário extremo sugerido: *"e se isso rodar 1 milhão de vezes por minuto?"*.
