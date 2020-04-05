# Exemplo de API
  
Este exemplo de documentação APIRest/RestFull Usando Swagger:
  
```
# this is an example of the Uber API
# as a demonstration of an API spec in YAML
swagger: '2.0'
info:
  title: Lista de Usuários
  description: Essa API provê o acesso aos usuários do sistema
  contact:
    name: Wesley Moizaque
    email: Wesleymsan14@gmail.com
  version: "1.0.0"
# the domain of the service
# host: api.meusite.com
# array of all schemes that your API supports
schemes:
  - https
# will be prefixed to all paths
# basePath: /v1
produces:
  - application/json
paths:
  /users:
    get:
      summary: Lista dos Usuários
      description: |
        Este endpoint retorna **todos** usuários cadastrados no sistema.
      tags:
        - Users
      responses:
        200:
          description: Uma lista(Array) de usuários
          schema:
            type: array
            items:
              $ref: '#/definitions/User'
        default:
            description: Erro inesperado
            schema:
              $ref: '#/definitions/Error'
    post:
      summary: Cria um usuário
      description: |
        Este endpoint cria um usuário no sistema.
      parameters: 
        - name: user
          in: body
          description: ID do usuário
          required: true
          schema:
            $ref: '#/definitions/User'
      tags:
        - Users
      responses:
        201:
          description: Usuário cadastrado com sucesso!
          schema:
              $ref: '#/definitions/User'
        default:
            description: Erro inesperado
            schema:
              $ref: '#/definitions/Error'
    put:
      summary: Atualiza um usuário
      description: |
        Este endpoint atualiza um usuário no sistema. O id do usuário deve ser imformado.
      parameters: 
        - name: user
          in: body
          description: Usuário
          required: true
          schema:
            $ref: '#/definitions/User'
      tags:
        - Users
      responses:
        200:
          description: Usuário atualizado com sucesso.
          schema:
              $ref: '#/definitions/User'
        404:
          description: Usuário não encontrado. Lembre-se de informar o ID.
        default:
          description: Erro inesperado
          schema:
            $ref: '#/definitions/Error'
        
  /users/{id}:
    get:
      summary: Mostra apenas um usuário
      description: |
        Este endpoint retorna **apenas** usuários à qual foi informado o id.
      parameters: 
        - name: id
          in: path
          description: ID do usuário
          required: true
          type: integer
      tags:
        - Users
      responses:
        200:
          description: Usuário encontrado!
          schema:
            $ref: '#/definitions/User'
        default:
          description: Erro inesperado
          schema:
            $ref: '#/definitions/Error'
    delete:
      summary: Apagar um usuário
      description: |
        Este endpoint apaga usuários à qual foi informado o **id**.
      parameters: 
        - name: id
          in: path
          description: ID do usuário
          required: true
          type: integer
      tags:
        - Users
      responses:
        200:
          description: Usuário excluído com sucesso!
        404:
          description: Usuário não encontrado.
        410:
          description: Usuário inexistente.
        default:
          description: Erro inesperado
          schema:
            $ref: '#/definitions/Error'
definitions:
  User:
    type: object
    required: 
      - email
      - name
    properties:
      id:
        type: integer
        description: Código do usuário
      email:
        type: string
        description: Email do usuário
      name:
        type: string
        description: Nome do usuário
      
  Error:
    type: object
    properties:
      code:
        type: integer
        format: int32
      message:
        type: string
# Added by API Auto Mocking Plugin
host: virtserver.swaggerhub.com
basePath: /wesleymsan/ListaDeUsuarios1/1.0.0
```
