---
title: "The Java For-Loop"
date: 2016-10-21T09:07:00-05:00
archives: "2016"
layout: post
tags: []
author: Ryan Cox
---
I’m beginning to enjoy Java.  Here’s a small thing I learned a while ago (truth be told, I found this post as a draft and figured I’d finish it and post it six months later…  Sue me.)  that could save you some heartache or at least a line or two of code:  the .forEach function on a List object is amaze-balls.

Example:  I have a List of widgets:

```List allTheWidgets = new ArrayList();```

Now, let’s say that I want to do something like make an assertion on each of the widgets in that list.  You’d probably start by doing something like:

``` for (int i = 0; i < allTheWidgets.size; i++ ) {```
```    Assert.assertEquals(allTheWidgets.get(i).getSomeProp(), "The value I expect"); ```
```}```

Now, that’s all well and good, but it can be done even easier than that.

```allTheWidgets.forEach(widget -> {```
    ```Assert.assertEquals(widget.getSomeProp(), "The value I expect");```
```}```

The widget in the above code is a single object in the list of Widgets, iterated through the list itself.  Therefore, without having to declare a new instance of a Widget or iterate through a list by an index, you can perform the same function or set of functions on every position in the list created.  This is referred to as a passive iterator.

Not Earth shattering, but could come in handy.