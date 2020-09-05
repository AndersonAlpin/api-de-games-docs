# API de Games
Está API é utilizada para gerenciar os games cadastrados, além de realizar uma autenticação do usuário.
## Endpoints
### GET /games
Esse endpoint é responsável por retornar a listagem de todos os games cadastrados no banco de dados.
#### Parâmetros
Nenhum.
#### Respostas
##### OK! 200
Caso essa resposta aconteça, você vai receber a listagem de todos os games.
Exemplo de resposta:
```
[
    {
        "id": 5,
        "title": "Grand Chase Prime",
        "price": 120,
        "year": 2006,
        "createdAt": "2020-09-03T21:40:08.000Z",
        "updatedAt": "2020-09-03T22:15:03.000Z"
    },
    {
        "id": 6,
        "title": "The King of Fighters",
        "price": 190,
        "year": 2002,
        "createdAt": "2020-09-05T01:40:50.000Z",
        "updatedAt": "2020-09-05T01:41:01.000Z"
    }
]
```
##### Falha na autenticação! 401
Caso essa resposta aconteça, significa que aconteceu alguma falha durante o processo de autenticação da requisição. Motivos: E-mail ou senha inválidos.<br>
Exemplo de resposta:
```
{
    "error": "Token inválido."
}
```

### POST /auth
Esse endpoint é responsável por fazer o processo de login.
#### Parâmetros
Email: E-mail do usuário cadastrado no sitema.<br>
password: Senha do usuário cadastrado no sistema.<br>
Exemplo:
```
{
   "email": "usuario@gmail.com",
   "password": "0000"
}
```
#### Respostas
##### OK! 200
Caso essa resposta aconteça, você vai receber o token JWT para ter acesso aos endpoints protegidos pela API.<br>
Exemplo de resposta:
```
{
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MSwiZW1haWwiOiJ1c3VhcmlvQGdtYWlsLmNvbSIsImlhdCI6MTU5OTI3NTI2MiwiZXhwIjoxNTk5NDQ4MDYyfQ.oAVKzcanUoOq8WxKLw0In7DDGTXlMeKhqOtVYyroe_4"
}
```
##### Falha na autenticação! 401
Caso essa resposta aconteça, significa que aconteceu alguma falha durante o processo de autenticação da requisição. Motivo: Token inválido / Token expirado.<br>
Exemplo de resposta:
```
{
    "error": "Credenciais inválidas."
}
```
