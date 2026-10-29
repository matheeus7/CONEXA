# Rastreabilidade

Este documento conecta cada necessidade identificada até o critério de aceitação que a
verifica, permitindo auditar por que cada requisito existe e o que prova que ele foi atendido.

| Problema | Necessidade | Objetivo | Requisito | História | Critério (resumo) |
|---|---|---|---|---|---|
| Fragmentação de contexto entre ferramentas | Ver tudo em um só lugar, por área | Obj. 1 | RF04 | US04 | Área criada e associada à Minha Vida, privada por padrão |
| Ausência de noção de responsável distinto do criador | Saber quem responde por cada tarefa | Obj. 2 | RF05, RF07 | US06 | Tarefa registrada com responsável (padrão: o criador) |
| Necessidade de identificar o dono de cada vida e proteger o acesso | Ter conta própria e entrar com segurança | Obj. 1, 6 | RF01, RF02, RF03 | US01, US02, US03 | Conta criada com Minha Vida vazia; login recusa credenciais incorretas; senha nunca em texto puro |
| Dificuldade de manter a organização atualizada | Editar e excluir áreas, tarefas e eventos | Obj. 1 | RF04, RF05, RF06 | US05, US07, US09, US10 | Exclusão de área remove itens e conexões com confirmação; tarefa concluída sai de atrasos e alertas; eventos visíveis em calendário |
| Compartilhamento por unidade inteira (confirmado em Todoist/Trello/Cozi) | Compartilhar só uma área específica | Obj. 3 | RF08 | US12 | Pessoa conectada (por e-mail, já cadastrada) só vê a área compartilhada, em "Compartilhadas comigo" |
| Compartilhamento sem controle do que a outra pessoa pode fazer | Definir o que cada pessoa pode fazer na área | Obj. 3 | RF09 | US13 | Visualizador não edita; Colaborador edita |
| Falta de forma de revogar compartilhamento | Retomar controle sobre uma área compartilhada | Obj. 6 | RF10 | US14 | Acesso negado na próxima requisição após revogação; tarefas do revogado voltam ao dono |
| Ausência de indicador de sobrecarga para uso pessoal (confirmado: só existe para equipes, ex. ClickUp) | Perceber excesso de responsabilidades antes de atrasar | Obj. 4 | RF11 | US15 | Índice de Carga (0–100, fórmula determinística) calculado, sem linguagem clínica |
| Percepção tardia de atraso | Ver rapidamente o que já está atrasado | Obj. 4, 5 | RF05, RF11 | US08 | Tarefa vencida e não concluída aparece como atrasada |
| Compromissos sobrepostos não percebidos a tempo | Ser avisado de conflitos de horário | Obj. 5 | RF06, RF11 | US11 | Eventos sobrepostos sinalizados no calendário |
| Necessidade de visão geral rápida da rotina | Ver panorama sem navegar por várias telas | Obj. 1, 4 | RF13 | US16 | Dashboard mostra áreas, tarefas do dia e Índice de Carga |
| Necessidade de perceber prazos próximos a tempo de agir | Ser avisado antes do vencimento | Obj. 4 | RF12 | US17 | Alerta interno para tarefas do usuário atrasadas ou a menos de 24h do prazo |
| Necessidade de isolamento real entre áreas privadas e compartilhadas | Garantir que dados não vazem entre áreas | Obj. 6 | RNF01, RNF03 | US12, US14 | Testes de acesso negado a áreas não conectadas |

Os requisitos não funcionais são verificados pelos testes descritos em cada um (RNF01 e RNF03:
acesso negado; RNF02: inspeção do banco e HTTPS; RNF04: teste de usabilidade; RNF05: medição de
tempo; RNF06: dependências entre módulos; RNF07: navegadores; RNF08: exclusão transacional).
Os requisitos Pós-MVP (RF14–RF17) e as histórias US18–US21 não entram nesta tabela até serem
priorizados.

Os objetivos (Obj. 1 a 7) referenciados nesta tabela estão definidos no documento de objetivos
do produto.

## Como usar esta tabela nas próximas etapas

- Para **Issues** (Etapa 2 em diante): cada linha desta tabela pode virar uma Epic ou Issue,
  usando o ID do requisito/história como referência cruzada no rastreador (ex.: GitHub Issues,
  Jira).
- Para **desenvolvimento baseado em componentes** (Etapa 2): os requisitos agrupados por
  história aqui já indicam quais dados um componente precisa expor a outro (ex.: o componente
  de Tarefas precisa expor "está atrasada?" para o componente de Radar consumir).
- Para **testes** (Etapa 6): os critérios de aceitação desta tabela e os critérios detalhados por
  história devem virar casos de teste automatizados ou roteiros de teste manual.
- Para o **MVP** (esta etapa): toda linha cujo requisito esteja marcado como MVP nos requisitos
  funcionais compõe o conjunto mínimo definido no escopo do MVP.
