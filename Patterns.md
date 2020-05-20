13.2

Tactics

Fitness

Lekciq



Many patterns are used for Connector and components(dynamic runn time )

For static (modules) layers is the most used pattern.

Best practice is to write the uses  of the layers.

layer_1 , layer_2 


Component-connector patterns :

Broker :
	- broker instance is created which communicated with the client and connects him to the server 
	+ if the server is not working the broker finds a working server 
	+ client is not concerned with the location of the server 
	- bad for permormance because the broker needs to find the server location in order to connect
<broker.img>

Model-View-Controller:
	context : user interface is easy to change 
	+ useful for frontend if you have a complex interface that the client will use with a lot of views
	- bad for use in small scale interfaces that wont be complex 

Client-Server Pattern
	+ Servers can serve requests for more than one client at a time 
	+ Sever is passive. Only when a client initiates contact, the server responds. So we save a lot of resources in this architecture
	+ Secure . Servers can control how you access them
	+ Easily upgradable 
	+ Centralized data 
	- servers can be a bottle neck
	- server single point of failure 

Peer-to-peer:
	* components can be a server and a client
	+ great for handling vast ammounts of trafic (a lot of clients) Scalability
	+ no server cost Efficiency 
	+ no single point of failure Adaptability 
	- security ( for example if one client is affected everyone will get virus)
	- leechers 

Shared data pattern : 
 	+ scalability more clients can you stored data 
	+ reduce data duplication
	- security - infected files can spread and corupt	
	- single point of failure 

