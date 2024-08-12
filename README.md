# nosql-challenge

NoSQL Challenge For this week challenge we were given following tasks. 

The UK Food Standards Agency evaluates various establishments across the United Kingdom, and gives them a food hygiene rating. We been contracted by the editors of a food magazine, Eat Safe, Love, to evaluate some of the ratings data in order to help their journalists and food critics decide where to focus future articles.

This challenge was with 3 parts: 
Part 1: Database and Jupyter Notebook Set Up Part
2: Updating the Database 
Part 3: Exploratory Analysis

Part 1: Database and Jupyter Notebook Set Up 
• Part one and two were done in NoSQL_setup.ipynb. Firsly, connected the MongoDB, and imported the data provided in the establishments.json file from our Terminal. Named the database uk_food and the collection establishments. 
• Within the notebook, imported the libraries we need: PyMongo and Pretty Print (pprint). 
• Created an instance of the Mongo Client. 
• Confirmed that we created the database and loaded the data properly: • Listed the databases we have in MongoDB. Confirmed that uk_food is listed. 
• Listed the collection(s) in the database and ensured that establishments is there. 
• Found and displayed one document in the establishments collection using find_one and display with pprint. 
• Assigned the establishments collection to a variable to prepare the collection for use.


Part 2: Update the Database Some modifications were done before analysis as follows. An exciting new halal restaurant just opened in Greenwich but hasn't been rated yet. The magazine has asked us to include it in our analysis. Added following information to the database:

{ “BusinessName":"Penang Flavours", "BusinessType":"Restaurant/Cafe/Canteen", "BusinessTypeID":"", "AddressLine1":"Penang Flavours", "AddressLine2":"146A Plumstead Rd", "AddressLine3":"London", "AddressLine4":"", "PostCode":"SE18 7DY", "Phone":"", "LocalAuthorityCode":"511", "LocalAuthorityName":"Greenwich", "LocalAuthorityWebSite":"http://www.royalgreenwich.gov.uk", "LocalAuthorityEmailAddress":"health@royalgreenwich.gov.uk", "scores":{ "Hygiene":"", "Structural":"", "ConfidenceInManagement":"" }, "SchemeType":"FHRS", "geocode":{ "longitude":"0.08384000", "latitude":"51.49014200" }, "RightToReply":"", "Distance":4623.9723280747176, "NewRatingPending":True }

Found the newly added restaurant's BusinessTypeID for "Restaurant/Cafe/Canteen" and return only the BusinessTypeID and BusinessType fields. Updated the new restaurant with the BusinessTypeID we found.

The magazine is not interested in any establishments in Dover, therefore, checked how many documents contain the Dover Local Authority. Then, removed any establishments within the Dover Local Authority from the database, and checked again the number of documents to ensure they were deleted. Some of the number values are stored as strings, when they should be stored as numbers. Used update_many to convert latitude and longitude to decimal numbers. Used update_many to convert RatingValue to integer numbers.


Part 3: Exploratory Analysis:Eat Safe, Love had specific questions they want you to answer, which will help them find the locations they wish to visit and avoid.
• Used the following questions to explore the database, and find the answers, so that we can provide them to the magazine editors.
• Which establishments have a hygiene score equal to 20?
• Which establishments in London have a RatingValue greater than or equal to 4? 
• What are the top 5 establishments with a RatingValue of 5, sorted by lowest hygiene score, nearest to the new restaurant added, "Penang Flavours"? • For this tasked I compared the geocode to find the nearest locations. Search within 0.01 degree on either side of the latitude and longitude. 
• How many establishments in each Local Authority area have a hygiene score of 0? Sort the results from highest to lowest, and print out the top ten local authority areas.

