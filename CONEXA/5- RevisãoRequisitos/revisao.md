# Revisão de Requisitos

Os 17 RF e 9 RNF estavam bem fundamentados, mas 14 problemas impediam implementar ou testar com
segurança. Todos foram corrigidos nos documentos. As decisões marcadas com **(D)** foram assumidas
por mim e precisam da sua confirmação.

## Problemas encontrados e correções

| # | Problema | Correção |
|---|---|---|
| 1 | O Radar somava "tarefas/eventos" com prioridade, mas Eventos não têm prioridade. | Eventos entram com prioridade Média **(D)**. |
| 2 | Não estava definido de quem são as tarefas do Índice de Carga (criadas por mim? em minhas Áreas? atribuídas a mim?). | Conta a Tarefa em que a Pessoa é **responsável**, em qualquer Área com acesso; tarefa delegada não entra **(D)**. Reforça o diferencial tarefa × responsabilidade. |
| 3 | A janela de 7 dias deixava de fora tarefas vencidas há mais tempo. | Entram atrasadas (qualquer data) + prazos nos próximos 7 dias. |
| 4 | RF11 não era testável sem o `fator_de_escala`. | Fator provisório 4, como configuração, com exemplo numérico verificável (20, 12, 32). |
| 5 | "Duração estimada" era citada como dado do Radar, mas Tarefas não têm duração e a fórmula não a usa. | Removida do escopo do Radar. |
| 6 | Status da Tarefa indefinido; "atrasada" ora status, ora condição. | `Pendente`/`Concluída`; atrasada é condição derivada. Prazo passou a ser obrigatório. |
| 7 | RF07 permitia atribuir a "qualquer Pessoa com acesso", inclusive Visualizador, que não pode editar. | Responsável = dono ou Colaborador **(D)**. |
| 8 | RF09 não dizia se Colaborador conclui/exclui; RF09 e US13 divergiam. | Matriz de permissões única; Colaborador cria, edita, conclui e exclui itens **(D)**; registra autoria. |
| 9 | RF08 não dizia como conectar, nem se havia aceite, nem onde a Pessoa conectada vê a Área. | Conexão por e-mail de Pessoa já cadastrada, sem aceite no MVP **(D)**; seção "Compartilhadas comigo"; casos de recusa. |
| 10 | RF10 não tratava tarefas atribuídas à Pessoa revogada; "imediatamente" não era testável. | Tarefas voltam ao dono **(D)**; critério: próxima requisição é negada (permissão checada a cada requisição). |
| 11 | RF12 e a arquitetura: o Pub/Sub reage a **mudanças**, mas "ficar atrasada" acontece pela passagem do tempo. | Alertas e Radar calculados na consulta (RF12). Ajuste sugerido em `1-padrao_arquitetura.md`: o evento de Tarefas invalida/atualiza, mas o atraso é avaliado na leitura. |
| 12 | RNF03 citava "API", que não existe no MVP (Thymeleaf no servidor). | Trocado por formulários e listagens. |
| 13 | RNF04, 05, 06, 07, 08 sem métrica ou com termos vagos ("carga normal", "versões atuais", "remover ou desassociar", "relativamente independentes"). | Métricas: 5 pessoas/4 concluem; p95 ≤ 2 s com 200 tarefas e 50 eventos; duas últimas versões estáveis; exclusão transacional; módulos só via porta. |
| 14 | RNF09 marcado Pós-MVP mas aplicado à Etapa 2; RF13 dizia ser "consequência de RF03". | RNF09 virou diretriz de arquitetura; origem do RF13 corrigida (RF03, RF11, RF12). |

Também foram corrigidos: RF01 sem regra de senha/e-mail; RF02 sem critério de logout; RF04 não
citava Conexões na exclusão; RF06 sem regra de eventos que se tocam; contagem errada no README
("17 RF e 9 RNF do MVP" → 13 RF + 4 Pós-MVP; 8 RNF + 1 diretriz).

## Alinhamento entre documentos

- **Histórias:** não havia história para editar tarefa nem para editar/excluir evento. US07 e US09
  foram ampliadas; US12 e US17 ajustadas ao RF08 e RF12.
- **Critérios de aceitação:** US06, US12, US13, US14, US15 e US17 atualizados.
- **Rastreabilidade:** RF01–RF03 e as edições/exclusões (RF04–RF06) não tinham linha. Duas linhas
  adicionadas, mais a nota de como cada RNF é verificado.
- **Backlog:** sem mudança de estrutura; os títulos de US07 e US09 podem ser ajustados.

## Decisões pendentes (D)

1. Eventos entram no Índice com prioridade Média.
2. O Índice conta só tarefas em que a Pessoa é responsável.
3. Colaborador pode concluir e excluir itens (e não só criar/editar).
4. Conexão sem etapa de aceite no MVP (e recusa de e-mail não cadastrado, o que revela que a
   conta existe; aceitável no MVP, a rever com o convite por e-mail do Pós-MVP).
5. Revogação devolve as tarefas ao dono.
6. `fator_de_escala` = 4 até a calibração da Etapa 4.

## Lacunas não incluídas (propostas, sem alterar o escopo)

- **Exclusão de conta e dados pessoais** (relevante para LGPD, e coerente com o princípio de
  privacidade). Sugestão: RF Pós-MVP.
- **Recuperação de senha.** Depende de e-mail, hoje fora do escopo; sugestão: Pós-MVP junto de RF17.
- **Acessibilidade básica**, **backup do banco** e **cobertura mínima de testes** como RNFs.
- **Critérios de aceitação de RF14–RF17**, a escrever quando entrarem em Sprint.
