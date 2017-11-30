# Creating the first Sidef script

A Sidef script can be written in any text editor and, by convention, it has the **`.sf`** extension.

The content of a simple _Hello World_ program looks like this:

```ruby
#!/usr/bin/sidef

say "Hello, 世界";
```

If we save the content in a new file called **`hello.sf`**, we can execute the code by running:

```console
$ sidef hello.sf
```
