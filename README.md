
# Health Emergency Analytics Workshop

This github repository is used to develop the website of the Health Emergency
Analytics Workshop co-organised by RECON, the UK Public Health Rapid Support
Team, the London School of Hygiene and Tropical Medicine, and the Wellcome
Trust.



## How to contribute

Workflow for contributing to the website: 

1. fork the project
2. clone it on your computer
3. make and check changes
4. make a pull request (PR) to propose changes
5. amend until PR is successful

In the following I detail the non-trivial parts (I assume fluent use of git and
github).



### Making changes

#### Checking the website locally

You need to install [hugo](https://gohugo.io/getting-started/installing/), and then run:

```
hugo server --disableFastRender -D
```

and open up the local URL.


#### Structure of the website

Most changes are straightforward, and either rely on modifying existing fields
in `yaml` config files, or editing / adding `markdown` files, which `hugo` will
turn into pretty-looking html.

Files to be aware of include:

* `config.toml`: title of the page (used for meta) and base URL
* `content/post/`: folder storing articles ("posts") as `markdown` files (see
  example below)
* `data/en/intro.yaml`: title page
* `data/en/contactinfo.yaml`: elements used for the 'contact' page at the bottom
  of the website
* `layouts/partials/nav.html`: to add new items to the navigation bar
* `static/images/`: folder to store images


#### Editing posts

Exmple of `content/post/aims.md`:

```
+++
title = 'Our aims'
slug = 'aims'
#image = 'images/pic03.jpg'
description = 'Aims of the meeting'
disableComments = true
date = '2019-01-28'
+++

This event aims at ...
```

The first part between `+++` is the header. The image can be commented out if
needed (the default image is currently a brown rectangle stored in
`static/images`). Excellent free, high-resolution images can be found at
[Pexels](https://www.pexels.com/). Note that the **date** will not be shown, but
is used to sort out posts in the main home page, most recent first.


Posts accept standard `markdown` and `html`.



#### Adding new posts

Every documented topic is technically stored as a 'post', as the website
template is originally a blog. I have disabled the display of dates, but the
home page will list them from the most recent to the oldest.

To add new post, copy and existing `md` in `content/post/`, rename it, and
change its content as you see fit. You will need to add a ligne in
`layouts/partials/` if you want to add a link to this post in the nav bar. See
these lignes:

```{html}
<li class="active"><a href='{{ "/" | relLangURL }}'>Home</a></li>
<li class="active"><a href='/post/aims'>Aims</a></li>
<li class="active"><a href='/post/practical_info'>Practical info</a></li>
<li class="active"><a href='/post/schedule'>Schedule</a></li>
<li class="active"><a href='/post/sponsors'>Sponsors</a></li>
```
