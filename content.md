# Ruby Basics

Let us begin with a quick introduction in Ruby.

## Goal

In this lesson, you'll write your very first Ruby program, learn how Ruby "thinks" about code, and understand the building blocks you'll use in every project. We want to get you as quickly as possible to the point where you can write useful programs, and to do that we have to concentrate on the basics.

## 1. Printing to the Console

The only way to learn a new programming language is by writing programs in it. The first program to write is the same for all languages:

Print the words: "hello, world"

[source](https://archive.org/details/c-programming-language-2nd-edition/page/9/mode/1up)

In Ruby, printing output to the console is achieved using several built-in methods: `puts`, `print`, `p`, and `pp`.

```ruby
pp("hello, world")
```
{: .repl }

<aside class="tip">
  Try using the other print methods (<code>puts</code>, <code>print</code>, and <code>p</code>). Do you notice a difference in the output?
</aside>

## 2. Understanding the Syntax

<!-- TODO: add diagram breaking this down -->

Let's break down what's happening when we run `pp("hello, world")`:

- `pp` is a *method* (a "message" you send to an object).
- `self` is the *receiver* of the `pp` message. (You could even write it as `self.pp("hello, world")`)
- `"hello, world"` is a string, your method's argument.

<!-- 

https://stackoverflow.com/questions/45474802/could-you-explain-sender-and-receiver-in-oop-and-give-examples

https://stackoverflow.com/questions/15592268/how-to-understand-sender-and-receiver-in-ruby

arguments, parameters, method (message), receiver 

For example, in a call like self.pp("hello, world"), the object self is the receiver of the pp message with "hello, world" being the argument.

-->

### When `self` is Implied

In Ruby, when you call a method at the top level (like `pp("hello, world")`), Ruby quietly assumes you mean `self.pp("hello, world")`

You don't see the `self.` part because Ruby adds it for you. This is called an *implicit receiver*, the "thing" that's running your code (the `main` object) is understood without you having to type it.

You'll learn more about `self` later, but for now just know:

- If you don't write a receiver, Ruby uses `self` automatically.
- Inside the top level of your program, `self` is the `main` object.

<aside class="tip">
  Later, when you're inside your own classes, <code>self</code> will mean "this particular object," and Ruby will still fill it in automatically when you don't write it.
</aside>

### Parentheses: Optional but Helpful

In Ruby, parentheses can often be omitted when calling methods. For example:

`pp "hello"` is the same as `pp("hello")`

*Without* parentheses the code reads as a more natural and "sentence-like" style. *With* parentheses is a more standard approach across different programming languages.

<!-- TODO: show, don't tell -->
<aside class="warning">
  <strong>Warning:</strong> Omitting parentheses can sometimes confuse Ruby about which arguments belong to which method. Parenthese are preferred when passing multiple arguments or to make order of operations clear.
</aside>

### Casing Rules in Ruby

Ruby cares about letter case.

```
method_names → lowercase with underscores "snake_case"
variable_names → lowercase with underscores "snake_case"
ClassNames → CapitalizedCamelCase 
CONSTANTS → ALL_CAPS
```

Try to be consistent with casing in your code and filenames.

<!-- NOTE: parentheses optional in ruby -->

## 3. Everything is an Object

In Ruby, *everything is an object*.

Think of an object like a thing in the real world: a phone, a cat, or a sandwich.

Each object:

- Has attributes associated with it (a phone has a color, a cat has a name)
- Can do actions (a phone can ring, a cat can meow)

In Ruby, things like numbers, words, and even pieces of code are all objects with their own actions (called methods) and properties.

For example:

```ruby
"hello".upcase
```
{: .repl }

In this example:

`"hello"` is an object (a string)
`.upcase` is a method (an action the object can perform)

Resulting in `"HELLO"`

Even numbers are objects:

```ruby
5.next  # tells the number 5 to give you the next number
```
{: .repl }

### The "Main Object" and `self`

When you start a Ruby program, Ruby is already inside an object behind the scenes, we call it the main object.

Right now, the program is being run "from inside" that main object. Ruby uses the special word `self` to refer to the object you're currently inside.

For example:

```ruby
pp self
```
{: .repl }

This will show you the `main` object Ruby is starting in. You don't have to fully understand `self` yet, just know it's Ruby's way of saying "me, the thing currently running this code." Later, when you create your own objects, <code>self</code> will point to those objects instead of the main object.

## 4. Variables

Remember Algebra? `100 = x + 50, Find x` Ruby has variables too. We can store any data type in a variable. Let's update our hello world program to use a variable.

```ruby
greeting = "hello, world"
pp(greeting)
```
{: .repl }

Instead of retyping the string, you store it in the `greeting` variable and print it whenever you like.

<aside class="tip">
  We can be more descriptive in naming variables than just x, y, z, etc. One of the hardest things about programming is naming things well. I encourage you to be verbose and descriptive when naming things. This will make it easier to understand.
</aside>

## 5. Error Messages

Let's try to break things. Run this repl calling the `kaboom!` method.

```ruby
kaboom!
```
{: .repl }

Looks like we've triggered our first *error message*, `-e:1:in '<main>': undefined local variable or method 'kaboom!' for main (NameError)`. Let's break it down step-by-step:

1. `-e:1`: Ruby is telling you the location of the problem. `-e` means this code was run directly from the command line (or a quick REPL test) `:1` means the problem is on line 1.
2. `in '<main>'`: This means the error happened in the "main" part of your program, the top level before you're inside any class or method.
3. `undefined local variable or method 'kaboom'`: Ruby looked for something called `kaboom` and couldn't find it as either a local variable (like my_name) or a method (like puts)
4. `for main`: Ruby was trying to run this code as part of the main object, the default object Ruby starts in.
5. `(NameError)`: This is the type of error: a `NameError` means Ruby doesn't recognize the name you gave it.

Error messages are your friend. Please read the error message! Seriously, **read the error message**. They will often provide context clues like line numbers and even suggest changes to make it work.

<!-- TODO: add screenshot/video showing shortcut to click to the location in your code -->

## 6. Code Comments

Comments are ignored by Ruby but are essential for explaining your code.

```ruby
# NOTE: This prints a friendly message
pp "hello, world"
```
{: .repl }

I encourage you to use comments to document your code and provide context.

<aside class="tip">
  On many editors (including VSCode), <pre>⌘ + /</pre> toggles comments.
</aside>

## 7. Data Types

<!-- String, Integer, Numeric, Array, Hash -->
Ruby's common data types include:

```ruby
"text"     # String
42         # Integer
3.14       # Float
[1, 2, 3]  # Array
{a: 1}     # Hash
```
{: .repl }

You'll use these to store and manipulate different kinds of information. We'll cover these in more detail in future lessons.

## 8. How to run Ruby

There are two main ways to run Ruby code:

<!-- TODO: video example -->
### Run a Ruby File

Save your code in a file and run `ruby my_file.rb`.

<!-- TODO: video example -->
### Interactive Ruby

Open an interactive Ruby console by running the terminal command `irb`. IRB is great for quick experiments.

## 9. Reading Documentation

Ruby's official documentation is a treasure trove of information. I encourage you to bookmark these links.

- [Ruby Docs](https://docs.ruby-lang.org/)
- [Ruby.org Guides](https://www.ruby-lang.org/en/documentation/)

## Practice Challenge

Change your greeting so it includes your name, like: `"hello, Ian!"`. Then, try printing it with both `puts` and `pp`.

## Wrap-Up

- You learned to print text, store it in variables, and identify Ruby's basic data types.
- Next, you'll explore the basic data types and control flow to make programs interactive.
- Bookmark the Ruby docs. you'll visit them often.

## Quiz

- What does `pp` do in Ruby? <a href="https://docs.ruby-lang.org/en/master/PP.html">Ruby Docs: class PP</a>
- It pauses the program.
  - Not correct. `pp` prints data in a human-readable format.
- It prints output in a more readable way.
  - Correct! `pp` pretty-prints objects.
- It permanently stores variables.
  - Not correct. `pp` has nothing to do with saving data.
{: .choose_best #ruby_pp title="Understanding pp" answer="2"}

## References

- [Official Ruby Programming Language website](https://www.ruby-lang.org/en/documentation/)
- [Ruby Programming Language Documentation](https://docs.ruby-lang.org/)
