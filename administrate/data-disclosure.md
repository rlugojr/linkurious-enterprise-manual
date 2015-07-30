## Data disclosure

By default, Linkurious discloses all the properties of nodes and edges. We may prevent specific nodes or relationship properties to be accessed by Linkurious. Undisclosed data properties cannot be reached by Linkurious users nor be indexed by the search engine.

### Edit disclosed properties

Open the data management dashboard, then scroll down to the **Disclosure** section. Undisclosed properties are listed on the left side of the screen. Disclosed properties are listed on the right side of the screen. Move properties from one list to the other to change their status.

![disclosed-properties](https://raw.githubusercontent.com/Linkurious/linkurious-enterprise-manual/master/screenshots/155.png)

For instance, we want to avoid users to access the `category` property of nodes. Select the `category` property and click on the left arrow to move it to the list of undisclosed properties. Click on the **Apply** button. The `category` property will not show up in visualizations anymore, even on existing visualizations. 

Do the same for edge properties.

<div class="alert alert-warning">
  Reindex data once the undisclosed properties are configured in order to remove them from search results.
</div>
