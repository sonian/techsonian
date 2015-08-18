---
layout: post
title: Evaluating Microsoft Azure Machine Learning as a Service
category: Sonian Technology
author: Murilo Pereira
---

## Introduction

Microsoft Azure Machine Learning (MAML) provides several machine
learning (ML), statistics and data pipeline constructs through a
drag-and-drop visual interface. It allows users to ingest, transform,
and visualize data, which can be used train models. MAML also provides
ML helpers like feature selection, feature normalization, mean
normalization, cross-validation, model evaluation and scoring.

With regard to text analytics tools, it includes feature hashing and
named entity recognition (NER). The available NER outputs people,
locations, and organizations.

## How easy is the API to work with?

MAML doesn’t have APIs per-se. Rather, it allows users to publish ML
models and data transformations as web services through a REST API
with a single click.

Regarding the easiness of the MAML web interface, it works mostly by drag-and-dropping “modules” (read from database, transform, train model, write to database), which can be viewed as discrete units of computation. The entire data pipeline can be constructed using it.

## Thoughts on API documentation and clarity

Microsoft clearly put a lot of effort on documentation. Help links are
available everywhere and contain useful prose and specifications.

## Is Azure ML useful for analyzing email?

MAML has “Reader” and “Writer” modules: “Reader”s allows
table-formatted data (e.g. CSV) to be ingested from HTTP services or
proprietary Azure services like Azure SQL and Azure Blob Storage. So
setting up a ML service for email would entail:

* Creating a “Reader” that ingests data from our servers
* Doing data transformations (or not if we do that already)
* Training a model
* Publishing an HTTP web service to be used by our servers (i.e. analyzer)

The kind of models we could train are numerous:

* Email categorization (personal message, announcement, etc.)
* Sentiment analysis
* Spam detection

It would be useful to think about this top-down: what do customers want and how can we use ML to give it to them.

## Overall impressions

* MAML is still in preview, so it has some rough edges. While running
  models I’ve seen several cryptic error messages which didn’t help me
  resolve the issue. There was also some UI glitches.
* “Experiments” created on MAML are effectively outside our
  control. We wouldn’t be able to reuse any functionality if we wanted
  to stop using Azure. In contrast,
  [Databricks Cloud](https://databricks.com/cloud/) (a similar product
  built on top of Apache Spark) gives more control to users:
  experiment steps are defined with actual code and could be extracted
  out of Databricks Cloud to be run on our own servers if we wanted
  to.
* The “outside our control” characteristic also seems to imply that we
  have little say over the actual compute and memory resources used to
  train and run models, meaning we can choose the size or power of
  clusters. (I’m still going over the features, maybe there’s a way to
  do this).
* I really liked how MAML allows users to seamlessly exchange between
  different ML algorithms (MAML modules, e.g. logistic regression,
  neural networks, support vector machines) in experiments. The
  configurability is also very useful. These characteristics allows
  for quick experimentation and tuning when building models.
* The functionality is available entirely through a visual UI, which
  constraints how users build their pipelines and services to the use
  and edge cases imagined by Microsoft. I’ve found difficulty in
  building pipelines published as web services because I had to learn
  how to combine “modules” and make them work with options that don’t
  seem to appear in the interface. An optional interface where it
  allowed more flexibility (code) would’ve been nice.

MAML feels like a very well done product with a huge number of future application appeal.

## Cost

Bearing in mind this is the preview pricing model, it seems relatively
attractive. There are two fees, the per-hour active compute and a
per-web-service API call fee, both prorated. Per-hour fee is lower
whilst you are using ML Studio ($0.38/hour) and a little higher when
in production via ML API Service ($0.75/hour). The per-API calls are
free while in ML Studio and cost $0.18/1000 predictions while in
production.

## Sources

[Training a Neural Network with Azure Machine Learning (video)](http://youtu.be/GPXvtoIAbOg)
[Azure ML: A Brief Introduction](https://projectbotticelli.com/knowledge/brief-introduction-to-microsoft-azure-ml)
