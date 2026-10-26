## 4. Diagrama de Classes (código)

### Descrição

Mostra, no nível de código, as classes que implementam o domínio e o mecanismo do Radar, com seus
atributos, métodos e relações. É o diagrama mais próximo da implementação em Java.

### Elementos

**Domínio**
- `Pessoa`: id, nome, e-mail e senha com hash; autentica e cria áreas.
- `Area`: nome e descrição; sabe dizer se está visível para determinada pessoa.
- `Tarefa`: título, descrição, prazo, prioridade, status, criador e responsável; pode ser
  concluída, atribuída a outra pessoa e informar se está atrasada.
- `Evento`: título, início e fim; informa se conflita com outro evento.
- `Conexao`: liga uma Pessoa a uma Área com um `NivelPermissao`.
- `Notificacao`: mensagem, tipo de alerta, indicador de leitura e data de criação.
- Enums: `Prioridade`, `StatusTarefa`, `TipoAlerta`, `NivelPermissao` e `NivelCarga`.

**Portas, Radar e eventos**
- `TarefaPort`, `EventoPort` e `RadarPort` (interfaces): as portas públicas dos componentes.
- `RadarService`: implementa `RadarPort`, calcula o `IndiceCarga` e lista atrasos e conflitos.
- `NotificacaoService`: gera os alertas a partir dos eventos recebidos.
- `IndiceCarga`: objeto de valor com o valor do índice, o nível de carga, a quantidade de tarefas
  atrasadas e de conflitos de horário.
- `AlteracaoRegistradaEvent`: evento interno publicado quando uma Tarefa ou um Evento muda.

### Relações

- **Composição:** Pessoa possui Áreas; Área contém Tarefas e Eventos. Se a área é removida, o que
  está dentro dela também é.
- **Associações:** Tarefa tem um `criador` (1) e um `responsável` (0..1), ambos Pessoa; Conexão liga
  uma Pessoa a uma Área; Notificação tem um destinatário.
- **Realização:** `RadarService` realiza `RadarPort`.
- **Dependência:** `RadarService` usa `TarefaPort` e `EventoPort`, cria `IndiceCarga` e assina
  `AlteracaoRegistradaEvent`; `NotificacaoService` assina o mesmo evento e cria `Notificacao`.

### Explicação

O diagrama traduz em classes os dois conceitos centrais do CONEXA. O primeiro é que **tarefa não é
responsabilidade**: a `Tarefa` guarda criador e responsável como atributos separados, o que prova o
conceito com o menor custo de implementação no MVP. O segundo é que **o Radar é um consumidor**: o
`RadarService` não acessa o banco nem as classes de Tarefa e Evento diretamente, só as interfaces
`TarefaPort` e `EventoPort`, e se mantém atualizado reagindo ao evento interno. O cálculo do índice
é determinístico (prioridade, prazo e quantidade de itens ativos), sem IA, como definido na ideação.

---

## Premissas assumidas nos diagramas

A documentação existente não define os itens abaixo; eles foram propostos e podem ser ajustados:

| Item | Valor adotado |
|---|---|
| `NivelPermissao` | LEITURA, EDICAO |
| `StatusTarefa` | PENDENTE, CONCLUIDA (atraso é calculado pelo prazo) |
| `TipoAlerta` | TAREFA_ATRASADA, CONFLITO_HORARIO, CARGA_ALTA |
| `NivelCarga` | BAIXA, MODERADA, ALTA |
| Nomes de atributos e métodos das classes | Sugestões a validar na implementação |

<img width="1742" height="1419" alt="diagrama_classes drawio" src="https://github.com/user-attachments/assets/dda90e1a-0174-491b-a530-d7fe8e2850f9" />
