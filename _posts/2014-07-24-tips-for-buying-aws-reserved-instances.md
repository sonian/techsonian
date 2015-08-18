---
layout: post
title: Tips for buying AWS Reserved Instances
category: Cloud
description: ""
author: Pete Zimmerman
---

AWS Reserved Instances are a scalable, easy and cost effective way to
store your information in the cloud. As described on the
[Amazon AWS site](http://aws.amazon.com/ec2/#pricing), it’s a web
service that provides resizable capacity in the cloud.

![AWS]({{ site.baseurl }}/public/images/2014/07/aws-logo.jpg)

For those who are already using AWS, here are some recommendations:

First generation AWS ECS instance users, if you have Reserved
Instances up for renewal this year, benchmark the proper replacement
instances with the 2nd and 3rd generations. Get your infrastructure
automation ready to bootstrap these instance types.

Be sure to calculate upfront cost savings and the ongoing hourly
instance discount between the old and new instance types. In some
cases, it may be more economical to renew your new instance type weeks
or even months early.

If you’re using an old instance type, be sure to check out the
reserved instance marketplace. You can find bargains, if you’re a
buyer of Heavy Usage instance types.

Looking for the lowest Effective Rate with a relatively short term
will bridge any gaps you have between your first generation instances
and your move to the new generations.

Also, don’t limit yourself to your preferred Availability Zone
(AZ). Look at the region within your instance class and you’ll likely
find better pricing. For example, you may be looking for c1.medium in
us-east-1c but notice c1.xlarge available in us-east-1e. Once you
purchase the RIs you can modify them in the AWS EC2 console and
convert 1 c1.xlarge to 4 c1. Medium. Just remember to move them to
your proper AZ. It may take up to an hour for the transaction to go
through to then allow you to move the RI. That hour could be a good
time to shop for more bargains in other regions or your favorite
shopping site!

<hr>
![Dr. Zim]({{ site.baseurl }}/public/images/2014/07/pete-z.jpg)
Pete Zimmerman is Vice President of Services. Pete is responsible for delivering the world class, high availability and superior customer satisfaction that Sonian’s customers and partners expect. He joined Sonian as one of the company’s first employees, bringing more than 10 years experience in SaaS-based messaging and collaboration solutions.
