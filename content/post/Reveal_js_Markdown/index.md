---
authors:
- admin
categories: []
date: "2019-07-11"
draft: false
featured: true
gallery_item:
- album: gallery
  caption: AllisonHill
  image: AllisonHill.png
- album: gallery
  caption: shortcode
  image: shortcode.png


image:
  caption: ''
  focal_point: ""
  placement: 2
  preview_only: false
lastmod: "2019-04-17T00:00:00Z"
projects: []
subtitle: 'How to create and aesthetically modify Reveal.js slides using R Markdown and a bit of HTML/CSS)'
summary: How to create and aesthetically modify Reveal.js slides using R Markdown (and a bit of HTML/CSS).
tags:
- reveal.js
- rmarkdown
- tutorial
- Beginner
- Getting started
title: 'Creating Reveal.js slides with R Markdown'
---



# *Background Perspective*

Traditionally, I have created my slides using PowerPoint. However, I found it increasingly tedious to show code and deploy slides to course websites so I started exploring with Reveal.js. The benefit is you can include code and code-generated figures (e.g. graphs) in your slides and easily update them without having to re-do every individual slide.

Before starting this endeavor, I had *zero* experience coding in HTML and CSS, but I was proficient in [markdown](https://rmarkdown.rstudio.com/authoring_basics.html) and [R Markdown](https://rmarkdown.rstudio.com/). If you are not familiar with either, click the links for some important background information.

*Note* - if you are an artist (or very focused on small visual details), then you might want to reconsider using reveal.js. Unless you are a pro with HTML/CSS, detailed customization of slides is challenging and some Powerpoint features are simply not available. 

I won't get into linking with GitHub or Hugo-generated sites (perhaps in a later post). Rather, **this post will outline how to get started with Reveal.js and alter basic aesthetics (including the CSS file) of your slides**.

Also - this is a working document. I will add pictures and more links at a later date.

<br/><br/>



# Getting Started

** First -- Read [the R Markdown Tutorial](https://bookdown.org/yihui/rmarkdown/revealjs.html) on creating slides with Reveal.js. I will not go over in detail some of the topics they cover there so best to have that read and under your belt before moving on.

## 1) [Install the Reveal.js package for R](https://github.com/jonathan-g/revealjs_jg)


```
install.packages("revealjs", type = "source")
```

[The link above](https://github.com/jonathan-g/revealjs_jg) has great information on getting started. Please read it for more detail.

<br/><br/>

## 2) Create a new R Markdown document 

In RStudio, click:

```
File / New file / R Markdown / Document

```

The R Markdown file comes with pre-existing front matter in the document that looks like this:

```
---
title: "Untitled"
output: html_document
---

```

Modify it to specify a reveal.js output:

```
---
title: "Whatever your document title is"
author: your name
date: July 22, 2015
output: revealjs::revealjs_presentation
---

```

<br/><br/>


## 3) Create a basic slide show

```
# How to make a PB&J sandwich


## Bread

I prefer whole wheat bread


## Peanut butter

Creamy pb for sure 



## Jelly

Nothing compares to my grandma's home made peach jam

```

<small> Level 1 headers are denoted by one pound sign (#) and level two headers are denoted by two (##). 
You cannot have words on a slide under a level 1 header because it's meant to be a title slide. Vincent Bauer [created this workaround](https://stanford.edu/~vbauer/teaching/revealjs.html) though if you really want words on that slide. </small>


<br/><br/>



## 4) Reveal.js aesthetics using R Markdown

#### A) Using a pre-defined theme

`Reveal.js` comes with pre-defined [themes](https://bookdown.org/yihui/rmarkdown/appearance-and-style-1.html) that you can quickly use to get started. Just specify which theme you want in your YAML metadata (e.g. the front matter of your R Markdown document) like this:

```
output:
  revealjs::revealjs_presentation:
    theme: sky
    
```

**SPACING MATTERS HERE** so preserve the indentation structure seen above. Also, don't forget the `:` after presentation. 


<br/><br/>

#### B) Adding aesthetics within your .rmd file

If you're using one of the pre-defined themes and just want a few slide-specific modifications, here are some options:

* To left-align the body text of a slide (so not the title that is indicated by `##`):

```
<section style="text-align: left;">
Left-align: This works to align text left on this slide only.
</section>

```

* To have a slide fade in, add the transition in curly brackets beside the title of your slide:

```
## Fade in, Slide out {data-transition="slide-in fade-out"}

```


* Adding an image as the background with `data-background` beside the title

```

## Level Two Title {data-background="./images/Sandwich.png"}

```
<small> You will need to navigate to the directory where your pictures are held. I recommend putting a folder called `images` in the same directory as your .rmd file and adding images within that folder. If you do that, use the above code and just change the name of your image. The `.` indicates the directory I'm currently in and the resulting `/` navigate to the correct location of the image. </small>


* Changing multiple aspects of the slide (background color, text color, and transition)

```
## Slide Title {data-transition="fade-in" data-background="#228B22" style="color:black;"}

```

<small> This slide will transition to the next slide by fading. The background of this slide is green (as indicated by the HEX code `#228B22` and the text color of the title is black. </small>

* Change the color of the body text (not the title)

```
::: {style="color: blue;"}

> * Yes, and it fades in 
> * and the bullets are incrimental
> * becuase I used the carrot sumbol
> * and the color is blue
> * because I specified it and used ::: symbols

:::

```

<small> Remove the `>` if you don't want the bullets to appear one by one. </small>


* Specify the color of one line of text

```
<div style="color:#2a52be;margin:20px;margin-top:50px;" >
This text is blue and has a margin around it.
</div>

```

* Altering text color along with other aesthetics (e.g. bold, italics, size, etc) - (have to use a bit of HTML)

```
<div style="color:darkred;margin:20px;margin-top:50px;" >
Here is some text that is in red, 
<b>in between the b symbols mean put this text in bold</b> 
but this text is not bold
</div>


<p style="margin:10px;font-size:80%;">--- <i>This is smaller italisized text</i>, p. 25.</p>


```


* Add a link in your slide

```
[Link](www.example.com)

```

* To insert an image in a slide, put this in the text body

```
<img src="/images/tmp_warning.png"  height="100" width="200">

```


* Add speaker notes to your slide! 

  * This is one of my favorites. To activate speaker mode, press "S" once you've launched your presentation. This will bring up a separate browser window that you can drag to the speaker computer screen. 
  
  * In order to use speaker notes, you have to specify so in your YAML metadata at the top of your R Markdown document

```
---
title: "Title"
date: "July 12, 2019"
output: 
  revealjs::revealjs_presentation:
    reveal_plugins: ["notes"]

---
    
```

<small> **THE SPACING ABOVE IS WRONG**. I don't know what's up with it, but I'll fix it later. Use the example of how to space the YAML metadata from 4.a above. </small>

Then within your slide, designate text that is speaker notes by doing the following:
  
```
<div class="notes">
Here are secret notes that will not appear on the slide. They will appear when speaker view is activated!
</div>

```


* To have a slide with no header start the next slide with `---` instead of `##`. You can still modify the color, etc of the slide by doing something like this:

```
--- {background: "#007777"}.
This is a colored slide with no title

```


<br/><br/>



#### C) Modifying the CSS 

If the above doesn't provide enough personalization for your slides, then you can create a .CSS file. I  __*highly*__  recommend just modifying one from an [existing theme](https://github.com/hakimel/reveal.js/blob/master/css/theme/template/theme.scss). Here are a few tips for doing that:

Copy an existing CSS file into the *same* directory as your .rmd file. 

Then, modify whatever you want. This will require that you know a bit of CSS and HTML. 

Here is an example of what the first part of your css might look like (this is mine):


```

@import url('https://fonts.googleapis.com/css?family=Catamaran&display=swap');
@import url('https://fonts.googleapis.com/css?family=Libre+Baskerville&display=swap');
@import url(https://fonts.googleapis.com/css?family=Anonymous+Pro:400,700,400italic,700italic);
/**
 * 
 */
html * {
  color-profile: sRGB;
  rendering-intent: auto; }

/*********************************************
 * GLOBAL STYLES
 *********************************************/
body {
  background: #e6e8eb;
  background-color: #e6e8eb; }

.reveal {
  font-family: 'Catamaran', sans-serif;
  font-size: 47px;
  font-weight: normal;
  color: #0f0f0f; }

::selection {
  color: #fff;
  background: #05dff7;
  text-shadow: none; }

::-moz-selection {
  color: #fff;
  background: #05dff7;
  text-shadow: none; }

.reveal .slides section,
.reveal .slides section > section {
  line-height: 1.3;
  font-weight: inherit; }
  
```

Let's break this down a bit:

* The `@import url` text is specifying what fonts you want to use within your css. Here, I've picked out three, one font for headings, one font for the body text of my slides, and one font for code that appears on my slides (I define which font is for which aspect of the slide later in the CSS). To change the font, go to [Google Fonts]( https://fonts.google.com/) and get the appropriate  `@import` code for your font of choice.


* Specify a global background color:
```

body {
  background: #e6e8eb;
  background-color: #e6e8eb; }
  
```  
<small> This can be overwritten for a specific slide (see example above in section 4B) </small>

and font details:


```

.reveal {
  font-family: 'Catamaran', sans-serif;
  font-size: 47px;
  font-weight: normal;
  color: #0f0f0f; }
  
```

[Here is a fun way](https://htmlcolors.com/color-picker) to find the Hex codes for whatever colors you want and [this HTML Cheatsheet](https://github.com/hakimel/reveal.js/blob/master/css/theme/README.md) also is fun with letting you see how colors vary depending on how you use them. It's also helpful for explaining HTML.



* The `Selection` parameter specifies what color will appear when someone highlights a portion of text with their mouse. For example, if you highlight this sentence with your mouse, the background will be blue. [Here is a great explanation of all the options that exist](https://css-tricks.com/almanac/selectors/s/selection/). 


* To understand what all of the tags are in a CSS file (i.e. all those words/acronyms like "ul"), [click here](https://www.w3schools.com/tags); and to understand all of the parameter options (e.g. font-size = 150%), [click here](https://www.w3schools.com/cssref/).

<small> *Honestly, that may be my new favorite website of all time. It's so helpful at explaining css and HTML tags and lets you play around with different settings to see the output. </small>


* One thing I will note is that if you're looking at [my CSS]() and [my slide examples](), you'll notice that the text is centered on the slide, but I don't specify in the CSS to center the text. As far as I know, centering is the default. 

If you want to [specify everything as left-justified](https://github.com/hakimel/reveal.js/issues/1897), put this in your css under the global options section:

```
.reveal .slides section > section {
     text-align: left;  
     line-height: 1.3;
     font-weight: inherit; }

```

* [You can also alter the css so that different types of media have different settings](https://www.w3schools.com/css/css3_mediaqueries.asp). This may be useful if you have a colored background in your html slides but want to print slides that have a white background. 


<br></br>

#### D) Saving your slides to PDF. 

Honestly, I'm still trying to find a good way to do this because the automated way has been a bit wonky for me (almost certainly user error). 

My current route is to [change the url](https://www.r-bloggers.com/presentations-in-rmarkdown/ ) and go from there. 




**[You can find my CSS here]()**. [Jonathan Gilligan]() created a [CSS]() by modifying the [solarized theme](). I then took [his CSS] and modified it to make it [my own]() (I liked a lot of the [classes](https://bookdown.org/yihui/rmarkdown/custom-css-1.html) he created so I saw no point in reinventing the wheel!

To copy it and modify my css (or anyone's) and make it your own, click the 'raw' button in GitHub, highlight and copy the document, and paste it into a text editer (e.g. Notepad on Windows). Save it as `.css`. **[There is a much more refined way of doing] this(https://github.com/hakimel/reveal.js/blob/master/css/theme/README.md) using Gruntfile** I figured it was easy enough to just modify someone else's already wonderfully executed css file.


<br/><br/>


[Reveal.js documentation on creating your own css](https://github.com/hakimel/reveal.js/blob/master/css/theme/README.md)



{{< gallery >}}



