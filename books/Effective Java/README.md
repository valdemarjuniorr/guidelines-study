# Effective Java (Third Edition)

## Consider static factory methods instead of constructors
The traditional way for a class to allow a client to obtain an instance is to provide a public constructor. There is another technique that should be a parte of every programmer's toolkit. A class can provide a _public static factory method_, which is simply a static method that returns an instance of the class.

```java
public static Boolean valueOf(boolean b) {
    return b ? Boolean.TRUE : Boolean.FALSE;
}
```

### Advantages
- One advantage of static factory methods is that, unlike constructors, **they have names**.
- They are **NOT** required to create a new object each time they're invoked. This allows immutable classes to use preconstructed instances or to cache instances as they're constructed.
- It can greatly improve performance if equivalent objects are requested often, especially if they are expensive to create.
- They can return an object of any subtype of their return type.(Polymorphism)

## Consider a builder when faced with many constructor parameters
Static factories and constructors share a limitation: they do not scale well to large numbers of optional parameters. **The Builder pattern simulates named optional parameters** as found in Python and Scala. Long sequences of identically typed parameters can cause subtle bugs in case reverse, for example, two such parameters, the compiler won't complain, but the program will misbehave at runtime.

```java
NutritionFacts cocaCola = new NutritionFacts.Builder(240, 8).calories(100)
        .sodium(35).carbohydrate(27).build();
```

### Advantage
- The code is easy to write and, more importantly, easy to read.

### Disadvantage
- The object may be in an inconsistent state partway through its construction.
- The object precludes the possibility of making a class immutable.

## Avoid finalizers and cleaners
**Finalizers are unpredictable, often dangerous, and generally unnecessary**. Their use can cause erratic behavior, poor performance, and portability problems. **NEVER** depend on a finalizer or cleaner to update persistent state.

## Prefer try-with-resources to try-finally
To be usable with this constructor, a resource must implement the _AutoCloseable_ interface, which consists of a single void-returning close method. Many classes and interfaces in the Java libraries and third-party libraries now implements or extend `AutoCloseable`. If you write a class that represents a resource that must be closed, your class should implement `AutoCloseable` too.

```java
public static String firstLineOfFile(String path) throws IOException {
    try (BufferedReader br = new BufferedReader(new FileReader(path))) {
        return br.readLine();
    }
}
```

## Obey the general contract when overriding equals
The easiest way to avoid problems is not to override the equals method, in which case each instance of the class is equal only to itself. This is the right thing to do if any of the following conditions apply:
- Each instance of the class is inherently unique.
- There is no need for the class to provide a "logical equality" test.
- A superclass has already overridden equals, and the superclass behavior is appropriate for this class.

One kind of value class that does **NOT** require the `equals` method to be overridden is a class that uses instance control to ensure that at most one object exists with each value. Enum types all into this category. For these classes, logical equality is the same as object identity, an Object's equals method functions as a logical equals method.

When you override the equals method, you must adhere to its general contract. If you violate it, you may well find that your program behaves erratically or crashes, and it can be very difficult to pin down the source of the failure. For an `equals` method to be useful, all of the elements in each equivalence class must be interchangeable from the perspective of the user.

### high-quality equals method
1. Use the == operator to check if the argument is a reference to this object. If so, return `true`.
2. Use the `instanceof` operator to check if the argument has the correct type.
3. Cast the argument to the correct type.
4. For each "significant" field in the class, check if that field of the argument matches the corresponding field of this object.

For the best performance, you should first compare fields that are more likely to differ, less expensive to compare, or, ideally, both.
When you are finished writing your `equals` method, ask yourself three questions:
- Is it symmetric?
- Is it transitive?
- Is it consistent?
  And don't just ask yourself; write unit tests to check, unless you use `AutoValue`.

**ALWAYS OVERRIDE `hashCode` WHEN YOU OVERRIDE `equals`**.

## Always override hashcode when you override equals
You **MUST** override `hashcode` **in every class that overrides** `equals`. If you fail to do so, your class will violate the general contract for `hasCode`, which will prevent if from functioning properly in collections such as `HashMap` and `HashSet`.

## Always override toString
When Object provides an implementation of the `toString` method, the string that it returns is generally not what the user of your class wants to see. The general contract for `toString` says that the returned string should be "a concise but informative representation that is easy for a person to read."

## Minimize mutability
1. Don't provide methods that modify the object's state(_known as mutators_).
2. Ensure that the class can't be extended.
3. Make all fields `final`.
4. Make all fields `private`.
5. Ensure exclusive access to any mutable components.

Note that the method names are prepositions(such as `plus`) rather than verbs(such as `add`). This emphasizes the fact that methods don't change the values of the objects. The `BigInteger` and `BigDecimal` classes did not obey this naming convention, and it led to many usage errors.

You need not and should not provide a `clone` method or `copy` constructor on an immutable class.

## Favor composition over inheritance
It is safe to use inheritance within a package, where the subclass and the superclass implementations are under the control of the same programmers. Inheriting from ordinary concrete classes across package boundaries might be dangerous. **Unlike method invocation, inheritance violates encapsulation**.

Inheritance is appropriate only in circumstances where the subclass really is a subtype of the superclass. In other words, a _class B_ should extends a _class A_ only if an "is-a" relationship exists between the two classes. If you are tempted to have a _class B_ extend a _class A_, ask yourself the question:
- Is every B really an A? If you cannot truthfully answer yes to this question, B should not extend A.

Even then, inheritance may lead to fragility if the subclass and the superclass is not designed for inheritance.

## Use interface only to define types
When a class implements an interface, the interface serves as a _type_ that can be used to refer to instances of the class. That a class implements an interface should therefore say something about what a client can do worth instances of the class. It is inappropriate to define an interface for any other purpose.

**The constant interface pattern is a poor use of interface**. They should not be used merely to export constants.

## Use enums instead of int constants
There is a better way to associate a different behavior with each enum constant: declare an abstract `apply` method in the enum type, and override it with a concrete method for each constant in a _constant-specific_ class body. Such methods are known as _constant-specific_ method implementation:

```java
// Enum type with constant-specific method implementations
public enum Operation {
    PLUS {
        public double apply(double x, double y) {
            return x + y;
        }
    }, 
    MINUS {
        public double apply(double x, double y) {
            return x - y;
        }
    }, 
    TIMES {
        public double apply(double x, double y) {
            return x * y;
        }
    }, 
    DIVIDE {
        public double apply(double x, double y) {
            return x / y;
        }
    };
    public abstract double apply(double x, double y);
}
```

## Use marker interfaces to define types
Marker interfaces have two advantages over marker annotations. First and foremost, **marker interfaces define a type that is implemented by interfaces of the marked class; marker annotations do not**. The existence of a marker interfaces type allows you to catch errors at compile time that you couldn't catch until runtime if you used a marker annotations.
**Another advantage of marker interfaces over marker annotations is that they can be targeted more precisely**. If an annotation type is declared with target `ElementType.TYPE`, it can be applied to _any_ class or interface.

## Prefer lambdas to anonymous classes
**Lambdas lack names and documentation; if a computation isn't self-explanatory, or exceeds a few lines, don't put it in a lambda**. One line is ideal for a lambda, and three lines is a reasonable maximum. If you violate this rule, it can cause serious harm to the readability of your programs.

## Favor the use of standard functional interfaces
The `Operator` interfaces represent functions whose result and argument types are the same. The `Predicate` interface represents a function that takes an argument and returns a `boolean`. The `Function` interface represents a function whose argument and return types differ. The `Supplier` interface represents a function that takes no arguments and returns(or "supplies") a value. Finally, `Consumer` represents a function that takes an argument and returns nothing, essentially consuming its argument.

## Use streams judiciously
Stream pipelines are evaluated _lazily_. Evaluation doesn't start until the terminal operation is invoked, and data elements that aren't required in order to complete the terminal operation are never computed. This _lazy_ evaluation is when makes it possible to work with infinite streams. Note that a stream pipeline without a terminal operation is a silent no-op, so don't forget to include one.

`computeIfAbssent` method, which was added in Java 8. This method looks up a key in the map: If the key is present, the method simply returns the value associated with it. If not, the method computes a value by applying the given function object to the key, associates this value with the key, and returns the computed value. The `computeIfAbsent` method simplifies the implementation of maps that associate multiple values with each key.

In the absence of explicit types, careful naming of lambda parameters is essential to the readability of stream pipelines.

## Prefer Collection to Stream as a return type

## Make defensive copies when needed
Defensive copies are made _before_ checking the validity of the parameters, and the validity check is performed pn the copies rather than on the originals. It protects the class against changes to the parameters from another thread.

## Design method signatures carefully
Every method should "pull its weight". Too many methods make a class difficult to learn, use, document, test, and maintain.
THere are three techniques for shortening overly long parameter lists:
1. One is to break the method up into multiple methods, each of which requires only a subset of the parameters.
2. Parameter lists is to create _helper classes_ to hold groups of parameters. Typically these helper classes are static member classes.
3. A third technique that combines aspects of the first two is to adapt the _Build pattern_ from object construction to method invocation.

**Avoid long paramaters lists**

## Return optionals judiciously
**Container types, including collections, maps, streams, arrays, and optionals should not be wrapped in optionals**. Rather than returning an empty `Optional<List<T>>`, you should simply return an empty `List<T>`. Returning the empty container will eliminate the need for client code to process an optional. 
You should declare a method to return `Optional<T>` if it might not be able to return a result and clients will have to perform special processing if no result is returned. 

We have not discussed other possible uses, and that is bevause most other uses of optionals are suspect. For example, you should never use optionals as map values.
It is almost never appropriate to use an optional as a key, value, or element in a collection or array. Is it ever appropriate to store an optional in an instance field? Often it's a "bad smell". However, be aware that there are real performance consequences associated with returning optionals; for performance-critical methods, it may be better to return `null` or throw an exception.

## Minimize the scope of local variables
By minimizing the scope of local variables, you increase the readability and maintainability of your code and reduce the likelihood of error.

## Avoid float and double if exact answers are required
The `float` and `double` types are particularly ill-suited for monetary calculations because it is impossible to represent 0.1 (or any other negative power of ten) as a `float` or `double` exactly.

## Avoid strings where other types are more appropriate
Strings are poor substitutes for other value, enum or aggregate types.

## Beware the performance of string concatenation
**Using the string concatenation operator repeatedly to concatenate n strings requires time quadratic in n**. This is an unfortunate consequence of the fact that strings are immutable. When two strings are concatenated, the contents of both are copied. **To achieve accptable performance, use a `StringBuilder` in place of a `String`**.

## Refer to objects by their interfaces
If appropriate interfaces types exist, then parameters, return values, variables, and fields should all be declared using interfaces types.

## Prefer interfaces to reflection
Reflection is powerful, but should not be used indiscriminately. If an appropriate interface type is available, it is generally better to use it than to use reflection.
Reflection allows one class to suse another, even if the latter class did not exists when the former was compiled. This power, however, comes at a price:
- You lose all the benefits of compile-time type checking, including exception checking.
- The code required to perform reflective access is clumsy and verbose.
- Performance suffers.

## Optimize judiciously
Using an implementation type rather than an interface in an API ties you to a specific implementation, even though faster implementations may be written in the future. 

Once you're carefully designed your program and produced a clear, concise, and well-structure implementation, then it may be time to consider optimization, assuming you're not already satisfied with the performance of the program.

## Adhere to generally accepted naming conventions
Interfaces are named like classes, for example, `Collection` o `Comparator`, or with an adjective ending in _able_ or _ible_, for example, `Runnable`, `Iterable`, or `Accessible`. Because annotation types have many uses, no part of speech predominates.

Method that perform some action are generally named with verb or verb phrase, for example, `append`, `drawImage`, `isDigit`, `getBackground`. Methods that return a boolean value are generally named with a question verb phrase, for example, `isDigit`, `isEmpty`, `canRead`.

Methods that return a view whose type differs from that of the receiving object are often called `asType`, for example, `asList`, `asSet`, `asMap`.

## Use exceptions only for exceptional conditions
Exceptions are, as their name implies, to be used only for exceptional conditions; they should never be used for ordinary control flow. **A well-designed API must not force its clients to use exceptions for ordinary control flow**. A class with a "state-dependent. method that can be invoked only under certain unpredictable conditions should generally have a separate "state-testing" method indicating whether it is appropriate to invoke the state-dependent method.

Throw checked exceptions for recoverable conditions and unchecked exceptions for programming errors. When in doubt, throw unchecked exceptions.

## Favor the use of standard exceptions
**Do not reuse** `Exception`, `RuntimeException`, `Throwable`, or `Error` directly. Treat these classes as if they were abstract. You can't reliably test for these exceptions because they are superclasses of other exceptions that a method may throw.

## Throw exceptions appropriate to the abstraction
Higher layers should catch lower-level exceptions and, in their place, throw exceptions that can be explained in terms of the higher-level abstraction. This idiom is known as _exception translation_. The detail message of an exception should not be confused with a user-level error message, which must be intelligible to end users. Unlike a user-level error message, the detail message is primarily for the benefit of programmers or site reliability engineers, when analyzing a failure.

## Don't ignore exceptions
When the designers of an API declare a method to throw an exception, they are trying to tell you something. Don't ignore it! It is easy to ignore exceptions by surrounding a method invocation with a `try` statement whose `catch` block is empty. This is poor practice, as it causes the exception to be ignored silently.

**If you choose to ignore an exception, the `catch` block should contain a comment explaining why it is appropriate to do so, and the variable should be named `ignored`**

## Use lazy initialization judiciously
Lazy initialization is a double-edged sword. It decreases the cost of initializing a class or creating an instance, at the expense of increasing the cost of accessing the lazily initialized field. Depending on what fraction of theses fields eventually require initialization, how expensive it is to initialize them, and how expensive it is to initialize them, and how often each one is accessed once initialized, lazy initialization can(like many "optimizations") actually harm performance.
