+++
banner = "hugo.png"
categories = ["Learning", "Code"]
date = "2019-04-16T13:50:46+05:00"
menu = ""
tags = []
title = "What I learned creating this site"
+++

## Introduction

>"Use a static site generator," they said.<br>
"It'll be so quick!" they said.

Well, *they* were both right and wrong. Let me tell you about my experience creating this site.


#### Some Bullet Points
* Static Site Generator - Hugo
* Customizing a theme
* Hosting on Netlify

## Hugo
Hugo is a static site generator that relies on the Go html template engine to create lightweight, easy to get up and running websites. Commonly used for resume sites, portfolio sites, blogs, etc. You can actually get going with a premade theme blazingly fast and with minimal commands. Running `hugo server` from the terminal allows you to see your site on `localhost:1313` and automatically update when you make changes in the code.

But of course, I would not just take the premade theme at face value. I needed to customize it, add things, remove things, learn all the quirks and ins-and-outs of it. And thats when started to get a bit more tricky.

## Customizing a theme
Every theme is kind of like learning your own little micro-language almost. Most of the things I needed to customize were located in the `config.toml` file. But some weren't, and that's when you have to go digging around in your theme. My theme had subfolders under layouts called `_default` and `partials` where the HTML files were located. These files mostly look like normal HTML, with some of Go's [html/template](https://golang.org/pkg/html/template/) library's syntax in there:

{{< highlight html >}}
<div class='row'>
  {{ range .Site.Params.portfolio.gallery }}
</div>
{{< /highlight >}}

This reminds me a bit of `erb` files in Ruby on Rails applications, where you can write Ruby code inside of what I affectionately called the angry squid/happy squid, ie: `<%= code here =>`.

Once I got the hang of the templating syntax and the organization of my folders, it was really fun  customizing the rest of my site.

## Hosting on Netlify

In my experience, deploying your site is the most exciting and scary part of web development. It could either deploy without a hitch, or take you down an 8 hour rabbit hole...I've experienced both and it seems to be about a 50/50 coin toss. 🤷🏻‍

In my previous projects, I've deployed on Heroku with Rails projects and it worked fairly well. Hugo and Netlify seem to be somewhat in cahoots, since they have a convenient walkthrough guide in their docs. They also have several others for hosting on GitHub, Firebase, etc.

When I was first getting this site up, Netlify didn't like that I had customized my theme, which was living in a `submodule` in the repo. I ended up creating a copy of that theme into my own new custom theme, and getting rid of the submodule altogether. I also had an error in the Hugo version, so I had to make sure to specify that in the build environment variables.

---
And so in closing - Yes, Hugo is a fairly straightforward and quick way to get a static site up. Making a lot of customizations may take you down a few rabbit holes in the process. I had a good time learning and tinkering with it and will continue doing so as I make updates and improvements on this site!

Cheers!
