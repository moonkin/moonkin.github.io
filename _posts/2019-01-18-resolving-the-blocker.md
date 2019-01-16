---
layout:  post
title:   "Week 5: Resolving the blocker"
date:    2019-01-18
feature: 'assets/img/pascal-debrunner-754884-unsplash.jpg'
excerpt: "A few words about the subscription feature."
tag:
- Outreachy
- Debian
- Internship tasks
- Main integration task
comments: true
---
<center><font size="-1" color="lightgrey">Photo by Pascal Debrunner on Unsplash</font></center>

*Hi, I am Anastasia, an Outreachy intern working on the project ["Improve integration of Debian derivatives with Debian infrastructure and community"](https://wiki.debian.org/Outreachy/Round16/Projects/DerivativesIntegration). Here are my other posts that haven't appeared in the feed on time:*

* [Week 1: Applying for Outreachy](/applying-for-outreachy/)
* [Week 3: My first tasks](/my-first-tasks/)

This post is about my work on the subscription feature for Debian derivatives - first of the two main issues to be resolved within my internship. And this week's topic from the organizers is "Think About Your Audience", especially newcomers to the community and future Outreachy applicants. So I'll try to write about the feature keeping the most important details but taking into account that the readers might be unfamiliar with some terms and concepts.

## What problem I was trying to solve

As I wrote [here](/my-first-tasks/), around the middle of December the Debian derivatives census was
re-enabled. It means that the census scripts started running on a scheduled basis. Every midnight they
scanned through the derivatives' [wiki pages](https://wiki.debian.org/Derivatives/Census), retrieved
all the info needed, processed it and formed [files and directories](http://deriv.debian.net/) for
future use.

At each stage different kinds of errors could occur. Usually that means the maintainers should be
contacted so that they update wiki pages of their derivatives or fix something in their apt
repositories. Checking error logs, identifying new issues, notifying maintainers about them and keeping
in mind who has already been notified and who has not - all this always was a significant amount of work
which should have been eventually automated (at least partially).

## What exactly I needed to do

By design, the subscription system had nothing in common with the daily spam mailing. Notifications
should have only been sent when new issues appeared, which doesn't happen too often.

It was decided to create several small logs for each derivative and then merge them into one. The resulting log should have also had comments, like which issues are new and which ones have been fixed since the last log was sent.

So my task could be divided into three parts:

* create a way for folks to subscribe
* write a script joining small logs into separate log for each particular derivative
* write a script sending the log to subscribers (if it has to be sent)

The directory with the small logs was supposed to be kept until the next run to be compared with the new small logs. If some new issues appeared, the combined log would be sent to subscribers; otherwise it would simply be stored in the derivative's directory.

## Overcoming difficulties

I ran into first difficulties almost immediately after my changes were deployed. I forgot about the
parallel execution of `make`: in the project's crontab file we use the `make --jobs=3`, which means three parallel Make jobs are creating files and directories concurrently. So all can turn to chaos if you weren't extra careful with the makefiles.

Every time I needed to fix something, Paul had to run a cron job and create most of the files from zero. And for nearly two days we've pulled together, coordinating actions through IRC. At the first day's end the main problem seemed to be solved and I let myself rejoice... and then things went wrong. I was at my wits' end and felt extremely tired, so I went off to bed. The next day I found the solution seconds after waking up!

## Cool things

When finally all went without a hitch, it was a huge relief to me. And I am happy that some folks have already signed up for the errors, and hope they consider the feature useful.

Also I was truly pleased to know that Paul had first learned about makefiles' order-only prerequisites from my code! That was quite a surprise :)

## More details

If you are curious, in the [Projects](/projects/) section a more detailed report will appear soon.
