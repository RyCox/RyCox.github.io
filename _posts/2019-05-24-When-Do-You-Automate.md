---
title: When Do You Automate?
author: Ryan Cox
date: 2019-05-24T09:10:00-5:00
layout: post
img: software.jpg
tags: []
archive: "2019"

---

## How do I decide what I'm going to automate?
---
Well, it's really simple: What do I need to do over and over, but don't want to?  That's what it all boils down to.  When I'm looking at something that's both **repetitious** and **tedious**, I'm looking at something that deserves to be automated.

That said, how long is it going to develop the test?  Am I going to have to spend three hours on something that won't be executed every build?  Is this test such an edge case that running it once and then adding it to the backlog of tests doesn't add any benefit?  Personally, this is my biggest area of opportunity for improvement, as I really like coding things and figuring out how to automate even the most absurd of scenarios.

    Scenario: If Mercury and Uranus both aligned with Earth, and my API hadn't switched over from the DNS, and my data was invalid, I should get a 400 and a very specific and concise error message regarding the orbit of the database.

Of course, that's hyperbole, but you get the point.  The benefit of running that scenario in every CI build makes zero sense.

So, to summarize and use a neat bullet point list, I will automate a scenario if:
- It will be done repetitively
- It will not take longer than twice the time to manually execute it to develop the scenario in my automation
- The test will be used regularly to validate regression

Finally, if the answers to those bullet points aren't really clear, then you're left with:  Is the benefit of automating the scenario outweighed by the cost of automating it?  

Clearly, this isn't a hard and fast rule, but something that's going to vary based on your team, your experience, and your sprint estimates.  That said, realizing that not everything *has* to be automated is sometimes the biggest hurdle.