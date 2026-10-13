# Padrões Arquiteturais

## Visão Geral do CONEXA

O CONEXA é um sistema voltado para a organização pessoal e a gestão de responsabilidades do
cotidiano. Suas principais funcionalidades são:

* Organização da vida do usuário em áreas privadas (Minha Vida);
* Criação de tarefas e eventos com responsável, prazo e prioridade;
* Conexão seletiva de outras pessoas a áreas específicas, com controle de permissão;
* Cálculo de um Índice de Carga (Radar) e alertas sobre tarefas atrasadas e conflitos de horário.

## Arquitetura Recomendada

A escolha abaixo parte de três restrições já fixadas na Etapa 1, não de preferência: o
isolamento entre Áreas (RNF03), a exigência de que os componentes sejam testáveis e mantidos de
forma independente (RNF06), e a regra de que o Radar **consome**, mas não **possui**, os dados de
Tarefas e Eventos. A arquitetura ideal para o CONEXA combina:

* **Arquitetura em Camadas com Portas e Adaptadores (Hexagonal)**: separa Apresentação,
  Aplicação e Persistência, e dentro da Aplicação cada componente (Áreas, Tarefas, Eventos,
  Conexões, Radar) expõe uma porta pública e esconde sua implementação interna. É o que
  transforma "o Radar consome, não possui" em uma restrição estrutural verificável no código, em
  vez de uma convenção que depende de disciplina da equipe;
* **MVC (Model-View-Controller)**: estrutura a camada de apresentação web, já que o protótipo do
  MVP prevê várias telas (Login, Dashboard, Minha Vida, Área, Tarefa, Calendário, Conexões,
  Radar) com fluxos de navegação e validação de entrada próprios de cada uma;
* **Observer / Pub-Sub interno, não distribuído**: desacopla o disparo de alertas (RF12) e o
  recálculo do Radar das mudanças em Tarefas e Eventos — quando uma tarefa é criada, editada ou
  fica atrasada, isso é publicado como evento interno, e Radar e Notificações reagem como
  assinantes, sem que Tarefas precise conhecê-los. Fica deliberadamente como um mecanismo interno
  ao mesmo processo, não como uma arquitetura orientada a eventos distribuída — isso seria
  desproporcional para o MVP, mas já prepara o terreno para o Radar Compartilhado no Pós-MVP.

## Exemplo Visual

```text
        ┌────────────────────────────┐
        │    APRESENTAÇÃO (MVC)      │
        │   View ←→ Controller       │
        └──────────────┬─────────────┘
                        │ chama as portas abaixo
        ┌───────────────▼────────────┐
        │  APLICAÇÃO (Hexagonal)     │
        │  cada componente = porta   │
        │  + núcleo privado          │
        │  Áreas · Tarefas · Eventos │
        │  Conexões · Radar          │
        └──────┬───────────────┬─────┘
               │ publica       │ assina
        ┌──────▼───────────────▼─────┐
        │   OBSERVER / PUB-SUB       │
        │   (interno, mesmo processo)│
        │  Tarefa criada/atrasada →  │
        │  Radar recalcula,          │
        │  Notificações gera alerta  │
        └──────────────┬──────────────┘
                        │
        ┌───────────────▼────────────┐
        │       PERSISTÊNCIA         │
        └─────────────────────────────┘
```

## Conclusão

A arquitetura proposta para o CONEXA é organizada, modular e justificada por requisitos
concretos da Etapa 1, não por preferência estética. A combinação de Camadas com Portas e
Adaptadores, MVC e Observer/Pub-Sub interno garante isolamento entre os componentes, mantém o
Radar como consumidor — nunca dono — dos dados de Tarefas e Eventos, estrutura a apresentação web
do MVP, e permite que evoluções já previstas (Radar Compartilhado, entidade Responsabilidade,
mais níveis de permissão) entrem como novos assinantes de eventos ou novas implementações por
trás de uma porta existente, sem exigir retrabalho nos componentes já construídos.
