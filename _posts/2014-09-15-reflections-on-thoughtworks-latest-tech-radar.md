---
layout: post
title: Reflections on ThoughtWorks’ Latest Tech Radar
category: commentary
author: Ian Truslove
---

I enjoy reading through
[ThoughtWorks’ Tech Radar](http://www.thoughtworks.com/radar/#/) every
time it comes out.  I heard ThoughtWorker Neal Ford talk about it in a
[No Fluff conference](http://nofluffjuststuff.com/home/main), and
thought it was a great idea for facilitating a conversation within
your team or company, and for giving you a personal yardstick for
keeping abreast of industry developments.

Company tech radars express a technology risk tolerance profile.  Each
“blip” on the radar is an item categorized into one of four quadrants:
Techniques, Tools, Platforms, and Languages & Frameworks.  Each blip
is also placed into a ring in the radar; the rings represent the risk
associated with the blip.  The rings are: Adopt, Trial, Assess, and
Hold.  The “Adopt” ring indicates low-risk.  “Trial” items are less
well understood, but perhaps on their way to “Adopt” status.  “Assess”
items are high risk because of a lack of information, and “Hold” items
are a high risk because of plenty of hard-earned information.  It’s
highly unlikely any two companies’ tech radars are the same, and
looking at a radar gives you a snapshot of a company’s technical
strengths, plans and direction, and (perhaps by omission) their
weaknesses.

For me, ThoughtWorks’ radar paints a picture of their consulting
activities, and seemingly takes a few fun jabs at the pain points
those folks must commonly endure.  Obviously they’re a software
consultancy, and they do lots of web-based front ends, some mobile
work, typically with JVM or perhaps .NET backends.  They are often
working in Big Corporate land, and the radar is their declaration of
war on the old “enterprise” ways, and a statement of intent: the Tools
quadrant is aggressive compared with the other three quadrants.  It’s
also laden with JavaScript and web front end tools. JavaScript
proliferation is called out in their headlines. I imagine there are
lively discussions on their internal JavaScript IRC channel!

## A Brave New World?

Connectedness is essentially an assumption. The ongoing revelations
from Snowden and trivial access to sophisticated intrusion and malware
toolkits hopefully refocuses all of us software types on on the
security of our customers’ data.

I enjoyed the double negative of “Ignoring OWASP Top 10” (Techniques#26; hold)
being placed in “Hold”, and thank the Germans for providing
us with a word for keeping only that which is necessary:
Datensparsamkeit (Techniques #19; assess).  If the system is
compromised, what is potentially lost or exposed?  Sloppy logging is
an attack vector, and should be considered when building and
maintaining systems.

Finally, whilst it’s good to see increasing adoption of two-factor
authentication (TOTP Two-Factor Authentication, Platforms #44;
assess), we mustn’t let ourselves see this as a panacea (Schneier,
[“Two-Factor Authentication: Too Little, Too Late”][schneier]), we must continue
to be rigorous about our security solutions.

[schneier]: https://www.schneier.com/essays/archives/2005/04/two-factor_authentic.html

## The Web Way

Sonian and ThoughtWorks seem to be similarly vested in the Web as more
than just for web sites (“Web as platform”, Jan 2011 radar; adopt).
REST APIs are seemingly ubiquitous, and a modern web UI is
mandatory. The JavaScript Cambrian explosion continues, and is even
called out in this Tech Radar headlines page.  Thankfully, software
engineering practices around the front end are more and more
commonplace.  “Segregated DOM plus node for JS testing” (Techniques #2; adopt)
and “Handwritten CSS” (Languages #106; hold) are at quite
different ends of the front end spectrum, but both represent a focus
on sustainable, maintainable code in a team setting.  Some interesting
points for me in this area were Grunt.js (Tools #59; trial) being only
in “Trial”, and Leaflet.js (Tools #73; assess) barely squeaking in to
“Assess”: both are stable, well-adopted tools with good APIs, good
documentation and active communities, and they are generally far
superior to those things they displace (hand rolled asset pipeline
scripts anyone?).  Given the amount of front end work I suspect
ThoughtWorks are doing, these valuable tools seem under-represented.

On the back-end side, Swagger (Tools #78; assess) and HAL (Languages #89; trial)
demonstrate the continual tension between a laissez-faire
approach of “getting things done” (perhaps at the expense of
communicating exactly what has been done) and standards-based
discoverable services (and XML overload).  Whilst treading the fine
line between the equally undesirable ends of this spectrum, I think
it’s great to see lightweight standards and automatable tools such as
these emerge. They are easy for API providers to adopt, and make it
easier for end users to understand, test, and consume the API.

## Pipelines

Continuous Delivery and DevOps themes are everywhere now, and
ThoughtWorks have been loudly sounding the call.  This radar covers
the old and the new.  “Chaos Monkeys” (Tools #53; trial) breaking your
stack combined with “Focus on mean time to recovery” (Techniques #6,
trial) has to be the apotheosis of the Continuous Integration mantra
of “if it hurts, do it more frequently”.  Netflix’s Simian army and
the all-or-nothing approach to ensuring the stack is operational under
some fairly extreme conditions, combined with a systematic,
quantitative approach to measuring and optimizing quality of service
in the event of failures must be the surest way to build high
confidence in the fault tolerance of your entire infrastructure.

Continuous Delivery is a huge incremental step beyond Continuous
Integration.  The rise in popularity of containerization and
virtualization tools like Docker (Tools #54; trial) and Packer (Tools #62; trial)
are surely driven by the difficulty in achieving an
end-to-end CD pipeline, and ideas like “Machine image as a build
artifact” (Techniques #10; trial) point out the one thing missing from
this (and the previous) tech radars: all the tools, languages,
techniques and platforms are useless without skilled, motivated,
trained people.

– [@iantruslove](https://twitter.com/iantruslove)
