# Estudo sobre JWT
Guia criado sobre estudos feitos sobre JWT.

## Convenções usadas neste documento
As palavras-chave de nível de exigência **"PRECISA"**, **"NÃO PRECISA"**, **"OBRIGATÓRIO"**, **"DEVERÁ"**, **"NÃO DEVERÁ"**, **"DEVE"**, **"NÃO DEVE"**, **"RECOMENDADO"**, **"PODE"** e **"OPCIONAL"** usadas serão interpretadas conforme descrito no RFC 2119.

## Sobre JWT(JSON Web Token)
JWT é um padrão aberto((RFC 7519)[https://tools.ietf.org/html/rfc7519] que define de forma compacta e contida de transmitir, seguramente, mensagens entre duas partes com JSON. A informação é verificada e confiável, por que é assinada digitalmente.

### Quando usar?
Cenários que o JWT é útil utilizar:
- Autorização:
È o cenário mais comum. Uma vez logado, todas os requests subsequentes irão incluir JWT. Single Sign On usa bastante por que é pequeno e gasta poucos recursos de rede e é facilmente usado através de diferentes domínios.

- Troca de informação:
JWT é uma boa forma de trocar informações seguras entre partes, por que JWT pode ser assinado usando, por exemplo (public/private key pairs)[https://en.wikipedia.org/wiki/Public-key_cryptography].

## Estrutura 
De forma simplificada, JWT consiste em três partes separadas por ponto(.):
- Header
- Payload
- Signature

Ex.: `xxxxx.yyyyy.zzzzz`

### Header
O **Header** consiste em duas partes: O tipo de token, que é JWT, e o algoritmo hash usado, como HMAC SHA256 or RSA.
Ex.:
```json
{
  "alg": "HS256",
  "typ": "JWT"
}
```
Esse JSON é `Base64Url`, codificado para formar a primeira parte do JWT.

### Payload
A segunda parte do JWT é o **Payload**, que contêm as afirmações(Claims) sobre uma entidade. Existem três tipos de afirmações(Claims): 

- Registered
São coleções de afirmações pré-definidas que não são obrigatórias, mas recomendadas, por prover um set de afirmações(Claims) interoperáveis e úteis.

Algum deles são: **iss** (issuer), **exp** (expiration time), **sub** (subject), **aud** (audience).

_Note que os nomes das afirmações(claim) são apenas três caracteres como JWT tem o significado de ser compacto._

- Public
Esses podem ser adicionados ao seu critério, mas para evitar colições, eles **DEVERIAM** ser definidos no (IANA JSON Web Token Registry)[https://www.iana.org/assignments/jwt/jwt.xhtml] ou ser definida como URI que contêm namespaces para evitar colições.

- Private 
São afirmações(Claims) criados para compartilhar informações entre as partes que concordaram em usá-las e não são nem _registered_ ou _public_.

Ex.: 
```json
{
  "sub": "1234567890",
  "name": "John Doe",
  "admin": true
}
```
Esse JSON é `Base64Url`, codificado para formar a segunda parte do JWT.

### Signature
Para criar uma assinatura você precisa do **Header** e **Payload** codificados, o secret, o algoritmo especifícado no **Header** e assiná-los.

Por exemplo, se quiser usar o algoritmo _HMAC SHA256_, a assinatura será criada da seguinte forma:
```HMACSHA256(
  base64UrlEncode(header) + "." +
  base64UrlEncode(payload),
  secret)
```

A assinatura é usado para verificar se a mensagem não foi alterada no meio do caminho. No caso de tokens assinados, verifica também se vocẽ é realmente quem você está dizendo quem é.

O output são três strings Base64-URL separados por pontos e que pode ser passado facilmente nos ambientes HTTP.

```
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c
```