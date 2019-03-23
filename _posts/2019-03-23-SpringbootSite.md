---
title: "Uber Simple Spring Boot REST API"
date: 2019-03-23T09:07:00-05:00
archives: "2019"
tags: []
author: Ryan Cox
---


## REST APIs are awesome.  
Think about it: 
    
1. There aren't any messy UIs to fool around with.
2. You can get your data in easy to read formats like JSON and, if absolutely necessary, XML.
3. Computers talk to each other with APIs, so you don't even need a human to do work.

So, it should come as no surprise that testing APIs are super easy and convenient.  First thing you need, though, to test an API is... an API.  So I decided I'd create one from scratch that would allow me to bang on it with some [RestAssured](https://github.com/rest-assured/rest-assured) tests and [Postman](https://www.getpostman.com/).

First thing I did was create a new gradle project with IntelliJ.  All we need to do is name the ArtifactId, which should be the project name, configure your gradle (default settings are fine here), and hit *GO*.  This will give you a basic Java project and some simple scaffolding.