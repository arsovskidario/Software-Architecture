# Designing Architecture

## Attribute Driven Design (ADD)
- It is generally used when we want to have some kind of architecture not a complete one but one "workable" architecture  that can be used to start the developing process based on some already defined quality requirements.
- Before we start using the iterative process we first need to prioritize 10 requirements which are called **drivers** because the process of developing is "driven" by those same prioritized requirements

### Steps in ADD
1. Select a module that will be decomposed
	- we select a model that will be decomposed into smaller sub-modules 
	- we define the interface that will communicate with the sub-modules	
		 
2. Look at the prioritized requirements and identify which tactics are going to be beneficial for use 
	- *Note* : if we are using frameworks the pattern for the architecture will be defined according to that same framework we are using 
		 
3. Creating sub-modules based on the chosen tactics
	- *Example* : If you have chosen modifiability then the sub-modules will be created in an approach that applies loose-coupling and high cohesion.	
		 
4.  Repeat the steps until every requirement is satisfied. <br/>

---

**Pro tip** : Building a systems infrastructure (middleware) is more beneficial because the infrastructure defines how the components will communicate between each other. If you for example build functionality first then it will be hard to test the system to see if the functionality is working as planned. 
