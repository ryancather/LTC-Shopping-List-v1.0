# Model View Controller

The Model View Controller (MVC) design pattern attempts to split up the View (what the user can see) and the data (the model) by implementing a Controller class to manage the flow of information. The main idea is that the View should never talk directly to the Model and vice-versa. 

This allows for the model or the view to be updated without affecting the other. You may have to make changes to the Controller to reflect the changes, but in a more controlled fashion.

You will be following the MVC design in this tutorial by creating a number of Views and associated View Controllers and a single Model class to contain all the data that will be displayed.

![][3]

[3]: images/ltc-shopping-order-v1/model-view-controller.png