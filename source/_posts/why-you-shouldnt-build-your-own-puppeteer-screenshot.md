---
layout: post
title: Why you shouldn't build your own Puppeteer Screenshot API Solution
permalink: why-you-shouldnt-build-your-own-puppeteer-screenshot-api-solution
description: In this post we explain why building your own Puppeteer Screenshot API Solution could be inefficient and why you should consider a managed solution.
date: 2019-02-26 21:19:04
tags: 
- getscreenshot 
- puppeteer
---

Puppeteer is very quickly becoming the default solution that most developers choose to build web testing architecture for their apps. It's also becoming a very popular option to build parsers and services that depend on emulating browser sessions. One reason for Puppeteer's rising popularity is that until now most headless browser solutions weren't officially backed by browser vendors. Since Puppeeteer is the official Chrome headless browser solution by Google, it's not hard to understand why many developers are considering it over other popular solutions like Selenium and PhantomJS (officially abandoned/suspended). 

One popular use case for headless browsers is programatically taking screenshots of websites at certain points of the development process, like after deploy to a staging or production environment. 

Many companies also use headless browsers to [take screenshots of competitor websites](https://blog.rasterwise.com/2019/02/24/how-to-build-a-competitor-tracker-using-getscreenshot-and-cron-job-org/) and landing pages, or to track web properties like app store profiles and search results.

Whatever is the use case you might have to look for a programmatical web screenshot API, there's a high probability that you're considering Puppeteer to build this functionality. Not only Puppeteer offers an excellent and simple API that easily allows to trigger screenshot captures, but it also offers a comprehensive documentation and engaged community and development team.

However, building these solutions in-house not always make sense and usually implementing these systems can become an area where development resources are wasted, especially if your specialty is not building testing architecture and optimizing browser technologies.

If you're decision maker whose job is to optimize your development costs and optimizing the efficiency of your development team (or your own efficiency), keep reading. Here are three  important reasons why building your own puppeteer screenshot api solution is not always the smartest decision.


### Using Puppeteer is easy but is hard to make it work the right way.

Writing your own service on top of Puppeteer is usually not that hard. Puppeteer just requires a NodeJS runtime and a simple script with Async/Await JavaScript calls to execute different actions like setting up viewport sizes, hitting key strokes or capturing the loaded content. That's the easy part. However as you start digging more into your particular case you will quickly find out that Puppeteer is a very finicky machine that not always behaves as expected.

The default example found in Puppeteer's documentation only works for very simple websites and screenshots scenarios. In the practice you will find that you need to tweak the execution order of the action, add different logic to handle animations, add random waits and scroll operations to trigger lazy-loaded content, and more weird execution caveats. In general, Puppeteer requires you to constantly tweak different settings to capture specific rendering scenarions.

If you don't want to spend countless hours tweaking a script, writing your own implementation might not be a good option for you.


### Puppeteer needs its own infrastructure.

If you're planning to write a semi-useful screenshot utility for your company or yourself you will quickly realize that you need to run this somewhere. Amazon EC2? Amazon ECS? Digital Ocean Droplet? Google GCE? Heroku App? A Linux Machine in the janitorial closet?

Whatever is that you end up choosing, this is going to be extra infrastructure that needs to be provided, measured, mantained, secured and billed. If there's anything that the cloud has taught us so far, is that spinning new resources for random small utilities is not an efficient way of spending development resources. But even if you manage to provision architecture for your small application in a contained and cheap way, you will still need to deal with other issues like securing your application and exposing it to your core app in a consumable way. 

This is too much overhead for a particular and narrow use case.


### Developing non-core solutions is a money waster

When you spend time in areas that are not the core of your product, you're actually being financially inefficient. Taking screenshots is likely not a core task of your business so it doesn't makes much sense to waste development resources in this area.

Here is a brief example of how inefficient it gets:

A mid-level developer in a small market earns $90K USD per year, working 40 hours per week. His/her effective hour rate is: *$47 USD per hour*. 

Writing a basic implementation of a screenshot utility will take *at least 5 hours*. But this is just a simple prototype. Many use cases will need to be addressed, and there's likely going to be a large amount of time spent in optimizing, securing, provisioning, testing, etc. 

A realistic utility that can be used for a development workflow is going to take at the very least **30 hours** of development time, but likely more.

Other un-accounted areas of development time are: documentation, training and mantainance.

Given this scenario is very likely that writing a semi-good solution will take **more than a week** and mantaining it, will take at least **an hour every month**.
This means that writing this solution will cost almost **$2000 USD of development time** plus another **$500 USD or so, just to support it every year**. And of course this doesn't include the cost of the infrastructure you're paying to run it.


### So what's the alternative

We honestly believe that developers shouldn't waste their time and effort in building micro-utilities that don't serve the core of their product. That's why we build [GetScreenshot](https://getscreenshot.rasterwise.com/). We believe that spending +$2500 worth of development time and stress to build these kind of services simply doesn't make sense. Using a solution like GetScreenshot can cost you as little as 60 USD a year and it will give you a highly scalable and optimized screenshot Pupeeteer Screenshot API Solution. You focus on your app and we focus in providing you a reliable screenshot service.

We encourage you to [try us out](https://getscreenshot.rasterwise.com/), but even if you're not conviced with our service, we really think you should consider a managed solution to handle your screenshot operations. Not only you're off-loading all the complexities of writing and tweaking your solution, but also you're getting a predictable / affordable cost for something that shouldn't cost you that much in the first place.

If you're interested in trying out [GetScreenshot by Rasterwise](https://getscreenshot.rasterwise.com/) you can use this coupon (**FREEMONTH5**) to get the first month for free in the basic plan. Just go through the checkout and apply it at the end. Your credit card won't get charged. If you're curious about our implementation you can find more details in our [documentation](https://rasterwise.gitbook.io/docs/).

