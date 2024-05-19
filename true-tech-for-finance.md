[LMAX Disruptor](https://lmax-exchange.github.io/disruptor/)

[Jane Street](https://www.youtube.com/watch?v=eqkAaplKBc4&list=PLCiAikFFaMJoWyXnJ2BWpse5HuiYibNYs&ab_channel=JaneStreet)

[Safe at Any Speed: Building a Performant, Safe, Maintainable Packet Processor](https://www.youtube.com/watch?v=BysBMdx9w6k&t=198s&ab_channel=JaneStreet)

[How to Build an Exchange](https://www.youtube.com/watch?v=b1e4t2k2KJY&ab_channel=JaneStreet) [and here](https://www.janestreet.com/tech-talks/building-an-exchange/)

Multicast. How many people know what multicast is? All right, most people. So for those of you that don’t, TCP/IP networking has built into a lot of the hardware, the network cards, and the switches more importantly, the ability to have logical addresses. That when you send a packet to this address, it’s electronically repeated to every interested party. Relatively simultaneously. It’s really powerful. And without it, this kind of architecture really would not work. But it means that when the Matching Engine accepts an order, or produces an execution, both parties to that execution see it at the same time. The market data sees that at the same time. The Drop Port sees at the same time. The trade reporter sees at the same time, et cetera. There’s only one downside. This is UDP, which means it’s unreliable.

We run a secondary Matching Engine. But what does he do? What does he listen to? He’s going to come up, and he’s going to listen to, not the ports. Because the order in which the UDP packets are arriving at the passive Matching Engine, they’re totally no guarantee there. So what he actually listens to, is the Matching Engines output. He’s able to, and we’ll see some messages later. He’s able to essentially identify only those messages that the clients submitted. And he’s going to essentially run the identical state machine, and actually the identical code that the primary Matching Engine is running. 

