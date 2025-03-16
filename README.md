# UK Food Standards Database Analysis
The UK Food Standards Agency evaluates establishments across the United Kingdom and assigns them a food hygiene rating. I was contracted by Eat Safe, Love magazine to analyze some of this data to help journalists and food critics decide where to focus their future articles. Here's what I did! 

## 🛠️ Part 1: Database and Jupyter Notebook Set Up
1. Imported Data
    - Loaded the establishments.json file into MongoDB via the terminal.
    - Named the database uk_food and the collection establishments.
    - Copied the import command into a markdown cell for reference.
2. Set Up the Notebook
    - Imported PyMongo and Pretty Print (pprint).
    - Created a MongoDB client instance and connected to the database.
3. Confirmed Data Import
    - Listed all databases to ensure uk_food was created.
    - Checked collections to verify establishments existed.
    - Retrieved a sample document using find_one() to confirm successful import.

## 🔄 Part 2: Updating the Database
1. Added a New Restaurant
    - The magazine requested the addition of a new halal restaurant, Penang Flavours, which had not been rated yet.
2. Updated the BusinessTypeID
    - Queried the database to find the correct BusinessTypeID for "Restaurant/Cafe/Canteen".
    - Updated Penang Flavours with the appropriate BusinessTypeID.
3. Removed Establishments in Dover
    - Checked how many establishments were under the Dover Local Authority.
    - Removed all records with this Local Authority.
    - Verified the deletion by checking the document count again.
4. Converted Data Types
    - Some numerical fields were stored as strings, so I updated them:
      - Converted longitude and latitude to decimal numbers.
      - Converted RatingValue to integers.

## 🔎 Part 3: Exploratory Analysis
The magazine had specific questions, and I used MongoDB queries to find the answers!
1. Establishments with a Hygiene Score of 20
    - Used count_documents() to get the total number.
    - Retrieved the first document using find_one().
    - Converted results into a Pandas DataFrame for better readability.
2. Highly Rated Establishments in London
    - Found establishments with RatingValue ≥ 4 in the London Local Authority using a $regex search.
3. Top 5 Establishments Near "Penang Flavours" with a Rating of 5
    - Queried locations within 0.01 degrees of latitude and longitude.
    - Filtered by RatingValue = 5.
    - Sorted by Hygiene score (ascending).
4. Local Authorities with the Most Hygiene Score of 0
    - Used the aggregation pipeline to count establishments per Local Authority.
    - Sorted results in descending order to find the top 10.
  
## 🎯 Key Takeaways
✅ Successfully modified and cleaned the dataset.  
✅ Found insights on hygiene scores and highly rated establishments.  
✅ Identified the best places near "Penang Flavours" for potential reviews.  

This project was a great exercise in MongoDB, NoSQL queries, and data cleaning! 🚀📊
