---
title: 'Migrate from Wordpress to GatsbyJS'
description: 'I finally came back to write a new post :) A few months ago, I decided to migrate my blog from Wordpress to any SSG (Static Site Generator). I was between Jekyll and GatsbyJS and chose GatsbyJS because it is written on JavaScript, most popular SSG nowadays and has many additional futures.'
date: '2020-10-14T23:37:21+06:00'
template: 'post'
draft: false
slug: 'migrate-from-wordpress-to-gatsbyjs'
categories: ['Life']
tags: []
socialImage: '/media/2020-10-14--migrate.png'
---
I finally came back to write a new post :) A few months ago, I decided to migrate my blog from [Wordpress](https://wordpress.org/) to any SSG (Static Site Generator). I was between [Jekyll](https://jekyllrb.com/) and [GatsbyJS](https://www.gatsbyjs.com/) and chose GatsbyJS because it's written on JavaScript, most popular SSG nowadays and has [many additional futures](https://www.gatsbyjs.com/features/jamstack/gatsby-vs-jekyll-vs-hugo). 

As a starter, I've chosen [gatsby-starter-lumen](https://github.com/alxshelepenok/gatsby-starter-lumen) because IMO it's the best one for blogs. 

Why you should migrate from Wordpress to Gatsby:

- Your blog don't need any paid hosting service anymore (You can use your GitHub/GitLab instead)
- You can easily add/edit blog pages and posts as [Markdown](https://daringfireball.net/projects/markdown/) documents with a special header where you need to place necessary information set by your starter or yourself such as title, slug, description etc.
- You can easily add necessary plugins provided by Gatsby instead of choosing around many Wordpress ones
- **Main advantage** - Gatsby pages load like a rocket while Wordpress is a slow piece of shit

After reading this post you will be able to:

1. [Start your Gatsby Website](#start-your-gatsby-website)
2. [Configure your website according to your personal data](#configure-your-website-according-to-your-personal-data)
3. [Export your Wordpress posts as Markdown](#export-your-wordpress-posts-as-markdown)
4. [Add exported posts in Gatsby](#add-exported-posts-in-gatsby)
5. [Assign your own domain name](#assign-your-own-domain-name)

## Start your Gatsby website

You can easily start your website using any [existing starter](https://www.gatsbyjs.com/starters/). Almost all starters `README.md` have instructions how to deploy a particular starter on GitHub Pages and/or Netlify. As I've written before, I used [gatsby-starter-lumen](https://github.com/alxshelepenok/gatsby-starter-lumen). It's `README.md` has a button ![](/media/2020-10-14--deploy-to-netlify-button.png) which you just need to press once to deploy the starter on Netlify. It will suggest you to give GitHub/GitLab permissions and choose a name for your new repository. After finishing all initialization steps, you can clone your website's repo and add/edit any file you need.

## Configure your website according to your personal data 

After deploying I suggest you to change your personal information in `config.js` according to your starter. In my config I've changed url, website name, social links and other necessary fields.

## Export your Wordpress posts as Markdown

I've used [WP Gatsby Markdown Exporter](https://wordpress.org/plugins/wp-gatsby-markdown-exporter/) to simply export posts I've already written and their media.

![](/media/2020-10-14--wp-export-screenshot.png) 

You can also use similar tools such as [ExitWP](https://github.com/some-programs/exitwp).

## Add exported posts in Gatsby

After deploying your starter and exporting Wordpress posts you need to change each post header according to the template given in sample posts from your starter. You can see the instance for my starter below.

![](/media/2020-10-14--post-header.png)

You also need to add all media from your posts into `/media/` directory of your website.

## Assign your own domain name

Using Netlify you can easily assign your own domain name to your new website. You just need to click ![](/media/2020-10-14--domain-settings-button.png) on your blog's Netlify page and add your domain and nameservers. As for me, I'm using [Namecheap](https://www.namecheap.com/) and I've just chosen *Custom DNS* in my domain settings and provided this custom DNS nameservers to Netlify. 

![](/media/2020-10-14--custom-dns.png)

---

I hope this post will help you to migrate your blog from old and slow Wordpress to modern and fast GatsbyJS. Have a nice day!
