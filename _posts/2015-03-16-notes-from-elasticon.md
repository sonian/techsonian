---
layout: post
title: Notes from Elastic{ON}
categories: [Open source projects, Sonian Technology]
authors: [Dan Dillinger, Ian Truslove]
---

By [Dan Dillinger](https://twitter.com/yazirian),
[Ian Truslove](https://twitter.com/iantruslove)

![Sonian ❤ ES]({{ site.baseurl }}/public/images/2015/03/sonian-heart-es.png)

Last week, [Elastic](http://www.elastic.co/) (née Elasticsearch) held
their first ever user conference
[Elastic{ON}](http://www.elasticon.com/)15 in San Francisco, and we
were lucky enough to attend. Sonian uses Elasticsearch as one of our
core architectural technologies, indexing upwards of 17 million
documents per day; we were keen to hear and learn as much
Elasticsearch goodness as we could.

The overarching theme from ElasticON was the rebranding: it is not
just Elasticsearch anymore. The ELK stack ([Elasticsearch][es],
[Logstash][logstash], [Kibana][kibana]) received lots of coverage,
both the products’ new features individually and also their integrated
use. Using Kibana to rapidly generate data visualizations of
Elasticsearch queries and aggregation results is definitely a powerful
tool, and the change to [D3.js][d3] for chart rendering will make product
integration simple.

[es]: https://www.elastic.co/products/elasticsearch
[logstash]: https://www.elastic.co/products/logstash
[kibana]: https://www.elastic.co/products/kibana
[d3]: http://d3js.org/

[Aggregations](http://www.elastic.co/guide/en/elasticsearch/reference/current/search-aggregations.html)
also received decent coverage at the conference. This, plus mentions
of other upcoming features such as reducers and performance
optimization work with doc values seems to indicate that
Elasticsearch’s analytics capabilities are squarely in the development
team’s focus.

Another analytics tool from Elastic is the
[Elasticsearch Hadoop](https://www.elastic.co/products/hadoop). Currently
supporting [Pig](http://pig.apache.org/),
[Hive](https://hive.apache.org/),
[Cascading](http://www.cascading.org/),
[Spark](https://spark.apache.org/) and
[Storm](https://storm.apache.org/), and with various other
improvements coming, this is already a powerful tool to use to
interoperate with data in HDFS, or to use Hadoop processing
technologies on data held in Elasticsearch.

One notable deprecation for Sonian is that of
[facets](http://www.elastic.co/guide/en/elasticsearch/reference/current/search-facets.html).
Aggregations are the replacement for facets, and the facets API is
marked for removal in a future release. Since aggregations can be
composed, nested, and are clearly under active development, migrating
from facets to aggregations will only expose benefits.

A particularly exciting point of interest for an archiving company
like Sonian has been the introduction and subsequent leaps of progress
around [doc values][] a promising new tool to keep the heap usage of a
cluster in check while still providing flexible and performant access
to field data. We’re very excited to see what we’ll be able to do with
both the clusters we run today, and the new demands of our upcoming
products, when we begin to add doc value definitions to our mappings.

[doc values]: http://www.elastic.co/guide/en/elasticsearch/guide/current/doc-values.html

If Elasticsearch, Lucene, or text analytics at scale is of interest to
you, Sonian has some
[new job openings](http://sonian.com/about/careers/). Please check
them out!
