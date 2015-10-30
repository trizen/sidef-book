# Dumping the AST

The `-d` and `-D` command-line options can load or dump the abstract syntax tree (AST) of a given Sidef program.

Example:

```shell
$ sidef -o AST.pl -D script.sf      # will dump the AST of script.sf
```

The above command parses the `script.sf` file, then it dumps the AST into the `AST.pl` file, which can be examined, changed and/or re-loaded with the `-d` command at a later time:

```shell
$ sidef -d AST.pl                  # will load and execute the AST file
```

This feature is used mainly in debugging purposes and it requires the [Data::Dump](https://metacpan.org/pod/Data::Dump) Perl module.
