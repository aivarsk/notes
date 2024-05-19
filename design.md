[Locality of Behaviour](https://htmx.org/essays/locality-of-behaviour/)

The behaviour of a unit of code should be as obvious as possible by looking only at that unit of code.

[The Clean Code Debacle and Rhetoric Tricks - Casey Muratori vs Mr "Uncle Bob" Martin](https://www.youtube.com/watch?v=ZLxazlP7Ppo&ab_channel=gingerBill)

WTF is "Clean Code tm" and how to measure that.

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
