# Add Imagery

In this section you'll add some images to associate with the items to display on screen. You'll also add an icon to your app!

## 9.1 Copy in Images

Find images that match your items and copy the files in.

A few notes on the images. You'll need to resize them to approximately 80x80 pixels and they have to be PNG files.

![][67]

[67]: images/ltc-shopping-order-v1/copy-in-images.png

## 9.2 Update Code to set the images

Open ShoppingListItems.swift and look for the populateDataWithItems() method.

Update the entries to include the images that you've imported. Make sure that the names of the images match the code you're inputting. 

Note, you do not need to include the .png as part of the name.

Also note the ! at the end of each of the additional lines of code

![][68]

[68]: images/ltc-shopping-order-v1/update-code-to-set-the-images.png

## 9.3 Run the app

Your App should now look like this

![][69]

[69]: images/ltc-shopping-order-v1/run-the-app.png

## 9.4 App Icon

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