title: Command-line reference
block: __content__
sections: build
          init

Command-line reference
======================

The gansa command-line program is intended to be run with a command. If a command is not specified, a help message will be displayed.

The following commands are recognized:

* [build](#build)
* [init](#init)

build
-----

This command is used to render a Gansa site.

Usage: `gansa build [-h] [-o OUT] [-v]`

Options:

* **-h**, **--help**: display a help message for this command.
* **-o OUT**, **--out OUT**: the name of the output directory.
* **-v**, **--verbose**: display verbose error messages.

init
----

This command is used to initialize the environment of a Gansa site.

Usage: `gansa init [-h] [-v]`

Options:

* **-h**, **--help**: display a help message for this command.
* **-v**, **--verbose**: display verbose error messages.