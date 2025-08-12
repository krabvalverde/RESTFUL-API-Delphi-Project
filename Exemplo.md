# Exemplo de Interação com API - Login

Todo o tráfego é realizado via HTTPS, em meu domínio `https://api.getsoftwave.com.br`, garantindo que todos os dados contidos durante a <br> 
troca de informações seja criptografada.

---

Aqui vai um pequeno exemplo de troca de informações durante uma requisição no endpoint /login/verificar-cpf:


Ao inserir o CPF no campo, envia-se o seguinte JSON para a API:

{ <br>
  "cpf": "123456789123" <br>
}

A resposta da API será:

- Status 200 (se o usuário existir no banco de dados)
- JSON retornado:
{ <br>
  "nome": "Kaique" <br>
}

O mesmo se aplica para o campo de senha:

{ <br>
  "cpf": "123456789123", <br>
  "senha": "senha" <br>
}

A API recebe, compara a senha recebida com o hash salvo no banco e retorna:

- Status 200 (indica que a autenticação foi bem-sucedida)
- JSON retornado:
{ <br>
  "access_token": "token de acesso válido por 15 minutos", <br>
  "refresh_token": "token refresh válido por 20 dias" <br>
}

---

# Possíveis erros

Em casos de erro (como CPF ou senha incorretos), a API pode retornar:
- Status 400 (Bad Request) para parâmetros inválidos.
- Status 401 (Unauthorized) quando a autenticação falhar.

