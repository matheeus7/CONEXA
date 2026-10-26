## 2. Diagrama de Contêineres

### Descrição

Abre a caixa do CONEXA e mostra as unidades que executam de forma independente: o que roda no
navegador, o que roda no servidor e onde os dados ficam guardados. Aqui "contêiner" significa uma
parte executável ou armazenamento, e não necessariamente um contêiner Docker.

### Elementos

- **Navegador Web (HTML + CSS):** exibe as 8 telas do protótipo (Login, Dashboard, Minha Vida,
  Área, Tarefa, Calendário, Conexões e Radar). Não tem lógica de negócio; só apresenta páginas
  geradas pelo servidor.
- **Aplicação Web CONEXA (Java 17 + Spring Boot):** concentra tudo o que o sistema faz: telas
  (Spring MVC + Thymeleaf), regras de negócio, autenticação (Spring Security + BCrypt), eventos
  internos e monitoramento (Actuator + Logback).
- **Banco de Dados (PostgreSQL):** armazena Pessoa, Área, Tarefa, Evento, Conexão e Notificação.

### Relações

- Usuário e Pessoa Conectada usam o Navegador Web.
- O Navegador e a Aplicação Web trocam requisições e páginas HTML por **HTTPS**.
- A Aplicação Web lê e grava no banco via **Spring Data JPA / Hibernate**.

### Explicação

A principal decisão deste nível é o **monólito**: um único serviço, implantado em um único contêiner
Docker. Microsserviços e aplicativo mobile nativo estão fora do escopo do MVP, e uma aplicação única
com renderização no servidor evita manter um front-end separado, o que é proporcional a um projeto
acadêmico. O banco é relacional porque o domínio tem relações bem definidas (Área pertence a Pessoa,
Tarefa pertence a Área, Conexão liga Pessoa a Área).

---
<img width="1361" height="671" alt="diagrama_conteineres drawio" src="https://github.com/user-attachments/assets/691288aa-8cc4-466f-a02f-505fc1a6a14e" />
