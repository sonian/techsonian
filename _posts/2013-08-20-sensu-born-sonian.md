---
layout: post
title: Sensu - Born @ Sonian
category: Open source projects
description: ""
author: Steve Martin
---

Remember way back in 2007?

![Sensu]({{ site.baseurl }}/public/images/2013/07/sensu.png)

The Dixie Chicks cleaned up at the Grammys. The Departed won the
Academy Award for Best Picture as the U.S. began its “troop surge” in
Iraq and Nicolas Sarkozy was elected President of France…

That seems like a long time ago…

Well, that was the same time that Sonian started building their cloud
SaaS.  Back then, at the dawn of cloud computing, there simply weren’t
monitoring and management tools that could scale and integrate with
the emerging DevOps technologies.  As our cloud workloads grew, we
needed to build a monitoring and management framework to support our
growing installed base around the globe.

Sensu is that cloud monitoring framework.

Unlike it’s popular predecessor, Nagios, which uses a group of
centralized servers to perform continual checks on remote hosts to
determine system performance, Sensu adopted a more modern and
distributed design, employing RabbitMQ to manage the subscriptions,
check requests and health results. This model allows for far more
horizontal scaling and immediately drew the attention of developers
who were already running up against the limitations of Nagios.

If you like history and want the skinny on exactly how it works and
why we built it, you can find that
[right here](http://www.sonian.com/sensu-a-monitoring-framework/).

You can also
[see the groundswell start](http://sonian.com/the-sensation-of-sensu/)
in the first 100 days on Joe Miller’s
[excellent blog](http://www.joemiller.me/2012/01/19/getting-started-with-the-sensu-monitoring-framework/).

Former Sonian Sean Porter delivers a great overview on the Audax
Health Engineering podcast.  You can find it through
[this blog entry](http://www.audaxhealth.com/wp/company-news/cloud-monitoring-a-conversation-with-sean-porter-on-sensu/)
which includes LOTS of other great Sensu links.

If you’re more interested in the present, start with the
[GitHub wiki](https://github.com/sensu/sensu) where you’ll find an
engaged community that wants to see you succeed. Join the ever-growing
list of companies successfully managing workloads in the cloud,
courtesy of Sonian.

We built it because we needed it.  We open sourced it because we knew
it was an important tool that would help others struggling with
significant cloud workloads.  Sonian continues to open source code
because we believe it fosters cooperation and drives innovation. We
did it years before Tesla, #justsayin.
