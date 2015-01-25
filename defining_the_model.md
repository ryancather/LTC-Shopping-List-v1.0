# Defining the Model

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