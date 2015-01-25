#LTC Shopping List v1.0

The LTC Shopping List series of tutorials is designed to develop a working iOS app (for both iPhone and iPad) which allows users to choose ingredients for their recipes and submit their list to a central location for bulk purchasing. This is to satisfy the requirement for students at a school to select their ingredients and the teacher purchase the items for all students on a weekly basis.

The series of tutorials will develop the app in various stages, with each stage being a complete, working version.

The plan for the sequence of versions are as follows.

**Version 1** This version will focus on functionality, with a hard-coded ingredient list. At the end of the tutorial, the user will be able to select from a list of ingredients in a table and then email the list to their teacher.

This version will see the foundations of the app created, using the Model-View-Controller structure to set up the app for future development. The shopping list items will load into a TableView, broken up by categories/sections. This will be the structure to the app in subsequent versions.

**Version 2** The User Interface is improved in this version by customising the cells in the table to display more information efficiently. The initial welcome screen will also be updated, using Auto-Layout, to be displayed correctly on different screen sizes and orientations.

**Version 3** This version improves upon the storing of the ingredient list. Instead of hard-coding the list, the app will retrieve the latest version of the list from a webserver to display to the user. The images will also be downloaded, which will require the integration of Grand Central Dispatch to keep the interface responsive while the images are downloading.

**Version 4** This update will focus on the interface with introducing some more interactivity to the cells in the table.

**Version 5** The final version will change the way the selected ingredient list is submitted to the teacher. Rather than an email being sent, this version will update a central location with the students selection, and the teacher will be able to get a single total of all ingredients from all students.



## End Result

To give you a concept of what this version may look like after you complete this tutorial, here is the working version. The user can select items to order and email that to their teacher.

![][1]

[1]: images/ltc-shopping-order-v1/end-result.png

## Software Versions

This tutorial was written for and works with Xcode v6.1.1 and Swift v1.1. If you are coding this in later version of each, some modifications may be required.

## 1. Create a new Project

In Xcode 6, create a new iOS Single-View App, calling it "LTC Shopping List". Set the Language to be Swift and under Devices set it to be "Universal". This will allow you to design the User Interface for both the iPhone and iPad, which you will do in a later tutorial.



![][2]

[2]: images/ltc-shopping-order-v1/create-a-new-project.png

## 2. Model View Controller

The Model View Controller (MVC) design pattern attempts to split up the View (what the user can see) and the data (the model) by implementing a Controller class to manage the flow of information. The main idea is that the View should never talk directly to the Model and vice-versa. 

This allows for the model or the view to be updated without affecting the other. You may have to make changes to the Controller to reflect the changes, but in a more controlled fashion.

You will be following the MVC design in this tutorial by creating a number of Views and associated View Controllers and a single Model class to contain all the data that will be displayed.

![][3]

[3]: images/ltc-shopping-order-v1/model-view-controller.png

## 3. Create Additional Files

Before you can start configuring the User Interfaces, there are a few additional files you need to create.

### 3.1 Create View Controller

Now that the View has been created, now you will need to create the View Controller to provide the background code for this view to work.

Go to File -> New -> File, and under iOS choose Swift File. When asked for the name of the file, enter "UserNameViewController". 

![][4]

[4]: images/ltc-shopping-order-v1/create-view-controller.png

### 3.2 Configure the View Controller

To allow the storyboard to "see" the View Controller as a View Controller, you need to announce that the swift file you've created is to be used as a View Controller.

Define the class name and have it inherit the UIViewController class.

Save the file.

![][5]

[5]: images/ltc-shopping-order-v1/configure-the-view-controller.png

### 3.3 Create a ShoppingListViewController.swift

It's now time to create the correct settings for the view for the items to be displayed and selected.

Start by creating a ShoppingListViewController.swift file, following the same process as for the UserNameViewController.swift file. Note that this class inherits from UITableViewController instead of UIViewController. This adds extra functionality specifically for use with tables.

Save the File.

![][6]

[6]: images/ltc-shopping-order-v1/create-a-shoppinglistviewcontrollerswift.png

## 4. Configuring the User Interfaces

Currently, the View is set up completely empty. You will need to create a new navigation controller and two views. One which will ask the user for their name and one that will display and collect the shopping list items.

To conform with the Model-View-Controller design structure, each of these two views will have a corresponding code file.

![][7]

[7]: images/ltc-shopping-order-v1/configuring-the-user-interfaces.png

### 4.1 Create the Navigation Controller

Open the Main.storyboard file.

Select and Delete the existing View. 

From the Object Library (bottom right), find and drag out the Navigation Controller object.

![][8]

[8]: images/ltc-shopping-order-v1/create-the-navigation-controller.png

### 4.2 Set the Navigation Controller to be the Initial View Controller

As you've deleted the existing one and recreated the Views, you'll need to tell Xcode which view to load first. In this case the first view will be the Navigation Controller.

Select the Navigation Controller in the Document Outline and then under the Attributes Inspector, make sure the "Is Initial View Controller" option is ticked.

![][9]

[9]: images/ltc-shopping-order-v1/set-the-navigation-controller-to-be-the-initial-view-controller.png

### 4.3 Create new View Controller

From the Object Library, drag out a View Controller. This will be the view that will collect the users name and load the second view.

![][10]

[10]: images/ltc-shopping-order-v1/create-new-view-controller.png

### 4.4 Link the Navigation Controller to the new View

Hold down the Control button and click and drag from the Navigation Controller to the new View Controller. When the menu appears, choose Root View controller. 

![][11]

[11]: images/ltc-shopping-order-v1/link-the-navigation-controller-to-the-new-view.png

### 4.5 Create the Username View 

This new view will be called the UserName View. You'll create the View Controller for it in a later step, but first organise the layout for the information that needs to be displayed and collected. Luckily this is a simple view with it's purpose only to collect the users name.

This name is only used for when the user exports their list, then a name can be associated with that order. This will allow the teacher to be able to identify who ordered what items.

Using the Object Library, drag out a label, a text field and a button. 

Double Click on the label and change the text to "Please enter your name to begin ordering". 

Double Click on the button and change the label to "Begin Ordering"

Single Click the Text Field and under the Attributes Inspector, change the placeholder text to "Enter Name here"

![][12]

[12]: images/ltc-shopping-order-v1/create-the-username-view-.png

### 4.6 Create Segue

Hold down the control key and click and drag from the "Begin Ordering" button to the remaining View. 

This view will have "Prototype Cells" appearing as a heading. In the menu that appears choose "Show". This creates a segue between the two views.

![][13]

[13]: images/ltc-shopping-order-v1/create-segue.png

### 4.7 Uniquely identify the segue

So that you can refer to this particular segue in code later, you will have to give this segue a unique identifer.

Select the segue and under the Attribute Inspector, set the Identifier field to "ordering"

![][14]

[14]: images/ltc-shopping-order-v1/uniquely-identify-the-segue.png

### 4.8 Select the View Controller

Look on the left in the Document Outline for the View Controller Scene. Select the View Controller in that list. You should notice that the view outline is now highlight blue.

![][15]

[15]: images/ltc-shopping-order-v1/select-the-view-controller.png

### 4.9 Associate the View to the UserNameViewController.swift file

On the right under the Identity Inspector, the class option has defaulted to "UIViewController". You will need to change that to UserNameViewController.

This now will allow you to write code specifically for this view. This will be done in later steps.

![][16]

[16]: images/ltc-shopping-order-v1/associate-the-view-to-the-usernameviewcontrollerswift-file.png

### 4.10 Configure the Shopping List View

Back in Main.storyboard, select the Root View Controller Scene in the Document Outline on the left of the window. You should see the outline of the view highlighted in blue.

Under the Identity Inspector on the right change the class to ShoppingListViewController.

![][17]

[17]: images/ltc-shopping-order-v1/configure-the-shopping-list-view.png

### 4.11 Configure the Prototype Cells

Now that the Views are associated with the correct View Controllers, it is finally time to configure the cells that will display the information to the user. The majority of the work is done in code, but you will need to change a few settings on the cell to allow for all the information to display.

In the Document Outline, expand the options until you see Table View Cell. Select that.

![][18]

[18]: images/ltc-shopping-order-v1/configure-the-prototype-cells.png

### 4.12 Set the style to Right Detail

Now that the cell has been displayed, look in the Identity Inspector for the style option. Change it to "Right Detail".

That's all that is needed to configure the cells to be displayed.

![][19]

[19]: images/ltc-shopping-order-v1/set-the-style-to-right-detail.png

### 4.13 Change the Title

Almost there.

Change the heading of the view from the unimaginatively named "Root View Controller" to "LTC Shopping List" by double clicking on the Title in the View.

![][20]

[20]: images/ltc-shopping-order-v1/change-the-title.png

### 4.14 Include buttons on the header

The last configuration that is needed on the View is to include two buttons; one for exporting the data and another for reseting the data.

Choose "Bar Button Item" from the Object Library and drag one of them to the left of the heading "LTC Shopping List" and another to the right.

Double click on each button to change the name to Export and Reset.

![][21]

[21]: images/ltc-shopping-order-v1/include-buttons-on-the-header.png

## 5. Collecting the Users Name

In this section you will write the code so that when the user taps the button, the app collects the users name from Text Field and then displays the next view.

This View will also have a View Controller but no model, as you only need to collect the users name, a simple string.

### 5.1 Create the connection from UI Elements to code

Open the Main.storyboard.

Xcode has the ability to easily create connections between Views and the corresponding View Controllers. There are two main types of connections that you'll be creating; 

1) Action, is for when you want the code to do something when the user does something on screen.

2) Outlet, is for when you want to be able to access a UI element from within code.

Select the User Name View in the storyboard and click on the Assistant Editor button. You should now see both the View and the View Controller code on screen.

![][22]

[22]: images/ltc-shopping-order-v1/create-the-connection-from-ui-elements-to-code.png

### 5.2 Create Button Action

Now to create the function for when the user taps the Begin Ordering Button.

Control Click Drag from the Begin Ordering button to the View Controller.

![][23]

[23]: images/ltc-shopping-order-v1/create-button-action.png

### 5.3 Create the Action

In the menu that appears set the connection type to be Action and the name to be getUserName. Click Connection. 

This creates the IBAction function structure for you.

![][24]

[24]: images/ltc-shopping-order-v1/create-the-action.png

### 5.4 Give the Text Field a name

Perform the same steps for the Text View, except in this case, set the connection type to be Outlet and name it "userNameField".

Your project should now look like the following

![][25]

[25]: images/ltc-shopping-order-v1/give-the-text-field-a-name.png

### 5.5 Set up a UserName variable

Before writing the code for the function, set up a String variable to temporarily hold the users name. As this variable may or may not contain a value, it needs to be created as an Optional with the ? postfix.

![][26]

[26]: images/ltc-shopping-order-v1/set-up-a-username-variable.png

### 5.6 Write the getUserName() function

Now the string variable has been created and you've created the connections between the View and the code, you can now write the code for the getUserName() function to store the users name from the userNameField element.

![][27]

[27]: images/ltc-shopping-order-v1/write-the-getusername---function.png

### 5.7 Prepare for the Seque

So far, you've collected the users name and stored it into a variable, now you will need to write another function that will actually perform the segue - load the next view.

This method is overridden from the parent UIViewController class.

![][28]

[28]: images/ltc-shopping-order-v1/prepare-for-the-seque.png

### 5.8 Set up the Destination Variable

There's one last thing you have to do for this to work. You've set up the code so that the view will load, but you need to "send" the usersName variable to the next View Controller. You can do this by creating a variable in the ShoppingListViewController class and then store the usersName variable into that one.

Open the ShoppingListViewController.swift file and define an optional String variable named "currentUser". This variable will be used throughout the ShoppingListViewController class to access and use the Users name. This will become important when the user wants to finalise or export their order so that the recipient knows who ordered which items.

Note the ? postfix to indicate that the currentUser variable is an optional.

Save the file.

![][29]

[29]: images/ltc-shopping-order-v1/set-up-the-destination-variable.png

### 5.9 "Send" the users name

Back in the UserNameViewController class, change the prepareForSegue() function to set the newly created currentUser variable to be the usersName.

Note the ! after currentUser variable. This forces Xcode to extract the String out of the variable instead of treating it as an Optional.

That's all you need to do to store the name in the next View Controller. Save the file.

![][30]

[30]: images/ltc-shopping-order-v1/-send--the-users-name.png

### 5.10 Test that the name was received.

Just to make sure that the users name has been sent correctly, you can use the name to change the title of the view to include the users name.

In the ShoppingListViewController, implement the function viewDidLoad(). This is similar to the prepareForSegue() function previously, it is overridden from the superclass.

Note the ! after currentUser variable. This forces Xcode to extract the String out of the variable instead of treating it as an Optional.

Run the code and type in a name into the User Name Text Field and tap the Begin Ordering button. You should see your name appear as the title on the shopping list!

![][31]

[31]: images/ltc-shopping-order-v1/test-that-the-name-was-received.png

## 6. Defining the Model

So far, you've created two Views to display information to the user and two corresponding View Controllers. To conform to the Model-View-Controller (MVC) design pattern, you will now need to create a Model class in order to create the data that will be displayed by the Shopping List View Controller.

In this first Version, the Model class will be very static, and a lot of hard coding. This is just to demonstrate how to quickly and easily get data appearing in the table view. In later versions of the app, you will learn how to be more dynamic with creating the data to appear. One of the benefits to MVC is that you will be able to simply change the Model class to load the data and the View Controller and the View will not be aware (or care) of any changes. This makes it easier to update the app for later versions, as the code in the Model won't interact or interrupt with View Controllers.

![][32]

[32]: images/ltc-shopping-order-v1/defining-the-model.png

### 6.1 Create ShoppingItems.swift

Create a new iOS swift file (the same way as before) to create a new Swift file called "ShoppingListItems.swift". Create the following basic structure to the class.

![][33]

[33]: images/ltc-shopping-order-v1/create-shoppingitemsswift.png

### 6.2 Struct!

In order to structure your code a little, define an "Item" struct in the ShoppingListItems class which will contain the title, count, an increment value and a variable for an image.

The title of the item is simply the name. The count will be how much the user wishes to order (starting at 0). The Increment value will be how much the count will increase by when the user selects it in the list and the image will be an image of the product.

The Increment value is needed to make it easier for the user to change items that need to be ordered in different quantities. For instance, the user will want to select how many full chickens they want so this will increase by 1, but for the amount of butter, it doesn't make sense to order "1 Butter". So for items such as butter, the app will increment at a higher value to simulate the user choosing the amount of butter in grams.

![][34]

[34]: images/ltc-shopping-order-v1/struct-.png

### 6.3 Define an array

In order to store the full offerings of items, you will need to define an array of items.

This syntax may look strange, but you are creating a two dimensional array of items. You need the two dimensions in order for you to display the items in categories in the table view.

![][35]

[35]: images/ltc-shopping-order-v1/define-an-array.png

### 6.4 Define the function to populate the arrays

This function will be called when the ShoppingListItems class is instantiated. You'll do this in a later step.

![][36]

[36]: images/ltc-shopping-order-v1/define-the-function-to-populate-the-arrays.png

### 6.5 Define the category arrays

Expand the populateDataWithItems() method to create two arrays of items. These two arrays will be added to the multidimensional array you defined earlier.

These two arrays will store all the butter and cheese items available to the user.

![][37]

[37]: images/ltc-shopping-order-v1/define-the-category-arrays.png

### 6.6 Define empty butter and cheese items

These items will be used to temporarily create new items before adding them to the corresponding category arrays

![][38]

[38]: images/ltc-shopping-order-v1/define-empty-butter-and-cheese-items.png

### 6.7 Create the first butter item

Enter the code to create a new butterItem and add it to the buterArray. 

Currently you don't have images in your project so don't set that value yet. This won't cause issues with your app - if there's no image set, the table view simply won't display anything in the place of the image.

![][39]

[39]: images/ltc-shopping-order-v1/create-the-first-butter-item.png

### 6.8 Second butter item

Create a second butter item and append it to the butter array. You can reuse the butterItem variable as adding it to the array make a copy of the struct to store in the array.

Note the += for adding the second Butter item to the array. This tells Xcode to append the item to the end of the array, creating a new element.

![][40]

[40]: images/ltc-shopping-order-v1/second-butter-item.png

### 6.9 Create two Cheese items

In the same fashion as the butter items, create two Cheese items and add them to the cheese array.

![][41]

[41]: images/ltc-shopping-order-v1/create-two-cheese-items.png

### 6.10 Populate the array

Now that you've got two items in their corresponding category arrays, populate the itemsList array with the two sub arrays.

This is the fundamental structure of your Model in the MVC. You can extend this to create as many items in as many categories as you wish.

![][42]

[42]: images/ltc-shopping-order-v1/populate-the-array.png

### 6.11 Populate the array on Instantiation

Create a init() method to call this populateDataWithItems() method so that when the model gets instantiated, your array will be populated and available to the View Controllers.

![][43]

[43]: images/ltc-shopping-order-v1/populate-the-array-on-instantiation.png

### 6.12 Reporting the number of sections

In order to display the items to the user on your view, there is the ability to display them in sections. See the example under  at the start of the tutorial. The Shopping List View Controller needs to know how many sections to create in order to display them all (and no more).

Currently there is only two sections in your itemsList array, so it would be easy just to set it as 2. However, you want to create your code so that if you expand the list later, then you won't need to find the hard-coded 2 and update it.

Create a method which returns with the size of the array,

![][44]

[44]: images/ltc-shopping-order-v1/reporting-the-number-of-sections.png

### 6.13 Reporting the Section Headers

 In order to do display the sections properly, you have to give each section a heading. One way of doing this is to allow the Model to be queried and it respond with the section headings and this is the way you'll do that here. 

Create a method called getSectionHeader() which accepts an Int as an argument and returns a String. The Int will be the ViewController requesting the heading for a particular section, starting at 0. The returned String will be the text of the heading.

This method can be expanded later to add additional sections as required.

![][45]

[45]: images/ltc-shopping-order-v1/reporting-the-section-headers.png

### 6.14 Reporting the number of rows in each section.

Similar to displaying the sections, the View Controller needs to be aware of how many rows are in each section. Currently you have 2 each, but again, you'll want to generate this dynamically.

Create a method which returns with the number of items in each category array. This function needs to accept an integer which indicates what section it is (similar to the Section Header function above) and return with an integer which indicates how many entries there are and therefore how many rows to display.

![][46]

[46]: images/ltc-shopping-order-v1/reporting-the-number-of-rows-in-each-section.png

### 6.15 Item Detail Methods

Write three methods which, given the section and row the user selects, returns the Name, Count and Image of that item.

These will be called when the View Controller is creating individual rows (the table view calls them "cells") and needs to know what to display.

![][47]

[47]: images/ltc-shopping-order-v1/item-detail-methods.png

### 6.16 Allow for the user to update the item Counts

So far, the access methods are all about informing the View Controller and not about updating the data (the Model). However, you want the item count (the quantity) to increase when the user taps on that cell. 

Define a method which updates the item count of the particular item by its increment value.

Note the += in the assignment. This takes the value of itemCount of the particular element, adds the increment to it and stores the result back into the itemCount.

![][48]

[48]: images/ltc-shopping-order-v1/allow-for-the-user-to-update-the-item-counts.png

### 6.17 Define the Reset Method

You'll recall that you created a button on the Shopping List view called Reset. If the user presses this button, all the quantity values are set back to zero. Create this method in the Model now so you can access it later.

This method doesn't need to take any arguments or return anything as it simply resets the itemCount of all elements in the array to be 0.

![][49]

[49]: images/ltc-shopping-order-v1/define-the-reset-method.png

### 6.18 Return the email text

The last method you need to create in your model is the method which builds the text to email. In later versions this method can be modified to perform the export in another way, but for now, it will simply create a String with the list of selected items and their counts.

The method loops through the itemsList multidimensional array and checks each item. If the items itemCount is greater than 0 it will add it to the end of the string.

Finally, it returns the string to the calling method (in the View Controller).

The \n in the string indicates a return character. This will put each item on its own line in the email that will be generated.

![][50]

[50]: images/ltc-shopping-order-v1/return-the-email-text.png

### 6.19 That's it!

The Model is done. Now the View Controller has to do the hard work.

Save your work. 

To check for all errors, perform a Build of your project. ⌘B or Product -> Build

## 7. Bringing it all together - the ViewController

Now you have defined the View and the Model, now it's time to complete the project by finalising the V in MVC - the ShoppingListViewController.

This ViewController queries the Model and update the View on the item details. It also handles any input from the user, by accepting the relevant taps on the screen and updates or queries the model as required.

![][51]

[51]: images/ltc-shopping-order-v1/bringing-it-all-together---the-viewcontroller.png

### 7.1 Create the connection from UI Elements to code

Similar to the UserNameViewController, you will need to create a few connections from the View to the ViewController. 

Open the Main.storyboard, hold down Control and Click and drag from the Reset and Export Buttons to create Actions called resetAllItems and exportItems.

Don't forget you need to have selected the Assistant Editor to be able to see both the View and the ViewController

![][52]

[52]: images/ltc-shopping-order-v1/create-the-connection-from-ui-elements-to-code-1.png

### 7.2 Instantiate the Model

Declare a new variable that creates a instance of the ShoppingListItems model.

This will create the object and in turn, run method to populate the arrays - creating all the data that you need.

![][53]

[53]: images/ltc-shopping-order-v1/instantiate-the-model.png

### 7.3 Implement the code to reset items

You will need to add only two lines of code to the resetAllItems() method. The first will call the resetItemCount method in the Model (availableItems) and the other will reload all the data for the View to be updated.

![][54]

[54]: images/ltc-shopping-order-v1/implement-the-code-to-reset-items.png

### 7.4 Enable the View Controller to send messages

In order for the ShoppingListViewController class to have the ability to send emails, you need to tell Xcode to import the framework when the object is instantiated.

To do this, import the MessageUI framework modify the class definition to include the MFMailComposeViewControllerDelegate library.

![][55]

[55]: images/ltc-shopping-order-v1/enable-the-view-controller-to-send-messages.png

### 7.5 Implement the code to send the email

Luckily, the MessageUI framework does most of the heavy lifting for sending emails, and all you have to do is give it the information to create and send the email. You need to create an object and pass it the subject, recipients and the body of the email.

To get the message body, you will call the itemsToEmail() method you created in the ShoppingListItems model.

Note the ! after currentUser for the subject.

![][56]

[56]: images/ltc-shopping-order-v1/implement-the-code-to-send-the-email.png

### 7.6 Allow the email message screen to disappear

In order for the iOS device to send the email, the previous function will work. However, in order for the screen to be dismissed so the user can return to the app you need to implement a method that Xcode looks for in order for it to dismiss.

![][57]

[57]: images/ltc-shopping-order-v1/allow-the-email-message-screen-to-disappear.png

### 7.7 Get the number of sections

As the view is a Table View, and this View Controller is a TableViewController, there are a number of methods that you have to implement in order to display the correct information.

Implement the numberOfSectionsInTableView() method to call the getSections() method from your model.

This method will tell the View how many sections to create.

![][58]

[58]: images/ltc-shopping-order-v1/get-the-number-of-sections.png

### 7.8 Get the number of rows in each section

Implement method to return the number of rows in each section.

This method will call the getRowsInSection() method that you defined in the Model. You'll need to pass the section number to the method to get the value.

![][59]

[59]: images/ltc-shopping-order-v1/get-the-number-of-rows-in-each-section.png

### 7.9 Get the headers for each section

Using your getSectionHeaders() method in the model, implement the method to display the headers for each section.

![][60]

[60]: images/ltc-shopping-order-v1/get-the-headers-for-each-section.png

### 7.10 Get the cell data to display in each cell

This complex method gets all the details on each of the array elements and displays the information in each cell.

Additionally, if the count is anything higher than 0 is displays a checkmark so it stands out a bit more to the user.

Note the ? postfixes on the cell attributes.

![][61]

[61]: images/ltc-shopping-order-v1/get-the-cell-data-to-display-in-each-cell.png

### 7.11 Change the values when the cell is tapped

Implement the didSelectRowAtIndexPath method to tell the ViewController to update the model, updating the cell's item count by increasing by the increment.

Calling the tableView.reloadData() method forces the View to update the cell information. 

![][62]

[62]: images/ltc-shopping-order-v1/change-the-values-when-the-cell-is-tapped.png

### 7.12 The ViewController is complete!

Run your app and test all the functionality to ensure that there are no errors, unexplained behaviour or spectacular crashes.

![][63]

[63]: images/ltc-shopping-order-v1/the-viewcontroller-is-complete-.png

## 8. Expand your App!

Now that the foundations are all set up, you can expand your app to include more items in more sections! 

In this section, you app will include extra items and sections (and include different increment values) to make it look like this!

![][64]

[64]: images/ltc-shopping-order-v1/expand-your-app-.png

### 8.1 Expand your Offerings!

Update the populateDataWithItems() method to include new items and new categories. Don't forget to update the increment values as appropriate!



You can find the complete list here : 

     func populateDataWithItems() {
             var butterArray = Array<item>()
             var cheeseArray = Array<item>()
             var milkArray = Array<item>()
             var eggsArray = Array<item>()
             var creamArray = Array<item>()
             var frozenArray = Array<item>()
             var chickenArray = Array<item>()
             
             var butterItem = item()
             var cheeseItem = item()
             var milkItem = item()
             var eggsItem = item()
             var creamItem = item()
             var frozenItem = item()
             var chickenItem = item()
             
             butterItem.title = "Butter"
             butterItem.itemCount = 0
             butterArray = [butterItem]
             butterItem.title = "Ghee"
             butterItem.itemCount = 0
             butterArray += [butterItem]
             butterItem.title = "Salt Reduced"
             butterItem.itemCount = 0
             butterArray += [butterItem]
             butterItem.title = "Margarine"
             butterItem.itemCount = 0
             butterArray += [butterItem]
             
             cheeseItem.title = "Blue"
             cheeseItem.itemCount = 0
             cheeseArray += [cheeseItem]
             cheeseItem.title = "Bocconcini"
             cheeseItem.itemCount = 0
             cheeseArray += [cheeseItem]
             cheeseItem.title = "Brie"
             cheeseItem.itemCount = 0
             cheeseArray += [cheeseItem]
             cheeseItem.title = "Camembert"
             cheeseItem.itemCount = 0
             cheeseArray += [cheeseItem]
             cheeseItem.title = "Cheddar"
             cheeseItem.itemCount = 0
             cheeseArray += [cheeseItem]
             cheeseItem.title = "Edam"
             cheeseItem.itemCount = 0
             cheeseArray += [cheeseItem]
             cheeseItem.title = "Fetta"
             cheeseItem.itemCount = 0
             cheeseArray += [cheeseItem]
             cheeseItem.title = "Fruche/Strawb"
             cheeseItem.itemCount = 0
             cheeseArray += [cheeseItem]
             cheeseItem.title = "Gouda"
             cheeseItem.itemCount = 0
             cheeseArray += [cheeseItem]
             cheeseItem.title = "Greuyer"
             cheeseItem.itemCount = 0
             cheeseArray += [cheeseItem]
             cheeseItem.title = "Mascarpone"
             cheeseItem.itemCount = 0
             cheeseArray += [cheeseItem]
             cheeseItem.title = "Mozzarella"
             cheeseItem.itemCount = 0
             cheeseArray += [cheeseItem]
             cheeseItem.title = "Parmesean"
             cheeseItem.itemCount = 0
             cheeseArray += [cheeseItem]
             cheeseItem.title = "Philadelphia"
             cheeseItem.itemCount = 0
             cheeseArray += [cheeseItem]
             cheeseItem.title = "Ricotta (g)"
             cheeseItem.itemCount = 0
             cheeseArray += [cheeseItem]
             cheeseItem.title = "Tasty shredded"
             cheeseItem.itemCount = 0
             cheeseArray += [cheeseItem]
             cheeseItem.title = "Tofu firm"
             cheeseItem.itemCount = 0
             cheeseArray += [cheeseItem]
             
             milkItem.title = "Milk (mL)"
             milkItem.itemCount = 0
             milkArray += [milkItem]
             milkItem.title = "Milk Low Fat (mL)"
             milkItem.itemCount = 0
             milkArray += [milkItem]
             
             eggsItem.title = "Eggs RSPCA"
             eggsItem.itemCount = 0
             eggsItem.increment = 1
             eggsArray += [eggsItem]
             
             creamItem.title = "Lite Cream (mL)"
             creamItem.itemCount = 0
             creamArray += [creamItem]
             creamItem.title = "Sour Cream (mL)"
             creamItem.itemCount = 0
             creamArray += [creamItem]
             creamItem.title = "Thick Cream (mL)"
             creamItem.itemCount = 0
             creamArray += [creamItem]
             creamItem.title = "Cooking Cream (mL)"
             creamItem.itemCount = 0
             creamArray += [creamItem]
             creamItem.title = "Greek Yoghurt (mL)"
             creamItem.itemCount = 0
             creamArray += [creamItem]
             
             frozenItem.title = "Greek Yoghurt (mL)"
             frozenItem.itemCount = 0
             frozenArray += [frozenItem]
             
             chickenItem.title = "Bones"
             chickenItem.itemCount = 0
             chickenItem.increment = 1
             chickenArray += [chickenItem]
             chickenItem.title = "Breast (g)"
             chickenItem.itemCount = 0
             chickenItem.increment = 50
             chickenArray += [chickenItem]
             chickenItem.title = "Mince"
             chickenItem.itemCount = 0
             chickenArray += [chickenItem]
             chickenItem.title = "Drumsticks"
             chickenItem.itemCount = 0
             chickenArray += [chickenItem]
             chickenItem.title = "Duck Breast"
             chickenItem.itemCount = 0
             chickenArray += [chickenItem]
             chickenItem.title = "Maryland"
             chickenItem.itemCount = 0
             chickenArray += [chickenItem]
             chickenItem.title = "Tenderloin (g)"
             chickenItem.itemCount = 0
             chickenArray += [chickenItem]
             chickenItem.title = "Thigh (each)"
             chickenItem.itemCount = 0
             chickenItem.increment = 1
             chickenArray += [chickenItem]
             chickenItem.title = "Whole Chicken"
             chickenItem.itemCount = 0
             chickenArray += [chickenItem]
             chickenItem.title = "Turkey Breast"
             chickenItem.itemCount = 0
             chickenItem.increment = 50
             chickenArray += [chickenItem]
             chickenItem.title = "Turkey Mince"
             chickenItem.itemCount = 0
             chickenArray += [chickenItem]
             chickenItem.increment = 50
             chickenItem.title = "Wing"
             chickenItem.itemCount = 0
             chickenArray += [chickenItem]
             
             
             itemsList = [butterArray, cheeseArray, milkArray, eggsArray, creamArray, frozenArray, chickenArray]
         }

![][65]

[65]: images/ltc-shopping-order-v1/expand-your-offerings-.png

### 8.2 Update the Section Headings

Your app will still work without this step, however it will look better with proper headings rather than "Error".

Update the getSectionHeaders() method in your ShoppingListItems.swift file.

![][66]

[66]: images/ltc-shopping-order-v1/update-the-section-headings.png

## 9. Add Imagery

In this section you'll add some images to associate with the items to display on screen. You'll also add an icon to your app!

### 9.1 Copy in Images

Find images that match your items and copy the files in.

A few notes on the images. You'll need to resize them to approximately 80x80 pixels and they have to be PNG files.

![][67]

[67]: images/ltc-shopping-order-v1/copy-in-images.png

### 9.2 Update Code to set the images

Open ShoppingListItems.swift and look for the populateDataWithItems() method.

Update the entries to include the images that you've imported. Make sure that the names of the images match the code you're inputting. 

Note, you do not need to include the .png as part of the name.

Also note the ! at the end of each of the additional lines of code

![][68]

[68]: images/ltc-shopping-order-v1/update-code-to-set-the-images.png

### 9.3 Run the app

Your App should now look like this

![][69]

[69]: images/ltc-shopping-order-v1/run-the-app.png

### 9.4 App Icon

Open the Images.xcassets file and you'll see one entry for AppIcon. This is a collection of image assets that can be used throughout your app (not just for the icon).

Find an appropriate app icon and you'll have resize them (in your favourite image editting software or icon generating software) so that there are a number of versions/sizes.

The icons in the following screenshot have the following sizes:

iPhone App 2x - 120 x 120 pixels

iPhone App 3x - 180 x 180 pixels

iPad App 1x - 72 x 72 pixels

iPad App 2x - 144 x 144 pixels

You can continue to add icons, but those 4 are the main ones you'll be testing on.

![][70]

[70]: images/ltc-shopping-order-v1/app-icon.png