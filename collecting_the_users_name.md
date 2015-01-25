# Collecting the Users Name

In this section you will write the code so that when the user taps the button, the app collects the users name from Text Field and then displays the next view.

This View will also have a View Controller but no model, as you only need to collect the users name, a simple string.

## 5.1 Create the connection from UI Elements to code

Open the Main.storyboard.

Xcode has the ability to easily create connections between Views and the corresponding View Controllers. There are two main types of connections that you'll be creating; 

1) Action, is for when you want the code to do something when the user does something on screen.

2) Outlet, is for when you want to be able to access a UI element from within code.

Select the User Name View in the storyboard and click on the Assistant Editor button. You should now see both the View and the View Controller code on screen.

![][22]

[22]: images/ltc-shopping-order-v1/create-the-connection-from-ui-elements-to-code.png

## 5.2 Create Button Action

Now to create the function for when the user taps the Begin Ordering Button.

Control Click Drag from the Begin Ordering button to the View Controller.

![][23]

[23]: images/ltc-shopping-order-v1/create-button-action.png

## 5.3 Create the Action

In the menu that appears set the connection type to be Action and the name to be getUserName. Click Connection. 

This creates the IBAction function structure for you.

![][24]

[24]: images/ltc-shopping-order-v1/create-the-action.png

## 5.4 Give the Text Field a name

Perform the same steps for the Text View, except in this case, set the connection type to be Outlet and name it "userNameField".

Your project should now look like the following

![][25]

[25]: images/ltc-shopping-order-v1/give-the-text-field-a-name.png

## 5.5 Set up a UserName variable

Before writing the code for the function, set up a String variable to temporarily hold the users name. As this variable may or may not contain a value, it needs to be created as an Optional with the ? postfix.

![][26]

[26]: images/ltc-shopping-order-v1/set-up-a-username-variable.png

## 5.6 Write the getUserName() function

Now the string variable has been created and you've created the connections between the View and the code, you can now write the code for the getUserName() function to store the users name from the userNameField element.

![][27]

[27]: images/ltc-shopping-order-v1/write-the-getusername---function.png

## 5.7 Prepare for the Seque

So far, you've collected the users name and stored it into a variable, now you will need to write another function that will actually perform the segue - load the next view.

This method is overridden from the parent UIViewController class.

![][28]

[28]: images/ltc-shopping-order-v1/prepare-for-the-seque.png

## 5.8 Set up the Destination Variable

There's one last thing you have to do for this to work. You've set up the code so that the view will load, but you need to "send" the usersName variable to the next View Controller. You can do this by creating a variable in the ShoppingListViewController class and then store the usersName variable into that one.

Open the ShoppingListViewController.swift file and define an optional String variable named "currentUser". This variable will be used throughout the ShoppingListViewController class to access and use the Users name. This will become important when the user wants to finalise or export their order so that the recipient knows who ordered which items.

Note the ? postfix to indicate that the currentUser variable is an optional.

Save the file.

![][29]

[29]: images/ltc-shopping-order-v1/set-up-the-destination-variable.png

## 5.9 "Send" the users name

Back in the UserNameViewController class, change the prepareForSegue() function to set the newly created currentUser variable to be the usersName.

Note the ! after currentUser variable. This forces Xcode to extract the String out of the variable instead of treating it as an Optional.

That's all you need to do to store the name in the next View Controller. Save the file.

![][30]

[30]: images/ltc-shopping-order-v1/-send--the-users-name.png

## 5.10 Test that the name was received.

Just to make sure that the users name has been sent correctly, you can use the name to change the title of the view to include the users name.

In the ShoppingListViewController, implement the function viewDidLoad(). This is similar to the prepareForSegue() function previously, it is overridden from the superclass.

Note the ! after currentUser variable. This forces Xcode to extract the String out of the variable instead of treating it as an Optional.

Run the code and type in a name into the User Name Text Field and tap the Begin Ordering button. You should see your name appear as the title on the shopping list!

![][31]

[31]: images/ltc-shopping-order-v1/test-that-the-name-was-received.png