# NUID:
- Hardik Sodhani : 002770306
- Rucha Chotalia : 002711888
- Aakash Rajawat : 002764127
- Diya Baldota   : 002747966

# Apartment Rental System
The goal of our project is to make a unified solution for people to find and book the best rental apartments according to their set of preferences with filters that allow them to look for the distance to their universities or workplace, their preferred locality and also fit in their budget, in and around Boston.

## The steps and requirements for our project:
+ To gather the data of approximately 800+ apartments in the vicinity of Boston.
+ Data Preprocessing for removing the redundancies in the collected data.
+ To generate an optimal system that provides the user the best suitable apartment options for their set preferences. 

## The features of our dataset:
    1. Sr no
	2. Apt no, Floor
	3. Rent
	4. Locality
	5. Square ft. area
	6. Number of Rooms and Bath
	7. Furnished (y/n)
	8. Parking (y/n)
	9. Pets allowed (y/n) 
	10. Utilities(electricity, gas, trash, hot water) 
	11. Distance from University and schools		
	12. Type of Apartment
	13. Security type
	14. Number of people on lease
	15. Laundry in unit or in basement
	16. Lease start or end date
	17. Availability(y/n)
	18. Transportation

# A Python code on Scrapping twitter data for Boston Apartment rentals:

A python code on Google Colab which uses Twitter API v2 for scrapping data from Twitter based on the Keywords entered by he user
(in this case #Bostonrentals and #Bostonapartments). The goal is to obtain data from twitter based on the availability of any apartment retal
information that has been posted on the website and store it in a local database server. 

## UML Diagram

## Explaination on some of the design decisions:

- ‘BostonRentals’ table has everything that is posted on the twitter platform with the keyword that the user inputs and has properties 
   like (created_at, id, text, media, location), all the new tweets can be scraped and added to this table using the scripting from keyword 
   using Twitter API v2.
- ‘BostonFollow’ table has the count of followers the user has gained per tweet. This table can be altered as and when there 
  is new tweet posted by the user.
- 'Tweets_df’ table shows the last 50 tweets of the set username. It has attributed such as created_at, id, text which can be scraped
   using the username of a user, in this case ‘Apartments Boston’.
   
## SQL STATEMENTS:

### Use case: User searches for rentals in Boston:
SELECT * from bostonrentals where location="Boston, MA";


### Use case: Search on twitter with a specific price range:
SELECT * from bostonrentals where Text like '%3,000%'

### Use case: Search on twitter with a specific house type:
SELECT * FROM bostonrentals WHERE Text like '%5 Bedrooms 2 Baths%'

### Use case: Search on twitter with a specific area of preference:
SELECT * FROM bostonrentals ORDER BY Location ASC

### Use case: User is redirected to their specific search:
SELECT *
FROM bostonrentals
WHERE NOT (Text LIKE '%RT%');

# USE CASES:

### 1. User Registers and creates an account
Description: User registers for an account on NoHome
Actors: User
Precondition: When the user wants to rent a place, they will first register 
Steps:
Actor action – User will request for registration
System Responses – If customer information is correct then customer is registered and use case ends
Post Condition: Customer is successfully registered
Alternate Path: The customer request is not correct, the system throws an error
Error: User information is incorrect

### 2. Search on twitter for rentals in Boston
Description: User searches for rentals in Boston
Actors: User
Precondition: The user will search for rentals when they  are already registered.
Steps:
Actor action – User will use hashtags like #bostonrentals in the search tab
System Responses –  If the customer search is valid they will get all the tweets with the hashtag #bostonrentals
Post Condition: Customer gets all the rentals in Boston with hashtag #bostonrentals
Alternate Path: The Customer request has no results, the system shows an error
Error: Shows no results for the search

### 3. Search on twitter with a specific price range
Description: User searches for rentals with a specific price range in Boston
Actors: User
Precondition: The user will search for rentals with specific price range in Boston, only once they login to their twitter account
Steps:
Actor action – User will use twitter and look for rentals in their budget in the search tab
System Responses –  If the customer search is valid they will get all the tweets with the hashtag #bostonrentals
Post Condition: Customer gets all the rentals in Boston with hashtag #bostonrentals
Alternate Path: The Customer request has no results, the system shows an error
Error: Shows no results for the search

### 4. Search on twitter with a specific house type
Description: User searches for rentals with a specific house type in Boston
Actors: User
Precondition: Once the user logs into their account they will be able to search for rentals with their specific house type in Boston
Steps:
Actor action – User will input their preferences of house type(eg.apartment, home, studio) in thee search tab 
System Responses –
Post Condition:The user will get all the results with the specified condition
Alternate Path:No results are found and the system will ask them to search again
Error:Show no results for the search

### 5. Search on twitter with a specific area of preference
Description: User searches for rentals with their preferred vicinity in Boston
Actors:User
Precondition: Once the user logs into their account they will be able to search for rentals with their specific areas in Boston
Steps: 
Actor action – User will input their area preference and the search tab
System Responses –
Post Condition: The user will get all the results with the specified condition
Alternate Path: No results are found and the system will ask them to search again
Error: Show no results

### 6. User is redirected to their specific URL through twitter
Description: User clicks on the URL mentioned in the tweet and they will be re-directed to apartments site where 
Actors: User
Precondition: User will first have to login to their twitter account then they will click on the URL and they will be directed to the site        
Steps:
Actor action –  User will view the tweet and click on the URL mentioned in the tweet
System Responses –
Post Condition: The user will be successfully be redirected to the site
Alternate Path: The user will not be redirected to the right page
Error: 404 Page not found

### 7. User will be able to book an appointment for viewing the flat through the URL
Description: Once the user is redirected to the site they will be able to book a viewing appointment through their site
Actors:User
Precondition: User will first have to click on the link through the tweet after logging into their twitter account
Steps:
Actor action – User will book an appointment for viewing from the link
System Responses –
Post Condition:The viewing appointment will be booked suitable to the user’s time
Alternate Path: The appointment will fail to book or no appointments available
Error: No appointments booked

### 8. Look for reviews for a place previously rented by a different user
Description: The user will be able to view the reviews of people who have previously rented the place
Actors:User
Precondition:The user will have to log into their account and then view the reviews under the tweet
Steps:
Actor action – The user will have to check the tweets which have the reviews
System Responses –
Post Condition:The user will be able to read all reviews under the tweet
Alternate Path: No reviews for the rental
Error: No results found

### 9. Search on twitter for a house having certain set of amenities
Description: The user will be able to search for specific amenities according to the user’s requirements  
Actors: User
Precondition: The user will have to log into their twitter account and then search for their requirements 
Steps:
Actor action –The user will be able to search in the search tab the amenities that fit their requirements
System Responses –
Post Condition: The user will be get all the search results that fir their conditions
Alternate Path:The search results won’t be found
Error: No search for the user’s conditions

### 10. Search on twitter for a rental with a certain lease requirements
Description: The user will be able to search for lease criteria according to the users requirements
Actors: User
Precondition:The user will have to log into their twitter account and then search for their requirements 
Steps:
Actor action – The user will be able to search in the search tab the lease requirements that the user wants
System Responses –
Post Condition: The search result will be displayed
Alternate Path: No results for the specified requirements
Error:No searches found

### 11. Search for a rental with specific building amenities
Description: The user will be able to search for specific amenities in the building according to the user’s requirements  
Actors: User
Precondition: The user will have to log into their twitter account and then search for their requirements 
Steps:
Actor action – The user will be able to search in the search tab the amenities that fit their requirements
System Responses –
Post Condition: The search results will be found
Alternate Path: No results for the specifies requirements
Error:No searched found



### 12. Search for a rental with universities around them 
Description:The user will be able to search for universities around the rental vicinity
Actors: User
Precondition: The user will have to log into their twitter account and then search for their requirements 
Steps:
Actor action – The user will be able to search in the search tab the universities around the vicinity
System Responses –
Post Condition: The search results will be found
Alternate Path: No results for the specifies requirements
Error:No searched found

### 13. Look for how many days the listing has been posted
Description:The user will be able to see since how many days the listing has been posted
Actors:User
Precondition: The user will have to log into their twitter account and then see since how many days the listing has been posted
Steps:
Actor action – The user will be able to see the time since the listing has been posted
System Responses –
Post Condition: The time since posted will be displayed 
Alternate Path: No timeline mentioned
Error: No listings found

### 14. Look for a rental with public transport near them
Description:The user will be able to search for public transport around the rental vicinity
Actors: User
Precondition: The user will have to log into their twitter account and then search for their requirements 
Steps:
Actor action – The user will be able to search in the search tab the public transport around the vicinity
System Responses –
Post Condition: The search results will be found
Alternate Path: No results for the specifies requirements
Error:No searched found

### 15. Look for a apartment types of the rental
Description: User searches for rentals with a specific apartment  type(studio,1bhk,2bhk, 3bhk etc) in Boston
Actors: User
Precondition: Once the user logs into their account they will be able to search for rentals with their specific apartment type in Boston
Steps:
Actor action – User will input their preferences of apartment type(studio,1bhk,2bhk, 3bhk etc) in thee search tab 
System Responses –
Post Condition:The user will get all the results with the specified condition
Alternate Path:No results are found and the system will ask them to search again
Error:Show no results for the search

### 16. Look for rental closer to the grocery stores
Description:The user will be able to search for grocery stores around the rental vicinity
Actors: User
Precondition: The user will have to log into their twitter account and then search for their requirements 
Steps:
Actor action – The user will be able to search in the search tab the grocery stores around the vicinity
System Responses –
Post Condition: The search results will be found
Alternate Path: No results for the specifies requirements
Error:No searched found

### 17. Look for a rental that has the closest medical centers
Description:The user will be able to search for the medical centers closest to the rental vicinity
Actors: User
Precondition: The user will have to log into their twitter account and then search for their requirements 
Steps:
Actor action – The user will be able to search in the search tab the medical centers closest to the the vicinity
System Responses –
Post Condition: The search results will be found
Alternate Path: No results for the specifies requirements
Error:No searched found

### 18.Look for rental with extra amenities like fireplace, balcony
Description: The user will be able to search for specific amenities in the rental (fireplace, balcony etc)  according to the user’s requirements  
Actors: User
Precondition: The user will have to log into their twitter account and then search for their requirements 
Steps:
Actor action – The user will be able to search in the search tab the amenities that fit their requirements
System Responses –
Post Condition: The search results will be found
Alternate Path: No results for the specifies requirements
Error:No searched found

### 19.Security type for the rental unit:
Description: The user will be able to search for the security type (key, tap etc) for the rental
Actors: User
Precondition: The user will have to log into their twitter account and then search for their requirements 
Steps:
Actor action – The user will be able to search in the search tab the security requirements that fit their requirements
System Responses –
Post Condition: The search results will be found
Alternate Path: No results for the specifies security type
Error:No searched found

### 20.Look for a rental closer to the airport:
Description:The user will be able to search for the airport closest to the rental vicinity
Actors: User
Precondition: The user will have to log into their twitter account and then search for their requirements 
Steps:
Actor action – The user will be able to search in the search tab the airport closest to the the vicinity
System Responses –
Post Condition: The search results will be found
Alternate Path: No results for the specifies requirements
Error:No searched found




