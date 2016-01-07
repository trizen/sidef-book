# Dumping the AST

The `-D` command-line option dumps the abstract syntax tree (AST) of a given Sidef program.

Example:

```shell
$ sidef -D script.sf      # will dump the AST of script.sf
```

This feature is used mainly in debugging the parser and it requires the [Data::Dump](https://metacpan.org/pod/Data::Dump) Perl module.
