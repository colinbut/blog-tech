---
layout: post
title:  "Configuring a multi-module project in Maven"
date:   2016-02-21 20:10:08
categories: jekyll update
comments: true
---

## Background
<p><strong>In this blog post</strong> I am going to show you how to easily set up a multi-module Java project in Maven. This is not new. The reason i am writing this is because i feel there is not enough resources out there that documents how to do it. There is the Maven documentation guide but i think that is convoluted with so many irrelevant details if you just want to simple setup a very simple multi-module project structure in Maven.</p>

I eventually found out how to do by googling it and discovered a few articles with many bits and pieces. So in this article of mine, i am going to use this to collate all the knowledge i gathered from elsewhere.

## Pre-requisites

1. Maven
2. Java
3. IDE (I like to use either IntelliJ IDEA or Eclipse) - not essential
4. Capability with XML

## Here it goes...

The following is based on a sample project of mine: [Java EE Samples](https://github.com/colinbut/javaee-samples)


#### 1. Create standard Maven project
Lets us initialise a de-facto maven project structure:

```
mvn -B archetype:generate -DgroupId=com.mycompany.javaee-samples -DartifactId=javaee-samples -DarchtetypeArtifactId=maven-archetype-webapp -DinteractiveMode=false
```

Above will create a standard webapp project with the javaee-samples folder as the working directory for this particular project.

#### 2. Create modules
We need to decide what modules we are going to create. Lets say for this javaee-samples project we want individual Java EE technology samples to be a separate project on its own (modules) and we want them to be in a separate folder but still reside under the javaee-samples directory as the root.

Navigate to inside the javaee-samples folder:

```
cd javaee-samples
```

let's run the above maven command for each of the following sub-projects (modules) for now:

- jsf-sample
- jsp-sample
- jpa-sample

#### 3. pom.xml file configuration

This is where the magic happens. It is also to be the most difficult part. Well... not really.

In the root pom.xml file (the one under javaee-samples folder directory) edit it so it has the following contents:

{% highlight xml %}
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0                               http://maven.apache.org/maven-v4_0_0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.mycompany.javaeesamples</groupId>
    <version>1.0</version>
    <artifactId>javaee-samples</artifactId>
    <packaging>pom</packaging>
    <name>javaee-samples</name>

    <modules>
        <module>jsf-sample</module>
        <module>jsp-sample</module>
        <module>jpa-sample</module>
    </modules>

    <!-- plus other pom file configuration such as build info, dependency management etc... -->
</project>
{% endhighlight %}

In each of the following sub directories - for each of the projects - edit their pom.xml file so it is like the following:

{% highlight xml %}
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0                               http://maven.apache.org/maven-v4_0_0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <!-- specifying the parent pom.xml file project -->
    <parent>
        <groupId>com.mycompany.javaeesamples</groupId>
        <artifactId>javaee-samples</artifactId>
        <version>1.0</version>
    </parent>

    <!-- details for this pom.xml (project)-->
    <version>1.0</version>
    <artifactId>jsf-sample</artifactId>
    <packaging>pom</packaging>
    <name>JSF</name>

    <!-- plus other pom file configuration such as build info, dependency management etc... -->

</project>
{% endhighlight %}

That is it!. Of course this is a very basic sample showing you how to set up the structure. You will obviously need to expand on it yourself and add in the extra required information into your pom.xml file.
