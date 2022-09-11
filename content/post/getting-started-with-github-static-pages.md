---
title: "Getting Started With Github Static Pages"
description: "Enthusiastic Technology explorer! Love's Biking, Hiking & Eating Delicious Food!"
date: "2022-06-28"
aliases: ["posts", "articles", "blog", "showcase", "docs"]
author: "themayurkumbhar"
tags: ["getting-started", "markdown", "portfolio", "github-pages"]
draft: false
---

If you reading this blog means you want to create minimal portfolio or profile without thinking more around designing 
but should be more professional and small, compact & easy to implement without any setup, learning any new language. 
If you are the one who don't like to code around HTML tags, CSS files or JS. If you are backend engineer like me 😄 and 
want good profile page without worrying about the frontend language.

> You are always welcome to raise pull request to improve this blog.

GitHub provides each user domain of its github username followed by `github.io` where your profile is hosted as a 
website. There are multiple ways you can create your portfolio. You can use any existing framework, language, tools, 
forking existing repositories and updating as required. This post will focus on how can you write only your portfolio 
content using markdown and let github take care of rest.
Once you have basic repository setup ready you can follow along.

## Why to use markdown? 🤔

Markdown is most widely used for documentation purpose. Most of developers use this as day to day work in documenting 
either APIs, WiKi or repository README.md files. This enables best practices and standard structure present in markdown 
to write portfolio in better format. Also developers are mastered in writing markdown (if you are not, strongly suggest 
to practice documentations using markdown).

> 💡 Quick understanding of [MarkDown](https://www.markdownguide.org/basic-syntax/)!

## Let's Get Started -

### Repositroy Structure Layout 🧱

```text
.
├── Readme.md
├── _config.yml
├── _includes
│   ├── about-me.md
│   ├── contact.md
│   ├── education.md
│   ├── posts.md
│   └── professional.md
├── index.md
└── posts
    └── getting-started.md

```

### Understanding different files in Repository 📚

#### 1. [index.md](https://github.com/themayurkumbhar/themayurkumbhar.github.io/blob/master/index.md?plain=1) -

This is the main file which used as root for the website. When someone hits your profile url this is the first page 
that gets loaded, which also called as "Landing Page"

* You can have a single page website where you can add all the profile data in the same file.
* Or you can choose the separate the files in multiple folders and update specific sections as and when required.

> 💡 We will discuss the multiple files approach in this post.

* [index.md](https://github.com/themayurkumbhar/themayurkumbhar.github.io/blob/master/index.md?plain=1) file looks like this:

```markdown
  --- 
  layout: default #layout style
  ---
  
  {% include file1.md %}
  
  {% include file2.md %}
  
  {% include file3.md %}
  
```


* Layout part defines which layout to use while rendering index file.
* Syntax {% raw %}`{% include filename.md %}`{% endraw %} imports the files in your index file and expands the contents
to fit in a single file.
    * github before generating website first imports all the contents and then renders the files conetent as HTML/CSS.

#### 2. [\_config.yml](https://github.com/themayurkumbhar/themayurkumbhar.github.io/blob/master/_config.yml?plain=1) -

This file used to configure the configuration parameters which can be used by the github website generator
[Jekyll](https://github.com/daattali/beautiful-jekyll/blob/master/_config.yml?plain=1). We will see the some basic
required configurations which will enable us to generate the portfolio website.

* [config file](https://github.com/themayurkumbhar/themayurkumbhar.github.io/blob/master/_config.yml?plain=1) looks like below:

```yaml
  
  title: <Title of your website>
  description: <discription of your wesite>
  theme: jekyll-theme-slate #choose theme for your blog
  relative_links: #true to enable your posts relative paths
    enabled: true
    collections: false
  plugins:
    - jekyll-relative-links #enable your posts links relative path
    - jekyll-default-layout #default or create new layout
 
```

* You can select a theme from the list of jekyll themes [HERE](http://jekyllthemes.org/)

> 💡 This website is generated using a theme called [jekyll-theme-slate](https://github.com/pages-themes/slate)

#### 3. [\_includes](https://github.com/themayurkumbhar/themayurkumbhar.github.io/tree/master/_includes) -

This **folder** contains all the separate MarkDown files which are part of the portfolios and are broken down to 
specific contents of file, so they can be modified independently.

* Includes can contain any kind of data files which are logically separated from each other contents.
* You can distribute your contents as required in multiple files and then include them as and when required in different files.
* Example take [contact.md](https://github.com/themayurkumbhar/themayurkumbhar.github.io/tree/master/_includes/contact.md) file.

```markdown

  ## 📇 [Connect with Me!](#contact)
  ✉️ [mailme@mail.com](mailto:mailme@mail.com)
  📱 [+91-1234567890](tel:+911234567890)
  
```
* Then you can include this in your root [index.md](https://github.com/themayurkumbhar/themayurkumbhar.github.io/blob/master/index.md?plain=1) file.


```markdown
  {% include contact.md %}
```


#### 4. [posts](https://github.com/themayurkumbhar/themayurkumbhar.github.io/blob/master/_includes/posts.md?plain=1) -

This **folder** contains all your blog posts which are separated with each new MarkDown file. Once the blog post file 
is created you need to include that in your [posts.md](https://github.com/themayurkumbhar/themayurkumbhar.github.io/blob/master/_includes/posts.md?plain=1) file to publish on your blogs.

* Always create a new file for each blog, include them only when ready to publish.
* Example take a blog file [getting-started.md](https://github.com/themayurkumbhar/themayurkumbhar.github.io/blob/master/posts/getting-started.md?plain=1):

```markdown
  
  ---
  layout: default
  title: Getting Started
  ---
  
  # Getting Started With GitHub Pages in Markdown!
  
  **Hello world!**, This is blog post using **Markdown** and **GitHub Pages**.
  
  I hope you like it!
  Conetents of blog post goes here...
  
```
* Now consider our root blogs in [posts.md](https://github.com/themayurkumbhar/themayurkumbhar.github.io/blob/master/_includes/posts.md?plain=1) file -
    * We will include `getting-started.md` in `posts.md` file so it can be rendered in blogs section of your portfolio.

```markdown

  ## Tech Blogs
  
  ### [1. Getting Started ](/link/to/posts/getting-started.html)
 
```

> 💡 You can also include diagrams/images/videos/code blocks in your blog.

### Setting up changes in github ⚙️

Once you are ready with your portfolio files, make sure then are committed and pushed to your github repository named
`<your_github_username>.github.io`.

Let's now set up your special repository to act as a website using github.

1. Go to `Settings` on your repository
2. Select `Pages` section, which will show you `Github Pages`
3. Now select drop-down `Source` and choose `master` branch to configure & hit `save`.
4. Wait for a minute or two, you will get the link to your website
5. Boom! Your website is ready!!! 🚀

> 💡 Bonus Fact: You can include HTML/CSS tags in your MarkDown file to have more control over customizations! 😎
