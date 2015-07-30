## Data disclosure

By default, Linkurious discloses all the properties of nodes and edges. We may prevent specific nodes or relationship properties to be accessed by Linkurious. Undisclosed data properties cannot be reached by Linkurious users nor be indexed by the search engine.

### Edit disclosed properties

Open the data management dashboard, then scroll down to the **Disclosure** section. The list of undisclosed properties is on the left side of the screen. The list of disclosed properties is on the right side of the screen. Move properties from one list to the other to change their status.

For instance, we want to avoid users to access the `category` property of nodes.

![disclosed-properties](https://raw.githubusercontent.com/Linkurious/linkurious-enterprise-manual/master/screenshots/155.png)

Select the `category` property and click on the left arrow to move it to the list of undisclosed properties. Click on the **Apply** button. The `category` property will not show up in visualizations anymore, even on existing visualizations. 

Do the same for edge properties.

<div class="alert alert-warning">
  Reindex data once undisclosed properties are configured to remove them from search results.
</div>
