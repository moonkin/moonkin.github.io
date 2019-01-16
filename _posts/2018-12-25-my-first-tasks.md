---
layout: post
title: "Week 3: My first tasks"
date: 2018-12-25
feature: 'assets/img/raphael-koh-259721-unsplash.jpg'
excerpt: "The work I've done during the first three weeks of the internship and my experience of getting stuck and asking for help."
tag:
- Outreachy
- Debian
- Internship tasks
comments: true
---
<center><font size="-1" color="lightgrey">Photo by Raphael Koh on Unsplash</font></center>

Hi! It has now been three weeks since my internship in Debian started. In my [first post](/applying-for-outreachy/) I said a few words about the project I am working on, but I'd like to list the key points again.

## Key points

The central part of the project is the [census](https://wiki.debian.org/Derivatives/Census) collecting detailed information about Debian derivatives (software distributions based on Debian). Derivatives may be quite different depending on which Debian release they are based on and how they modify or extend it. Each derivative has its own wiki page where its maintainer is expected to keep the most up-to-date information, like links to the official website, wiki, blogs, forums, git (or other VCS) repositories and mirrors, as well as contact information and apt sources.list snippets.

The [census scripts](https://salsa.debian.org/deriv-team/census/tree/master/bin) take information from the wiki pages and process it for integration into various parts of the Debian infrastructure. For example, they find a link to the derivative's blog, download its web pages, use automatic feed discovery algorithms to find a link to the blog's Atom/RSS feed and then produce a configuration snippet to be added to the [aggregated one](https://salsa.debian.org/planet-team/config/blob/master/config/config.ini.deriv) in the Planet Debian repository. Once it is added, the post from the blog will appear in the [Planet Debian Derivatives](https://planet.debian.org/deriv/) feed.

Some of the derivatives in the census are marked as inactive as they are no longer maintained for some reasons. Their information is still present in the wiki but is not processed by the census scripts, so it is mostly preservation of history. And if you are wondering why some distro is inactive, on the wiki page there is often a link to a [discussion with its maintainer](https://lists.debian.org/debian-derivatives) or to some other source where the reason is explained.

Directories and files produced by the census scripts are listed [here](http://deriv.debian.net/). If the scripts fail to download or process some data or some other issue occurs, there often are [mail templates](https://wiki.debian.org/Derivatives/CensusQA) to be sent to the maintainers. For now there is no option to send notifications automatically, but it will appear in the nearest future as it is the first of the two [blockers (main integration tasks)](https://wiki.debian.org/Outreachy/Round16/Projects/DerivativesIntegration). I am already working on the subscription system and hope to finish it by the New Year :)

## My work

During the last three weeks I have been working on several small tasks:
* some that helped to re-enable the census (make its scripts produce [data](http://deriv.debian.net/) daily):
  * implementing an [option](https://salsa.debian.org/deriv-team/census/commit/2cee3414d48fda292f33864999550264537f4887) to disable some scripts
  * adding my email to the crontab files to receive the output of the scripts
* some connected to Planet Debian Derivatives:
  * [updating](https://salsa.debian.org/planet-team/config/commit/9c4c2a873d3a40721624bc8c2e987576ca4f50bd) logos and feeds of some derivatives
  * [creating](https://salsa.debian.org/deriv-team/census/commit/359dc268a5d9ebc83bf7647aa0d4094738098f1e) a tarball of logos on the server's side to be downloaded by the [review script](https://salsa.debian.org/deriv-team/census/blob/master/bin/review-planet-config-heads)
* preparations for the future work on the subscription system:
  * synchronizing the census output produced by three parallel jobs and thus having errors listed quite randomly
  * [removing](https://salsa.debian.org/deriv-team/census/commit/09110bb3b203f50101218a857e3bd096981ca620) some errors from the output

## Everybody struggles

Every two weeks interns receive a mail from Outreachy organizers with guidelines and goals for the next couple of weeks. There also are some topics that we are suggested to talk about in our blogs to help future applicants and interns. This week's topic is "Everybody struggles", about getting stuck and asking for help. (All my future posts will probably have the how-I-got-stuck section too, because it happens all the time!)

For me getting stuck is as much a part of the learning process as reading, making notes, trying new tools and approaches, searching for the code samples and so on. I only feel foolish when I realize I had misunderstood something at the very start and was moving in the wrong direction. But I try to remind myself that even then it is not a waste of time, as I learn something anyway.

**For future applicants and interns** You can't escape being stuck while working on a complex project. And after focusing intensively on some task and still not moving any closer to the solution you will probably feel frustrated. But all this doesn't just drain your energy, it also shapes your understanding of the task and helps you find useful tools for your future work. So don't regret the time spent! And if you feel confused and question your chosen approach, mentors are always here to guide you.
{: .notice}

In my post about the application process I wrote about some difficulties I had faced while making my first contributions. At that time I was hesitant to ask for help and scared of making mistakes. Also being a non-native English speaker I felt more secure when contacting the project's mentors by email, so it often took more time to get help than if I used instant messaging<sup>1</sup>. Later I slowly began talking in IRC and even got used to discussing my code publicly. There was no pressure to do so, only encouragement, and I just decided to try one day and all went good. I started receiving help almost immediately and although I continue making mistakes from time to time, I am not as upset about them as in the beginning.

**For future applicants and interns** After all you aren't supposed to know everything! You are here to learn. Good luck to you all!
{: .notice}

<sup>1</sup> *BTW, I really struggled to find an IRC client for my Android phone until I came across [Riot Matrix client](https://matrix.org/docs/projects/client/riot-android.html). It is super cool. It integrates several IRC networks like Freenode and OFTC and can work as an IRC bouncer (you remain connected and don't lose message history). There also are [web](https://matrix.org/docs/projects/client/riot.html) and [desktop](https://riot.im/desktop.html) versions. Hope it will be of use to someone.*
