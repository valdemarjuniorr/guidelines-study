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



## Proverbios do GoLang

https://go-proverbs.github.io/

## Quotes
- ["If you took a working C/C++/Java function and translated that to Golang, it’s highly unlikely that would yield remotely decent Golang code."](https://medium.com/myntra-engineering/my-journey-with-golang-web-services-4d922a8c9897)