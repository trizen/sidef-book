# Optimization

The `-O level` command-line option controls the level of optimization before the execution begins.


Currently, there are three level of optimization available:

* 0 - Does nothing. (default)
* 1 - Does constant folding on the AST. (recommended)
* 2 - Does constant folding, after which it deparses the AST into Sidef code, parses the code again and does constant folding on the new AST.


In the end, the code is translated into Perl and is ready to be executed. In the translation process, however, more non-optional optimizations are done, such as loop-optimizations, scope-optimizations, etc...
