---
layout: post
title:  "Trying Dr. Jekyll's potion"
date:   2014-01-29 13:35:12
categories: news, jekyll, github pages
---

As a software developer, I've always tried to use the technology I teach in my own projects but that wasn't always possible. Several years ago I started a site generation platform based on XSLT, and used it to set up my company's website, but I didn't have enough time to maintain it so I gave up. Ten years ago I wrote a small blogging platform in Java using EJB 2. It was a great project to master the technology, and I used several parts of it for teaching, but I was never able to set it up with my hosting provider.

After a long time not blogging about technology, I decided to set up this blog. Again I was tempted to write a ultra-simple blogging application or at least adapt one. I didn't want to start another Wordpress blog. I wanted something that I could easily configure and have total control over style and structure, based on templates with markdown support, preferably written in JavaScript. I didn't really find it and once again started thinking about writing a blogging platform. But then I ran out of time, I found Jekyll and decided to give it a try.

Jekyll is a Ruby application so it's very easy to set up (especially if you are on a Mac which has native Ruby and Gem support). The [project page](http://jekyllrb.com/) shows how to download, install and set the site up with four shell commands. You write the posts using markdown and templates, and jekyll generates the working site for you. And you can add other plugins to the process, such as SASS/LESS CSS pre-processsing for example. If you host your blog in GitHub Pages you don't even need to run Jekyll - just GIT push the site and your are done.

### Configuration

Almost. You'll probably want to configure the structure of your site, add services (such as [Disqus](http://disqus.com/) for comments), stylesheets or skins.

When you run the command:

```
    jekyll new my-blog
```

You get a minimum directory structure like this

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



### Comments