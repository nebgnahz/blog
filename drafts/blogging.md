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

- Jekyll (in Ruby)
- Hugo (in Golang)
- Hexo (in Javascript)

And I've seen (also personally used Gitbook).

## Other Knowledges

### DNS + IP

The first you need to know about a website is probably its name, which, in technical terms, is a URL (unique resource locator).
It consists of a protocol specification, domain name, and resource path.

### Server and Hosting

Your blog needs to live somewhere. Having a file on your laptop doesn't give other people access to it.
You may configure DNS in a way that points the blog to your laptop but often we use dedicated servers,
as the name suggests, they serve the files.

You can buy a physical machine and use it as server; or rent a (often virtual) server from someone.
I typically go to [Low End Box](https://lowendbox.com/) for discounted hosting options; but if your budget is sufficient,
pick one. DigitalOcean is pretty good.

You may also use hosting services without directly controlling the server.
My recent fond is Netlify that can do continuous deployment with Github repos.

### HTML + CSS + JS

There are three parts: content (what), layout (where) and reactive features (advanced how).
Content is expressed as HTML file (such as this line is in `<p>` paragraph tag);
CSS dictates the layout (that controls the font, text size and its location on the page); 
and Javascript to implement fancy features (such as click to go back to top).

There are some overlapped functionality among these three parts.
You can put an image using HTML `<img>` tag, CSS `background` property or dynamically updated with Javascript.

### Responsive Design

Nowadays increasingly people are viewing sites using their mobile phone instead of desktop.
Being responsive or not will largely affect readers' experience.
