# Precompilation

Sidef supports precompilation by saving each compiled code inside a database, which is updated automatically and sanitized periodically.

This method reduces significantly the boot-time of Sidef programs, and it works as following:

* it checks the database with the MD5 of the code
* if the MD5 exists inside the database, it returns the executable code

otherwise:

* parses the code and generates the executable code
* stores the executable code inside the database with the MD5 of the code

Next time when the same code is executed, Sidef will simply retrieve the executable code from the database, without generating it again:

```console
$ sidef -s script.sf             # may load slow the first time
$ sidef -s script.sf             # will load much faster the second time
```

When a given code is not executed again in the next two or three days, it will be removed automatically from the database. The code which is used frequently, will not be removed.
