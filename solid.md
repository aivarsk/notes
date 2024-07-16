https://en.wikipedia.org/wiki/SOLID

For OOP but why OOP in the first place? Why not functional, procedural or a mix of all.

## Definition

Principles
- Single-responsibility principle: "There should never be more than one reason for a class to change."[2] In other words, every class should have only one responsibility.[3]
- Open–closed principle: "Software entities ... should be open for extension, but closed for modification."[4]
- Liskov substitution principle: "Functions that use pointers or references to base classes must be able to use objects of derived classes without knowing it."[5] See also design by contract.[5]
- Interface segregation principle: "Clients should not be forced to depend upon interfaces that they do not use."[6][7]
- Dependency inversion principle: "Depend upon abstractions, [not] concretes."[8][7]

### Sources

S

https://web.archive.org/web/20150202200348/http://www.objectmentor.com/resources/articles/srp.pdf
This principle was described in the work of Tom DeMarco1 and Meilir Page-Jones2
. They
called it cohesion. As we’ll see in Chapter 21, we have a more specific definition of cohesion at the package level. However, at the class level the definition is similar.

What is a Responsibility?
In the context of the Single Responsibility Principle (SRP) we define a responsibility to be
“a reason for change.”   But this is guessing the future requirements: proactive not reactive.
When to stop separating: connect/close + send/recv or connect/close + send + recv ??


```
Modem.java -- SRP Violation
interface Modem
{
public void dial(String pno);
public void hangup();
public void send(char c);
public char recv();
}
```

is SFTP part of FTP with a "SSH part" or is it a new subclass?

O

https://web.archive.org/web/20150905081105/http://www.objectmentor.com/resources/articles/ocp.pdf
Bertrand Meyer2
 gave us guidance as long ago as 1988 when he
coined the now famous open-closed principle. To paraphrase him:
SOFTWARE ENTITIES (CLASSES, MODULES, FUNCTIONS, ETC.)
SHOULD BE OPEN FOR EXTENSION, BUT CLOSED FOR
MODIFICATION. 

When a single change to a program results in a cascade of changes to dependent modules,
that program exhibits the undesirable attributes that we have come to associate with “bad”
design. The program becomes fragile, rigid, unpredictable and unreusable. The openclosed principle attacks this in a very straightforward way. It says that you should design
modules that never change. When requirements change, you extend the behavior of such
modules by adding new code, not by changing old code that already works.

But changes happen because the old code does not work.

Assumes extension by inheritance. Assumes the extension points will be sufficient. Assumes extensions will be aligned, not perpendicular or something completely different.

How about implementing feature or part of on it's own and then checking which code can be reused.

L

FUNCTIONS THAT USE POINTERS OR REFERENCES TO BASE
CLASSES MUST BE ABLE TO USE OBJECTS OF DERIVED CLASSES
WITHOUT KNOWING IT.
The above is a paraphrase of the Liskov Substitution Principle (LSP). Barbara Liskov first
wrote it as follows nearly 8 years ago1
:
What is wanted here is something like the following substitution property: If
for each object o1 of type S there is an object o2 of type T such that for all
programs P defined in terms of T, the behavior of P is unchanged when o1 is
substituted for o2 then S is a subtype of T.

I

CLIENTS SHOULD NOT BE FORCED TO DEPEND UPON INTERFACES
THAT THEY DO NOT USE.
When clients are forced to depend upon interfaces that they don’t use, then those clients
are subject to changes to those interfaces. This results in an inadvertent coupling between
all the clients. Said another way, when a client depends upon a class that contains interfaces that the client does not use, but that other clients do use, then that client will be
affected by the changes that those other clients force upon the class. We would like to
avoid such couplings where possible, and so we want to separate the interfaces where possible.

See S


D

https://web.archive.org/web/20150905081103/http://www.objectmentor.com/resources/articles/dip.pdf


The Dependency Inversion Principle
A. HIGH LEVEL MODULES SHOULD NOT DEPEND UPON LOW LEVEL MODULES. BOTH SHOULD DEPEND UPON ABSTRACTIONS.
B. ABSTRACTIONS SHOULD NOT DEPEND UPON DETAILS. DETAILS SHOULD DEPEND UPON ABSTRACTIONS.
One might question why I use the word “inversion”. Frankly, it is because more traditional
software development methods, such as Structured Analysis and Design, tend to create
software structures in which high level modules depend upon low level modules, and in
which abstractions depend upon details. Indeed one of the goals of these methods is to
define the subprogram hierarchy that describes how the high level modules make calls to
the low level modules. Figure 1 is a good example of such a hierarchy. Thus, the dependency structure of a well designed object oriented program is “inverted” with respect to
the dependency structure that normally results from traditional procedural methods.


Why not say (functional style) : just pass extra parameter in. Looks like OOP thingie.


Right away, OLID suggests there is a base and derived class or an interface and implementation class. 

Inheritance is overused and bad in most cases (not all), composition is preferred. Creating an interface to break dependency on a single implementation falls in one of these:
- you either duplicate the exact API from implementation to interface making the interface not generic enough for possible future implementations or (most likely) you will not have another implementation making that interface just another boilerplate layer.
- you try to make the interface generic enough but are doing a premature abstraction and predicting the future for no good reason
- you DO have multiple implementations right away. Which is when you do the OLI. Thing to consider: maybe "implementation inversion" leads to cleaner code:
- instead of: a common function that takes an interface to do stuff
- do: different classes call the same utility function with parameters
- meaning: do L somewhere at a higher level, do not push it all the way down

- rule of thumb: you can't get the interface/base class right until you have 2-3 derived classes.
- maybe a matrix with 1, n implementations and XXX on other axis



 SOLID during initial implementation version long-time support
 https://martinfowler.com/bliki/DesignStaminaHypothesis.html

https://wiki.c2.com/?CouplingAndCohesion Low coupling, High cohesion

https://web.archive.org/web/20150906155800/http://www.objectmentor.com/resources/articles/Principles_and_Patterns.pdf

GORUCO 2009 - SOLID Object-Oriented Design by Sandi Metz
https://www.youtube.com/watch?v=v-2yFMzxqwU


if you refer to something -> you depend on it
when the things you depend on change -> you must change OR not - depends on the kind of change and the language (C, C++ ABI)

https://www.amazon.com/Growing-Object-Oriented-Software-Guided-Tests/dp/0321503627

loosely coupled (Sandi says this is DI but it is not)
highly cohesive
easily composable
context independent

interface segregation is for C++ and compile-time dependencies, quit talking about it. My background: just try to rebuild with ccache and don't be too smart about it (main binary vs libs, templates, compile time flags, etc)
liskov is about subcassing (Foo Fooish). If you have to check type, you failed at this. We do not do subclasses

if testing seems hard - examine your design. But some of the "clean code" requires so much stuff to execute

Is it DRY?

Does it have one responsibility
Does everything in it change at the same rate - THIS IS GOLD
Does it depend on things that change less often than it does


Sandi: only mock classes I own, don't mock/stub the object under test :( How about mocking as the last resort?


SDO are the remaining ones


LOVE the Sandi approach of writing the code and refactoring. Look at the code, see what would be the best structure for the code. Much of the SOLID happens ahead of time with putting classes and interfaces and then trying to implement that. I think the same happens with design patterns

Scale of likelihood of change

classitis small classes



https://www.youtube.com/watch?v=4xqkI953K6Y Unknown unknowns
https://www.youtube.com/watch?v=8ncQrGuunHY

A recent study found that more than 90% of catastrophic failures in distributed data-intensive systems were caused by incorrect error handling


https://www.youtube.com/watch?v=TT_RLWmIsbY LoB and breaking the rules


Coupling just from the API point of view, not from the functional/feature view


https://stackoverflow.com/questions/14000762/what-does-low-in-coupling-and-high-in-cohesion-mean


In one of your conference, you explained the benefit to DEFER decisions about technical details when building a software (web interfaces, database etc...): 
I don't know if you ever read this book: http://www.amazon.com/Growing-Object-Oriented-Software-Guided-Tests/dp/0321503627  but it seems to promote exactly the contrary. One of its idea is:

_ Start by writing a Walking Skeleton with an end-to-end focus.  "We've seen too much projects failing because integration of components was not define earlier in the project phase".
Thus, in this case, an architect would firstly focus on: What do we think TECHNICALLY we need to achieve our goal.. "hummm  Swing, ok ..  MYSQL humm okkk that seems good". The very opposite way of yours :)

1) Walking skeleton predates GOOS. Cockburn wrote about it last century http://alistair.cockburn.us/Walking+skeleton.

2) When people speak about deferring decisions they're usually concerned with avoiding premature commitment. Cockburn specifically says that the Walking Skeleton "need not use the final architecture, but it should link together the main architectural components. The architecture and the functionality can then evolve in parallel."

3) In an old article (http://martinfowler.com/ieeeSoftware/whoNeedsArchitect.pdf), Martin Fowler says "one of an architect’s most important tasks is to remove architecture by finding ways to eliminate irreversibility in software designs." He's talking about making design decisions that protect us from making hard-to-change architectural commitments. Too much flexibility and the system becomes over-complex, too little and you're at the mercy of every change (whether due to your product owner or a changing 3rd party component)

4) BDD has never recommended driving development through the UI. BDD encourages us to focus on the behaviour of the system. Exercise the system at the layer appropriate for the behaviour that you are developing. It's worth keeping the Testing Pyramid in mind, and probably the Testing Iceberg too (http://claysnow.co.uk/?p=175315341). And always remember that the GUI itself is just another component.

5) I don't agree with Uncle Bob that outside-in and inside-out approaches result in profoundly different test structures. Specifically I have seen no evidence that outside-in tests necessarily lead to more mocks, or to mocks/doubles that rely on mechanism rather than results.

6) More contentiously, I think that we're all working outside-in anyway. TDD by it's very definition works from the outside of a component, driving its design and implementation through an emerging public API. Further, if there's no clear link from your user's requirements through to the code you're implementing something is going very wrong, so we're all working from the outside after all.



SOLID is very one-sided, it pushed "low coupling". Low coupling, high cohesion is a more balanced way: single responsibility can go on indefinitely but the cohesion part says to keep similar and related things together (Locality of Behavior)


We need "MongoDB is web scale"  for SOLID
