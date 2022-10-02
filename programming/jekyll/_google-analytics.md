---
layout: page
title: Integrar Google Analytics a tu sitio web
menu: jekyll
---

Google Analytics is the goto web tool to understand web traffic that comes to your site. It provides useful information like, where a user is from, how long they are on your website and what pages they have visited. Google Analytics could be used to make powerful design and business decisions based on what your users are doing.

One of the first things that I do when setting up a new website with Jekyll, is create a new Google Analytics account so that I could start collecting data from the website the moment it is up and running.

If you’ve got a Google account, getting Google Analytics is super easy. Since the steps in getting a Google Analytics account are better explained in their official website, I won’t be covering it here. Instead here is a link to the site.

Once you’ve created a new Google Analytics account for the site you want to track, you’ll want to grab the Google Analytics tracking code. This tracking code is a short piece of JavaScript that you include on all the pages you want to gather data regarding visitors to your website.

The tracking code could usually be found under Admin > Property > Tracking Info > Tracking Code.

On the Tracking Code page, take note to write down both the tracking ID and the tracking code which is found under a heading Global Site Tag (gtag.js). What I usually do is open up a blank text file and copy and paste both the tracking ID and code in there, to have it handy later.

Adding Google Analytics to all your pages and posts in Jekyll
Now that you’ve got your Google Analytics tracking code, it’s time to put it in all the pages and posts of your Jekyll project. This may sound daunting since immediately you might think to yourself, I have to copy and paste that tracking code in every single page that I create with Jekyll?

The answer to your question is no! Thanks to the templating system found in Jekyll, we can paste the tracking code once into a file and reference that file to have Jekyll include Google Analytics into every page it generates for us.

Crea un nuevo archivo llamado `analytics.html` en la carpeta `_includes` que se encuentra en tu proyecto de Jekyll.

~~~
├── _includes
│   ├── analytics.html
~~~

Copia y pega el código de seguimiento de Google Analytics en el archivo `analytics.html`. Tiene la forma siguiente:

~~~html
<!-- Global site tag (gtag.js) - Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=UA-XXXXXXXX-X"></script>
<script>
    window.dataLayer = window.dataLayer || [];
    function gtag(){dataLayer.push(arguments);}
    gtag('js', new Date());
    gtag('config', 'UA-XXXXXXXX-X');
</script>
~~~

donde `UA-XXXXXXXX-X` es tu código de seguimiento.

A continuación, abre el archivo `default.html` que se encuentra en la carpeta `_layouts`.

Añade `{% include analytics.html %}` encima de la etiqueta de cierre `</head>`.

~~~html
// _layouts/default.html
...
    {% include analytics.html %}
</head>
<body>
~~~

Ahora, tu página web incluirá el código de seguimiento de Google Analytics.

Para evitar que este código se cargue de manera local, se puede añadir una estructura condicional como la siguiente:

~~~html
// _layouts/default.html
...
    {% if jekyll.environment == 'production' %}
        {% include analytics.html %}
    {% endif %}
</head>
<body>
~~~

Esto hará que solo se añada el código de seguimiento a la página web cuando escribamos la siguiente línea en la  terminal:
~~~
JEKYLL_ENV=production jekyll build
~~~

Back in _includes/analytics.html replace UA-XXXXXXXX-X with {{ site.google_analytics }} like this,

~~~html
<!-- Global site tag (gtag.js) - Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id={{ site.google_analytics }}"></script>
<script>
    window.dataLayer = window.dataLayer || [];
    function gtag(){dataLayer.push(arguments);}
    gtag('js', new Date());
    gtag('config', '{{ site.google_analytics }}');
</script>
~~~

Open up your `_config.yml` file and add google_analytics: `"UA-XXXXXXXX-X"` replacing UA-XXXXXXXX-X for your own tracking ID.

To take it one step further, you could also open up _layouts/default.html and add a logical and operator to the if statement to only render the block if the google_analytics key exists in your _config.yml file,

~~~html
// _layouts/default.html
...
  {% if jekyll.environment == 'production' and site.google_analytics %}
  {% include analytics.html %}
  {% endif %}
</head>
<body>
~~~