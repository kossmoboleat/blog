---
layout: post
title: Talking with machines: What is an URI/URL
date: 2017-01-14 09:30:54.000000000 +01:00
---

## DDD & REST

I recently had a discussion with a colleague about the way a web application should model its backend API. We have always claimed to have a RESTful API, but after watching a [talk by Oliver Gierke](https://jaxenter.de/ddd-rest-45713) I'm not so sure anymore. His talk "DDD & REST" is mainly about two things. First he points out that DDD offers very useful ideas to model business domains. Second he argues that the same principles can be applied to "modern" REST APIs. 

Now this is where the trouble starts. I've blogged about how IT is prone to buzzwords in [another post]({{ site.baseurl }}{% post_url 2013-10-16-computer-vocabulary-is-immature %}). Unfortunately REST has become nearly a buzzword too, i.e. it's meaning has become very vague. So I thought great, let's write a blog post about this. Turns out defining what REST is takes about 180 pages and a [Phd thesis](http://www.ics.uci.edu/~fielding/pubs/dissertation/top.htm). Therefore I'm going to take this slow and do this step by step as I learn. [Wikipedia's first sentence on REST](https://www.wikiwand.com/en/Representational_state_transfer) is:

> **Representational state transfer** (**REST**) or **RESTful** [Web services](https://www.wikiwand.com/en/Web_service) are one way of providing interoperability between computer systems on the [Internet](https://www.wikiwand.com/en/Internet). REST-compliant Web services allow requesting systems to access and manipulate textual representations of [Web resources](https://www.wikiwand.com/en/Web_resource) using a uniform and predefined set of [stateless](https://www.wikiwand.com/en/Stateless_protocol) operations.

## URI vs URL

When using REST you can choose any kind of protocol you want. You could use bare TCP-sockets or Websockets or HTTP. As HTTP is the most used protocol today I'm going to concentrate on it. The Web resources mentioned in Wikipedia's definition in case of HTTP need an address. Oliver called this address a URI a couple of times. The term URL is much more familiar to me and I'll try to define the two here.

URI stands for uniform resource identifier and it's the super-set of all URLs and URNs. Formally it's a "string of characters used to identify a resource" [[wikipedia](https://www.wikiwand.com/en/Uniform_Resource_Identifier)]. URL stands for uniform resource locator. So in addition to precisely identify a resource you also get a means to locate it. URN stands for uniform resource name. Wikipedia has a useful analogy to explain the difference:

> A **Uniform Resource Name (URN)** can be compared to a person's name, while a **Uniform Resource Locator (URL)** can be compared to their street address. In other words, a URN identifies an item and a URL provides a method for finding it.

A good example for a URL is "http://blog.timbenke.de/root-of-all-problems-on-android/". It contains the protocol "http" that can be used to find the resource. A useful example for a URN is "urn:isbn:0-486-27557-4". With the given information its possible to find the book in any book store. Still it's not as specific as the protocol part in the URL. Wikipedia has another example with a more hierarchical URN path: "urn:example:mammal:monotreme:echidna". 

A relative URI or URI reference can be used to specify a "local id" of a resource relative to the current context. In the case of HTTP this can then also be a relative URL. If I have source code in a file http://blog.timbenke.de/posts/index.html

```html
    <img src="../images/foo.png"/>
```

Then given the base URL and the relative path "../images/foo.png" you can easily determine a new absolute URL:

http://blog.timbenke.de/images/foo.png. That's why the relative URI is in fact also a relative URL because using the context information you have a "means of acting upon or obtaining the representation" [[wikipedia](https://www.wikiwand.com/en/Uniform_Resource_Identifier)]. 

REST services sometimes use relative URLs or URLs without protocol because repeating the complete address would be too verbose. I.e. when obtaining a list of widgets you get 

```javascript
{ "widgets" : [
  {"name" : "widget 12",
  "href" : "/widgets/12"},
  {"name" : "widget 37",
  "href" : "/widgets/37"}
]}
```

Usin a relative URLs in the form of "../widgets/56" is discouraged. Still a URL of the form "/widgets/12" is only a URL because there's an absolute reference URL that contains the protocol.

Given all this complicated work we had to do to define URLs from URIs I understand completely why Oliver Gierke always talked about URIs :-)

References:

* https://www.w3.org/DesignIssues/Relative
* https://danielmiessler.com/study/url-uri/#gs.UsybhdA
* https://www.wikiwand.com/en/Uniform_Resource_Identifier
