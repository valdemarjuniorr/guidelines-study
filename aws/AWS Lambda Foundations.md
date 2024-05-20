# AWS Lambda Foundations

## Description
O ambiente Serverless é uma abstração que permite focar no código da aplicação sem perder tempo construíndo e mantendo infra-estrutura.

A plataforma serverless pode ser integrado com serviços da AWS como por exemplo, `Step functions`, `S3`, Data bases, `EventBridge`, `SNS`, `SQS`, `API Gateway`, `App Sync` e etc.

## O que é Lambda?
É um serviço computacional para executar código sem se preocupar com provisionar ou gerenciar servidores. Lambda são executados em infra-estruturas altamente disponíveis e escaláveis.

## Benefícios
Os benefícios de usar `Lambda` inclue:
- Executar código sem provisionamento ou manutenção de servidores.
- Inicializa funções para resposta a eventos.
- Escala automaticamente
- Proporciona internamente monitoramento e logging via `Amazon CloudWatch`.

## Lambda Function
O código que é executado dentro do Lambda é chamado `Lambda Function`. Pense numa função como uma  aplicação pequena e self-contained. Depois que a `Lambda function` é criada, ela está pronta para ser executada, logo depois de ser inicializada. Cada função inclui o código e também algumas informações como nome da função e os recursos obrigatórios. Elas são naturalmente `stateless`, sem ter nenhuma relação com a infra-estrutura. 

A função ela pode ser disparada por um evento `S3`, `Amazon DB`, `Amazon kinesis` e por ai vai.

## Funcionamento
Quando a função é executada sincronicamente, a função é executada e é esperado uma resposta. Na resposta é adicionado informações adicionais, por exemplo a versão da função que ela foi executada.

Para execuções `async`, eventos são enfileirados e o requisitor não espera a função terminar de executar. Com a execução `async` é possível usar os destinatários das respostas da função.

### Polling invocation
Essa chamada foi projetado para integrar com `AWS streaming` e serviços de filas sem necessidade de código ou de gerenciamento de servidor. Esse modelo de invocação suporta:
- `AWS Kinesis`
- `SQS`
- `Amazon DynamoDB Streams`

## Ciclo de vida do Lambda
Quando uma Lambda function é criada, é preciso especificar a quantidade de memória disponível e a quantidade máxma de chamadas por função. Todas as funções são executadas dentro de um ambiente de execução, onde permissões, recursos, credenciais, variáveis de ambientes são compartilhados entre as funções.

### Fase inicial (init fase)
Nessa fase, lambda executa em um ambiente configurado, baixa o código da função e todas as suas camadas, inicializa suas estenções, inicializa o tempo de execução e depois executa o código.

### Fase de invocação (invoke phase)
Nessa fase, a lambda invoca o gerenciador da função(handler). Depois da função ser executada, a Lambda preparar o hander para invocar outra função.

### Fase de desalocação(shutdown phase)
Se a lambda não receber nenhuma chamada por um período de tempo, ela fase começa, onde todos os recursos são desalocados e o ambiente é desligado.

## Performance
Aplicações Serverless podem ser altamente performáticas, graças ao fácil paralelismo e a concorrência. A escalabilidade é auto-gerenciada.

## Inicialização Cold and warm

### Cold start
Inicialização fria(`cold start`) ocorre quando uma nova lambda function é necessária ser executada. Quando ela é solicitada para ser executar, primeiro o ambiente de execução é preparado. Nesse momento, o serviço baixa o codigo da função e cria o ambiente com memória e tempo configurados. O código é executado fora do `handler`, só depois que é executado dentro do `handler`.

### Warm start
É quando o serviço de lambda mantem o ambiente ao invés de destruído imediatamente. Isso permite que a função execute novamente dentro do mesmo ambiente de execução, ganhando tempo, não sendo ncessário inicializar o ambiente novamente.


## Boas práticas
- Armazene e referencie dependências localmente
- Limite a reinicialização de variáveis
- Adicione código para verificar e reusar conexões existentes
- Utilize o espaço temporário como `transient cache`
- Verifique se o processo em background foi finalizado

## Permissões
Existem dois tipos de permissões:
- Permissão de execução da lambda
- Permissão da execução sobre outros serviços

As permissões de execução de uma lambda é controlada usando as políticas do IAM. Por exemplo, é verificado na política de acesso se uma lambda function tem permissão de inserir dados em uma tabela do `DynamoDB`. Na regra é necessário incluir `Trust policy` que permite que a lambda function para `AssumeRole` para que consiga realizar a operação de salvar na tabela.

Lembrando que o pricípio de segurança é o mais restritivo possível

## Autorização
Com lambda você pode executar seu próprio código. As linguagens suportadas são:
- Node.js
- Python
- Java
- Go
- C#
- Ruby
- PowerShell

### Handler method
O `handler` é um método na função onde são processados os eventos. Quando a função é invocada, o lambda executar essa função. Quando o hander finaliza a execução é retorna uma resposta, essa resposta se torna disponível para outra lambda function.

#### Boas práticas
Com lambda function é uma boa prática separar lógica de negócio do `handler method`, permitindo portabilidade da regra de negócio e criação de testes unitários, sem se preocupar com código de infra-estrutura.

Outra boa prática é modularizar as funções. Ao invés de criar uma função que compacta, cria uma imagem e indexa, considere ter 3 lambdas para cada propósito.

Considere as funções lambda como `Stateless`

## AWS SAM
AWS SAM é uma ferramenta open-source para aplicações serverless. Ela prove uma sintaxe rápida para criar funções, APIs, banco de dados e mapeamento de recursos. Com algumas linhas de código, é possível definir as responsabilidades da aplicação usandoo YAML.

## Configurando Lambda Functions
Conforme comentado anteriormente, as primeiras configurações para uma lambda function são:
- Memória
- Timeout
- Concorrência e escalabilidade

### Memória
É possível alocar 10Gb de memória. Qualquer aumento de memória, dispara o equivamente em CPU disponível para a função.

### Timeout
Essa configuração dita quanto tempo a lambda function pode ser executada. O máximo de execução de uma lambda é de 900 segundos(15 minutos). Defina o `timeout` para o máximo, apenas depois de testar sua aplicação. Existe casos que a aplicação deveria falhar rápido e não esperar o timeout máximo.

É importante analisar quanto tempo a função executa. A lambda function é cobrado baseado na execução em 1-ms incrementado. Evitando que a aplicação chegue ao tempo máximo de timeout, evita de ser cobrado à mais por função.

### Concorrência e escalabilidade
Essa configuração afeta a performance da função e sua habilidade de escalar sob demanda. Concorrênciai é a quantidade de chamadas a função executa ao mesmo tempo

#### Tipos de concorrência
- Concorrência não reservada(Unreserved concurrency) é quando a concorrência não é definida. O mínimo é de 100. Isso permite que não tenha nenhum provisionamento que ainda seja permitido executar.
- Concorrência reservada(Reserved concurrency) garante o númnero máximo de concorrências para a função. Quando a função tem `reserved concurrency`, nenhuma outra função pode usar aquela concorrência.
- Concorrência provisionada(Provisioned concurrency) inicializa uma quantidade de ambientes(`runtime environment`) para que a função responsa imediatamente as chamadas. Essa opção é utilizada em casos da função precisar de uma alta performance e uma baixa latência

## Deploy e teste de uma aplicação Serverless
