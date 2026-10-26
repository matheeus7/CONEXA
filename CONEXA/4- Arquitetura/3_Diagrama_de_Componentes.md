## 3. Diagrama de Componentes

### Descrição

Abre o contêiner **Aplicação Web CONEXA** e mostra seus blocos internos, organizados nas três
camadas definidas no padrão arquitetural. Cada componente tem uma responsabilidade única e uma porta
pública (interface); o núcleo de regras fica escondido atrás dela.

### Camadas e componentes

**Camada de Apresentação (MVC)**
- Seis **Controllers**, cada um ligado à porta de um componente: `AuthController`, `AreaController`,
  `TarefaController`, `EventoController`, `ConexaoController` e `RadarController`.
- **Views Thymeleaf:** templates das 8 telas, preenchidos com o modelo montado pelos Controllers.

**Camada de Aplicação (Portas e Adaptadores / Hexagonal)**
- **Autenticação:** cadastro, login, senha com hash e sessão protegida (RNF01, RNF02).
- **Áreas:** Minha Vida; áreas privadas por padrão; aplica o isolamento entre áreas (RNF03).
- **Conexões:** conecta uma pessoa a uma área com nível de permissão e informa se ela pode acessar.
- **Tarefas:** tarefa com responsável distinto do criador, prazo e prioridade; publica eventos.
- **Eventos:** compromissos por data e detecção de conflito de horário; publica eventos.
- **Radar:** Índice de Carga por regra determinística, tarefas atrasadas e conflitos.
- **Notificações:** gera e lista alertas internos (RF12).
- **Barramento de Eventos Interno:** Observer/Pub-Sub no mesmo processo
  (`ApplicationEventPublisher` / `@EventListener`).

**Camada de Persistência**
- **Repositórios JPA:** adaptadores de saída, um por entidade do domínio.

### Relações

- O Navegador conversa com a camada de apresentação por HTTPS; a apresentação chama as portas da
  camada de aplicação; a aplicação acessa dados pelos repositórios; os repositórios leem e gravam
  no PostgreSQL.
- **Tarefas** e **Eventos** validam o acesso consultando **Áreas**, que consulta **Conexões** para
  decidir a permissão.
- **Tarefas** e **Eventos** publicam as alterações no **Barramento**, que avisa o **Radar**
  (recalcular) e as **Notificações** (gerar alerta).
- O **Radar** consulta Tarefas e Eventos pelas portas.

### Explicação

Três regras do projeto aparecem de forma visível neste diagrama:

1. **O Radar consome, mas não possui, os dados de Tarefas e Eventos.** Ele só os lê pelas portas
   públicas, e a estrutura em Portas e Adaptadores torna isso verificável no código, e não apenas
   uma convenção da equipe.
2. **Tarefas não conhecem o Radar nem as Notificações.** Elas apenas publicam eventos, e quem tem
   interesse assina. Isso mantém o acoplamento baixo e permite que evoluções futuras, como o Radar
   Compartilhado, entrem como novos assinantes sem alterar componentes já construídos.
3. **O isolamento entre áreas (RNF03)** passa sempre pela verificação Áreas ↔ Conexões.

Como cada componente depende apenas de portas, é possível testá-los isoladamente, trocando as
dependências por mocks (JUnit 5 + Mockito), o que atende ao RNF06.

---

<img width="2562" height="1082" alt="diagrama_componentes drawio" src="https://github.com/user-attachments/assets/f558eabd-9ad4-4ca2-97e7-c30c90d89792" />
