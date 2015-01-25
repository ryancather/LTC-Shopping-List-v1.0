# Expand your App!

Now that the foundations are all set up, you can expand your app to include more items in more sections! 

In this section, you app will include extra items and sections (and include different increment values) to make it look like this!

![][64]

[64]: images/ltc-shopping-order-v1/expand-your-app-.png

## 8.1 Expand your Offerings!

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

## 8.2 Update the Section Headings

Your app will still work without this step, however it will look better with proper headings rather than "Error".

Update the getSectionHeaders() method in your ShoppingListItems.swift file.

![][66]

[66]: images/ltc-shopping-order-v1/update-the-section-headings.png