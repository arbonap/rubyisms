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
- Rails Console allows you to play around with and test your code. You're allowed to instantiate a particular test object, and play around with it to better understand its behaviors. For example, you can take advantage of `rails c` if you want to quickly hand-test if a model validation successfully went through after instantiating a particular object. Moreover, you can play around with Rails methods with the Rails Console.

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
- A hook method is like `include`, when you include instance methods, and `extend` when you want to include class methods.
- A filter is a special Rails controller method. An example would be a `before_save` filter, which calls a method before it saves to the database.


## When do you use named scopes? What are the benefits?
- I believe you use named scopes when you're using something like a state-machine game, and you can have your different states as different namespaces. For example, you can have an :admin namespace or a :user namespace. The benefit is that it organizes your logic better.

## What is so special about the Asset Pipeline?
- The Asset Pipeline minifies/compresses JavaScript and CSS assets. It allows you to write these assets in other languages, like Coffeescript or SASS.
- If you have Sprockets enabled, it caches assets in development and production.


## Any reason you would write your own Rails Helpers?
- I would use a rails helper if I had some complicated view logic that I wanted to DRY up, take out of the view, and use the rails helper to help me write some more complicated HTML.


## What are the benefits of using migrations? If you screw up a migration that you have already committed to the source code repository (e.g. named a column badly or gave it the wrong data type), what do you do to fix it?
- Migrations are how you change and update your schema.rb (or database tables) in a Rails app. A benefit to using migrations is that you do not have to directly write lots of raw SQL, and can use lots of Rails sugar to help you accomplish database changes.
- To fix a messed up migration, you want to `rake db:rollback`. After rolling back, rewrite or correctly edit your migration file, and then after you're done, type `rake db:migrate` in the terminal in order to enact your schema changes.
- Try checking your work by writing up RSpec tests that test the model you're working on. Also, may try to hand test your changes in `rails c`. Then commit your changes and push up to the master branch.


## What are some ways of optimizing the performance of slow web pages in a Rails application? Please mention 3 at least.
- You can use different caching mechanisms.
1. You can utilize the `fresh_when?` method, which checks an assets' etag. If the etag hasn't changed, the view will cache and have a `304` status.
2. You can replace slower n + 1 queries written in Ruby/Active Record with more efficient raw SQL queries
3. You can use Russian Doll caching. This is when you use a key-based cache expiration. Whenever the ‘inner’ cache expires, we also want the outer cache to expire. But if the outer cache expires, don't expire the inner cache.

## Rails 4 replaced attr_accessible with a new alternative. What is it and why was that done?
- `attr_accessible` allows developers to whitelist attributes and allow them to be updated in bulk in the model. This was replaced with strong parameters. Now protecting attributes is done in the controller, where it belongs, instead of the model. This was done for security purposes, and also to better follow 'the Rails Way', which values skinny models.

## Why would you place a gem in the :asset group in Gemfile? Why would you place a gem in the :development group? Please explain.
- I am not familiar with the :asset part of a Gemfile. I started learning Rails with Rails 4.
- You put gems in the `:development` part of a Gemfile if it's a gem that you only use in a development environment. For example, gems used for testing code are put in `:development`.


## Have you used Rails Observers before? If so, what was the reason? What are they useful for?
- I have never used this before.

## Have you written your own Rails initializer before? If so, why? Please explain what they are useful for and at one point they get initialized in the Rails web application loading process.
- No, I have never written my own Rails initializer.


## Have you written a Rake task before? Why would you write a Rake task? How do you write it add it to a Rails application? Do you have any code design preferences for writing a Rake task?
- No, I have never written a Rake task before.

## How does Rails help developers ensure data security?
- Rails ensures data security a number of ways. One way is with strong params. Strong params is the idea where you whitelist mass-assignment protection. It protects attributes from end-user assignment. Blacklisting is not safe. Also, another way Rails ensures data security is with its CSRF token. This token is to prevent Cross-Side scripting attacks.


## What approach do you follow in Rails in order to build interactive webpages relying on Ajax?
- I would try to use a frontend framework, such as React, to organize my frontend code. I'd try to follow the common setup of organizing React code with components, containers, actions, and reducers.

## How does Git differ from SVN, CVS, and Visual SourceSafe?
- Git differs from other systems of version controls because it calculates the deltas, or the change, between different code. Other


## Please provide examples for when the "git stash" command is useful.
- Say you're in the middle of completing a messy feature, and want to work on something else. You want to stash your changes if you are in the middle of a story, and need to move to a different branch. You stash your dirty changes. Git keeps them on a stack, which you can then pop at a later time.

## What is the difference between "git commit" and "git push"?
- A git commit is like a snapshot. It is like a save-point of the state of your code. Ideally, you commit your code when you're in a logical stopping point, and your code isn't broken.
- Ideally, a git push is when you push up your code to Github when you've finished a feature. Your code is then on Github, or the cloud. It's not just on your local machine now, but also in a repository where other developers can pull it down and build further upon your code.

## Have you ever used the Git Rebase functionality? If so, why and how does it compare to the Git Merge functionality?
- Yes, I have used interactive rebases to squash my commits in my Open Source work. I have worked on Open Source projects in the past where the developers reviewing my PR's wouldn't accept my working-code without squashing my commits into a cohesive commit-story. Rebasing in git re-writes history. It provides a linear story. Merging does not leave a linear story. Merging leaves an extra merge commit, which many Open Source developers are not happy with in my personal experience. Moreover, merging gives you two sets of commits that are the same changes.

## Mention 2 practical uses of Git branches.
1. You can create a branch if you want to play with experimental code in an environment that will not introduce breaking changes into master.
2. Branches are a way f or developers to parallelize work. A team of software developers can take advantage of branches to work on different features at the same time.

## What is the difference between "git pull" and "git fetch"?
- A `git pull` is both a `git fetch` and afterwards a `git merge` in one.
- A `git fetch` updates your remote tracking branches.
## What are some practical uses for the "git cherry-pick" command?
- A `git cherry-pick` is a good way to take a commit from a feature branch and rebase it on top of master.

## Do you have a favorite release branching strategy with Git? If so, please explain in detail.
This is my usual workflow:
1. git pull --rebase master
2.

## Please explain GitHub's Fork functionality
- A fork is when a developer makes an individual copy of a codebase on Github that is linked to their personal Github account.

## What is a GitHub Pull Request and what is it useful for?

## What are they ways of contributing to an open-source project on GitHub using Git?

## What are the commands needed to share your local code changes with the team?

## Suppose you made a few code changes that you no longer want. How do you reset them to the last version stored in Git?
- It depends. If you've already committed and pushed this commit up to master, you can go to the master branch and do `git revert <shah here>`. Git reverts undoes a commit by doing a new commit and then tacking the new commit onto the existing project.
- You could also do `git reset HEAD~<number of commits you want to go back> --soft`. The `--soft` flag keeps the staged changes. The `--hard` flag wipes staged changes away-- be very careful with this option.
