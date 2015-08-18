---
layout: post
title: Introducing Apodini, A Step Toward Clojure!
category: Open source projects
description: "Apodini release: a Clojure REST client for Rackspace CloudFiles and OpenStack Swift"
author: Dan Dillinger
---

We are excited to announce the open-source release of Apodini, one of
our internal libraries. Here at Sonian, we are committed to quality
software and to contributing to the projects that have helped us so
much, and Apodini is another way of us saying, “Thanks!”

## What is Apodini?

Apodini is a Clojure-native REST client for Rackspace CloudFiles and
OpenStack Swift. Written entirely in Clojure from the ground up, it
provides a comfortable functional interface for Clojure developers
working with the CloudFiles family of object stores. In case you were
wondering, the name ‘Apodini’ comes from the taxonomy of swifts, one
of the fastest flying birds in the world.

One of the key components to Sonian’s Information Discovery Cloud is
having easy, consistent and well-understood tools with which we can
innovate over technologies like cloud-based object stores. Sonian is a
user of, and a contributor to, the OpenStack project. We have been
“pioneering” the use of cloud object stores for over six years, and
understand the nuances between the various offerings. We created
Apodini to be a library that is the right fit for us. Now we hope it
can be the right fit for your project, too.

## Why did we build Apodini?

With Apodini, we’ve been able to more easily understand the code we
need to make the best use of our Swift and CloudFiles object
stores. We’ve also been able to make quick and easy changes, and
tailor it to suit our evolving needs, such as supporting multiple
authentication methods. Apodini also provides easy-to-use functional
abstractions; for example, lazy sequences over object listings that
completely takes pagination out of the list of things developers need
to worry about.

## Where is Apodini?

It’s available on github! Go to https://github.com/sonian/apodini and
check it out. It’s also available for use directly from your Clojure
project’s configuration, just add it to your project.clj and you’re
all set.

Apodini is made available under the Apache 2.0 license, which you can
read here: http://www.apache.org/licenses/LICENSE-2.0.html

![Apodini]({{ site.baseurl }}/public/images/2013/04/Apodini.jpg)
