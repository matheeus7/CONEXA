# Casos de Teste

Casos de teste derivados dos critérios de aceitação dos requisitos do MVP (RF01–RF13 e
RNF01–RNF08). Cada caso é rastreável ao requisito que verifica.

**Legenda — Tipo:** `Aut` = automatizado (JUnit/Mockito ou teste de integração) · `Man` = manual.
**Prioridade:** A = alta, M = média, B = baixa.

**Dados de apoio usados nos casos:**
- Ana (dona), Bruno (Colaborador), Carla (Visualizadora), Davi (sem conexão), todos cadastrados.
- Ana possui as Áreas "Faculdade" (compartilhada) e "Casa" (privada).
- "Agora" = momento da execução; prazos são relativos a ele.

---

## RF01 — Cadastro de usuário

| ID | Cenário | Passos | Resultado esperado | Tipo | Pri. |
|---|---|---|---|---|---|
| CT-001 | Cadastro válido | Informar nome, e-mail novo e senha de 8+ caracteres e confirmar | Conta criada, Pessoa autenticada e levada ao Dashboard | Aut | A |
| CT-002 | E-mail duplicado | Cadastrar com e-mail já existente | Cadastro recusado; mensagem "e-mail já em uso"; nenhuma conta nova | Aut | A |
| CT-003 | Senha curta | Cadastrar com senha de 7 caracteres | Recusado; regra de senha exibida | Aut | A |
| CT-004 | E-mail inválido | Cadastrar com "ana@" | Recusado; erro de formato | Aut | M |
| CT-005 | Campos vazios | Enviar o formulário em branco | Recusado; erros por campo | Aut | M |

## RF02 — Autenticação

| ID | Cenário | Passos | Resultado esperado | Tipo | Pri. |
|---|---|---|---|---|---|
| CT-006 | Login correto | Entrar com e-mail e senha corretos | Redirecionado ao Dashboard | Aut | A |
| CT-007 | Senha errada | Entrar com senha incorreta | Acesso recusado; mensagem genérica | Aut | A |
| CT-008 | E-mail inexistente | Entrar com e-mail não cadastrado | Mesma mensagem genérica do CT-007 (não revela qual campo errou) | Aut | A |
| CT-009 | Logout | Fazer logout e abrir uma URL interna | Redirecionado ao login | Aut | A |
| CT-010 | Acesso sem login | Abrir URL interna sem sessão | Redirecionado ao login | Aut | A |

## RF03 — Minha Vida

| ID | Cenário | Passos | Resultado esperado | Tipo | Pri. |
|---|---|---|---|---|---|
| CT-011 | Minha Vida criada no cadastro | Cadastrar nova Pessoa e abrir Minha Vida | Espaço existe, sem Áreas | Aut | A |

## RF04 — Áreas

| ID | Cenário | Passos | Resultado esperado | Tipo | Pri. |
|---|---|---|---|---|---|
| CT-012 | Criar Área | Ana cria a Área "Casa" | Área associada à sua Minha Vida, sem Conexões | Aut | A |
| CT-013 | Editar Área | Ana renomeia "Casa" | Novo nome persistido | Aut | M |
| CT-014 | Excluir Área vazia | Ana exclui uma Área sem itens | Área removida | Aut | M |
| CT-015 | Excluir Área com itens | Ana exclui "Faculdade" (com tarefas, eventos e conexões) | Pede confirmação listando o que será removido; ao confirmar, tudo é removido | Aut | A |
| CT-016 | Cancelar exclusão | Cancelar na confirmação do CT-015 | Nada é removido | Man | M |
| CT-017 | Colaborador não edita Área | Bruno tenta renomear ou excluir "Faculdade" | Ação recusada | Aut | A |

## RF05 — Tarefas

| ID | Cenário | Passos | Resultado esperado | Tipo | Pri. |
|---|---|---|---|---|---|
| CT-018 | Criar tarefa sem responsável | Ana cria tarefa com título, prazo e prioridade | Status `Pendente`; responsável = Ana | Aut | A |
| CT-019 | Prazo obrigatório | Criar tarefa sem prazo | Recusado | Aut | A |
| CT-020 | Editar tarefa | Alterar título, prazo e prioridade | Alterações persistidas | Aut | M |
| CT-021 | Concluir tarefa | Marcar como concluída | Status `Concluída`; sai de atrasos, alertas e Índice | Aut | A |
| CT-022 | Excluir tarefa | Excluir tarefa | Tarefa removida | Aut | M |
| CT-023 | Tarefa atrasada | Tarefa `Pendente` com prazo de ontem | Aparece como atrasada na lista, no Dashboard e no Radar | Aut | A |
| CT-024 | Concluída não é atrasada | Tarefa com prazo de ontem, `Concluída` | Não aparece como atrasada | Aut | A |
| CT-025 | Tarefa em Área sem acesso | Davi tenta criar tarefa em "Casa" | Acesso negado | Aut | A |

## RF06 — Eventos

| ID | Cenário | Passos | Resultado esperado | Tipo | Pri. |
|---|---|---|---|---|---|
| CT-026 | Criar evento | Criar evento com título, data, hora, duração e Área | Evento criado e visível no calendário | Aut | A |
| CT-027 | Área obrigatória | Criar evento sem Área | Recusado | Aut | M |
| CT-028 | Editar e excluir evento | Alterar e depois excluir | Persistido e removido | Aut | M |
| CT-029 | Conflito de horário | Eventos 10:00–11:00 e 10:30–11:30 | Ambos sinalizados como conflito | Aut | A |
| CT-030 | Conflito entre Áreas | Mesmos horários do CT-029 em Áreas diferentes da Ana | Ambos sinalizados | Aut | A |
| CT-031 | Eventos que se tocam | Eventos 10:00–11:00 e 11:00–12:00 | Nenhum sinalizado | Aut | A |
| CT-032 | Visualização em calendário | Abrir o calendário no mês com eventos | Eventos exibidos nos dias corretos | Man | M |

## RF07 — Responsável por tarefa

| ID | Cenário | Passos | Resultado esperado | Tipo | Pri. |
|---|---|---|---|---|---|
| CT-033 | Atribuir a Colaborador | Em "Faculdade", Ana atribui tarefa ao Bruno | Responsável = Bruno | Aut | A |
| CT-034 | Visualizador não é opção | Abrir o seletor de responsável em "Faculdade" | Carla não aparece; Ana e Bruno aparecem | Aut | A |
| CT-035 | Atribuir a Visualizador por requisição direta | Enviar atribuição a Carla forçando o formulário | Recusado | Aut | A |
| CT-036 | Sem conexões | Em "Casa" (sem conexões) abrir o seletor | Apenas Ana | Aut | M |

## RF08 — Conexões

| ID | Cenário | Passos | Resultado esperado | Tipo | Pri. |
|---|---|---|---|---|---|
| CT-037 | Conectar Pessoa cadastrada | Ana conecta o e-mail do Bruno a "Faculdade" | Conexão ativa imediatamente | Aut | A |
| CT-038 | Isolamento da Área | Bruno acessa "Casa" por URL direta, busca e listagens | Acesso negado em todos os caminhos; "Casa" nunca aparece para ele | Aut | A |
| CT-039 | E-mail não cadastrado | Ana conecta "x@x.com" | Recusado; nenhuma Conexão criada | Aut | A |
| CT-040 | Auto-conexão | Ana conecta o próprio e-mail | Recusado | Aut | M |
| CT-041 | Conexão duplicada | Conectar o Bruno novamente à mesma Área | Recusado | Aut | M |
| CT-042 | Compartilhadas comigo | Bruno abre sua Minha Vida | "Faculdade" aparece em "Compartilhadas comigo" | Aut | A |
| CT-043 | Listar conexões | Ana abre as conexões de "Faculdade" | Lista Bruno e Carla com seus níveis | Aut | M |
| CT-044 | Não-dono não gerencia | Bruno tenta conectar ou revogar alguém | Recusado | Aut | A |

## RF09 — Permissões

| ID | Cenário | Passos | Resultado esperado | Tipo | Pri. |
|---|---|---|---|---|---|
| CT-045 | Visualizador não escreve | Carla tenta criar, editar, concluir e excluir tarefa e evento | Todas recusadas, com mensagem de falta de permissão | Aut | A |
| CT-046 | Visualizador lê | Carla abre Área, tarefas e eventos | Visualiza normalmente | Aut | A |
| CT-047 | Colaborador escreve | Bruno cria, edita, conclui e exclui tarefa e evento | Todas permitidas | Aut | A |
| CT-048 | Colaborador sem gestão | Bruno tenta excluir a Área ou gerenciar Conexões | Recusado | Aut | A |
| CT-049 | Autoria registrada | Bruno edita uma tarefa | Item registra Bruno e o horário da alteração | Aut | M |
| CT-050 | Mudança de nível | Ana muda Bruno para Visualizador; Bruno tenta editar | Recusado já na próxima requisição | Aut | A |

## RF10 — Revogação

| ID | Cenário | Passos | Resultado esperado | Tipo | Pri. |
|---|---|---|---|---|---|
| CT-051 | Revogar com sessão aberta | Bruno logado em "Faculdade"; Ana revoga; Bruno atualiza a página | Acesso negado | Aut | A |
| CT-052 | Tarefas voltam ao dono | Bruno era responsável por 2 tarefas; Ana revoga | As 2 tarefas passam a ter Ana como responsável | Aut | A |
| CT-053 | Some de "Compartilhadas comigo" | Após revogar, Bruno abre Minha Vida | Área não aparece | Aut | A |
| CT-054 | Reconectar | Ana reconecta o Bruno | Novo acesso concedido sem restaurar responsabilidades antigas | Aut | M |

## RF11 — Radar Individual

Fator de escala = 4.

| ID | Cenário | Dados | Resultado esperado | Tipo | Pri. |
|---|---|---|---|---|---|
| CT-055 | Sem itens | Nenhum item ativo | Índice 0 | Aut | A |
| CT-056 | Tarefa Alta atrasada | 1 tarefa Alta vencida (3+2=5) | Índice 20 | Aut | A |
| CT-057 | Tarefa Média em 1 dia | 1 tarefa Média com prazo amanhã (2+1=3) | Índice 12 | Aut | A |
| CT-058 | Soma | Dados dos CT-056 e CT-057 | Índice 32 | Aut | A |
| CT-059 | Teto | 10 tarefas Alta atrasadas (50 pontos) | Índice 100 (não passa de 100) | Aut | A |
| CT-060 | Prazo distante | Tarefa com prazo em 10 dias | Não entra no cálculo | Aut | A |
| CT-061 | Prazo em 3 a 7 dias | Tarefa Baixa com prazo em 5 dias (1+0) | Entra: Índice 4 | Aut | M |
| CT-062 | Tarefa concluída | Tarefa Alta atrasada, `Concluída` | Não entra | Aut | A |
| CT-063 | Tarefa delegada | Ana atribui tarefa ao Bruno | Não entra no Índice da Ana; entra no do Bruno | Aut | A |
| CT-064 | Evento | 1 evento nos próximos 2 dias (Média 2 + urgência 1) | Índice 12 | Aut | A |
| CT-065 | Evento passado ou fora da janela | Evento ontem e evento em 10 dias | Não entram | Aut | M |
| CT-066 | Conflito não altera o Índice | 2 eventos conflitantes versus os mesmos sem conflito | Índice idêntico; conflito aparece na lista | Aut | A |
| CT-067 | Listas auxiliares | Radar com tarefas atrasadas e eventos conflitantes | Exibe lista de atrasadas e lista de conflitos | Aut | A |
| CT-068 | Linguagem não clínica | Percorrer todas as telas e mensagens do Radar | Nenhum texto sugere avaliação médica, psicológica ou clínica | Man | A |
| CT-069 | Determinismo | Calcular duas vezes com os mesmos dados | Mesmo resultado | Aut | M |

## RF12 — Alertas internos

| ID | Cenário | Passos | Resultado esperado | Tipo | Pri. |
|---|---|---|---|---|---|
| CT-070 | Prazo em menos de 24h | Tarefa `Pendente` com prazo daqui a 10 h | Aparece nos alertas do Dashboard | Aut | A |
| CT-071 | Prazo em mais de 24h | Prazo daqui a 30 h | Não aparece | Aut | A |
| CT-072 | Atrasada | Tarefa vencida e `Pendente` | Aparece como atrasada | Aut | A |
| CT-073 | Concluir remove | Concluir a tarefa do CT-070 | Alerta desaparece | Aut | A |
| CT-074 | Atraso por passagem do tempo | Tarefa com prazo daqui a 1 min; aguardar vencer e recarregar o Dashboard | Aparece como atrasada, sem nenhuma edição da tarefa | Aut | A |
| CT-075 | Outra Área | Tarefa de "Casa" com a Área "Faculdade" aberta | Alerta aparece mesmo assim | Man | M |
| CT-076 | Só tarefas minhas | Tarefa de Ana atribuída ao Bruno, vencendo em 5 h | Alerta aparece para o Bruno, não para a Ana | Aut | A |

## RF13 — Dashboard

| ID | Cenário | Passos | Resultado esperado | Tipo | Pri. |
|---|---|---|---|---|---|
| CT-077 | Resumo completo | Abrir o Dashboard com dados | Mostra Áreas, tarefas do dia, alertas e Índice | Man | A |
| CT-078 | Tarefa de hoje sem navegar | Tarefa com prazo hoje em "Faculdade" | Aparece no Dashboard | Aut | A |
| CT-079 | Estado vazio | Pessoa recém-cadastrada abre o Dashboard | Mensagem orientando a criar a primeira Área | Man | M |

---

## Requisitos não funcionais

| ID | Req. | Cenário | Procedimento | Resultado esperado | Tipo | Pri. |
|---|---|---|---|---|---|---|
| CT-080 | RNF01 | Privacidade por padrão | Davi tenta abrir cada Área, tarefa e evento da Ana por URL direta | Acesso negado em todos | Aut | A |
| CT-081 | RNF02 | Hash de senha | Consultar a tabela de usuários após cadastro | Nenhuma senha legível; hash adaptativo e salgado | Aut | A |
| CT-082 | RNF02 | HTTPS | Acessar a URL implantada por HTTP | Redirecionado para HTTPS | Man | A |
| CT-083 | RNF03 | Isolamento entre Áreas | Bruno (só "Faculdade") tenta "Casa" por URL, busca, formulário, Dashboard e Radar | Acesso negado; nenhum dado de "Casa" aparece em listagens ou no Radar | Aut | A |
| CT-084 | RNF04 | Usabilidade | 5 pessoas sem instrução criam uma Área e uma Tarefa com responsável e prazo | Ao menos 4 concluem ambas em até 3 passos cada | Man | A |
| CT-085 | RNF05 | Tempo de resposta | Carga de 200 tarefas ativas e 50 eventos; medir criação de tarefa, Dashboard e Radar | p95 ≤ 2 s em cada operação | Aut | M |
| CT-086 | RNF06 | Modularidade | Teste de dependências entre módulos | Módulos só se acessam por suas portas; nenhum acesso ao núcleo interno de outro módulo | Aut | A |
| CT-087 | RNF06 | Teste isolado | Testar o Radar substituindo Tarefas e Eventos por dublês | Testes passam sem banco nem outros módulos reais | Aut | M |
| CT-088 | RNF07 | Navegadores | Executar os fluxos principais nas duas últimas versões estáveis de Chrome, Firefox e Edge | Funcionamento idêntico, sem erros | Man | M |
| CT-089 | RNF08 | Exclusão consistente | Excluir "Faculdade" e consultar tarefas, eventos e conexões dela | Nenhum registro órfão | Aut | A |
| CT-090 | RNF08 | Atomicidade | Forçar falha durante a remoção da Área | Nada é removido (rollback completo) | Aut | A |

---

## Resumo de cobertura

| Requisito | Casos | Requisito | Casos |
|---|---|---|---|
| RF01 | CT-001 a 005 | RF10 | CT-051 a 054 |
| RF02 | CT-006 a 010 | RF11 | CT-055 a 069 |
| RF03 | CT-011 | RF12 | CT-070 a 076 |
| RF04 | CT-012 a 017 | RF13 | CT-077 a 079 |
| RF05 | CT-018 a 025 | RNF01 | CT-080 |
| RF06 | CT-026 a 032 | RNF02 | CT-081, 082 |
| RF07 | CT-033 a 036 | RNF03 | CT-083 |
| RF08 | CT-037 a 044 | RNF04 | CT-084 |
| RF09 | CT-045 a 050 | RNF05 | CT-085 |
| | | RNF06 | CT-086, 087 |
| | | RNF07 | CT-088 |
| | | RNF08 | CT-089, 090 |

Total: 90 casos (81 automatizáveis, 9 manuais). Os requisitos Pós-MVP (RF14–RF17) e a diretriz
RNF09 não têm casos de teste até serem priorizados.
