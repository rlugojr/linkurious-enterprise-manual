# Build Your First Graph Visualization

In this chapter, we'll learn the basics of how to explore and visualize a graph with Linkurious Enterprise.

## About the dataset

This section of the manual and the following chapters are based on a dataset coming from [Crunchbase](http://www.crunchbase.com/). Crunchbase is a popular website that tracks the start-up ecosystem, especially the start-ups and the investors.

We have used Crunchbase to create a graph of approximatively 75 000 nodes and and 250 000 edges. That graph countains three types of entities :
* cities ;
* companies ;
* investors.

Companies and investors can be linked to cities by the ```HAS_CITY``` relationship.

Companies can be linked to each other by the ```ACQUIRED``` relationship.

Investors and companies can be linked to each other by the ```INVESTED_IN``` relationship.

In order to follow the manual, we suggest you download and install the dataset.

Simply grab the file below and put its content in ```[YOUR_NEO4J_FOLDER]/data/graph.db```.
