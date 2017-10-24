---
layout: post
title: Learning to leave the fallen behind
snip: A case for not supporting the older XML messaging system for your new APIs. Sacrificing backwards compatibility for a better tomorrow.
humanDate: December, 2013
cover: http://www.wallpapers-web.com/data/out/93/4563064-great-wallpapers.jpg
---

So, we have been working on creating a public facing API. We are working in a
market where we expect the users (most of them) of such an API to not have
technological expertise or even soundness. As elitist as that may sound, I have
personally interacted with a few and can vouch that they are still far behind
the crowd that usually consumes any API. It is still a technologically nascent
market.

A dilemna that recently came up was what messaging format to use. Arguments
between XML and JSON were sought. JSON won, naturally, being the lightweight
schema-less creature that it is. There were still some discussions and we
reluctantly released a XML version of the API as well. I wasn't happy, and will
enumerate some of the reasons for the same.

## XML (eXtensible Markup Language)

XML is a document format. It is immensely popular as one because it is easy to
validate because it can have a schema. Also, with `<![CDATA[]]>`, it is super
easy to embed binary messages, such as images and media. It is incredibly
useful and has led to many open formats such [Office Open XML][docx] which
allow greater and easier interoperability between separate systems. As an
example, say you were writing a .docx viewer. Because the document is in XML
you wouldn't have to write a parser to convert to domain objects in your
language of choice. You can leverage XML libraries already available and
robustly map the document to its memory representation without wondering
whether you have addressed all the parsing requirements.

XML is powerful and it works great in the domain it was meant to be applied to.
The problem starts when we started using XML as a data exchange format. It is
too beefy and complex.

## JSON (JavaScript Object Notation)

JSON is a reduced subset of JavaScript that makes use of programming language
constructs like objects, attributes and arrays. As such, parsing JSON into data
structures in the programming language of your choice is consistent. Also, JSON
as a format and a grammar is much simpler. The validity of JSON is only judged
by the ability of a JSON parser to parse it. There is no schema necessary. This
is bad if you want to use JSON to write documents with a pre-decided format.

<blockquote>Use the correct tool for the correct job.</blockquote>

## Comparing JSON to XML as a data exchange format

* An XML document is a tree. A JSON document is a key-value structure. While
trees are immensely extensible, they are not natural. They should not be used
everywhere. They have ambiguity built into them. An example:

{% highlight xml %}
<book>
  <title>Harry Potter and the Chamber of Secrets</title>
  <author>J.K. Rowling</author>
</book>
{% endhighlight %}

is as valid as

{% highlight xml %}
<book title="Harry Potter and the Chamber of Secrets" author="J.K. Rowling"/>
{% endhighlight %}

For a book with multiple authors, you can only use the former mechanism and not
the latter. In JSON, there is only one way to represent the information.

{% highlight json %}
{
  "author": "J.K. Rowling",
  "title":  "Harry Potter and the Chamber of Secrets"
}
{% endhighlight %}

In case of multiple authors, just replace the string with a list of strings.

* The thing with trees is that they can go very deep if unchecked and they
provide a mechanism for you to think about such deep structures. If you are
writing or consuming JSON, the key-value nature of the message will keep you 
from thinking up deeply nested structures.

* Aside from this, XML messages are verbose and would take much larger bandwidth.
Although for short messages, this hardly matters, when you are serving public
APIs, the volume of data becomes significant.

<hr>

## The Responsibility of the Producers

Providing an XML view of the same data is not really a large technical
challenge. It is a matter of replacing the rendering module with another one.
So why the rant?

I believe any producers of publicly consumable content are responsible for
driving the standards and best-practices in that domain. News channels are
responsible for ensuring correct and objective coverage of events. Any fall in
the standard of the news as general will be attributed to each of the channels.

Similarly, when we provide JSON *and* XML as data exchange solutions, we are
endorsing the usage of XML in a domain it wasn't designed for. We are letting
past decisions, wrong as they may have been, influence the future direction.

As long as such XML APIs are available, there will be consumers for such APIs.
It is the responsibility of the producers of such APIs to educate the consumers
and move them forward. If we keep trying to maintain the same feature set as
company X and decide to support arcane usage patterns, how will the industry as
a whole move forward?

Producers need to provide incentive to the consumers so that they may move
towards, what we know for a fact to be, more effective alternatives. This is
where I believe new APIs need to improve. This is where we have a chance to
make a difference, to shape the outcome of the future, and this is where we
usually shy away from our responsibilities, because we do not have faith in our
own ability to educate and lack the conviction to drive technological change.

<hr>

*Opinions expressed are solely my own and do not express the views or opinions
of my employer.*


[docx]: http://en.wikipedia.org/wiki/Office_Open_XML


