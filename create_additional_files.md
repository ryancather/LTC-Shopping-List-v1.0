# Create Additional Files

Before you can start configuring the User Interfaces, there are a few additional files you need to create.

## 3.1 Create View Controller

Now that the View has been created, now you will need to create the View Controller to provide the background code for this view to work.

Go to File -> New -> File, and under iOS choose Swift File. When asked for the name of the file, enter "UserNameViewController". 

![][4]

[4]: images/ltc-shopping-order-v1/create-view-controller.png

## 3.2 Configure the View Controller

To allow the storyboard to "see" the View Controller as a View Controller, you need to announce that the swift file you've created is to be used as a View Controller.

Define the class name and have it inherit the UIViewController class.

Save the file.

![][5]

[5]: images/ltc-shopping-order-v1/configure-the-view-controller.png

## 3.3 Create a ShoppingListViewController.swift

It's now time to create the correct settings for the view for the items to be displayed and selected.

Start by creating a ShoppingListViewController.swift file, following the same process as for the UserNameViewController.swift file. Note that this class inherits from UITableViewController instead of UIViewController. This adds extra functionality specifically for use with tables.

Save the File.

![][6]

[6]: images/ltc-shopping-order-v1/create-a-shoppinglistviewcontrollerswift.png