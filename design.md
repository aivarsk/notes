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

--

Services, Classes are design ahead of time and then we try to make the code fit.
Instead, try to write the actual code (big blob) and see what shape it takes and which classes, services can and make sense to be created.
