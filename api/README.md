# api-guidelines-study
Guia criado basedo em estudos de como criar APIs 

**Recursos**

 Uma API baseada em recurso(simples e conjunto):
- Um conjunto contém uma lista de recursos do mesmo tipo. Por exemplo, um usuário tem um conjunto de contatos.
- Um recurso tem algum estado e zero ou mais sub-recursos. 
- Cada sub-recurso pode ser um recurso simples ou um recurso de um conjunto.

Por exemplo, a API do Gmail tem um conjunto de usuários, cada usuário tem um conjunto de mensagens, um conjunto de conversas, um conjunto de marcadores, um recurso de perfil e vários recursos de configuração.

A característica principal de uma API orientada por recursos é que ela enfatiza os recursos (modelo de dados) sobre os métodos realizados nos recursos (funcionalidade).

Exemplos da API do Gmail usando conjuntos e recursos

um conjunto de usuários: `users/*`. Cada usuário tem os seguintes recursos:
* Um conjunto de mensagens: `users/*/messages/*`
* Um conjunto de conversas: `users/*/threads/*`
* Um conjunto de marcadores: `users/*/labels/*`

# Nome dos recursos
Recursos são chamados de entidades. Cada recurso precisa ter um nome exclusivo. O nome do recurso é organizado hierarquicamente usando códigos do conjunto e códigos de recursos, separados por barras. Se um recurso contiver um sub-recurso, o nome dele será formado por meio da especificação do nome do recurso pai seguido pelo código do sub-recurso, separado por barras novamente.

Ex.:
`/users/{userID}/messages/{messageID}/`

Termos muito gerais devem ser evitados ou qualificados. Por exemplo, 
rowValues tem preferência sobre values. Os seguintes termos devem ser evitados sem qualificação:
- elements
- entries
- instances
- items
- objects
- resources
- types
- values

## Nome dos recursos VS URL
Nome do recurso e a url não são a mesma coisa. Diferentes recurso pode ser expostos com diferentes versões, protocolos e endpoints, mas com a mesma URL. 

`/v1/users/*/messages/*`

O nome de um recurso deve ser tratado como string e gerenciado como caminho de pastas normal e não suportando % encoding.

Para definições de recursos o primeiro campo deveria ser tratado como string e o nome do recurso deveria ter como sufixo name.
`first_name, display_name`

`"/v1/{name=shelves/*/books/*}"`

## Métodos Padrão
Na API do google existem métodos padrões que são o `List`, `Get`, `Create`, `Update` e `Delete`. A utilização de métodos padrões reduz a complexidade e aumenta a consistência, tornando mais fácil de aprender e usar.

A tabela abaixo mostra o mapa de métodos padrões para HTTP

| Standard Method | 	HTTP Mapping | 	HTTP Request Body |	HTTP Response Body |
|-----------------|:--------------:|-------------------:|-------------------:|
| List | GET <collection URL> | N/A | Resource* list|
| Get | GET <resource URL> | N/A | Resource*|
| Create | POST <collection URL> | Resource | Resource*|
| Update | PUT ou PATCH <resource URL> | Resource | Resource*|
| Delete | DELETE <resource URL> | N/A | google.protobuf.Empty**|

### List

O método `List` tem o nome da coleção e nenhum ou vários parâmetros e retorna uma lista de recursos que batem com as entradas.

É utilizada para pesquisar recursos. Para casos menos especificos poderia ser utilizado o método customizado como `Search`

Um `Batch get`(Quando uma consulta tem vários IDs de recursos e retorna recursos específicos para esses IDs), deveria ser implementado um `BatchGet` ao invés de apenas `List`.

Requisitos:
* `List` tem que implementar o método HTTP `GET`.
* Os recursos retornados devem ser os mesmos dos mapeados no caminho da URL.
* O corpo da requisição deve estar vazio.
* A resposta deve conter a lista de recursos com metadados opcionais

### Get

Método `Get` tem o nome do recurso, com nenhum ou vários parâmetros, e retorna o recurso específico.

Requisitos: 
* `Get` tem que implementar o método HTTP `GET`.
* Os filtros da requisição do recurso a ser recuperados, deveriam ser mapeados na URL.
* Os recursos retornados devem ser os mesmos dos mapeados no caminho da URL.
* O corpo da requisição deve estar vazio.
* O recurso retornado deve ser mapeado no corpo da resposta da requisição.

Exemplo:

```
// Note the URL template variable which captures the multi-segment resource
    // name of the requested book, such as "shelves/shelf1/books/book2"
    get: "/v1/{name=shelves/*/books/*}"
```

### Create
O método `Create` tem o nome do recurso pai, um recurso, e nenhum ou vários parâmetros. Cria um novo recurso do tipo do recurso pai `parent` especificado e retorna esse recurso criado.

Requisitos: 
* `Create` tem que implementar o método HTTP `POST`.
* A mensagem da requisição deveria ter o `parent` que especifica o nome do recurso pai, onde o novo recurso será criado.
* Todos os demais campos da requisição, **poderiam** ser mapeados nos parâmetros da URL.
* A requisição **deveria** conter o nome do campo `<recurso>_id` para permitir que o cliente escolha por id. Esse campo **deve** estar nos parâmetros da URL.
* O recurso retornado **poderia** estar no corpo da resposta.
