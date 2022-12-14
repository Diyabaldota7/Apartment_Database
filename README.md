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
    1. ID
	2. Price
	3. Type of Apartment
	4. Region
	5. Square ft. area
	6. Number of Beds
	7. Laundry Option
	8. Number of Baths
	9. Number of Cats Allowed
	10. Number of Dogs Allowed
	11. Image URL		
	12. State


### DMDD APT1 Table:

CREATE TABLE dmddapt1 (
    Id int,
    Price int,
    type varchar(255),
    );

### DMDD APT2 Table:

CREATE TABLE dmddapt2 (
    Id int,
    Region varchar(255),
    sqft INT,
    bed INT,
    laundry_options varchar(255),
);

### DMDD APT3 Table:

CREATE TABLE dmddapt3 (
    Id int,
    Baths int,
    cats_allowed varchar(255),
    dogs_allowed varchar(255)
);

### DMDD APT4 Table:

CREATE TABLE dmddapt4 (
    Id int,
    image_url varchar(500),
    state varchar(255)
);


## Explaination on some of the design decisions:

- ‘DMDD APT1’ table has the id, price and type of the apartment (eg. 768798123002, 3000, Condo).
- ‘DMDD APT2’ table has the area, sqft., Number of Beds, Laundry Option.
- 'DMDD APT3’ table shows Number of Baths, No. of Cats Allowed, No. of Dogs Allowed.
- 'DMDD APT4' table shows the images of the apartment and the State in which the apartment is located.


# USE CASES:

### Use Case 1:
SELECT dmddapt1.id, dmddapt2.beds, dmddapt2.sqfeet 
FROM dmddapt1
INNER JOIN dmddapt2 ON dmddapt1.id=dmddapt2.id;

### Use Case 2:
SELECT dmddapt1.id, dmddapt2.beds, dmddapt2.laundry_options 
FROM dmddapt1
LEFT JOIN dmddapt2 ON dmddapt1.id=dmddapt2.id;

### Use Case 3:
SELECT dmddapt1.id, dmddapt2.region, dmddapt2.sqfeet
FROM dmddapt2
RIGHT JOIN dmddapt1 ON dmddapt1.id=dmddapt2.id ;

### Use Case 4:
SELECT dmddapt1.id, dmddapt2.region, dmddapt2.sqfeet
FROM dmddapt2
INNER JOIN dmddapt1 ON dmddapt1.id=dmddapt2.id 
ORDER BY dmddapt2.sqfeet DESC;

### Use Case 5:
SELECT dmddapt1.type,  dmddapt2.sqfeet
FROM dmddapt2
INNER JOIN dmddapt1 ON dmddapt1.id=dmddapt2.id ;

### Use Case 6:
SELECT AVG(dmddapt1.price)
FROM dmddapt2
INNER JOIN dmddapt1 ON dmddapt1.id=dmddapt2.id ;

### Use Case 7:
SELECT state, count(image_url) as count
FROM dmddapt4
GROUP BY state;

### Use Case 8:
SELECT COUNT(id) as count, region
FROM dmddapt2
GROUP BY region;

### Use Case 9:
SELECT dmddapt1.id, dmddapt2.beds, dmddapt2.sqfeet 
FROM dmddapt1
INNER JOIN dmddapt2 ON dmddapt1.id=dmddapt2.id
where dmddapt2.laundry_options like '%laundry in bldg%' or dmddapt2.laundry_options like '%laundry on site%';

### Use Case 10:
SELECT dmddapt1.id, dmddapt1.price, dmddapt1.type, dmddapt2.region 
FROM dmddapt1
INNER JOIN dmddapt2 ON dmddapt1.id=dmddapt2.id
where dmddapt2.region = 'Boston' and dmddapt1.type like '%apartment%';

### Use Case 11:
SELECT *
FROM dmddapt2
JOIN dmddapt3 ON dmddapt2.id=dmddapt3.id
where dmddapt2.region='Boston' and dmddapt3.cats_allowed=1  ;

### Use Case 12:
SELECT *
FROM dmddapt1
JOIN dmddapt4 ON dmddapt1.id=dmddapt4.id
where dmddapt1.type = 'apartment' and dmddapt4.image_url IS NOT NULL;

### Use Case 13:
SELECT dmddapt1.id, dmddapt1.price, dmddapt1.type, dmddapt2.region 
FROM dmddapt1
JOIN dmddapt2 ON dmddapt1.id=dmddapt2.id
where dmddapt2.region = 'Boston' and dmddapt1.type like '%apartment%';

### Use Case 14:
SELECT dmddapt1.id, dmddapt1.price, dmddapt2.region 
FROM dmddapt1
JOIN dmddapt2 ON dmddapt1.id=dmddapt2.id
where dmddapt2.sqfeet > 700 and dmddapt1.type like '%apartment%'
ORDER BY dmddapt1.price DESC;

### Use Case 16:
SELECT dmddapt1.id, dmddapt1.price, dmddapt2.beds,dmddapt2.laundry_options 
FROM dmddapt1
JOIN dmddapt2 ON dmddapt1.id=dmddapt2.id
where dmddapt2.laundry_options='w/d in unit';

### Use Case 17:
SELECT dmddapt1.id, dmddapt1.price, dmddapt2.beds,dmddapt2.beds 
FROM dmddapt1
JOIN dmddapt2 ON dmddapt1.id=dmddapt2.id
where dmddapt2.beds>1;

### Use Case 16:
SELECT DISTINCT dmddapt2.region, dmddapt2.sqfeet
FROM dmddapt2
RIGHT JOIN dmddapt1 ON dmddapt1.id=dmddapt2.id ;

### Use Case 18:
SELECT dmddapt1.id, dmddapt3.cats_allowed, dmddapt3.cats_allowed
FROM dmddapt3
RIGHT JOIN dmddapt1 ON dmddapt1.id=dmddapt3.id ;

### Use Case 19:
SELECT * FROM dmddapt1 
where price>100 
order by price desc;

### Use Case 20:
Select * from dmddapt2
where beds >= 2 and laundry_options = 'w/d in unit'


## ER Diagram:
<br>

<img src="ERdiagram (1).png" width="1000" height="500"/><br><br>


