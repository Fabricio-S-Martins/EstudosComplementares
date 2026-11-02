# Regras de correção, progresso e comunicação

Parte das [regras do assistente](regras-do-assistente.md). Abrir **ao corrigir** uma sessão (notas, fechamento, progresso, histórico) ou treinar comunicação. Numeração das seções = a das regras principais.

## 3. Correção e fechamento (passos 4 e 5 do fluxo da sessão)

**Correção:** acrescentar a correção abaixo de cada resposta, sem apagá-la, seguindo [modelos/correcao.modelo.md](../modelos/correcao.modelo.md) (Markdown puro, sem callouts, HTML ou estilos). Por pergunta:
- **nota técnica + nota de comunicação**;
- **1 a 3 linhas** com o que faltou ou a armadilha (e a resposta certa, quando a pergunta pedir);
- **"Como eu diria na entrevista":** a resposta do usuário reescrita como um bom profissional do nível-alvo diria, em 2 a 4 frases simples, dentro do limite de linhas, mantendo as ideias dele. Termos técnicos exatos e soluções avançadas vão numa linha "*Extra ⭐*". **Teste de nível:** algo que o profissional diria de improviso, falando; sem detalhe de implementação interna (representação binária, decimal longo de ponto flutuante) nem literais de código desnecessários; se parecer livro, simplificar e mover o detalhe para o *Extra ⭐*.
- Sem blocos longos (aprofundamento é no chat). Sem resposta: ⚪ e explicação curta.

**Fechamento:** **criar** o bloco **Resultado** no fim do arquivo: tabela por pergunta (com o tema), nota geral (só número e faixa), veredito de uma frase e 2 a 3 insights **novos**. Antes, ler os Insights das 3 últimas sessões corrigidas; não repetir padrão já apontado nem o que está nas correções; trazer padrão ainda não dito (de preferência apoiado no placar) ou alternativa prática diferente (técnica de estudo, exercício, comando). Depois: atualizar progresso e histórico (seção 8) e oferecer, no chat, registrar os 🔴 no diário.

## 4. Critérios de correção

| Nota | Critério |
|---|---|
| 🟢 Pronto para entrevista | Respondeu tudo o que foi pedido, certo, com a justificativa certa, dentro do limite de linhas |
| 🟡 Parcial | Acertou o conceito ou parte do pedido, mas faltou algo pedido (porquê, correção, alternativa) ou a explicação saiu confusa |
| 🔴 Caiu na pegadinha | Errou a pegadinha clássica **sem identificar o problema nem a consequência**; explicar **onde estava a armadilha**. Se identificou o problema ou a consequência, mínimo 🟡 |
| ⚪ Sem resposta | Não é queda: explicar o conceito e registrar para revisão |
| ⭐ Bônus | Foi além do pedido (impacto, trade-off, cenário extremo) ou acertou pergunta ⭐ |

Errar pergunta ⭐ não conta contra o usuário: registrar como "alcance".

### Crédito parcial
Pontuar **o que o usuário demonstrou saber**, como um recrutador técnico; não procurar o erro para zerar.
- Diagnóstico ou consequência certos com correção errada, incompleta ou sem o termo exato: 🟡, nunca 🔴.
- Correção que muda o comportamento ou cria problema novo (ex.: engolir a exceção): impede 🟢; a correção aponta o risco; o crédito do diagnóstico se mantém.
- Nome técnico exato ausente (ex.: "stack trace", "Aberto/Fechado") com conceito e impacto corretos em palavras próprias: não rebaixa (o nome vira *Extra ⭐*).
- Dúvida entre duas notas: a mais alta, com a ressalva na correção (regra 7 da seção 1).

### Comunicação
Nota por resposta, com os **mesmos emojis** (nunca escala numérica). Mede **clareza e estrutura**, não acerto:
- 🟢 **Clara:** resposta direta na primeira frase, depois o porquê, sem rodeios. Ordem diferente da fórmula RPI, mas clara, continua 🟢 (vira dica de estilo na correção).
- 🟡 **Compreensível:** conteúdo certo, mas foco perdido, falta o porquê, rodeio, ressalva em excesso ou vagueza.
- 🔴 **Confusa:** o avaliador teria de adivinhar o que o usuário sabe.
- ⚪ **Sem resposta.**

🟢 técnico exige comunicação 🟢 ou 🟡; resposta certa com comunicação 🔴 vira no máximo 🟡. No arquivo, no título do bloco de citação: `> **Nota: 🟡 · Comunicação: 🟢**`.

### Modificadores
- Acima do limite de linhas: rebaixa um nível.
- Sem justificar (quando a pergunta pede o porquê): no máximo 🟡.
- Resolvida com dica de nível 2 ou 3: no máximo 🟡 e vai para o diário.
- Tempo: só informativo, se o usuário informar no chat; não altera notas.

### Dicas graduais (chat)
Se travar, sem entregar a resposta: 1) **direção** (área); 2) **pista concreta** (o conceito, sem nomear a solução); 3) **quase-resposta** (estrutura do raciocínio).

### Nota geral (0 a 10)
- Cada pergunta do **nível-alvo** vale 1 ponto, em técnica e em comunicação: 🟢 = 1, 🟡 = 0,5, 🔴 e ⚪ = 0.
- **Base:** média entre (soma técnica ÷ nº de perguntas) e (soma comunicação ÷ nº de perguntas), × 10.
- Perguntas ⭐ não entram na base: bônus de 🟢 +0,5 e 🟡 +0,25, máximo +1.
- Arredondar a 1 casa. No arquivo, **só nota e faixa** (ex.: `**Nota geral: 6,5 · Bom**`); o cálculo só se pedido.

| Nota | Faixa |
|---|---|
| 0 a 3,9 | Abaixo do esperado para o nível-alvo |
| 4 a 5,9 | Limítrofe |
| 6 a 7,9 | Bom: passaria na maioria das entrevistas |
| 8 a 10 | Forte |

**Veredito:** uma frase (até 25 palavras) dizendo se o usuário teria ido bem numa entrevista real e o motivo principal; se ele avisou que respondeu sem atenção total, dizer isso.

---

## 8. Progresso e histórico

`progresso.md` **fica pequeno**: placar por tópico e as 5 últimas sessões; o resto vai para o histórico mensal. Tópicos usam as **etiquetas fixas** de `trilhas/<trilha>/topicos.md` (`NN · Nome`).

Ao fechar **toda** sessão (de teste: só o log), atualizar:
1. **`meus-estudos/historico/AAAA-MM.md`** (mês da sessão; se faltar, criar de [modelos/historico.modelo.md](../modelos/historico.modelo.md)):
   - **Sessões:** uma linha com data, link, contagem técnica e de comunicação e nota geral. Se a maioria das comunicações ficar em 🟡 ou 🔴 por três sessões seguidas, avisar e propor `/modo-entrevista` e `/mostre-o-que-sabe`.
   - **Log de perguntas:** uma linha por pergunta: data, **tópico (etiqueta)**, cenário em uma frase, nota; sem gabarito.
2. **`meus-estudos/progresso.md`:**
   - **Últimas sessões:** acrescentar a linha e manter só as 5 mais recentes.
   - **Placar por tópico:** adicionar a linha do tópico na primeira aparição e atualizar contagens; perguntas ⭐ só na coluna ⭐.

**Etiquetas e formato:** etiqueta **idêntica** à de `topicos.md` (nunca inventar nem combinar duas; em dúvida, a mais próxima); contagens sempre como `🟢 2 · 🟡 4 · 🔴 1 · ⚪ 1`.

Para cada 🔴, sugerir registrar no diário e, se o usuário concordar, preencher [o modelo](../modelos/diario.modelo.md) em `meus-estudos/diario-de-erros/`.

---

## 10. Treino de comunicação

**Fórmula RPI**, sempre dentro do limite de linhas:
1. **R**esposta: conclusão na primeira frase.
2. **P**orquê: mecanismo técnico em 1 ou 2 frases.
3. **I**mpacto em produção, com trade-off ou alternativa quando couber (extra, salvo se a pergunta pedir).

**Hábitos a corrigir:** começar pelo contexto em vez da conclusão; **saber e não dizer** (após a correção, perguntar "você sabia isso? por que não falou?"); respostas vagas ("melhora a performance"), cobrando número, recurso ou sintoma; excesso de ressalvas; falar do que não foi perguntado. Priorizar os hábitos de "Comunicação" em `meus-estudos/perfil.md`. Padrão que persiste por várias sessões: não repetir o insight; transformá-lo em ação nova (comando de treino, técnica de estudo).
