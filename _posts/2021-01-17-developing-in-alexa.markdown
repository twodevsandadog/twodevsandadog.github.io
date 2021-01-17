---
layout: post
title: "Developing in Alexa"
date: 2021-02-17 10:15:00 +0200
summary: Discussion of Alexa skill development
published: true
---

For the last year or two I have been developing an Alexa skill on and off.  Compared to other alexa skills it heavily utilizes the screens on the Spot and Hub devices.

This has been a lot of what I have been learning about lately so I thought I would foster some discussion around it in case you are considering creating an Alexa skill or are curious about the ecosystem.

What's fun about it?
-------------------
It's gratifying working on a UI for a physical device.  Even more gratifying that it's a much simpler ecosystem than working on a website UI.  Website development is so complicated these days.

It's a relief to be able to code > refresh > see, touch and hear the changes I am making.  The APL documments are made from rather simplistic XML so the options in how you can do things are very minimal.  Yea, it's definitely a limitation, but one I guess I enjoy.

Small fish in the sea
-------------------
This is probably a weird thing to like about a platform but I really like it that the community is so small.  There's no prescident.  I can't find answers on StackOverflow (usually), people don't have opinions about how to develop on this (not as many anyway).  Have a problem?  Write a support ticket to Amazon; they're usually rather helpful.

It takes the pressure off, ya know?  I may not be a great Alexa developer, but who the heck is?  Not many people.  Just gotta figure it out as you go.

I fully admit, it's probably not a very marketable skill either.  But that's alright.

What's not fun about it?
-------------------
The ecosystem is pretty bad.  It's in a constant state of migration to a new way of managing/deploying.  Originally you had your interaction model that you uploaded (manually) to your skill and then you gave it a Lambda ARN to call.  You could update your interaction model and Lambda arn, they would review the changes, then push them to your production skill.

Now there are various options.  You can develop your Lambda function inside of the Alexa console itself (ugh, why would anyone do that).  You can also develop the code locally and then manage the lambda and interaction model inside of the Alexa framework.  Finally, you can still host your own AWS Lambda in a regular AWS account (thank goodness).

There's no built in options for hosting locally, you have to download a debugger file and run that on your machine, use ngrok so you expose a public URL on port 3000 then put that URL into the alexa skill config.  Even then there's bugs if you try to use any symbols and the skill will crash so I had to patch the debugger file.

What could improve Alexa development most?
-------------------
Make a first class emulator that runs locally!  Right now the only option is a test console inside of the alexa console.  You can select a device to show and then call your skill.  It's not accurate though, the UI there looks wildly different from me opening the skill on a physical device.  

As a consequence if I want to develop for a specific screen I really need that device in my house and I need to drive my partner crazy by saying "Alexa, open ___" repeatedly throughout development.

Also I am fully aware from feedback of my skill that older devices have different limitations than the newer ones but these aren't documented anywhere.  I have no way to change the version of the device that is being emulated in the test console, but I guess in it's current state I wouldn't really trust it if I could.

Would you make another Alexa skill?
-------------------
Probably.  But I would be much more realistic with my client about the limitations and what they should expect.  No matter how great the design is, you should probably expect mediocrity.  It'll work okay, but don't compare it to the capabilities of a website or phone app, it's not there (yet??).

Is it getting better?
-------------------
Yes, I will say, they are iterating on Alexa infrastructure quite quickly.  A lot has changed in the last year.  For example I used to have to authenticate and do a service call to an alexa endpoint to get details like the current user's timezone.  Now it's easily fetchable and built into the UI (and it never fails!).  Consequently I am often kicking myself wishing I did a feature 6 months later, but that's the nature of it.

Conclusion
-------------------
This was mostly meant to reflect on my experience and share with others if they were interested.

If you are an Alexa development enthusiast and have any comments or advice on this it would be great to hear from you.  <a href="mailto:britney.devs@gmail.com">Send me an email</a>.  You can also email me if you're curious about Alexa development and don't know where to start.  