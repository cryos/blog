+++
categories = ["general"]
tags = ["development"]
images = ["images/github-activity-public.png"]
banner = "images/github-activity-public.png"
date = "2023-04-10T14:42:00-04:00"
title = "GitHub Activity and Single Sign-on"
menu = ""
description = "Short post about an interesting oddity with GitHub activity feeds interacting with single sign-on"

+++

My work has always involved some mixture of open source development and private repositories for one reason or another. There are also some fairly large portions of work away from GitHub, which is why I have always liked some of the aggregation services that can look at a wider view of open code. One big surprise to me was that GitHub cannot see all of my contributions even with the private contributions ticked. You can see the two activity views below one above the other where the only difference is whether I am logged in using my organization's sign sign-on.

![Activity on GitHub when signed in](/images/github-activity-public.png)

![Activity on GitHub when signed in twice or not at all](/images/github-activity-public-saml.png)

I led a lot of the work to move from some private GitLab instances to the GitHub enterprise offering. It was surprising to me to learn that even GitHub does not see through the single sign-on and that those commits are even more private. If you read their explanation they actually go in to the fact that you won't see it if you don't have an active single sign-on session. Even weirder is, as they state, if you log out (or open a private window) you will then see it again. Odd behavior, but I guess I see where the choice comes from as I cannot see those commits when logged in without a single sign-on session.

I am sure there were some very good reasons for what seems like a highly irregular behavior regarding private commits. When I started using GitHub none of these things were even possible, and I would guess some evolution happened as the additional layers of authentication were added. My private work is four factor protected by my GitHub credentials, that two factor, and my organizations credentials and two factor. Logging in on a new machine is a little much with all those logins!
