# Precompilation

Sidef v2.25 introduced support for precompilation, by saving each compiled code inside a special database, which is updated automatically and sanitized periodically.


This method reduces significantly the boot-time of Sidef programs, and it works as follows:

    * checks the database with the MD5 of the code
    * if the MD5 exists inside the database, it returns the executable code


otherwise:

    * parses the code and generates the executable code
    * stores the executable code inside the database and returns it


Next time when the same code is executed, Sidef will simply retrieve the executable code from the database, without parsing or generating any new executable code.

```console
$ sidef -s script.sf             # it may load slow the first time
$ sidef -s script.sf             # it will run instantaneously the second time
```

When a given code is not executed again in the next two or three days, it will be removed automatically from the database. The code which is used frequently, will not be removed.
