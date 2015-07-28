# Build your first graph visualization

In this chapter, we will learn the basics of how to explore and visualize a graph with Linkurious Enterprise.

### About the dataset

This section of the manual and the following chapters are based on a dataset coming from [Crunchbase](http://www.crunchbase.com/). Crunchbase is a popular website that tracks the start-up ecosystem, especially the start-ups and the investors.

We have used Crunchbase to create a graph of approximatively 75 000 nodes and and 250 000 edges. We have then created a subset of the graph to focus on French companies only. It contains 1855 nodes and 3566 relationships. That graph countains four types of entities :
* cities;
* companies;
* investors;
* markets.

Companies and investors are linked to cities by the **HAS_CITY** relationship.

Companies are linked to each other by the **ACQUIRED** relationship.

Investors and companies are linked to each other by the **INVESTED_IN** relationship.

Companies are linked to markets by the **HAS_MARKET** relationship.

In order to follow the manual, we suggest you to [download and install this dataset](http://linkurio.us/public/crunchbase-fr.db.zip).
Extract the downloaded archive and put its content in ```[YOUR_NEO4J_FOLDER]/data/graph.db```.
