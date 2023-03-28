# Java threads

## Criando novas threads

Existe duas formas de criar uma thread em java:
- Instanciando uma Thread e colocando o trecho de código entro do método `run()`.
- Estendendo a classe Thread e implementando o método `run()`.

Por exemplo: 
```java
public static void main(String[] args) {
    var thread = new Thread(new Runnable() {
        @Override
        public void run() {
            // Código a ser executado     
        }
    });
}
```
Ou a versão usando lambdas:
```java
var thread = new Thread(() -> {
    // Código a ser executado     
});
```
A outra forma de criar uma thread é estendendo `Thread`. Por exemplo:
```java
public static void main(String[] args) {
    var thread = new NewThread();
    thread.start();
}

public static class NewThread extends Thread {
    @Override
    public void run() {
        // Código a ser executado
    }
}
```

### Executando uma thread

Para executar uma thread, basta executar o método `.start()`. Por exemplo:
```java
var thread = new Thread(() -> {
    // Código a ser executado     
});
thread.start();
```
Obs: Mesmo chamando o método `start()` não quer dizer que a thread será executada imediatamente.

### Nomeando threads

A JVM dá nomes para as thread criadas como, por exemplo `Thread-0`. Quando se trabalha com a criação de muitas threads, fica um pouco difícil de gerenciá-las. 
Isso pode ser resolvido nomeando-as. Por exemplo, usando o método `.setName()`:
```java
thread.setName("better name thread");
```

### Prioridades
No SO existe o pool de threads e como essas threads são gerenciadas. É possível definir a prioridade de uma thread a ser executada em relação as outras. 
Isso é feito através do método `.setPriority()`, que pode ser entre 1 até 10. Por exemplo:

```java
thread.setPriority(10);
```

Ou utilizando a constante:
```java
thread.setPriority(Thread.MAX_PRIORITY);
```

## Coordenação de threads
Quando a thread não está sendo executada é preciso terminá-la, porque está sendo consumido recursos que poderiam ser economizados.
Vamos ver como terminar uma thread.

### Thread.interrupt
Para interromper a execução de uma thread é possível chamando o método `.interrupt()`. Se o método `.interrupt()` não for chamado
a aplicação irá esperar que a thread `BlockingTask` seja finalizada, mesmo que a `Main` thread já tenha sido finalizada antes.

```java
public static void main(String[] args) {
    var thread = new Thread(new BlockingTask());
    thread.start();
    thread.interrupt();
}

public static class BlockingTask implements Runnable {
    @Override
    public void run() {
        try {
            Thread.sleep(50000);
        } catch (InterruptedException e) {
            System.out.println("Existing blocking thread");
        }
    }
}
```
#### Daemon Thread
Daemon threads são operações executadas, mas que não são o ponto focal da aplicação. Por exemplo:
- Um editor de texto, que envia o comando para salvar o arquivo de tempos em tempos.
- Uma execução de um comando, que não temos o controle do momento de interromper o código.

Para isso, basta chamar o método `.setDaemon(Boolean.TRUE)`. Seguindo o exemplo anterior e adicionando a chamada:
```java
public static void main(String[] args) {
    var thread = new Thread(new BlockingTask());
    thread..setDaemon(Boolean.TRUE)
    thread.start();
    thread.interrupt();
}

public static class BlockingTask implements Runnable {
    @Override
    public void run() {
        try {
            Thread.sleep(50000);
        } catch (InterruptedException e) {
            System.out.println("Existing blocking thread");
        }
    }
}
```
Mesmo a thread `BlockingTask` não tiver sido terminada, quando a `Main` thread finalizar, a outra thread também será finalizada.

### Thread.join
Para evitar que seja colocado um `while` no código para verificar se `Thread-B` terminou de executar para que `Thread-A` use o resultado, é necessário usar o método `.join()`.
Tendo as seguintes assinaturas:
- `public final void join()`
- `public final void join(long millis)`
- `public final void join(long millis, int nanos)`

Dessa forma é possível economizar CPU, economizando recursos. A chamada do método impede que o resultado seja retornado apenas quando a thread é finalizada.
Para definir uma tolerância de espera de uma thread, considerando que uma aplicação não pode esperar para sempre, é possível usar a versão do método:
```java
thread.join(2000);
```
Dessa forma é adicionado uma tolerância de espera de 2s.

## Thread pooling
Thread pooling é basicamente criar uma thread para executar uma tarefa e após finalizada, reutilizá-la para executar outra task, assim evita criar outras threads todas às vezes.
Dentro da JDK existe uma implementação de pool de threads, conhecido como `Fixed Threads pool Executor`. Por exemplo:
```java
int numberOfThreads = 4;
Executor executor = Executors.newFixedThreadPool(numberOfThreads);
..
Runnable task = ...;
executor.execute(task);
```