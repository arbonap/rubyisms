## What would you say is the one feature that distinguishes Ruby from all other programming languages?

- One unique feature in Ruby that distinguishes it from other programming languages is the idea of a Symbol. I believe a Symbol takes up less memory than a String.


## What is the difference between “each” and a “for loop”? What is another alternative to using a “for loop”?

- The difference between `.each` is that in Ruby, `.each` is a common enumerable used to loop through an iterable (i.e, an array or collection). Unlike a `for loop`, `.each` takes in a block. `.each` performs whatever is inside the block it is given on the iterable. Utilizing `.each` is much more Ruby-like and considered the "Ruby way" than using "for loops". For loops are more standard in other languages, such as Python. Another alternative to using a "for loop" in Ruby is using `.map`. `.map` is almost exactly the same as `.each`, except for that `.each` returns the original object it was called after running the block for each value. However, `.map` is almost the same except it returns a new object with those changes.

## What are two ways for grabbing the last two letters in a String?

- You can use the `.slice` method, like so:
>>"example".slice(-2..-1)
=> "le"

- Or, you can also use bracket notation to slice:
>> "example"[-2..-1]
=> "le"

## What is the difference between the “initialize” and the “new” method on an object?

- When writing a class, you have to tell it how it will first start off. What attributes will a class begin with? Enter the special `def initialize` method.
- When you want to instantiate a new object, you call `.new` on that class, give it certain specific arguments, and save it in an instance variable.

## What is the difference between “require” and “load”? Give practical examples of when to use each of them.
- Both are methods used to import libraries, modules, or gems.
- The difference between `require` and `load` is that `require` only loads in the library once, meanwhile `load` imports the library every time it's called upon, even if said library is already in memory. There's also different syntax usage between `require` and `load`. With `load`, you need to add the full name of the library, while with `require` you don't need to add `.rb` to the end of the path.
- In my personal experience, use of `require` is a lot more common than `load`, because it doesn't unnecessarily import a library every time it's called upon, but rather keeps it in memory.
- A practical example of when to use `load` is when you need to force something to reload a lot, like a test server.

## What's the difference between a String and a Symbol? What are the benefits/reasons for using Symbols?

- A string is something in between single or double quotes, like this: `"beyonce"`. Strings are mutable.
- In Ruby, a symbol is something like this `:beyonce`. It looks like a string, but it is preceded by a colon and is not in quotes. Symbols are immutable, and something unique to Ruby compared to other programming languages.

Because symbols are immutable, symbols take less memory than strings do. Because of this, programs are more performant when utilizing symbols over strings. In Ruby, symbols are used as identifiers. Symbols are usually keys in a hash, like a params hash.

## What is the difference between an Array and a Hash? What is the similarity between them?

_Differences between an array and hash_:
- An array is a collection of any object, while a hash is a a collection of key-value pairs.
- You index into an array via a numerical index. You index into a hash via its unique key, which many times is a symbol.
- Arrays are ordered, hashes are unordered.
_Similarities between an array and hash_:
- Both are data structures used to store data.
- If you know the index of the array and the key of the hash you're trying to index into, indexing into both has constant lookup time.


## Why would you ever mix-in a module to a class as opposed to using inheritance? Could you provide practical examples?
- Mix-in's are inheritance based, but it's greater incapsulation for a set of qualities you'd want for a class

## What is an eigen-class (also known as singleton class)? What is the benefit of having it? Could you provide examples illustrating the benefits?

- I have never heard of a singleton class.

## Please explain how “super” works.
- `super` invokes the method with the same name in the parent class (or superclass). In other words, it calls the same method, but looks for the method definition "above" in the class hierarchy. In other words, it calls the method definition in whatever class the current class you're in inherits from.

## Please explain how “yield” works.
- `yield` is kind of like a soft return. I say "soft" in the sense that the method "keeps going", assuming there are actions that come after the `yield` in the method. In other words, a `yield` lets you inject a block somewhere else in a method.

## What is the difference between a lambda and a proc? What are some practical uses for each? Any other alternatives?

- A lambda is like an anonymous function.
- A proc is like a more flexible block. Procs don't check the number of their variables, but lambdas do.
- I believe you can use lambdas to create closures, like in JavaScript.

## What is the difference between using backticks and using the “system” method to invoke a shell command?
- `system("takes in a string")`, meanwhile
` `backticks do not take in a string` `

## Have you heard of the Ruby 2 Refinements feature? If so, please explain the usage and benefits.

- No, I have never heard of this.

____________
<!-- Rails questions -->

## What makes Rails special as a web development technology compared to all others?

- Rails is a unique framework because of its DSL, or Domain Specific Language. The Rails DSL makes it very human-readable. Moreover, Rails can take advantage of large community of open source maintainers that (fairly) reliably maintain gems. Also, Rails takes advantage of Ruby as a language. Ruby is flexible, dynamic, has many handy methods, and lots of syntactic sugar that makes developing easier on the developer. Lastly, Rails is very opinionated. There is a so-called "Rails Way" of developing, and the framework pushes you to develop in that way.

## What is useful about Rails Console? Could you provide practical examples of using it for live websites?
- Rails Console allows you to play around with and test your code. You're allowed to instantiate a particular test object, and play around with it to better understand its behaviors. For example, you can take advantage of `rails c` if you want to quickly hand-test if a model validation successfully went through after instantiating a particular object. If your object   

## Please give an overview of MVC? What is a common problem in writing MVC code in Rails? What is the remedy for it?

- MVC is supposed to emphasize a clear separation of concerns, where the view and controller should know little
about the model, and the model should know little about the view and controller.
overarching architecture.
The model’s purpose is to create an interface for the data; Rails utilizes a database to store data. The model provides an internal interface (API) that allows other parts of the app to interact with it. The view contains the user interface and displays
the data. The controller receives the user input, and handles requests from views and updates the model by changing the
model’s state accordingly. Having a separation of concerns makes it easier to add new features
to a codebase, and facilitates maintainability and readability of an application.
- A common problem in writing MVC code in Rails is that developers sometimes write very fat models, or put too much logic in their views. In order to remedy this, developers should try to transition more of their code in their model to their controller. Similarly, there should not be a lot of complicated logic in the views, since this violates the "separation of concerns" principal. Developers can take advantage of encapsulating their code into partials when there is lots of code in the view that is repeated.


## What is the difference between hook methods and filters?
-


## When do you use named scopes? What are the benefits?
-

## What is so special about the Asset Pipeline?
-

## Any reason you would write your own Rails Helpers?
-


## What are the benefits of using migrations? If you screw up a migration that you have already committed to the source code repository (e.g. named a column badly or gave it the wrong data type), what do you do to fix it?
-


## What are some ways of optimizing the performance of slow web pages in a Rails application? Please mention 3 at least.
-

## Rails 4 replaced attr_accessible with a new alternative. What is it and why was that done?
- `attr_accessible` allows developers to whitelist attributes and allow them to be updated in bulk in the model. This was replaced with strong parameters. Now protecting attributes is done in the controller, where it belongs, instead of the model. This was done for security purposes, and also to better follow 'the Rails Way', which values skinny models.

## Why would you place a gem in the :asset group in Gemfile? Why would you place a gem in the :development group? Please explain.
-


## Have you used Rails Observers before? If so, what was the reason? What are they useful for?
- I have never used this before.

## Have you written your own Rails initializer before? If so, why? Please explain what they are useful for and at one point they get initialized in the Rails web application loading process.
- No, I have never written my own Rails initializer.


## Have you written a Rake task before? Why would you write a Rake task? How do you write it add it to a Rails application? Do you have any code design preferences for writing a Rake task?
- No, I have never written a Rake task before.

## How does Rails help developers ensure data security?
- Rails ensures data security a number of ways. One way is with strong params. Strong params is the idea where you whitelist mass-assignment protection. It protects attributes from end-user assignment. Blacklisting is not safe. Also, another way Rails ensures data security is with its CSRF token. This token is to prevent Cross-Side scripting attacks.


## What approach do you follow in Rails in order to build interactive webpages relying on Ajax?
-
