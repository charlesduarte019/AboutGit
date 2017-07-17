**Monitoriamento de Site**
=============

## **Sumário**

* [Site](#site)
	* [Adicionar Site](#adicionar-site)
 	* [Listar Todos os Sites](#listar-todos-os-sites)
 	* [Listar Informações Basica de Todos os Sites](#listar-informações-basica-de-todos-os-sites)
 	* [Buscar Site](#buscar-site)
 	* [Editar Site](#editar-site)
 	* [Excluir Site](#excluir-site)

## **Site**

   <_Descrição sobre o modulo_>

### **Adicionar Site**

   Adiciona um novo site.    

* **URL**

   ```http
   /interface/monitoring/host HTTP1.0
   ```

* **Método:** `POST`

*  **Parâmetro**

    |NOME|TIPO|MÍNIMO|MÁXIMO|FORMATAÇÃO|OBRIGATÓRIO|DESCRIÇÃO|
    |----|:--:|:----:|:----:|:--------:|:---------:|---------|
    nome|String|3|50|-|Sim|<_Descrição_>.|
    base_cidade_id|Integer|-|-|-|Sim|<_Descrição_>.|
    peso|Double|-|-|-|Sim|<_Descrição_>.|
    conf|Json|-|-|-|Não|<_Descrição_>.|
    latitude|Numeric|-|-|-|Sim|<_Descrição_>.|
    longitude|Numeric|-|-|-|Sim|<_Descrição_>.|
    observação|Json|-|-|-|Não|<_Descrição_>.|

*  **Requisição**

    ```json
    {
       "nome": "site",
       "base_cidade_id": 1,
       "peso": 0.1,
       "conf": "{}",
       "latitude": -1.123456,
       "longitude": -0.123456,
       "observacao": "{}"
    }
    ```
* **Resposta com Sucesso:**
  
    **Código:** 201 CREATED <br />
    **Conteúdo:**
    ```json
    {
       "id": 1
    }
    ```
 
* **Resposta com Erro:**

    **Código:** 400 BAD REQUEST <br />
    **Conteúdo:** `{ "PARAMETROS INVALIDOS": "Algo não está certo!" }`

    OU

    **Código:** 401 UNAUTHORIZED <br />
    **Conteúdo:** `{ "DONT_HAVE_PERMISSION": "Você não tem permissão para acessar essa ação!" }`

### **Listar Todos os Sites**

   Retorna todos os Sites cadastradas no sistema. Por padrão será retornado um limite máximo de 15 registros. Para retornar uma quantidade diferente, o limite deve ser enviado na requisição. Caso limite seja igual a 0 (zero) será retornado todos os registros. 

* **URL**

   ```http
   /interface/monitoring/host HTTP1.0
   ```

* **Método:** `GET`

*  **Parâmetro**

    |NOME|TIPO|MÍNIMO|MÁXIMO|FORMATAÇÃO|OBRIGATÓRIO|DESCRIÇÃO|
    |----|:--:|:----:|:----:|:--------:|:---------:|---------|
    limite|Integer|-|-|-|Não|Limite máximo de registros a serem retornados.|
    deslocamento|Integer|-|-|-|Não|Quantos registros devem ser ignorados a partir do início.|
    ordem|String|-|-|-|Não|Registro por qual será ordenado os dados.|
    ordenador|String|-|-|-|Não|Indica se a ordenação será crescente ou decrescente(ASC OU DESC).|
    filtro|JSON|-|-|-|Não|Filtros por valor de deteminado atributo.|
    filtro.id|Integer|-|-|-|Não|Filtros por valor do ID da Forma de Pagamento.|
    filtro.nome|String|3|255|-|Não| Filtros por valor Nome da Forma de Pagamento.|

* **Resposta com Sucesso:**
  
    **Código:** 200 OK <br />
    **Conteúdo:**
    ```json
    {
        "total":1,
        "data":[
            {
                "id": 1,
                "nome": "site",
                "cidade_nome": "cidade",
                "cidade_uf": "uf",
                "peso": 0.1,
                "conf": "{}",
                "latitude": -1.123456,
                "longitude": -0.123456,
                "observacao": "{}"
            }
        ]
    }
    ```
 
* **Resposta com Erro:**

    **Código:** 401 UNAUTHORIZED <br />
    **Conteúdo:** `{ "DONT_HAVE_PERMISSION": "Você não tem permissão para acessar essa ação!" }`

* **Notas:**

  *Se não for passado nenhum parâmetro de paginação(limite, deslocamento, ordem e ordenador) ou filtro irá retornar todos os registros.*

### **Listar Informações Basica de Todos os Sites**

   Retorna as informações básicas de todos os Sites cadastradas no sistema. Por padrão será retornado um limite máximo de 15 registros. Para retornar uma quantidade diferente, o limite deve ser enviado na requisição. Caso limite seja igual a 0 (zero) será retornado todos os registros. 

* **URL**

   ```http
   /interface/monitoring/host/simples HTTP1.0
   ```

* **Método:** `GET`

*  **Parâmetro**

    |NOME|TIPO|MÍNIMO|MÁXIMO|FORMATAÇÃO|OBRIGATÓRIO|DESCRIÇÃO|
    |----|:--:|:----:|:----:|:--------:|:---------:|---------|
    limite|Integer|-|-|-|Não|Limite máximo de registros a serem retornados.|
    deslocamento|Integer|-|-|-|Não|Quantos registros devem ser ignorados a partir do início.|
    ordem|String|-|-|-|Não|Registro por qual será ordenado os dados.|
    ordenador|String|-|-|-|Não|Indica se a ordenação será crescente ou decrescente(ASC OU DESC).|
    filtro|JSON|-|-|-|Não|Filtros por valor de deteminado atributo.|
    filtro.id|Integer|-|-|-|Não|Filtros por valor do ID da Forma de Pagamento.|
    filtro.nome|String|3|255|-|Não| Filtros por valor Nome da Forma de Pagamento.|

* **Resposta com Sucesso:**
  
    **Código:** 200 OK <br />
    **Conteúdo:**
    ```json
    {
        "total":1,
        "data":[
            {
                "id": 1,
                "nome": "site",
                "cidade_nome": "cidade",
                "cidade_uf": "uf"
            }
        ]
    }
    ```
 
* **Resposta com Erro:**

    **Código:** 401 UNAUTHORIZED <br />
    **Conteúdo:** `{ "DONT_HAVE_PERMISSION": "Você não tem permissão para acessar essa ação!" }`

* **Notas:**

  *Se não for passado nenhum parâmetro de paginação(limite, deslocamento, ordem e ordenador) ou filtro irá retornar todos os registros.*

### **Buscar Site**

   Busca os dados de um determinado Site pelo ID. 

* **URL**

   ```http
   /interface/monitoring/host/{id} HTTP1.0
   ```

* **Método:** `GET`

*  **Parâmetro**

    |NOME|TIPO|MÍNIMO|MÁXIMO|FORMATAÇÃO|OBRIGATÓRIO|DESCRIÇÃO|
    |----|:--:|:----:|:----:|:--------:|:---------:|---------|
    {id}|Integer|-|-|-|Sim|ID do Site, passado na URL.|

* **Resposta com Sucesso:**
  
    **Código:** 200 OK <br />
    **Conteúdo:**
    ```json
    {
        "id": 1,
        "nome": "site",
        "cidade_nome": "cidade",
        "cidade_uf": "uf",
        "peso": 0.1,
        "conf": "{}",
        "latitude": -1.123456,
        "longitude": -0.123456,
        "observacao": "{}"
    }
    ```
 
* **Resposta com Erro:**

    **Código:** 401 UNAUTHORIZED <br />
    **Conteúdo:** `{ "DONT_HAVE_PERMISSION": "Você não tem permissão para acessar essa ação!" }`

### **Buscar Site**

   Busca os dados de um determinado Site pelo ID. 

* **URL**

   ```http
   /interface/monitoring/host/{id} HTTP1.0
   ```

* **Método:** `GET`

*  **Parâmetro**

    |NOME|TIPO|MÍNIMO|MÁXIMO|FORMATAÇÃO|OBRIGATÓRIO|DESCRIÇÃO|
    |----|:--:|:----:|:----:|:--------:|:---------:|---------|
    {id}|Integer|-|-|-|Sim|ID do Site, passado na URL.|

* **Resposta com Sucesso:**
  
    **Código:** 200 OK <br />
    **Conteúdo:**
    ```json
    {
        "id": 1,
        "nome": "site",
        "cidade_nome": "cidade",
        "cidade_uf": "uf",
        "peso": 0.1,
        "conf": "{}",
        "latitude": -1.123456,
        "longitude": -0.123456,
        "observacao": "{}"
    }
    ```
 
* **Resposta com Erro:**

    **Código:** 401 UNAUTHORIZED <br />
    **Conteúdo:** `{ "DONT_HAVE_PERMISSION": "Você não tem permissão para acessar essa ação!" }`

### **Editar Site**

    Edita os dados de um Site pelo ID.

* **URL**

   ```http
   /interface/monitoring/host/{id} HTTP1.0
   ```

* **Método:** `PUT`

*  **Parâmetro**

    |NOME|TIPO|MÍNIMO|MÁXIMO|FORMATAÇÃO|OBRIGATÓRIO|DESCRIÇÃO|
    |----|:--:|:----:|:----:|:--------:|:---------:|---------|
    {id}|Integer|-|-|-|Sim|ID do Site, passado na URL.|
    nome|String|3|50|-|Sim|<_Descrição_>.|
    base_cidade_id|Integer|-|-|-|Sim|<_Descrição_>.|
    peso|Double|-|-|-|Sim|<_Descrição_>.|
    conf|Json|-|-|-|Não|<_Descrição_>.|
    latitude|Numeric|-|-|-|Sim|<_Descrição_>.|
    longitude|Numeric|-|-|-|Sim|<_Descrição_>.|
    observação|Json|-|-|-|Não|<_Descrição_>.|

* **Resposta com Sucesso:**
  
    **Código:** 200 OK <br />
    **Conteúdo:**
    ```json
    {
        "nome": "site"
    }
    ```
 
* **Resposta com Erro:**

    **Código:** 401 UNAUTHORIZED <br />
    **Conteúdo:** `{ "DONT_HAVE_PERMISSION": "Você não tem permissão para acessar essa ação!" }`

* **Notas:**

  *Passar somente os atributos que serão atualizados.*


### **Excluir Site**

    Exclui um Site pelo ID.

* **URL**

   ```http
   /interface/monitoring/host/{id} HTTP1.0
   ```

* **Método:** `DELETE`

*  **Parâmetro**

    |NOME|TIPO|MÍNIMO|MÁXIMO|FORMATAÇÃO|OBRIGATÓRIO|DESCRIÇÃO|
    |----|:--:|:----:|:----:|:--------:|:---------:|---------|
    {id}|Integer|-|-|-|Sim|ID do Site, passado na URL.|

* **Resposta com Sucesso:**
  
    **Código:** 204 NO CONTENT <br />
    **Conteúdo:**` `
 
* **Resposta com Erro:**

    **Código:** 401 UNAUTHORIZED <br />
    **Conteúdo:** `{ "DONT_HAVE_PERMISSION": "Você não tem permissão para acessar essa ação!" }`

* **Notas:**

  *Passar somente os atributos que serão atualizados.*
