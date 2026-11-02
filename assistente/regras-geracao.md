# Regras de geração de perguntas

Parte das [regras do assistente](regras-do-assistente.md). Abrir **ao gerar** enunciados e gabaritos (qualquer comando de treino). Numeração das seções = a das regras principais.

## 9. Perguntas: qualidade e cobertura

### 9.0 Qualidade na construção
Escrever certo de primeira: o checklist 9.1 é a especificação e a ficha garante isso antes da primeira linha. Depois de gravar, só a auditoria leve (item 5).

1. **Sortear** os tópicos e **consultar o índice** de cenários (seção 7) antes de pensar em enunciados.
2. **Ficha de cada pergunta** (uma linha, decidida antes de escrever; fonte do enunciado **e** do gabarito):
   - **Etiqueta · tipo · nível** (rótulo conforme o que se pede, item 11);
   - **Cenário** comum de entrevista, fora do índice (itens 4, 15, 17);
   - **Resposta única esperada**, já conhecida (saída exata do código, defeito único, consulta, veredito); havendo várias correções válidas, **todas** (item 16). Em código, saída ou defeito é **resolvido na ficha**, não conferido depois;
   - **"Responda:"**: no máximo dois grupos de entrega (item 5), verbos de ação, sem citar resultado nem técnica (itens 6 e 9);
   - **Premissas** a declarar (itens 7 e 12).
3. **Enunciado final direto da ficha**, na ordem do item 2 e com código mínimo (item 8); sem rascunhar duas vezes nem reescrever depois.
4. **Gabarito da mesma ficha**, na mesma rodada; cada parte dele (exceto *Extra ⭐*) corresponde ao que o "Responda:" pede.
5. **Auditoria leve**, uma passada depois de gravar; por pergunta, confirmar só: (a) "Responda:" com no máximo dois pedidos; (b) nenhuma expressão proibida do item 6; (c) enunciado leva a uma única resposta e não a revela; (d) gabarito com a mesma quantidade de perguntas, cobrindo só o pedido. Corrigir só o que falhar.
6. Pergunta **contestada**: aplicar o checklist inteiro (item 18).

O objetivo é **simular testes admissionais reais**: enunciados claros, objetivos e sem subjetividade.

### 9.1 Checklist de redação
1. **Autocontido:** o cenário se entende sem conhecer nada fora do texto; sem jargão sem contexto (ex.: "entrega pelo menos uma vez" sem explicar o efeito).
2. **Ordem fixa:** (a) contexto técnico em 1 a 3 frases; (b) cenário ou código; (c) situação-problema objetiva; (d) "Responda:".
3. **Tecnologia só quando necessária:** não introduzir ferramenta, framework ou produto (RabbitMQ, Redis, Kafka...) que o `meus-estudos/perfil.md` não diga que o usuário domina; preferir o conceito genérico ("fila de mensagens", "cache") e a stack do perfil.
4. **Cenário de uso amplo:** APIs e padrões que um profissional do nível-alvo encontra na maioria dos projetos da stack (framework, camada de dados, linguagem). APIs de nicho só em ⭐; se o conceito é geral mas a API é de nicho, reescrever com API comum.
5. **Uma ideia por pergunta:** no máximo **dois grupos** de pedido no "Responda:", relacionados: (a) *diagnóstico* (problema, causa, sintoma, risco, veredito e justificativa = um só); (b) *solução* (correção, consulta, algoritmo, reescrita); (c) *medida* (complexidade, número aproximado, custo). "Informe também..." e "aproximadamente quantas...?" abrem grupo novo. Com três, remover um ou mover para o gabarito como extra ⭐.
6. **Pedido inequívoco:** dizer exatamente o que entregar (resultado, causa, correção, consulta, veredito, complexidade) com verbos de ação; sem "fale sobre" ou "comente"; evitar palavras vagas ("construção", "mecanismo") havendo termo direto ("tipo", "técnica", "abordagem"). **Proibido, sem critério declarado:** "mais eficiente", "melhor", "mais adequado", "evitar isso", "em silêncio", "de forma correta"; trocar pelo que se quer obter ("qual algoritmo...", "que mudança faria o sistema detectar...") e dizer **onde** a correção atua quando importar (código, banco, configuração).
7. **Sem ambiguidade:** uma única interpretação razoável; declarar premissas (ex.: "a tabela não tem índices").
8. **Código realista e mínimo:** compilável, nomes de domínio coerentes, sem trecho que não influencie a resposta. Indicar se o código **não compila** ou se o erro é de **comportamento**.
9. **Sem entregar a resposta:** vale também para o "Responda:": pede o que entregar, sem citar o resultado esperado (ex.: "corrija para imprimir `012`", "limite a 20 chamadas" quando o número é a resposta) nem o nome da técnica de correção; descrever o **comportamento desejado** sem o valor final. Teste: se a resposta aparece no enunciado, reescrever.
10. **Escrever como candidato:** vale 6 e 9.
11. **Rótulo do tipo** ("Ache o erro", "Arquitetura", "SQL"...) corresponde ao que a pergunta pede.
12. **Estado e premissas explícitos:** de onde vêm os dados e o que cada ator tinha no momento do problema (ex.: "o DTO chega com os valores que a tela mostrava quando B a abriu"); fato não visível no código é declarado. **Dado que causa o problema** (valores, entradas, configuração) aparece no código ou é dito como fato do cenário, nunca só em prosa (ex.: "o pedido tem itens de preço 0.10 e 0.20" sem mostrar a criação).
13. **Conformidade durante a escrita** (pela ficha, não por revisão): os pontos (a) a (d) do item 5 de 9.0, mais 15, 16 e 17.
15. **Teste do entrevistador real:** "um entrevistador de verdade faria esta pergunta, neste formato, a um candidato deste nível?". Cenário que só existe para justificar a pergunta (ex.: "alguém altera o arquivo de configuração com a API rodando") ou recurso de nicho → trocar por tema clássico de entrevista. Cenário com cara de gambiarra é reprovado.
16. **Solução com uma única resposta:** se o "Responda:" pede correção e há várias válidas, (a) restringir no texto ("mantendo o uso de `lock`", "sem mudar a assinatura"), (b) pedir "uma correção" e listar **todas** as aceitas no gabarito, ou (c) trocar o tema. Vale para "o que é impresso?" (saída única) e para pedidos em aberto ("aponte o principal problema", "o que há de errado?") com mais de um defeito legítimo (ex.: responsabilidade no controller, falta de validação, entidade exposta): delimitar o eixo ("considerando apenas a segurança", "o risco de desempenho").
17. **Tema por ferramenta (ORM, biblioteca, recurso específico):** o domínio do perfil (ex.: Entity Framework) só entra no nível-alvo com cenários comuns do dia a dia (N+1, `ToList` precoce, rastreamento em leitura). Comportamentos finos (explosão cartesiana de `Include`, `IOptionsMonitor`, `AsSplitQuery`) **não** viram pergunta, nem ⭐. O ⭐ aprofunda tema geral (concorrência, assíncrono, arquitetura), não recurso de nicho.
18. **Pergunta contestada** (enunciado confuso, denso ou mal escrito): presumir que o usuário tem razão, sem defender o texto. Reescrever enunciado e gabarito, **desconsiderar a pergunta da nota** (placar e histórico "—", como na seção 1, regra 7), dizer qual item do checklist falhou e **verificar as outras perguntas da sessão** contra 5, 6, 13, 15, 16 e 17. Se o motivo for novo, acrescentar a lição aqui como item.
19. **Relações que decidem a resposta ficam no código:** quem depende de quem (construtores e injeção de dependência, chaves e relacionamentos, quem chama quem) é mostrado em código, nunca resumido em prosa ("os serviços recebem X e Y" não basta: mostrar cada construtor). Vale para a ficha e para a conferência do item 5 de 9.0, junto com o item 12.
20. **Hipótese que muda o código ("e se X fosse retirado/trocado?"):** só vale se o código mostrado **contém** X naquele ponto. Antes de enviar, ler o trecho e confirmar que a condição da hipótese ainda não é verdadeira nele; se já for (ex.: perguntar "se o `await` saísse do `lock`" com o `await` já fora), reescrever o código ou a pergunta. Vale também para a pergunta de fixação do `/ensina`. Para cada item "(a)/(b)", resolver a resposta esperada na ficha, como em "Em código, saída ou defeito é resolvido na ficha" (item 2 de 9.0).

### 9.2 Regras de conteúdo
- **Um único erro plantado** em "ache o erro"; com mais de um defeito, dizer no enunciado ("há mais de um problema; aponte os que encontrar") e aceitar cada achado válido.
- Se o impacto em produção for exigido, escrever isso na pergunta.
- Usar as ementas da trilha: tópicos básicos e intermediários para o nível-alvo; itens profundos (concorrência avançada, trade-offs, cenários extremos) para ⭐.
- "O que é X?" só como porta de entrada para "por que, e o que acontece quando...?".
