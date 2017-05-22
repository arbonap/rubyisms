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
- Git differs from other systems of version controls because it calculates the deltas, or the change, between different code. Git takes snapshots of code, rather than storing all versions of code. Other version control systems such as SVN store all versions of code on a sever, and then developers have a local copy of the files on their computer. Older versions of version control systems do not allow more than one developer to checkout or use a particular file at a time, creating bottlenecks.


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
- To delete a branch on my local filesystem, I do `git branch -d <name of my branch>`
- To delete the branch from my terminal on Github, I do `git branch origin :[name of my branch]`

## Please explain GitHub's Fork functionality
- A fork is when a developer makes an individual copy of a codebase on Github that is linked to their personal Github account.

## What is a GitHub Pull Request and what is it useful for?
- Pull requests let other developers know about the changes you've made to a shared Github repository.
- Pull requests are very useful for other developers to do Code Reviews. Developers interested in your code can review the change, or discuss any future modifications. You can even ask for code review via Github now.


## What are they ways of contributing to an open-source project on GitHub using Git?
- If you are given rights to the particular repository, instead of forking, you can bypass forking the repository and just create a branch directly off of the repository in question. You can then create a Pull Request from your branch.
- You can fork the repository, and then create a pull request from your personal repository. You can then create a Pull request from your forked repo.

## What are the commands needed to share your local code changes with the team?
I prefer rebasing. This is my usual workflow:
1. On the master branch, I do `git pull --rebase` to get latest changes
2. git checkout -b `new branch name`
2. Write tests. Build features on said branch
3. Make sure tests pass.
4. `git rebase master` to get latest master changes, especially if you've been working on a particular branch for a while.
5. `git push origin some-branch -f`
I usually get a pull request at this point, and then rebase into master after approval via Github.

## Suppose you made a few code changes that you no longer want. How do you reset them to the last version stored in Git?
- It depends. If you've already committed and pushed this commit up to master, you can go to the master branch and do `git revert <shah here>`. Git reverts undoes a commit by doing a new commit and then tacking the new commit onto the existing project.
- You could also do `git reset HEAD~<number of commits you want to go back> --soft`. The `--soft` flag keeps the staged changes. The `--hard` flag wipes staged changes away-- be very careful with this option.


## What are the benefits of writing semantic HTML and CSS? Could you provide an example of semantic use of them and another example of non-semantic use of HTML and CSS?
- Using semantic HTML reinforces the meaning of information in webpages and web apps. Using semantic HTML5 also makes tags briefer, and clearer. Using semantic markup is an accessibility issue. You should use semantic HTML and CSS so screen-readers are able to more easily parse your code. It's best practice to use semantic HTML/CSS so your site better meets accessibility needs.
- Semantic HTML examples: using "<header></header>" for a site header, using "<footer></footer>" for a site's footer, and using "<h1></h1>" only for the highest level heading.
- Non-semantic use of HTML: Using something like "<div class="header"></div>" instead of using the header tag ("<header></header>"). Another example would be using a link tag for a button, when you really should use a button tag.

## What is the main difference between a div and a span? What are they useful for? Examples?
- A span is inline and meant for small chunks of HTML. Spans can be useful for emphasizing text within a div.
- A div is block-line and usually meant for larger chunks of HTML. Divs should be used to wrap sections of a document.

## What is the difference between liquid/fluid layouts and fixed layouts? What are the pros and cons in each? Please provide links to websites that have a liquid/fluid layout and others that have a fixed layout, 2 links each.
- Responsive sites: https://designmodo.com/hotel-travel-websites/, https://www.omadahealth.com/
- Unresponsive sites: https://www.warnerbros.com/archive/spacejam/movie/jam.htm, http://www.dolekemp96.org/main.htm

## What is the difference between margin and padding?
- Margin is within the div
- Padding is outside the div

## Say, you have two consecutive P elements on top of each other with a margin-top of 20px and margin-bottom of 10px. What will be the vertical distance between them in pixels once rendered in the web browser?
- 30px

## Please mention 2 ways of laying out product boxes with text-writing flow (left to right, and top to bottom) where each box contains the product image with a description below the image and a price below the description. 5 of them max fit horizontally, but if the user shrinks the browser window width, they flow downward fitting 4 or less horizontally, down to 1 minimum when the browser has very small width. You may provide both HTML markup and CSS stylesheet code.

- HTML:
```
<div id="container">
  <div class="row">
  	<div class="col one">
      <p>I love Selena Quintanilla! She is an amazing pop star. </p>
		</div>
		<div class="col two">
      <p>I love Selena Quintanilla! She is an amazing pop star. </p>
		</div>
    <div class="col three">
      <p>I love Selena Quintanilla! She is an amazing pop star. </p>
    </div>
    <div class="col four">
      <p>I love Selena Quintanilla! She is an amazing pop star. </p>
    </div>
    <div class="col five">
      <p>I love Selena Quintanilla! She is an amazing pop star. </p>
    </div>
  </div>
</div>
```

```
.col{
    color:#fff;
		float:left;
		margin:2%;
		width: 15%;
}
.one{
  background-color: red;
}

.two{
  background-color: green;
}

.three{
  background-color: #ff69b4;
}

.four{
  background-color: purple;
}
.five{
  background-color: blue;
}
@media screen and (max-width: 850px) {
  .col{
    float: left;
    width: 20%;
    color:#fff;
    margin: 2%;

  }
}

	@media screen and (max-width: 600px) {
		.col{
			float: none;
			margin:0;
			width: 100%;
		}
	}
```
## What is the difference between "display: inline;", "display: inline-block;", and "display: block;"? Please name some common elements that have "display: inline;" by default, the elements that have "display: inline-block" by default, and the elements that have "display: block;" by default.
- An element with "display: inline;" can't have a width or height, or vertical margin. It is used to display something in a sentence. Some common elements that have "display: inline" are "<em></em>"", emphasized text and "<i></i>"," italicized text.
- An element with "display: block;" can have width, height, and margin. Also forces a line break after the block element. A common element that has "display: block" by default are <p></p> paragraphs.
- If you want to resize an inline element and give it width, height and or margin, give it "display: inline-block;". Does not force a line break-- this allows other elements to sit to their left and right.

## What are the practical benefits of using Twitter Boostrap? Would you provide some examples? Please mention 3 examples where Twitter Bootstrap is immensely useful compared to not using it.
Practical benefits of using Twitter Bootstrap:
- If you have to build quickly, Bootstrap helps you quickly get started
- Responsiveness
- Large community support, and well-maintained
- Customizable
Drawbacks to using Twitter Bootstrap:
- Out of the box, Bootstrap is bulky and heavy and could potentially significantly add to load time
- It doesn't follow best practices in terms of semantic markup; you can be left with DOM elements packed with very long class names
- Makes scalability and maintenence more challenging
- Due to its popularity, your web application may not look unique

## How do you build a liquid/fluid layout with Twitter Bootstrap?
- Add media queries accordingly based on the screen size of the user's device
- Utilize Bootstrap's 12 column grid system when executing media queries

## Can you use any fonts that the web browser does not support by default? Please explain.
- Yes. You're able to include fonts via third-party API's like the GoogleFonts API. Or, you can include fonts not supported by default in your Rails app in app/assets/fonts directory.

## What does CSS stand for Cascading StyleSheets? Why the use of the word "Cascading"? Any practical benefits to it? Please provide examples.
- More than one  rule could apply to a particular piece of HTML. Because of this, there is a cascade algorithm that defines how exactly CSS rules apply, and which ones take precedence when rules collide.
The cascade is implemented by importance, specificity, and then order.

## How do you render a square image as circular using HTML and CSS?
- Increase the border-radius to 100%

## Please provide a practical example of using CSS3 Transitions and/or Animations.
- You can use a CSS3 fade-in transition on page-load.

## What is the benefit of using CSS3 Transitions/Animations over JavaScript animations?
- CSS3 transitions can have better run-time than JQuery animations, which can help with improving rendering and page load times. For example, adding many rendering/animation Javascript libraries can add to an app's load time.

## What is the benefit of namespacing JavaScript code and what is one way of doing it?
- You namespace code to avoid collisions with other variables or objects in the global namespace. It's a way to safeguard code from breaking if another piece of code uses the same variable or method name.
- One way of namespacing in JavaScript is using Object literal notation.

## Could you explain JavaScript's prototype-based Inheritance?
- A prototype is a working object instance. Objects inherit directly from other objects. Unlike with class inheritance in languages like Ruby, in JavaScript, class taxonomies are not an automatic given of prototypal object orientation.

## Everything is an Object in JavaScript. True or false? Please explain.
- False. Unlike Ruby, not everything is an Object in JavaScript. In JavaScript, an Object is like a hashmap. JavaScript also has primitives, which are things like strings, numbers, and booleans.

## What is CoffeeScript and what does it offer over JavaScript?
- CoffeeScript compiles to vanilla JavaScript. There's no interpretation at runtime. CoffeeScript became popular with many developers because of the syntactic sugar it brings. CoffeeScript is very ruby-ish and python-like with its flavor of syntax. It has significant white-space like Python. Because of this, CoffeeScript was very popular, especially with traditionally backend Rails developers because people found it more familiar syntax than vanilla JavaScript.

## Suppose you have a list of radio buttons contained in a div and upon selecting a radio button you want to have the selected radio button display a bolder font, have underlined text, and have a lightgray background color. What code would you write to accomplish this in HTML/CSS/JavaScript (It is OK if you only write HTML and JavaScript or only HTML and CSS to solve this. It is also OK to utilize all 3 languages. )

- HTML:
```
<div class="radioPanel">
 <label>First choice </label>
 <input type="radio" />
 <label>Second choice </label><input type="radio" />
<label>Last choice </label><input type="radio" />                  
</div>
```
- CSS:
```
.radioPanel {
    margin-left:20px;
    margin-right: 20px;
    padding-left:20px;
    padding-right: 20px;
    width: 500px;
    color:black;
    ```
- JavaScript:
```
$(function() {
    $('.radioPanel input[type="radio"]').change(function() {
        $('.radioPanel label').css('background-color', 'transparent');
        $('.radioPanel label').css('font-weight', 'normal');
        $('.radioPanel label').css('text-decoration', 'none');
        if ($(this).is(':checked'))
               $(this).prev('label').css('background-color', 'gray');
               $(this).prev('label').css('font-weight', 'bold');
               $(this).prev('label').css('text-decoration', 'underline');
      });
});
```
## Can you ever think of a use case for negative padding or margin?
- If you want to give an image a rollover with borders, you could use negative margin to accomplish this so the border size doesn't shift the layout on a rollover

## What is Ajax? Please provide examples of using it on a web page.
- Asynchronous JavaScript and XML. Instead of XML, though, nowadays we send over JSON. Basically, Ajax is a client-side protocol that is used client-side to communicate server-side without a need for a hard refresh. It helps avoid unnecessary entire page refreshes.
## What is the difference between document and window?
- Window is the browser window that holds the current browsing context, and document is the HTML page inside of it that represents the DOM.
## What is the recommended strategy for loading JavaScript on a webpage?
- You should load in your JavaScript last, so the webpage can load visibly before executing JS. I'd also attach libraries like jQuery with an on ready handler, so it can execute after the DOM loads.

## Suppose there is an HTML UL list of menu items, how do you make it display them horizontally?
- I would give the UL list of menu items "ul {display: inline;}"

## What is a CSS selector?
- A CSS selector is how you actually select the content you want to style.

## What is the significance of the $ operator in jQuery? Please name three different uses for it.
- It is the jQuery way to select/find HTML elements. You can use this syntax to find elements by ID or Class. You can also use this syntax to pass it a function to run when the document is ready. It's similar to "body.onload()". You're also able to pass it a string of HTML to turn this into a DOM element.

## What is a CSS selector?
- A CSS selector is how you actually select the content you want to style.

## What is the difference between a CSS class and an ID? What are some practical uses for each?
- Classes are not unique. ID's are supposed to be unique. Classes are denoted by a ".", while ID's are denoted by "#".
- ID's are used when wanting to apply unique stylings
- A class is utilized when you want to apply the same stylings to a family of elements

## What text color will the following list element have? HTML: <li class="product_feature" id="product_feature_1"> Heated Leather Seats </li> and CSS: ul li { color: red; } #product_feature_1 { color: black; } .product_feature { color: blue; } body #product_feature_1 { color: yellow; } #product_feature_1.product_feature { color: purple; }
- purple



## Please provide examples of when inlined, internal and external stylesheet linking is beneficial in an HTML document.
- Inline CSS can be useful for testing and quickly experimenting. It's also useful for smaller websites. It has the added benefit of lower HTTP requests.
- With internal CSS, styles don't need to be applied to every single element.
- The advantages of external stylesheet is faster load time and reduced file-size.

## What does DOM stand for? Why is it useful to know about it when writing jQuery JavaScript code? Please provide an example.
- Document Object Model. It's used whenever you interact with elements of a web page.
- Browsers build an internal representation of the page with the "body" element at the top of the hierarchy and has child nodes below it. The DOM is the model underneath that gives developers access to the API that allows us to manipulate and navigate the Document.



## Please explain when you would augment an application with a framework such as Angular.js, Ember.js, Batman.js, or Knockout.js. What are the use cases and problems they help with? Please provide a practical example of a web application that benefits from one of the frameworks mentioned.
- You would use a frontend framework in order to give developers easier to remember, and more intuitive API.
- Frontend frameworks are usually opinionated, and through their opinionated methodology, usually incorporate some sort of cohesive structure to your frontend code.
- I know many Rails developers feel more comfortable with Ember, because the two frameworks have many similarities. For example Rails models and Ember models are very similar. The ember-cli is similar to the CLI provided by Rails. Debugging in Ember is similar to debugging in Rails.
- Ember also helps with avoiding hard page reloads. Ember keeps a long-running state.
## What are some of the new elements that HTML 5 adds? What are their benefits?
- Semantic HTML was introduced. Div tags themselves are meaningless. Newer HTML5 tags such as the article tag, or the figure tag give semantic meaning to HTML. This helps improve readability and better communicates to other developers the goal a particular part of HTML is trying to accomplish. It enhances the intention of code. Moreover, it helps make tags more brief, and simpler.


## Agile has been used to mean a lot of things. What do you think Agile truly means?
- In my mind, I believe agile emphasizes iterating quickly, being flexible enough to change directions relatively quickly, and emphasizing only shipping necessary features rather than planning meticulously upfront for features that your users aren't going to use.

## What is the difference between traditional project management (sometimes associated with the Waterfall process) and Agile iterative development? Could you define what Scrum calls a Sprint and XP calls an Iteration?
- Waterfall emphasizes meticulous longterm planning into the future. The planning period for a waterfall process is very long, and many times comes from the top of the organization. To contrast, agile iterative development takes into account that focuses on Many times sprints are two weeks long. This is where engineers focus on implementing a part of a feature.

## Any experience with Agile estimation or planning poker? If so, please explain.
- Yes, I have pointed stories during IPM. The more points a story has, the more complicated and longer said story will take. The less points a story is, the simpler and shorter amount of time it will take. Some teams break down larger pointed stories into smaller stories.
## Please define "Team Velocity" and how it is calculated.

- Team Velocity is the rate at which a team ships code. Velocity is calculated based on the number of points completed each week, divided by the number of developers a team has.

## Could you talk a little bit about the XP idea of Collective Ownership?
- I am not familiar with the XP idea of Collective Ownership.

## Do you have any experience with pair-programming? If so, could you list all the way it helps a team produce higher quality code faster?
- Yes, I have experience pair-programming. Pairing allows two brains to work on the same problem, allowing faster breakthroughs when developing. This also allows developers to debug more quickly. Moreover, with pair programming, information silos are avoided because developers are periodically on-boarding other developers about the code they have written. Lastly, I believe pair programming helps developers stay more focused.

## Please define Test Driven Development and explain why it is sometimes called Test Driven Design.
- TDD is a methodology when you write tests before you write your actual code. This is so to never ship untested code. According to some developers, if your code is untested, it may as well be as good as broken. Under TDD, you follow the Red-Green-Refactor method. First, you write your tests. Run the test suite, and watch your code fail. Make your tests pass. Then refactor.

## Are you familiar with XP's term "Spike"? What is it and why is it needed?
- I am not familiar with XP's term 'spike'.

## What does YAGNI stand for and why is it important in Agile software development?
- YAGNI stands for "you aren't going to need it". It's a phrase that basically rejects the idea of Waterfall planning. It's the idea that a feature you planned for in a waterfall planning process, it turns out to be unnecessary or unpopular after more user research. It's an acronym thats a proponent of the agile, iterative approach that only plans for what is most necessary.

## Could you explain the difference between unit tests and integration tests? What are some ways of writing each type in a Rails application?

- An example of a unit test would be like an RSpec test that tests a model. An integration test would be like a Selenium/Capybara test, that possibly opens up the browser and clicks through a page of the app and inputs mock data. Unit tests test a small building-block of code, usually a "behind-the-scenes" part of the code. Integration tests test many moving parts, and make sure they cohesively work together.

## Please define "Refactoring", explain benefits, and talk about when it is possible and when it is too risky or not possible.

- Refactoring means to dry up messy, repeatable code. Hopefully, when a developer refactors, the code becomes clearer to others and re-usable in other parts of the codebase. It may be too risky to refactor code if DRYing code up too much then becomes hard to understand for others. Developers must find a balance between DRY code and readability.

## Agile is often confused with "zero documentation". What is your understanding about the matter?
- Sometimes, agile teams move too quickly and change directions very quickly. To some developers, it may not be worth it to write down documentation for other developers about a certain part of the codebase, if that part of the codebase may be completely re-written or deleted based on the future direction of the team.

## Agile is often confused with "no design up front". What is your understanding about the matter?
- "No design up front" is a misunderstanding of agile. It's the idea that up-front design work is bad, and that instead you should change your design one test-case at a time.

## While writing automated tests, when do you need to use Mock objects? When do you need to use Factories? What are the trade-offs?
- Factories are good when you're dealing with the thing you're actually testing. Mocks are for when you need to interact with an API, but that thing itself has been tested elsewhere. Factories are more tied to ActiveRecord models, or in other words, a thing that can be persisted to your database. They let you use the entire interface directly, whereas mocks are way more limited - you have to specify everything explicitly yourself. But, using mocks doesn't slow down your test as much as having many factories may.
- Also, unless you have a verified double as your mock, there's no guarantee that your mock is keeping up with changes in your codebase. So if you use unverified mocks, your tests start drifting.

## What are the benefits of having daily scrums/stand-up-meetings ? How long should they be?

The benefits of having daily scrum is that you're aware of what the rest of your team is working on. It lis a forum for people checking-in with one another.

I believe stand-up should be less than 10 minutes long. It's purpose is to let people quickly check in about their progress, alert the team what they're working on currently, and to see if anyone is stuck or needs help.
