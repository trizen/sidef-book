# Installation

Sidef can be installed automatically from [CPAN](https://metacpan.org/pod/distribution/Sidef/lib/Sidef.pod), invoking the following command:

```console
$ cpan Sidef
```

To install Sidef manually, download the [latest version](https://github.com/trizen/sidef/archive/master.zip), unzip it and follow the installation steps:

```console
$ perl Build.PL
$ ./Build test
$ sudo ./Build install --install_path script=/usr/bin
```

For packaging Sidef, run:

```console
$ perl Build.PL --destdir "/my/package/path" --installdirs vendor
$ ./Build test
$ ./Build install --install_path script=/usr/bin
```

If the installation succeeded, you should be able to run the `sidef` command:

```console
$ sidef -h
```
