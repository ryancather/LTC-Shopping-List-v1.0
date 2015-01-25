# Bringing it all together - the ViewController

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