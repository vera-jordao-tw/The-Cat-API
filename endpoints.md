# Endpoints The Cat API

<br> 

Neste arquivo voccê conheerá cada endpoint, as formas de requisição e os exemplos de _response body_. 🐾

<br>

## Tabela de Conteúdo
- [1. Post/images/upload](#1-post/images/upload)
- [2. GET/images](#2-get-images)
- [3. GET/images/{image_id}](#3-get-images_id)
- [4. DEL/images/{image_id}](#4-del/images/image_id)

<br>

## 1. POST/images/upload

<br>

https://api.thecatapi.com/v1/images/upload

<b>

Este endpoint cria uma nova imagem quando é informado um arquivo válido do tipo:

-   .gif    
-   .jpg    
-   .png

<br>

> [!IMPORTANT]  
> 1. O **file** é um _body param_  **obrigatório**.
> 2. Imagens sem gatos ou impróprias serão rejeitadas.

<br>

### Exemplo de requisição:

```  
curl -X 'POST' \
POST 'https://api.thecatapi.com/v1/images/upload' \
--header 'x-api-key: live_w10RexaKpMeFam5ubRnZZ4hHui6WWajbHQ95pWkGkZsch9kAxa6nSodlPSJ5PnBj' \
--form 'file=@"7iDTcrCER/Cat-100.jpeg"'
```
<br>

![201-Created](https://user-images.githubusercontent.com/27686944/204299738-5dfb178e-0c50-4bc1-b5d2-c5cba44fedfb.jpeg)

<br>

> 😻 A resposta de código `201 Created` indica que o arquivo da imagem foi criado com sucesso. Ela retorna um JSON com as informações, incluindo o novo `ID`.

<br>

### Exemplo de response body:
``` json
{
    "id": "N40r_E3J-",
    "url": "https://cdn2.thecatapi.com/images/N40r_E3J-.jpg",
    "width": 750,
    "height": 600,
    "original_filename": "Cat-100.jpeg",
    "pending": 0,
    "approved": 1
}
```
<br>

## 2. GET/images

<br>

https://api.thecatapi.com/v1/images?limit=1

<br>

Este endpoint busca **todas** as imagens enviadas para sua conta via `/images/upload.`

> [!IMPORTANT]  
> O `limit` é um _path param_  **obrigatório**.

<br>

Para limitar o retorno, use estes _query params_:

| Parâmetro	 | Descrição |  Tipo | Obrigatório |
|--|--|--|--|
| `limit` | Número de resultados a serem retornados. O valor máximo é 25. O valor padrão é 1. | `integer` | **Sim**
| `mime_types` | Tipos de imagem a serem retornados: .gif, .jpg, ou .png. O padrão é retornar todos os tipos. | `string` delimitado por vírgulas. | Não
| `order` | Ordem de retorno: RANDOM, ASC ou DESC. O padrão é RANDOM. | integer | Não

<br>

### Exemplo de requisição:

``` 
curl --location --request 
GET 'https://api.thecatapi.com/v1/images?limit=1' \ 
--header 'x-api-key: live_w10RexaKpMeFam5ubRnZZ4hHui6WWajbHQ95pWkGkZsch9kAxa6nSodlPSJ5PnBj'
```

<br>

![200-OK-reduc](https://user-images.githubusercontent.com/27686944/204300801-4c2dd4bb-509a-4fe3-8f24-951f39150728.jpeg)


<br>

> 😻 A resposta de código `200 OK` indica que a consulta foi executada com sucesso. Ela retorna um JSON com todas as informações da imagem.

<br>

### Exemplo de response body:

```  json
[
  {
    "breeds": [],
    "id": "N40r_E3J-",
    "url": "https://cdn2.thecatapi.com/images/N40r_E3J-.jpg",
    "width": 750,
    "height": 600,
    "sub_id": null,
    "created_at": "2022-11-26T15:14:36.000Z",
    "original_filename": "Cat-100.jpeg",
    "breed_ids": null
  }
]
```
<br>

## 3. GET/images/{image_id}

<br>

https://api.thecatapi.com/v1/images/{image_id}

<br>

Este endpoint **busca** a imagem correspondente ao _**path param**_  `image_id`.

<br>

> [!IMPORTANT]  
> O `image_id` é um _path param_  **obrigatório**.

<br>

### Exemplo de requisição:

``` 
curl --location --request 
GET 'https://api.thecatapi.com/v1/images/6nd1mD1zw' \ 
--header 'x-api-key: live_w10RexaKpMeFam5ubRnZZ4hHui6WWajbHQ95pWkGkZsch9kAxa6nSodlPSJ5PnBj'
```
<br>

![200-OK-reduc](https://user-images.githubusercontent.com/27686944/204300864-71bca146-bcaa-435c-9b59-d8e9cfc1a232.jpeg)

<br>

> 😻 A resposta de código `200 OK` indica que a consulta foi executada com sucesso. Ela retorna um JSON com todas as informações da imagem.
>
> <br>

### Exemplo de response body:

```  json 
[
  {
    "breeds": [],
    "id": "N40r_E3J-",
    "url": "https://cdn2.thecatapi.com/images/N40r_E3J-.jpg",
    "width": 750,
    "height": 600,
    "sub_id": null,
    "created_at": "2022-11-26T15:14:36.000Z",
    "original_filename": "Cat-100.jpeg",
    "breed_ids": null
  }
]
```

<br>

## 4. DEL/images/{image_id}

<br>

https://api.thecatapi.com/v1/images/{image_id}

<br>

Este endpoint **exclui** o registro correspondente ao _**path param**_  `image_id`.

<br>

> [!IMPORTANT]  
> O `image_id` é um _path param_  **obrigatório**.

<br>

### Exemplo de requisição:

``` 
curl --location --request 
DELETE 'https://api.thecatapi.com/v1/images/6nd1mD1zw' \ 
--header 'x-api-key: live_w10RexaKpMeFam5ubRnZZ4hHui6WWajbHQ95pWkGkZsch9kAxa6nSodlPSJ5PnBj'
```

<br>

![204-No Content-reduc](https://user-images.githubusercontent.com/27686944/204301141-50031ac7-ad10-4e9f-8ce7-2872c7fc5cb8.jpeg)

<br>

> 😻 A resposta de código `204 No Content` indica que a exclusão foi executada com sucesso. Ela retorna um JSON vazio.

<br>

> [!NOTE]  
> Para confirmar a exclusão do registro, execute o GET /images/{image_id}.

<br>

***
😹  *"O tempo gasto com gatos nunca é tempo perdido"*. - Sigmund Freud

***

<br>

_Esta documentação também está disponível no Postman em_ https://documenter.getpostman.com/view/23760915/2s8YsuurZs 
