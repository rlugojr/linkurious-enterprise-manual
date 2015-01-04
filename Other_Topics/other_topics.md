# Other Topics

## Indexation

The graph database is automatically indexed on startup at the moment, you can edit this setting in linkurious/config/production.js.

Change ```force_reindex: true``` to ```force_reindex: false```.

## Requirements

Windows, Linux or Mac OS

64 bits system

Java 8u25 **and the JAVA_HOME environment variable set up** ([see how to do it on Windows](http://help.virtocommerce.com/support/discussions/topics/38969))

Neo4j 1.9.5+ or 2.x with a small database of less than 200k nodes and relationships

Internet Explorer 10, Firefox 15, Chrome 23, Safari 6, and Opera 12.

## Reportings bugs

This early version is released for **beta testing**, so please experiment with these features and report bugs at support@linkurio.us (it will open a thread on [Freshdesk](http://freshdesk.com/)).

Reported bugs will be fixed progressively.

## Importing data

Linkurious relies on Neo4j to store the data. The data importation is thus not handled by our solution. If you want to import data to Neo4j, you have those solutions:

* there is a Gephi plugin that lets you export any file compatible with Gephi to Neo4j ([list of compatible formats](https://gephi.org/users/supported-graph-formats/))

* if you can handle a spreadsheet, you can [easily](http://blog.neo4j.org/2013/03/importing-data-into-neo4j-spreadsheet.html) import csv formated data

* for the more tech savvy there are even more option ([Batch importer](https://github.com/jexp/batch-import), [Talend connector](https://github.com/Zenika/talend-neo4j-connector))

* if you want to get help from professionals, we can get you in touch with great people.

* If you are still not sure about whether you can get your data in Linkurious contact us, we’ll be happy to answer if you contact us.
*

Finally, if you want to quickly try to use Linkurious Enterprise with dummy data, you can download a [Neo4j compatible dataset](http://neo4j.com/developer/guide-example-data/).

## Overall architecture

![architecture](http://linkurio.us/wp-content/uploads/2012/12/Linkurious-architecture.png)

Linkurious is the sum of two components: the frontend, running in the web browser and providing the user interface, and the backend, server component connected to the graph database. The backend provides a fast search engine and runs on any system able to support node.js, including Windows, Linux and Mac OS.

While we ship a lightweight search engine fully running in memory, it can easily be switched to another engine such as Apache Lucene. The graph database can be located on the same machine as the backend or on any other machine in your network.

## Technology

Below is a list of the open source technologies we use. They have proven to be efficient and reliable:

* [Angular.js](https://angularjs.org/)
* [Sigma.js](http://sigmajs.org/)
* [ElasticSearch](http://www.elasticsearch.org/)
* [Node.js](http://nodejs.org/)

## Choose The Text Of The Nodes And Edges

Linkurious Enterprise lets you choose which of the properties of your graph should be used displayed on the canvas.

In order to customize this, we need to open the design panel on the right.

![](https://dl.dropboxusercontent.com/s/j9emxs72jlrkfn7/90.png?dl=0)

Right now Linkurious Enterprise displays the ```name``` of the nodes. Now let's go to the ```Toolstips``` tab. Here we can see the different properties of the nodes in our graph. The ```name``` property is first. In the bottom of the screen, it is possible to select the relationships.

![](https://dl.dropboxusercontent.com/s/h5vbkg2krgsbmh6/91.png?dl=0)

We want to show the ```city``` in the visualization. To do it, we simply drag ```city``` on the top of the list.

![](https://dl.dropboxusercontent.com/s/nvupr705s3on8g6/92.png?dl=0)

Now the text displayed next to your node changes. Instead of looking at ```Linkfluence``` we are looking at ```Saint-denis-sur-loire```.

![](https://dl.dropboxusercontent.com/s/0ew4ynw9m0bidna/93.png?dl=0)

The same approach can be used for the relationships.

> Linkurious Enterprise will try to use the properties at the top of the list. If a node doesn't have that property, Linkurious Enterprise will look for the next property, etc.

## Customize The Tooltip

When you right-click on a node or an edges, you can view its properties in a pop-up menu called a tooltip.

![](https://dl.dropboxusercontent.com/s/zp1nhk2rhbo04o0/94.png?dl=0)

We can see that our node is a ```Company``` which ```name``` is ```Linkfluence```.

It is possible to customize the content of the tooltip and display only certain properties.

In order to customize this, we need to open the design panel on the right.

![](https://dl.dropboxusercontent.com/s/j9emxs72jlrkfn7/90.png?dl=0)

Now let's go to the ```Toolstips``` tab. Here we can see the different properties of the nodes in our graph. By default all the properties are ```on``` and are thus displayed. In the bottom of the screen, it is possible to select the relationships.

![](https://dl.dropboxusercontent.com/s/h5vbkg2krgsbmh6/91.png?dl=0)

Simply turn off the properties you do not want to display. Here we are going to turn off the ```name``` and ```url```.

![](https://dl.dropboxusercontent.com/s/1sm9j6hw14nqv9u/95.png?dl=0)

When we right-click on our node again, the  ```url ``` and  ```name ``` are removed from the tooltip.

![](https://dl.dropboxusercontent.com/s/wdevhqcx2gbxi8u/96.png?dl=0)
