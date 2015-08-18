---
layout: post
title: Sonian introduces Carousel
category: Open source projects
description: ""
author: Dan Dillinger
---

Today, we’re excited to open source another tool for writing flexible,
scalable cloud-aware services in Clojure. Sonian is committed to
Clojure, the cloud, and open source, and hope that you’ll find this as
useful as we do.

## What is Carousel?

Carousel is a library for anyone who wants to build a long-running
service, manage its lifecycle, and interact with it from the
command-line while it’s up. This extensible library lets a service
author easily define what it means to initialize, start, and stop
their software, query its status, and easily add any other phases that
might be needed. Here at Sonian, we use it to quickly set up the
common tasks needed to create new pieces of our cloud platform. We can
express things like queue declaration in just a couple of lines of
code, and drive their initialization from a Carica config file. And
when we need to implement a command or automate a task from our
scripts, Carousel’s defadmin lets us write pure functions with
standard arguments that will answer those requests. Interacting with
these services becomes as simple as sending text to a port. Adding
nrepl listeners is super easy, too.


## Where is Carousel?

It’s available on GitHub at https://github.com/sonian/carousel and
also from Clojars, for direct inclusion in your project.clj
files. Carousel is made available under the Apache 2.0 license, which
you can read here: http://www.apache.org/licenses/LICENSE-2.0.html

## Bonus!

Sonian’s also open-sourcing a Leiningen template to automate quickly
setting up a Pedestal service running inside an Immutant application
server. These excellent tools have quickly become favorites for
building REST APIs and other cloud services; we’ve standardized on our
best-practices in this template, letting us get right to work building
the software we need. We hope you find it useful in your projects,
too!

You can find it on GitHub at https://github.com/sonian/pedestal-immutant.

See more at: http://sonian.com/sonian-introduces-carousel/
