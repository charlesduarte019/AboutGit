**Title Arquive**
=============

## **Sumário**

* [Title1](#title1)
* [Title2](#title2)
	* [Adicionar Title2](#adicionar-title2)
 	* [Listar Todos os Title2](#listar-todos-os-title2)
 	* [Buscar Title2](#buscar-title2)
 	* [Editar Title2](#editar-title2)
 	* [Excluir Title2](#excluir-title2)

## **Title1**

   <_Descrição sobre o modulo_>

* **URL**

   ```http
   /api/v1/title1 HTTP1.0
   ```

* **Method**

    `GET` | `POST` | `DELETE` | `PUT`

*  **Parâmetro**

    |NOME|TIPO|MÍNIMO|MÁXIMO|FORMATAÇÃO|OBRIGATÓRIO|PERMISSÂO|DESCRIÇÃO|
    |----|:--:|:----:|:----:|:--------:|:---------:|:-------:|---------|
    usuario|String|-|-|-|Não|Não|Nome do usuário.|
    senha|String|-|-|-|Não|Não|Senha do usuário a ser testada.|

*  **Requisição**

    ```json
    {
    	"usuario": "usuario",
    	"senha": "usuario123"
    }
    ```
* **Resposta com Sucesso:**
  
  * **Code:** 200 <br />
    **Content:**
    ```json
    {
    	"id": 12
    }
    ```
 
* **Resposta com Erro:**

  * **Code:** 404 NO CONTENT <br />
    **Content:** `{ error : "Email Invalid" }`

  OU

  * **Code:** 401 UNAUTHORIZED <br />
    **Content:** `{ error : "Log in" }`

* **Notas:**

  <_Caso tenha alguma observação sobre o modulo._>
