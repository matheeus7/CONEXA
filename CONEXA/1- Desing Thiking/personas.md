# Personas

Quatro personas, escolhidas para cobrir diferentes combinações de uso individual vs.
compartilhado e diferentes tipos de área da vida predominante.

---

## Persona 1 — Beatriz, a estudante que também trabalha

- **Idade:** 21 anos
- **Ocupação:** Estudante de Engenharia (noturno) e estagiária durante o dia
- **Contexto:** Divide o tempo entre aulas, um estágio remunerado e um projeto de TCC em grupo.
  Mora com os pais.
- **Objetivos:** Não perder prazos de entrega da faculdade nem do estágio; saber, numa
  semana de provas, se está assumindo tarefas demais do projeto de TCC em relação aos colegas.
- **Dores:** Usa o Google Agenda para o estágio, um grupo de WhatsApp para o TCC e post-its para
  a faculdade. Já perdeu um prazo de entrega porque a data estava só na conversa do grupo.
- **Necessidades:** Um lugar único para ver prazos de faculdade, estágio e TCC lado a lado; saber
  quando está sobrecarregada antes da semana de provas chegar.
- **Comportamento:** Usa o celular a maior parte do tempo; abre o app várias vezes ao dia entre
  aulas.
- **Como o CONEXA ajuda:** Cria as áreas "Faculdade", "Estágio" e "Projeto TCC". Conecta os
  colegas do TCC apenas à área "Projeto TCC" — eles não veem o estágio nem a faculdade dela. O
  Radar avisa quando várias entregas de áreas diferentes caem na mesma semana.

---

## Persona 2 — Rafael, o profissional autônomo com múltiplos projetos

- **Idade:** 34 anos
- **Ocupação:** Designer freelancer
- **Contexto:** Atende 3 a 5 clientes ao mesmo tempo, cada um com prazos e reuniões próprias.
  Também cuida de tarefas administrativas do próprio negócio (emissão de notas, cobrança).
- **Objetivos:** Não aceitar mais trabalho do que consegue entregar; saber, ao fechar um novo
  contrato, se tem capacidade real na semana pretendida.
- **Dores:** Hoje usa uma ferramenta de projetos por cliente (cada cliente tem seu próprio
  Trello/Notion) e nenhuma dá uma visão agregada de tudo o que ele tem em aberto.
- **Necessidades:** Ver a carga total somando todos os clientes, não projeto por projeto; separar
  claramente o que é de cada cliente para não misturar informações confidenciais.
- **Comportamento:** Trabalha no computador a maior parte do dia; checa o resumo do dia pela
  manhã.
- **Como o CONEXA ajuda:** Cada cliente vira uma área ("Projeto Cliente A", "Projeto Cliente B").
  As áreas não se comunicam entre si para os clientes (cada um só vê o que é seu, se for
  conectado), mas o Radar de Rafael enxerga a carga somada de todas.

---

## Persona 3 — Ana e João, o casal que divide a casa

- **Idade:** 29 e 31 anos
- **Ocupação:** Ana é enfermeira (plantões); João trabalha em horário comercial fixo
- **Contexto:** Moram juntos há 2 anos. Dividem contas, compras e tarefas domésticas, mas nunca
  formalizaram "quem faz o quê" — combinam de boca e esquecem.
- **Objetivos:** Ter uma lista visível de tarefas de casa com responsável definido; evitar que a
  mesma pessoa acumule tarefas de casa toda semana sem perceber.
- **Dores:** Discussões recorrentes sobre "eu sempre que faço X" sem dado nenhum para confirmar
  ou refutar isso.
- **Necessidades:** Compartilhar só a área "Casa" (não querem misturar com o trabalho um do
  outro); ver, ao final da semana, quantas tarefas cada um assumiu.
- **Comportamento:** Ambos usam celular; checam o app à noite para organizar o dia seguinte.
- **Como o CONEXA ajuda:** Criam a área "Casa" compartilhada entre os dois. Cada tarefa doméstica
  tem um responsável definido. No Pós-MVP, o Radar Compartilhado mostrará a carga de cada um
  dentro dessa área (ver [`alteracoes.md`](./alteracoes.md#alteração-3--radar-compartilhado-e-sugestões-de-redistribuição-movidos-para-pós-mvp)).

---

## Persona 4 — Carla, a pessoa com rotina fragmentada em projetos pessoais

- **Idade:** 42 anos
- **Ocupação:** Gerente de projetos em uma empresa de médio porte, com projetos pessoais paralelos
  (reforma da casa, curso de idiomas, cuidado de um familiar idoso)
- **Contexto:** No trabalho já usa uma ferramenta corporativa de projetos; o problema dela é tudo
  o que fica *fora* do trabalho.
- **Objetivos:** Ter clareza sobre os compromissos pessoais que competem pelo mesmo tempo livre
  que o trabalho já consome.
- **Dores:** Sabe organizar projetos profissionalmente, mas sua vida pessoal fica em anotações
  soltas porque não vale a pena abrir uma ferramenta corporativa para isso.
- **Necessidades:** Uma ferramenta leve, pessoal, que separe claramente vida pessoal de trabalho
  (o trabalho continua na ferramenta da empresa), mas que uma responsabilidade específica (ex.:
  cuidar do pai) possa ser compartilhada com um irmão.
- **Comportamento:** Baixa tolerância a ferramentas complexas; quer abrir, ver o essencial e
  fechar.
- **Como o CONEXA ajuda:** Usa o CONEXA só para a vida pessoal (não tenta substituir a ferramenta
  do trabalho). Cria a área "Cuidado do pai" e conecta o irmão só a essa área, mantendo reforma da
  casa e curso de idiomas privados.

---

## Como as personas influenciam decisões de produto

| Decisão de produto | Persona que mais justifica |
|---|---|
| Solo-first (funciona sem conectar ninguém) | Carla, Rafael |
| Conexão restrita a uma área específica | Beatriz (TCC), Ana/João (Casa), Carla (Cuidado do pai) |
| Radar individual no MVP | Rafael (carga somada de clientes), Beatriz (semana de provas) |
| Radar compartilhado no Pós-MVP | Ana e João |
| Responsável por tarefa (mesmo em áreas privadas) | Beatriz, Rafael |

