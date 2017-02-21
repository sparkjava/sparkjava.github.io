---
layout: default
title: Download
permalink: /download/
---

## A Lightweight Web Framework
Spark Framework is a true micro Java web framework. Its total size is less than a megabyte, and to keep it lean and clean we decided to cut support for Java 7 in Spark 2. If you are stuck with Java 7 for whatever reason, you unfortunately have to have to use Spark 1.

## Download Spark Framework
Spark Framework is available both on <a href="http://search.maven.org/#search%7Cga%7C1%7Ca%3A%22spark-core%22" target="_blank">Maven Central</a> and <a href="https://github.com/perwendel/spark" target="_blank">GitHub</a>.

### Maven Users
Add the following snippet to your <a href="http://maven.apache.org/pom.html" target="_blank">POM</a>:

~~~markup
<dependency>
    <groupId>com.sparkjava</groupId>
    <artifactId>spark-core</artifactId>
    <version>2.5.5</version>
</dependency>
~~~

Not familiar with Maven? Click [here](/tutorials/maven-setup) for more detailed instructions.

### Other dependency managers:
~~~java
Gradle : compile "com.sparkjava:spark-core:2.5.5" //add to build.gradle
   Ivy : <dependency org="com.sparkjava" name="spark-core" rev="2.5.5" conf="build" /> //ivy.xml
   SBT : libraryDependencies += "com.sparkjava" % "spark-core" % "2.5.5" //build.sbt
~~~

## Non-maven Users
Clone the repo from <a href="https://github.com/perwendel/spark" target="_blank">GitHub</a>,  
If you really want to, you can also download Spark Framework as a <a href="https://github.com/perwendel/spark/archive/master.zip">ZIP (from GitHub)</a>