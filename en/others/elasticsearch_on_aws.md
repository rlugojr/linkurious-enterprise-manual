# ElasticSearch on AWS

By default, Linkurious ships with an embedded ElasticSearch instance which works out-of-the-box by default. The embedded ElasticSearch instance will work well for average to large database sizes, but for search-heavy use-cases or very large databases, configuring [your own ElasticSearch cluster](https://www.elastic.co/products/elasticsearch) might be necessary.

An easy way to deploy an easy-to-scale ElasticSearch cluster yourself is to use [Amazon Web Services](https://aws.amazon.com/) (AWS).

Please follow these steps to create a configure your AWS ElasticSearch cluster with Linkurious.

#### 1. Create your AWS account
Visit the [Amazon Elasticsearch Service page](https://aws.amazon.com/elasticsearch-service/) and hit the "sign-up" button. Follow the steps to create your account.

#### 2. Create your new cluster

