## Functional Programming in Go

### 1 Higher Order Functions

#### 1 An over view of HOF
##### Functional programming
- Functional programming is the process of building software by using pure functions, avoiding shared state, mutable data, and side effects.
- Functions in Go are first-class citizens.

##### Features of Higher Order Functions
- Can be passed as parameters
- Can be returned from other functions

#### 2 Exploring Pure Functions
##### What are pure functions
- The output of a pure function depends entirely on the input and nothing else.
- There is nothing that can change its output.
##### Why use pure functions
- Functions with the same input return the same output
- There is no hidden state in between that can change it.
- Idempotent - it doesn't matter how many time we call the functions
- The output of the function depends entirely on the output and nothing else
- Race conditions due to side effects are not possible with pure functions

#### 3 Encapsulating External State
##### Encapsulation of state using optionals
- Pure functions are great to encapsulate state with optionals
- Optional s act as containers
- We can prevent concurrency issues easily
- Makes testing with isolation easier

#### 4 Understanding Closures
##### What are closures?
A closure is a function value that reference variables from outside its body.

##### Why use closures?
- You can reference a variable without being passed as parameter and change its state.
- Don't have to use global variables.
- Are safer to use by isolating data.
- Extra: Create a middleware using a closure.

### 2 Function Literals and Streams
#### Overview

#### Anonymous Functions

#### Invoking Functions Directly

#### Lambda Expressions

#### Reactive Programming

#### Common Methods for Streams

### 3 Immutability and Monads
#### Overview

#### Immutable/Mutable Data Structures

#### Using const to Declare Variables

#### Immutable Maps

#### Immutable Structs

#### Building a Named Monoid

### 4 Lazy and Eager Evaluation
#### Overview

#### Using Closures

#### Emulating Generators Using Channels and Routines

#### Avoiding Re-Evaluation Using Sync

#### Short-Circuit Evaluation

### 5 Currying Functions in GO
#### Overview

#### Partial Functions

#### An Attempt to Curring in Go

### 6 Design Patterns
#### Popular Design Patterns

#### Exploring Monads

#### Observer Pattern

#### Decorator Pattern

### 7 Testing Functions in Go
#### Benefits of Testing FP Code

#### Unit Testing

#### Using httptest

#### Using Testify


