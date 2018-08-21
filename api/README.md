# api-guidelines-study
Guia criado basedo em estudos de como criar APIs

## Convenções usadas neste documento
As palavras-chave de nível de exigência **"PRECISA"**, **"NÃO PRECISA"**, **"OBRIGATÓRIO"**, **"DEVERÁ"**, **"NÃO DEVERÁ"**, **"DEVE"**, **"NÃO DEVE"**, **"RECOMENDADO"**, **"PODE"** e **"OPCIONAL"** usadas serão interpretadas conforme descrito no RFC 2119.

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
* Os recursos retornados **deverá** ser os mesmos dos mapeados no caminho da URL.
* O corpo da requisição **deverá** estar vazio.
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
* `Create` **deve** implementar o método HTTP `POST`.
* A mensagem da requisição deveria ter o `parent` que especifica o nome do recurso pai, onde o novo recurso será criado.
* Todos os demais campos da requisição, **poderiam** ser mapeados nos parâmetros da URL.
* A requisição **deveria** conter o nome do campo `<recurso>_id` para permitir que o cliente escolha por id. Esse campo **deve** estar nos parâmetros da URL.
* O recurso retornado **poderia** estar no corpo da resposta.

O método `Create` **deveria** tratar o código de erro `ALREADY_EXISTS`.

### Update
O método `Update` recebe uma messagem contendo um recurso com nenhum ou mais parâmetros. O recurso específico e suas propriedades serão atualizadas e retornadas.

Requisitos: 
* O método `Update` deveria suportar parcialmente atualização uasndo HTTP `PATCH`, com o campo `FieldMask` nomeado `update_mask`.
* Se o método `Update` só suportar atualização do recurso inteiro, **deve** usando método http `PUT`.
* A requisição **deve** conter o recurso que irá ser atualizado.
* A resposta da requisição **deve** ser o recurso atualizado.

O método `Update` **deveria** tratar o erro de `NOT_FOUND` no caso de um recurso inexistente.

### Delete
O método `Delete` recebe o nome do recurso com nenhum ou vários parâmetros, que deleta ou marca para deleção um específico recurso.
A API **não deveria** confiar nas informações retornadas de um método `Delete` e que também **não deve** ser chamado repetidamente.

Requisitos:
* O método `Delete` **deve** implementar o método HTTP `DELETE`.
* A requisição da mensagem recebida, para o recurso específico, **deverá** ser mapeada no caminho da URL.
* O corpo da requisição **deverá** estar vazio.
* Se o método `Delete` imediatamente remover o recurso, **deverá** retornar um corpo vazio.
* Se o método `Delete` inicializar uma operação longa de deleção, **deverá** retornar o tempo dessa operação.
* Se o método `Delete` apenas marcar o recurso como será deletado, **deverá** retornar o recurso atualizado.

O método `Delete` **deveria** tratar o erro de `NOT_FOUND` no caso de um recurso inexistente.

----

### Errors

Every API MUST use the appropriate HTTP Status Code to communicate the result of a request operation.
Every API designer, implementer and consumer MUST understand the semantic of the HTTP Status Code being used.
At a minimum everyone MUST be familiar with the semantics of "Common" HTTP Status Codes.

Here's some usefull links :

- [Status Codes on W3c](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html)
- [Status Codes on Wikipedia](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes)
- [Status Codes on Mozilla](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status)
- [Status Codes explained](https://github.com/for-GET/know-your-http-well/blob/master/status-codes.md)
- [Choosing a HTTP Status Code](https://www.codetinkerer.com/2015/12/04/choosing-an-http-status-code.html)

#### Status Codes Explained

Here's a explanation about the most common used Status Codes.
This section text are all from [Status Codes explained](https://github.com/for-GET/know-your-http-well/blob/master/status-codes.md), and adapted for this guideline.

##### Status 1xx - Informational

The 1xx Status Codes indicates an interim response for communicating connection status or request progress prior to completing the requested action and sending a final response.

|   Code   |   Status   |   Description   |
|----------|----------|:-------------:|
| 100 | Continue | Indicates that a initial part of the request was received and not rejected by the server |
| 101 | Switching Protocols	| Indicates that the server understands and is willing to comply with the client's request, via the Upgrade header field, for a change in the application protocol being used on this connection |
| 102 | Processing | Is an interim response used to inform the client that the server has accepted the complete request, but has not yet completed it |

##### Status 2xx - Successful

The 2xx Status Codes indicates that the request made are successful, accepted, received or understood.
You MUST NOT use 2xx status to return any kind of error.

|   Code   |   Status   |   Description   |
|----------|----------|:-------------:|
| 200 | Ok | Indicates that the request has succeeded |
| 201 | Created | Indicates that the request has been fulfilled and has resulted in one or more new resources being created |
| 202 | Accepted | Indicates that the request has been accepted for processing, but the processing has not been completed |
| 203 | Non-Authoritative Information | Indicates that the request was successful but the enclosed payload has been modified from that of the origin server's 200 (OK) response by a transforming proxy |
| 204 | No Content | Indicates that the server has successfuly fulfilled the request and that there is no additional content to send in the response payload body |
| 205 | Reset Content | Indicates that the server has fulfilled the request and desires that the user agent reset the "document view", which caused the request to be sent, to its original state as received from the origin server |
| 206 | Partial Content	| Indicates that the server is successfully fulfilling a range request for the target resource by transferring one or more parts of the selected representation that correspond to the satisfiable ranges found in the requests's Range header field |
| 207 | Multi-Status | Provides status for multiple independent operations |
| 226 | IM Used | The server has fulfilled a GET request for the resource, and the response is a representation of the result of one or more instance-manipulations applied to the current instance |

##### Status 3xx - Redirection

The 3xx Status Codes indicates that further action needs to be taken by the user agent in order to fulfill the request.

|   Code   |   Status   |   Description   |
|----------|----------|:-------------:|
| 300 | Multiple Choices | Indicates that the target resource has more than one representation, each with its own more specific identifier, and information about the alternatives is being provided so that the user (or user agent) can select a preferred representation by redirecting its request to one or more of those identifiers |
| 301 | Moved Permanently | Indicates that the target resource has been assigned a new permanent URI and any future references to this resource ought to use one of the enclosed URIs |
| 302 | Found | Indicates that the target resource resides temporarily under a different URI |
| 303 | See Other | Indicates that the server is redirecting the user agent to a different resource, as indicated by a URI in the Location header field, that is intended to provide an indirect response to the original request |
| 304 | Not Modified | Indicates that a conditional GET request has been received and would have resulted in a 200 (OK) response if it were not for the fact that the condition has evaluated to false |
| 305 | Use Proxy | __Deprecated__ |
| 306 | | __Unused__ |
| 307 | Temporary Redirect | Indicates that the target resource resides temporarily under a different URI and the user agent MUST NOT change the request method if it performs an automatic redirection to that URI |
| 308 | Permanent Redirect | The target resource has been assigned a new permanent URI and any future references to this resource outght to use one of the enclosed URIs. [...] This status code is similar to 301 Moved Permanently (Section 7.3.2 of rfc7231), except that it does not allow rewriting the request method from POST to GET |

##### Status 4xx - Client Errors

The 4xx Status Codes indicates that the client seems to have erred.

|   Code   |   Status   |   Description   |
|----------|----------|:-------------:|
| 400 | Bad Request | Indicates that the server cannot or will not process the request because the received syntax is invalid, nonsensical, or exceeds some limitation on what the server is willing to process |
| 401 | Unauthorized | Indicates that the request has not been applied because it lacks valid authentication credentials for the target resource |
| 402 | Payment Required | __Reserved__ |
| 403 | Forbidden | Indicates that the server understood the request but refuses to authorize it |
| 404 | Not Found | Indicates that the origin server did not find a current representation for the target resource or is not willing to disclose that one exists |
| 405 | Method Not Allowed | Indicates that the method specified in the request-line is known by the origin server but not supported by the target resource |
| 406 | Not Acceptable | Indicates that the target resource does not have a current representation that would be acceptable to the user agent, according to the proactive negotiation header fields received in the request, and the server is unwilling to supply a default representation |
| 407 | Proxy Authentication Required | Is similar to 401 (Unauthorized), but indicates that the client needs to authenticate itself in order to use a proxy |
| 408 | Request Timeout | Indicates that the server did not receive a complete request message within the time that it was prepared to wait |
| 409 | Conflict | Indicates that the request could not be completed due to a conflict with the current state of the resource |
| 410 | Gone | Indicates that access to the target resource is no longer available at the origin server and that this condition is likely to be permanent |
| 411 | Length Required | Indicates that the server refuses to accept the request without a defined Content-Length |
| 412 | Precondition Failed | Indicates that one or more preconditions given in the request header fields evaluated to false when tested on the server |
| 413 | Payload Too Large | Indicates that the server is refusing to process a request because the request payload is larger than the server is willing or able to process |
| 414 | URI Too Long | Indicates that the server is refusing to service the request because the request-target is longer than the server is willing to interpret |
| 415 | Unsupported Media Type | Indicates that the origin server is refusing to service the request because the payload is in a format not supported by the target resource for this method |
| 416 | Range Not Satisfiable | Indicates that none of the ranges in the request's Range header field overlap the current extent of the selected resource or that the set of ranges requested has been rejected due to invalid ranges or an excessive request of small or overlapping ranges |
| 417 | Expectation Failed | Indicates that the expectation given in the request's Expect header field could not be met by at least one of the inbound servers |
| 418 | I'm a teapot | Any attempt to brew coffee with a teapot should result in the error code 418 I'm a teapot |
| 422 | Unprocessable Entity | The server understands the content type of the request entity (hence a 415 Unsupported Media Type status code is inappropriate), and the syntax of the request entity is correct (thus a 400 Bad Request status code is inappropriate) but was unable to process the contained instructions |
| 423 | Locked | Indicates that the source or destination resource of a method is locked |
| 424 | Failed Dependency | Indicates that the method could not be performed on the resource because the requested action depended on another action and that action failed |
| 426 | Upgrade Required | Indicates that the server refuses to perform the request using the current protocol but might be willing to do so after the client upgrades to a different protocol |
| 428 | Precondition Required | Indicates that the origin server requires the request to be conditional |
| 429 | Too Many Requests | Indicates that the user has sent too many requests in a given amount of time ("rate limiting") |
| 431 | Request Header Fields Too Large | Indicates that the server is unwilling to process the request because its header fields are too large |
| 451 | Unavailable For Legal Reasons | This status code indicates that the server is denying access to the resource in response to a legal demand |

##### Status 5xx - Server Errors

The 5xx Status Codes indicates that the server is aware that it has erred or is incapable of performing the requested method.
Business errors MUST NOT be returned with 5xx Status Codes.

|   Code   |   Status   |   Description   |
|----------|----------|:-------------:|
| 500 | Internal Server Error | Indicates that the server encountered an unexpected condition that prevented it from fulfilling the request |
| 501 | Not Implemented | Indicates that the server does not support the functionality required to fulfill the request |
| 502 | Bad Gateway | Indicates that the server, while acting as a gateway or proxy, received an invalid response from an inbound server it accessed while attempting to fulfill the request |
| 503 | Service Unavailable | Indicates that the server is currently unable to handle the request due to a temporary overload or scheduled maintenance, which will likely be alleviated after some delay |
| 504 | Gateway Time-out | Indicates that the server, while acting as a gateway or proxy, did not receive a timely response from an upstream server it needed to access in order to complete the request |
| 505 | HTTP Version Not Supported | Indicates that the server does not support, or refuses to support, the protocol version that was used in the request message |
| 506 | Variant Also Negotiates	| Indicates that the server has an internal configuration error: the chosen variant resource is configured to engage in transparent content negotiation itself, and is therefore not a proper end point in the negotiation process |
| 507 | Insufficient Storage | Means the method could not be performed on the resource because the server is unable to store the representation needed to successfully complete the request |
| 511 | Network Authentication Required | Indicates that the client needs to authenticate to gain network access |
