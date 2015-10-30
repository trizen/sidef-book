# Compilation

Sidef script can be compiled into stand-alone Perl programs by using the `-c` command-line option:


```shell
$ sidef -o out.pl -c script.sf
```

The above command will compile the Sidef `script.sf` into `out.pl` Perl script, which will run everywhere where Perl runs, without requiring any additional library.
