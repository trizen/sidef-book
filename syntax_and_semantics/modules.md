# Modules

A module is a static containing namespace for declarations.

```ruby
module AModule {

  func a () {
    say "AModule::a"
  }

  const g = "any variable"

  class R {
    method r { say "AModule::R.r" }
  }
}
```

Modules cannot be instantiated as objects, cannot be modified, and cannot be directly referred to by their name (like `AModule`) without a member name (like `AModule::a`). Therefore, they are for containing related code that doesn't need to be instantiated like a class.