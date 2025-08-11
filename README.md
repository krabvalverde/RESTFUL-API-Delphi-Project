# 💻 REST API em Delphi 12

RESTFUL API rápida e leve feita com **Delphi 12 (Atenas)**, usada para executar comando SQL em meu <br>
servidor de banco de dados PostgreSQL.

Este projeto foi criado para facilitar a execução de requisições em meu servidor de banco de dados <br>
hospedado na nuvem.

Ainda em desenvolvimento...

Para dúvidas ou mais informações, estou à disposição! 😉

---

# 💡 Utilização
  - Fazer requisições HTTP
  - Utilizando rotas para interagir com o banco de dados PostgreSQL (servidor)
  - Gerenciar entrada e saída de JSON
  - Autenticação de usuários com JWT

---

# ⚙️ Stack
  - **Horse** - Framework HTTP leve e rápido para Delphi
  - **Boss** - Instalador de dependências para Delphi
  - **PostgreSQL** - Banco de dados relacional open-source
  - **Delphi 12 (Athens)** — Pascal para apps nativos

---
# 🐎 Horse Framework 
| Página oficial do Horse                    |
|--------------------------------------------|
| [Horse](https://github.com/HashLoad/horse) |
---
# ⚜️ Boss
| Instalador de dependências Boss          |
|------------------------------------------|
| [Boss](https://github.com/HashLoad/boss) |

---
# 🧬 Middlewares utilizados

| Middlewares oficiais                                               | 
|--------------------------------------------------------------------|
| [horse/json](https://github.com/HashLoad/jhonson)                  |
| [horse/jwt](https://github.com/HashLoad/horse-jwt)                 |                                           
| [horse/exception](https://github.com/HashLoad/handle-exception)    |                              
| [horse/logger](https://github.com/HashLoad/horse-logger)           |                                    
| [horse/compression](https://github.com/HashLoad/horse-compression) |  

---
# 🔗 Endpoints atuais

| Método | Endpoint                 | Descrição                                                                        | 
|--------|--------------------------|----------------------------------------------------------------------------------|
| POST   | `/login/validar-cpf`     | Realiza validação do CPF inserido                                                |
| POST   | `/login/validar-senha`   | Realiza validação da senha do usuário                                            |
| POST   | `/consultas/dependentes` | Consulta os dependentes do usuário da requisição (feito para projeto específico) |
| GET    | `/status`                | Retorna informações de conexão da API e do banco de dados                        |
