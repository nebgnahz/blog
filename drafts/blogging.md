Blogging Framework
---

This post summarizes a few blogging frameworks available today and discuss their pros and cons.
It's not meant as an exhaustive list but hopefully enough to be helpful.

The boundary between blog and a personal site is quite blurry.
Often you will see them intertwined. One-post blog about yourself is, kind of, like your personal site.
Or a personal site with various links to articles you wrote is, more or less, a blog.
The frameworks I listed below can be used for either purpose.

---

There are two big categories of blogging framework, depending on how much time you'd like to invest and the degree of customization.
I will discuss them in turn.

## Commercial Sites

The first category is the commercially available sites that you can simply start blogging with two steps:
(1) register an account and (2) write. The following examples may give you a sense of what they are.

- [WordPress](https://wordpress.com/)
- [Blogger](https://www.blogger.com/)
- [Medium](https://www.medium.com/)
- [Jianshu](http://www.jianshu.com/)

They often have various theme/templates that you can choose to suit your personal aesthetics.
In terms of customization, there is ofen an admin page that you can enable/disable certain modules or tweak the layout.
With these websites, you do not need to worry about hosting.
Your blog is assigned a domain name (more precisely, a subdomain) and the content is hosted by the company.

I've personally used WordPress when I was interested in [indoor localization](https://indoorlocalization.wordpress.com/)
and [Medium](https://medium.com/@nebgnahz) for some personal experience/life blogging. There are alternative blogging sites
such as [Blogger](https://www.blogger.com).
Or if you are creative, any sites that can publish content to the Internet can be one, like this one I am using right now.
Github is more often used as a code sharing repository but, hey, your blog can be perfectly viewed as code.
With all the nice features of git, you can do history tracing, branching;
with Github's nice additional features, you can track issues or even collaborate.

In summary, the pros for this category is:
- Off the shelf, ready in minutes
- Beautiful as templates are created by desginers
- No need for hosting
- You often get additional features, such as reader statistics

There are a few downsides here:

- Hard to make arbitrary modifications
- You will see someone else using the same theme, guaranteed
- Not flexible for migrating to other providers
- Not a fancy domain name (this one is fix-able with redirection, DNS CNAME or DNS A record)

### Open-source Static Sites

There are a couple open-source projects for these static sites.

- Jekyll (in Ruby), [show case](https://github.com/jekyll/jekyll/wiki/sites), [themes](http://jekyllthemes.org/)
- Hugo (in Golang), [show case](https://gohugo.io/showcase/), [themes](http://themes.gohugo.io/)
- Hexo (in Javascript), [themes](https://hexo.io/themes/)

Jekyll is probably the most well-known one given its deep integration with [GitHub Pages](https://pages.github.com/).
However, Ruby, with its environment isn't the best for all cases. You need to install all the dependencies before you can get started.
For that reason, many newer developers who are looking for static site generator often prefers Hugo.
Written in Go, you can simply download a compiled binary and then go.
Hexo is on top of Javascript (Nodejs), so if you are a web developer, it's your arena.

These frameworks pretty much share a similar structure. I will use Jekyll as an example.

#### Configuration

First there is a config file describing your sites. In Jekyll, it's `_config.yaml`.
One example is as follows, and the complete reference is [available](https://jekyllrb.com/docs/configuration/).
Most of the time you would start with the auto-generated and add features as you go (i.e. Google).

```yaml
name: "John Doe"
description: "John Doe's Blog"

baseurl: "https://blog.example.com"
markdown: redcarpet
redcarpet:
  extensions: ["smart", "tables", "autolink", "with_toc_data"]
permalink: pretty
highlighter: pygments
```

#### Writing Markdown

Then there is often a folder to organize your blogs. It's `_posts` and `_drafts` in Jekyll for the default case.
You can change the default folder through the `_config.yaml` configuration file.
You write blog in markdown format. Well, technically it's more than markdown.
You need to first write [frontmatter](https://jekyllrb.com/docs/frontmatter/), which is the metadata of this blog post in `yaml` format.
Then you write your blog. Below is the first blog I wrote when I was playing around with Jekyll.

```markdown
---
layout: post
title:  "Welcome to Jekyll!"
date:   2013-08-12 19:39:03
categories: dev
tags: [dev, web, design]
description: Should I declare success in my migration from Wordpress to Jekyll?
---
It took me a while actually to dive into Jekyll, but once you've
got used to it, it's actually much simpler than Wordpress. And
this simplicity is behind some sophistication -- careful design
of workflow, nice code re-use, etc. With some stolen css, this
new blog is ready to ship.

Inspired by Matt Swanson's blog -- [Do things, write about
it](http://mdswanson.com/blog/2013/08/11/write-things-tell-people.html),
I have determined to write something down regularly
AGAIN. Previous failed blogs (two Wordpress ones) illustrate my
laziness, but changes are made day-by-day. Keeping track of what
I think during the PhD life would probably be beneficial, at
least to myself in the future. While hopefully, some unpolished
writings may even inspire others.
```

The next step is basically get yourself familiarized with markdown syntax.
[This reference](https://daringfireball.net/projects/markdown/syntax) is a good reference.
In my experience, this is probably the simplest language you can learn.
Markdown has its limitations, for example, you cannot control the image size. It will load the image as is.
But that's not an issue at all. At places you want fine-grain control, use HTML; they co-exist well.

```markdown
Bruce Cornner: beautiful, horrible, hogwash, genius, maundering, precise,
quaint, avant-garde, historical, hackneyed, masterful, trivial, intense,
mystical, virtuosic, bewildering, absorbing, concise, absurd, amusing,
innovative, nostalgic, contemporary, iconoclastic, sophisticated, trash,
masterpieces, etc. IT'S ALL TRUE.

<img src="images/bruce-conner-small.jpg"
     alt="Bruce Conner"
     style="width:340px;"/>
```

#### Tuning Theme

It's often a good idea to start with some theme and then tune it.
Creating a theme from scratch is quite time-consuming; and hard to get beautiful.
Pick a theme and then modify parts.

For the HTML part of the theme, there are two parts.
`_includes` folder defines all the modules, such as header, footer, side bar, etc.
`_layouts` has various layouts for your page, such as a default layout, a layout for individual post, etc.
In this way, modules are reusable and it's very easy to change/update layouts.

For the CSS of a page, it's often in a `assets` folder or `public` folder in the root directory.
I am old-schooled, using `css` directly and I am recently quite fond of [skeleton](http://getskeleton.com).
Modern approaches often using `scss`.
The syntax is relatively easy to learn but it's quite tricky in terms how to get a nice-looking site.

## Other Knowledges

### DNS + IP

The first you need to know about a website is probably its name, which, in technical terms, is a URL (unique resource locator).
It consists of a protocol specification, domain name, and resource path.
IP is Internet protocol and we usually will say "IP address". It often determines the actual location of a machine.
For example, `Github.com` is a domain name, and if you use `$ dig github.com`, you will see something like the following:
```
 [ . . . ]

;; ANSWER SECTION:
github.com.             24      IN      A       192.30.253.113
github.com.             24      IN      A       192.30.253.112

 [ . . . ]
```

`192.30.253.113` and `192.30.253.112` are IP addresses for the same domain name.
Having multiple IP addresses can be quite useful for fault tolerance and performance.
It's like having two homes and you can go either one depending on which one is closer;
and if you lose the keys to one, the other one is still available. And yes, `dig` is the tool to find out :)

### Server and Hosting

Your blog needs to live somewhere. Having a file on your laptop doesn't give other people access to it.
You may configure DNS in a way that points the blog to your laptop but often we use dedicated servers,
as the name suggests, they serve the files.

You can buy a physical machine and use it as server; or rent a (often virtual) server from someone.
I typically go to [Low End Box](https://lowendbox.com/) for discounted hosting options; but if your budget is sufficient,
pick one. DigitalOcean is pretty good.

You may also use hosting services without directly controlling the server.
My recent fond is [Netlify](https://www.netlify.com) that can do continuous deployment with Github repos.

### HTML + CSS + JS

There are three parts: content (what), layout (where) and reactive features (advanced how).
Content is expressed as HTML file (such as this line is in `<p>` paragraph tag);
CSS dictates the layout (that controls the font, text size and its location on the page); 
and Javascript to implement fancy features (such as click to go back to top).

There are some overlapped functionality among these three parts.
You can put an image using HTML `<img>` tag, CSS `background` property or dynamically updated with Javascript.

### HTTPS

It's almost a must.

Having HTTPS makes the connection encrypted and makes your site much more legit nowadays.
The tool to do it is mature, and now free.
Use [Let's Encrypt (also known as Cerbot)](https://certbot.eff.org/).
Netlify has a nice integration that gives you one-click HTTPS.

### Responsive Design

Nowadays increasingly people are viewing sites using their mobile phone instead of desktop.
Being responsive or not will largely affect readers' experience.
These are typically handled in CSS, although you can achieve the same thing with Javascript.

Typically you use media query:
```css
/* Default */
body {
  font-size: 1.5rem;
}

/* Mobile */
@media (min-width: 400px) {
body {
  font-size: 2.0rem;
}
}

/* Tablet */
@media (min-width: 750px) {
body {
  font-size: 2.0rem;
}
}
```

### Debugging

Use your favorite browser and right click, there is a `Inspect` option.
Chrome's one is currently my choice since it supports traffic throttling quite well.
