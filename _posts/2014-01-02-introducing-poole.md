---
layout: post
title: Introducing Poole
---

*The Strange Case of Dr. Jekyll and Mr. Hyde* tells the story of a lawyer investigating the connection of two persons, Dr. Henry Jekyll and Mr. Edward Hyde. Chief among the novel's supporting cast is a man by the name of Mr. Poole, Dr. Jekyll's loyal butler.

-----

Poole is the butler for [Jekyll](http://jekyllrb.com), the static site generator. It's designed and developed by [@mdo](https://twitter.com/mdo) to provide a clear and concise foundational setup for any Jekyll site. It does so by furnishing a full vanilla Jekyll install with example templates, pages, posts, and styles.

There are currently two themes built on Poole:

* [Hyde](http://hyde.getpoole.com)
* [Lanyon](http://lanyon.getpoole.com)

Learn more and contribute on [GitHub](https://github.com/poole).

### What's included

Poole is a streamlined Jekyll site designed and built as a foundation for building more meaningful themes. Poole, and every theme built on it, includes the following:

* Complete Jekyll setup included (layouts, config, [404](/404.html), [RSS feed](/atom.xml), posts, and [example page](/about))
* Mobile friendly design and development
* Easily scalable text and component sizing with `rem` units in the CSS
* Support for a wide gamut of HTML elements
* Related posts (time-based, because Jekyll) below each post
* Syntax highlighting, courtesy Pygments (the Python-based code snippet highlighter)

Additional features are available in individual themes.

### Browser support

Poole and it's themes are by preference a forward-thinking project. In addition to the latest versions of Chrome, Safari (mobile and desktop), and Firefox, it is only compatible with Internet Explorer 9 and above.

### Download

Poole is developed on and hosted with GitHub. Head to the <a href="https://github.com/poole/poole">GitHub repository</a> for downloads, bug reports, and features requests.

Thanks!

----

*Ejemplo de codigo (ver el código fuente)*

{% highlight python %}
#-*- coding: utf-8 -*-
from flask.ext.wtf import Form
from wtforms import StringField, BooleanField, TextAreaField
from wtforms.validators import DataRequired, Length
from models import User

class LoginForm(Form):
    openid = StringField('openid', validators=[DataRequired()])
    remember_me = BooleanField('remember_me', default=False)

class EditForm(Form):
    nickname = StringField('nickname', validators=[DataRequired()])
    about_me = TextAreaField('about_me', validators=[Length(min=0, max=140)])

    # Constructor personalizado para este formulario. Necesita el nickname
    def __init__(self, original_nickname, *args, **kwargs):
        Form.__init__(self, *args, **kwargs)
        self.original_nickname = original_nickname

    # Validador personalizado.
    def validate(self):
        if not Form.validate(self):
            return False
        if self.nickname.data == self.original_nickname:
            return True
        user = User.query.filter_by(nickname=self.nickname.data).first()
        if user != None:
            self.nickname.errors.append(gettext(u'This nickname is already in use. Please choose another one.'))
            return False
        return True

class PostForm(Form):
    post = StringField('post', validators=[DataRequired()])

class SearchForm(Form):
    search = StringField('search', validators=[DataRequired()])
{% endhighlight %}


*Temas Jekyll*

[so-simple-theme](http://mmistakes.github.io/so-simple-theme/theme-setup/){:target="_blank"}<br>
[poole theme](https://github.com/poole/poole){:target="_blank"}<br>

*Jekyll general*

[How I Created a Beautiful and Minimal Blog Using Jekyll, Github Pages, and poole](http://joshualande.com/jekyll-github-pages-poole/){:target="_blank"}<br>
[Jekyll-syntax. All jekyll pygment variations of syntax.css](https://github.com/iwootten/jekyll-syntax)<br>
[Pygments home](http://pygments.org/){:target="_blank"}<br>
[Jekyll home](http://jekyllrb.com/){:target="_blank"}<br>
[kramdown Syntax](http://kramdown.gettalong.org/syntax.html){:target="_blank"}<br>
[Jekyll From Scratch - Getting Started](http://pixelcog.com/blog/2013/jekyll-from-scratch-introduction/){:target="_blank"}<br>
[Jekyll From Scratch - Core Architecture](http://pixelcog.com/blog/2013/jekyll-from-scratch-core-architecture/){:target="_blank"}<br>
[Jekyll From Scratch - Extending Jekyll](http://pixelcog.com/blog/2013/jekyll-from-scratch-extending-jekyll/#contact-forms-with-jotform){:target="_blank"}<br>
[¿Cómo hice el blog? - Raúl Ávila](http://raulavila.com/2015/01/como-hice-el-blog/){:target="_blank"}<br>

*Jekyll plugins*

[Colección de plugins indispensables](https://divshot.com/blog/web-development/advanced-jekyll-features/){:target="_blank"}<br>
[Plugins Jekyll](http://www.jekyll-plugins.com/){:target="_blank"}<br>
[Asset bundling with Jekyll - Cómo construir asset Jekyll (agrupar en un solo archivo el  código estático: css, js, images, etc)](http://tkareine.org/blog/2013/02/22/asset-bundling-with-jekyll/){:target="_blank"}<br>
[¿Cómo implementar plugins en GitHub 1?](http://charliepark.org/jekyll-with-plugins/){:target="_blank"}<br>
[¿Cómo implementar plugins en GitHub 2?](http://arademaker.github.io/blog/2011/12/01/github-pages-jekyll-plugins.html){:target="_blank"}<br>
[¿Cómo implementar plugins en GitHub 3?](http://blog.nitrous.io/2013/08/30/using-jekyll-plugins-on-github-pages.html){:target="_blank"}<br>

*Diseño web*

[Compass home](http://compass-style.org/){:target="_blank"}<br>
[Tutorial de Compass y Sass](http://www.intersencia.com/blog/tutorial-de-sass-y-compass/){:target="_blank"}<br>
[Sass home](http://sass-lang.com/){:target="_blank"}<br>
[The Sass Way](http://thesassway.com/){:target="_blank"}<br>
[Sass, el manual oficial](http://librosweb.es/libro/sass/){:target="_blank"}<br>
[Introducción a Sass y Compass](http://www.cristalab.com/tutoriales/introduccion-a-sass-y-compass-c111623l/){:target="_blank"}<br>
[Ejemplo de graidentes y texto 3 D con Sass y Compass](http://www.cristalab.com/tutoriales/colores-gradientes-y-texto-3d-con-sass-y-compass-c111672l/){:target="_blank"}<br>
[Manual bootstrap 3 (spanish)](http://librosweb.es/libro/bootstrap_3/){:target="_blank"}<br>
[How to Learn Web Design](https://ash.guru/how-to-learn-web-design/){:target="_blank"}<br>
[Recursos web jquery](http://www.unheap.com/){:target="_blank"}<br>
[10 Great Google Font Combinations You Can Copy](http://designshack.net/articles/css/10-great-google-font-combinations-you-can-copy/){:target="_blank"}<br>
[Stop Using Arial & Helvetica](http://www.64notes.com/design/stop-helvetica-arial/){:target="_blank"}<br>
[Fontsquirrel - Sitio para bajar fuentes free](http://www.fontsquirrel.com/){:target="_blank"}<br>
[Colores y paletas](http://www.color-hex.com/){:target="_blank"}<br>
[Más colores y paletas](https://mudcu.be/sphere/){:target="_blank"}<br>
[Idea para la cabecera - Código de barras](http://www.desarrollomultimedia.es/articulos/crear_un_codigo_de_barras_photoshop.html){:target="_blank"}<br>

