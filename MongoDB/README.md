# MongoDB
## Anotações realizadas no curso  MongoDB - The Complete Developer's Guide 2023.

## Conceitos
### Collections

Collections é uma coleção de documentos. Documento é uma "tabela" no mundo dos banco de dados relacionais.

### JSON vs BSON
O MongoDB usa BSON ao invés de Json. A [diferença entre eles](https://www.mongodb.com/json-and-bson) é que o BSON é binário e é muito mais rápido de recuperar do que o JSON. 
Por exemplo, o tipo ObjectId é utilizado pelo BSON e não é um JSON válido.

### Comandos

Mostrar os banco de dados:
```
show dbs
```
Para mostrar algumas informações sobre o banco de dados, como quantidade de coleções, objetos, média de tamanho dos documentos, etc. Para isso, execute:
```
db.stats();
```
O resultado é parecido com:
```
[ { 
   "avgObjSize": 278.73333333333335, 
   "collections": 6, 
   "dataSize": 4181, 
   "db": "soq", 
   "fsTotalSize": 1081101176832, 
   "fsUsedSize": 62515675136, 
   "indexSize": 192512, 
   "indexes": 6, 
   "objects": 15, 
   "ok": 1, 
   "scaleFactor": 1, 
   "storageSize": 221184, 
   "totalSize": 413696, 
   "views": 0 
  } ]
```
Para entrar em banco de dados específico, por exemplo, retornado pelo comando `show dbs` :
```
use NOME_DO_BANCO_DE_DADOS
```

### CRUD

Vamos considerar que existe um banco de dados com o nome `flightData`

#### Create

```
db.flightData.flights.insertOne(
    { 
        departureAirport: "MUC", 
        arrivalAirport: "SFO", 
        aircraft: "Air Bus A380", 
        distance: 12000, 
        intercontinental: true 
    } 
);
```
**Obs.**: Para a collection `flights` não precisa ter o mesmo schema. Por exemplo, eu poderia executar o comando e iria funcionar normalmente:
```
db.flightData.flights.insertOne({departureAirport: "MUC"});
```

O MongoBD gerará um atributo `_id` do tipo `ObjectId`, mas que também pode ser especificado ao criar um documento.
É possível adicionar vários documentos de uma vez. Para isso é necessário usar o `insertMany()`. Por exemplo:
```
db.flightData.flights.insertMany( 
    [{ 
        departureAirport: "MUC", 
        arrivalAirport: "SFO", 
        aircraft: "Air Bus A380", 
        distance: 12000, 
        intercontinental: true 
    }, 
    { 
        departureAirport: "SFO", 
        arrivalAirport: "MUC", 
        aircraft: "Air Bus A400", 
        distance: 12000, 
        intercontinental: true 
    }] 
    );
```

#### Read

Lista todos os dados no documento `flights`.
```
db.flightData.flights.find();
```
O output desse comando é:
```
[{"_id": {"$oid": "63d51782d6ab7d08a116fcd4"}, "aircraft": "Air Bus A380", "arrivalAirport": "SFO", "departureAirport": "MUC", "distance": 12000, "intercontinental": true}]
```
Pode ser adicionado ao final do comando o método `.pretty()` para exibir o JSON identado:
```
[ 
  { 
    "_id": {"$oid": "63d51782d6ab7d08a116fcd4"}, 
    "aircraft": "Air Bus A380", 
    "arrivalAirport": "SFO", 
    "departureAirport": "MUC", 
    "distance": 12000, 
    "intercontinental": true 
  } 
]
```
É possível passar filtros para recuperar documentos. Por exemplo, recuperar todos os voos que tenham a distância de `12000`:
```
db.flightData.flights.find({distance: 12000});
```
Mas também é possível realizar operações no filtro, por exemplo, recuperar todos os voos com distâncias maiores que `10000`:
```
db.flightData.flights.find({distance: {$gt: 10000}});
```

#### Update

Para atualizar um documento o comando é o `UpdateOne()`, mas existe um novo operador `$set`. O `$set` é uma palavra reservada para identificar a operação e o valor é um documento com o valor que quer ser alterado. 
Por exemplo, adicionar um novo campo `marker: "delete"`. O comando seria:
```
db.flightData.flights.updateOne({distance: 12000}, {$set: {marker: "delete"}});
```
O output do comando será:
```
[{"acknowledged": true, "matchedCount": 1, "matchedCount": 1}];
```
Esse comando irá procurar o primeiro documento que os filtros será aplicado e irá atualizá-lo.
Para o caso de atualizar todos os documentos que se aplicam o filtro, o comando é o `updateMany()`:
```
db.flightData.flights.updateMany({}, {$set: {marker: "delete"}});
```

Existe o método `update()` que essencialmente faz o mesmo que `updateMany()`. A diferença é que o documento inteiro é substituído pelo novo documento e a palavra reservada `$set` não é mais necessária. 
Por exemplo:
```
db.flightData.flights.update({}, {marker: "delete"});
```
**Obs.**: **ESSA OPERAÇÃO PODE SER PERIGOSA** e precisa ser executada com muito cuidado.
A forma mais segura de executar essa atualização de documento é utilizando o método `replaceOne()`. Por exemplo, para remover o atributo `intercontinetal` o comando seria:
```
db.flightData.flights.replaceOne({_id: ObjectId("ID_DO_OBJETO")}, { 
    departureAirport: "MUC", 
    arrivalAirport: "SFO", 
    aircraft: "Air Bus A380", 
    distance: 12000 
});
```

#### Delete

Para deletar um documento o comando é o `deleteOne()`, onde é preciso passar um filtro. Por exemplo, se eu quiser deletar um documento que o `departureAirport` é igual a `MUC`, o comando seria:
```
db.flightData.flights.deleteOne({departureAirport: "MUC"});
```
O output do comando será:
```
[{"acknowledged": true, "deletedCount": 1}]
```
Esse comando irá procurar o primeiro documento que os filtros será aplicado e irá deletá-lo. Para o caso de deletar todos os documentos que se aplicam o filtro, o comando é o `deleteMany()`:
```
db.flightData.flights.deleteMany({departureAirport: "MUC"});
```

## Operações com collections

O método `find` não retorna todos os documentos, o método retorna um `cursor`, que por padrão são de 20 documentos. Para recuperar todos os documentos é possível fazer a operação `forEach`. 
Considere que o comando foi executado:
```
db.flightData.passengers.insertMany([ 
    {name: "Valdemar Jr", age: 41}, 
    {name: "Erika", age: 22}, 
    {name: "Klaus", age: 32}, 
    {name: "Alex", age: 35}, 
    {name: "Melanie", age: 25}, 
]);
```

### forEach

```
db.flightData.passengers.find().forEach((passData) => {
    printjson(passData) 
});
```

### Projection

`Projection` é a manipulação dos dados necessários. Nem sempre precisamos de todos os campos de um documento e onde Projection ajuda. Para listar apenas os nomes dos passageiros:
```
db.flightData.passengers.find({}, {name: 1, _id: 0});
```
O caso do `_id:0` é que por padrão o método `find` sempre retorna o campo `_id`. Para os outros campos são desnecessários, porque já é definido zero como padrão.

### Embedded Documents

É possível adicionar mais de 100 níveis de documentos. O tamanho máximo de um documento é de **16mb**. É possível também ter arrays de embedded documents. 
Para adicionar um embedded document é preciso passar um novo documento no parâmetro `$set`. Por exemplo:

```
db.flightData.flights.updateMany({}, { 
    $set: {status: {description: "on-time", lastUpdated: "1 hour ago"}} 
});
```

### Arrays

É possível adicionar um novo documento, onde a sua estrutura é um array. Por exemplo, adicionar o campo `hobbies`:
```
db.flightData.passengers.updateOne({name: "Valdemar Jr"}, {$set:  
        {hobbies: ["Photography", "Cycling"]} 
});
```
Para pesquisar em arrays de embedded documents, o MongoDB é esperto para recuperar e buscar dentro de toda a estrutura. Por exemplo:
```
db.flightData.passangers.find({hobby: "Photography"});
```
Também é possível navegar entre as estruturas de documento, por exemplo:
```
db.flightData.flights.find({"status.description": "on-time"});
```

### Schema

O MongoDB é `schemaless`, mas não quer dizer que não possa definir um.

#### Validação de schema

É possível especificar quais documentos serão validados e o que acontece quando a validação de `schema` falhar. É possível lançar uma exception ou um warning em caso de erro de validação de esquema. 
Depende do tratamento da aplicação.

Para criar um `schema`, onde os campos `name` e `age` são obrigatórios e `age` precisa ser um `number`, é preciso definir o `schema` na criação da coleção:
```
db.createCollection("patients", { 
    validator: { 
        $jsonSchema: { 
            bsonType: "object", 
            required: ["name", "age"], 
            properties: { 
                name: { 
                    bsonType: "string", 
                    description: "must be a string" 
                }, 
                age: { 
                    bsonType: "number", 
                    description: "must be a number" 
                } 
            } 
        } 
    } 
})
```
Se tentar executar os comandos abaixo, irá ocorrer um erro, porque não estão de acordo com o `schema` definido no comando `createCollection`:
```
db.patients.insertOne();
```
O campos `name` e `age` são obrigatórios.

```
db.patients.insertOne({name: "Valdemar"});
```
O campo `age` é obrigatório.
```
db.patients.insertOne({name: "Valdemar", age: "41"});
```
O campo `age` precisa ser um number.

Para mudar o `schema` é necessário executar o comando como administrador, executando `runCommand`. Por exemplo, para mudar a validação do `schema` previamente criado 
e definir que em caso de erro de `schema` apresente apenas um *warning*:
```
db.runCommand({ 
    collMod: "patients", 
    validator: { 
        $jsonSchema: { 
            bsonType: "object", 
            required: ["name", "age"], 
            properties: { 
                name: { 
                    bsonType: "string", 
                    description: "must be a string" 
                }, 
                age: { 
                    bsonType: "number", 
                    description: "must be a number" 
                } 
            } 
        } 
    }, 
    validationAction: "warn" 
})
```

## Relacionamentos

As duas formas de relacionar documentos no MongoDB são `Embedded Documents` e `References`.

### Embedded Document
Para referências, ler a [documentação aqui](https://www.mongodb.com/basics/embedded-mongodb#:~:text=Embedded%20documents%20are%20an%20efficient,only%20when%20they're%20worthwhile).


### Referência

Em referência tem várias duplicações, porque se alterar a informação de um lado, precisa alterar todas as outras informações dos documentos que estriam relacionados.

#### OneToOne

Para esse relacionamento é recomendado usar Embedded Document. Usar References para relacionamentos diretos 1-1 é necessário fazer isso em dois passos ao invés de um só:
```
var dsid = db.patients.findOne({name: "Valdemar"}).diseaseSummary 
db.diseaseSummaries.findOne({_id: dsid})
```
Se o relacionamento por 1-1, mas que se fizer sentido eles existirem separados, eles poderiam ser referenciados por pelo _id ou por qualquer outro campo que o identifique. Por exemplo, o relacionamento 1-1 entre Pessoa e Carro, eles poderiam existir sozinhos. Vai depender da regra de negócio.

#### OneToMany

Acredito que a mesma regra de relacionamento `OneToOne` pode ser aplicada para relacionamento `OneToMany`. Se o relacionando entre os documentos fizerem sentido sozinhos, eles poderiam ser criados em documentos diferentes. 
O exemplo de `Cidade` e `Cidadãos`.

#### ManyToMany

No mundo relacional, seriam criados três tabelas e uma tabela para relacionar as duas. Em MongoDB é possível criar com apenas dois documentos, usando `Embedded Document`.
Quando mais frequente o documento mudar, mais ele se adequa a estratégia de `Relacionamento`.

#### Agregador `$lookup`

Com ele é possível realizar uma consulta em mais de um Documento com um único comando, ao invés de dois.
```
db.patients.aggregate([ 
    {$lookup: 
            {from: "diseaseSummaries", localField: "diseaseSummary", foreignField: "_id", as: "diseases"} 
}]);
```

## Create Operations

### Ordered Inserts

O padrão do MongoDB é não ser `transactional`. Por exemplo, se tentar inserir o comando baixo, mas o segundo documento `{_id: "cars", name: "car"}` já existir, o primeiro vai ser adicionado 
e o restante ignorado:
```
db.hobbies.insertMany([{_id: "bike", name: "Cycling"}, {_id: "cars", name: "car"}, {_id: "yoga", "name": "Yoga"}])
```
Para ignorar os documentos com erro e seguir com as inserções, existe o parâmetro chamado `ordered`, onde o padrão é `true`, mas para termos esse comportamento setamos como `false`, como é feito abaixo:
```
db.hobbies.insertMany([{_id: "bike", name: "Cycling"}, {_id: "cars", name: "car"}, {_id: "yoga", "name": "Yoga"}], {"ordered": false})
```

### Write Concern

https://www.mongodb.com/docs/manual/reference/write-concern/

### Atomicidade

A atomicidade é em nível de documento, incluindo `Embedded Documents`, então para ter atomicidade teria que ser a nível Documento root.

## Read Operations

### Operators

Na documentação do MongoDB existem os seguintes operadores:
- Query e Projections
- Update
- Query Modifiers
- Aggregations

A sintaxe para usar operadores é, usando find:
```
db.[DOCUMENT].find({[ATTRIBUTE]: {OPERATOR: VALUE}});
```
Aplicado ao nosso exemplo de coleção `flights`:
```
db.flights.find({distance: {$gt: 1000}});
```
É possível também usar `Embedded Document` como filtro, apenas adicionado ponto `"."` para navegar entre os documentos. Por exemplo:
```
db.flights.findOne({"status.description": "on-time"})
```

Operadores `$in` e `$nin`, são operadores que recebem um array `[]` com valores a serem retornados e a diferença respetivamente:
```
db.flights.find(distance:{$in: [2000, 3000]});
```

#### Logical Operators
Para operações lógicas a sintaxe é um pouco diferente:
```
db.[DOCUMENT].find([LOGIC OPERATOR]: [{FILTER OPERATORS}]);
```
Exemplo de `$or`:
```
db.flights.find({$or:[{distance: {$lt: 4000}}, {intercontinental: true}]});
```
Para o caso de `$and` operator funciona exatamente como `$or`, mas que existe uma forma enxuta. Por exemplo:
```
 db.flights.find({$and:[{distance: {$lt: 4000}}, {intercontinental: true}]});
```
Seria o mesmo que:
```
 db.flights.find({distance: {$lt: 4000}, {intercontinental: true}});
```
Por que termos o operador `$and` então? Para casos onde o atributo é repetido. Por exemplo:
```
db.flights.find({distance: 4000, distance: 3000});
```
Se fizer da forma acima, o valor do filtro `distance: 4000` será substituído pelo segundo filtro, porque JSON não permite atributos repetidos.

Operador `$exists` verificar se o atributo do documento existe e combinado com o `$ne` é excelente para verificar se o atributo existe e se tem algum valor. 
Por exemplo:
```
db.flights.find({status: {$exists: true, $ne:null}})
```
O operador `$expr` é muito interessante quando se quer comparar o valor de dois campos de um documento. Por exemplo, vamos criar e inserir o documento `stock` 
e que terá dois atributos `volume` e `target`:
```
db.stock.insertMany([{volume: 100, target: 120}, {volume: 89, target: 80}, {volume: 200, target: 177}]);
```
E para verificar quais os `stock` onde o volume é maior do que o `target`, basta executar:
```
db.stock.find({$expr: {$gt: ["$volume", "$target"]}});
```
**Obs.**: Importante usar o `$` dentro das expressões para que o MongoDB analise o valor do atributo, como é feito em `$volume`.

#### Cursors
O método `find()` retorna um cursor e isso é importante para recuperar os documentos de forma performática.

#### Ordenar
Para ordenar, por exemplo, por distance, basta executar o comando abaixo:
```
db.flights.find().sort({distance: 1});
```
Onde:
- `1` é decrescente.
- `-1` é crescente.
  É possível usar a função `limit()` para limitar a quantidade de Documentos recuperados, para paginação, por exemplo.
```
db.flights.find().sort({distance: 1}).limit();
```

#### Update Operations

Seguindo a documentação do MongoDB, para alterar um Documento é preciso dois passos:
- Como identificar o que vai ser alterado.
- E como será alterado.
  - Quando o atributo é adicionado/substituído. 

Por exemplo, em `hobbies`:
```
db.users.updateOne( 
    {_id: ObjectId("ID_DO_DOCUMENTO")}, {$set: {hobbies:[ 
            {title: "Sports", frenquency: 1}, 
            {title: "Cooking", frenquency: 1}, 
            {title: "Dancing", frenquency: 3} 
        ]}});
```

#### Operadores `$min`, `$man` e `$mul`

Para o operador `$min` podemos fazer, por exemplo:
```
db.users.updateOne({name: "Valdemar Jr"}, {$min: {age: 41}});
```
Para que o atributo age seja alterado, o valor da propriedade deve ser menor que o valor atual. Caso contrário não será atualizado. O mesmo vale para o operador `$max`.
O operador `$mul` ele multiplica o valor atual com o valor passado no documento. Por exemplo:
```
db.users.updateOne({name: "Valdemar Jr"}, {$mul: {age: 2}});
```
Considere que o valor anterior era `41` ele vai passar a ser `82`.

#### Operador `$unset`

Com esse operador é possível remover atributos de um documento. Por exemplo:
```
db.users.updateOne({name: "Erika"}, {$unset: {age:""}})
```
O valor definido no documento `{age: ""}` não importa, ele vai ser ignorado e removido do Documento original.

#### Operador `$upsert`

Esse operador ele responsável por realizar `updates`, mas caso no filtro do `update` não exista, ele insere. O `$upsert` é uma sigla para `update/insert`. Então, por exemplo:
```
db.users.updateOne({name: "Maria"}, {$set: {age: 27}}, {upsert:true});
```
Se no filtro não existir `Maria`, esse novo documento será inserido. Útil para quando se quer atualizar um valor, que ele não existe ainda.

#### Operador `$elemMatch`

Operador responsável para atualizar documentos que estão dentro de um array, combinando valores daquele elemento do array e atualizar exatamente aquele valor dentro do array. Por exemplo:
```
db.users.find({hobbies: {$elemMatch: {title: "Sports", frequency: {$gte:3}}}}, {$set: {"hobbies.$.highFrequency": true}});
```
Para atualizar todos os elementos de um array:
```
db.users.updateMany({age: {$gt: 30}}, {$inc: {"hobbies.$[].frequency": -1}});
```

#### Operador `$push`

Para adicionar array dentro de um documento, basta executar o comando:
```
db.users.updateOne({name: "Valdemar Jr"}, {$push: {hobbies: {title: "Sports", frequency: 2}}});
```
Também é possível adicionar mais de um elemento ao array usando o operador `$each`. Como é feito aqui:
```
db.users.updateOne({name: "Valdemar Jr"}, {$push: {hobbies: {$each: [{tittle: "Wine", frequency: 1}, {title: "Hiking", frequency: 2}]}}});
```
Para evitar que um elemento dentro de um array seja adicionado repetidamente, existe o operador `$addToSet`. Não importa quantas vezes o comando seja executado, ele não irá adicionar elementos repetidos ao array. Por exemplo:
```
db.users.updateOne({name: "Valdemar Jr"}, {$addToSet: {hobbies: {title: "Gaming", frequency: 4}}})
```

#### Operador `$pull`

Esse operador é responsável para remover um elemento de um array. Por exemplo:
```
db.users.updateOne({name: "Valdemar Jr"}, {$pull: {hobbies: {title: "Sports"}}})
```

### Delete Operations

Para deletar um documento específico, basta executar o comando:
```
db.users.deleteOne({name: "Erika"});
```
Para deletar vários:
```
db.users.deleteMany({age: {$gte: 32}});
```

## Índices(indexes)

Tenha cuidado ao inserir indices demais, porque tem um custo de ao inserir, todos os índices precisam ser atualizados.

Existe um método que dá para explicar como está a desempenho da sua query. Esse método é o `.explain()`, que é chamado antes da sua operação. Por exemplo:
```
db.users.explain().find({});
```
Para criar um índice execute o comando:
```
db.users.createIndex({"hobbies.title": 1});
```
Onde o valor 1 quer dizer que o índice será criado de forma ascendente. E para remover um índice:
```
db.users.dropIndex({"hobbies.title": 1});
```

É possível fazer a composição de índices, por exemplo:
```
db.users.createIndex({"hobbies.title": 1}, {age: 1});
```
É possível utilizar índice para ordenação de documentos.
Para recuperar os índices de um documento, basta executar:
```
db.users.getIndexes();
```
Para adicionar um índice _UNIQUE_, basta executar o comando:
```
db.users.createIndex({"hobbies.title": 1}, {unique: true});
```
Para o índice _UNIQUE_, MongoDB considera `null` como valor. Para evitar que o valor `null` seja contado como valor, é possível usando `partialFilterExpression`. Por exemplo:
```
db.users.createIndex({email: 1}, {unique: true, partialFilterException: {email: {$exists: true}});
```
É possível criar índices no MongoDB com tempo de vida(TTL). Isso é super útil para criar scripts para executar operações que serão feitas apenas uma vez. 
Para isso execute o comando:
```
db.users.createIndex({email: 1}, {expireAfterSeconds: 3600});
```
Esse comando irá criar um índice ascendente, com **TTL** de **3600** milisegundos.

É possível adicionar índices em textos, por exemplo, pesquisar por labels, tags e palavras chaves.
```
db.products.createIndex({description: "text"});
```
Para usar o índice e pesquisar por texto, é preciso usar `$text`. Por exemplo:
```
db.products.find({$text: {$search: {"awesome"}}});
```
Nesse comando, se tentar buscar por mais de uma palavra, será retornado todos os documentos onde no campo description teriam essas palavras. Por exemplo:
```
db.products.find({$text: {$search: {"red book"}}});
```
Para que seja retornado as duas palavras, tem que adicionar aspas duplas:
```
db.products.find({$text: {$search: {"\"red book\""}}});
```

**Pontos de atenção ao criar índices**:

- Se a consulta geralmente percorre todos os documentos, utilizar índice pode não ser o melhor caminho. Índice é indicado para recuperar um grupo de documentos rapidamente.
- Campos que são difíceis de buscar usando índices, não são recomendados, por exemplo, em datas, porque existem muitas variações que não valem serem adicionados a tabela de índices.
- Quando se cria índices, elas são blocantes, isso quer dizer que quando um índice está sendo criado, todas as outras operações precisam esperar. Para criar um índice não blocante, 
basta executar o comando: `db.users.createIndex({age: 1}, {background: true});`.


### Aggregation framework

Para operações de usando `aggregate` existem alguns passos(pipelines) que são executados:
```
db.persons.aggregate([
    {$match: {gender: "female"}}, // Tem a mesma função do método find()
    {$group: {_id: {state: "$location.state"}, totalPersons: {$sum: 1} }} // agrupar o documento baseado em um atributo("location.state")
    {$sort: {totalPersons: -1}},
    {$skip: 10}, // pula os 10 primeiros
    {$limit: 10} // limita o resultado a 10 documentos
]);
```
Operação `$project` serve para manipular a informação retornada. Por exemplo:
```
db.persons.aggregate([
    {$project: _id: 0, gender: 1, fullName: {$concat: ["$name.first", " ", "$name.last"]}}
]);
```
Essa operação cria um atributo `fullName` e concatenar os valores do documento `name`, que tem `name` e `last` como atributos e adiciona um espaço em branco entre eles.

### Numeric Data

Muito cuidado ao tentar criar um valor que seja maior que o permitido para o tipo. Por exemplo, o tipo `NumerInt` seu tamanho máximo é `2147483647`. Se tentar criar um documento que o 
tipo seja `NumberInt` e o valor seja maior que o permitido, não ocorrerá erro, mas será criado um valor não correspondente. Por exemplo:
```
db.users.isnertOne({age: NumberInt("2147483648")}); // maior apenas +1 maior do que aceito pelo NumberInt
```

## Performance

### Consultas e operações eficientes
`Capped Collections` são collections que podem ser utilizados como cache ou que poderiam ser deletedos caso não sejam acessados por um tempo.
Para criar esse tipo de `Collection`, execute o comando:
```
db.createCollection("capped", {capped: true, size: 10000, max: 3}));
```
Onde:
- O atributo `capped:true` que idenfifica que a collection será do tipo `capped`.
- `max` indica que o número máximo de documentos será `3`.

Considere o comando previamente executado:
```
db.capped.insertMany([
    {name: "Valdemar"},
    {name: "Erika"},
    {name: "Ana"},
]);
```
Caso um novo documento seja inserido, o primeiro documento será apagado para ser colocado no lugar do novo documento. 
Por exemplo, se adicionarmos um novo documento:
```
db.capped.insertOne({name: "Max"});
```
O documento `{name: "Valdemar"}` será substituído.

## Transactions
Para trabalhar com transactions é necessário criar uma `session`. Por exemplo:
```
const session = db.getMongo().startSession();
session.startTransaction();

const usersCol = session.getDatabase("blog").users;
const postsCol = session.getDatabase("blog").posts;
...

session.commitTransaction(); // ou session.aboutTransaction(); 
```

