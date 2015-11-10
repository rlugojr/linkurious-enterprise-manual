## Search on multiple properties

You are looking for a specific node or relationship and the search bar gives you too many results? The text you are searching is too common! 
You may want to narrow you search by searching on multiple properties.

Searching a startup that has the text ```facebook``` on any of his properties gives us 88 matches. Let's try to narrow it down.

![](Facebook_Example.png)

We click on the  ```Advanced``` icon, a new menu appears:

![](Advanced_Search.png)

We can see the name of the different categories in our database and their occurences.
We hit ```Options``` to see the name of the different properties in our graph.

![the search on multiple properties](https://dl.dropboxusercontent.com/s/bog5w0tdm64ukic/71.png?dl=0)

In our graph, Facebook has the label ```Company```. We are going to select ```Company``` to restrict our search to the nodes that have the label ```Company```.

We can now see the different possible properties associated with the nodes with the ```Company``` label.

![the company label](https://dl.dropboxusercontent.com/s/wtkhoy7drk1y7ri/72.png?dl=0)

In our graph, a ```Company``` can have properties like  ```category ```,  ```city ``` or  ```first_funding_at ```. Not all the nodes with the ```Company``` label will have **all** the properties though.

In order to narrow down our results, we are going to search on multiple properties at once. To find Facebook, we are going to look for a company that uses facebook.com as its home page url and is located in Menlo Park.

![multi properties search](https://dl.dropboxusercontent.com/s/ypa7vhlid87sblf/73.png?dl=0)

Now when we type ``facebook``, the results are filtered to show only the nodes that have the label ```Company``` and the value ``facebook.com`` for the property ```homepage_url```.

![multi properties search](https://dl.dropboxusercontent.com/s/oc1zcemb7le2753/74.png?dl=0)

We can see that the results are now filtered. We simply click on the result we are interested in.

The same approach can be applied to the search of edges.

> Linkurious Enterprise will look for **exact** matches for the values you enter in the search options menu.
