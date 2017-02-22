---
layout: default
title: News
permalink: /news/
---

<div class="notification" markdown="1">
Follow us on 
[Twitter](https://twitter.com/sparkjava)
to get the latest news, and other Spark related content
</div>

## Spark 2.5.1/2.5.2 static files vulnerability
Early November 2016 a [vulnerability](http://www.cvedetails.com/vulnerability-list/vendor_id-15987/product_id-34958/version_id-203903/Sparkjava-Spark-2.5.html) in how Spark 2.5/2.5.1 handles static files was exposed through a [mailing list](http://marc.info/?l=full-disclosure&m=147814643630342&w=2).
We fixed it the same day we became aware of it, and a new version of Spark (2.5.2) was released.

The person who found the vulnerability says they tried to contact us for weeks and that we were unresponsive, but we would like to note that this attempted contact was limited to sending each of us an email using an obscure custom domain that the sender knew might get caught in gmail's spam filter (they stated this in the email).
Be assured that we do read emails and that this is the first email gmail has mistaken for spam in years.

### Best practice for reporting vulnerabilities:
1. Try to email us (preferably using a normal domain). Our emails are on the [contact](/contact) page.
2. If 1 fails, create an issue on GitHub saying you need to talk to us about a vulnerability.
3. If both 1 and 2 fails, create an issue on GitHub describing the vulnerability.
4. If 1, 2 an 3 fails, feel free to expose the vulnerability in order to inform people.
It's not that we want to keep vulnerabilities a secret, but we want to users to have a fixed version of Spark to switch to once the vulnerability is exposed.

## Spark 2.5 released (May 2016)
At last, {% include macros/mavenLink.html version="2.5" %}
We made so many changes that we decided to skip version 2.4! ... ... ... Okay, we did release 2.4, but there was a bug in the static file API. Since you can't amend or remove a release on maven we had to do a new release.

### New static file API:
~~~java
staticFiles.location("/public");
staticFiles.externalLocation(System.getProperty("java.io.tmpdir"));
staticFiles.header("Server", "Robustified Backend");
staticFiles.expireTime(600);
~~~

### Convenience API for redirects:
~~~java
redirect.get("/hi", "/hello");
redirect.post("/hi", "/hello");
redirect.put("/hi", "/hello");
redirect.delete("/hi", "/hello");
redirect.any("/hi", "/hello");
~~~

### Instance API
The instance API is intended for advanced users, so the official documentation will still use the static api. Everything normally available in the static API is now available on objects you can instantiate:
~~~java
// When using the instance API, the Service variable should
// be called 'http' for the semantic to make sense
// ie: http.get("..."), http.post("..."), etc

public static void main(String[] args) {
    igniteFirstSpark();
    igniteSecondSpark();
}

static void igniteSecondSpark() {
    Service http = ignite();

    http.get("/basicHello", (q, a) -> "Hello from port 4567!");
}

static void igniteFirstSpark() {
    Service http = ignite()
                      .port(8080)
                      .threadPool(20);

    http.get("/configuredHello", (q, a) -> "Hello from port 8080!");
}
~~~

### Route Overview
We've added an experimental feature which displays all the mapped routes of your application:

You can enable it like this:

~~~java
RouteOverview.enableRouteOverview(); // overview available at /debug/routeoverview/
RouteOverview.enableRouteOverview("/my/overview/path"); // available at specified path
~~~

## Spark Debug Tools
We've started a new project, called Spark Debug Tools 
(repo [here](https://github.com/perwendel/spark-debug-tools))

There has also been other bugfixes and minor changes. {% include macros/seeCommitHistory.html %}

## Spark 2.3 released (Sep 2015)
Woop woop, {% include macros/mavenLink.html version="2.3" %}

Changes
* WebSocket support
* Thymeleaf template engine support
* Jetbrick template engine support
* Major improvements to implementation
* Newer versions of all dependencies
* Other minor features have also been added, as well as some bugfixes. {% include macros/seeCommitHistory.html %}

## Spark 2.2 released (May 2015)
{% include macros/mavenLink.html version="2.2" %}

New features
* GZIP support
* Support for multiple new template engines:
* Handlbars
* Pebble
* Water
* Spark jar now seen as bundle by any OSGI container
* Embedded Jetty threadpool configuration
* awaitInitialization method on SparkBase
* Unicode support for routes and params
* Methods for removing all routes (or particular ones)
* There have also been other minor bugfixes and improvements, {% include macros/seeCommitHistory.html %}

## Spark survey results (Apr 2015)
### About the survey
For the past couple of weeks we've been showing users on the documentation page a survey popup (in the lower right corner though, we're not evil). A couple of hundred users have responded to the survey now, so we've stopped it. We're sorry if this annoyed anyone, but hey, at least we're sharing the results with you.

### Survey results
<img src="/img/news/survey1.png" alt="Spark survey results image 1">
As expected, a lot of our users (51%) use Spark to create REST APIs, but the amount of people who use Spark to create webpages is pretty high too (25%). Most people use Spark for personal projects (57%), but a lot also use it at work (42%).

A surprisingly high number of our users seem to be using Spark for educational purposes, which is cool. We've seen the most educational traffic from Brown University (thank you Miyazaki-sensei, if you have any feedback from you or your students, please let us know).

Note: It was possible to select as many alternatives as you wanted for this question, so keep in mind that there is a lot of overlap between the different groups.

<img src="/img/news/survey2.png" alt="Spark survey results image 2">
As can be seen from the first question, about 80% of our users have not deployed their application. These people have been omitted from this chart, making the sample size approximately 50 people. Still, it indicates that Spark is a viable candidate for bigger projects.

<img src="/img/news/survey3.png" alt="Spark survey results image 3">
No big surprises here. As most Spark users create REST APIs without any view, they have little interest in template engines. Good news for Freemarker users though, we will work on better code examples for you guys in the coming months, showing that it's definitely possible (and easy) to create a web application with a MVC'ish structure in Spark!

<img src="/img/news/survey4.png" alt="Spark survey results image 4">
We're glad to see that 90% of our users think that Spark's documentation is okay or better ("Good" being the largest group at 41%). If you find any faults or have any input regarding the documentation, please let us know. We would like all our users to think that our documentation is at least okay.

## Spark 2.1 released (Dec 2014)
Per has been really busy at work lately, but {% include macros/mavenLink.html version="2.1" %}
The new version is 2.1, not 2.1.0. Since we're aiming to be a lightweight/micro web framework, we decided that having 3 digits was too much! Also, eight more versions will probably be more than we need before the next major release of Spark (3.0).

Changes
* Added Request.bodyAsBytes() (get the body as bytes without having to convert it to String)
body() is now available even if "consumed" by previous filter/route (this also solves some query map related problems)
* Allow overriding of HTTP method using X-HTTP-Method-Override header
* Static resources functionality for other application servers (previously only available for the embedded Jetty)
* Fixed MimeParse Exception
* Moved route error info to log (from 404 page)
* Replaced all System.out/System.err with slf4j logging
* Other smaller bugfixes


## Spark is used all around the world (Oct 2014)
One month after the website redesign we decided to have a look at which countries Spark users come from, so we created a heat map of our website visitors. While this is probably not 100% corresponding to our user base, it's reasonable to assume that it's pretty close. We're proud to be a Java web framework with such a diverse user base, but Africa (and Greenland) seem to be a little underrepresented... If you know any web developers there, please spread the word (ᵔᴥᵔ)

<img src="/img/news/sparkworld.png" alt="Spark user heatmap">

Top ten countries
1. United states (23.44%)
2. China (7.06%)
3. Germany (6.21%)
4. India (5.44%)
5. United Kingdom(5.09%)
6. France (3.52%)
7. Brazil (3.04%)
8. Poland (2.95%)
9. Japan (2.70%)
10. Canada (2.56%)

In total we had visitors from 141 different countries!


## Spark 2.0.0 released (May 2014)
{% include macros/mavenLink.html version="2.0.0" %}
Spark 2.0.0 is a complete rewrite of the old Spark core to provide support for the new Java 8 lambdas.
The new paradigm is hugely based on the lambda philosophy, so Java 7 is officially not supported anymore. If you want to work with Java 7, you can still use Spark 1, but unfortunately it won't be updated any longer. Please consider migrating to Java 8 if possible :)

Spark 2 Hello World
~~~java
import static spark.Spark.*;

public class HelloWorld {
    public static void main(String[] args) {
        get("/hello", (req, res) -> "Hello World");
    }
}
~~~
