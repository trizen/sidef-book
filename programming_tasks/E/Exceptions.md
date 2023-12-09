[1]: https://rosettacode.org/wiki/Exceptions

# [Exceptions][1]

An exception is thrown by the `die` keyword, which, if not caught, it terminates the program with an appropriate exit code.

```ruby
try  {
    die "I'm dead!"        # throws an exception
}
catch { |msg|
    say "msg: #{msg}"      # msg: I'm dead! at test.sf line 2.
}

say "I'm alive..."
die "Now I'm dead!"        # this line terminates the program
say "Or am I?"             # Yes, you are!
```

#### Output:
```
msg: I'm dead! at test.sf line 2.
I'm alive...
Now I'm dead! at test.sf line 9.
```
