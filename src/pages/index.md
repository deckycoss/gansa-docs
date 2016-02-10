__block__: content
title: Gansa
sections: Downloads
          License

Gansa
=====

Gansa is a simple tool and Python library for creating static websites.

Features:

* Generate pure HTML from Markdown syntax
* Design page layouts using Jinja2 or Jade templates
* Support for a variety of database engines

Downloads
---------

[Gansa source code](https://github.com/deckycoss/gansa)

[Documentation source code](https://github.com/deckycoss/gansa-docs) (a good example Gansa project!)

License
-------

Gansa is copyright 2016 Decky Coss.

Gansa is licensed under the terms of the [GNU General Public License](http://www.gnu.org/licenses/gpl-3.0.en.html).

### How to license a Gansa project ###

A project created using Gansa only needs to be licensed under the GPL where it contains source code that falls under the GPL's definition of a "covered work"—that is, "either the unmodified Program or a work based on the Program". (In this case, "the Program" refers to Gansa.)

For example, imagine that a project contains some CSS and JavaScript asset files, as well as two Python modules, "callbacks.py" and "models.py". Both modules are required in order to compile the project, but only callbacks.py interfaces with the Gansa API directly. callbacks.py would need to be licensed under the GPL, whereas models.py would need to be licensed under the GPL or a GPL-compatible license. The asset files would not need to be licensed under any GPL-compatible license, because it is possible to compile the project without them.