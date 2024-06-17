[API Churn / GraphQL](https://intercoolerjs.org/2016/02/17/api-churn-vs-security)

generic API don't have sufficient information about intent to do proper access control

[Is microservices even architecture?](https://x.com/allenholub/status/1794073247497220246)

Conway's Law says that organizational communication paths [== org structure] are mirrored in the systems the org creates. When management organizes the teams, they are effectively designing the software. They know nothing about software. We are turning over our architecture to fools.


[Cloud architecture is meaningless, it is the deployment strategy](https://x.com/allenholub/status/1794818184408920238)

The so-called "cloud architectures" are not an architecture at all. They are a deployment strategy that removes choices, adds complexity, and locks you into a specific vendor. They often damage (or preclude you from having) an actual architecture. Literally everything you do in the cloud, you could do with multiple threads in a monolith (something I often do before breaking up the monolith into distinct services because it makes building and testing easier). So, the architecture can be deployed on the cloud or in a monolith.

DRY - some duplication is cheaper than the wrong abstraction.

[Clean Code works through side effects on the object itself](https://www.youtube.com/watch?v=IqHaGd9J42s)

Integration level tests are better for refactoring than unit tests because refactoring changes units

[Locality of Behaviour](https://htmx.org/essays/locality-of-behaviour/)

The behaviour of a unit of code should be as obvious as possible by looking only at that unit of code.
These two concepts are key to creating maintainable codebases. Most of so called principles are just reiterations and reinventions of these (and few more) concepts.

Cohesion is basically a measure of how code put in the same code unit is related.
Coupling is a measure of “how much other code will I have to change if I change X”.

[The Clean Code Debacle and Rhetoric Tricks - Casey Muratori vs Mr "Uncle Bob" Martin](https://www.youtube.com/watch?v=ZLxazlP7Ppo&ab_channel=gingerBill)

WTF is "Clean Code tm" and how to measure that.
"Clean" is not a measurable quantity.
How to measure programmer performance.
"Clean Code tm" claims to increase programmer performance but how do you know, how do you measure?
CC might not be over-engineered, but it is open-engineered. Does all the code have to be open and ready for modifications and changes? Are we trying to predict the future? How about solving the problem at hand?

["Clean Code" is bad. What makes code "maintainable"? ](https://www.youtube.com/watch?v=8ncQrGuunHY)

- "premature abstraction"

There is no perfect code, follow 80/20:
- spend 20% to make 80% good enough, clean or for 80% functionality
- just accept that the remaining 20% will a couple issues. evaluate if it's worth to fix them

https://www.pymnts.com/artificial-intelligence-2/2024/apples-ai-rollout-will-likely-stretch-into-next-year/

MACH architecture principles — Microservices, API-first, Cloud-native, and Headless

[Clean Code Q&A](https://github.com/cmuratori/misc/tree/main)

Every program composed of **o** operations and **t** types has a complexity of **o**x**t**.
- If we use OO we can increase **t** with minimum disruption to the source code; but increasing o disrupts many source code modules.
- If we use switch statements we can increase **o** with minimum disruption to the source code; but increasing **t** disrupts many source code modules.

BUT how often do we add new T compared to O in a real project.

Nice:
```
class raw_device
{
public:
	void Handler(raw_device_request *Packet, raw_device_result *Result);
};

void raw_device::Handler(raw_device_request *Packet, raw_device_result *Result)
{
	switch(Packet->Op)
	{
		case RIO_read:
		// etc.
		
		case RIO_write:
		// etc.
		
		case RIO_get_name:
		// etc.
		
		default:
		// write error Result
	}
}
```

[Modular Monolith](https://www.youtube.com/watch?v=nuHMlA3iLjY)

- [Monolith First by Martin Fowler](https://martinfowler.com/bliki/MonolithFirst.html)
- microservices should never be the default choice, but rather a last resort (Sam Newman)


https://www.youtube.com/watch?v=MA4UHNUYaqI
- "premature clean code" before getting all done

--

Services, Classes are design ahead of time and then we try to make the code fit.
Instead, try to write the actual code (big blob) and see what shape it takes and which classes, services can and make sense to be created.
