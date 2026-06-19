# E-Sports Tournament Manager

Uma plataforma centralizada para organização, moderação e gestão de campeonatos amadores de e-sports. O sistema substitui fluxos manuais e descentralizados (planilhas, formulários e envio de prints em chats) por uma solução robusta focada em **Segurança, Autenticação e Autorização (RBAC)**.

---

## O Problema vs A Solução

| Contexto | Descrição |
| :--- | :--- |
| **O Problema (Cenário Atual)** | Organizadores de torneios amadores perdem horas gerenciando inscrições falsas, validando printscreens de vitória enviados no Discord e resolvendo disputas verbais causadas por jogadores irregulares (smurfs). A falta de um sistema unificado gera fraudes e exaustão para a moderação. |
| **A Solução (Este Projeto)** | Um sistema web full-stack onde o **Capitão** faz login de forma segura utilizando sua conta real do Discord (evitando fakes), cadastra sua equipe, faz o check-in e reporta vitórias enviando evidências diretamente na plataforma. Os **Juízes** possuem um painel de moderação restrito para validar os prints e avançar as equipes em um chaveamento gerado automaticamente. |

---

## Tecnologias Utilizadas (Tech Stack)

| Camada | Tecnologia | Detalhes |
| :--- | :--- | :--- |
| ![Backend](https://img.shields.io/badge/-Backend-4CAF50?style=flat-square) | **Java 21** | Linguagem principal, utilizando os recursos mais modernos da versão LTS. |
| ![Backend](https://img.shields.io/badge/-Backend-4CAF50?style=flat-square) | **Spring Boot 4.1.x** | Framework para aceleração e estruturação da API REST. |
| ![Security](https://img.shields.io/badge/-Security-F44336?style=flat-square) | **Spring Security** | Responsável por validar Tokens JWT e garantir que rotas protegidas não sejam acessadas indevidamente (OAuth2 Resource Server). |
| ![Database](https://img.shields.io/badge/-Database-2196F3?style=flat-square) | **PostgreSQL / H2** | Mapeamento Objeto-Relacional (ORM) via Spring Data JPA para abstração do banco de dados de produção (PostgreSQL) e desenvolvimento (H2). |
| ![Frontend](https://img.shields.io/badge/-Frontend-00BCD4?style=flat-square) | **React** | Biblioteca para construção da interface de usuário (SPA). |
| ![Frontend](https://img.shields.io/badge/-Frontend-00BCD4?style=flat-square) | **React Router** | Gerenciamento de rotas e criação de *Protected Routes* baseadas nas permissões do usuário. |
| ![Identity](https://img.shields.io/badge/-Identity-FF9800?style=flat-square) | **Auth0 / Firebase** | Gerencia o fluxo de login OAuth2 com o Discord, emitindo os JWTs. |

---

## Principais Funcionalidades

| Categoria | Funcionalidade | Descrição |
| :--- | :--- | :--- |
| **Segurança e Acesso** | Login Social Seguro | Autenticação exclusiva via integração com Discord OAuth2. |
| **Segurança e Acesso** | Isolamento de Dados | A API garante que um Capitão só consiga agir em partidas onde sua equipe esteja escalada. |
| **Segurança e Acesso** | RBAC | Controle de acesso baseado em perfis restritos (`CAPTAIN`, `JUDGE`, `ADMIN`). |
| **Fluxo do Campeonato** | Gestão de Equipes | Criação de equipes e escalação vinculando o Nickname in-game dos jogadores. |
| **Fluxo do Campeonato** | Chaveamento Automático | Geração algorítmica dos confrontos diretos (Brackets) após o período de check-in. |
| **Fluxo do Campeonato** | Submissão de Evidências | Interface para o Capitão submeter o link/imagem com a prova gráfica da vitória. |
| **Fluxo do Campeonato** | Sistema de Disputas | Possibilidade de contestar uma partida caso haja violação de regras pelo time adversário. |
| **Moderação** | Fila de Validação | Painel exclusivo para Juízes analisarem as evidências em tempo real. |
| **Moderação** | Avanço Dinâmico | Ao aprovar um resultado, o sistema promove a equipe vencedora automaticamente. |
| **Moderação** | Auditoria de Ações | Registro rastreável de qual Juiz aprovou qual resultado, garantindo integridade. |

---

## Como rodar o projeto localmente

*(Instruções detalhadas serão adicionadas conforme o desenvolvimento da API progredir)*

1. Clone o repositório.
2. Configure as variáveis de ambiente com suas chaves do Provedor de Identidade (Auth0/Firebase) no arquivo `application.properties`.
3. Rode o Backend usando o comando do Maven: `./mvnw spring-boot:run`.
