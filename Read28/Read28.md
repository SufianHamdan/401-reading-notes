# Read: 28 - RecyclerView

**Create dynamic lists with RecyclerView**
  * RecyclerView makes it easy to efficiently display large sets of data. You supply the data and define how each item looks, and the RecyclerView library dynamically creates the elements when they're needed.
  * RecyclerView recycles those individual elements, and is also the name of the library. When an item scrolls off the screen, RecyclerView doesn't destroy its view. Instead, RecyclerView reuses the view for new items that have scrolled onscreen. This vastly improves performance, improving your app's responsiveness, and reducing power consumption.
  * Key classes: 
    - RecyclerView - the ViewGroup that contains the views corresponding to your data. 
    -  RecyclerView.ViewHolder - Each individual element in the list is defined by a view holder object, and after the view holder is created, the RecyclerView binds it to its data. 
    -  RecyclerView.Adapter - RecyclerView requests those views, and binds the views to their data, by calling methods in the adapter. 
    -  LayoutManager - arranges the individual elements in your list. 
  * Plan your layout:
    - Items in your RecyclerView are arranged by a LayoutManager class. The RecyclerView library provides three layout managers:
      * LinearLayoutManager arranges the items in a one-dimensional list
      * GridLayoutManager arranges all items in a two-dimensional grid
      * StaggeredGridLayoutManager is similar to GridLayoutManager, but it does not require that items in a row have the same height or items in the same column have the same width. The result is that the items in a row or column can end up offset from each other.
  * Implementing your adapter and view holder:
    - Adapter and ViewHolder classes work together to define how your data is displayed.
    - The ViewHolder is a wrapper around a View that contains the layout for an individual item in the list.
    - The Adapter creates ViewHolder objects as needed, and also sets the data for those views. 
    - When you define your adapter, you need to override three key methods: 
      * onCreateViewHolder() - RecyclerView calls this method whenever it needs to create a new ViewHolder. 
      * onBindViewHolder() - RecyclerView calls this method to associate a ViewHolder with data. 
      * getItemCount() - RecyclerView calls this method to get the size of the data set. 