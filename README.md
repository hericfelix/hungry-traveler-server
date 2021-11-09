<h1 align="center">
  Hungry Traveler - API
</h1>

<p align = "center">
Este é o backend da aplicação HungryTraveller - Um compilado gastronômico. O objetivo dessa aplicação é conseguir criar um frontend de qualidade, utilizando o que foi ensinado no segundo módulo do curso (Q2) - E desenvolver hard skills e soft skills.
</p>

<p align="center">
  <a href="#endpoints">Endpoints</a>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</p>

## **Endpoints**

A API tem um total de 4 endpoints, sendo em volta principalmente do usuário - que poderá cadastrar seu perfil, listar restaurantes, favoritos. <br/>

O url base da API é https://hungry-traveler-json-server.herokuapp.com

## Rotas que não precisam de autenticação

<h2 align ='center'> Criação de usuário </h2>

`POST /register - FORMATO DA REQUISIÇÃO`

```json
{
  "email": "kenzo@faminto.com",
  "password": "123456",
  "name": "Kenzo"
}
```

Caso dê tudo certo, a resposta será assim:

`POST /register - FORMATO DA RESPOSTA - STATUS 201`

```json
{
  "accessToken": "xxxxx",
  "user": {
    "email": "kenzo@faminto.com",
    "name": "Kenzo",
    "id": 1
  }
}
```

<h2 align = "center"> Login </h2>

`POST /login - FORMATO DA REQUISIÇÃO`

```json
{
  "email": "kenzo@faminto.com",
  "password": "123456"
}
```

Caso dê tudo certo, a resposta será assim:

`POST /login - FORMATO DA RESPOSTA - STATUS 201`

```json
{
  "accessToken": "xxxxx",
  "user": {
    "email": "kenzo@faminto.com",
    "name": "Kenzo",
    "id": 1
  }
}
```

Com essa resposta, vemos que temos duas informações, o user e o token respectivo, dessa forma você pode guardar o token e o usuário logado no localStorage para fazer a gestão do usuário no seu frontend.

<h2 align = "center"> Listando restaurantes </h2>

`GET /restaurants/ - FORMATO DA RESPOSTA - STATUS 200`

```json
{
  "name": "DOM",
  "type": "comida brasileira",
  "location": "",
  "address": "",
  "city": "São Paulo",
  "image": "",
  "menu": "",
  "business hours": "",
  "id": 1
}
```

<h2 align = "center"> Listando avaliações </h2>

`GET /score/restaurant_id - FORMATO DA RESPOSTA - STATUS 200`

```json
{
  "id": 1,
  "userId": 1,
  "restaurantId": 1,
  "score": 5
}
```

## Rotas que necessitam de autorização

Rotas que necessitam de autorização deve ser informado no cabeçalho da requisição o campo "Authorization", dessa forma:

> Authorization: Bearer {token}

Após o usuário estar logado, ele deve conseguir adicionar um restaurante aos seus favoritos.

<h2 align = "center"> Adicionando aos favoritos </h2>

`POST /favorites/restaurant_id - FORMATO DA REQUISIÇÃO`

```json
{
  "userId": 1,
  "restaurantId": 1
}
```

Ele consegue também listar seus restaurantes favoritos.

`GET /favorites/restaurant_id - FORMATO DA RESPOSTA - STATUS 200`

```json
{
  "id": 1,
  "userId": 1,
  "restaurantId": 1,
  "score": 5
}
```

Também é possível deletar um restaurante da lista de favoritos, utilizando este endpoint:

`DELETE /favorites/restaurant_id`

```
Não é necessário um corpo da requisição.
```

<h2 align = "center"> Adicionando avaliação </h2>

Assim como os endpoints anteriores, nesse precisamos estar logados, com o token no cabeçalho da requisição. Estes endpoints são para adicionar ou deletar uma avaliação de um restaurante.

`POST /score/userId - FORMATO DA REQUISIÇÃO`

```json
{
  "id": 1,
  "userId": 1,
  "restaurantId": 1,
  "score": 5
}
```

Também é possível deletar uma avaliação feita pelo usuário, utilizando este endpoint:

`DELETE /score/restaurant_id`

```
Não é necessário um corpo da requisição.
```
