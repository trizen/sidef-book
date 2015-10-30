# Compilation

Sidef script can be compiled into stand-alone Perl programs by using the `-c` command-line option:


```shell
$ sidef -o out.pl -c script.sf
```

The above command will compile the Sidef file `script.sf` into the Perl script `out.pl`, which is a fully portable, stand-alone Perl program, which will work everywhere where Perl works.
