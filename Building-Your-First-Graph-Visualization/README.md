# Build your first graph visualization

In this chapter, we will learn the basics of how to explore and visualize a graph database with Linkurious.

### About the dataset

This section of the manual and the following chapters are based on a dataset coming from [Crunchbase](http://www.crunchbase.com/). Crunchbase is a popular website that tracks the start-up ecosystem, especially companies and investors.

We have used Crunchbase to create a graph database of approximatively 75 000 nodes and 250 000 edges. From this we have then created a subset of to focus on French companies only. It contains 1855 nodes and 3566 relationships. This graph contains 4 types of nodes:
* cities
* companies
* investors
* markets

Companies and investors are linked to cities by the `HAS_CITY` relationship. Companies are linked to each other by the `ACQUIRED` relationship. Investors and companies are linked to each other by the `INVESTED_IN` relationship. Companies are linked to markets by the `HAS_MARKET` relationship.

In order to follow this manual, we suggest you to [download and install the dataset](http://linkurio.us/public/crunchbase-fr.db.zip).
Extract the archive and put its content in the folder `[YOUR_NEO4J_FOLDER]/data/graph.db`.
