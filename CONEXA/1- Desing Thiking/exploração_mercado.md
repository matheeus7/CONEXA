# Exploração de Mercado e Análise de Soluções Existentes

## Objetivo desta análise

Esta seção não é uma pesquisa comercial extensa. O objetivo é responder a uma pergunta
específica: **se já existem sistemas que fazem algo parecido com o CONEXA, por que o CONEXA
deveria existir?** Para isso, foram selecionadas seis soluções que, juntas, cobrem as categorias
mais próximas do problema do CONEXA: apps de tarefas pessoais, ferramentas de organização
flexível, gestão visual de projetos, calendário compartilhado, visualização de carga de trabalho
em equipes, e organização familiar compartilhada. Todas as informações abaixo vêm de páginas
oficiais dos produtos ou de documentação de suporte oficial, com a fonte registrada em cada
seção; nenhuma característica foi assumida sem confirmação.

---

## 1. Todoist

**Propósito principal:** gerenciador de tarefas pessoal com recursos de colaboração em projetos
compartilhados.

**Público-alvo:** indivíduos e pequenas equipes que precisam organizar tarefas e prazos.

**Como organiza tarefas:** projetos (que podem ter sub-projetos), rótulos (labels) para
categorizar por contexto, filtros customizados, prioridades P1–P4 e datas em linguagem natural.

**Como trabalha com outras pessoas:** um projeto pode ser compartilhado com colaboradores, que
recebem convite por e-mail; tarefas dentro de um projeto compartilhado podem ser atribuídas a um
colaborador específico, mas **apenas uma pessoa por tarefa** pode ser designada como
responsável.
Fonte: o Todoist permite compartilhar projetos com convidados, atribuir uma tarefa a um colaborador específico usando "+nome", e cada tarefa só pode ter uma única pessoa atribuída
(todoist.com/help, geekflare.com).

**Como trata privacidade/compartilhamento:** o compartilhamento é feito por projeto inteiro, não
por sub-recorte dentro do projeto — quem é convidado a um projeto vê todas as tarefas daquele
projeto. Convidados ("guests") têm acesso limitado apenas aos projetos específicos para os quais foram convidados, mas dentro de um projeto compartilhado não há como restringir a visibilidade de tarefas específicas por pessoa.

**Automação/inteligência:** reconhecimento de linguagem natural em datas, filtros combináveis e
um sistema de gamificação (Karma) por produtividade — não há um índice único de carga de
trabalho.

**Limitações relacionadas ao problema do CONEXA:** o Todoist organiza tarefas por projeto, não
por "área da vida" com um conceito de privacidade diferenciada entre áreas dentro da mesma conta;
não existe distinção entre "criador da tarefa" e "responsabilidade contínua" além do campo de
atribuição de uma única pessoa; não há um indicador agregado de sobrecarga somando várias áreas
da vida do usuário.

**Fontes:** todoist.com/help/articles/todoist-glossary; geekflare.com/software/todoist-review;
everhour.com/blog/todoist-for-project-management.

---

## 2. Notion

**Propósito principal:** ferramenta flexível de páginas e bancos de dados, usada tanto para notas
pessoais quanto para gestão de projetos em equipe.

**Público-alvo:** indivíduos organizando informação pessoal e equipes organizando documentação e
processos de trabalho.

**Como organiza tarefas:** através de bancos de dados customizáveis (páginas com propriedades,
visualizações em lista, quadro, calendário); não existe um conceito nativo de "tarefa" ou
"responsabilidade" — tudo é modelado manualmente pelo usuário.

**Como trabalha com outras pessoas:** compartilhamento por página, com cinco níveis de permissão
(Acesso completo, Pode editar, Pode editar conteúdo, Pode comentar, Pode visualizar).
Fonte: o Notion oferece diferentes níveis de permissão por página, incluindo acesso completo, edição, edição de conteúdo, comentário e visualização, permitindo controle granular sobre o que cada pessoa compartilhada pode fazer (notion.com/help/sharing-and-permissions).

**Como trata privacidade/compartilhamento:** por padrão, o workspace pessoal é privado;
ao adicionar o primeiro convidado a uma página, o Notion passa a separar automaticamente as páginas em duas categorias na barra lateral: Compartilhadas e Privadas (matthiasfrank.de). Isso é conceitualmente parecido com a ideia de "área privada por padrão" do CONEXA, mas aplicado a páginas individuais, não a um agrupamento fixo de "áreas da vida".

**Automação/inteligência:** possui um assistente de IA (Notion AI) para resumir e gerar conteúdo,
mas não há um indicador nativo de carga de responsabilidades.

**Limitações relacionadas ao problema do CONEXA:** por ser uma ferramenta de propósito geral, o
Notion não vem com o conceito de "área da vida" pronto — o usuário precisaria construir do zero
uma estrutura equivalente às áreas do CONEXA, incluindo suas próprias regras de privacidade por
página. Não existe um cálculo de carga de responsabilidades nativo; qualquer coisa do tipo
precisaria ser construída manualmente pelo usuário com fórmulas de banco de dados.

**Fontes:** notion.com/help/sharing-and-permissions; matthiasfrank.de/how-to-share-notion-pages-complete-guide.

---

## 3. Trello

**Propósito principal:** gestão visual de projetos e tarefas em quadros (boards) no estilo Kanban.

**Público-alvo:** equipes de trabalho e, secundariamente, uso pessoal para organizar projetos.

**Como organiza tarefas:** quadros contendo listas e cartões; cada cartão pode ter responsável,
prazo, checklist e etiquetas.

**Como trabalha com outras pessoas:** cada quadro tem uma visibilidade própria — Privado, Visível
ao Workspace, Visível à Organização (Enterprise) ou Público.
Fonte: quadros privados são visíveis apenas aos seus membros (e administradores do Workspace em planos pagos), enquanto quadros visíveis ao Workspace ficam visíveis e editáveis por todos os membros do Workspace por padrão (support.atlassian.com/trello).

**Como trata privacidade/compartilhamento:** a unidade de compartilhamento é o quadro inteiro — não existe
um nível intermediário nativo que compartilhe "parte de um quadro" com uma pessoa e outra parte
com outra. Dentro de um quadro, existem membros normais (que podem editar sem restrição) e observadores com acesso somente leitura, disponíveis apenas em planos Premium (help.trello.com).

**Automação/inteligência:** possui automação de regras (Butler) para mover cartões e disparar
ações, mas não há indicador de carga de responsabilidades por pessoa.

**Limitações relacionadas ao problema do CONEXA:** assim como no Todoist, o Trello compartilha
"o quadro inteiro" como unidade — não há uma forma nativa de dizer "esta pessoa só vê a lista de
tarefas da faculdade, não o quadro inteiro da minha vida". Também não existe separação entre
"tarefa" e "responsabilidade recorrente", nem cálculo de sobrecarga.

**Fontes:** support.atlassian.com/trello/docs/changing-the-visibility-of-a-board;
help.trello.com/article/791-changing-permissions-on-a-board.

---

## 4. Google Calendar

**Propósito principal:** calendário pessoal e compartilhado para eventos e compromissos.

**Público-alvo:** uso pessoal, familiar e corporativo.

**Como organiza tarefas:** eventos com data/horário; possui também uma lista de tarefas simples
integrada (Google Tasks), mas sem conceito de área ou responsabilidade.

**Como trabalha com outras pessoas:** um usuário pode compartilhar calendários inteiros ou
específicos, com quatro níveis de permissão.
Fonte: os níveis de permissão vão desde "ver apenas ocupado/livre" (sem detalhes), passando por "ver todos os detalhes do evento", até "fazer alterações nos eventos" e "fazer alterações e gerenciar compartilhamento" (calendly.com/blog).

**Como trata privacidade/compartilhamento:** o padrão de privacidade no Google Calendar é, na
prática, por calendário — muitas pessoas usam um único calendário para tudo, misturando
trabalho e vida pessoal, e o nível "ver apenas ocupado/livre" é o mais usado quando se quer
compartilhar disponibilidade sem revelar conteúdo. Isso é parecido com o princípio "tudo começa
privado" do CONEXA, mas o Google Calendar não organiza nativamente "áreas da vida" — cada área
exigiria que o usuário criasse manualmente um calendário separado e gerenciasse o
compartilhamento de cada um individualmente.

**Automação/inteligência:** sugestão de horários para reuniões e detecção de conflito de
horário dentro do próprio calendário — este último é uma funcionalidade que o CONEXA também
pretende ter (RF06/RF11), mostrando que a detecção de conflito de horário já é uma expectativa
comum de mercado, não um diferencial isolado.

**Limitações relacionadas ao problema do CONEXA:** é um calendário, não um gerenciador de
responsabilidades — não há conceito de "quem é responsável por uma atividade recorrente", nem
um índice agregado de carga somando tarefas e compromissos de múltiplas áreas.

**Fontes:** support.google.com/calendar/answer/37082; calendly.com/blog/how-to-share-your-google-calendar.

---

## 5. ClickUp (Workload View)

**Propósito principal:** plataforma de gestão de projetos e trabalho para equipes, com uma
funcionalidade específica de visualização de carga de trabalho.

**Público-alvo:** equipes e gestores de projeto que precisam balancear a alocação de tarefas
entre pessoas.

**Como organiza tarefas:** tarefas dentro de projetos/listas, com estimativas de tempo,
responsável e datas.

**Como trabalha com outras pessoas e trata carga:** a Workload View é o recurso mais próximo do
conceito de Radar do CONEXA encontrado nesta pesquisa.
Fonte: a Workload View do ClickUp funciona como um mapa em tempo real de quem está com a capacidade comprometida, quem está em risco de sobrecarga e onde há tarefas não atribuídas, usando cores (verde, amarelo, vermelho) para indicar se uma pessoa está abaixo da capacidade, perto do limite ou sobrecarregada (clickup.com/blog).
Depois de agrupar a visualização por responsável, é possível definir limites de capacidade por pessoa, e o ClickUp aplica esses limites de forma consistente em toda a visualização.

**Como trata privacidade/compartilhamento:** é uma ferramenta de equipe — a Workload View
pressupõe que todos os membros do time já compartilham o mesmo espaço de trabalho; não há um
conceito de "conexão seletiva por área da vida pessoal".

**Automação/inteligência:** é explicitamente baseada em regras determinísticas (capacidade
definida manualmente vs. horas alocadas), não em IA — reforça que um indicador de carga não
precisa depender de inteligência artificial para ser útil.

**Limitações relacionadas ao problema do CONEXA:** a Workload View resolve exatamente o problema
de "quem está sobrecarregado", mas apenas **dentro de um contexto de equipe de trabalho já
compartilhado**, exigindo licença paga (Pro) e pressupondo que todos já têm acesso à mesma área
de trabalho. Não existe uma versão pessoal (para a vida fora do trabalho) nem uma versão que
funcione antes de haver qualquer compartilhamento.

**Fontes:** clickup.com/blog/clickup-workload-views-team-capacity; clickup.com/blog/smart-workload-balancing-tools.

---

## 6. Cozi Family Organizer

**Propósito principal:** organização compartilhada da rotina familiar (agenda, compras, tarefas
domésticas, receitas).

**Público-alvo:** famílias, especialmente com filhos.

**Como organiza tarefas:** calendário familiar colorido por membro, listas de compras e listas de
tarefas/afazeres domésticos (inclusive checklists de tarefas para crianças).

**Como trabalha com outras pessoas:** o modelo de compartilhamento do Cozi é o oposto do modelo
do CONEXA.
Fonte: toda a família compartilha uma única conta, à qual cada membro acessa usando seu próprio e-mail, mas todos enxergam as mesmas informações, sem importar como ou de onde cada um acessa (apple.co/3ou3QT3).

**Como trata privacidade/compartilhamento:** **não existe compartilhamento seletivo por área** —
é uma conta única e compartilhada por padrão para toda a família. Não há equivalente ao conceito
de "Finanças → Privado" do CONEXA dentro da mesma conta familiar.

**Automação/inteligência:** envio de e-mails automáticos de agenda diária/semanal; não há
indicador de carga nem detecção de sobrecarga por pessoa.

**Limitações relacionadas ao problema do CONEXA:** o Cozi é o exemplo mais próximo do caso de uso
"Casa"/família do CONEXA, mas resolve o compartilhamento assumindo que a família inteira vê tudo.
Ele não atende ao caso da persona Carla, que precisa compartilhar só uma responsabilidade
específica (cuidado do pai) com um irmão sem expor o resto da vida pessoal — o modelo de conta
única do Cozi não permite esse recorte.

**Fontes:** apps.apple.com/app/id407108860; apple.co/3ou3QT3 (App Store); cozi.com/features.

---

## Síntese da exploração de mercado

| Achado | Implicação para o CONEXA |
|---|---|
| Todoist e Trello compartilham por "unidade inteira" (projeto/quadro), não por recorte seletivo dentro dela | Confirma que "conectar uma pessoa a **apenas uma área específica**, sem ver as demais" não é o padrão de mercado em apps de tarefas — é um ponto de diferenciação real |
| Notion tem permissão granular por página, mas exige que o usuário construa a estrutura de "áreas da vida" do zero | O CONEXA entrega essa estrutura pronta (áreas predefinidas + privacidade por padrão), reduzindo esforço de configuração |
| Google Calendar já tem 4 níveis de permissão e detecção de conflito de horário | Confirma que "níveis de permissão" e "detecção de conflito" são funcionalidades esperadas do mercado, não diferenciais — o CONEXA deve implementá-las bem, não se vender por tê-las |
| ClickUp Workload View prova que um indicador de carga determinístico (sem IA) é viável e valioso — mas só existe para equipes de trabalho já compartilhadas | Valida a viabilidade técnica do Radar como regra determinística; mostra que o diferencial do CONEXA é levar esse conceito para a vida pessoal e para relações não-corporativas (casal, família, estudo) |
| Cozi resolve o compartilhamento familiar com conta única, sem privacidade seletiva dentro da família | É o caso mais próximo do "Casa" do CONEXA e confirma que nenhuma solução popular de organização familiar oferece privacidade seletiva por área dentro do mesmo grupo — reforça diretamente o diferencial do CONEXA |

Nenhuma das seis soluções combina, ao mesmo tempo: (a) organização por áreas privadas da vida
pessoal, (b) conexão seletiva por área/pessoa, e (c) um indicador de carga agregando tarefas e
compromissos de todas as áreas. É essa lacuna que sustenta a proposta de diferenciação do
CONEXA.
