---
title: "Refocusing"
date: 2017-10-28T09:07:00-05:00
archives: "2017"
layout: post
tags: []
author: Ryan Cox
---
I feel like I’ve been all over the place lately. Work has been a lot of re-verifying old applications and updating existing tests to use the latest architecture and features. Honestly, it’s been getting monotonous, though certainly necessary. Technical debt, while not always super interesting, is absolutely necessary. That said, I’m getting to do some new stuff soon:

Typescript – We’re working on an Angular 2 (which is actually Angular 4.something… go figure) application that we’re going to be using protractor for the UX testing. Since the application’s going to be in typescript, so will the automation! New language [check]

SNS testing – We’re using a lot of AWS stuff at work these days, and one of the biggest features being taken advantage of is Simple Notification System messaging. So, for functional testing of the apps that make use of it, we’re using an AWS client to generate a CLI key that gives us access to read and/or post to the topics and get the JSON messages so we can serialize/deserialize them into Java objects. Really cool stuff.

Speaking of AWS, I just finished a training on some AWS Architecture and Solutions, so I should be able to put together a blog post on some of what we did. Good times.