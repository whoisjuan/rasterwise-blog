---
layout: post
title: How to build a competitor tracker using GetScreenshot and cron-job.org
permalink: how-to-build-a-competitor-tracker-using-getscreenshot-and-cron-job-org
description: This tutorial explains how to build a periodical screenshot tracker, that allows you to get captures of your website or competitors websites and receive them in your email inbox.
date: 2019-02-24 20:10:59
categories: tutorial, getscreenshot
---

### Getting Started

In this post we will learn how to build a **simple competitor tracker** that will send you daily / weekly /  monthly screenshots of competitors websites or any website that you periodically visit to track how its changing. For example App Store review pages or feeds with low activity. We will also briefly explore how a GET API call works and its key elements. This tutorial is for begginers. If you're familiar with APIs and development in general feel free to jump to the **TL;DR** part at the end.

### Pre-requesites

To build this tracker you will need a [GetScreenshot](https://getscreenshot.rasterwise.com/) Screenshot API key and a cron-job-org account. We will be using GetScreenshot built-in mail functionality to send the captures to your own email account.

The first thing you want to do is subscribing and obtaining a GetScreenshot API. GetScreenshot costs 5 USD a month but you can enter the coupon FREEMONTH5 at the checkout to get the first month waived. You will also need a cron-job-org account which is free.

You can get your GetScreenshot API Key [here](https://getscreenshot.rasterwise.com/); 
And get your cron-job-org account [here](https://cron-job.org/en/signup/).

### Setting Up The API Call

After you subscribe and get your API key you will need to compose and API query call that will be used as the backbone of your tracker. GetScreenshot API is a RESTful API with a very simple and minimal setup. It's basically a simple URL that takes in some pieces of information to give you back what you're requesting.

For the sake of this example we will assume that we want to screenshot the New York Times homepage in a daily basis. Here are the pieces that you will require to build the API call and adjust it to your screenshot needs:

1) Base API URL: https://api.rasterwise.com
2) API Key: You will receive this after subscribing.
3) URL of Website you want to screenshot: Any URL you want to screenshot, in this case https://nytimes.com
4) Email address where you want to receive the captures: Any email address like john.doe@example.com

Additionally you can add other pieces (parameters) to adjust the type of screenshot you're getting. You can learn more about this in the documentation but for now we will keep it simple.

Now that we have all the pieces we can use them to compose the API call that will be used to screenshot the New York Times.

Our final API call will look something like this

`https://api.rasterwise.com?apikey=PUT_HERE_THE_KEY&url=https://nytimes.com&email=john.doe@example.com`

If you look closely this is just a composition of all the pieces. Basically the pattern is the following:

Base API URL + `?apikey=` + API Key + `&url=` + URL of Website + `&email=` + Your Email Address.

#### Brief Explanation of GET API Calls 
> This is basically how RESTful APIs work. They are URLs that receive different types of calls. In this case we are making a GET call and we are passing the parameters to the API via query parameters which are small capsules like `&url=` that receive the information. When you make this call, then the server gets this information and proccess it to return back what you're asking for.

If your final API call is correct you should be able to enter this in your own browser navigation bar and get a response back that will look like this:

```
{
    "status": "success",
    "originUrl": "https://www.nytimes.com",
    "captureDate": "2019/02/23",
    "captureHour": "21:12:15",
    "screenshotImage": "https://rasterwise.s3.amazonaws.com/temp/imageYJi781B4Po.png"
}
```

You should also receive an email message with the screenshot attached to it.

If you're not getting this back, make sure that your API key is correct and that the parameters are being passed correctly. The first parameter should be `?apikey=`. Note that it starts with a `?` and the rest of parameters start with `&`.

---
### Setting Up The Recurrent Task (a.k.a: Cron Job)

Now that we have our API call ready is time to use it in cron-job-org. This service allows you to put a schedule and perform actions programatically. These actions are known as cron jobs. In this case cron-job.org is going to make the API call that we just composed in a daily basis, just like if we were doing it from the browser. Every day we will receive an email with the attachment of a freshly taken screenshot.

The first thing you want to do is creating a cron-job-org free account. You can create it by visiting this [link](https://cron-job.org/en/signup/)

After creating an account and logging in. Go to the cronjobs section.

{% asset_img 'download1.png' cron-job-1 %}

Then click create cronjob.

{% asset_img 'download.png' cron-job-2 %}

Now you have to pick a name. Then, where it says url, paste the API call we composed at the beggining of this tutorial. Finally in the schedule section, pick a schedule that fits your tracking needs and save the cronjob.

{% asset_img 'download-2.png' cron-job-3 %}

Success! At this point you should have a solid tracker that we will send periodic screenshots of any website directly into your inbox.

You can replicate these steps to create as many trackers as you want and with whatever frequency you want. GetScreenshot gives you 2500 Screenshots a month, so you can build screenshot trackers for your co-workers and different projects.


### TL;DR 

1) Using the GetScreenshot API, compose an API call that fits your screenshot needs. You will need to use the `email` parameter to recieve the screenshot on your inbox, but you can also use the webhook option to post to a custom endpoint like a Slack endpoint or an IFTTT endpoint. You can find all the details of the GetScreenshot API at getscreenshot.gitbook.io
2) Sign-up a cron-job.org account and create a cronjob that makes a call to the GetScreenshot API. In cron-job-org you can set the periodicity of the call to fit your needs.
3) You should get the screenshots and its resulting operations at the time at which you set them in cron-job-org.