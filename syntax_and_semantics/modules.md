# Modules

In Sidef, a module is the declaration of a new namespace:

```ruby
module Fibonacci {
    func nth(n) {
        n > 1 ? nth(n-2)+nth(n-1) : n
    }
}

say Fibonacci::nth(12)    # prints: 144
```

The default namespace name is `main`. Variables from other namespaces can be used inside a module by either importing them, or by specifying their full name which includes the namespace:

```ruby
var foo = 42

module Bar {
    var baz = 99
    say main::foo   #=> 42
}

say Bar::baz        #=> 99
```

Importing an identifier in the current namespace, can be done using the syntax `import namespace::identifier_name`:

```ruby
var foo = 42

module Bar {
    import main::foo
    var baz = 2*foo
}

import Bar::baz
say baz             #=> 84
```

Modules cannot be instantiated as objects, cannot be modified, and cannot be directly referred to by their name (like `ModuleName`) without a member name (like `ModuleName::var_name`). Therefore, they are for containing related code that doesn't need to be instantiated like a class.
