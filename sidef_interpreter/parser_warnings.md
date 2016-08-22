# Parser warnings

Sidef provides the `-k` option which will keep track of all the possible unsafe parser interpretations.

For example, if we declare the following function, but we misspell its name when we call it, Sidef will interpret it as a method call, which is probably not what we want:

```ruby
func foo(n) { say n }
fo(42)                   # will get interpreted as `42.fo`
```

When the command-line option `-k` is specified, the following warning is produced:

```
[INFO] `fo` is parsed as a prefix method-call at script.sf line 2
```

One simple way to catch this kind of errors at parse-time, it to always call functions with the explicit `.call` method:

```ruby
func foo(n) { say n }
fo.call(42)
```

The above code will fail to compile, producing the following error message:

```
File : test.sf
Line : 2
Error: variable <fo> is not declared in the current scope

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
fo.call(42)
^
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
[?] Did you mean: foo
```
