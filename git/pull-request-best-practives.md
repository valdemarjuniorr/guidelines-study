# Guideline de code review e pull request:

###
 **Antes de abrir o PR ou quando estiver fazendo o CR, execute um checklist com todos itens abaixo.**
 **Se o PR não atender algum dos requisitos definidos neste guideline, ele não pode ser mergeado.**

 - Se alterar alguma SQL, colocar a query executada e o resultado em texto do explain plan no PR;
 - Se adicionar campo ou entidade, adicionar junto o SQL para alteração do banco;
 - Ter pelo menos um +1 de algum Ownership no PR;
 - Se o PR e CR for do mesmo ownership, além de ter um CR do ownership é preciso ter pelo menos um CR de outro time;
 - Se o PR for feito em par, o par não pode dar +1.
 - A descrição do pull request deve contextualizar o problema de negócio e técnico. Explicar a solução adotada, deixando bem claro porque a alteração esta sendo feita.
 - O Pull request só pode ter um objetivo, se tiver mais de um objetivo, deve ser quebrado em mais PRs.
 - Se alterar alguma interface, colocar um print do antes e depois.
 - Se criar uma interface, colocar um print do mockup e um da tela.
 - O Pull request não pode ser mergeado se tiver algum -1. Todos comentarios devem ser respondidos ou resolvidos.

# O que você deve avaliar em um Pull Request?

### Design

- O código segue boas práticas, como [Clean Code](https://de.wikipedia.org/wiki/Clean_Code), [DRY](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself) e [SOLID](https://en.wikipedia.org/wiki/SOLID_(object-oriented_design))?
- O código segue as convenções de código e arquitetura estabelecida pelo time?
- O código segue as convenções da linguagem? (Exemplo para Java: [Java Code Conventions](http://www.oracle.com/technetwork/java/codeconventions-150003.pdf),[Google Java Style](https://google.github.io/styleguide/javaguide.html))
- O código está com a abstração correta? Se estiver utilizando herança, está utilizando ela corretamente?
- O código está no lugar correto?
- Quando existe mais de um padrão, o novo código está seguindo o padrão atual? O código está migrando para o padrão correto ou seguindo o padrão antigo?
- O novo código não poderia reaproveitar código já existente? Está introduzindo código duplicado? Não poderia ser refatorado para um padrão reutilizável?
- O código pode estar introduzindo problemas de segurança para a aplicação?
- O código está adicionando funcionalidades que ainda não são necessárias? O código não pode ser simplificado? KISS e YAGNI ([Yagni - Martin Fowler](http://martinfowler.com/bliki/Yagni.html),[KISS and YAGNI - Coding Horror](http://blog.codinghorror.com/kiss-and-yagni/))
- Existem códigos não utilizados que poderiam ser removidos?
- Quando adicionado uma nova dependência, realmente é necessário?
- Exceções estão sendo tratadas corretamente?
- Se foi criada uma nova dependência com um serviço externo, foi tomado o cuidado necessário para que uma eventual queda, lentidão ou mal-funcionamento do serviço externo não afete o sistema dependente?

#### Java

- O código usa interfaces desnecessariamente? (com apenas uma implementação chamada ``*impl``) (ver [Yagni](http://martinfowler.com/bliki/Yagni.html), ver [InterfaceImplementationPair](https://martinfowler.com/bliki/InterfaceImplementationPair.html)). Interfaces desnecessárias deixam mais difícil a navegação entre as classes do projeto, significam mais arquivos para serem compilados e invalidam o feedback imediato dado por deduzir quando uma classe realmente tem duas implementações. Um exemplo de quando faz sentido usar interface? Quando implementando o *strategy pattern*. Sempre é possível adicionar a interface depois, quando for necessária.
- O código usa classes abstratas? __Via de regra__ prefira composição sobre herança. Herança quebra encapsulamento e deixa o código menos flexível. Ver https://www.javaworld.com/article/2076012/core-java/a-conversation-with-james-gosling.html e http://wiki.c2.com/?InheritanceBreaksEncapsulation.
  - Por consequência, evite subclasses. Exceções: *Exception*s, interface com bibliotecas externas (como comandos do Hystrix).
  - Especialmente, evite o *template method pattern*, pois ele dificulta ainda mais o entendimento, causando uma sensação de *vai-e-volta* ao tentar ler uma classe.
- Como as técnicas desaconselhadas acima (que não implicam código ruim por si só), evite código que *induza* a problemas. Prefira código que encoraje flexibilidade.

### Performance

- O código pode estar introduzindo problemas de performance?
- O código utiliza as estruturas de dados corretas para aquele cenário?
- O código realiza muitas consultas custosas ao banco de dados?

### Legibilidade e Manutenibilidade

- Os nomes de classes, métodos, atributos, variáveis, parâmetros e afins refletem as coisas que elas representam?
- Eu consigo entender o que o código faz lendo ele?
- Eu consigo entender o que os testes fazem?
- As mensagens de erros são entendíveis?

### Funcionalidade

- O código está fazendo o que ele supostamente deveria fazer?
- Existem algum possível bug "oculto" como por exemplo checar uma variável errada ou utilizar um operador de comparação errado?
- As mensagens de usuários estão escritas corretamente?
- Existem erros óbvios que irão quebrar o ambiente de produção?

### Testes

- Os testes cobrem uma boa quantidade de cenários? Cobrem cenários felizes e casos de exceção? Existem casos que não foram considerados e deveriam ter sido considerado?
- Existem testes que garantem que o código está realizando corretamente sua função? O teste está realmente testando os critérios de aceitação daquela funcionalidade?