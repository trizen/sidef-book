# Variables

Variables are commonly declared using the `var` keyword:

```ruby
var num = 42
var str = "42"
var bool = true
```

## Lexical variables

These kinds of variables are lexical, but statically block scoped. This is the usual way of declaring variables in Sidef.

```ruby
var x = 42    # sets the lexical x to 42
say x         # prints the lexical value of x
```

## Static variables

This kind of variables are static, block-scoped and initialized only once.

```ruby
static x = 42   # sets the static x to 42
say x           # prints the static value of x
```

## Global variables

Global variables are declared at the top-level of the current namespace. They can be accessed from everywhere, anytime. However, try to avoid using them, unless you really don't have any better alternative.

```ruby
global x = 42     # sets global x to 42
say x             # prints the global value of x
```

## Local variables

Local variables (also known as "dynamically scoped variables") can be used to localize array/hash lvalues or global variables to a limited scope.

```ruby
global x = 42    # sets the global x to 42
do {
   local x = 100     # localizes x inside this block to 100
   say x             # prints the local value of x
}
say x            # prints the global value of x (42)
```

A slightly more advanced example, illustrating the localization of an hash lvalue, would be:

```ruby
func foo(h) {
    say h{:key}
}

var h = Hash(key => "a")

foo(h)                        # prints "a"
do {
    local h{:key} = "b"       # local change only
    foo(h)                    # prints: "b"
}
foo(h)                        # prints: "a"
```

## Variable scoping

All variables (including functions and classes) are block scoped in the following way:

```ruby
var x = 'o'

do {
    say x              # o
    var x = 'm'
    say x              # m
    do {
        say x          # m
        var x = 'b'
        say x          # b
    }
    say x              # m
}

say x                  # o
```

Declaring multiple variables at once is also possible:

```ruby
var (x, y, z) = (3.14, false, "foo")
```

We can, also, declare variables with some default values:

```ruby
var (x, y=755, z=777) = (666, 655)

say x        # prints: 666
say y        # prints: 655
say z        # prints: 777
```

## Slurpy variables

Slurpy (or greedy) variables are a special type of variables which can be initialized with a list of values, creating automatically a container to hold the data.

```ruby
var *arr = (1,2,3)    # creates an Array
say arr               # prints: [1,2,3]

var :hash = (a => 1, b => 2)   # creates an Hash
say hash                       # prints: Hash(a=>1, b=>2)
```

## Working with variables

Any method applied to a variable is applied on the object at which the variable is pointing at:

```ruby
var x = 'sidef'
say x.uc        # prints: `SIDEF`
say x           # prints: `sidef`
```

Special `!` at the end of a method changes the variable in-place (almost like in Ruby):

```ruby
var x = 'sidef'
x.uc!            # notice the `!`
say x            # prints: `SIDEF`
```

Appending the = sign at the end of arithmetic operators, the variable will be changed in place:

```ruby
var x = 5
x += 10            # adds 10 to "x"
say x              # prints: 15
```

## Special variables

Currently, there are only four real predefined variables:

* `ARGV`: Special `Array` that contains the program's command-line arguments, that were not given to Sidef.
* `ENV` : Writable `Hash` copy of environment variables and their values when the program was started.
* `ARGF`: Special `FileHandle` object used to read lines from argument-files or from `STDIN` when no argument has been specified.
* `DATA`: Special `FileHandle` object that points to the data stored after the `__END__` or `__DATA__` tokens.

```ruby
ARGV.each { |arg|
  say arg
}

say ENV{:HOME}  # get an environment variable

ARGF.lines { |line|
  say line
}

say DATA        # prints: "hello\nworld"

__DATA__
hello
world
```

## Topic variable

The special topic variable (`_`) is declared at compile-time in each block-object in the program. You may not see its real name very often, because it has been overtaken by the elegant prefix dot (.) operator:

```ruby
[25,36,49].map {.sqrt} \
          .each{.log.say}
```

...where `.sqrt` really means `_.sqrt`, and `.log.say` means `_.log.say`.
