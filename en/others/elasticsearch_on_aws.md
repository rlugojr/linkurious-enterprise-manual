# Elasticsearch on AWS

By default, Linkurious ships with an embedded Elasticsearch instance which works out-of-the-box by default. The embedded Elasticsearch instance will work well for average to large database sizes, but for search-heavy use-cases or very large databases, configuring [your own ElasticSearch cluster](https://www.elastic.co/products/elasticsearch) might be necessary.

An easy way to deploy an easy-to-scale Elasticsearch cluster yourself is to use [Amazon Web Services](https://aws.amazon.com/) (AWS).

Please follow these steps to create a configure your AWS Elasticsearch cluster with Linkurious.

#### 1. Create your AWS account
Visit the [Amazon Web Services website](https://aws.amazon.com/) and create your account (or log in if you already have one).

#### 2. Create a new cluster
Visit the [Amazon Elasticsearch Service page](https://aws.amazon.com/elasticsearch-service/), log-in and follow the steps to create an Elasticsearch cluster:

##### a. Select "services" > "Elasticsearch Service"
![](ASW-ES-1.png)
<hr>
##### b. Hit "get started"
![](AWS-ES-2.png)
<hr>
##### c. Name your cluster <span style="color:red">`(1)`</span> and select the Elasticsearch version 2.x <span style="color:red">`(2)`</span>, hit "Next"
![](AWS-ES-3.png)
<hr>
##### d. Select the instance type, number of instances and number of dedicated masters in your cluster <span style="color:red">`(3)`</span>, depending on your database's size.
![](AWS-ES-4.png)
<hr>
##### e. Configure the access policy for your cluster. Use "access from specific IP" <span style="color:red">`(4)`</span> and enter the public IP address of your Linkurious server <span style="color:red">`(5)`</span> 
![](AWS-ES-5.png)
<hr>
##### f. Review your configuration and confirm the creation of the cluster.
![](AWS-ES-6.png)
<hr>
