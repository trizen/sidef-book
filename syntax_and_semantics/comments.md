# Comments

### Single-line comments

The sharp (`#`) character sequence marks the following text as a single-line comment. Single-line comments end at the end-of-line.

```ruby
#
## The hello-world program...
#
say "Hello, world!";         # with single-line comments.
```

### Multiple-line comments

Comments can span multiple lines by using the multiple-line comment style. Such comments start with `/*` and end with `*/`. The text between those multi-line comment markers is the comment.
```C
/*
   This is another style of a comment.
   It allows multiple lines.
*/
```

### Embedded comments

This kind of comments are a little bit weird at the first glance, but they are useful sometimes.

```perl6
var speed = (distance #`(in meters) / time #`(in seconds));
```

is equivalent with:

```ruby
var speed = (distance / time);
```

A common use of embedded comments is to specify a shell evaluation code to execute the actual Sidef script when it's executed by a shell program. However, the eval statement is completely ignored by Sidef since the block in which it is defined, it's never executed.

```perl6
#`(if running under some shell) {
    eval 'exec /usr/bin/sidef $0 ${1+"$@"}'
}
```
