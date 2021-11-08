##### json-server-hungry-traveler

Esse é o repositório com a base de JSON-Server + JSON-Server-Auth desenvolvida para ser usada no desenvolvimento do Capstones do Q2.

### Cadastro

POST /register - FORMATO DA REQUISIÇÃO

{
"email": "kenzo@faminto.com",
"password": "123456",
"name": "Kenzo"
}

Caso dê tudo certo, a resposta será assim:

POST /register - FORMATO DA RESPOSTA - STATUS 201

{
"accessToken": "xxxxx",
"user": {
"email": "kenzo@faminto.com",
"name": "Kenzo",
"id": 1
}
}

### Login

POST /login - FORMATO DA REQUISIÇÃO

{
"email": "kenzo@faminto.com",
"password": "123456"
}

Caso dê tudo certo, a resposta será assim:

POST /login - FORMATO DA RESPOSTA - STATUS 200

{
"accessToken": "xxxxx",
"user": {
"email": "kenzo@faminto.com",
"name": "Kenzo",
"id": 1
}
}
