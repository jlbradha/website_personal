---
authors:
- admin
categories: []
date: "2019-07-11"
draft: false
featured: true
gallery_item:
- album: gallery
  caption: shortcode
  image: shortcode.png
- album: gallery
  caption: Forest
  image: theme-forest.png

image:
  caption: ''
  focal_point: ""
  placement: 2
  preview_only: false
lastmod: "2019-04-17T00:00:00Z"
projects: []
subtitle: 'Tips for beginners creating a website with Blogdown/Hugo :thumbsup:'
summary: Tips for beginners on creating a website with Blogdown and Hugo packages.
tags:
- Academic
- Hugo
- Blogdown
- Beginner
- Getting started
title: 'Creating a website with Blogdown/Hugo'
---



# **This post is for those interested in creating a _free_ website using Hugo and Blogdown. Read on for tips to easily make your own website.** 

# *A bit of background...*
I'm not an expert in R, html, or [insert any other language], but I *am* really good at Googling things... so that's where I started when creating my website. There are a lot of really helpful resources out there (see [here](https://bookdown.org/yihui/blogdown/get-started.html), and [here](https://alison.rbind.io/post/2017-06-12-up-and-running-with-blogdown/)) for getting started with website creation using Blogdown and Hugo. However, despite these amazing tutorials, I still had to deploy expert Googling skills to work through a few snags. This post is not meant to replicate the wonderful tutorials others have already created. Rather, it's meant to just slightly expand some explanations for those of us who need a bit more detail. 

*Disclaimer*: The words written here are just reflective of my own experience. Your experience may be quite different, but my hope was to try and bring to light a few of the hurdles I faced and the work arounds I found. I used [GitHub](www.github.com) and deployed with [Netlify](Netlify.com) so that's what the below 'tips' reflect. It's also a working document so pictures and a more aesthetically pleasing layout to come soon. No judgement.

* I will create another post on how I made my course websites. Similar process (Hugo/Blogdown) but a different theme and thus a slightly different approach.


# Getting Started

Before starting, I *highly* recommend reading chapters 1 - 3 of the amazing book [Creating Websites with R Markdown](https://bookdown.org/yihui/blogdown/content.html#shortcode) by [Yihui Xie] (https://yihui.name/), [Amber Thomas](https://amber.rbind.io/), and [Alison Presmanes Hill](https://alison.rbind.io/). It's really well written and it provides some essential background information that will make your life much easier (and save you some Googling time). 


## A few things I got stuck on with Installation

I already had R and RStudio working and had been using them for years, but I wanted/needed to install Git for other things I was working on. This turned out to be a problem for me.


#### Installing Git for Windows in RStudio
* ok -- this one really threw me for a loop. I installed Git and suddenly RStudio crashed and wouldn't do anything. I panicked (like one does) and for an entire week I tried absolutely everything...even the dreaded uninstall and re-install of both R and RStudio. **Nothing Worked**. 

Finally, I uninstalled git and magically RStudio worked once more. Problem? -- I actually need Git so [here is the workaround](https://stackoverflow.com/questions/39688656/r-studio-will-not-start-while-git-for-windows-is-installed):
  * You need to clear your local session state (which doesn't happen by deleting and reinstalling!). To do this, go to your local RStudio folder. For me this was at:

```
C:\Users\username\AppData\Local\RStudio-Desktop

```
<sub>*(where 'username' is your individual username)*</su> 

  * Change the name of that folder and then restart RStudio to get it to generate a new folder with a new address to Git. 
  * Then delete the folder you renamed and voila! RStudio and Git should love each other once more. Also, this is small potatoes, but FYI - this does delete whatever preferences/Global options one had set up in RStudio.

  
  
## Done with installation? Follow Alison's tutorial!  

Next, start with [Alison's](https://alison.rbind.io/) very well-written [tutorial: "Up & Running with Blogdown"](https://alison.rbind.io/post/2017-06-12-up-and-running-with-blogdown/) on creating a website.



**Additional helpful info as you work through Alison's tutorial:**

<br/><br/>

### Cloning your Github Repo
* After you create your Github repo (aka after you complete numbers 1-3 on Alison's website), you can clone it via RStudio instead of with terminal (so this is an alternative way to #4 on her tutorial). Go into RStudio and do the following:

``` 
Project --> Version Control --> Git --> *enter your repository URL*
```

<sub> *Go to your Github repository and click the "clone or download" button to copy the URL </sub>


Continue with #6 on Alison's [tutorial](https://alison.rbind.io/post/2017-06-12-up-and-running-with-blogdown/) on creating a website.

<br/><br/>

### Picking and personalizing your theme


* As is recommended in the [Blogdown book](https://bookdown.org/yihui/blogdown/other-themes.html) and in [Alison's tutorial](https://alison.rbind.io/post/2017-06-12-up-and-running-with-blogdown/), I used the Hugo Academic theme. **Important to note** is that personalizing your website varies depending on the theme so read the documentation!

 * For example, personalizing the [Academic theme](https://github.com/gcushen/hugo-academic) is no longer done with the config.toml file. It's now done in the menus.toml. Details such as this can be found in the [Hugo-Academic Documentation](https://sourcethemes.com/academic/docs/).
 
 * Another example of a theme is Jonathan Gilligan's Hugo-Syllabus template ([Github code](https://github.com/jonathan-g/hugo-syllabus) and [Example](https://ees3310.jgilligan.org/)), and configuration of this template is done in the config.toml file. 
 
* When you create the menu buttons on the front of the website (either through the config.toml or the menus.toml or whatever file it's on), you will then create a markdown (.md) (*not* R Markdown) file in the `content` directory to populate that button (e.g. have words, etc appear on a page when that button is selected). See the section below '**Creating a new post**' for how to do that.

* *Note* Your newly created file name must match the menu name that you chose in your configuration file (e.g. config.toml or menus.toml)

**Bottom Line**: 

1. Read the documentation for the theme

2. Download the example (if available) for the theme to see how things work

3. Look on Github at the repositories and configuration files for people who have used that theme 


<br/><br/>
 

### Creating a new post
* If you want to create a new new post (and by 'new post', I mean any new markdown or R Markdown document), you go into the `Addins` menu and select `new post`.
* To specify where that post will go (i.e. into what folder), specify that in the `subdirectory` section. For example, you could type this into the `subdirectory` section of the new post box to put your new post in the "Getting-started" folder:

``` content/post/Getting-started
```

<sub> yes... I will take a screen shot at some point to make this easier</sub>

If you forget to specify the directory, no problem. Just save it wherever and then move it manually (through your finder folder) or use the `Files` tab in RStudio (check the box --> `more` and then `move to`)


Continue on with [Alison's tutorial](https://alison.rbind.io/post/2017-06-12-up-and-running-with-blogdown/) until you get to # 7 "Deploying with Netlify".

<br/><br/>

### Deploying with Netlify
So... Netlify will only be able to deploy your site if the version of hugo you're running matches with what they are using to deploy. Since Alison's blog post, the way to do this is a bit different, but still very easy. Here's how to do it:

1. Push all the changes you've made to Github
I had a few problems with RStudio crashing when I tried to stage and push things to github so [here is a workaround](https://community.rstudio.com/t/blogdown-unable-to-stage-and-commit/6621/4). In the termial window, type the following: 

 * `git commit -A`    
 
 * ` git commit -m` "*enter your commit message here*"
 
 * `git push origin master`


To push things individually, you can check the box under `staged` in the Git window of RStudio and commit that way.

 
Then go to github and make sure it's all there! 

  * **Note** If you can't get Git to commit, it means you need to listen to that red warning you received `To stop the server, run servr::daemon_stop(1) or restart your R session` when you inilized `serve_site`.  
  * If neither of those options work, go into your `.git` folder (in your repository folder on your personal computer) and delete the `index` file.


2. Go to [Netlify](https://www.netlify.com/) and log in with your github account

3. Click `New site from Git` and choose your Git provider (mine is GitHub)

4. Select the repository of choice and click `deploy site`

5. If you get an error, it's probably because of your Hugo version. 

* First, [figure out what version of Hugo you have] (https://maraaverick.rbind.io/2017/10/updating-blogdown-hugo-version-netlify/)

* Then, read [this workaround](https://maraaverick.rbind.io/2017/10/updating-blogdown-hugo-version-netlify/)
 * *Important to note* is that in order to edit variables in Netlify now, things are a bit different than when [Mara](https://maraaverick.rbind.io/) wrote that tutorial. Now, within Netlify, go to:
 
 ```
 Build and Deploy --> Environment --> Edit variables
 ```
 
<br/><br/>


### Using a custom domain name

Netlify automatically gives you a webite name (mine was something like zealous-aardvark). You can change this name to whatever you want (e.g. jenniferbradham.netlify.com). However if you want to use a custom domain name (e.g. jenniferbradham.org), then you have a few more steps to do. I purchased my domain name through [Google Domains](https://domains.google/#/), so that's what I'll be referencing in the steps below.

[Here is the Netlify manual on how to add a custom domain](https://www.netlify.com/docs/custom-domains/). For simplicity's sake, I'll outline the relevant steps below, but the tutorial provides a lot more information.

1. Deploy your site with Netlify (see above)

2. Log in to [Google Domains](https://domains.google/#/), and select the name of your domain (if you just have one domain, then there is only one option). 

3. In the left navigation panel, click `DNS`

4. Scroll down to `Custom resource records`. Here you will create two entries.

```
Name      Type        TTL     Data
@         A           1H      104.198.14.52

```

and the second entry is:

```
Name      Type        TTL     Data
www       CNAME       1H      yournetlifysitename.netlify.com

```

This is all in the [Netlify custom-domains manual](https://www.netlify.com/docs/custom-domains/#manual), under the heaing "Manual DNS Configuratiion for Root and WWW Custom Domains". 

5. Go back to Netlify, select the `Domain management tab` then click the link next your custom domain. The link will say something like "verify with Netlify". Click that link and follow the instructions. Netlify will then instruct you to enter the custom name servers. 

 * To do that go back to your Goolge Domains page and look under the `Name servers` selection (again, under the DNS tab).

 * Select `Use custom name server` and enter each of the numbers provided by Netlify as a separate entry. 



<br/><br/>


### Shortcodes

While looking at other people's configuration files on GitHub, you may come across something that looks like this:


{{< gallery >}}



That is referencing a Hugo shortcode. [Here](https://gohugo.io/content-management/shortcodes/) is a great tutorial on using shortcodes and [here](https://zealous-sammet-9b702c.netlify.com/post/tips_websitecreation/) is one on writing your own shortcodes.

* One thing to note is that shortcodes are written in html. You can't create an html document with the `New Post` function in Blogdown. Instead just use a text editor (e.g. notepad on Windows) and save it as html in the `shortcodes` folder that you will create within the `layouts` folder. Below the `File name` bar, make sure you change `Save as type` from `*.txt` to `All Files (*.*)` so your file doesn't have a  `.txt` ending. 










<br/><br/>


### Additional helpful links
<sub> *I'm basically using this section so I can easily get back to links I often need* </sub>

* Here is a helpful link on [getting started with Hugo in general](https://gohugo.io/getting-started/)

* [Updating you version of Hugo for blogdown on Netlify](https://maraaverick.rbind.io/2017/10/updating-blogdown-hugo-version-netlify/)
  
* [Markdown Cheatsheets](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#lists)

* [Git ignores directories with no contents](https://stackoverflow.com/questions/3030230/does-git-ignore-empty-folders) so don't panic if it shows up gray in your git repository

* [One more tutorial that might be helpful](https://notes.peter-baumgartner.net/slide/)

* [Inserting an image into your post](https://discourse.gohugo.io/t/solved-how-to-insert-image-in-my-post/1473)

* [My layouts folder disappeared](https://stackoverflow.com/questions/51253614/home-layout-missing-in-layouts-folder-but-works)

* [Relative links](https://github.blog/2013-01-31-relative-links-in-markup-files/)

* [Markdown extended syntax](https://www.markdownguide.org/extended-syntax/)

* [Changing icons on your webpage](https://material.io/tools/icons/?icon=help&style=baseline)



