# Code Complete
## by Steve McConnell

*A collection of wisdom and best practices for software construction.*

---

## Chapter 3: Software Construction - Building Software

> "It generally doesn't make sense to code things you can buy ready-made."
>
— Page 18

> "Measure twice, cut once" is highly relevant to the construction part of software development, which can account for as much as 65 percent of the total project costs. The worst software projects end up doing construction two or three times or more. Doing the most expensive part of the project twice is as bad an idea in software as it is in any other line of work."
>
— Page 23

> "Explicit requirements help to ensure that the user rather than the programmer drives the system's functionality. If the requirements are explicit, the user can review them and agree to them. If they're not, the programmer usually ends up making requirements decisions during programming. Explicit requirements keep you from guessing what the user wants."
>
— Page 38

---

##  Chapter 3: Measure Twice, Cut Once - Architecture

> "The architecture doesn't need to specify every class in the system. Aim for the 80/20 rule: specify the 20 percent of the classes that make up 80 percent of the system's behavior."
>
— Page 46

> "Coding guidelines should be developed with security implications in mind, including approaches to handling buffers, rules for handling untrusted data (data input from users, cookies, configuration data, and other external interfaces), encryption, level of detail contained in error messages, protecting secret data that's in memory, and other issues."
>
— Page 47

> "The essential problem with large systems is maintaining their conceptual integrity. A good architecture should fit the problem. When you look at the architecture, you should be pleased by how natural and easy the solution seems."
>
— Page 52

> "If the software is a kind that you haven't worked with before, allow more time for the uncertainty of designing in a new area. Ensure that the time you need to create a good architecture won't take away from the time you need for good work in other areas. If necessary, plan the architecture work as a separate project, too."
>
— Page 56

> "If you want to develop high-quality software, attention to quality must be part of the software-development process from the beginning to the end. Attention to quality at the beginning has a greater influence on product quality than attention at the end."
>
— Page 59

---

## Chapter 4: Key Construction Decisions

> "The Sapir-Whorf hypothesis says that your ability to think a thought depends on knowing words capable of expressing the thought. If you don't know the words, you can't express the thought and you might not even be able to formulate it."
>
— Page 63

> "The implementation must be consistent with the architecture that guides it and consistent internally. That's the point of construction guidelines for variable names, class names, routine names, formatting conventions, and commenting conventions. In a complex program, architectural guidelines give the program structural balance and construction guidelines provide low-level harmony, articulating each class as a faithful part of a comprehensive design."
>
— Page 66

---

## Chapter 5: Design Challenges

> "Design is the activity that links requirements to coding and debugging. A good top-level design provides a structure that can safely contain multiple lower-level designs. Good design is useful on small projects and indispensable on large projects."
>
— Page 73

> "Projects fail most often because of poor requirements, poor planning, or poor management. But when projects do fail for reasons that are primarily technical, the reason is often uncontrolled complexity. Keeping routines short helps reduce your mental workload."
>
— Page 80

> "A good general rule is that a system-level diagram should be an acyclic graph. In other words, a program shouldn't contain any circular relationships in which a Class A uses Class B, Class B uses Class C and Class C uses Class A."
>
— Page 85

> "Don't use a boolean variable as a status variable. Use an enumerated type instead. It's common to add a new state to a status variable, and adding a new type to an enumerated type requires a mere recompilation."
>
— Page 99

> "Cohesion refers to how closely all the routines in a class or all the code in a routine support a central purpose—how focused the class is. Classes that contain strongly related functionality are described as having strong cohesion, and the heuristic goal is to make cohesion as strong as possible."
>
— Page 105

> "A binary search is more elegant, but a brute-force, sequential search is often sufficient. When in doubt, use brute force."
>
> — Butler Lampson, Page 107

> "The guiding principle behind the top-down approach is the idea that the human brain can concentrate on only a certain amount of detail at a time. If you start with general classes and decompose them into more specialized classes step by step, your brain isn't forced to deal with too many details at once."
>
— Page 111

> "A weakness of the bottom-up composition approach is that it's hard to use exclusively. Most people are better at taking one big concept and breaking it into smaller concepts than they are at taking small concepts and making one big one."
>
— Page 113

> "A final risk of prototyping arises when developers do not treat the code as throwaway code. I have found that it is not possible for people to write the absolute minimum amount of code to answer a question if they believe that the code will eventually end up in the production system. They end up implementing the system instead of prototyping."
>
— Page 114

> "The more dogmatic you are about applying a design method, the fewer real-life problems you are going to solve. Treat design as a wicked, sloppy, heuristic process. Don't settle for the first design that occurs to you. Collaborate. Strive for simplicity. Prototype when you need to. Iterate, iterate, and iterate again. You'll be happy with your designs."
>
— P.J. Plauger, Page 119

> "Provide services in pairs with their opposites. Most operations have corresponding, equal, and opposite operations. If you have an operation that turns a light on, you'll probably need one to turn it off."
>
— Page 137

> "Favor read-time convenience to write-time convenience. Code is read far more times than it's written, even during initial development. Favoring a technique that speeds write-time convenience at the expense of read-time convenience is a false economy."
>
— Page 141

---

## Chapter 6: Working Classes

> "Containment is the simple idea that a class contains a primitive data element or object. A lot more is written about inheritance than about containment, but that's because inheritance is more tricky and error-prone, not because it's better. Containment is the work-horse technique in object-oriented programming."
>
— Page 143

> "Designing ahead"—trying to anticipate future needs, usually without fully understanding what those future needs are. The best way to prepare for future work is not to design extra layers of base classes that "might be needed someday"; it's to make current work as clear, straightforward, and simple as possible. That means not creating any more inheritance structure than is absolutely necessary."
>
— Page 146

> "Initialize all member data in all constructors, if possible. Initializing all data members in all constructors is an inexpensive defensive programming practice."
>
— Page 150

> "Avoid creating god classes. Avoid creating omniscient classes that are all-knowing and all-powerful. If a class spends its time retrieving data from other classes using Get() and Set() routines (that is, digging into their business and telling them what to do), ask whether that functionality might better be organized into those other classes rather than into the god class."
>
— Page 155

---

## Chapter 7: High-Quality Routines

> "A function like CosineAndTan() has lower cohesion because it tries to do more than one thing. The goal is to have each routine do one thing well and not do anything else."
>
— Page 168

> "Make names of routines as long as necessary. Research shows that the optimum average length for a variable name is 9 to 15 characters."
>
— Page 171

> "To name a procedure, use a strong verb followed by an object. A procedure with functional cohesion usually performs an operation on an object. The name should reflect what the procedure does, and an operation on an object implies a verb-plus-object name. PrintDocument(), CalcMonthlyRevenues(), CheckOrderInfo(), and RepaginateDocument() are samples of good procedure names."
>
— Page 172

---

## Chapter 8: Defensive Programming

> "Programs that use exceptions as part of their normal processing suffer from all the readability and maintainability problems of classic spaghetti code."
>
> — Andy Hunt & Dave Thomas, Page 199

> "Don't throw an uncaught exception in a section of code if you can handle the error locally. Avoid throwing exceptions in constructors and destructors unless you catch them in the same place."
>
— Page 199

> "Consider creating your own project-specific exception class, which can serve as the base class for all exceptions thrown on your project. This supports centralizing and standardizing logging, error reporting, and so on."
>
— Page 203

> "Create a general design for the class. Class design includes numerous specific issues. Define the class's specific responsibilities, define what "secrets" the class will hide, and define exactly what abstraction the class interface will capture."
>
— Page 216

> "Naming the routine might seem trivial, but good routine names are one sign of a superior program and they're not easy to come up with. In general, a routine should have a clear, unambiguous name. If you have trouble creating a good name, that usually indicates that the purpose of the routine isn't clear."
>
— Page 221

> "Eliminate the causes of all error messages and warnings. Pay attention to what the messages tell you about your code. A large number of warnings often indicates low-quality code, and you should try to understand each warning you get."
>
— Page 231

---

## Chapter 10: Guidelines for Initializing Variables

> "Initialize each variable close to where it's first used. Some languages, including Visual Basic, don't support initializing variables as they're declared."
>
— Page 241

> "This is an example of the Principle of Proximity: keep related actions together. The same principle applies to keeping comments close to the code they describe, keeping loop setup code close to the loop, grouping statements in straight-line code, and to many other areas."
>
— Page 242

> "When you keep references to variables close together, you enable the person reading your code to focus on one section at a time. If the references are far apart, you force the reader to jump around in the program. Thus the main advantage of keeping references to variables together is that it improves program readability."
>
— Page 245

> "Finally, short live times are useful when splitting a large routine into smaller routines. If references to variables are kept close together, it's easier to refactor related sections of code into routines of their own."
>
— Page 247

---

## Chapter 11: The Power of Variable Names

> "Names that are too long are hard to type and can obscure the visual structure of a program."
>
— Page 261

> "Are short variable names always bad? No, not always. When you give a variable a short name like i, the length itself says something about the variable—namely, that the variable is a scratch value with a limited scope of operation."
>
— Page 262

> "Many programs have variables that contain computed values: totals, averages, maximums, and so on. If you modify a name with a qualifier like Total, Sum, Average, Max, Min, Record, String, or Pointer, put the modifier at the end of the name."
>
— Page 263

> "When you find yourself 'figuring out' a section of code, consider renaming the variables. It's OK to figure out murder mysteries, but you shouldn't need to figure out code. You should be able to read it."
>
— Page 266

> "Some programmers like to put Is in front of their boolean names. Then the variable name becomes a question: isDone? isError? isFound? isProcessingComplete? Answering the question with true or false provides the value of the variable. A benefit of this approach is that it won't work with vague names: isStatus? makes no sense at all. Use positive boolean variable names. Negative names like notFound, notDone, and notSuccessful are difficult to read when they are negated—for example, if not notFound."
>
— Page 268

> "Why Have Conventions? Conventions offer several specific benefits: They let you take more for granted. By making one global decision rather than many local ones, you can concentrate on the more important characteristics of the code. They help you transfer knowledge across projects. Similarities in names give you an easier and more confident understanding of what unfamiliar variables are supposed to do. They help you learn code more quickly on a new project. They reduce name proliferation. They compensate for language weaknesses."
>
— Page 270

> "Standardized prefixes add precision to several areas of naming that tend to be imprecise. The precise distinctions between min, first, last, and max are particularly helpful. Standardized prefixes make names more compact."
>
— Page 281

> "Avoid names with similar meanings. If you can switch the names of two variables without hurting the program, you need to rename both variables."
>
— Page 285

> "Avoid 'magic numbers'. Magic numbers are literal numbers, such as 100 or 47524, that appear in the middle of a program without explanation. If you program in a language that supports named constants, use them instead."
>
— Page 292

> "Changes can be made more reliably. If you use named constants, you won't overlook one of the 100s or change a 100 that refers to something else."
>
— Page 293

> "Character and string literals are cryptic. Comments or named constants clarify your intentions."
>
— Page 297

---

## Chapter 12: Fundamental Data Types

> "Use named constants in data declarations. Using named constants helps program readability and maintainability in data declarations and in statements that need to know the size of the data they are working with."
>
— Page 308

> "Use structures to simplify parameter lists. You can simplify routine parameter lists by using structured variables. Rather than passing each of the elements needed individually, you can group related elements into a structure and pass the whole enchilada as a group structure."
>
— Page 322

> "Careful programmers avoid passing a structure as a parameter when only one or two fields from the structure are needed—they pass the specific fields needed instead."
>
— Page 322

---

## Chapter 14: Organize Straight-Line Code

> "Document unclear dependencies with comments. Try first to write code without order dependencies. Try second to write code that makes dependencies obvious. If you're still concerned that an order dependency isn't explicit enough, document it. Documenting unclear dependencies is one aspect of documenting coding assumptions, which is critical to writing maintainable, modifiable code."
>
— Page 349

> "Put the most common cases first. By putting the most common cases first, you minimize the amount of exception-case handling code someone has to read to find the usual cases. You improve efficiency because you minimize the number of tests the code does to find the most common cases."
>
— Page 359

> "Order cases by frequency. Put the most frequently executed cases first and the least frequently executed last. This approach has two advantages. First, human readers can find the most common cases easily. Readers scanning the list for a specific case are likely to be interested in one of the most common cases, and putting the common ones at the top of the code makes the search quicker."
>
— Page 361

---

## Chapter 17: Unusual Control Structures

> "Make sure the recursion stops. Check the routine to make sure that it includes a nonrecursive path. That usually means that the routine has a test that stops further recursion when it's not needed."
>
— Page 396

> "Use safety counters to prevent infinite recursion. If you're using recursion in a situation that doesn't allow a simple test such as the one just described, use a safety counter to prevent infinite recursion."
>
— Page 396

> "Limit recursion to one routine. Cyclic recursion (A calls B calls C calls A) is dangerous because it's hard to detect."
>
— Page 396

---

## Chapter 18: Table-Driven Methods

> "Indexed access schemes offer two main advantages. First, if each of the entries in the main lookup table is large, it takes a lot less space to create an index array with a lot of wasted space than it does to create a main lookup table with a lot of wasted space."
>
— Page 425

> "As Butler Lampson, a distinguished engineer at Microsoft, says, it's better to strive for a good solution and avoid disaster rather than trying to find the best solution."
>
— Page 429

> "If using flags like 0 and 1 is common practice, what's wrong with it? It's not clear from reading the code whether the function calls are executed when the tests are true or when they're false. Nothing in the code fragment itself tells you whether 1 represents true and 0 false or whether the opposite is true."
>
— Page 432

---

## Chapter 19: General Control Issues

> "Move complicated expressions into boolean functions. If a test is repeated often or distracts from the main flow of the program, move the code for the test into a function and test the value of the function."
>
— Page 434

> "Not a few people don't have not any trouble understanding a nonshort string of nonpositives—that is, most people have trouble understanding a lot of negatives."
>
— Page 435

> "Studies by Noam Chomsky and Gerald Weinberg suggest that few people can understand more than three levels of nested ifs, and many researchers recommend avoiding nesting to more than three or four levels."
>
— Page 445

> "One measure of 'programming complexity' is the number of mental objects you have to keep in mind simultaneously in order to understand a program. This mental juggling act is one of the most difficult aspects of programming and is the reason programming requires more concentration than other activities. It's the reason programmers get upset about 'quick interruptions'—such interruptions are tantamount to asking a juggler to keep three balls in the air and hold your groceries at the same time."
>
— Page 456

> "Researchers have tried to formalize their intuitive feelings and have come up with several ways of measuring complexity. Perhaps the most influential of the numeric techniques is Tom McCabe's, in which complexity is measured by counting the number of 'decision points' in a routine."
>
— Page 457

> "One powerful technique for improving software quality is setting explicit quality objectives from among the external and internal characteristics described in the previous section."
>
— Page 466

> "The organization must show programmers that quality is a priority. Making the quality-assurance activity explicit makes the priority clear, and programmers will respond accordingly."
>
— Page 466

> "Guidelines should control the technical character of the software as it's developed. Such guidelines apply to all software development activities, including problem definition, requirements development, architecture, construction, and system testing."
>
— Page 467

> "The surprising implication is that people actually do what you ask them to do. Programmers have high achievement motivation: They will work to the objectives specified, but they must be told what the objectives are."
>
— Page 469

---

## Chapter 20: The Software Quality Landscape

> "The General Principle of Software Quality is that improving quality reduces development costs."
>
— Page 476

---

## Chapter 21: Collaborative Construction

> "Programmers who are still wet behind the ears need guidance from those who are more knowledgeable, and more knowledgeable programmers who tend to be busy need to be encouraged to spend time sharing what they know."
>
— Page 482

> "Don't force pair programming of the easy stuff. One group that used pair programming for the most complicated code found it more expedient to do detailed design at the whiteboard for 15 minutes and then to program solo."
>
— Page 483

> "Trying to improve software quality by increasing the amount of testing is like trying to lose weight by weighing yourself more often. What you eat before you step onto the scale determines how much you will weigh, and the software-development techniques you use determine how many errors testing will find. If you want to lose weight, don't buy a new scale; change your diet. If you want to improve your software, don't just test more; develop better."
>
— Page 501

---

## Chapter 24: Refactoring

> "If you throw several untested routines together at once and find an error, any of the several routines might be guilty. If you add one routine at a time to a collection of previously tested routines, you know that any new errors are the result of the new routine or of interactions with the new routine."
>
— Page 502

> "If you fix errors with logical duct tape and superstition, quality degrades. If you treat modifications as opportunities to tighten up the original design of the program, quality improves."
>
— Page 564

> "There is no code so big, twisted, or complex that maintenance can't make it worse."
>
> — Gerald Weinberg, Page 564

> "Refactoring is a change made to the internal structure of the software to make it easier to understand and cheaper to modify without changing its observable behavior."
>
> — Martin Fowler, Page 565

> "One way to improve a system is to increase its modularity—increase the number of well-defined, well-named routines that do one thing and do it well."
>
— Page 565

> "A parameter list has too many parameters. Well-factored programs tend to have many small, well-defined routines that don't need large parameter lists. A long parameter list is a warning that the abstraction of the routine interface has not been well thought out."
>
— Page 565

> "If a routine has a poor name, change the name of the routine where it's defined, change the name in all places it's called, and then recompile."
>
— Page 567

> "The additional 'design ahead' code creates additional complexity, which calls for additional testing, additional defect correction, and so on. The overall effect is to slow down the project. Experts agree that the best way to prepare for future requirements is not to write speculative code; it's to make the currently required code as clear and straightforward as possible so that future programmers will know what it does and does not do and will make their changes accordingly."
>
— Page 569

> "Move a complex boolean expression into a well-named boolean function. If the expression is complicated enough, this refactoring can improve readability. If the expression is used more than once, it eliminates the need for parallel modifications and reduces the chance of error in using the expression."
>
— Page 572

> "Return as soon as you know the answer instead of assigning a return value within nested if-then-else statements. Code is often easiest to read and least error-prone if you exit a routine as soon as you know the return value."
>
— Page 572

> "Replace conditionals (especially repeated case statements) with polymorphism. Much of the logic that used to be contained in case statements in structured programs can instead be baked into the inheritance hierarchy and accomplished through polymorphic routine calls."
>
— Page 573

> "Convert a long routine to a class. If a routine is too long, sometimes turning it into a class and then further factoring the former routine into multiple routines will improve readability."
>
— Page 573

> "Normally, query operations don't change an object's state. If an operation like GetTotals() changes an object's state, separate the query functionality from the state-changing functionality and provide two separate routines."
>
— Page 573

> "Pass specific fields rather than a whole object. If you find yourself creating an object just so that you can pass it to a routine, consider modifying the routine so that it takes specific fields rather than a whole object."
>
— Page 574

> "Convert one class to two. If a class has two or more distinct areas of responsibility, break the class into multiple classes, each of which has a clearly defined responsibility. Eliminate a class. If a class isn't doing much, move its code into other classes that are more cohesive and eliminate the class."
>
— Page 575

> "Replace inheritance with delegation. If a class needs to use another class but wants more control over its interface, make the superclass a field of the former subclass and then expose a set of routines that will provide a cohesive abstraction."
>
— Page 575

> "Introduce a foreign routine. If a class needs an additional routine and you can't modify the class to provide it, you can create a new routine within the client class that provides that functionality."
>
— Page 575

> "If a class needs several additional routines and you can't modify the class, you can create a new class that combines the unmodifiable class's functionality with the additional functionality. You can do that either by subclassing the original class and adding new routines or by wrapping the class and exposing the routines you need."
>
— Page 575

> "Remove Set() routines for fields that cannot be changed. If a field is supposed to be set at object creation time and not changed afterward, initialize that field in the object's constructor rather than providing a misleading Set() routine."
>
— Page 576

> "Spend your time on the 20 percent of the refactorings that provide 80 percent of the benefit."
>
— Page 582

> "Refactor when you add a class. Adding a class often brings issues with existing code to the fore. Use this time as an opportunity to refactor other classes that are closely related to the class you're adding."
>
— Page 582

> "In a maintenance environment, improve the parts you touch. Code that is never modified doesn't need to be refactored. But when you do touch a section of code, be sure you leave it better than you found it."
>
— Page 582

---

## Chapter 25: Code-Tuning Strategies

> "Before you invest time solving a performance problem, make sure that you're solving a problem that needs to be solved."
>
— Page 589

> "The Pareto Principle, also known as the 80/20 rule, states that you can get 80 percent of the result with 20 percent of the effort."
>
— Page 591

> "Reducing the lines of code in a high-level language improves the speed or size of the resulting machine code—false! Many programmers cling tenaciously to the belief that if they can write code in one or two lines, it will be the most efficient possible."
>
— Page 592

> "It's almost impossible to identify performance bottlenecks before a program is working completely. Programmers are very bad at guessing which four percent of the code accounts for 50 percent of the execution time."
>
— Page 594

> "If you need to optimize before a program is complete, minimize the risks by building perspective into your process. One way is to specify size and speed goals for features and then optimize to meet the goals as you go along."
>
— Page 595

> "Use a high-quality design. Make the program right. Make it modular and easily modifiable so that it's easy to work on later. When it's complete and correct, check the performance. If the program lumbers, make it fast and small. Don't optimize until you know you need to. **Jackson's Rules of Optimization:** Rule 1. Don't do it. Rule 2 (for experts only). Don't do it yet—that is, not until you have a perfectly clear and unoptimized solution."
>
> — M. A. Jackson, Page 596

---

## Chapter 26: Code-Tuning Techniques

> "Many of the things people feel rushed to do simply don't need to be done. If he waited long enough, he claimed, the things that weren't important would be procrastinated into oblivion and he wouldn't waste his time doing them."
>
— Page 615

> "Readability and maintenance are usually more important than execution speed or size."
>
— Page 617

> "One of the most powerful tools in code tuning is a good routine decomposition. Small, well-defined routines save space because they take the place of doing jobs separately in multiple places. They make a program easy to optimize because you can refactor code in one routine and thus improve every routine that calls it."
>
— Page 639

---

## Chapter 27: How Program Size Affects Construction

> "Productivity is substantially determined by the kind of software you're working on, personnel quality, programming language, methodology, product complexity, programming environment, tool support, how 'lines of code' are counted, how nonprogrammer support effort is factored into the 'lines of code per staff-year' figure, and many other factors."
>
— Page 653

> "Regardless of the size of a project, a few techniques are always valuable: disciplined coding practices, design and code inspections by other developers, good tool support, and use of high-level languages. These techniques are valuable on small projects and invaluable on large projects."
>
— Page 655

> "Some developers welcome standards because they reduce arbitrary variance in the project. If your group resists adopting strict standards, consider a few alternatives: flexible guidelines, a collection of suggestions rather than guidelines, or a set of examples that embody the best practices."
>
— Page 662

> "Use 'suggestions' or 'guidelines' with respect to the area. Avoid setting rigid 'rules' or 'standards.'"
>
— Page 683

> "The details of a specific standard are often less important than the fact that some standard exists. Don't set standards for your programmers, but do insist they standardize in the areas that are important to you."
>
— Page 683

---

## Chapter 29: Integration

> "As Kent Beck points out, frequent integration sometimes forces you to break the construction of a single feature into multiple episodes. That overhead is an acceptable price to pay for the reduced integration risk, improved status visibility, improved testability, and other benefits of frequent integration."
>
— Page 704

---

## Chapter 32: Self-Documenting Code

> "The question of whether to comment is a legitimate one. Done poorly, commenting is a waste of time and sometimes harmful. Done well, commenting is worthwhile."
>
— Page 818

> "Good code is its own best documentation. If the code is bad enough to require extensive comments, try first to improve the code so that it doesn't need extensive comments."
>
— Page 818

> "Comments should say things about the code that the code can't say about itself—at the summary level or the intent level."
>
— Page 818

---

## Chapter 33: Personal Character

> "Your employer can't force you to be a good programmer; a lot of times your employer isn't even in a position to judge whether you're good. If you want to be great, you're responsible for making yourself great. It's a matter of your personal character."
>
— Page 820

> "Keeping routines short reduces the load on your brain. Writing programs in terms of the problem domain rather than in terms of low-level implementation details reduces your mental workload."
>
— Page 821

> "It's been shown that humble programmers who compensate for their fallibilities write code that's easier for themselves and others to understand and that has fewer errors. The real low road is the road of errors and delayed schedules."
>
— Page 821

> "If your workload consists entirely of short-term assignments that don't develop your skills, be dissatisfied. If you're working in a competitive software market, half of what you now need to know to do your job will be out of date in three years. If you're not learning, you're turning into a dinosaur."
>
— Page 822

> "If you can't learn at your job, find a new one."
>
— Page 822

> "The mistake Bert made was not realizing that estimates aren't negotiable. He can revise an estimate to be more accurate, but negotiating with his boss won't change the time it takes to develop a software project."
>
— Page 827

> "Management is responsible for the big-picture issues of running a company. If a certain software capability is worth $250K to a company and you estimate it will cost $750K to develop, the company shouldn't develop the software. It's management's responsibility to make such judgments."
>
— Page 828

> "Laziness: The quality that makes you go to great effort to reduce overall energy expenditure. It makes you write labor-saving programs that other people will find useful, and document what you wrote so that you don't have to answer so many questions about it."
>
— Page 830

> "It's easy to confuse motion with progress, busy-ness with being productive. The most important work in effective programming is thinking, and people tend not to look busy when they're thinking. If I worked with a programmer who looked busy all the time, I'd assume that he was not a good programmer because he wasn't using his most valuable tool, his brain."
>
— Page 830

> "Try to think of an alternative approach that would circumvent the problem altogether. Rewrite the troublesome section of code from scratch. Come back to it later when your mind is fresh. Fighting computer problems is no virtue. Avoiding them is better."
>
— Page 831

> "When you first learn something, learn it the right way. When you first do it, you're actively thinking about it and you still have an easy choice between doing it in a good way and doing it in a bad way."
>
— Page 833

> "The characteristics of a superior programmer have almost nothing to do with talent and everything to do with a commitment to personal development."
>
— Page 836

> "Good character is mainly a matter of having the right habits. To be a great programmer, develop the right habits and the rest will come naturally."
>
— Page 836

---

## Chapter 34: Themes in Software Craftsmanship

> "Dividing a system into subsystems at the architecture level so that your brain can focus on a smaller amount of the system at one time. Carefully defining class interfaces so that you can ignore the internal workings of the class. Preserving the abstraction represented by the class interface so that your brain doesn't have to remember arbitrary details. Avoiding deep inheritance hierarchies because they are intellectually demanding."
>
— Page 837

> "The point of having coding conventions is also mainly to reduce complexity. When you can standardize decisions about formatting, loops, variable names, modeling notations, and so on, you release mental resources that you need to focus on more challenging aspects of the programming problem."
>
— Page 838

> "My message to the serious programmer is: spend a part of your working day examining and refining your own methods. Even though programmers are always struggling to meet some future or past deadline, methodological abstraction is a wise long-term investment."
>
> — Robert W. Floyd, Page 840

> "A blanket attempt to avoid mistakes is the biggest mistake of all. Design is a process of carefully planning small mistakes in order to avoid making big ones."
>
— Page 852

> "Team programming is more an exercise in communicating with people than in communicating with a computer. Individual programming is more an exercise in communicating with yourself than with a computer."
>
— Page 854

---

## 📚 About This Document

This is a curated collection of quotes from **Code Complete, 2nd Edition** by Steve McConnell, organized by chapter for easy reference and sharing. Each quote includes its page number for quick lookup in the original text.

The book is considered one of the most comprehensive guides to software construction and is essential reading for professional software developers.
