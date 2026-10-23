# Estudos Complementares — Laboratório de Treino de Backend .NET

Treino diário para entrevistas e testes técnicos de **Backend .NET**, no nível que você escolher (**Júnior, Pleno ou Sênior**). Um assistente de IA (o [Claude Code](https://claude.com/claude-code)) atua como **avaliador**: faz perguntas, corrige com tom acolhedor e **nunca entrega a resposta de início**.

O foco é **responder sob pressão, explicar o porquê e mostrar com clareza o que você já sabe**. A nota de comunicação pesa tanto quanto o acerto técnico.

---

## Como começar

1. Instale o [Claude Code](https://claude.com/claude-code) e clone este repositório.
2. Abra o Claude Code **nesta pasta**. O [CLAUDE.md](CLAUDE.md) carrega as [regras](assistente/regras-do-assistente.md).
3. Peça um treino escrevendo o comando dentro de uma frase, por exemplo: "vamos fazer uma /sessao". Se a mensagem começar com `/`, o Claude Code pode tratá-la como um comando próprio e dar erro.
4. **Na primeira vez**, o assistente faz uma entrevista curta (nível-alvo, tecnologias que você domina, pontos fracos, dificuldades de comunicação) e cria o seu perfil em `meus-estudos/perfil.md`. Sem ele, nenhuma sessão é gerada.
5. O assistente cria `meus-estudos/sessoes/NN-sessao.md`. **Responda dentro do arquivo**, respeitando o limite de linhas, e peça "corrija a sessão NN". A correção, a nota geral e os insights entram no mesmo arquivo.
6. Registre os 🔴 no diário ([modelo](modelos/diario.modelo.md)).

> **Seus dados ficam só na sua máquina.** Tudo o que é pessoal (perfil, progresso, sessões, gabaritos e diário) vive em `meus-estudos/`, que está no `.gitignore`. O repositório traz apenas os modelos.

> **Aviso:** [assistente/pegadinhas-gabarito.md](assistente/pegadinhas-gabarito.md) é material **do assistente** e contém as respostas das pegadinhas. Para treinar de verdade, não abra esse arquivo.

---

## Comandos

| Comando | O que faz | Duração |
|---|---|---|
| `/sessao` | **Treino diário:** 10 perguntas sortidas de módulos variados | ~20 min |
| `/rapido` | 3 perguntas sortidas, para dias corridos | ~5 min |
| `/treino [tema]` | 2 perguntas de um tema ou módulo | ~5 min |
| `/ache-o-erro` | Um bloco de código com um erro oculto | 2 min |
| `/logica` | Desafio rápido de sequência ou raciocínio | 2–3 min |
| `/simulado-20min` | 6 a 8 questões densas e variadas | 20 min |
| `/modo-entrevista` | Perguntas orais, sem código | 10 min |
| `/mostre-o-que-sabe` | Perguntas abertas ("fale da sua experiência com X") | 10 min |
| `/revisao-semanal` | Refaz os temas errados da semana | 15 min |
| `/ensina [tema]` | Explica um conceito novo, sem nota | livre |

O sorteio é **ponderado pelos seus erros** (veja as [regras](assistente/regras-do-assistente.md)).

---

## Como a nota funciona

| Marca | Significado |
|---|---|
| 🟢 | Respondeu o que foi pedido, certo e com a justificativa certa |
| 🟡 | Parcial: faltou algo que a pergunta pedia ou a explicação saiu confusa |
| 🔴 | Caiu na pegadinha, sem identificar o problema |
| ⚪ | Sem resposta |
| ⭐ | Pergunta de um nível acima do seu: errar não conta contra você; acertar dá bônus |

Cada resposta recebe também uma **nota de comunicação** (mesmos emojis). No fim da sessão vêm a **nota geral de 0 a 10**, um veredito e alguns insights. A régua muda conforme o nível-alvo do seu perfil.

**Fórmula RPI para responder:** **R**esposta na primeira frase, **P**orquê (o mecanismo) e **I**mpacto em produção, quando couber.

---

## Estrutura

| Pasta | Conteúdo |
|---|---|
| [conteudo/01-fundamentos-csharp/](conteudo/01-fundamentos-csharp/LEIAME.md) | Valor vs referência, memória e GC, strings, boxing |
| [conteudo/02-linq-e-colecoes/](conteudo/02-linq-e-colecoes/LEIAME.md) | Execução tardia, IEnumerable vs IQueryable, N+1 |
| [conteudo/03-assincronismo-e-threads/](conteudo/03-assincronismo-e-threads/LEIAME.md) | async/await, deadlocks, ThreadPool, cancelamento |
| [conteudo/04-injecao-de-dependencia/](conteudo/04-injecao-de-dependencia/LEIAME.md) | Ciclos de vida, dependência cativa |
| [conteudo/05-banco-de-dados-e-sql/](conteudo/05-banco-de-dados-e-sql/LEIAME.md) | Joins, ACID, índices, plano de execução, paginação |
| [conteudo/06-arquitetura-e-decisoes/](conteudo/06-arquitetura-e-decisoes/LEIAME.md) | SOLID, monólito vs microsserviços, mensageria |
| [conteudo/07-encontre-o-erro/](conteudo/07-encontre-o-erro/LEIAME.md) | Erros comuns de produção em C# e SQL |
| [conteudo/08-logica-e-algoritmos/](conteudo/08-logica-e-algoritmos/LEIAME.md) | Sequências, arrays, raciocínio rápido |
| [conteudo/09-aspnet-testes-e-resiliencia/](conteudo/09-aspnet-testes-e-resiliencia/LEIAME.md) | Pipeline, segurança, testes, cache, resiliência |
| [assistente/](assistente/regras-do-assistente.md) | Regras de como a IA se comporta e as pegadinhas (material do assistente) |
| [modelos/](modelos/) | Modelos de perfil, progresso, histórico, sessão e diário |
| `meus-estudos/` | **Local, fora do git:** perfil, progresso, histórico, sessões, gabaritos e diário |

As pastas de `conteudo/` são **ementas**, não bancos de perguntas: o assistente gera perguntas novas a cada sessão.

---

## Rotina sugerida

| Frequência | O quê |
|---|---|
| Diário | 1 `/sessao` (ou `/rapido` nos dias corridos) |
| 3x por semana | `/ache-o-erro` e `/logica` de aquecimento |
| Semanal | `/revisao-semanal` |
| Quinzenal | `/simulado-20min` |

---

## Regras de ouro

1. **Responda antes de abrir qualquer gabarito.**
2. **Explique o porquê**, não só a opção certa.
3. **Respeite o limite de linhas.** Síntese faz parte do treino.
4. **Erro sem revisão é só frustração:** leve os 🔴 para o diário.

---

## Licença

[MIT](LICENSE).
