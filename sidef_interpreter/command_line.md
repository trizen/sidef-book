# Command-line options

The Sidef interpreter has the following command-line options:

```text
usage: sidef [switches] [--] [programfile] [arguments]

  -A int        set the numeric accuracy to a certain number of digits
  -c            compile the code as a stand-alone Perl program
  -C            check syntax only
  -D            dump the syntax tree of a program
  -d file       load a dumped syntax tree
  -E program    one line of program
  -H            interactive help
  -i            interactive mode
  -k            keep track of potential unsafe parser interpretations
  -M mode       set the rounding mode of floating-point numbers
                valid modes: [even], odd, +inf, -inf, zero, trunc, common
  -n type       try to use a specific backend for Math::BigInt
                valid types: GMP, Pari, FastCalc
  -o file       file where to dump the output
  -O level      perform code optimizations before execution
                valid levels: [0], 1, 2
  -P int        set the precision of floating-point numbers
  -r            parse and deparse a Sidef program
  -R lang       parse and deparse a Sidef program into a given language
                valid values: sidef, perl
  -s int        the number of spaces used in code indentation
  -t            treat all command-line arguments as scripts
  -v            print version number and exit
  -w            enable warnings with stack backtrace
  -W            make warnings fatal (with stack backtrace)
```

which we'll examine in the following pages.
