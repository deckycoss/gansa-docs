title: Callbacks
__block__: content
sections: Context processors
          Postrender functions

Callbacks
=========

Gansa's functionality can be extended through **callbacks**. A callback is a function written by the user that is automatically called at a pre-determined time. Gansa callbacks are written in Python.

There are two types of callbacks that may be used in a Gansa site: context processors and postrender functions.

Context processors
------------------

Each terminal view object can have a callback function that will be run just before the view is rendered. This function is known as a **context processor**. A context processor's primary intended purpose is to modify the view's context table in ways that a static YAML file cannot, but it may have many other uses.

The context processor function must accept the following parameters, in this order (parameter names are omitted as they do not matter):

* (dictionary): the context table for the view.
* (dictionary): a representation of the view object. Includes all of the properties listed in the [view object specification](views.html#specification), plus a property called **full_route**, which represent's the view's full route.
* ([Site](api.html#site)): the Site object for this Gansa site.

The function must either return *None*, or a dictionary representing the new context table that will be used by the view.

All views can specify a context processor, either explicitly or through inheritance, but context processors will only run on terminal views.

### An example ###

Let's revisit our ["Hello world" example](basics.html#hello-world):

**pages/index.md**

    title: My Page
    __block__: main

    Hello world!

This time, we're going to modify the template so that it displays the date on which the site was last rendered:

**templates/base.html**

    <html>
    <head>
        <title>{{title}}</title>
    </head>
    <body>
        {% block main %}{% endblock %}

        <p>Site last updated on {{ date_updated.strftime("%B %d, %Y").replace(" 0", " ") }}</p>
    </body>
    </html>

We will generate the "date_updated" context variable from our context processor in "callbacks.py":

**views.yaml**

    - route: index.html
      template: base.html
      context_processor: callbacks:index

**callbacks.py**

    import datetime

    def index(context, view, site):

        copy = dict(context)
        copy["date_updated"] = datetime.datetime.now()

        return copy

The result should look something like [this](files/hello_with_date.html).

Postrender functions
--------------------

A Gansa site can specify a callback function that will be run every time the site is successfully rendered. This function is known as a **postrender function**.

Some examples of uses for postrender functions include updating the project database, triggering a deploy script, and post-processing the generated HTML output.

The postrender function must accept the following parameters, in this order (parameter names are omitted as they do not matter):

* ([Site](api.html#site)): the Site object for this Gansa site.
* (dictionary): the table of arguments that were originally used to render the site (i.e., the arguments used by Site.build).

The function does not have to return anything. In fact, anything returned by the function will be ignored.

### An example ###

The "blog" example project included with Gansa demonstrates how postrender functions can be used. Refer to the project's [README.md file](https://github.com/deckycoss/gansa/blob/main/example/blog/README.md) for more information.
