# Code Complete by Steve McConnell

## Software Construction: Building Software

"It generally doesn't make sense to code things you can buy ready-made". Page 18

"Measure twice, cut once" is highly relevant to the construction part of software development, which can account for as much as 65 percent of the total project costs. The worst software projects end up doing construction two or three times or more. Doing the most expensive part of the project twice is as bad an idea in software as it is in any other line of work." Page 23

"Explicit requirements help to ensure that the user rather than the programmer drives the system's functionality. If the requirements are explicit, the user can review them and agree to them. If they're not, the programmer usually ends up making requirements decisions during programming. Explicit requirements keep you from guessing what the user wants during programming. Explicit requirements keep you from guessing what the user wants". Page 38

## Measure Twice, Cut Once

"The architecture doesn't need to specify every class in the system. Aim for the 80/20 rule: specify the 20 percent of the classes that make up 80 percent of the system's behavior (Jacobsen, Booch, and Rumbaugh 1999; Kruchten 2000)." Page 46

"Coding guidelines should be developed with security implications in mind, including approaches to handling buffers, rules for handling untrusted data (data input from users, cookies, configuration data, and other external interfaces), encryption, level of detail contained in error messages, protecting secret data that's in memory, and other issues." Page 47

"The Mythical Man-Month, is that the essential problem with large systems is maintaining their conceptual integrity (Brooks 1995). A good architecture should fit the problem. When you look at the architecture, you should be pleased by how natural and easy the solution seems." Page 52

"If the software is a kind that you haven't worked with before, allow more time for the uncertainty of designing in a new area. Ensure that the time you need to create a good architecture won't take away from the time you need for good work in other areas. If necessary, plan the architecture work as a separate project, too." Page 56

"If you want to develop high-quality software, attention to quality must be part of the software-development process from the beginning to the end. Attention to quality at the beginning has a greater influence on product quality than attention at the end." Page 59

## Key Construction Decisions

"The Sapir-Whorf hypothesis says that your ability to think a thought depends on knowing words capable of expressing the thought. If you don't know the words, you can't express the thought and you might not even be able to formulate it (Whorf 1956)." Page 63

"The implementation must be consistent with the architecture that guides it and consistent internally. That's the point of construction guidelines for variable names, class names, routine names, formatting conventions, and commenting conventions.In a complex program, architectural guidelines give the program structural balance and construction guidelines provide low-level harmony, articulating each class as a faithful part of a comprehensive design." Page 66

## Design Challenges

"Design is the activity that links requirements to coding and debugging. A good top-level design provides a structure that can safely contain multiple lower-level designs. Good design is useful on small projects and indispensable on large projects." Page 73

"Projects fail most often because of poor requirements, poor planning, or poor management. But when projects do fail for reasons that are primarily technical, the reason is often uncontrolled complexity. [..] Keeping routines short helps reduce your mental workload." Page 80

"A good general rule is that a system-level diagram should be an acyclic graph. In other works, a program shouldn't contain any circular relationships in which a Class A uses Class B, Class B uses Class C and Class C uses Class A". Page 85

"Don't use a boolean variable as a status variable. Use an enumerated type instead. It's common to add a new state to a status variable, and adding a new type to an enumerated type requires a mere recompilation" Page 99

"Cohesion refers to how closely all the routines in a class or all the code in a routine support a central purpose—how focused the class is. Classes that contain strongly related functionality are described as having strong cohesion, and the heuristic goal is to make cohesion as strong as possible." Page 105

"A binary search is more elegant, but a brute-force, sequential search is often sufficient. When in doubt, use brute force. — Butler Lampson" Page 107

"The guiding principle behind the top-down approach is the idea that the human brain can concentrate on only a certain amount of detail at a time. If you start with general classes and decompose them into more specialized classes step by step, your brain isn't forced to deal with too many details at once." Page 111

"A weakness of the bottom-up composition approach is that it's hard to use exclusively. Most people are better at taking one big concept and breaking it into smaller concepts than they are at taking small concepts and making one big one." Page 113

"A final risk of prototyping arises when developers do not treat the code as throwaway code. I have found that it is not possible for people to write the absolute minimum amount of code to answer a question if they believe that the code will eventually end up in the production system. They end up implementing the system instead of prototyping." Page 114

"As P.J. Plauger says, "The more dogmatic you are about applying a design method, the fewer real-life problems you are going to solve" (Plauger 1993). Treat design as a wicked, sloppy, heuristic process. Don't settle for the first design that occurs to you. Collaborate. Strive for simplicity. Prototype when you need to. Iterate, iterate, and iterate again. You'll be happy with your designs." Page 119

"Provide services in pairs with their opposites. Most operations have corresponding, equal, and opposite operations. If you have an operation that turns a light on, you'll probably need one to turn it off." Page 137

"Favor read-time convenience to write-time convenience. Code is read far more times than it's written, even during initial development. Favoring a technique that speeds write-time convenience at the expense of read-time convenience is a false economy." Page 141

## 6 Working Classes

"Containment is the simple idea that a class contains a primitive data element or object. A lot more is written about inheritance than about containment, but that's because inheritance is more tricky and error-prone, not because it's better. Containment is the work-horse technique in object-oriented programming." Page 143

"designing ahead"—trying to anticipate future needs, usually without fully understanding what those future needs are. The best way to prepare for future work is not to design extra layers of base classes that "might be needed someday"; it's to make current work as clear, straightforward, and simple as possible. That means not creating any more inheritance structure than is absolutely necessary." Page 146

"Initialize all member data in all constructors, if possible. Initializing all data members in all constructors is an inexpensive defensive programming practice." Page 150

"Avoid creating god classes. Avoid creating omniscient classes that are all-knowing and all-powerful. If a class spends its time retrieving data from other classes using Get() and Set() routines (that is, digging into their business and telling them what to do), ask whether that functionality might better be organized into those other classes rather than into the god class (Riel 1996)." Page 155

## 7 High-Quality Routines

"A function like CosineAndTan() has lower cohesion because it tries to do more than one thing. The goal is to have each routine do one thing well and not do anything else." Page 168

"Make names of routines as long as necessary. Research shows that the optimum average length for a variable name is 9 to 15 characters." Page 171

"To name a procedure, use a strong verb followed by an object. A procedure with functional cohesion usually performs an operation on an object. The name should reflect what the procedure does, and an operation on an object implies a verb-plus-object name. PrintDocument(), CalcMonthlyRevenues(), CheckOrderlnfo(), and RepaginateDocument() are samples of good procedure names." Page 172

## 8 Defensive Programming

"Programs that use exceptions as part of their normal processing suffer from all the readability and maintainability problems of classic spaghetti code. — Andy Hunt Dave Thomas" Page 199

"Don't throw an uncaught exception in a section of code if you can handle the error locally.Avoid throwing exceptions in constructors and destructors unless you catch them in the same place." Page 199

"Consider creating your own project-specific exception class, which can serve as the base class for all exceptions thrown on your project. This supports centralizing and standardizing logging, error reporting, and so on." Page 203

"Create a general design for the class. Class design includes numerous specific issues. Define the class's specific responsibilities, define what "secrets" the class will hide, and define exactly what abstraction the class interface will capture." Page 216

"Naming the routine might seem trivial, but good routine names are one sign of a superior program and they're not easy to come up with. In general, a routine should have a clear, unambiguous name. If you have trouble creating a good name, that usually indicates that the purpose of the routine isn't clear." Page 221


"Eliminate the causes of all error messages and warnings. Pay attention to what the messages tell you about your code. A large number of warnings often indicates low-quality code, and you should try to understand each warning you get." Page 231

## 10 Guidelines for initializing Variable

"Initialize each variable close to where it's first used. Some languages, including Visual Basic, don't support initializing variables as they're declared." Page 241

"This is an example of the Principle of Proximity: keep related actions together. The same principle applies to keeping comments close to the code they describe, keeping loop setup code close to the loop, grouping statements in straight-line code, and to many other areas." Page 242

"When you keep references to variables close together, you enable the person reading your code to focus on one section at a time. If the references are far apart, you force the reader to jump around in the program. Thus the main advantage of keeping references to variables together is that it improves program readability." Page 245

"Finally, short live times are useful when splitting a large routine into smaller routines. If references to variables are kept close together, it's easier to refactor related sections of code into routines of their own." Page 247

## 11 The Power of Variable Names

"Names that are too long are hard to type and can obscure the visual structure of a program." Page 261

"Are short variable names always bad? No, not always. When you give a variable a short name like i, the length itself says something about the variable—namely, that the variable is a scratch value with a limited scope of operation." Page 262

"Many programs have variables that contain computed values: totals, averages, maximums, and so on. If you modify a name with a qualifier like Total, Sum, Average, Max, Min, Record, String, or Pointer, put the modifier at the end of the name." Page 263

"When you find yourself "figuring out" a section of code, consider renaming the variables. It's OK to figure out murder mysteries, but you shouldn't need to figure out code. You should be able to read it." Page 266

"Some programmers like to put Is in front of their boolean names. Then the variable name becomes a question: isdone? isError? isFound? isProcessingComplete? Answering the question with true or false provides the value of the variable. A benefit of this approach is that it won't work with vague names: isStatus? makes no sense at all. A drawback is that it makes simple logical expressions less readable: if ( isFound ) is slightly less readable than if ( found ). Use positive boolean variable names. Negative names like notFound, notdone, and notSuccessful are difficult to read when they are negated—for example, if not notFound" Page 268

"Why Have Conventions? Conventions offer several specific benefits: They let you take more for granted. By making one global decision rather than many local ones, you can concentrate on the more important characteristics of the code. They help you transfer knowledge across projects. Similarities in names give you an easier and more confident understanding of what unfamiliar variables are supposed to do. They help you learn code more quickly on a new project. Rather than learning that Anita's code looks like this, Julia's like that, and Kristin's like something else, you can work with a more consistent set of code. They reduce name proliferation. Without naming conventions, you can easily call the same thing by two different names. For example, you might call total points both pointTotal and totalPoints. This might not be confusing to you when you write the code, but it can be enormously confusing to a new programmer who reads it later. They compensate for language weaknesses. You can use conventions to emulate named constants and enumerated types. The conventions can differentiate among local, class, and global data and can incorporate type information for types that aren't supported by the compiler." Page 270

"Standardized prefixes add precision to several areas of naming that tend to be imprecise. The precise distinctions between min, first, last, and max are particularly helpful. Standardized prefixes make names more compact. For example, you can use cpa for the count of paragraphs rather than totalParagraphs. You can use ipa to identify an index into an array of paragraphs rather than indexParagraphs or paragraphsIndex." Page 281

"Avoid names with similar meanings. If you can switch the names of two variables without hurting the program, you need to rename both variables." Page 285

"Avoid "magic numbers". Magic numbers are literal numbers, such as 100 or 47524, that appear in the middle of a program without explanation. If you program in a language that supports named constants, use them instead." Page 292

"Changes can be made more reliably. If you use named constants, you won't over-look one of the 100s or change a 100 that refers to something else." Page 292
