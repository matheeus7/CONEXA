# Design Thinking


## 1. Empatia

Situação realista (Beatriz, estudante-trabalhadora):

Beatriz tem prova de Cálculo na quinta-feira, uma entrega de relatório no estágio na
sexta-feira e uma reunião do grupo de TCC na quarta à noite. Cada um desses compromissos está
em um lugar diferente: a prova está anotada no caderno, a entrega do estágio está no Google
Agenda do trabalho, e a reunião do TCC foi combinada em um áudio de WhatsApp que ela não
consegue mais encontrar no meio da conversa. Na terça-feira, ela percebe que vai ter que estudar
para a prova, terminar o relatório e se preparar para a reunião — tudo em dois dias — mas só
percebe isso tarde, porque nenhuma ferramenta somava esses três compromissos numa visão só.

Dificuldades observadas:

- Nenhuma ferramenta atual olha para a semana de Beatriz como um todo; cada uma só vê sua
  própria fatia (faculdade, estágio, grupo de WhatsApp).
- Ela só percebe a sobrecarga quando já é tarde para se reorganizar.
- Ela não tem como saber, olhando o grupo de TCC, se está fazendo mais tarefas do projeto que
  os colegas.

## 2. Definição

**Problema principal:** pessoas com múltiplas áreas de vida não conseguem ver, num único lugar,
o total de responsabilidades que carregam nem como essas responsabilidades se distribuem entre
si e outras pessoas.

**Problemas secundários:** fragmentação de contexto entre ferramentas; ausência de noção de
"responsável" distinta de "tarefa"; compartilhamento por unidade inteira em vez de seletivo por
área (confirmado na exploração de mercado); ausência de indicador de sobrecarga para uso
pessoal.

**Necessidades derivadas:**

1. Ver tarefas e compromissos de todas as áreas da vida em um só lugar.
2. Saber quem é responsável por cada tarefa, não só que ela existe.
3. Compartilhar apenas uma área específica com uma pessoa, sem expor o resto da vida.
4. Receber um aviso objetivo quando a carga de responsabilidades estiver alta.

## 3. Ideação

Foram levantadas doze ideias ao todo, cobrindo as quatro necessidades derivadas na etapa de
Definição. Nem toda ideia levantada em uma sessão de ideação vira funcionalidade: a tabela
abaixo registra também ideias levantadas apenas para explorar o espaço do problema, sem
compromisso de implementação, com o status real de cada uma — selecionada (presente no sistema
atual), não selecionada (avaliada e descartada, com motivo) ou em análise (não descartada, mas
sem decisão nem avaliação suficiente para entrar no MVP ou no Pós-MVP formal).

| # | Ideia | Necessidade relacionada | Status | Avaliação |
|---|---|---|---|---|
| 1 | Áreas da vida como espaço nativo (Minha Vida), cada uma com privacidade própria | Ver tudo em um só lugar | **Selecionada** | No sistema atual — resolve a fragmentação sem depender de integrações externas nem misturar contextos que deveriam ficar separados |
| 2 | Um único calendário/lista compartilhável por padrão para tudo | Ver tudo em um só lugar | **Não selecionada** | Mistura áreas que deveriam ter privacidade diferente (ex.: Finanças e Faculdade no mesmo lugar); o próprio Google Calendar evita isso separando calendários por assunto |
| 3 | Agregador que importa dados de outras ferramentas (Google Calendar, e-mail, etc.) | Ver tudo em um só lugar | **Em análise** | Depende de integrações externas complexas, fora do escopo acadêmico desta fase; não descartada em definitivo, pode voltar a ser avaliada se houver demanda real dos usuários testados |
| 4 | Campo "responsável" simples na Tarefa, distinto do criador | Saber quem responde por cada coisa | **Selecionada** | No sistema atual — prova o conceito central (tarefa ≠ responsabilidade) com o menor custo de implementação no MVP |
| 5 | Atribuição múltipla — várias pessoas responsáveis pela mesma tarefa | Saber quem responde por cada coisa | **Não selecionada** | Gera ambiguidade sobre quem deve agir; o próprio Todoist permite apenas uma pessoa por tarefa exatamente por esse motivo |
| 6 | Entidade "Responsabilidade" independente, com histórico e recorrência, desde o MVP | Saber quem responde por cada coisa | **Não selecionada** | Exigiria modelar sincronização entre Tarefa e Responsabilidade antes de validar o conceito básico; prevista para o Pós-MVP, não descartada de vez |
| 7 | Conectar uma pessoa a uma Área específica, com nível de permissão definido | Compartilhar seletivamente | **Selecionada** | No sistema atual — entrega granularidade sem exigir que o usuário monte a estrutura de áreas do zero |
| 8 | Compartilhar o projeto/quadro inteiro com a pessoa (modelo Todoist/Trello) | Compartilhar seletivamente | **Não selecionada** | É exatamente a lacuna de mercado identificada na exploração de mercado — expõe mais do que o necessário |
| 9 | Modo "compartilhado por padrão" para contas conjuntas (ex.: casais) | Compartilhar seletivamente | **Não selecionada** | Contraria diretamente o princípio "tudo começa privado"; rejeitada por coerência de produto, não por falta de demanda |
| 10 | Índice de Carga por regra determinística (prioridade, prazo, quantidade de itens ativos) | Indicador de sobrecarga | **Selecionada** | No sistema atual — é o Radar; viabilidade sem IA confirmada pela Workload View do ClickUp na exploração de mercado |
| 11 | IA generativa analisando a rotina e sugerindo reorganização | Indicador de sobrecarga | **Não selecionada** | Exige modelo de IA, dados de treinamento e infraestrutura fora do escopo acadêmico; registrada como ideia Futura |
| 12 | Autoavaliação subjetiva — perguntar ao usuário "como você está se sentindo em relação à sua carga?" | Indicador de sobrecarga | **Não selecionada** | Não é verificável nem consistente entre usuários, e corre risco de ser lida como avaliação de bem-estar, o que o produto explicitamente evita |

### Ideias adicionais levantadas fora das quatro necessidades centrais

Estas ideias surgiram na sessão de ideação por associação (ex.: "e se o Radar aparecesse também
fora do app?"), mas não decorrem diretamente de nenhuma das quatro necessidades derivadas na
Definição — por isso ficam registradas à parte, todas como **em análise** ou **não
selecionadas**, sem nenhuma marcada como selecionada:

| # | Ideia | Status | Avaliação |
|---|---|---|---|
| 13 | Templates de áreas prontas por persona (ex.: pacote "Estudante" com Faculdade/Estágio/TCC) | **Em análise** | Reduziria esforço de configuração inicial; não avaliada a fundo, poderia entrar no Pós-MVP se os testes de usabilidade mostrarem fricção no primeiro uso |
| 14 | Marcação automática de tarefas recorrentes (ex.: "toda segunda") | **Em análise** | Depende de uma decisão de modelagem (Tarefa recorrente vs. série de Tarefas) que pertence à Etapa 2, não a esta etapa de produto |
| 15 | Modo "foco do dia" (esconder tudo, mostrar só as tarefas de hoje) | **Em análise** | Hipótese de UX válida, mas não testada com as personas; não é requisito, é ideia de design a validar em prototipação futura |
| 16 | Chat/comentários dentro de uma Área compartilhada | **Não selecionada** | Aproximaria o CONEXA de uma ferramenta de mensagens (o próprio Todoist já tem algo assim); foge do problema central que o CONEXA se propõe a resolver |
| 17 | Gamificação leve (pontos por tarefa concluída, ao estilo "Karma" do Todoist) | **Não selecionada** | Não relacionada ao problema de gestão de responsabilidades; risco de distorcer o Índice de Carga em pontuação de produtividade |
| 18 | Widget de carga na tela de bloqueio do celular | **Não selecionada** | Depende de aplicativo mobile nativo, que está explicitamente Fora do Escopo desta fase |
| 19 | Delegação automática de tarefa via sugestão de IA | **Não selecionada** | Mesma razão do item 11 — depende de IA generativa, fora do escopo acadêmico do MVP |

### Síntese da Ideação

Das doze ideias ligadas diretamente às quatro necessidades centrais, quatro foram selecionadas e
já formam o núcleo do produto (Áreas, campo responsável, Conexão por Área, Radar por regra
determinística); as demais oito foram descartadas ou adiadas, cada uma com motivo registrado —
nenhuma foi rejeitada por preferência pessoal. Das sete ideias adicionais levantadas por
associação, nenhuma foi selecionada: três seguem em análise para possível entrada no Pós-MVP
(templates de área, recorrência de tarefas, modo foco do dia) e quatro foram descartadas por
fugirem do problema central ou dependerem de infraestrutura fora do escopo acadêmico (chat
interno, gamificação, app mobile, IA de delegação). As ideias em análise não têm compromisso de
entrada em nenhuma etapa futura — permanecem aqui como registro de que foram consideradas, à
espera de evidência (testes de usabilidade ou demanda real) antes de virarem requisito.

## 4. Prototipação

Telas necessárias para representar o MVP:

1. **Login / Cadastro**
2. **Dashboard** (visão resumida da Minha Vida: áreas, tarefas do dia, alerta do Radar)
3. **Minha Vida** (lista de áreas)
4. **Área** (lista de tarefas e eventos daquela área, indicando quem é o responsável de cada
   tarefa)
5. **Nova Tarefa / Editar Tarefa** (título, área, prazo, prioridade, responsável)
6. **Calendário de Eventos** (visão dos compromissos por data)
7. **Conexões da Área** (quem tem acesso àquela área e com qual permissão)
8. **Radar** (índice de carga, tarefas atrasadas, conflitos de horário)

## 5. Teste / Validação

Perguntas e critérios propostos para testar o protótipo com usuários (mesmo que informalmente,
com colegas ou conhecidos que se encaixem nas personas):

| Critério | Pergunta para o usuário testado |
|---|---|
| Facilidade de uso | "Você conseguiu criar uma área e uma tarefa sem ajuda?" |
| Entendimento do conceito | "Na sua opinião, qual a diferença entre 'Minha Vida' e uma área?" |
| Utilidade | "Isso resolveria algum problema real que você tem hoje?" |
| Clareza | "Ficou claro quem era o responsável por cada tarefa que você viu?" |
| Organização | "Você conseguiu achar rapidamente as tarefas atrasadas?" |
| Privacidade | "Você entendeu que uma área só fica visível para quem você conectar a ela?" |
| Utilidade das conexões | "Faria sentido para você conectar alguém a apenas uma área específica da sua vida?" |
| Utilidade do Radar | "O índice de carga te ajudaria a perceber excesso de tarefas antes de ficar atrasado?" |

Critério de sucesso mínimo: pelo menos 4 em 5 pessoas testadas conseguem, sem instrução prévia,
(a) criar uma área, (b) criar uma tarefa com responsável e prazo, e (c) identificar corretamente
o índice de carga na tela do Radar.
