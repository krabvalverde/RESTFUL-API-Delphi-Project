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

---
# 🛠 Utilização básica

### Criando uma rota customizada

1. Criando uma rota pública:
- Declarar a rota no API.dpr, especificando o método HTTP (GET, POST...):
```
THorse.Get('/exemplo/ping',
  procedure(Req: THorseRequest; Res: THorseResponse; Next: TProc)
  begin
    Res.Send('Pong');
  end;
```

Dessa forma, quem requisitar no endpoint receberá a resposta, sem necessidade de autenticação.

2. Criando uma rota privada (JWT):
- Declarar a rota no API.dpr, também especificando o método HTTP:

```  
THorse
  .AddCallback(HorseJWT(GetEnv('API_KEY'), THorseJWTConfig.New.SessionClass(TCustomClaims)))
  .Post('exemplo/rota/privada',
    procedure(Req: THorseRequest; Res: THorseResponse; Next: TProc)
    var
      oClaims: TCustomClaims;
    begin
      oClaims := Req.Sessions<TCustomClaims>;
      
      { Resto da função do endpoint }
     
    end;
```

**OBS**: O método '.AddCallBack' é quem cuida da validação do token e já verifica se não está expirado, não é necessária valiação adicional.  
Nos endpoints privados, DEVE ser criado o objeto de 'TCustomClaims' e declarar da maneira acima, pois é nele que ficam guardadas as <br>
informações da sessão do usuário. Não é necessário liberar o objeto da memória, o próprio Horse faz a gestão.  
**ATENÇÃO**: Sempre especifique o tipo de token que será utilizado no endpoint através da propriedade 'TCustomClaims.Tipo' (refresh ou access).

3. Criando métodos:
- Utilize a unit 'untMethods' para criar métodos que serão utilizados nos endpoints.

4. Criando propriedades de tokens:
- Defina as propriedades que os tokens de usuário podem ter em 'unAPI.Infra.Claims', utilizando sempre getters e setters.

Dicas:
- Nunca retorne erros explicitos da API nos 'E.Message', sempre retorne erros genéricos utilizando 'raise Exception.Create'. Essa prática dificulta algum possível
invasor de conseguir informações específicas do funcionamento da API.






