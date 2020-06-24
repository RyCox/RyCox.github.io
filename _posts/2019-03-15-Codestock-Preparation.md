---
title: Codestock Preparation
author: Ryan Cox
date: 2019-03-15T09:10:00-5:00
layout: post
tags: []
archive: "2019"

---

OK, I've got approximately a month until Codestock, so that's a month until I give a presentation on 
### RESTful Testing.
God help me.

I've given the presentation once before, and I feel it went well.  I did a shallow dive into what RESTful calls are, how they're used by machines to talk to each other and pass data or kick off processes.  I think I'm going to go into more depth there, but also:

- Find a decent API to use for testing
- Create some automated tests to exercise this new service.
- Use Postman for manual and RestAssured for code.

So!  Let's get started.  First things first, I need a new service that isn't going to require me to import a bunch of miscellaneous frameworks and muddy up the waters.  After a brief search, I found [mockapi.io](https://mockapi.io/)!  I was able to create an account here, and then an Employee resource with the fields I required.

Once I had that, I was able to go to IntelliJ, create a quick [gradle project](https://github.com/RyCox/RestApiDemo) and add my dependencies

build.gradle file: 
    
    
    plugins {
        id 'java'
    }

    version '1.0-SNAPSHOT'

    sourceCompatibility = 1.8

    repositories {
        mavenCentral()
    }

    dependencies {
        compile group: 'junit', name: 'junit', version: '4.12'
        compile("io.rest-assured:rest-assured:3.0.5")
        compile('io.rest-assured:json-schema-validator:3.0.5')
        compile("org.springframework.boot:spring-boot-starter-test:2.0.1.RELEASE")
        compile("com.fasterxml.jackson.datatype:jackson-datatype-jsr310:2.9.0")
        compile("javax.xml.bind:jaxb-api:2.2")
        compile("com.fasterxml.jackson.datatype:jackson-datatype-jsr310:2.9.0")
    }

So, from here, I can create my api class in the test module, and start wiring things up.  RestAssured is going to allow me to make the REST calls, and Spring is going to wire it up for me so I don't have to instantiate it everywhere I want to use it and pass through properties, etc.

In the end, my tests looked like this:

``` java
    @Test
    public void testEmployees() {
        Response response = mockApi.getEmployees();
        Assert.assertEquals(200, response.getStatusCode());
        List<Employee> employeeList = new ArrayList<>();
        employeeList = response.as(employeeList.getClass());
        Assert.assertTrue(employeeList.size() > 0);
    }
```
You can find the full test suite on my [github page](https://github.com/RyCox/RestApiDemo).  Not as bad as I thought it'd be!