## 1. Diagrama de Contexto

### Descrição

Mostra o CONEXA como uma única caixa e o que está ao redor dela: as pessoas que o usam e os
sistemas externos com os quais ele conversa. É a visão que qualquer pessoa, mesmo sem formação
técnica, consegue ler.

### Elementos

- **Usuário:** dono da Minha Vida. Organiza a própria vida em áreas privadas, cria tarefas e
  eventos com responsável e prazo e acompanha o Radar de carga. Representa as personas Beatriz,
  Rafael e Carla.
- **Pessoa Conectada:** alguém que o usuário conectou a **uma única área**, com um nível de
  permissão (colegas de TCC, o irmão de Carla, João na área "Casa"). Não enxerga as demais áreas.
- **CONEXA:** o sistema, uma aplicação web de organização pessoal e gestão de responsabilidades.
- **E-mail / Push (tracejado):** canais externos de notificação, mantidos no diagrama apenas para
  deixar explícito que estão **fora do escopo do MVP**.

### Relações

- O Usuário organiza áreas, tarefas e eventos e consulta o Radar.
- A Pessoa Conectada acessa somente a área em que foi conectada.
- O CONEXA, em uma versão futura, enviaria alertas por e-mail ou push (seta tracejada).

### Explicação

Neste nível não aparecem autenticação, banco de dados nem serviços de mapa, porque o MVP não depende
de nenhum sistema externo: a autenticação (Spring Security), a persistência (PostgreSQL) e as
notificações (RF12) ficam dentro do próprio CONEXA. Por isso o diagrama é enxuto, ao contrário de
sistemas que integram serviços de terceiros.

Há também uma observação importante: a Pessoa Conectada **também é uma conta CONEXA**, com a própria
Minha Vida privada. O vínculo acontece por área, nunca pela conta inteira. Isso materializa o
diferencial do produto identificado na exploração de mercado: conectar alguém apenas a uma área
específica.

<img width="1162" height="821" alt="diagrama_contexto drawio" src="https://github.com/user-attachments/assets/58a7a912-a49c-4205-a076-795432934d99" />
