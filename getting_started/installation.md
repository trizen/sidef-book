# Installation

Sidef can be installed automatically from the [CPAN](https://metacpan.org/pod/distribution/Sidef/lib/Sidef.pod), by invoking the following command:

```console
$ cpan Sidef
```

If the testing takes a long time, add the `-T` flag to build and install Sidef without testing:

```console
$ cpan -T Sidef
```

When the `cpan` command is not available, try:

```console
$ perl -MCPAN -e "CPAN::Shell->install(q{Sidef})"
```

**IMPORTANT**: Sidef needs the [GMP](https://gmplib.org/), [MPFR](http://www.mpfr.org/) and [MPC](http://www.multiprecision.org/) C libraries.

## Installing from git source

To install Sidef manually, download the [latest version](https://github.com/trizen/sidef/archive/master.zip), unzip it and follow the installation steps:

```console
$ perl Build.PL
# ./Build installdeps
# ./Build install
```

When [Module::Build](https://metacpan.org/pod/Module::Build) is not installed, try:

```console
$ perl Makefile.PL
$ make test
# make install
```

## Android installation

It's also possible to install Sidef on Android, by installing [Termux](https://f-droid.org/en/packages/com.termux/) and executing the following commands:

```console
$ pkg install perl make clang libgmp libmpfr libmpc
$ cpan -T Sidef
```

If the installation succeeded, the `sidef` command should be available:

```console
$ sidef -h
```
