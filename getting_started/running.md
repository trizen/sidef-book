## Running Sidef without installation

It is possible to run Sidef without having to install it. If you're using a Unix-like OS, all you need to do is to execute the following commands:

```console
$ wget 'https://github.com/trizen/sidef/archive/master.zip' -O 'master.zip'
$ unzip 'master.zip'
$ cd 'sidef-master/bin/'
$ perl sidef -v
```

Those commands will download and unpack the latest version of Sidef and will execute the `bin/sidef` script which will print the current version of the language.

To execute a Sidef script, run:
```console
$ ./sidef ../scripts/sierpinski_carpet.sf
```

You can, also, add the following alias to your `~/.bashrc`:

```bash
alias sidef="/path/to/bin/sidef"
```