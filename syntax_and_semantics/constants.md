# Constants

Sidef implements three kinds of constants: `const`, `define` and `enum`.

## const

The common way of declaring constants in Sidef, is by using the `const` keyword:

```ruby
const pi = 3.14
say pi                 # prints: 3.14
#pi = 3                # compile-time error: can't modify non-lvalue constant
```

This kind of constants are created dynamically at run-time, but cannot be changed during the execution of the program.

When declared inside a class or a function, the constant is created and initialized dynamically, as illustrated in the following example:

```ruby
func f(a) {
    const x = a          # created dynamically at each function call
    return (x + 2)
}

say f(40)       #=> 42
say f(50)       #=> 52
```

## define

This keyword will define a compile-time evaluated constant and will point directly to the object at which it evaluated to.

```ruby
define PHI =   (1.25.sqrt + 0.5)
define IHP = (-(1.25.sqrt - 0.5))

say (PHI**7 - IHP**7 / PHI-IHP)
```

This type of constants are the most efficient ones.

## enum

The `enum` keyword will automatically declare and assign a list of constants with ascending numeric values (starting from 0):

```ruby
enum |Black, White|
say Black             # prints: 0
say White             # prints: 1
```

Alternatively, we have the possibility for specifying an initial value, which will get incremented after each declaration, by calling the method `.inc()`.

```ruby
enum |α="a", β|
say α             # prints: 'a'
say β             # prints: 'b'
```
