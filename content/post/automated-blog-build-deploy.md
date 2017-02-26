+++
banner = ""
menu = ""
description = "An overview of some of the work I did to automate the build and deployment of my Hugo-based blog to Firebase using Travis (whenever commits are pushed to the repository)"
date = "2017-02-26T10:52:30-05:00"
title = "Automated Blog Build and Deploy"
categories = ["general"]
tags = ["hugo", "automation"]
images = []

+++

One of the bigger weaknesses of static site generation is that the build and deploy process requires whatever machine you blog on has all of the pieces needed installed (pretty simple with hugo as you can download a static binary), and that when deploying you effectively deploy the entire site for any update. This means that making posts low bandwidth locations would be impractical, and so it has led to me posting less than I might have.
<!--more-->

I had been meaning to look into using some of the continuous integration (CI) services with Firebase to automate the build and deployment. Yesterday and this morning I finally found a few moments to look into this, and make the whole process simpler in the future. We use [Travis][travis] with [GitHub][github] for a number of projects, it is free for open source projects, and offers a flexible environment. I moved to [Firebase hosting][firebase-hosting] pretty early as I liked the free, valid SSL support, distributed using CDN, and integrated with a simple command-line tool for deployment.

The final piece of the puzzle was to create a .travis.yml file that is run when pushing to my GitHub [blog repository][github-blog]. I found an issue with Hugo master, and so rewrote the .travis.yml file to use the last release, and added a CI key to Travis to enable deployment without revealing the key to the world. After quite a few iterations it looks like it works, and if this commit leads to the creation of a new post I will declare success.

This means I can easily run the local hugo server when authoring new content, preview it, and once ready commit and push to see it deployed to the live blog. The repository then contains a record of posts, changes made, and the raw content. The Firebase hosted site uses a CDN coupled with SSL using the latest [HTTP/2 protocol][http2]. Right now I want to check it all works, you can inspect my blog repository to see how the pieces fit together (the one less obvious part is where the private environment variable comes from, and that is configured in the Travis settings for the repository).

[travis]: https://travis-ci.com/
[github]: https://github.com/
[firebase-hosting]: https://firebase.google.com/docs/hosting/
[github-blog]: https://github.com/cryos/blog
[http2]: https://http2.github.io/