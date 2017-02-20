# Compilation

A Sidef script can be compiled to a stand-alone Perl program using the `-c` command-line option:


```shell
$ sidef -o out.pl -c script.sf
```

The above command will compile the file `script.sf` into the Perl script `out.pl`, which will include the entire implementation code of Sidef.

Currently, Sidef code that contains `eval()` cannot be compiled correctly to Perl, as it requires some parse-time information for run-time evaluation, which is lost in the compilation process.
