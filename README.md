# Solidity Adventures

One dinosaurs journey learning how to write Smart Contracts in Solidity with examples.

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





