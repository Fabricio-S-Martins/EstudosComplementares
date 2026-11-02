# 06 — Arquitetura e Decisões

> **Ementa para o assistente gerar perguntas novas.** Nível: **Pleno/Sênior**.  
> Aqui o foco é **decisão com trade-off**, não definição.

## Tópicos

### SOLID prático
Para cada princípio, o assistente mostra **código que o viola** e pede: qual princípio, qual o problema em produção e como refatorar.
- **S**RP: classe que valida, persiste e envia e-mail; mudança por vários motivos.
- **O**CP: cadeia de `if/switch` por tipo que cresce a cada requisito.
- **L**SP: subclasse que lança `NotSupportedException` ou fortalece pré-condições.
- **I**SP: interface "gorda" que obriga implementar métodos inúteis.
- **D**IP: `new` de dependência concreta dentro do serviço, impossível de testar.
- Cobrar o limite: quando aplicar SOLID vira superengenharia.

### Monólito Modular vs Microsserviços
- Quando **aprovar** microsserviços: times independentes, escala por parte, ciclos de deploy distintos, domínio bem delimitado.
- Quando **reprovar**: time pequeno, domínio ainda instável, sem maturidade em observabilidade/CI-CD.
- Custos ocultos: consistência distribuída, latência de rede, versionamento de contratos, debug, infraestrutura.
- Monólito modular: fronteiras por módulo, comunicação por contratos, caminho de evolução.
- "Monólito distribuído" como anti-pattern.

### Mensageria e desacoplamento assíncrono
- **Fila** (um consumidor processa cada mensagem) vs **tópico** (publicação para várias assinaturas).
- **DLQ** (dead-letter queue): mensagens venenosas, política de retry, reprocessamento.
- Entrega **at-least-once**: por que consumidores precisam ser **idempotentes**.
- Idempotência: chave de idempotência, deduplicação, **máquina de estados** (ignorar transição inválida/repetida).
- Outbox pattern em nível conceitual; ordenação de mensagens; consistência eventual.

### Outros temas de entrevista
- Camadas: Clean/Hexagonal vs N-camadas; quando é demais.
- CQRS em nível conceitual (sem exagero); DDD básico (agregado, entidade, objeto de valor).
- REST: idempotência de verbos, códigos de status, versionamento.

## Sinais de resposta ⭐ (nível Sênior)
- Responde com **"depende de..."** e logo diz do que depende.
- Nomeia o custo da escolha, não só o benefício.
- Em mensageria, fala de falha parcial, duplicidade e DLQ sem ser lembrado.
