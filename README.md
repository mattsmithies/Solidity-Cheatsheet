# Solidity Adventures

One dinosaurs journey exploring the interesting facets of Solidity.

This is not an introduction and we suggest to start your Solidity journey using the following resources. We are exploring the more interesting elements of the language.

- [CryptoZombies by Loom Network](https://cryptozombies.io/)
- [Zastrin - real-world projects](https://www.zastrin.com/)

# Require 

The `require` keyword is a concise approach to the traditional style of  `if (predicate) return;`

### Format

`require ({ predicate });`

Where `predicate` needs to resolve to true in order to continue function execution.

Upon failure of the predicate in a require the function will halt.

# Events

An event is declared with the `event` keyword, it provides a observer style callback for a given client.

```
event Notify(bool isNotified);
```

When `Notify` is called with a `bool` value is passed, if the client is listening then it will be notified.

### Listening to event with web3 using Node client

After connected to the required network with reference to a given address.

```
var Contract = web3.eth.contract('ABI');
var Reference = Contract.at('CONTRACT ADDRESS');
var event = Reference.Notify();

event.watch(function(error, result) {
  if (!error) {
    console.log(result.args.isNotified);
  } else {
    console.log(error);
  }
});
```

The watch function referring to the `Notify` event will trigger and log out the result or error, if one exists. 

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







