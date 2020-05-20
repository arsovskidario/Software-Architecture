
# Tactis for availability:
 main focus is the availability of the service that is provided by our system, therefore 
	tactis for availability focus on finding the fault , recovering from it and preventing it from
	occuring again 

## Fault detecting 
- before we can repair a system we first need to find the fault that is cousing harm to our system
- Detecting faults can be done by *monitoring* which is a component with a soul purpose of monitoring the states of other system components and detecting irregolarities based on system specifications.
kl		
- **Ping/echo** is a tactic in which a monitoring component pings(signals) another component from the system and waits for a response in some time interval. If the elements doesn't reply in time then it is considered broke (timed out). Ping/echo is used in nodes connected by an IP. 

- **Heartbeat**, the component sets signals to the monitor in some interval of time, if the signal is received then the component is persumed as alive and working.

- **Voting**  a system where three components are given the same input and are expected to return the same output. If the output is not the same there is a fault. Implementing the system can be done by replicating the components so they have the same logic and always have to return the same output. If the output is different in one component that it's not working properly. Problems in this implementation can be the fact that the logic can be implemented in a bad way for all the components. Diversity in the production of the components ensures different implementation logic and less failure.

- **Exception Handling**

## Recover from faults 
 - **Active redundancy** - maintain multiple copies of a component that work syncroniously with the main component. If the main component fails one of the copy ones will stark working as the main component. All of the copy components are maintained and receive data at the same time the main one does.
 - **Passive redundancy** - same principle as active redundancy the main difference being that the copies are updated periodically by the main component and not at the same time. 
- **Exception handling** when an error occurs the system enters various states that the developer has created in case of failures. 
- **Rollback** -  the system keeps a copy of a state when it was working flawlessly and if a failure occurs it returns to the state it was working in. 
- **Retry** used in servers and networks where faults are expected, retrying the same operation in hopes of it running without a problem again.
- **Shadow mode** - then new component works in parallel with the main component and if it gives the same outputs it can be used as a substitute.
		

## Prevent faults ( Runtime based ) 
- *Removal from service*  temporary place a component in a out-of-service state and possibly restarting it.


# Modifiability 

**coupling** = probability that a a modificiation of one module will propagate to other models.
	high coupling is an enemy of modifiability
	**loose coupling** means basically using abstractions of classes to use them instead of directly instantiating them so for example if in the near future the class changes the abstraction will stay the same and wont affect your class.

Methods for reduce coupling :
-	Encapsulatation 
		
![java_loose_coupling]([https://raw.githubusercontent.com/arsovskidario/Software-Architecture/master/images/java_Loose_Coupling_Example.jpeg?token=AHAENOWHXD6ZN62ISNYJBY26ZYN3M](https://raw.githubusercontent.com/arsovskidario/Software-Architecture/master/images/java_Loose_Coupling_Example.jpeg?token=AHAENOWHXD6ZN62ISNYJBY26ZYN3M))
	
**cohesion** - do one thing and do it well approach

High cohesion means to keep similar and related things together, to couple or fuse parts which share content, functionality, reason or goal. In other words, low cohesion could for example mean a function/class/code entity which serves multiple purposes rather than being "to the point". One of the carrying ideas is to do one thing and do it well. Others could include the obvious fact that you don't replicate similar functionality in many places. This also improves locality of the code base, certain kinds of things are found at a certain place(file, class, set of functions, ...) rather than being scattered around.

**[Cohesion Examples](https://softwareengineering.stackexchange.com/a/163120/352227)**

**High Cohesion and Loose coupling  is the key**

Basically : Не давај директан достап до класови, т.е само сс интерфејси давај достап и за cohesion треба свак клас тачно да работи тој за што е определен т.е сви функцие на едн клас да манипулирав сс његови елементи а не да има функцие што работив без да ги користив/манипулирав његоњи атрибути.

The architecture is easier and more affordable when it's changed in the start rather than some time after.

**Binding time of modification** = prepare the architecture for future modifications in order to avoid reworking the entire architecture


# Performance
*GOAL:* generate a response to an event within a given time 
response time is made up of processing time( system is working on response) and blocked time(system unable to respond)

*Processing time* consumes valuable (hardware and software) resources and time contributing to the overall processing latency.

*Blocked time* computation can be blocked because of resources.
-	contention of resources ( basically atomic values where only one component can use them at a time)
-	availability of resources ( resource is unavailable in the system due to issues)
-	dependency on other computation(waiting for a result from computation of another component)

### Control of resources demand
Manage demand for the resources by reducing the overall number of events or limiting the response rate of the system.

- Manage sampling rate = reduce the frequency of a enviromental data being captured
- Limit event response = store incoming events into a queue until it's processed. If the queue is full you can drop the events and log them.
- Prioritize events = same as limit events response but you use a priority queue to prioritize given events.
- Reduce overhead 
	- co-location of cooperative components ( putting components working towards the same goal into the same runtime software component to avoid subroutine calls)
	- periodic cleanups of resources (ex. hash tables and virtual memory maps that need to be reinitialized)
	- execute on single-threaded servers
- Bound execution times = limit execution time that is used to respond to events
- Increase resource efficiency = improve the algorithm in critical areas.

### Manage Resources
If you can't control the demand of resources you can simply trade off resources.
This tactic is mainly applied to the processor.

- Increase resources = faster processors,additional processors,additional memory 
- Introduce concurrency = use different threads to process different streams in order to achieve parallel processing
- Bound queue sizes = if you create a cap on the queue that processes events than you can limit the computational power of your system
- Schedule resources = if multiple components are trying to use the same resource you can schedule the use of it so everyone gets a share just not in the same time.