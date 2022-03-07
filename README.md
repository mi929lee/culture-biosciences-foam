# Culture Biosciences: Foam Challenge

Hello! Unfortunately, I did not have enough time to actually implement this application, but I will explain how I would design this application.

My understanding of the project was that I am creating a website that allows users to view pictures and mark them as "foaming" or "non-foaming". The ones that haven't been explicitly marked are under the category of "classified". 

## Backend Design

### Database

In order to allow the app to keep track of whether each image is "foaming" or "non-foaming", a database needs to be used, with an API that will query and edit the database. My choice of storage would be MySQL (relational database), which would have four fields: `id`, `image link`, `date modified`, and `foaming` (which would store null, "foaming", or "non-foaming"). The user would have the option of filtering based on this `foaming` field. The `id` field would serve as the primary key, and be automatically incremented.

### API

I would then create a REST API with the Flask backend framework, since it uses Python (which is what Culture Biosciences uses, just to be consistent with the usage of technology).

## Frontend Design

In terms of how I would display the data, I would have a radio button on the top left, which would allow the user to toggle between viewing "foaming", "non-foaming", or unclassified images. This would be the part at which the user "filters" for the different types of images.

I would also display 15 images at a time (below the radio buttons), with a dropdown above or below it, which would indicate whether the image shows foaming or no foaming. Having the dropdown would be good, to ensure that there are no typos when inputting values into the database, which would ensure that the filtering works correctly. Pagination would allow the user to eventually see all of the images.

To update the database, I would use Javascript's handleChange to call a PUT request to edit the database. This would change the `foaming` field as well as the `date modified` field of that particular image.

Additionally, I would have a variable that keeps track of the number of changes to the database that would happen in one page (in one set of 15 images). If the number of changes is >1, then when we go to a different page in pagination, I would re-fetch the data. This would be prevent immense lagging/loading times for when a user wants to edit many images' `foaming` data field.

In terms of the styling of the overall page, I would use Bootstrap as the CSS framework, since it is the most commonly used. This would support pagination, radio buttons, and the dropdowns.
