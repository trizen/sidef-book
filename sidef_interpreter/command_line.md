# Command-line options

The Sidef interpreter has the following command-line options:

```text
Usage: sidef [switches] [--] [programfile] [arguments]

  -c            compile the code as a stand-alone Perl program
  -C            check syntax only
  -D            dump the syntax tree of a program
  -E program    one line of program
  -H            interactive help
  -i            interactive mode
  -k            keep track of potential unsafe parser interpretations
  -M mode       set the rounding mode of floating-point numbers
                valid modes: [near], zero, inf, +inf, -inf
  -o file       file where to dump the output
  -O level      perform code optimizations before execution
                valid levels: [0], 1, 2
  -P int        set the precision of floating-point numbers (default: 32)
  -r            parse and deparse a Sidef program
  -R lang       parse and deparse a Sidef program into a given language
                valid values: sidef, perl
  -s int        the number of spaces used in code indentation
  -t            treat all command-line arguments as scripts
  -v            print version number and exit
  -w            enable warnings with stack backtrace
  -W            make warnings fatal (with stack backtrace)
```

...which we'll examine in more detail in the following pages.
