# Solidity Adventures

One dinosaurs journey learning how to write Smart Contracts in Solidity with examples.

# Require 

The `require` keyword is a concise approach to the traditional style of  `if (predicate) return;`

### Format

`require ({ predicate });`

Where `predicate` needs to resolve to true in order to continue function execution.

# Events



# Modifier Functions

Modifier functions are a shorthand equivalent of interfaces/protocols which utilise predicates.

It provides a concise mechanism to a required predicate within a function definition.

This functionality comes with an additional gas cost but reduces possible cyclomatic complexity of given functions.

### Declaring a modifier function

The `modifier` keyword defines a function.

The `_;` line refers to the body of the parent function.

```
modifier checkSomething({type} value) {
	require (predicate);
    _;
}
```

### Usage of modifiers

Modifier are declared as part of the definition of a parent.

```
event Notify(bool isNotified);

modifier checkSomething(unit value) {
	require (value > 1);
    _;
}

function doSomething(uint number) public checkSomething(number) {
	Notify(true);
}

function runFunctions() public {
	
    // Will not execute the Notify event
    doSomething(1);
    
    // The Notify event is executed	
    doSomething(2);
}

```







