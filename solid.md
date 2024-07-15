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


O

L

I

D


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
