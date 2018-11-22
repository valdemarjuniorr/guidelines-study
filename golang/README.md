# Estudos sobre a linguagem GoLang

## Sobre Pacotes(package)
- Organizar seu código.
- Habilita reusabilidade de código, permitindo usá-lo em outros pacotes.
- Ajuda no encapsulamento de código.
- Representa apenas um conceito.
- Pequeno e vários.
- Crie pacote para um propósito e deixe toda a lógica relacionada a esse propósito e encapsule dentro dele mesmo.
- Use apenas letras minúsculas. Não use underline ou camelCase. Ex.: Não use `httpReader` ou `http_reader`.
- Não use plural. Ex.: `httputils`.

### Regras
- Pacotes estão dentro do diretório do workspace `$GOPATH/src`.
- É possível ter vários pacotes com o mesmo nome, contanto que em estrutura de pastas diferentes.
- Não é possível uma variável local que pertença apenas a um arquivo `.go`. O código é compartilhado no pacote inteiro.

### Boas práticas
- Elegante e simples.
- Óbvio apenas vendo o nome do pacote.
- Desenvolva o pacote internamente, mas projete para ser reutilizado algum dia.
- Considere mais utilizar pacotes com arquivos `_test.go`.
- Faça parecido com a biblioteca padrão ou pacotes de projetos grandes.

## Nomes são importantes

### Nomes
- Legibilidade é a definição de um bom código.
- Bons nomes são:  
 - Críticos para legibilidade.
 - Consistente ( fácil de advinhar ).
 - Pequeno ( fácil da digitar ).
 - Preciso ( fácil de entender ).

 Fonte: https://talks.golang.org/2014/names.slide#3

### A Rule of Thumbs

 Quanto maior a distância entre a declaração e o uso de uma variável, maior o nome deve ser.

### Use MixedCase
 - Nomes em GoLang deve usar MixedCase.
 - Não use nomes com underscore (_).
 - Acrônimos devem ser todos capitalizados. Ex.: `ServerHTTP`, `IDProcessor`, `ThreadID`.

### Variáveis locais
- Mantenham elas pequenas. Nomes grandes obscore o que o código faz.
- A combinação de variáveis/Types deveria usar nomes curtos:

```
Prefer i to index. 
Prefer r to reader. 
Prefer b to buffer.
```
- Evite nomes redundantes, dando contexto:
 - Prefira `count` a `runeCount` dentro de uma função chamada `RuneCount`.
 - Preria `ok` a `keyInMap`:
 `v, ok := m[k]`
 Nomes longos ajudam em funções muito grandes ou com muitas variáveis, mas isso é, frequentemente, um sinal que esse código deveria ser refatorado.

 Fonte: https://talks.golang.org/2014/names.slide#6

 RUIM: 
 ```
 func RuneCount(buffer []byte) int {
    runeCount := 0
    for index := 0; index < len(buffer); {
        if buffer[index] < RuneSelf {
            index++
        } else {
            _, size := DecodeRune(buffer[index:])
            index += size
        }
        runeCount++
    }
    return runeCount
}
 ```

BOM: 
```
func RuneCount(b []byte) int {
    count := 0
    for i := 0; i < len(b); {
        if b[i] < RuneSelf {
            i++
        } else {
            _, n := DecodeRune(b[i:])
            i += n
        }
        count++
    }
    return count
}
```

### Parâmetros
Parâmetros das funções são como variáveis locais, mas elas servem como documentação. 
- Quando os tipos são descritivos, eles deveriam ser curtas:
```
func AfterFunc(d Duration, f func()) *Timer

func Escape(w io.Writer, s []byte)
```

- Quando os tipos são mais ambíguos, os nomes devem servir como documentação:
```
func Unix(sec, nsec int64) Time

func HasPrefix(s, prefix []byte) bool
```

Fonte: https://talks.golang.org/2014/names.slide#9

### Return values
Return values deveriam ser nomeados apenas para melhorar a documentação.

```
func Copy(dst Writer, src Reader) (written int64, err error)

func ScanBytes(data []byte, atEOF bool) (advance int, token []byte, err error)
```

Fonte: https://talks.golang.org/2014/names.slide#10

### Receivers
Por convenção eles são uma ou dois caracteres. Os nomes devem ser consistentes. Não use `r` e em outro método use `rdr`.

```
func (b *Buffer) Read(p []byte) (n int, err error)

func (sh serverHandler) ServeHTTP(rw ResponseWriter, req *Request)

func (r Rectangle) Size() Point
```

Fonte: https://talks.golang.org/2014/names.slide#11  

### Nome exportados de pacotes
Nomes exportados de pacotes são qualificados pelo nome do pacote. Lembre-se disso ao criar variáveis, constantes, funções e tipos exportáveis.

Por isso existe:
`bytes.Buffer`, `strings.Reader` e não `bytes.ByteBuffer`, `strings.StringReader`

Fonte: https://talks.golang.org/2014/names.slide#12

### Erros
Tipos de erro deveria vir em forma de `FooError`:
```
type ExitError struct {
    ...
}
```

Nomes de variáveis de erro deveria vir em foma de `ErrFoo`:
```
var ErrFormat = errors.New("image: unknown format")
```

Fonte: https://talks.golang.org/2014/names.slide#14

### Nome de pacotes

Escolha nomes de pacotes que dão significado aos nomes exportados.
Evite nomes como `util`, `common` e etc.

Fonte: https://talks.golang.org/2014/names.slide#15

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

> if I care about "is it this specific string" I tend to write s == "".

Fonte: https://dmitri.shuralyov.com/idiomatic-go#empty-string-check

## Sobre Errors

### Tratamento de erros comuns em Go: 

```
if err != nil {
    return err
}
```
Se Go tivesse exceptions: 
```
func doSomething() {
    foo()
    bar()
    baz()
}
```
Mas como é realmente escrito em Go:
```
func doSomething() error {
    if err := foo(); err != nil {
        return err
    }
    if err := bar(); err != nil {
        return err
    }
    if err := baz(); err != nil {
        return err
    }
    return nil
}
```
E dessa forma é boa por que, mesmo?
- Erros são importantes.
- Pode influenciar no fluxo da aplicação.
- Nós perdermos muito tempo procurando por erros.
- Boas mensagens de erro, podem salvar dias de trabalho.
- Errors acontecem o tempo todo.
- Expliciticidade favorece legibilidade

Fonte: https://rogpeppe.neocities.org/error-loving-talk/index.html#5

### Panic!
Na verdade Go tem exceções, reservadas para situações exceptionais:
- Quando um erro realmente não deveria acontecer.
- Erros de inicialização.
- Broken internal [invariants](https://en.wikipedia.org/wiki/Invariant_(computer_science)) 

### Logs
A utilização de logs: 
- Quando quiser registrar o erro e continuar o fluxo.
- Geralmente utilizado em lógica de alto nível.

## Proverbios do GoLang

https://go-proverbs.github.io/

## Quotes
- ["If you took a working C/C++/Java function and translated that to Golang, it’s highly unlikely that would yield remotely decent Golang code."](https://medium.com/myntra-engineering/my-journey-with-golang-web-services-4d922a8c9897)

- Main() responsibility is to pull as much information from the environment to bootstrap the running program into working correctly.