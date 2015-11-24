# Compilation

A Sidef script can be compiled to a stand-alone Perl program using the `-c` command-line option:


```shell
$ sidef -o out.pl -c script.sf
```

The above command will compile the file `script.sf` into the Perl script `out.pl`, which is a fully portable, stand-alone Perl program.
