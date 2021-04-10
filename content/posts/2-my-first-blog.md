---
title: My first blog
date: 2021-04-10
categories: # Optional, will be displayed above the title of the page
- Software Development
tags: # Optional, will be displayed at the bottom end of the post
- github
- deployment
- jekyll
- hugo
- gatsby
- static site generator
draft: false
---

Since I'm a very chatty person and I like to talk about things I'm interested in, mostly about software development, but also about cyber security, DevOps etc, I decided to create a blog and write down my thoughts and my journey and maybe some of my posts will help others on their journey. But I'm also open for a good and respectful discussion or to meet other people with similar interests.

There are plenty of solutions to start with a blog, but since I'm a software developer and I've never done something with a static site generator, I decided to dig into
this topic, get an overview of current tools and do a short comparison.

## What is a static site generator
A static site generator (SSG) is a tool to produce static websites. This mean the produced website doesn't consits of PHP, Python or similar programming languages.
The website will just use the tool you're used to from frontend development: HTML, CSS and JavaScript.
The benefits are:
- easier to write
- easer to deploy
- more secure
- fast page loading times

For example this article is just a simple markdown file which was translated to a HTML page and it's hosted for free on [GitHub Pages](https://docs.github.com/en/pages/getting-started-with-github-pages) which I can really recommend. But there are many other similar services out there, e. g. DigitalOcean, Netlify or Heroku.

## Jekyll
Jekyll is one of the first known SSG and it's integrated into GitHub Pages. This means you can have a very easy and fast start if you choose to use GitHub Pages.
It is written in ruby which isn't a major language in 2021.
In my tests it was slower than the competitors and I tried to focus on other SSGs which use languages I also use for other projects.

## Gatsby
[Gatsby](https://www.gatsbyjs.com/) is currently one of the most used SSG on the market. It uses Node.js and mainly JavaScript but it's currently in the process of rewriting the code to TypeScript.
If you are familar with React or JavaScript in general and you want to have flexibility, Gatsby is definitely something you should consider.
In my case, I just wanted to have an easy tool to create blog articles. I don't want to write JavaScript for that case. 

## Hugo
[Hugo](https://gohugo.io/) is another SSG which a fast growing community. It is written in Go (golang) which performs much better than Gatsby in every aspect.
It was easier to setup a local blog and the re-compile times are much faster than Gatsby.
I didn't do a complete comparison of Gatsby and Hugo since I just needed a blog solution. Therefore I just can say that Hugo is the better solution if you just want to have a simple blog.

## Writing articles
Writing blog articles with Hugo is pretty straightforward.
At the beginning I had to [install Hugo](https://gohugo.io/getting-started/installing#scoop-windows) first. I choose to use the windows package manager [scoop](https://scoop.sh). For windows there is also a choco package available and in the future hopefully a winget package.
After Hugo was installed, I had to initialize a Hugo project with `hugo new site <blog-name>`, [add a theme](https://gohugo.io/getting-started/quick-start/#step-3-add-a-theme) to it as a git submodule and
finally I created my very first page with `hugo new posts/<article-name>.md`.
To start my local development server and to actually see the results of those few commands I entered previously, I just had to run `hugo server -D`.
Besides knowing [Markdown](https://www.markdownguide.org/getting-started/) there is just a little configuration you have to look out. Hugo uses a config.toml file as a centralized configuration for your
website. If the theme you use have configuration options, you can add / change that in the config.toml file as well.
Every blog article consits of a head and a body, similar to an HTML page. In the head you can define things like title, categories, release date and if it's public or not (draft). Those information
are used be Hugo and your chosen theme. The body then is pure markdown, nothing new here.

## Deployment
For the blog I used a public [GitHub repository](https://github.com/Zerotask/zerotask.github.io) which just has a simple `main` branch. Every time I push commits to that remote branch,
the [Hugo GitHub Action](https://github.com/marketplace/actions/hugo-setup) is triggered.
This action will checkout the branch and runs a `hugo --minify` and deploys the result (public folder) to a new branch `gh-pages`.
In the GitHub Pages settings I set this branch as the source. So after the action is done, GitHub Pages will grab the produces website and push it to [zerotask.github.io](https://zerotask.github.io).

For the future I plan to add some checks for grammar, markdown syntax etc which are also nice options GitHub Actions provide you.

