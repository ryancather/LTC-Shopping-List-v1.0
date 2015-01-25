# Configuring the User Interfaces

Currently, the View is set up completely empty. You will need to create a new navigation controller and two views. One which will ask the user for their name and one that will display and collect the shopping list items.

To conform with the Model-View-Controller design structure, each of these two views will have a corresponding code file.

![][7]

[7]: images/ltc-shopping-order-v1/configuring-the-user-interfaces.png

## 4.1 Create the Navigation Controller

Open the Main.storyboard file.

Select and Delete the existing View. 

From the Object Library (bottom right), find and drag out the Navigation Controller object.

![][8]

[8]: images/ltc-shopping-order-v1/create-the-navigation-controller.png

## 4.2 Set the Navigation Controller to be the Initial View Controller

As you've deleted the existing one and recreated the Views, you'll need to tell Xcode which view to load first. In this case the first view will be the Navigation Controller.

Select the Navigation Controller in the Document Outline and then under the Attributes Inspector, make sure the "Is Initial View Controller" option is ticked.

![][9]

[9]: images/ltc-shopping-order-v1/set-the-navigation-controller-to-be-the-initial-view-controller.png

## 4.3 Create new View Controller

From the Object Library, drag out a View Controller. This will be the view that will collect the users name and load the second view.

![][10]

[10]: images/ltc-shopping-order-v1/create-new-view-controller.png

## 4.4 Link the Navigation Controller to the new View

Hold down the Control button and click and drag from the Navigation Controller to the new View Controller. When the menu appears, choose Root View controller. 

![][11]

[11]: images/ltc-shopping-order-v1/link-the-navigation-controller-to-the-new-view.png

## 4.5 Create the Username View 

This new view will be called the UserName View. You'll create the View Controller for it in a later step, but first organise the layout for the information that needs to be displayed and collected. Luckily this is a simple view with it's purpose only to collect the users name.

This name is only used for when the user exports their list, then a name can be associated with that order. This will allow the teacher to be able to identify who ordered what items.

Using the Object Library, drag out a label, a text field and a button. 

Double Click on the label and change the text to "Please enter your name to begin ordering". 

Double Click on the button and change the label to "Begin Ordering"

Single Click the Text Field and under the Attributes Inspector, change the placeholder text to "Enter Name here"

![][12]

[12]: images/ltc-shopping-order-v1/create-the-username-view-.png

## 4.6 Create Segue

Hold down the control key and click and drag from the "Begin Ordering" button to the remaining View. 

This view will have "Prototype Cells" appearing as a heading. In the menu that appears choose "Show". This creates a segue between the two views.

![][13]

[13]: images/ltc-shopping-order-v1/create-segue.png

## 4.7 Uniquely identify the segue

So that you can refer to this particular segue in code later, you will have to give this segue a unique identifer.

Select the segue and under the Attribute Inspector, set the Identifier field to "ordering"

![][14]

[14]: images/ltc-shopping-order-v1/uniquely-identify-the-segue.png

## 4.8 Select the View Controller

Look on the left in the Document Outline for the View Controller Scene. Select the View Controller in that list. You should notice that the view outline is now highlight blue.

![][15]

[15]: images/ltc-shopping-order-v1/select-the-view-controller.png

## 4.9 Associate the View to the UserNameViewController.swift file

On the right under the Identity Inspector, the class option has defaulted to "UIViewController". You will need to change that to UserNameViewController.

This now will allow you to write code specifically for this view. This will be done in later steps.

![][16]

[16]: images/ltc-shopping-order-v1/associate-the-view-to-the-usernameviewcontrollerswift-file.png

## 4.10 Configure the Shopping List View

Back in Main.storyboard, select the Root View Controller Scene in the Document Outline on the left of the window. You should see the outline of the view highlighted in blue.

Under the Identity Inspector on the right change the class to ShoppingListViewController.

![][17]

[17]: images/ltc-shopping-order-v1/configure-the-shopping-list-view.png

## 4.11 Configure the Prototype Cells

Now that the Views are associated with the correct View Controllers, it is finally time to configure the cells that will display the information to the user. The majority of the work is done in code, but you will need to change a few settings on the cell to allow for all the information to display.

In the Document Outline, expand the options until you see Table View Cell. Select that.

![][18]

[18]: images/ltc-shopping-order-v1/configure-the-prototype-cells.png

## 4.12 Set the style to Right Detail

Now that the cell has been displayed, look in the Identity Inspector for the style option. Change it to "Right Detail".

That's all that is needed to configure the cells to be displayed.

![][19]

[19]: images/ltc-shopping-order-v1/set-the-style-to-right-detail.png

## 4.13 Change the Title

Almost there.

Change the heading of the view from the unimaginatively named "Root View Controller" to "LTC Shopping List" by double clicking on the Title in the View.

![][20]

[20]: images/ltc-shopping-order-v1/change-the-title.png

## 4.14 Include buttons on the header

The last configuration that is needed on the View is to include two buttons; one for exporting the data and another for reseting the data.

Choose "Bar Button Item" from the Object Library and drag one of them to the left of the heading "LTC Shopping List" and another to the right.

Double click on each button to change the name to Export and Reset.

![][21]

[21]: images/ltc-shopping-order-v1/include-buttons-on-the-header.png