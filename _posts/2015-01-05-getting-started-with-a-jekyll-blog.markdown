---
layout: post
title: Getting Started With a Jekyll Blog
date: 2015-01-04 16:06:26
summary: How to build a fully automated static blog with Jekyll.
---

**NOTE: I am hosting on Github Pages currently. However, this setup can be very painlessly applied towards a self hosted site as well.**

**NOTE 2: This setup requires an always-on and always-connected Mac. If you do not have access to one, this might not work for you.**

### Why a static blog?

At this point, I have tried most of the "CMS"es; Wordpress, Ghost, Tumblr, Medium, you name it. Some of them are better than the others on different metrics but none offers a simple and intuitive experience. "Simple" and "intuitive" are both relative terms, so I will define them here. 

**Simple**: To me in this context, simple refers to something that doesn't involve repeated steps and using unoptimized tools. I am willing to accept (and enjoy understanding) the initial complexity for building a solution that is simpler in day-to-day use.

**Intuitive**: In context of writing, intuitive to me means a setup where the act of sharing (posting) is not very different from the act of writing itself. 

Wordpress, Tumblr and Medium fail at one or the other of these metrics. So, what is an ideal solution? A setup where there is no requirement for specialized or proprietary tools and where writing (which I do in Markdown files stored on Dropbox) itself is publishing. The setup I am describing here, using Jekyll, fits in well!

### Tools used

* [Jekyll](http://jekyllrb.com)
* [Github Pages](https://pages.github.com)
* [Sublime Text](http://www.sublimetext.com/3) or any other text editor with decent MD syntax highlighting
* [Editorial for iOS](http://omz-software.com/editorial/) or any other text editor with Dropbox sync support.
* [Dropbox](https://www.dropbox.com) or any other folder sync solution
* [Alfred](http://www.alfredapp.com) (optional)
* [Hazel](http://www.noodlesoft.com/hazel.php) or [`launchd`](http://launchd.info)
* [Automator](http://support.apple.com/en-us/HT2488) or shell scripts

### Getting started with Jekyll

Jekyll is a static site generator, that you can run on any machine with Ruby installed. I chose to host on [Github Pages](https://pages.github.com), which are built using Jekyll. Hence, all it takes is pushing your changes to a repository and Github generates and (near instantly) makes the new site live. As such, there is nary a need to setup Jekyll on your local machine or install any of the dependencies[^fn-1]. Now, to setup using Github Pages, here is a very simple and easy to follow tutorial on [Smashing Magazine](http://www.smashingmagazine.com/2014/08/01/build-blog-jekyll-github-pages/). Do not bother to customize anything at this point as you might need to overwrite everything when theming.

Once you have the blog created and published, follow on to automate and customize the setup.

### Themes

Jekyll has some nice themes. Granted, the collection is nowhere near as expansive as for, say, Wordpress, some good ones can be found on [Jekyll Themes](http://jekyllthemes.org), and they are free! This blog, as of this writing on 01/04/2015 uses [Pixyll](http://jekyllthemes.org/themes/pixyll/) by [John Otander](http://johnotander.com) with some modifications.

To install a theme, just overwrite the whole repo you created in the last step and modify `_config.yml` file[^fn-2] to fit your preferences[^fn-3]. Editing CSS can be a little unconventional if you do not know about with preprocessors like [SCSS](http://sass-lang.com). However, they are written in not too different a syntax relative to CSS and it shouldn't be much of an issue. Elements can be distributed over different files. So, just perform a Finder search for what you are looking for, for example `site-title`, and edit the files which show up. Page templates are set in small HTML files using the [Liquid](https://github.com/Shopify/liquid/wiki) teplate engine. Again, it's not too difficult to understand. For editing purposes, just inspect what you want to edit in inspector in your browser, find the `class` or `id` name, search in Finder and edit the files[^fn-4].

### Automated Post Templates

The beauty of Jekyll to me is in the Markdown files it uses for posts and their simple structure. The only requirements imposed are file-name and some [front matter](http://jekyllrb.com/docs/frontmatter/). The fact that one doesn't have to fiddle with tens of text-fields and pickers and buttons to post is just great! However, typing front-matter every time can be tedious. So, here are some tools to the rescue.

##### OS X
I use Alfred very heavily. So much so that my Spotlight Shortcut ⌘-Space is mapped to Alfred (with ⌥-Space activating Spotlight). It's logical to have it run this as well. Here is a very simple workflow, adapted from [Mr. Poodle](http://frederikvoigt.de/2014/07/08/Mr-Poole---An-Alfred-Workflow-for-Jekyll-Sites/) which does a lot more, like build site as well. For my use case, I only need the ability to create a new draft with the right file name and front matter, publish it and open other drafts and posts. So, here is the simplified version: [Jekyll Alfred Workflow](http://culturedpixel.com/uploads/Jekyll.alfredworkflow). Please be sure to change the variables to the right file paths in the workflow or it will not work!

##### iOS
I use [Editorial by Ole Zorn](http://omz-software.com/editorial/) for pretty much all text handling on iOS. It's support for [workflows](http://www.editorial-workflows.com) is incredible and very handy. In this case, I use an adapted version of @josiahwiebe's workflow. You can find it here in the Editorial Workflows Directory: [New Jekyll Post in Dropbox ](http://www.editorial-workflows.com/workflow/5797754072727552/auAEu7A0Rmg).

This workflow will create a new `.markdown` file in the specified directory (which you can set in the python script near the end of the workflow) with time stamp and title in the file name. It will also populate the front matter and you can then start writing!

##### Windows
Get outta here!

### Automatic Publishing

Automated publishing takes a bit of work to set up and requires that the host mac is running at all times to do your bidding. If you do not have such an always-on, always-connected machine, you can get one from [macminicolo.net](http://www.macminicolo.net/). 

**So, here is what happens:** Whenever a post/draft is updated, created, or deleted, a hazel rule is matched. That Hazel rule then runs an Automator Workflow. This workflow first commits and pushes the repository to your Github account and then sends you a confirmation message over iMessage.
**Here is how it appears to you:** You edit a post and you get a text (from yourselves) with the time stamp of the publish date. You can then visit your blog and see the live content. *Simple!*

##### Setup Posts Sync
This one is easy. Either you can keep the entire Jekyll directory in your Dropbox account or, like me, you can symlink the `_posts` and `_drafts` folders to Dropbox to sync them and noting else.

From [Dropbox Wiki](http://www.dropboxwiki.com/tips-and-tricks/sync-other-folders#Mac_OS_X):

    ln -s /path/to/folder/that/you/want/to/sync/ ~/Dropbox/folder/name

##### Workflow to Push To Github
You can download my Automator Workflows to push to Github from here → [Automator Workflows](http://culturedpixel.com/uploads/Github%20Push%20Workflows.zip)

I just keep these on a level above the Jekyll directory. They will be run by Hazel, as you willl see in the next step. Before moving on, open the workflows in Automator and set the required variables in the bash script as well as iMessage AppleScript. Also, setup Github command line configuration on your Mac to use your account, if you don't have it already configured. [help.github.com](https://help.github.com/articles/set-up-git/).

##### Hazel Rule to Watch for Updates
If you do not already have Hazel, you can download a trial from [Noodlesoft](http://www.noodlesoft.com/hazel.php). It's an incredibly handy tool to have! Also, why Hazel? Why not just use Automator's Folder Actions? That's because Folder Actions can only detect additions or removal of files in a folder and not updates to existing files' contents, which is a big part of blogging.

Once you have Hazel installed, add your `_posts_` and `_drafts` folders to it and then import the respective rules. In the rules, edit the bash script to point things to the right directories. Then also make sure to select the Automator Workflows for Hazel to run.

Here is how the Hazel rule functions: Whenever Hazel detects a change to the directory, it calls the script. The script then computes a hash of that directory('s tar archive) and matches it against the last computed hash (this is stored in the hash file. You should give these files a directory in a level above your Jekyll directory). If the hash matches, then the script aborts the rule and nothing happens, as the folder has not really changed and Hazel was stimulated for other reasons. However, if the hash is indeed different, the rule will report a match and continue to run the Automator Workflow[^fn-5]. 

### That's All Folks!
With this setup, now I edit or create posts on my iPhone, or on my other Macs, and instantly receive notification that it was published[^fn-6]. As a matter of fact, I can blog from any machine with a browser (access Dropbox and upload a text file), not unlike all the other blogging engines.

I think, finally, I have a blogging setup that is very simple and frictionless and independent of finicky iOS apps or overachieving  websites. I have long wanted something like this and now, [here](https://github.com/gravicle/gravicle.github.io) it is!

[^fn-1]: However, if you wish to do so, docs on [Jekyllrb.com](http://jekyllrb.com/docs/home/) are more than sufficient.
[^fn-2]: It's just a text file. Set it up to open with Sublime text and you should be good!
[^fn-3]: The setup can be little bit more involved if your theme has dependencies like [this one](https://mademistakes.com/articles/minimal-mistakes-jekyll-theme/#installation). It's still quite simple.
[^fn-4]: This is actually *the* way front-end development works.
[^fn-5]: While one can just use the `Date Last Modified` > `did change` rule to match instead of the shell script, in practice I found it quite buggy!
[^fn-6]: Albeit, the pushing of the repository is near-instant, Github Pages can still take a slight bit of time to actually generate the pages and then make the changed site live.