# LTC Shopping List v1.0

The LTC Shopping List series of tutorials is designed to develop a working iOS app (for both iPhone and iPad) which allows users to choose ingredients for their recipes and submit their list to a central location for bulk purchasing. This is to satisfy the requirement for students at a school to select their ingredients and the teacher purchase the items for all students on a weekly basis.

The series of tutorials will develop the app in various stages, with each stage being a complete, working version.

The plan for the sequence of versions are as follows.

**Version 1** This version will focus on functionality, with a hard-coded ingredient list. At the end of the tutorial, the user will be able to select from a list of ingredients in a table and then email the list to their teacher.

This version will see the foundations of the app created, using the Model-View-Controller structure to set up the app for future development. The shopping list items will load into a TableView, broken up by categories/sections. This will be the structure to the app in subsequent versions.

**Version 2** The User Interface is improved in this version by customising the cells in the table to display more information efficiently. The initial welcome screen will also be updated, using Auto-Layout, to be displayed correctly on different screen sizes and orientations.

**Version 3** This version improves upon the storing of the ingredient list. Instead of hard-coding the list, the app will retrieve the latest version of the list from a webserver to display to the user. The images will also be downloaded, which will require the integration of Grand Central Dispatch to keep the interface responsive while the images are downloading.

**Version 4** This update will focus on the interface with introducing some more interactivity to the cells in the table.

**Version 5** The final version will change the way the selected ingredient list is submitted to the teacher. Rather than an email being sent, this version will update a central location with the students selection, and the teacher will be able to get a single total of all ingredients from all students.