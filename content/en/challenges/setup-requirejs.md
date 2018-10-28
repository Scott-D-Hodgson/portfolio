---
title: "Setup RequireJS"
date: 2018-10-28T17:05:00-04:00
tags: ["RequireJS", "Bootstrap", "jQuery", "jQCloud", "Popper.JS", "Hugo"]
---
With the inclusion of [jQCloud](http://mistic100.github.io/jQCloud/), to perform a word cloud on the tags that have been built into the Hugo taxonomy, there was one issue that rubbed the wrong say:

The headers for every page in the site included the `script` reference to the jQCloud javascript.  This mean that any page, whether it used the word cloud or not, would always load the file.

The desire is, instead, to load the jQCloud script only if the word cloud was being used on the site.

In order to accomplish this, [RequireJS](https://requirejs.org/) is a script file that takes care of the dynamic loading of JavaScript files.  To leverage this, the include script for [RequireJS](https://requirejs.org/) must be included into the `header.html` partial so that it is injected into all the pages generated with [Hugo](https://gohugo.io/).

```html
<script src="/js/require.js"></script>
```

This evolves quickly, however, into a bad dream since the [Require.js](https://requirejs.org) and [jQuery](https://jquery.com) have a special relationship that requires a bit of working around.  This is detailed in the section on [how to use require.js with jQuery](https://requirejs.org/docs/jquery.html#globalvars).

Furthermore, the [Bootstrap](https://getbootstrap.com/) framework has a dependency on [Popper.JS](https://popper.js.org/), which also has a dependency on [jQuery](https://jquery.com), and loading all of these pieces in the `header.html` partial page quickly becomes a nightmare.

{{% credit "inrsaurabh" "https://magento.stackexchange.com/questions/211202/error-loading-popper-js-on-magento-2-theme-require-js" %}}

The solution is to define the appropriate paths and shims for the various script files such that, when loaded dynamically, all the dependencies have been met.

```html
require.config({
    baseUrl: '/js/lib',
    paths: {
        jquery: 'jQuery-3.3.1/jquery',
        jqcloud: 'jQCloud-2.0.3/jqcloud',
        popper: 'Popper-1.14.4/popper',              
        bootstrap: 'Bootstrap-4.0.0/bootstrap'
    },
    "shim" : {
        "popper": {
            "deps": ["jquery"],
            "exports": "Popper"
        },
        "bootstrap" : {
            "deps": ["jquery", "popper"]
        }
    }
});
```

With this defined, now the loading of the page's libraries, via [RequireJS](https://requirejs.org/), can be done without issue.  

```html
require(["jquery", "popper"], function( $, Popper ) {
    window.Popper = Popper;
    console.log("worked");  
    require(["bootstrap"], function() {
        $(function () {
            //alert("ok");
        });
    });
});
```

Finally, since this was undertaken to update the usage of jQCloud to be dynamic, the `taxonomy.html` partial page is updated with the following script inclusion.

```html
<script>
requirejs(['jqcloud'], function( jQCloud ) {
    var words = [];
    // todo: insert code to set values from taxonomy
    $(".taxonomy-cloud").jQCloud(words, { autoResize: true });
});
</script>
```