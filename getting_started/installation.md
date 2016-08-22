# Installation

Sidef can be installed automatically from [CPAN](https://metacpan.org/pod/distribution/Sidef/lib/Sidef.pod), invoking the following command:

```console
$ cpan Sidef
```

To install Sidef manually, download the [latest version](https://github.com/trizen/sidef/archive/master.zip), unzip it and follow the installation steps:

```console
$ perl Build.PL
$ ./Build installdeps
$ ./Build test
$ ./Build install
```

If [Module::Build](https://metacpan.org/pod/Module::Build) is not installed, then use:

```console
$ perl Makefile.PL
$ make test
$ make install
```

If the installation succeeded, you should be able to run the `sidef` command:

```console
$ sidef -h
```
