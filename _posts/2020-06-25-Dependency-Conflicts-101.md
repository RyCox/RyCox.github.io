---
title: Dependency Conflicts 101
author: Ryan Cox
date: 2020-06-25T09:10:00-5:00
tags: ["gradle","java","dependency"]
img: ksp-notes.jpg
layout: post
archive: "2020"

---

# Dependency resolution process
I ran into a trippy issue with my tests recently.  I had a `null pointer` exception given, followed by a `no such method` error within a JaxB function.  I did my best to make sure I had everything I needed, and the versions that would support the actions I was trying to take, but nothing seemed to resolve and the exceptions were really confusing me (not a difficult task, I admit).

So, where to start?  I was _pretty_ sure that I was looking at a dependency conflict.  How do I know what dependencies were conflicting, though?  Well, most of the dependencies I was importing were APIs from other libraries, and I was sure they didn't actually _have_ any dependencies themeslves, so that narrowed down the list.  Then, I just needed to look in the documentation for the others to see what might be conflicting.  

What I found was this:  I was importing a specific version in my `build.gradle`, but another dependency was importing a different version of the same artifact.  This is known as **Transitive Dependency**.  

### Example: 

    + --- com.example:dependencyA:2.0.3
    + --- com.myDependency:libraryB:1.0.0
          | + -- com.example:dependencyA:1.0.3

In this example, I'm using version 2.0.3 of dependencyA, but the libraryB dependency has a dependency on version 1.0.3 itself.  This caused the issues I was seeing. 

## So!
How to resolve?  Well, there's a few ways:

1. You can force gradle to use a specific version of the dependency:
    
        configurations.all {
            resolutionStrategy.force 'com.example:dependencyA:2.0.3'
        }

2. You can set a substitution rule:
        
        configurations.all {
            resolutionStrategy.dependencySubstitution {
                substitute module('com.example:dependencyA:1.0.3') with module ('com.example.dependencyA:2.0.3')
            }
        }

3. Finally, you can exclude the dependency that's causing the problems as well:

        dependencies {
            compile('com.example:dependencyA:2.0.3')
            compile('com.myDependency:libraryB:1.0.0') {
                exclude 'com.example:dependencyA:1.0.3'
            }
        }

So, though it may take quite a bit of research to find out _which_ of your dependencies are conflicting, once you do the solution is easily remedied.

If you have any comments, please feel free to <a href="https://twitter.com/coxrya/status/1276228768152125443">reach out</a>!