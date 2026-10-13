# Tecnologias e Ferramentas Utilizadas

## Introdução

Aqui mostramos o Mapa de Tecnologias (Tech Stack) do CONEXA, detalhando as principais
ferramentas, linguagens e bibliotecas utilizadas no desenvolvimento do sistema.

O CONEXA foi definido na Etapa 1 como uma aplicação **web**, implantada como um único serviço
monolítico — não como um conjunto de microsserviços nem como aplicativo mobile nativo (ambos
explicitamente fora do escopo do MVP). A escolha de tecnologias desta etapa segue diretamente o
padrão arquitetural já definido: Camadas com Portas e Adaptadores
(Hexagonal) para a Aplicação, MVC para a Apresentação, e Observer/Pub-Sub interno para desacoplar
Notificações e Radar das mudanças em Tarefas e Eventos. Por isso, a prioridade aqui não é
"tecnologia mais moderna", e sim tecnologias que implementem essas três decisões sem exigir
infraestrutura além da viabilidade de um projeto acadêmico.

## Mapa de Tecnologias

```text
┌─────────────────────────────────────────────────────────────────┐
│                    APRESENTAÇÃO (padrão MVC)                     │
│         Spring MVC (Controllers) + Thymeleaf (Views)             │
└──────────────────────────────┬────────────────────────────────────┘
                                │
┌──────────────────────────────▼────────────────────────────────────┐
│          APLICAÇÃO (padrão Hexagonal — portas e adaptadores)      │
│   Java 17 + Spring Boot                                           │
│   Portas = interfaces dos componentes (Áreas, Tarefas, Eventos,   │
│   Conexões, Radar) · Núcleo = regras de negócio de cada um        │
│                                                                     │
│   Eventos internos (Observer/Pub-Sub):                            │
│   Spring ApplicationEventPublisher / @EventListener               │
│   → dispara Radar e Notificações quando Tarefas/Eventos mudam     │
│                                                                     │
│   Autenticação: Spring Security + senha com hash (BCrypt)         │
└──────────────────────────────┬────────────────────────────────────┘
                                │ Spring Data JPA / Hibernate
┌──────────────────────────────▼────────────────────────────────────┐
│                  PERSISTÊNCIA — PostgreSQL                        │
└─────────────────────────────────────────────────────────────────┘

   Testes: JUnit 5 + Mockito          Monitoramento: Actuator + Logback
   Implantação: contêiner Docker único, hospedagem gratuita/educacional
```

O mapa acima resume as principais tecnologias utilizadas no desenvolvimento do CONEXA,
organizadas nas seguintes categorias:

* **Apresentação**: interface web construída com Spring MVC e Thymeleaf, renderizada no próprio
  servidor — sem necessidade de um front-end separado, mantendo o sistema como uma única
  aplicação implantável.
* **Aplicação**: Java com Spring Boot, organizando cada componente identificado na Etapa 1 como
  um módulo com porta pública (interface) e núcleo privado.
* **Eventos internos**: mecanismo de publicação/assinatura embutido no próprio framework
  (Spring Events), sem um barramento de mensagens externo.
* **Banco de Dados**: PostgreSQL, acessado via Spring Data JPA, adequado ao modelo de domínio
  fortemente relacional do CONEXA (Pessoa, Área, Tarefa, Evento, Conexão).
* **Notificações**: alertas gerados e exibidos dentro da própria aplicação (RF12), sem canal
  externo (e-mail/push), conforme o escopo do MVP definido na Etapa 1.
* **Autenticação**: Spring Security, com senha armazenada com hash e sessão autenticada via
  HTTPS.
* **Monitoramento**: Spring Boot Actuator (verificação de disponibilidade) e Logback (registro de
  erros), suficientes para um sistema acadêmico sem exigir um serviço de terceiros pago.
* **Implantação**: um único contêiner Docker, hospedado em serviço gratuito ou no ambiente da
  disciplina — compatível com a decisão de manter o CONEXA como aplicação monolítica.

## Tabela de Tecnologias e Justificativa

A tabela abaixo documenta, de forma organizada, as tecnologias, ferramentas e padrões utilizados
no desenvolvimento do CONEXA. Esta estrutura tem como propósito:

* Facilitar a visualização rápida da stack tecnológica do projeto;
* Ajudar outra pessoa desenvolvedora a entender o ecossistema da aplicação;
* Justificar as escolhas técnicas, amarrando cada uma a uma decisão já tomada na Etapa 1 ou no
  padrão arquitetural desta etapa — nenhuma tecnologia foi escolhida sem motivo rastreável.

| Camada | Tecnologia | Justificativa |
|---|---|---|
| Apresentação | Spring MVC + Thymeleaf | Implementa o padrão MVC escolhido; renderização no servidor evita manter um front-end separado, mantendo o CONEXA como aplicação web monolítica |
| Aplicação | Java 17 + Spring Boot | Suporta nativamente injeção de dependência, necessária para implementar portas (interfaces) e adaptadores (implementações) do padrão Hexagonal sem acoplamento direto entre componentes |
| Eventos internos | Spring ApplicationEventPublisher / `@EventListener` | Implementa o Observer/Pub-Sub interno escolhido no padrão arquitetural, desacoplando Tarefas/Eventos de Radar e Notificações sem exigir um barramento de mensagens externo |
| Banco de Dados | PostgreSQL + Spring Data JPA (Hibernate) | Banco relacional, adequado ao domínio do CONEXA (Pessoa, Área, Tarefa, Evento, Conexão possuem relações e chaves estrangeiras bem definidas, não dados semiestruturados) |
| Autenticação | Spring Security + BCrypt | Atende RNF02 (senha com hash, nunca em texto puro) e RNF01 (privacidade por padrão), com sessão protegida por HTTPS |
| Notificações | Mecanismo interno da aplicação (sem serviço externo) | O MVP define alertas apenas internos (RF12); e-mail e push ficam fora do escopo desta fase, então nenhuma integração externa é necessária |
| Testes | JUnit 5 + Mockito | Permite testar cada componente isoladamente substituindo as portas de suas dependências por mocks, atendendo diretamente RNF06 (modularidade e testabilidade) |
| Monitoramento | Spring Boot Actuator + Logback | Fornece verificação de disponibilidade e registro de erros suficiente para um projeto acadêmico, sem depender de um serviço de monitoramento pago de terceiros |
| Implantação | Contêiner Docker único, hospedagem gratuita/educacional | Mantém a decisão de aplicação monolítica do padrão arquitetural; evita a complexidade de orquestrar múltiplos serviços, desproporcional ao escopo do MVP |

## Rastreabilidade com decisões anteriores

| Escolha desta seção | Origem da decisão |
|---|---|
| Aplicação monolítica, um único contêiner | Padrão arquitetural (Seção 1) — "aplicação web monolítica (não microsserviços)" |
| Spring Events para Observer/Pub-Sub | Padrão arquitetural (Seção 1) — "mecanismo interno ao mesmo processo, não arquitetura orientada a eventos distribuída" |
| PostgreSQL relacional | Modelo de domínio da Etapa 1 — entidades com relações explícitas (Área pertence a Pessoa, Tarefa pertence a Área, Conexão liga Pessoa a Área) |
| Senha com hash via Spring Security/BCrypt | RNF02 — Segurança de autenticação |
| Sem canal de notificação externo | Escopo da Etapa 1 — "Notificações por e-mail ou push mobile" listado como Fora do Escopo |
| JUnit 5 + Mockito para teste isolado de componentes | RNF06 — Manutenibilidade e modularidade |
