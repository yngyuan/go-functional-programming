## Functional Programming in Go

### 1 Higher Order Functions

#### 1.1 An over view of HOF
##### Functional programming
- Functional programming is the process of building software by using pure functions, avoiding shared state, mutable data, and side effects.
- Functions in Go are first-class citizens.

##### Features of Higher Order Functions
- Can be passed as parameters
- Can be returned from other functions

#### 1.2 Exploring Pure Functions
##### What are pure functions
- The output of a pure function depends entirely on the input and nothing else.
- There is nothing that can change its output.
##### Why use pure functions
- Functions with the same input return the same output
- There is no hidden state in between that can change it.
- Idempotent - it doesn't matter how many time we call the functions
- The output of the function depends entirely on the output and nothing else
- Race conditions due to side effects are not possible with pure functions

#### 1.3 Encapsulating External State
##### Encapsulation of state using optionals
- Pure functions are great to encapsulate state with optionals
- Optional s act as containers
- We can prevent concurrency issues easily
- Makes testing with isolation easier

#### 1.4 Understanding Closures
##### What are closures?
A closure is a function value that reference variables from outside its body.

##### Why use closures?
- You can reference a variable without being passed as parameter and change its state.
- Don't have to use global variables.
- Are safer to use by isolating data.
- Extra: Create a middleware using a closure.

### 2 Function Literals and Streams
#### 2.1 Overview
##### What is Function Literal
A functional literal is an unnamed function that is later bound into a variable when used.

##### Why use function literals
- Can be used inside other functions
- It has the advantage of using the parameters of the function it is nested in
- Comfortable and easy one-time usage

##### What are streams?
Steams allow you to work with sequence of elements, modify them or generate new data based on a specific rule or condition.

##### Steams in Go
- Powerful, easy to use and convenient
- Easy to do computations over slices or arrays
- Popular: map, reduce, filter
- Not support by default in Go(Go's lack of generics)

#### 2.2 Anonymous Functions
##### What are anonymous functions?
- functions without names
- have the same structure as the named functions
##### Why 
- Convenient and easy to use for one-time usage
- Great readability when using multiple non-complex anonymous functions
- More self-contained code
#### 2.3 Invoking Functions Directly
##### Advantages of self-invoked Functions
- keeping the global state clean
- Great at creating its own scope
- Garbage collection friendly
#### 2.4 Lambda Expressions
##### What are Lambdas?
- Sometimes anonymous functions are considered as lambdas
- Lambdas have a full-form structure in Go

lambda expressions in Go don't have a minimalistic and a different way to represent other than just using an anonymous function

#### 2.5 Reactive Programming
- A programming paradigm that is oriented around data flow and change
- Any real-time application is a Reactive system

##### Functional Reactive Programming 
- a form of functional programming which uses Reactive programming paradigm
- Reactive programming using mostly map, reduce and filter
- RxGo package

#### 2.6 Common Methods for Streams
- Streams allow you to work with sequence of elements modify them or generate new data based on specific rule or condition.
##### Why use streams
- good abstraction
- productive
- convenient and intuitive

##### How to Achieve Streams in Go
- Copy-paste for different types
- Interfaces
- Reflect package
- Code generator

### 3 Immutability and Monads
#### 3.1 Overview
- An immutable data structure's state canot be changed after it is created
- It behaves like it is in a read-only mode but with thread safety in mind and some other goodies
##### Advantages of Immutable Data Structures
- Easier to work with
- Thread safety
- Maintainability
- Readability
- Test easier
##### Should we always use them?
- Creating a new object to hold the modified values
- Use a lot of resources

#### 3.2 Immutable/Mutable Data Structures
##### Why use mutability
- Most imperative languages provide it by default
- Easier to reason in terms of everyday objects
- "Lazy developers"
##### Comparison
- Mutable
    - map
    - slice/arrays
    - channels
- Immutable
    - string
    - pointers
    - interfaces
#### 3.3 Using const to Declare Variables
##### Why use const?
- Speed(compiler optimizations)
- Safety (immutability)
- Flexibility (untyped operations)
- Readability

##### Using const
- Create read-only variables (Constants) 
- Typed and untyped
#### 3.4 Immutable Maps
- A collection of Key:Value pairs
- Synonyms:
    - Hashmap (java)
    - dict (python)
    - HAMT (Hash Array Mapped Trie)
    
##### Immutable Maps in Go
- New()
- Set()
- Get()

##### HAMT
- Hash array mapped trie(Radix Tree)
- better resouce management
- immutable
#### 3.5 Immutable Structs
##### How to Create an Immutable Struct?
- All fields private, non exported(lower case)
- Member initialized on construction
- No setter or mutators allowed
- Package visibility

#### 3.6 Building a Named Monoid
- In abstract algebra, a monoid is an algebraic structue with a single associative binary operation and identity element.
- Identity Element
    - Eg: Multiplication, 0 Addition, ""Concatination
 
##### Functors/Monads?
- Monads and Functors are not related to monoid
- A functor is a container of a type that, when subjected to a function maps from a->b, yields a container of type b
- A Monad is a special type of Functor
### 4 Lazy and Eager Evaluation
#### 4.1 Overview
**Lazy evaluation** is an evaluation strategy which holds the evaluation of an expression until its value is needed
##### Advatanges
- It allows the language runtime to discard sub-expressions that are not directly linked to the final result of the expression
- It allows faster computations
- It allows the programmer to access components of data structure out-of-order after initializing them, as long as they are free from any circular dependencies
- Great for using not-frequently access data

**Eager evaluation**, an expression is evaluated as soon as it is bound to a variable
##### Advatanges
- More control
- More transparent
##### Disadvantages
- More responsibility for the developer
- Potential overhead(more memory intense)

#### 4.2 Using Closures
A closure is the combination of a function and the lexical environment within which that function was declared (mdn)

#### 4.3 Emulating Generators Using Channels and Routines
- Generator pattern, sometimes known as iterator pattern is used to generate a series of values which then in itself used to produce an output

##### how does it work
- Goroutine is used to generate the new data
- Data are sent through the channels and returned
- We can range thorough the new data
- Consumer consumes the new data
- Generates output

#### 4.4 Avoiding Re-Evaluation Using Sync
Sync Package has primitives and mechanisms to deal with concurrency.

Important Sync Package Primitives
- sync.WaitGroup(add, wait, done methods)
#### 4.5 Short-Circuit Evaluation
Short-circuiting is where an expression is stopped being evaluated as soon as its outcome is determined.
- The support of short-circuit evaluation is not explicit in Go, but still we can back it up with some examples that prove that it is supported in Go. 

### 5 Currying Functions in GO
#### 5.1 Overview
Currying is the process of converting a function that has a lot of parameters into a sequence of functions that each have only a single parameter.
##### Pros
- Currying a lot of functions is easier/nicer to use
- Ease of reuse
- Build more sophisticated functions by combing multiple
##### Cons
- May bring side effects if the developer is not used to

Partial functions:
- have several parameters

Currying:
- have just one or zero parameters
- can be considered a type of partial function application
#### 5.2 Partial Functions
A function that takes a function with multiple parameters and returns a function with fewer parameters.

Partial Function Application:
- Providing functions with fewer parameters than originally expected

#### 5.3 An Attempt to Curring in Go
Currying is the process of transforming functions with a lot of parameters to a series of functions with just one parameter.

Uncurrying is the opposite process to currying, and can be seen as a form of de-functionalization

### 6 Design Patterns
#### 6.2 Exploring Monads
Monads
- Monad is a design pattern that helps us to build generic types by using function composition.
- A Monad is a particular type of functor
##### What is a functor
- Superclass of monads
- An abstract name for a container
- The ability to apply a function to the items inside the container
- A function is a container of type a that, when subjected to function that maps from a->b, yields a container of type b

##### What is Monad
- A special kind of a functor
- takes a type(meat), and turns it into a new type.(meat burrito)
- Return creates a new container
- Bind takes valus in container, applies to function and joins them together as we go along

##### Error Handling Monad
- Avoid using err !=nil all the time
- Any interface{}
- Monad: func(error)(Any, error) {}
- Return(Any)Monad {}
- Bind(Monad, func(Any) Monad)Monad {}

##### Pros
- Readability
- Faster to write and easier to manage
##### Cons
- Losing compile-time type safety
- Developers need to know about monads

#### 6.3 Observer Pattern
Observer Pattern
- a design pattern in which an object, called the subject, maintains a list of its dependents, called observers, and notifies them automatically of any state changes, usually by calling one of their methods.

Pub/Sub
- Uses an extended version of observer pattern
- Uses a broker (message queue)
- The core works the same
- Publish(observable), subscribe(observer)
#### 6.4 Decorator Pattern
Decorator Pattern
- the decorator pattern adds new functionality to an existing object without altering its structure
- it is a structural pattern as this pattern acts as a wrapper to an existing struct.
- example in other language
    - @app.route('/') // flask (python)


##### Why use decorator
- Add/remove behavior dynamically
- Does not affect other structures
- Simple and powerful
### 7 Testing Functions in Go
#### 7.1 Benefits of Testing FP Code
##### Why test your code
- Confident about the functionalities
- Leads to refactoring
- Confident in adding new changes without breaking the system
- Helps you identify bugs in early stages of development

##### Types of Software Testing
- Functional Testing
    - Unit Testing
    - Integration Testing
    - Acceptance Testing
- Non-Functional Testing
    - Security Testing
    - Performance Testing
    
#### 7.2 Unit Testing
- Test a single unit
- Fast
- Close to the source code

##### Unit Testing in Go
- Part of standard library
- Favors eros instead of assertions
- Using test and net/http/httptest packages
- Third-party
    - Testify
##### Usage
- using test package
- filename_test.go
- t *testing.T
- Use t.Error, t.Fail, t.Logf
- Does not use assertions
- Using Test Tables
    - Easier to test
    - can test multiple rules at the same time
    - include corner cases
 - Go test -cover for testing coverage
 
#### 7.3 Using httptest
- Using net/http/httptest packages
- Check headers, body, and status codes

#### 7.4 Using Testify
- Popular assertions and mocks out of the box
- Assertion based instead of error based
- Great mocking functionalities
    - databases, APIs

