---
layout: post
title:  "Blogging with Dr. Jekyll's potion - part 1"
date:   2014-01-29 13:35:12
tags: tutorial, web, html, ruby, javascript, jekyll, github pages
categories: tutorial, web

---

This is the first in a small series of posts on static site generators. I decided to set up this blog in [GitHub Pages](http://pages.github.com/) using [Jekyll](http://jekyllrb.com/) (Ruby-based), and I plan to start another one using [Assemble](http://assemble.io) (Node.js-based). I'm also going to try out some solutions like [Octopress](http://octopress.org) which extends Jekyll and [Prose.io](http://prose.io) which offers a web editor for GitHub. I'll take notes while I explore the frameworks and technologies, and share them as blog posts. 

[Jekyll](http://jekyllrb.com/) is a static site generator which can be used as a  blogging platform for software developers who enjoy writing code and are productive writing posts in plain text [Markdown](http://daringfireball.net/projects/markdown/). It's great if you want to have more control over your posts than you would with a blogging service such as [WordPress](http://www.wordpress.com) but are not willing to code one from scratch. You'll have to invest some time configuring the site, adding skins, services, writing templates, etc. and you won't have a dashboard to edit and manage your posts (unless you write one yourself). But once you have the minimum environment set up it runs quite smoothly. And if you use it for [GitHub Pages](http://pages.github.com/), you just have to write your posts in your favorite Markdown editor and ```git commit``` the results.

If you wish something a bit more automated, take a look at [Octopress](http://octopress.org) which extends Jekyll with a minimal blogging framework.

## Installation

Since Jekyll is a Ruby application you'll need to have a Ruby environment set up. In Linux platforms you  can try something like ```sudo apt-get install rubygems```. I believe that Macs have native Ruby support. I'm not sure about gem. Anyway, you can probably install it via [HomeBrew](http://brew.sh/). In Windows, try the [RubyInstaller](http://rubyinstaller.org/).

Once you have Ruby and Rubygems set up, run 
```gem install jekyll``` and you're done.

Now choose a local workspace directory and create a new project with the ```new``` command:

```
jekyll new my-blog
```
If you get an error complaining about missing requirements (this happened in some Linux environments where I installed Jekyll) run ```gem install json``` and try again.

This will set up a minimum structure for the blog with some sample posts. You can now generate and serve the site. Just enter the directory and issue the ```serve``` command:

```
cd my-blog
jekyll serve
```

And browse to <http://localhost:4000> to try it out.

{include "/public/images/2014-01/jekyll_1.png"}

You can see it's quite bare. No skins, no comments, no menus, no sidebars; just the essential parts. Now you need to configure it and add all the rest. You will have to create your own skins, add services, pagination, context menus, etc. In this post I'll show you how to set it up with some basic configuration.

## Configuration

When you run the command:

```
    jekyll new my-blog
```

You get a minimum default directory structure like this

```
my-blog/
    _layouts/
        default.html
        post.html

    _posts/
        2013-12-11-welcome-to-jekyll.markdown

    css/
        main.css
        syntax.css

    index.html
    _config.yml
```

From the root directory you can run ```jekyll build``` to generate the site into the ```_site``` directory, which will be created. The command ```jekyll serve``` builds the site and makes it available through a simple web server on port 4000. I prefer to use  ```jekyll serve --watch``` which regenerates the site automatically after any changes.

If you ran the command ```jekyll serve``` there will already be a ```_site``` directory containing the document root of the generated site (you can safely delete it whenever you want).

Jekyll treats the current directory as its source and uses ```_site``` as the destination directory. Certain files and subdirectories, including the ones starting with an underscore are treated as templates by Jekyll and will be processed. The others will be simply copied to the destination directory. You can specify different source and destination directories in the configuration or using flags when running ```jekyll```. More about this in the [Jekyll usage documentation](http://jekyllrb.com/docs/usage/).

### Files
Lets take a look at some of the generated files.
#### _config.yml
This is the global configuration file. It uses the [YAML](http://www.yaml.org/spec/1.2/spec.html) data format (which most of the time consists of ```name: value``` pairs) to set configuration parameters and metadata which can be used globally. Local context-sensitive parameters may also be defined using a YAML subset: [YFM - YAML front matter](http://jekyllrb.com/docs/frontmatter/) before each file that should be processed. 

Open the ```_config.yml``` file. It probably contains this:

```
name: Your New Jekyll Site
markdown: redcarpet
pygments: true
```

Here you can set properties that are recognized by Jekyll, such as ```markdown``` which specifies the flavor of markdown you wish to use, or ```pygments``` which turns on or off code-highlighting. You can access the values of these properties through a global object variable called ```site``` in your templates using the Liquid templating language. To access the name property you just need to place ```{{ site.name }}``` somewhere in your file.





#### index.html
You can place any text files in the root of your source directory. If they have a YFM header before their content, they will be processed. The YFM header can be empty. The following page will be processed and generate a file containing "The name of the site is Your New Jekyll Site" because it will read the ```name``` property from ```_config.yml```:

```
---
---

The name of the site is {{ site.name }}.
```

But you can also add YAML data in the header. Take a look at the ```index.html``` file:

```
---
layout: default
title: The title of this site
---

	<div id="home">
  		<h1>Blog Posts</h1>
  		<ul class="posts">
   	 	{% for post in site.posts %}
     	 		<li><span>{{ post.date | date_to_string }}</span> &raquo; 
     	 		    <a href="{{ post.url }}">{{ post.title }}</a></li>
   		{% endfor %}
  		</ul>
	</div>

```

#### _posts/2013-12-11-welcome-to-jekyll.markdown
#### _layouts/default.html and _layouts/post.html
#### css/main.css
#### css/syntax.css

For most of the configuration you will use [YAML](1), and for writing the templates you can use [Liquid](http://wiki.shopify.com/Liquid).
Basic configuration is declared in the [YAML](1) file ```_config.yml``` 


you can...
The ```_layouts``` directory contains the base templates for each different kind of file you use 

The ```_posts``` directory is where you will 
Besides those directories that were already created for you, you might want to add a ```_includes``` directory where you could store file fragments to build composite views.
Run the jekyll 

## Altering the site structure

### Posts
### Pages
### Layouts
### Includes

## Yaml

## Liquid

## Planning a responsive site

### Media-queries and mobile-first

## Adding services
- Disqus
- Semantic Web
- Social Media

## Writing drafts

## Comments