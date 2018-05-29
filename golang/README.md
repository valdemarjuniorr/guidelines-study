# Estudos sobre a linguagem GoLang

## Sobre Pacotes(package)
- Organizar seu código.
- Habilita reusabilidade de código, permitindo usá-lo em outros pacotes.
- Ajuda no encapsulamento de código.
- Representa apenas um conceito.
- Pequeno e vários.
- Crie pacote para um propósito e deixe toda a lógica relacionada a esse propósito e encapsule dentro dele mesmo.

### Regras
- Pacotes estão dentro do diretório do workspace `$GOPATH/src`.
- É possível ter vários pacotes com o mesmo nome, contanto que em estrutura de pastas diferentes.
- Não é possível uma variável local que pertença apenas a um arquivo `.go`. O código é compartilhado no pacote inteiro.

## Idiomatic GoLang
### Espaços simples entre as frases, depois de ponto final(.) e comentários.
Certo:

`// Comentário um. Comentário dois.`

Errado:

`//Comentário um.  Comentário dois.`

Referência: [CL 20022](https://golang.org/cl/20022).

Fonte: https://dmitri.shuralyov.com/idiomatic-go#single-spaces-between-sentences

### Nome de variável de erro( Error variable naming )
Certo: 

```
// Package level exported error.
var ErrSomething = errors.New("something went wrong")

func main() {
	// Normally you call it just "err",
	result, err := doSomething()
	// and use err right away.

	// But if you want to give it a longer name, use "somethingError".
	var specificError error
	result, specificError = doSpecificThing()

	// ... use specificError later.
}
```
Errado:

```
var ErrorSomething = errors.New("something went wrong")
var SomethingErr = errors.New("something went wrong")
var SomethingError = errors.New("something went wrong")

func main() {
	var specificErr error
	result, specificErr = doSpecificThing()

	var errSpecific error
	result, errSpecific = doSpecificThing()

	var errorSpecific error
	result, errorSpecific = doSpecificThing()
}
```
Referência: https://talks.golang.org/2014/names.slide#14.

Fonte: https://dmitri.shuralyov.com/idiomatic-go#error-variable-naming

### Palavras com mais de uma letra maiúscula, todas as letras são minúsculas
Certo:

```
// Exported.
var OAuthEnabled bool
var GitHubToken string

// Unexported.
var oauthEnabled bool
var githubToken string
```

Errado:

```
// Unexported.
var oAuthEnabled bool
var gitHubToken string
```

Para constar como é feito em projetos Go, `oAuth` não é bonito.

Fonte: https://dmitri.shuralyov.com/idiomatic-go#for-brands-or-words-with-more-than-1-capital-letter-lowercase-all-letters

### Comentários feitos por humanos tem que ter espaço simples depois das barras
Certo: 

```
// Esse é um comentário feito
// por humanos.
```

Errado:

```
//Esse é um comentário feito
//por humanos.
```

NUNCA COMENTE CÓDIGO com a intenção de commitar. Caso seja extremamente necessário, não deve ter espaço depois das barras.

Referência: 

Fonte: https://dmitri.shuralyov.com/idiomatic-go#comments-for-humans-always-have-a-single-space-after-the-slashes

### Não use 'defer' se a legibilidade do código não melhorar

Às vezes usar defer pode deixar seu programa mais lento.

Referência: https://lk4d4.darth.io/posts/defer/

### Use a forma singular para nomes de repositório/diretório ( repo/folder )
Certo:

```
github.com/golang/example/hello
github.com/golang/example/outyet
golang.org/x/mobile/example/basic
golang.org/x/mobile/example/flappy
golang.org/x/image/...
github.com/shurcooL/tictactoe/player/bad
github.com/shurcooL/tictactoe/player/random
```

Errado:

```
github.com/golang/examples/hello
github.com/golang/examples/outyet
golang.org/x/mobile/examples/basic
golang.org/x/mobile/examples/flappy
golang.org/x/images/...
github.com/shurcooL/tictactoe/players/bad
github.com/shurcooL/tictactoe/players/random  
```

Note como `example`, `image`, `player` contêm muitos pacotes relacionados, mesmo assim usam a forma singular.

Fonte: https://dmitri.shuralyov.com/idiomatic-go#use-singular-form-for-collection-repo-folder-name

### Evite Receive Names não utilizados

Certo:

```
func (foo) method() {
	...
}
```

Errado:

```
func (f foo) method() {
	...
}
```

Se `f` não for utilizado. É mais legível, por que indica que o parâmetro não é utilizado dentro do método.

Fonte: https://dmitri.shuralyov.com/idiomatic-go#avoid-unused-method-receiver-names

### Verificar strings vazias
Certo: 

```
if s == "" {
	...
}
```

Errado:

```
if len(s) == 0 {
	...
}
```

Se verificar string vazias usando `len(s)` é OK para alguns usuários.
A primeira forma é mais legível, por que é obvio que `s` é uma string e não um slice.

Veja o comentário Russ Cox https://groups.google.com/forum/#!topic/golang-nuts/7Ks1iq2s7FA:

*** if I care about "is it this specific string" I tend to write s == "".***

###

Fonte: https://dmitri.shuralyov.com/idiomatic-go#empty-string-check


## Proverbios do GoLang

https://go-proverbs.github.io/

## Quotes
- ["If you took a working C/C++/Java function and translated that to Golang, it’s highly unlikely that would yield remotely decent Golang code."](https://medium.com/myntra-engineering/my-journey-with-golang-web-services-4d922a8c9897)