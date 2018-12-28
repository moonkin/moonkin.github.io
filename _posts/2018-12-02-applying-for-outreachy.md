---
layout: post
title: "Applying for Outreachy"
date: 2018-12-02
feature: 'assets/img/lemur-357293-unsplash.jpg'
excerpt: "How I became an Outreachy intern in Debian: details of the application process."
tag:
- Outreachy
- Debian
- Application Process
comments: true
---
<center><font size="-1" color="lightgrey">Photo by LEMUR on Unsplash</font></center>

## Hi! :)

I am Anastasia, an Outreachy participant, and in this blog I'll be writing about
my work on the project ["Improve integration of Debian derivatives with Debian infrastructure and community"](https://wiki.debian.org/Outreachy/Round16/Projects/DerivativesIntegration).

Last year I received my undergraduate degree in Computer Science, but I have neither
worked as a programmer, nor contributed to Free and Open-Source Software ever before.
Thanks to Outreachy I started exploring the FOSS world and learned lots of new
things already during the application process.

I first heard about Outreachy in September, just a few days before the applications
opened, so I had to make up my mind rather quickly. Coincidentally, I've already
planned quitting my non-tech job until winter and the prospect of searching for a tech
one without practically no real-world experience worried me a lot. A paid, remote and
full-time internship looked exactly what I needed.

Trying to decide I've read some former interns' blogs and all of them said that even if you
are not accepted as an intern, participation in the application process itself can be extremely
fruitful. And now I can say that it's true!

## Application process

At first I answered some questions about my background in the [initial application](https://www.outreachy.org/apply/eligibility/).
The next step was picking a project from the list.

**For future applicants:** All projects have detailed descriptions,
lists of required skills, mentors' contact info and mentorship styles.
{: .notice}

As I had just completed the [Python specialization](https://www.coursera.org/specializations/python)
from the University of Michigan and was really determined to learn Python further, I looked through
the projects related to Python programming and then narrowed the list down to a few ones.

I ended up choosing Debian project as it seemed interesting and required some knowledge of shell
scripting which I wanted to improve as well as Python. Also there was Git marked with a `1` - it means
that you can be a complete beginner and mentors are ready to teach you. I must say that my Git
skills were very limited. I finished an online course and understood how Git works in
theory, but I haven't had enough practice because I've only tried local repositories. Also I have
never even seen Makefiles and was unfamiliar with a lot of Debian-specific stuff, but thought it
would be great to get to know some.

So in the following weeks I had to ask one of the project's mentors, Paul Wise, several really
newbie questions. His replies were friendly and patient, he often recommended me relevant commands
and explained me things when I got stuck (sometimes repeatedly). Thus by the end of October I gained
more understading and confidence and tried lots of cool things. Thank you, pabs!

## My first task

**For future applicants:** Your first contribution isn't supposed to be complex. Just pick something small from the list of application tasks and contact your project's mentors to introduce yourself and ask for any details!
{: .notice}

My first task was a social one and involved no coding. I needed to send an invitation to Debian derivative
not yet present in the [census](https://wiki.debian.org/Derivatives/Census). I used the premade invitation
template, picked two derivatives from the list provided by Paul and send invitations to their maintainers.
Although the task looks simple, it had social importance and also it was important for me as
I've learned how mailing lists work :)

## Later contributions

During the [contribution period](https://www.outreachy.org/apply/make-contributions/) I worked
on several other social, wiki maintenance and programming tasks. All these tasks are connected.
The information in the wiki needs to be up-to-date as it is processed by the census scripts, and
you need to notify the maintainers about all the issues those scripts detect.

At first I configured Debian Stretch VM and forked the project's codebase (actually, I cloned
it and created a fork only after I had trouble opening a merge request... remember, limited Git
skills). I didn't know which options to specify for the `make` command, so I was just sitting there
watching while it was creating directories for all the derivatives and producing some cryptic output.
Later I identified several kinds of errors in the output. The easiest ones were about broken
links and missing logo images, and those could have been fixed simply by updating the wiki pages.
So I did it. Some errors stopped appearing and I was proud of myself as if it was the project's most
important FIXME :)

Speaking of FIXMEs, later I picked some of them too. The files and directories produced by the scripts
are available [here](http://deriv.debian.net/), but there was no Description column before. My first
coding task was to create it. After finishing my work I knew much more about running and configuring
Apache servers, `mod_autoindex` module, `.htaccess` files and the census codebase itself, as
I had to read the README file thoroughly.

Other FIXME that I've chosen was ["add dd-lists of patched packages"](https://salsa.debian.org/deriv-team/census/commit/01668e1f52b7362e6e3f71bd35655b11a4d449ec).
A dd-list is a list of packages and their maintainers and uploaders. To be useful this information must
be the most up-to-date, in other words collected from Debian experimental and unstable suites.

Working on this task I got confused more often than ever before. Final commit looks good, but I can't
recall how many commits there originally were and I am afraid to look at the corresponding merge request.
Let's just say there were plenty of them.

**What went wrong:**
- I received lots of helpful information from Paul, but just couldn't handle it properly while misunderstanding
the very purpose of the task and being unable to ask the right questions
- I didn't realise that we needed a `debian.apt` directory with Debian sources files, and tried to use
sources from the derivatives `apt` directory (some of them even don't have one)
- I spent a huge amount of time trying to understand how to handle the `APT_CONFIG` environment
variable inside the Makefiles and my script

**Good moments:**
- As a result I learned how to:
  - write proper commit messages
  - squash commits
  - consciously add new targets with prerequisites and rules with automatic variables (all those `$@` and
  `$<` things) to Makefiles
  - use shellcheck tools to correct shell scripts
  - handle stress and be patient to myself, at least sometimes
- In the end the `APT_CONFIG` was set correctly!
- I proposed some ideas and they were accepted
- After all the struggle the `sed` syntax seemed relatively clear to me :')

Now I don't feel so bad about how I had described this contribution on the Outreachy website :)
After reading my description there one would think it all went without a hitch. No, it didn't!
It was a painful, but also exciting experience, and when all finally clarified it felt like a blessing.
And it's really cool when your code is reviewed by someone knowledgeable. And also I began to really
like Makefiles!

**What I would advise my past self**
- Don't panic
- Read the README
- Try IRC and Matrix, not only emails
- Make notes of the useful commands and working scripts, you might need them later
- Try to sleep better

## Final application

I had to write about my experience and provide the approximate timeline for the internship period.
I don't know if the application is supposed to be this long or not, but I wrote about my contributions,
the help I received and my feelings of the whole application process. Also there was a question
about personal or class projects which helped me to gain required skills.

**For future applicants:** I think it's good to mention all you've done to gain some required skill, be it reading, completing online-courses, solving puzzles, testing code samples or configuring environments. Unfinished projects seem to be good too! I myself wrote about one.
{: .notice}

## Results

My project had an extended deadline and I needed to wait only ten days until the results were announced.
I thought I would not be selected, but it happened! I remember feeling stunned for a few following days.
I was determined to do my very best, but a bit scared too. But the more I thought about the future, the more I liked it :)
Later in November I quited the job exactly as I had planned and was truly happy that I didn't have to
search for a new one in a hurry. Because I've already had something cool to do!

I want to say thanks to all Outreachy organizers for this awesome opportunity. And good luck to future applicants!
This winter promises to be a great and busy time. Can't wait to get started!
