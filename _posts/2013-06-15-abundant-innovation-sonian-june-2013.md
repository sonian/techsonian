---
layout: post
title: "Abundant Innovation @Sonian: June 2013"
category: The Sonian Way
description: ""
author: Greg Arnette
---

I was honored to witness the creativity of the @sonian product
development team at our June 2013 All-Team Meet-up. Our tradition the
past five years is to hold a 24-hour Codefest where teams
self-organize to work on a project they feel passionate about. Nearly
all of these passion pursuits benefit Sonian in some way. I’m a lucky
CTO / Founder!

For this meet-up 31 people across 9 teams created projects that will
help Sonian save money or wow customers with new features. Awards were
issued in two categories; Sizzle and Steak. Sizzle for a new
customer-facing feature and Steak for an improvement in the
behind-the-scenes platform. Each project is highlighted below in their
presentation order.

Team: Big Brother (Winner: Sizzle Category)<br>
Project: All your IM are Belongs to us<br>
Vikram, Joel and Arnaud teamed up on a project demonstrating the
capability to capture IM conversations using a proxy between the IM
client and the server. Their implementation captures all
conversations, encrypted or not, for compliance and data mining
purposes. This is an important requirement for organizations subjected
to regulatory information retention obligations. The data collection
is invisible to the end user because there is no software to
install. A few issues still need to be resolved such as SSL
certificate management and how to capture mobile device IM
conversations. Archiving and analyzing IM data is especially important
for the financial sector and other regulated industries.

Team: House of Targaryen<br>
Project: Making Developers Happy<br>
Alan, Josh, Scott and Ubiratan worked on a project to show how
Continuous Integration (CI) techniques can improve quality by finding
defects faster. This project demonstrated running tests as code is
checked into source control. CI automated processes identify problems
before the QA team begins their work, alerting the developer quickly
before too much time passes. This project can be rolled into
production with just a few more days of work.

Team: Facts and Fun<br>
Project: Data Analysis for Fun and Profit (and Fun)<br>
David, Raj, Steve and Robert demonstrated a new data management
technology with a specialty to manage information that slowly changes
over time. This is especially important for new features Sonian plans
to roll out later this year. The practical application is useful for
snapshotting corporate directory, email folder coordination and many
other use cases. This is also a general support system for data
visualizations, meta data, etc. and compliments the use of
ElasticSearch. An added bonus is lower operating costs for cloud
infrastructure expenses.

Team: @FootRest<br>
Project: PageStor<br>
Chitro showed how a web browser plug-in could be used to archive and
share page URLS. The plugin, combined with a future platform API,
would allow anyone to develop a simple recipe to archive the entire
page, the link, or sections. PageStor shows the possibility of
expanding the data type and collection endpoints (plug-ins!) for any
type of information to be retained in Sonian.

Team: Unicron<br>
Project: Galvatron<br>
Craig, Dan, and Joe collaborated on a cluster status dashboard to
display health, activity and workload information. Previously log file
scouring and queue monitoring was the only way to get visibility into
cluster activity. The Ops team will get valuable insights into jobs
such as packing & indexing. In the future the visual information is
useful to show customer IT administrators how their data progresses
through the pipeline.

Team: Super Friends (the audience favorite)<br>
Project: All your email are belong to us<br>
Daniel, Pete, Matt, Justin and Kevin created an impressive
demonstration of a full turn-key data migration service from
competitors hosted archives. This new capability allows a customer or
partner self-service data migration from their old repository to
Sonian. This project also added a new import component, S/SFTP which
will be valuable in and of itself for many other data import uses.

Team: Eat Not the Bread of Idleness (Winner: Steak Category)<br>
Project: Utilizing idle EC2 capacity for productive purpose<br>
Lee and Paul paired up for some creative problem solving; What to do
with excess cluster capacity? Perform work! The heart of Sonian’s data
processing pipeline is a technology called SAFE. It’s a cluster of
virtual compute nodes that perform all the data handling (encryption,
compression, exporting, etc.) tasks. SAFE was designed to use reserved
and spot EC2 nodes. Most of the time the cluster is busy, but
sometimes there are nodes loafing with spare capacity. This project
demonstrated task management to parcel work to idle nodes, or nodes
with spare capacity. This technique will have broad impact across the
back-end as it helps maximize virtual machine utilization.

Team: Dial Tone<br>
Project: Indexing of phone call recording/dictation<br>
Kevin, Matt and Mike joined forces with a fantastic demonstration
capturing live phone call recordings and indexing the speech to text
of the phone call. The proof of concept was fully implemented
including a live call captured, speech to text conversion, and
subsequent search on the text in the native Sonian user
interface. Voice file processing is an important new capability Sonian
plans to introduce in the future. Processing voice files fits nicely
into the Sonian workflow because of the work already completed with
multi-stage data handling and the ability to add new stages to the
pipeline process.

Team: That Thing That Jenn Wants<br>
Project: Mobile partner/sales-rep app for quick access to common tasks<br>
Randall, Rick, Peter, Gopal, Dan and Andrea represented most of the QA
team and created a stunning demonstration of a live iOS app allowing
salespeople to create and manage accounts. The mobile app could also
be used to allow OEM partners to display pipeline status, manage
renewals.
